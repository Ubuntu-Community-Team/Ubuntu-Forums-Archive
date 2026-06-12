---
title: "Java problem"
date: 2009-10-27
forum: Programming Talk
---

### Post by dwally89 on 2009-10-27
Hi,

I am currently trying to complete an assign for university and am coming up with a problem whilst writing the following code:

```
package ex5;
public class Ex5SelectionSort {
    // main, sort, findIndexOfNextSmallest, and arrayPrint
    public static void main(String[] args){

    }
    public static void sort(double toBeSorted[]){ 
        for (int i=0; i<toBeSorted.length; i++){
            findIndexOfNextSmallest(toBeSorted[], i);
        }
    }
    public static int findIndexOfNextSmallest(double unsorted[], int startIndex){
        int minimum=0;
        int i=startIndex;
        while (i<unsorted.length){
            if ((i+1)<unsorted.length){
                if (unsorted[i]<unsorted[i+1] && unsorted[i]<minimum){
                    minimum=i;
                }
            }
            i++;
        }
        return minimum;
    }    
}
```

The line ```
findIndexOfNextSmallest(toBeSorted[], i);
``` is giving me the error > cannot find symbol
symbol: class toBeSorted
location: class ex5.Ex5SelectionSort

unexpected type
required: value
found: class

'.class' expected

Anyone know what the problem is?

Thanks

---

### Post by shae on 2009-10-27
I think posting a simple case will help you out with your problems passing arrays.

[PHP]class Test
{
	public static void printArray(double[] array)
	{
		for(double num : array)
			System.out.println(num);
	}

	public static void main(String[] args)
	{
		double[] nums = { 1.0, 2.0, 3.0, 4.0, 5.0 };

		printArray(nums);
	}
}[/PHP]

---

### Post by muntasir_120 on 2009-10-27
In passing an array as an argument to another method, is the '[]' after its name required? Please consult your Java book.

---

### Post by doas777 on 2009-10-27
don't include the '[]' in your argument, but you do need them in the parameter (but I would put them at the end of double rather than after the var name).

---

### Post by dwally89 on 2009-10-27
Solved. Thanks.

---

