# COLLECTİON AND MAP INTERFACE

# Collection Interface

- [ ]  Classes that inherit from the Collection interface are gathered under the "java.util" package.

---

✔️Functions that subclasses deriving from the collection interface must provide:

- int size(): Returns the number of elements of the dataset.
- boolean isEmpty(): Returns true if there are no elements in the dataset.
- boolean contains(Object element): Indicates whether there is a searched element in the data set as true or false.
- Iterator iterator(): Returns the object to navigate through the individual elements in the dataset.
- Object[] toArray(): Returns the dataset as an array.
- boolean add(E e): Allows adding elements to the dataset.
- boolean remove(Object element): Allows deleting elements from dataset.
- boolean addAll(Collection<?> extends E elements): Adds another collection type dataset to the existing dataset in its entirety.
- void clear(): Deletes all elements in the dataset.
- boolean removeAll(Collection<?> elements):  Deletes the given set of elements from the current dataset.

![collection-interface.png](https://github.com/zehracakir/CollectionAndMapInterfaceJava/blob/main/collection-interface.png)

## COLLECTION

### SET INTERFACE

- The Set interface does not allow the same elements to be found again in the dataset.
- **Declaration:** The Set interface is declared as:

```java
public interface Set extends Collection
```

**Creating Set Objects**

```java
Set<?> hSet = new HashSet<>();
```

- Example

```java
import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class SetClass {
    public static void main(String[] args) {
        Set<String> hSet= new HashSet<>();

        //add element
        hSet.add("Zehra Çakır");
        hSet.add("Yusuf");
        hSet.add("Kerem Ege");
        hSet.add("Hatice");
        hSet.add("Fatma");
        hSet.add("Çakır");

        //size
        System.out.println("Size: "+hSet.size());

        //isEmpty
        System.out.println("isEmpty "+hSet.isEmpty());

        //Iterator
        Iterator<String> iterator=hSet.iterator();
        System.out.println("***With Iterator:***");
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }

       //remove
        hSet.remove("Çakır");
        System.out.println("***Then remove***");
        for (String a:hSet) {
            System.out.println(a);
        }

        //contains
        System.out.println("Contains "+ hSet.contains("Zehra Çakır"));

        //clear
        hSet.clear();
        System.out.println("***Then clear***");
        for (String a:hSet) {
            System.out.println(a);
        }

    }
}
```

### HashSet Class

- The objects that we insert into the HashSet do not guarantee to be inserted in the same order. The objects are inserted based on their hashcode.
- This class also allows the insertion of NULL elements.

### LinkedHashSet Class

- It is an ordered version of HashSet that keeps a doubly linked List among all elements. This class is used when iteration order needs to be maintained.
- While iterating over a HashSet, the order is unpredictable, LinkedHashSet allows us to iterate over the elements in the order in which they were added.

### TreeSet Class

- It behaves like a simple set, except that it stores the elements in a sorted format. TreeSet uses a tree data structure for storage. Objects are stored in sequential, ascending order.
- However, we can iterate in descending order using the TreeSet.descendingIterator() method.

```java
//Comparator: Provides the ability to sort objects by multiple data members
@Override
public int compare(Student o1,Student o2){
	return 0;
}

//Comparable: The compareTo() method compares two strings lexicographically.
@Override 
public int compareTo(Object o1){
	return this.age-((Employee)o).age;
}
```

## LIST INTERFACE

- Provides a way to store the ordered collection.
- It is an ordered collection of objects where duplicate values can be stored.
- Because the list preserves the order of insertion, it allows positional access and insertion of items.
- Duplicate or null-valued elements can be kept in classes that inherit from the List interface.
- **Declaration:** The List interface is declared as:

```java
public interface List<E> extends Collection<E> ;
```

- Example

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class ListClass {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();

        //add
        list.add(10);
        list.add(20);
        list.add(30);
        list.add(40);
        list.add(50);

        //Iterator
        System.out.println("***With Iterator***");
        Iterator<Integer> iterator = list.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }

        //get(int index)
        System.out.println("get(): " + list.get(3));

        //indexOf(Object)
        System.out.println("indexOf(): " + list.indexOf(50));

        //remove(int index)
        System.out.println("remove(): " + list.remove(2));
        //Let's print the list to see the change made with remove()
        for (Integer a : list) {
            System.out.println(a);
        }

        //set(int index,Object element)
        System.out.println("set(): " + list.set(2, 100));
        //Let's print the list to see the change made with set()
        for (Integer a : list) {
            System.out.println(a);
        }

        //subList(int fromIndex,int toIndex)
        System.out.println("New List");
        List<Integer> list2 = list.subList(1, 3);
        for (Integer b : list2) {
            System.out.println(b);
        }
    }
}
```

### ArrayList CLass

- It stores list data using dynamic arrays.
- Default size is 10. If the size is not enough, a new array is defined at runtime, which is twice the size of the existing array. Elements in the old array are transferred to the new array, preserving their indices.

✴️ ArrayList is preferred for storing and accessing data.

✴️ It is necessary to scroll the list when insert and delete operations are done, which degrades performance.

✴️ It is not a safe thread, it breaks data integrity.

### LinkedList Class

![linked-list.png](https://github.com/zehracakir/CollectionAndMapInterfaceJava/blob/main/linked-list.png)

- It is a linear data structure where the elements are not stored in contiguous locations and each element is a separate object with a data part and an address part.
- Elements are linked using pointers and addresses. Each element is known as a node.
- They are preferred over arrays because of the dynamism and ease of insertion and deletion.

### Vector Class

- Vector implements a dynamic array meaning it can grow or shrink as needed. Like an array, it contains components that can be accessed using an integer index.
- It is synchronized, this feature increases reliability. So it is slower than ArrayList.

### **Queue LinkedList Class**

- Queue is a FIFO (first-in-first-out) structure.
- The item that comes out first is at the beginning of the queue; It is retrieved with the remove() or poll() method.
- element(): Returns the item at the beginning of the queue, but does not remove it from the queue.
- add(eleman): Adds the element given in the parameter to the queue. It throws an error if the operation fails.
- offer(eleman): Adds the element given in the parameter to the queue. Returns null if the operation fails.
- poll(): Removes the element at the beginning of the queue from the queue.
- peek(): It is used to reach the next element in the queue.

### **Priority Queue Class**

- There is a FIFO structure, but this structure cannot solve all the possibilities that will be encountered. Thus, there is a need for a structure that orders the elements of the collection according to the desired priority.
- In a PriorityQueue queue, items are either in their natural order or in the order in which the Comparator is used at installation time. Of course, this depends on which constructor is used. Null items cannot be placed in a PriorityQueue queue. An object that is incompatible (not comparable) with its elements cannot be put in a PriorityQueue queue in its natural order. Doing so will throw a ClassCastException from the compiler.

## Map Interface

- Map Interface is one of its concrete classes. The HashMap class can also be called a mixed match. It is very effective in adding and removing elements to the mapping table and in finding the element whose key is given in the table.
- Classes using the Map Interface have the following methods:
- clear(): It deletes all the values found in the map.
- containsKey(Object key): Queries whether a certain key has already been entered.
- containsValue(Object value): Queries whether a certain object has been entered before.
- get(Object key): Returns the object corresponding to the key.
- put (Object key, Object value): Registers the key-value pair.
- remove (Object key): Deletes the value corresponding to a certain key.
- size(): Returns the key-value binary number registered up to that time.
- Example

```java
import java.util.HashMap;
import java.util.Map;

