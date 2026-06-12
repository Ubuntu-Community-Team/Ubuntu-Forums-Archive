---
title: "Java -- get height and width of a 2d array"
date: 2006-03-09
forum: Programming Talk
---

### Post by HokeyFry on 2006-03-09
how do you get the height and width of a 2 dimensional array in Java? is there something like "sampleArray.length()" for this or is it more complicated?

---

### Post by hod139 on 2006-03-09
Height and width are not clear terms, number of rows and columns is what I think you are looking for. This is how I would do it:

```

int[][] matrix = new int[20][30];
System.out.println("Number of rows = " + matrix.length);
System.out.println("Number of columns = " + matrix[0].length);

```

**Edit: **I should note that this isn't very robust.  If someone did this: 
```
int[][] matrix = new int[0][30];
```
the call to matrix[0].length would fail.

---

### Post by HokeyFry on 2006-03-09
yes height and width is what I meant. I was in a hurry while typing it and used the wrong terms.

I will try this and hope it works for what i am doing.


Also when you said it wouldn't work if you did this:

int[][] matrix = new int[0][30];

why would anyone do that? they would just make a one-dimensional array.

---

### Post by jerome bettis on 2006-03-09
2d arrays in java can be staggered, that means they can look like

xxxxxxxxx
xxxxxx
xxxxxxxxxxxx
xxxxxxxx
xxxxx
xx

and not necessarily like

xxxxxxxxx
xxxxxxxxx
xxxxxxxxx

i think you should look into using a vector of arrays, or a vector of vectors.

---

### Post by hod139 on 2006-03-09
[quote=jerome bettis]
2d arrays in java can be staggered, that means they can look like
 
 xxxxxxxxx
 xxxxxx
 xxxxxxxxxxxx
 xxxxxxxx
 xxxxx
 xx
[/quote] 
Not quite right. A two-dimensional array is an array of one-dimensional arrays. You can expect elements of rows are stored contigously, but the rows themselves may not be. If "x" is elements of my array data, and "y" is some other data, it may look like
xxxxx
yyyxxxxxyyy
xxxxxyyyyxxxxxyyyyy

> 
 i think you should look into using a vector of arrays, or a vector of vectors.
 Why? Unless you are using some hardcore numerical software that uses block-oriented algorithms the dynamic layout of rows most likely won't be a problem. In Java you can't use pointer arithmetic on arrays:
```

*address* = *baseAddress* + *elementSize* * (r**rowSize* + c) // Illegal in java

``` The only way to dereference the array is to use [], so the staggered layout won't cause problems. Another reason to use arrays, is that Vectors in Java can't take a primitive type, they can only take Objects. If you want a multi-dimensional array of ints you can use int. If you use vectors, you have to use Integer.

---

### Post by HokeyFry on 2006-03-09
i dont understand much about staggered arrays, as i have never heard of them until now. Also, using vector and arraylist (i was taught to use arraylist) is not that difficult because of the wrapper classes. Sure it is a little more work but at least you can resize the array as needed and use more than one type in one array. Although for the latter i guess you could use an Object array with a wrapper class...

---

### Post by hod139 on 2006-03-09
[quote=HokeyFry]i dont understand much about staggered arrays, as i have never heard of them until now. 
> 
The "staggering" is only the internal memory layout of the arrays.  

[quote]
Also, using vector and arraylist (i was taught to use arraylist) is not that difficult because of the wrapper classes. Sure it is a little more work but at least you can resize the array as needed and use more than one type in one array. Although for the latter i guess you could use an Object array with a wrapper class...
The big difference is that you can't use primitive types in Vectors or ArrayLists.  For large arrays the overhead with the wrappers can get prohibative.  At least with Java 1.5 the task of constantly casting the types is automated/hidden with their implementation of generics.  The cost is not gone though.

---

### Post by HokeyFry on 2006-03-09
ok the talk of arraylists and vectors has me with another question, but i dont want to start another thread. Dont worry it is still along this topic.

How do you create 2Dimensional arraylists/vectors? (ArrayList is preferred)

---

### Post by hod139 on 2006-03-09
It's possible, but it is ugly. It is probably better to define a class to store what you need, instead of forcing a list to do the job. Here is the code to do it though:

```

import java.util.*;

public class TwoDimArray{

    public static void main(String[] args){
        int[][] matrix = new int[10][30];
        System.out.println("Number of rows = " + matrix.length);
        System.out.println("Number of columns = " + matrix[0].length);

        ArrayList<ArrayList<String>> multiArrayList = new ArrayList<ArrayList<String>>();
        ArrayList<String> foo = new ArrayList<String>();
        multiArrayList.add(foo); 
        multiArrayList.get(0).add("String1");
        System.out.println("Element at (0,0) = " + multiArrayList.get(0).get(0));
    }
}

```

**edit**: This will only work on JRE1.5

---

