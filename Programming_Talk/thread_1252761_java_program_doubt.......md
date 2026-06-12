---
title: "java program doubt......"
date: 2009-08-29
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-29
here is just starting of code, where random numbers are genrated and then sorted and searched, 
should i use methods here? the array a getting created via random generator is out of scope!! and i can't use it after for loop?
how to do this without calling methods and just finish in main....
```

public class sorta {
	public static void main(String[] args) {
		Random rand=new Random();
		int []a;
		for(int i=0;i<9;i++) {
			a=new int [] {rand.nextInt()};
			}
		
		System.out.println("before sorting");
		for(int j=0;j<a.length;j++) {
				System.out.println(a[j]);
		}
	}

}
```

---

### Post by exutable on 2009-08-29
> **abhilashm86 said:**
> here is just starting of code, where random numbers are genrated and then sorted and searched, 
should i use methods here? the array a getting created via random generator is out of scope!! and i can't use it after for loop?
how to do this without calling methods and just finish in main....
```

public class sorta {
	public static void main(String[] args) {
		Random rand=new Random();
		int []a;
		for(int i=0;i<9;i++) {
			a=new int [] {rand.nextInt()};
			}
		
		System.out.println("before sorting");
		for(int j=0;j<a.length;j++) {
				System.out.println(a[j]);
		}
	}

}
```

Well I don't know if this is it, but you definitely need to make sure that the loop iterates through a.length-1 because a.length is out of the array's index.  Remember that counting in programming starts at 0

---

### Post by baizon on 2009-08-29
Hi,
you will get a compiling error "The local variable a may not have been initialized line 13"

So you need to change it to...
```

public class sorta {
	public static void main(String[] args) {
		Random rand=new Random();
		int []a = new int[9];
		for(int i=0;i<9;i++) {
			a[i]= rand.nextInt();
			}
		
		System.out.println("before sorting");
		for(int j=0;j<a.length;j++) {
				System.out.println(a[j]);
		}
	}
}
```
Now it will work fine.

---

### Post by abhilashm86 on 2009-08-30
yes thanks baizon
can anyone tell how exactly to use sort function call in java? i tried and then used search function, but have a look at output, onr element is missing? I could'nt figure out the error..........```
import java.util.Arrays;
import java.util.Random;
public class sorta {
	public static void main(String[] args) {
		Random rand=new Random();
		int []a=new int[9];
		
		for(int i=0;i<a.length-1;i++) {
			a[i]=rand.nextInt() %10;
		}
		
		
		System.out.println("before sorting");
			for(int j=0;j<a.length-1;j++) {
			System.out.print(" " +a[j]+ " ");
		}
		
		Arrays.sort(a);
			
		System.out.println("after sorting");
			for(int j=0;j<a.length-1;j++) {
			System.out.print(" " +a[j]+ " ");
		}
		int flag = 0;
		int key=5,k = 0;
		for(int j=0;j<a.length-1;j++) {
				k=Arrays.binarySearch(a,key);
				if(k==j)
				{
					System.out.println("key found at "+k+" position");
					flag=1;
				}
			}
		if(flag!=1)
		{
			System.out.println("key not found");
		}
	}
}


```

here is output 
```
before sorting
 -2  0  9  5  -9  2  0  3 after sorting
 -9  -2  0  0  0  2  3  5 key found at 7 position
```
as you can see 9 is not shown in sorted array??

---

### Post by Ragazzo on 2009-08-30
The for-loop doesn't iterate to the last item because of -1 in there.

The correct form is: 
```

for(int j=0;**j<a.length**;j++)

```

---

### Post by baizon on 2009-08-30
Yes, Ragazzo is right (and exutable was wrong). So you iterate from 0-a.length-1 which is 8, but you have 9 array positions.
That's tricky so always look out at this point ;)

Edit: So you have to change everywhere a.length-1 to _a.length_!

```

import java.util.Arrays;
import java.util.Random;

public class test {
	public static void main(String[] args) {
		Random rand=new Random();
		int []a=new int[9];
		
		for(int i=0;i<a.length;i++) {
			a[i]=rand.nextInt() %10;
		}
		
		
		System.out.println("before sorting");
			for(int j=0;j<a.length;j++) {
			System.out.print(" " +a[j]+ " ");
		}
		
		Arrays.sort(a);
			
		System.out.println("after sorting");
			for(int j=0;j<a.length;j++) {
			System.out.print(" " +a[j]+ " ");
		}
		int flag = 0;
		int key=5,k = 0;
		for(int j=0;j<a.length;j++) {
				k=Arrays.binarySearch(a,key);
				if(k==j)
				{
					System.out.println("key found at "+k+" position");
					flag=1;
				}
			}
		if(flag!=1)
		{
			System.out.println("key not found");
		}
	}

}

```

```

before sorting
 2  0  5  7  -7  -7  0  -4  5 after sorting
 -7  -7  -4  0  0  2  5  5  7 key found at 6 position

```

---

### Post by exutable on 2009-08-30
my bad, ****** up coach

---

### Post by abhilashm86 on 2009-08-30
> **exutable said:**
> my bad, ****** up coach

whats that mean?? kinda din't get you!!

---

