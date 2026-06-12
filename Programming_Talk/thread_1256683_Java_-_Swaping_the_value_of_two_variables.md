---
title: "Java - Swaping the value of two variables"
date: 2009-09-02
forum: Programming Talk
---

### Post by s3a on 2009-09-02
[I]import java.util.Scanner;

public class Seven

{
	
	public static void main (String [] args)
	
	{

	Scanner kb;
	
	System.out.print("Enter Two Integers: ");
	
	kb = new Scanner(System.in);
	
	int first = kb.nextInt();
	
	int second = kb.nextInt();
	
	System.out.println();
	
	first = second;
	second = first;
	
	//SOMETHING IS WRONG!!!!!!
	
	
	System.out.println("First = " + first + "\n" + "Second = " + second);
	
	}
	
}[/I]


_Question:_

Suppose you have two variable called first and second. Write minimal Java code to exchange
(swap) the contents of first and second. For example:
int first = 10;
int second = 17;
// ...
// your code to swap values of first and second
// ...
System.out.println(first + " " + second); // should print 17 10



I now understand why my code is wrong but I still do not see what is the correct code that I need.

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by Finalfantasykid on 2009-09-02
This sounds like it might be homework related, so I will be somewhat vague.

The problem is that you need a temporary variable whenever you do a swap operation.

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by kpkeerthi on 2009-09-03
[PHP]
int first = 10;
int second = 17;

// save first in a temp variable
int temp = first;

// now, assign second to first
first = second;

// then, assign temp (which had first's value) to second
second = temp;
[/PHP]

---

### Post by credobyte on 2009-09-03
Another solution: [http://www.hiteshagrawal.com/programming/swap-2-variable-content-without-temporary-variable](http://www.hiteshagrawal.com/programming/swap-2-variable-content-without-temporary-variable).

---

### Post by baizon on 2009-09-03
> **Finalfantasykid said:**
> This sounds like it might be homework related, so I will be somewhat vague.

The problem is that you need a temporary variable whenever you do a swap operation.

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

I think "we" are solving all his homework :)

---

### Post by credobyte on 2009-09-03
```
public static void swap(int fvar, int svar)
{
    first = svar;
    second = fvar;
}

public static void main(String args[])
{
    first = 4;
    second = 17;
    swap(first, second);
}

```

Since you know what you need to swap, this one should work.

> **baizon said:**
> I think "we" are solving all his homework :)

Nostalgia :p

---

### Post by s3a on 2009-09-03
I need the numbers to be unknown until the user inputs them and not to always be 10 and 17.

@credobyte:

What is svar and fvar? I have never heard of those two terms before. As for what kpkeerthi said, I understand that right now so thank you :) but I'm guessing the svar/fvar way puts the work on the computer instead of your brain?

And yes this is my homework, I did not know that was a "crime" but technically I will be developping for Debian/Ubuntu in the future so I'm not a waste of time :)

---

### Post by fiddler616 on 2009-09-03
> **s3a said:**
> I need the numbers to be unknown until the user inputs them and not to always be 10 and 17.

@credobyte:

What is svar and fvar? I have never heard of those two terms before. As for what kpkeerthi said, I understand that right now so thank you :) but I'm guessing the svar/fvar way puts the work on the computer instead of your brain?

And yes this is my homework, I did not know that was a "crime" but technically I will be developping for Debian/Ubuntu in the future so I'm not a waste of time :)

Don't worry about svar and fvar. He wrote a "method" (if you don't know what that is, you will soon enough) so that you could swap two variables easily many times. Unless you're coding in Python
```

int temp = a;
a = b;
b = temp;
```
is the standard way of doing it.

---

### Post by Zorael on 2009-09-03
Well, with two variables **a** and **b** in pseudocode;
```
a = a + b      // a is now a(0) + b(0)
b = a - b      // b is now a(0); b = a(0) + b(0) - b = a(0)
a = a - b      // a is now b(0); a = a(0) + b(0) - a(0) = b(0)
```
As small as you can do it without other functions, I think. Obviously a messy way of doing it, but he did say "minimal code". Key is to remember the expression is evaluated before the variable is set to the result.

