
<div id="top"></div>

<div align="center"> <h1> Welcome to the Java DSA repository!🔥 </h1>  <div>

<p>
	<br>
</p>  
	
## *Data-Structure Topics:*

   * [Arrays and ArrayLists](#arrays-and-arraylists)
   * [LinkedLists](#linkedlists)
   * [Stacks and Queues](#stacks-and-queues)
   * [Sets](#sets)
   * [Maps](#maps)
   * [Tree Data Structure](#trees)
  
# *Arrays and ArrayLists:*

## Most Basic types of array declaration:

data-type varName[size];

OR

data-type[size] varName;

------------------------------------------------------------------------------------------------------------------------------

## Initializing an array


int[] arr = new int[size];

OR

int[] arr = {0,1,2,3,4,5,6,7,8,9};


------------------------------------------------------------------------------------------------------------------------------

## Most common methods to find the size or length of an array

`arr.length` -> for calculating the length of all types of array (int[], String[], char[])

`arr.size()` -> for calculating the size of an object array(Ex. List array as it stores only objects)

---------------------------------------------------------------------------------------------

## Point to remember

`.length` -> It is used for calculating the length of all types of array (int[], String[], char[])

`.length()` -> It is used for calculating the length of a String

------------------------------------------------------------------------------------------------------------------------------

### `Array and List declarations:`  

```java
/*---- General ways of creating int and String arrays ----*/


int[] intArray1 = new int[10];                /*-- Array size should be provided --*/                             

int[] intArray2 = {0,1,2,3,4,5,6,7,8,9};      /*-- Also a valid declaration --*/

int intArray3[] = new int[10];                /*-- Another valid declaration --*/

int intArray4[] = {0,1,2,3,4,5,6,7,8,9};      /*-- Another valid declaration --*/

String[] stringArray1 = new String[5];

String[] stringArray2 = {"Hello", "Hello", "Hello", "Hello", "Hello"};




/*---- Creating Lists for Integer objects ----*/


List<Integer> list1 = new ArrayList<Integer>();                 /*-- Empty List, List size not required --*/

List<Integer> list2 = new ArrayList<>();                        /*-- Valid declaration, List size not required --*/

List<Integer> list3 = new ArrayList<Integer>(new Integer(100)); /*-- Integer object 100 as first element --*/

List<Integer> list4 = new ArrayList<>(new Integer(120));        /*-- Integer object 120 as first element --*/

List<Integer> list5 = new ArrayList<Integer>(130);              /*-- Integer object 130 as first element --*/




/*---- Creating Lists for String objects ----*/

/*-- We use Arrays.asList(String[] s) and (listName).toArray(String[] s) for dealing with Lists and String arrays--*/


List<String> list6 = new ArrayList<String>(Arrays.asList(new String("Hello"))); /*-- Valid declaration for String --*/

List<String> list7 = new ArrayList<>(Arrays.asList(new String("Hello")));       /*-- Valid declaration for String --*/

List<String> list8 = new ArrayList<> (Arrays.asList("Hello", "Hi"));            /*-- Adding two elements in the list --*/

List<String> list9 = new ArrayList<> (Arrays.asList(stringArray2));             /*-- Passing a String array in the asList method --*/       


/*---- Referencing ----*/


int[] intArray5 = new int[10];     

int[] intArray6 = intArray5;             

List<String> list10 = new ArrayList<>();

List<String> list11 = list10;            

```

---------------------------------------------------------------------------------------------
</br>

### `Converting List<Integer> into int[] (until Java 7):`

```java
public class Test {

    public static void main(String[] args) {

        List<Integer> list = new ArrayList<Integer>();
        list.add(1);
        list.add(2);

        int[] intArray = new int[list.size()];

        for(int i=0; i<list.size(); i++){

            intArray[i] = list.get(i); /* Auto-unboxing from Integer -> int */

        }

    }

}

```

</br>

### `Converting List<Integer> into int[] (Java 8):`

```java
public class Test {

    public static void main(String[] args) {

        List<Integer> list = new ArrayList<Integer>();
        list.add(1);
        list.add(2);

        int[] intArray = list.stream().mapToInt(i->i).toArray();

    }

}
```

</br>

### `Converting int[] into List<Integer>:`

```java
public class Test {

    public static void main(String[] args) {

        int[] intArray = {1,2,3,4,5,6,7};

        List<Integer> list = new ArrayList<Integer>();

        for(int i : intArray){

            list.add(i);   /* Auto-boxing from int -> Integer */

        }

    }

}

```

</br>

### `Converting List<String> into String[]:`

```java
public class Test {

    public static void main(String[] args) {

        List<String> list = new ArrayList<String>();
        list.add("Item 1");
        list.add("Item 2");
        list.add("Item 3");
        list.add("Item 4");

        String[] stringArray = new String[list.size()];
        stringArray = list.toArray(stringArray);       

        }

}

```

</br>

### `Converting String[] into List<String>:`

```java

public class Test {

    public static void main(String[] args) {

        String[] stringArray = {"Hello", "Hi", "Whats up"};
        List<String> list = Arrays.asList(stringArray);    

        for(int i=0; i<list.size(); i++){
            System.out.println(list.get(i));
        }

        /* Enhanced for loop can also be used for printing the elements of the list */
        for(String s : list){
            System.out.println(s);
        }

    }

}

```
</br>

### `Overview of char[] and List<Character> (Optional read):`

```java
public class Test {

    public static void main(String[] args){

        String name = "A Character String";
        /*---- Note: char is a data type and Character is the wrapper class ----*/
        char[] nameArray = name.toCharArray(); /*---- Character Array Declaration ----*/


        List<Character> list = new ArrayList<>(); /*---- List of Character objects ----*/
        list.add('a');
        list.add('b');

        StringBuilder sb = new StringBuilder();

        /*-- Now adding elements to String Builder from Character list--*/
        /*--- NOTE: This method for printing elements works for Integers, Strings and Character lists---*/
        for(char ch : list){
            sb.append(ch);
        }

    }

}
```

</br>

### `Two Dimensional (2D) Array declaration:`

```java
public class Test {

    public static void main(String[] args){

            ArrayList<ArrayList<Integer>> rows = new ArrayList<>();

            for(int i=0; i<5; i++){
                ArrayList<Integer> row = new ArrayList<>();
                for(int j=0; j<5; j++){
                    row.add(j*j);
                }
                rows.add(row);
            }

            for(int i=0; i<5; i++){
                for(int j=0; j<5; j++){
                    System.out.print(rows.get(i).get(j)+" ");
                }
                System.out.println("");
            }

    }

}

```

#### `Common ArrayList Operations:`

| SN | Operation | Method | Time Complexity |
| :---: | :---: | :---: | :---: |
| 01 | Adding an element to the ArrayList | `add(T element)` | O(1) |
| 02 | Setting an element to the ArrayList at a particular index | `set(int index, T element)` | O(1) |
| 03 | Return an element of the ArrayList using Index | `T get(int index)` | O(1) |
| 04 | Getting the size of the ArrayList | `int size()` | O(1) |
| 05 | Removing an element from a particular index in the ArrayList | `remove(int index)` | O(n) |
| 06 | Sorting an ArrayList | `Collections.sort(List list)` | O(nlog(n)) |



