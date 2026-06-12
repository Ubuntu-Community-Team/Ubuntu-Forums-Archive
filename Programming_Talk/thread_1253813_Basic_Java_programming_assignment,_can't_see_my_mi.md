---
title: "Basic Java programming assignment, can't see my mistake"
date: 2009-08-30
forum: Programming Talk
---

### Post by s3a on 2009-08-30
_Ok here is the output I am supposed to get according to my teacher:_

[i]How many cents? 196
7 Quarters
2 Dimes
0 Nickels
1 Pennies[/i]

_and here is my code so far:_

[i]import java.util.Scanner;

public class Assignment_1A_2
{
	public static void main (String [] args)
	{
	Scanner kb;
	kb = new Scanner(System.in);
	
	System.out.print("How many cents? ");
	int INPUTED_PENNIES = kb.nextInt();
	
	int PENNIES (int) (INPUTED_PENNIES % 5);
	int NICKELS (int) ((INPUTED_PENNIES / 5)) %2);
	int DIMES (int) ((INPUTED_PENNIES/10) % 2.5);
	int QUARTERS (int) ((INPUTED_PENNIES/25) % 4);

	System.out.println(QUARTERS + " Quarters");
	System.out.println(DIMES + "Dimes ");
	System.out.println(NICKELS + " Nickels");
	System.out.println(PENNIES + " Pennies");
	}
}[/i]

What is wrong when I try to compile this in order to run it?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by shadylookin on 2009-08-30
> **s3a said:**
> _Ok here is the output I am supposed to get according to my teacher:_

[i]How many cents? 196
7 Quarters
2 Dimes
0 Nickels
1 Pennies[/i]

_and here is my code so far:_

[i]import java.util.Scanner;

public class Assignment_1A_2
{
	public static void main (String [] args)
	{
	Scanner kb;
	kb = new Scanner(System.in);
	
	System.out.print("How many cents? ");
	int INPUTED_PENNIES = kb.nextInt();
	
	int PENNIES (int) (INPUTED_PENNIES % 5);
	int NICKELS (int) ((INPUTED_PENNIES / 5)) %2);
	int DIMES (int) ((INPUTED_PENNIES/10) % 2.5);
	int QUARTERS (int) ((INPUTED_PENNIES/25) % 4);

	System.out.println(QUARTERS + " Quarters");
	System.out.println(DIMES + "Dimes ");
	System.out.println(NICKELS + " Nickels");
	System.out.println(PENNIES + " Pennies");
	}
}[/i]

What is wrong when I try to compile this in order to run it?

Any help would be greatly appreciated!
Thanks in advance!

well if you want it to compile you need to add equal signs when you're trying to assign PENNIES, NICKLES, DIMES, and QUARTERS

this
((INPUTED_PENNIES / 5)) %2)
you need to either remove the ) after the %2 or one of the ) after / 5 

and for what it's worth only using mod will automatically give an integer there's no need to cast it. 

Anyway this won't give you the right answer. You should first take into account dollar values and remove everything but the change. Then you should see how many quartes will go into that then subtract that from the total change, then dimes, nickles, and finally pennies until you're done.

For instance 197
get rid of the dollar value you're left with 97
using integer division 97 / 25 = 3 so you have 3 quarters
97 - (25*3) = 22
integer division 22 / 10 = 2 so you have 2 dimes
22 - (10*2) = 2
using integer division 2/5 = 0 so you have 0 nickles
2 - (5*0) = 2
using integer division 2/1 = 2 so you have 2 pennies
2 - (2*1) = 0

and you're done

with your current algorithm
197 mod 5 = 2 so you have 2 pennies
197/5 mod 2 = 1 so you have 1 nickle
197/10 % 2.5 = 1 so you have 1 dime
197/25 mod 4 = 3 so you have 3 quarters

when you add that up you only have 92 cents instead of 97

---

### Post by Can+~ on 2009-08-30
Your algorithm is backwards, you should divide, THEN modulo.

For example: "How many Quarters (25 [cent/coin]) I need to get 196 [cent]".

```

_  196[cent]   _ = 7 [coins] + _21 [coins]_
25 [cent/coin]               25       
```

The Modulo (%) would represent those values that didn't add up enough to be represented by a Quarter (rightmost value). These values need to be re-divided by the following value (Dime (10 [cent/coin]))

---

### Post by s3a on 2009-08-30
Sorry for being stupid but, I understood some of the things that were said but still don't fully understand what you guys are pointing out:

[I]import java.util.Scanner;

public class Assignment_1A_2
{
	public static void main (String [] args)
	{
	Scanner kb;
	kb = new Scanner(System.in);
	
	System.out.print("How many cents? ");
	int INPUTED_PENNIES = kb.nextInt();
	
	int PENNIES = (int) (INPUTED_PENNIES % 5);
	int NICKELS = (int) ((INPUTED_PENNIES / 5) %2);
	int DIMES = (int) ((INPUTED_PENNIES/10) % 2.5);
	int QUARTERS = (int) (INPUTED_PENNIES/25);

	System.out.println(QUARTERS + " Quarters");
	System.out.println(DIMES + " Dimes");
	System.out.println(NICKELS + " Nickels");
	System.out.println(PENNIES + " Pennies");
	}
}
[/I]

---

