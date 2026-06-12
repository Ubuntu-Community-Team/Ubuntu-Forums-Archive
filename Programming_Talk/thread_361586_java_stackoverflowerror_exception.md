---
title: "java stackoverflowerror exception"
date: 2007-02-14
forum: Programming Talk
---

### Post by jordanmthomas on 2007-02-14
I am in an algorithms course at school and we are supposed to be analyzing insertion sort, quick sort, and merge sort.  Everything appeared to be going fine until I was running my final tests.

We have to sort 2^5, 2^6, 2^7, ....  2^20 elements using each method.
We have to do each of these with 
[LIST]
[*]sorted data
[*]unsorted data
[*]reverse sorted data
[/LIST]

Here's **the problem**:  when I do QuickSort on more than 2^13 (8192) elements that are already sorted java crashes and throws me a StackOverflowError Exception, which as I understand it means java thinks I am calling infinite recursions.  I am pretty sure I am not since it works on similar data of less length.

Here's **the question**:  is there a way to tell java to allow more recursions before calling it quits?
If not, would c do the same thing to me?  If not, I could pretty much port this straight to c...I would just have to read up on getting data from a file in c first.


Here's my QuickSort algorithm.  It works for unsorted data all the way up to the million items I have to sort.  It dies if I go over 8000-ish on pre-sorted data.  Maybe there's an improvement I could make?
[PHP]public static void QSort(int a, int b)
{
	if(b <= a)
	return;
	//System.out.println("going from " + a + " to " + b);
		
	
	int left = a;
	int right = b;
	
	int pivot = x[a];
	for(;;)
	{
		if(right <= left)
		break;
		
		while(left < b && x[left] < pivot)
		{
			left++;
		}
		while(right > a && x[right] >= pivot)
		{
			right--;
		}

		int temp = x[left];
		x[left] = x[right];
		x[right] = temp;
	}
	x[a] = x[right];
	x[right] = pivot;
	QSort(a,right - 1);
	QSort(right + 1, b);
}[/PHP]

---

### Post by lnostdal on 2007-02-14
it happens because you are recursing "too deep" .. that is; not necessarily infinite ("yet")

it will happen in C too

you can solve it (permanently) by iterate instead of recurse -- or if your compiler/language supports it you can make sure it does it for you: [http://en.wikipedia.org/wiki/Tail_Recursion](http://en.wikipedia.org/wiki/Tail_Recursion)

i do not know how to increase the stack-space for java (which is a somewhat temporary solution)

edit: tail-recursion in lisp: [http://www.bookshelf.jp/texi/onlisp/onlisp_3.html#SEC20](http://www.bookshelf.jp/texi/onlisp/onlisp_3.html#SEC20)

---

### Post by jordanmthomas on 2007-02-14
Yeah, I know I could change to iterative, but the assignment specifically calls for the recursive algorithm. :(

Thanks a lot for the reply though:  I will definitely read the article you linked to.

---

### Post by jordanmthomas on 2007-02-14
In case anyone else comes through I think I might have found what I was looking for:
from man java:
```
 -Xssn  Each Java thread has two stacks: one for Java code and one for C
              code.  The -Xss option sets the maximum stack size that  can  be
              used  by  C code in a thread to n.  Every thread that is spawned
              during the execution of the program passed to java has n as  its
              C stack size.  The default units for n are bytes and n must be >
              1000 bytes.

              To modify the meaning of n, append either the letter k for kilo-
              bytes or the letter m for megabytes.

       -Xmxn  Specifies the maximum size of the memory allocation pool.   This
              value  must  be  greater than 1000.  To modify the meaning of n,
              append either the letter k for kilobytes or  the  letter  m  for
              megabytes.



```
and reading this thread:
[http://forum.java.sun.com/thread.jspa?forumID=27&messageID=2164257&threadID=187774](http://forum.java.sun.com/thread.jspa?forumID=27&messageID=2164257&threadID=187774)

Maybe I will get it figured out soon.  (It's looking hopeful).

---

### Post by jordanmthomas on 2007-02-15
I was right, and just in time.
So, for anyone passing through:
I was able to stop the stack overflow by calling java like so:
```
java -Xss300M *blah*
```

---

