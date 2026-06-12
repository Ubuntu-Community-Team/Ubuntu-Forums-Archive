---
title: "[SOLVED] Problem 36 Project Euler"
date: 2008-09-12
forum: Programming Talk
---

### Post by dustman on 2008-09-12
Hello !

I think this problem is driving me nuts!!! I found about [[COLOR="Blue"]Project Euler[/COLOR]]("http://www.projecteuler.net") a while ago, and when I had some spare time, I would solve a problem or two. They're pretty approachable and some are interesting to do (well, at least for a programmer :D). 

The problem is that I got stuck with [Problem 36]("http://projecteuler.net/index.php?section=problems&id=36")

I created the algorithm using Java in about 10 minutes, but the site it telling that I don't have the correct answer!

```
package problems;

import java.util.Vector;

public class Problem36 {
	
	public Problem36() {
		int sum = 0;
		for (int i = 0; i <= 1000000; i++) {
			if (palindrome(String.valueOf(i))) {
				String base2 = base10ToBase2(i);
				String first = base2.substring(0,1);
				String last = base2.substring(base2.length()-1);
				if (!first.equals("0") && !last.equals("0")) {
					if (palindrome(base2)) {
						System.out.println("Number:"+i+", with binary representation:"+base2+" is palindrome in both bases");
						sum=sum + i;
					}
				}
			}
		}
		System.out.println("Sum is:"+sum);
	}
	
	public boolean palindrome(String number) {
		for (int i=0;i<number.length()/2;i++) {
			if (number.charAt(i) != number.charAt(number.length()-1-i))
				return false;
		}
		return true;
	}
	
	private String base10ToBase2(long number) {
		Vector<Long> v = new Vector<Long>();
		long quot = 0;
		long rem = -1;
		while (number / 2 != 0) {
			quot = number / 2;
			rem = number % 2;
			v.add(rem);
			number = quot;
		}
		v.add(quot);
		String s = "";
		for (Long l : v) {
			s = l+s;
		}
		return s;
		
	}

}
```

Could anyone tell me what's wrong with my code? Cause I've tried to fix it for almost half a day with no success :|. I've checked the numbers to see if I've converted them OK, and they're fine.

Thanks in advance!

Radu

---

### Post by mike_g on 2008-09-12
Edit: Oh, Ignore that I you need the sum of numbers not the count.

Edit2: Your program does not seem to be detecting number 1 as being a palindrome.

---

### Post by Reiger on 2008-09-12
If I didn't make some stupid mistake:

To see if some sequence is palindrone in binary you can 'simply' XOR the LtR and RtL rendering of the sequence. The result should be 0 if it is a palindrome that is there exist no difference between LtR and RtL (which is the defining property of a palindrone after all).

Essentially that is the same with base 10, point is: you need to take the absolute of substracting the LtR from the Rtl value (or vice versa) digit by digit. If the resulting value is 0, you have a palindrone.

Since it is easier to do this manipulation binary (simple XOR operation on the bits) I suggest finding all binary palindrones first, and inspecting their string representation in base 10 second.

EDIT 2: As for your String conversions (if you want to do both by string): I suggest to use the static Integer.toString(int i, int base); method instead. Saves a lot of hassle and code. ;) As for the binary version it's not needed (aforementioned bitwise XOR...). As for the base 10 case you can just use the static Integer.toString(int i) method.

EDIT: 3 with the example given in 36:

Example: 585:
binary: 1001001001 (LtR = Rtl we already knew that) XOR'ed = 000000000 = 0.
decimal: 585       (LtR = Rtl we already knew that) Absolutes of substraction of digits: = 000 = 0.

---

### Post by dustman on 2008-09-15
> **mike_g said:**
> 

Edit2: Your program does not seem to be detecting number 1 as being a palindrome.

Jesus, you're right :D. I just took my result, wrote as the correct answer result+1, and it's OK!

That's because "1 / 2 != 0", so the algorithm will never go into the while loop from the method "base10ToBase2(...)". On the other hand, I add the last quotient to the array of binary representation of numbers, so if "long quot = number" instead of "long quot = 0", everything goes smoothly. 

Thanks a lot!

---

