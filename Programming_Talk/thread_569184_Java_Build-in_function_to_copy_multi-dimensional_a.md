---
title: "Java Build-in function to copy multi-dimensional array?"
date: 2007-10-06
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-10-06
Best answer I can find is this:

```

public void multiArrayCopy(int[][] source,int[][] destination)
	{
	for (int a=0;a<source.length;a++)
		{
		System.arraycopy(source[a],0,destination[a],0,source[a].length);
		}
	}

```


(Copied from [http://forum.java.sun.com/thread.jspa?threadID=641756&messageID=3780724](http://forum.java.sun.com/thread.jspa?threadID=641756&messageID=3780724))

Does anyone know of a built-in java one-liner to copy a multi-dimensional array of primitives similar to the method above?

Also, anyone know of a way to initialize all elements of an array (single or multi-dimensional) to a given value?

---

### Post by Ramses de Norre on 2007-10-07
Pretty simple:
```
public void multiArrayCopy(int[][] source,int[][] destination)
{
    destination=source.clone();
}
```
And some in depth information about arraycopy vs clone can be found [here](http://www.javaspecialists.eu/archive/Issue124.html).

---

### Post by broken thumb on 2009-03-20
Calling "Object.clone()" on a multidimensional array will only give you
a new reference to the same arrays.  To see this, try the following code.

public class array {
public static void main(String[] args)
{
int array[][] = new int[3][3];
int newarray[][] = array.clone();
newarray[1][1]=400;
System.out.println(array[1][1]);
}
}

The original posting works correctly.

---

