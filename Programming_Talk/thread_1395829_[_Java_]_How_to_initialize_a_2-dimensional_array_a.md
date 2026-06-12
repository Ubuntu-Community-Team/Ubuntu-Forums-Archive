---
title: "[ Java ] How to initialize a 2-dimensional array as [][] ( not [3][5] ) ?"
date: 2010-02-01
forum: Programming Talk
---

### Post by SemiBuz on 2010-02-01
```
Object tableData[][] = new Object[500][500];

```Basically, I'm using a for loop to fill an array and to do that I need to initialize it first. 
How do I initialize it as [][] ( I don't know how long it'll be .. 10 .. 100 .. 10k .. I need an array which grows, even if I add 1,000,000 elements ) ?

---

### Post by denarced on 2010-02-01
You have to go through the array with a loop and initialize each object.
You could use the same loop to set values.

edit: took some time to figure out what you meant .. it's monday I guess ..
Take a look at [http://java.sun.com/javase/6/docs/api/java/util/Vector.html]("http://java.sun.com/javase/6/docs/api/java/util/Vector.html")

---

### Post by SemiBuz on 2010-02-01
You got it right but [COLOR=Green]JTable[/COLOR] doesn't like [COLOR=Green]Vector[/COLOR] so .. the question still haven't been answered :(

---

### Post by NovaAesa on 2010-02-01
Vector has a toArray method. So you could put the things you want into a Vector, then when you have put all the objects you want into it, convert it into an array and then dispose of the vector.

> 
toArray

public <T> T[] toArray(T[] a)
Returns an array containing all of the elements in this Vector in the correct order; the runtime type of the returned array is that of the specified array. If the Vector fits in the specified array, it is returned therein. Otherwise, a new array is allocated with the runtime type of the specified array and the size of this Vector.
If the Vector fits in the specified array with room to spare (i.e., the array has more elements than the Vector), the element in the array immediately following the end of the Vector is set to null. (This is useful in determining the length of the Vector only if the caller knows that the Vector does not contain any null elements.)

Specified by:
toArray in interface Collection<E>
Specified by:
toArray in interface List<E>
Overrides:
toArray in class AbstractCollection<E>
Parameters:
a - the array into which the elements of the Vector are to be stored, if it is big enough; otherwise, a new array of the same runtime type is allocated for this purpose.
Returns:
an array containing the elements of the Vector
Throws:
ArrayStoreException - if the runtime type of a is not a supertype of the runtime type of every element in this Vector
NullPointerException - if the given array is null
Since:
1.2


---

### Post by SemiBuz on 2010-02-01
```
        Vector element = new Vector();
        Vector list = new Vector();
        
        element.add("Milk");
        element.add(0.98);
        list.add(element);
        element.clear();
        
        element.add("Bread");
        element.add(1.24);
        list.add(element);
        element.clear();
        
        [COLOR=Red]Object data[][] = list.toArray();[/COLOR]
```

```
[COLOR=Red]Type mismatch: cannot convert from Object[] to Object[][][/COLOR]
```

I'm confused ..

---

### Post by CptPicard on 2010-02-01
Deprecated Vector is Deprecated... use ArrayList instead.

---

### Post by Reiger on 2010-02-01
First of all Vector is to be avoided in the Java world. It is buggy & old; and has long since been replaced by components from the Collections framework.

Also, a Vector or an ArrayList is single dimension so the result of a toArray() call is a single dimension array; and you are assigning that result to a 2 dimensional array, hence the error message.

---

### Post by SemiBuz on 2010-02-01
> **CptPicard said:**
> Deprecated Vector is Deprecated... use ArrayList instead.

> **Reiger said:**
> First of all Vector is to be avoided in the Java world. It is buggy & old; and has long since been replaced by components from the Collections framework.

Also, a Vector or an ArrayList is single dimension so the result of a toArray() call is a single dimension array; and you are assigning that result to a 2 dimensional array, hence the error message.

So basically there's no way to create a self-growing Object array ?

** Thought about setting the array length to 32000 ( max. allowed file count in 1 folder ) - heap ..

---

### Post by Some Penguin on 2010-02-01
No.  And it's a good thing, from an efficiency perspective.

---

### Post by Habbit on 2010-02-01
Can't you create an ArrayList<Object[]>? I'm not sure array types can be used as type parameters, but you can give it a try. Make sure to call toArray with the appropiate type.

---

### Post by Some Penguin on 2010-02-01
> **SemiBuz said:**
> So basically there's no way to create a self-growing Object array ?

** Thought about setting the array length to 32000 ( max. allowed file count in 1 folder ) - heap ..

Perhaps it's easier to count the number of files actually in a directory than it is to get performance-killing extensions into the Java language specification.

---

### Post by Queue29 on 2010-02-01
Holy people in this thread need to learn what a [LinkedList]("http://java.sun.com/j2se/1.4.2/docs/api/java/util/LinkedList.html") is, Batman.

---

### Post by TennTux on 2010-02-01
> **SemiBuz said:**
> So basically there's no way to create a self-growing Object array ?

** Thought about setting the array length to 32000 ( max. allowed file count in 1 folder ) - heap ..

Break the answers here down. The short answer is no.

Given the following example```

int num = new int[3][5] ;
int other = new int[2][] ;
other[0] = new int[4] ;
other[1] = new int[3] ;
```

When Java does *new int[3][5]* it is allocating memory for 15 ints stored as 3 arrays of 5 elements. Which is why you can allocate it one part at a time as in *other*. To change the size of the *num* array the simple answer is to allocate a new larger 2d array, then copy over the old values. Which is why classes like *Vector* and *ArrayList* where created so every programmer and his brother didn't need to reinvent the wheel.

-----
On another point. It sounded like the whole point of this was that you wanted to pass a 2d array of values to *JTable*. So you would not have to go to great lengths to program a *TableModel*, or you don't yet understand *TableModel*(s).

I have some old code laying around that is derived from *AbstractTableModel* and handles most of the code for working with a *Vector* of objects. **See attached.** If you derrive a class from this class and implement the *getValueAt(...)* method and maybe the *isCellEditable(...)* and *setValueAt(...)* methods you will not have to do too much coding. Though I suspect CptPicard would suggest you modify it to use an *ArrayList*. ;)

If you do this you can use something like the following code.```

class MyTableModel extends BaseTableModel<MyDataObject> {
	private static final String[]	COLUMN_NAMES	= {"Nam", "Val"} ;
	private	static final Class<?>[]	COLUMN_TYPES	= {String.class, Integer.class} ;
	public MyTableModel(Vector<MyDataObject> data) {
		super(COLUMN_NAMES, COLUMN_TYPES, data) ;
	}
	public Object getValueAt(int rowIndex, int columnIndex) {
		MyDataObject	rowObj	= getRowValue(rowIndex) ;
		if (rowObj == null)
			return null;
		
		switch(columnIndex) {
			case 0: 	return rowObj.getName() ;
			case 1:		return rowObj.getValue() ;
			default:	return null ;
		}
	}
}

```

You would want to change the name for *MyTableModel* and provide your own data object instead of *MyDataObject*.

If this code helps good. Otherwise you can just ignore it.

---

### Post by CptPicard on 2010-02-01
Not if he needs indexing...

---

