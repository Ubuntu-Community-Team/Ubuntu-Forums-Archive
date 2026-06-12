---
title: "can this be done with label in java....."
date: 2009-08-17
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-17
i was just trying to use jump with a condition, as java wont allow to use variables after a loop/indent, 
here the loop needs to execute till both integers are same......
```

import java.util.Random;

public class equal {
	public static void main(String[] args) {
		 
		Random rand=new Random();
		Label l1;
		
		l1:int n1=rand.nextInt()%10;
		int n2=rand.nextInt()%10;
		
		System.out.println(n1==n2);
		System.out.println(n1!=n2);
		if(n1!=n2) Jump l1; // can i make jump to l1??
		
	}
}


```
really i don't know its correct, how to do it, i tried do while also, but since no goto is allowed in java,
please tell how to do this?

---

### Post by jespdj on 2009-08-17
Your code is not valid Java code.

You can define labels that you can use in a **break** or **continue** statement, but labels are not some kind of objects or variables. The line "Label l1;" is strange and does not have anything to do with the "l1:" label.

There is no **goto** statement in Java (goto is a reserved word, but it is not a valid keyword), so you cannot directly jump to a labeled line. There's a good reason why there is no goto - it makes it too easy to write [spaghetti code](http://en.wikipedia.org/wiki/Spaghetti_code).

Forget about trying to use line labels (you rarely need them) and goto-like jumps. Instead, use a while or for loop. See [Control Flow Statements](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/flow.html) in Sun's Java tutorials.

---

### Post by abhilashm86 on 2009-08-17
> **jespdj said:**
> Your code is not valid Java code.

Forget about trying to use line labels (you rarely need them) and goto-like jumps. Instead, use a while or for loop. See [Control Flow Statements](http://java.sun.com/docs/books/tutorial/java/nutsandbolts/flow.html) in Sun's Java tutorials.

oh its fine, i'm new to java and its no java code!!, yes i tried with do while, worked fine.......
so how do u access a variable of int n1, n2 after the loop? i think the validity of int n1,n2 is just inside the loop......

---

### Post by jespdj on 2009-08-17
> **abhilashm86 said:**
> so how do u access a variable of int n1, n2 after the loop?
Declare the variables outside the loop. Something like this:
```
int n1 = 0;
int n2 = 0;

// The loop
for (...) {
  // ...
}

System.out.println(n1);
```

---

### Post by abhilashm86 on 2009-08-17
just altered using do-while, hmm will see now whats use of labels!!
```
import java.util.Random;

public class equal {
	public static void main(String[] args) {
		 
		Random rand=new Random();
		int n1=10,n2=30;
		do {
			System.out.println(n1==n2);
			System.out.println(n1!=n2);
		}while((n1=rand.nextInt()%5)!=(n2=rand.nextInt()%5));
		
	}			
}
```
thanks for your help:)

---