public class MapClass {
    public static void main(String[] args) {
        Map<String, String> mapTest = new HashMap<String, String>();

        //put(Key,Value)
        mapTest.put("Beşiktaş", "BJK");
        mapTest.put("Fenerbagçe", "FB");
        mapTest.put("Galatasaray", "GS");
        mapTest.put("Trabzonspor", "TS");

        for (Map.Entry<String, String> a : mapTest.entrySet()) {
            System.out.print(a.getKey() + ":");
            System.out.println(a.getValue());
        }

    }
}
```

### HashMap Class

- It stores data in pairs (Key, Value) and you can access them with an index of another type (for example, an Integer).
- It allows storing null keys as well, but there must only be one null key object and can be any number of nulls.
- This class makes no guarantees regarding the order of the map.

### **LinkedHasMap Class**

- LinkedHashMap contains key based values. It implements the Map interface and extends the HashMap class.
- It contains only unique items.
- It can have one null key and multiple null values.
- It's out of sync.
- It is the same as HashMap with an additional feature that it preserves the insertion order. For example, when we run the code with a HashMap, we get a different order of elements.

### TreeMap Class

- This class is a member of the Java Collections Framework.
- The class implements the Map interfaces including NavigableMap , SortedMap and extends the AbstractMap class.
- TreeMap in Java does not allow null keys (like Map) and therefore a NullPointerException is thrown. However, multiple null values can be associated with different keys.
- The input pairs and views returned by the methods in this class represent snapshots of the mappings at the time they were generated. They do not support the Entry.setValue method.
