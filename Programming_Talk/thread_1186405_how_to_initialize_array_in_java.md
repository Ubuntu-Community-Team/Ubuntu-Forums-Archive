---
title: "how to initialize array in java??"
date: 2009-06-13
forum: Programming Talk
---

### Post by abhilashm86 on 2009-06-13
i was just started with java, here in player class, i want to initialize play integer variable a, so i tried different ways to pass arguements to initialize array, 
so how to do initialize??
[PHP]public class play {
	int a[];
	int display(int size)
	{
		for(int i=0;i<size;i++)
			System.out.println(+a[i]);
	}
}

class player {
	public static void main(String args[]) {
		play abc=new play();
		abc.a={1,2,3,4,5,6,7,8,9,10}; // upto 10 
		abc.display(10);
		
	}
}[/PHP]
which is easiest method to initialize by passing array?

---

### Post by Zugzwang on 2009-06-13
Your question is hard to understand, maybe you are searching for something like the "arraycopy" function?

[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/System.html#arraycopy(java.lang.Object,%20int,%20java.lang.Object,%20int,%20int](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/System.html#arraycopy(java.lang.Object,%20int,%20java.lang.Object,%20int,%20int)

Also, for such fundamental questions, consider diving into the Java Tutorials ([http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)) for answers.

---

### Post by abhilashm86 on 2009-06-13
should we really use copyarray?? Well in c++ and c, we can pass it through functions right, 
so is it hard to pass values between classes, is there any other method to initialize??

---

### Post by Ariel David Moya Sequeira on 2009-06-13
As far as I understood the original question, you want to initialize a "play" object with "a" equal to the array {1, 2, ..., 10} (called from "player"). 

First of all, you need a *constructor* for "play". This is achieved by declaring a method named exactly as the class:
[php]public class play {
    private int[] a;

    public play(int[] anArray) {
        
    }
}[/php]

After that, you can assign "anArray" to "a" inside the constructor:
[php]public class play {
    private int[] a;

    public play(int[] anArray) {
         a = anArray;
    }
}[/php]

Finally, you can type down the rest of the class methods. The "display" method can return *void* if it doesn't need to return anything (like when you want to print something). Also, you can get the array's size by using the *length* attribute of the array:
[php]public class play {
     private int[] a;
 
     public play(int[] anArray) {
          a = anArray;    // Initialized by reference
     }

    public void display() {
        for (int index = 0; index < a.length; index++) {
            System.out.println(a[index])
        }
    }

 }[/php]

To make a new "play" object, you just have to use:
[PHP]play abc = new play({0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10});[/PHP]

If the above code doesn't work, then try:
[PHP]play abc = new play( (int[]) {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10} );[/PHP]

---

### Post by abhilashm86 on 2009-06-13
> **Ariel David Moya Sequeira said:**
> 

To make a new "play" object, you just have to use:
[PHP]play abc = new play({0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10});[/PHP]

If the above code doesn't work, then try:
[PHP]play abc = new play( (int[]) {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10} );[/PHP]

yes thanks a lot, well both the arrays we passed is not recieved by class, the error says,
play abc = new play({0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10});  
cannot convert int to play(class)
play abc = new play( (int[]) {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10} ); 
constructor play(int[],int ,int.......)is undefined

so maybe its better to use copyarray, i'll try and see

---

### Post by Ariel David Moya Sequeira on 2009-06-13
If that didn't work, then I'd try using:
[PHP]int[] anArray = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
play abc = new play(anArray);[/PHP]
Sorry, I'm working in something else right now, so I don't have a chance to test the examples I give right now. Add the fact I never used the direct initialization of an array before, so this question made me investigate a little bit; thanks for posting!

---

### Post by abhilashm86 on 2009-06-13
> **Ariel David Moya Sequeira said:**
> If that didn't work, then I'd try using:
[PHP]int[] anArray = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
play abc = new play(anArray);[/PHP]
Sorry, I'm working in something else right now, so I don't have a chance to test the examples I give right now. Add the fact I never used the direct initialization of an array before, so this question made me investigate a little bit; thanks for posting!

this is so meaning full :) it worked, thanks  a lot............

---

### Post by pbrockway2 on 2009-06-13
OP: The approach you took originally is workable - but you need to create the int array properly. (Depending on context, though, using an explicit constructor may well be better)

Here's a variation with nit-picky comments.

```

    // start class names with a capital
public class Play {
    int a[];
        // (a) the method must have a return type void
        // since it doesn't return anything
        // (b) keep the brace style consistenet
    void display(int size) {
            // use braces
        for(int i=0;i<size;i++) {
            // a[i] *is* +a[i]
            // + in this context means "positive", not "concatenate"
            System.out.println(a[i]);
        }
    }
}

    // start class names with a capital
class Player {
    public static void main(String args[]) {
        Play abc = new Play();
            // abc.a must use "new" to create an int array
        abc.a = new int[] {1,2,3,4,5,6,7,8,9,10}; 
        abc.display(10);
    }
}  

```

Check out "Creating, Initializing, and Accessing an Array" in [Sun's Tutorial]("http://java.sun.com/docs/books/tutorial/java/nutsandbolts/arrays.html").

---

### Post by jespdj on 2009-06-14
Instead of this:
```
abc.a={1,2,3,4,5,6,7,8,9,10}; // upto 10
```
Do this:
```
abc.a = new int[] {1,2,3,4,5,6,7,8,9,10}; // upto 10
```

---

### Post by abhilashm86 on 2009-06-15
> **jespdj said:**
> Instead of this:
```
abc.a={1,2,3,4,5,6,7,8,9,10}; // upto 10
```
Do this:
```
abc.a = new int[] {1,2,3,4,5,6,7,8,9,10}; // upto 10
```

well i tried this initially, but it gives an error
```

abhilash@abhilash:~$ javac j12.java
j12.java:19: variable abc might not have been initialized
		abc.a =new int[] {0,1,2,3,4,5,6};
		^
1 error

```
so there is a compulsory to create a constructor(zero or parametarized) in order to initialize.........

---

