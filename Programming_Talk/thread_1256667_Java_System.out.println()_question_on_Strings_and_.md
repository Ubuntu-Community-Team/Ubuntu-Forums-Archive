---
title: "Java System.out.println() question on Strings and numbers"
date: 2009-09-02
forum: Programming Talk
---

### Post by s3a on 2009-09-02
[I]import java.util.Scanner;

public class Eight

{

public static void main (String [] args)

	{
	
		Scanner kb;
		
		kb = new Scanner(System.in);
		
		//ANALYZE THIS FURTHER!!!!
		
		System.out.println(1 + 2 + 3 + 4);
		System.out.println("1 + 2" + 3 + 4);
		System.out.println("1 + 2" + (3 + 4));
		System.out.println(1 + "2 + 3" + 4);
		System.out.println("(1 + 2)" + 3 * 4);
		
	}
		
}[/I]

Can someone explain what is going on with those numbers because the output is not what I expected it to be.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by Finalfantasykid on 2009-09-02
I'm not sure what the question is, but I think the correct output based on that code is...

```

[I]10
1 + 234
1 + 27
12 + 34
(1 + 2)12[/I]

```

I could be wrong, as some of those are tricky, and I'm not good with tricks :P

But with Strings, the + operator acts the same way as the concat() method.  So for example...

"Hello ".concat("World");

is equivalent to

"Hello " + "World";

EDIT:  I was wrong with a couple of those outputs.  I have corrected my original output, now it is correct.

---

### Post by baizon on 2009-09-03
```
System.out.println(1 + 2 + 3 + 4);
```
Adding 1+2+3+4 
Result: 10

```
System.out.println("1 + 2" + 3 + 4);
```
Appending string and numbers.
Result: 1 + 2*34*

```
System.out.println("1 + 2" + (3 + 4));
```
Appending string and added numbers (because there are in a bracket and so they have higher priority).
Result: 1 + 2*7* 

```
System.out.println(1 + "2 + 3" + 4);
```
Appending a number with string and with a number again.
Result: *1*2 + 3*4*

```
System.out.println("(1 + 2)" + 3 * 4);
```
Appending string and added numbers (because multiplication have a higher priority)
Result: (1 + 2)*12* 

I hope that helps.

---

