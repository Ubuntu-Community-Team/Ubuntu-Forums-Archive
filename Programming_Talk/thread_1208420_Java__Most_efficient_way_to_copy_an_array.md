---
title: "Java:  Most efficient way to copy an array?"
date: 2009-07-09
forum: Programming Talk
---

### Post by Igniteflow on 2009-07-09
Hi, 
I have a method which works which is the following:

[PHP]
for ( int i = 0 ; i < x.length; i++ ) {
			y[i] = x[i];
		}
[/PHP]

x and y are int[]'s.  I was wondering if this is the most efficient method for making a copy of an array?  No particularly urgent reason, just want to start working on improving my code now, rather than going for "just works". Thanks in advance

---

### Post by smartbei on 2009-07-09
How about:
```

y = x.clone()

```
See: [http://www.javapractices.com/topic/TopicAction.do?Id=3](http://www.javapractices.com/topic/TopicAction.do?Id=3) for more information (has timings as well).

---

### Post by baizon on 2009-07-09
The most efficient way is "arraycopy()".
Documentation: [http://java.sun.com/j2se/1.4.2/docs/api/java/lang/System.html#arraycopy%28java.lang.Object,%20int,%20java.lang.Object,%20int,%20int%29]("http://java.sun.com/j2se/1.4.2/docs/api/java/lang/System.html#arraycopy%28java.lang.Object,%20int,%20java.lang.Object,%20int,%20int%29")

An example:
```

public class MyClass {
  public static void main(String[] args) {
    int[] array = {0,1,2,3,4};
    int[]  copy = {0,0,0,0,0};
		
    System.arraycopy(array,1,copy,1,3);
  }
}

```

---

### Post by froggyswamp on 2009-07-09
For very big loops/arrays there's no difference cause Java's first priority is to determine huge loops and optimize the hell out of them. In smaller loops (under several million - the majority of cases) I'd use System.arraycopy cause it's already "optimized" the very first time you use it (unlike a normal loop-n-copy solution), an example, using a 500000 long array of ints, the output is mostly this even after multiple runs:

```

useSystemCall done in: 1
useLoop done in: 16
useSystemCall done in: 1
useLoop done in: 1
useSystemCall done in: 1
useLoop done in: 1

```As seen above, the difference is in the 1st run: System.arraycopy is already optimized, while the loop solution yields worse results, next time though it's as fast as the System.arraycopy solution.

Much bigger arrays are 100% optimized so there's no difference in the 1st run.
The test code I used:
```

public class Main {
    private static final int MAX = 500000;
    private int[] src;
    private int[] dest;

    public static void main(String[] args) {
        new Main();
    }

    public Main() {
        src = new int[MAX];
        dest = new int[MAX];

        //init source array
        for(int i : src) {
            src[i] = i;
        }

        useSystemCall();
        useLoop();

        useSystemCall();
        useLoop();
        
        useSystemCall();
        useLoop();
    }

    private void useSystemCall() {
        long lStart = System.currentTimeMillis();

        System.arraycopy(src, 0, dest, 0, src.length);

        System.out.println( "useSystemCall done in: " + (System.currentTimeMillis() - lStart) );
    }

    private void useLoop() {
        long lStart = System.currentTimeMillis();

        for(int i=src.length-1; i>=0; i--) {
            dest[i] = src[i];
        }

        System.out.println( "useLoop done in: " + (System.currentTimeMillis() - lStart) );
    }

}

```Using System.arraycopy you have to write less code and it works slightly faster on 1st run in the majority of cases.

---

### Post by Igniteflow on 2009-07-11
Thanks everyone, will take that on board

---

### Post by NovaAesa on 2009-07-11
You could also try using the Arrays class (java.util.Arrays). It has heaps of static methods allowing copying of arrays (either the whole array, or only a part of it), sorting arrays, binary search on arrays, filling arrays, etc etc.

I don't know how it goes performance wise, but it comes with the inbuilt libraries, so I would assume that it is an optimal implementation.

EDIT: here's a link [http://java.sun.com/javase/6/docs/api/java/util/Arrays.html](http://java.sun.com/javase/6/docs/api/java/util/Arrays.html)

---

