---
title: "method not working in java"
date: 2012-10-30
forum: Programming Talk
---

### Post by Mia_tech on 2012-10-30
guys, the toArray method is not working, could someone tell me why
Thanks

```
package com.javablackbelt.utils;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class ListUtils {
	
	public static void main(String arg[]) {
		String[] arr = {"one", "two", "three", "four", "five"};
		ArrayUtils.print(arr);
		
		System.out.println();
		
		String [] reversedArr = ArrayUtils.reverse(arr);
		ArrayUtils.print(reversedArr);
		
		System.out.println();
		
		ArrayList<String> list = ArrayUtils.toArrayList(arr);
		ListUtils.print(list);		
		
		ArrayList<String> reversedList = ListUtils.reverse(list);
		ListUtils.print(reversedList);
		
		String[] arrFromList = ListUtils.toArray(list);
		//ArrayUtils.print(arrFromList);
		
	}
	
	public static void print(ArrayList<String> aStr) {
		System.out.print("list: [ ");
		for(String l: aStr)
			System.out.print(l+" ");
		System.out.println(" ] size: "+aStr.size());
	}
	
	public static ArrayList<String> reverse(ArrayList<String> aList) {
		ArrayList<String> newList = aList;
		
		Collections.reverse(newList);
		return newList;
	}
	
	public static String[] toArray(ArrayList<String> list) {
		ArrayList<String> newList = list;
		String[] newStr = (String[]) newList.toArray();
		
		return newStr;
	}

}
```

---

### Post by KdotJ on 2012-10-30
Firstly, to understand this you should read up a little on generics in Java. While the List API does offer the method you have shown, it returns an array of type Object. I suggest you use the method explained [)"]here]("http://docs.oracle.com/javase/6/docs/api/java/util/List.html#toArray(T[) instead.

You would need something more like this:

```

public static String[] toArray(ArrayList<String> list) {
    ArrayList<String> newList = list;
    String[] newStr = newList.toArray(new String[newList.size()]);
		
    return newStr;
}

```

---