edit: As linked above at [http://www.hiteshagrawal.com/programming/swap-2-variable-content-without-temporary-variable](http://www.hiteshagrawal.com/programming/swap-2-variable-content-without-temporary-variable), yeah.

---

### Post by fiddler616 on 2009-09-03
> **Zorael said:**
> Well, with two variables **a** and **b** in pseudocode;
```
a = a + b      // a is now intial a(0)+b(0)
b = a - b      // b is now a(0); b = a(0) + b(0) - b = a(0)
a = a - b      // a is now b(0); a = a(0) + b(0) - a(0) = b(0)
```
As small as you can do it without other functions, I think. Obviously a messy way of doing it, but he did say "minimal code". Key is to remember the expression is evaluated before the variable is set to the result.

I'll give you points for having it be shorter, but I think using a temporary variable is clearer. *Tries desperately to avoid a readability vs. optimization flame*

---

### Post by lisati on 2009-09-03
I'm experiencing nostalgia here too, and have spotted two possible "correct" answers so far.

Suggestion: do a walk through your code snippet and ask yourself what value each variable holds.

---

### Post by Namtabmai on 2009-09-03
For those advocating the swap with out using the temporary variable, I assume you're omitting checks for integer overflows only to make the snippets more concise?

Obviously you'd never use that in production with out the proper checks that your language may need.

---

### Post by Zorael on 2009-09-03
I'm not *advocating* not using a third and temporary variable. This just seems like one of those homework assignments about how the math is evaluated before being assigned to the variable.

It's like **a = a + 1**. Unless you know that (**a + 1**) is first evaluated and then **a** assumes that value, **a** could race to infinity and still (**a + 1 > a**).

---

### Post by credobyte on 2009-09-04
> **s3a said:**
> I need the numbers to be unknown until the user inputs them and not to always be 10 and 17.

@credobyte:

What is svar and fvar? I have never heard of those two terms before. As for what kpkeerthi said, I understand that right now so thank you :) but I'm guessing the svar/fvar way puts the work on the computer instead of your brain?

And yes this is my homework, I did not know that was a "crime" but technically I will be developping for Debian/Ubuntu in the future so I'm not a waste of time :)

They are called [COLOR=RoyalBlue]function/method arguments[/COLOR] and you can change them if you want.

In an abstraction ( no specific language ):
```
function (type variable_name1, type variable_name2)
{
    type first_argument = variable_name1;
    type second_argument = variable_name2;
}
```

Some good tips can be found @ [http://java.sun.com/developer/JDCTechTips/2001/tt1009.html](http://java.sun.com/developer/JDCTechTips/2001/tt1009.html) ;)

---

### Post by Hanratty on 2009-09-04
[COLOR=#7f0055]**public class **[/COLOR][COLOR=#000000]Swapping{[/COLOR]
[COLOR=#7f0055]**static **[/COLOR][COLOR=#7f0055]**void **[/COLOR][COLOR=#000000]swap[/COLOR][COLOR=#000000]([/COLOR][COLOR=#7f0055]**int **[/COLOR][COLOR=#000000]i,int j[/COLOR][COLOR=#000000])[/COLOR]{
[COLOR=#7f0055]**int **[/COLOR][COLOR=#000000]temp=i;[/COLOR]
[COLOR=#000000]i=j;[/COLOR]
[COLOR=#000000]j=temp;[/COLOR]
[COLOR=#000000]System.out.println[/COLOR][COLOR=#000000]("[/COLOR][COLOR=#0000ff]After     swapping[/COLOR][COLOR=#2a00ff]i = " [/COLOR][COLOR=#000000]+ i + [/COLOR]"[COLOR=#2a00ff] j = [/COLOR]"[COLOR=#000000]+ j[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#7f0055]**public static **[/COLOR][COLOR=#7f0055]**void **[/COLOR][COLOR=#000000]main[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]String[/COLOR][COLOR=#000000][] [/COLOR][COLOR=#000000]args[/COLOR][COLOR=#000000]){[/COLOR]
[COLOR=#7f0055]**int **[/COLOR][COLOR=#000000]i=[/COLOR][COLOR=#990000]1[/COLOR][COLOR=#000000];[/COLOR]
[COLOR=#7f0055]**int **[/COLOR][COLOR=#000000]j=[/COLOR][COLOR=#990000]2[/COLOR][COLOR=#000000];[/COLOR]
      [COLOR=#ffffff]
    [/COLOR][COLOR=#000000]System.out.prinln("[/COLOR][COLOR=#0000ff]Before swapping     i=[/COLOR][COLOR=#000000]"+i+" [/COLOR][COLOR=#0000ff] j=[/COLOR][COLOR=#000000]"+j);[/COLOR][COLOR=#ffffff]
    [/COLOR][COLOR=#000000]swap[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]i,j[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000];[/COLOR]
      [COLOR=#ffffff]
  [/COLOR][COLOR=#000000]}[/COLOR]
[COLOR=#000000]}[/COLOR]

---

