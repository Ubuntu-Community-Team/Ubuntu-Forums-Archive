---
title: "My (java) programs works well with normal amount of input/outputs not crazy amounts"
date: 2009-10-29
forum: Programming Talk
---

### Post by s3a on 2009-10-29
Here is my code:
```
import java.util.Scanner;

public class Asg_3A_Q1

{

	public static void main (String [] args)

	{

	Scanner kb = new Scanner(System.in);

	System.out.print("How many terms of the Fibonacci sequence? ");

	int position = kb.nextInt();

	int random = 3;

	if(position < 0)

	{

		System.out.println("Can&#8217;t generate " + position + " terms.\nTry again later ...");

		System.exit(0);

	}

	System.out.println();

	

	int x = 0;

	int y = 1;

	int a = 3;

	

	if(position >= 1)

	System.out.println("F( 1) = 0");

	if(position >= 2)

	System.out.println("F( 2) = 1");

	

	while(random <= position)

	{

	int z = x + y;

	System.out.printf("F(%2d", a);

	System.out.println(") = " + z);

	a++;

	x = y;

	y = z;

	random++;

	}

	}

}

```

Here is 20 outputs (no problem):
```
How many terms of the Fibonacci sequence? 20

F( 1) = 0
F( 2) = 1
F( 3) = 1
F( 4) = 2
F( 5) = 3
F( 6) = 5
F( 7) = 8
F( 8) = 13
F( 9) = 21
F(10) = 34
F(11) = 55
F(12) = 89
F(13) = 144
F(14) = 233
F(15) = 377
F(16) = 610
F(17) = 987
F(18) = 1597
F(19) = 2584
F(20) = 4181
```

But if I put a larger number (like 101), I experience anomalies:
```
How many terms of the Fibonacci sequence? 101

F( 1) = 0
F( 2) = 1
F( 3) = 1
F( 4) = 2
F( 5) = 3
F( 6) = 5
F( 7) = 8
F( 8) = 13
F( 9) = 21
F(10) = 34
F(11) = 55
F(12) = 89
F(13) = 144
F(14) = 233
F(15) = 377
F(16) = 610
F(17) = 987
F(18) = 1597
F(19) = 2584
F(20) = 4181
F(21) = 6765
F(22) = 10946
F(23) = 17711
F(24) = 28657
F(25) = 46368
F(26) = 75025
F(27) = 121393
F(28) = 196418
F(29) = 317811
F(30) = 514229
F(31) = 832040
F(32) = 1346269
F(33) = 2178309
F(34) = 3524578
F(35) = 5702887
F(36) = 9227465
F(37) = 14930352
F(38) = 24157817
F(39) = 39088169
F(40) = 63245986
F(41) = 102334155
F(42) = 165580141
F(43) = 267914296
F(44) = 433494437
F(45) = 701408733
F(46) = 1134903170
F(47) = 1836311903
F(48) = -1323752223
F(49) = 512559680
F(50) = -811192543
F(51) = -298632863
F(52) = -1109825406
F(53) = -1408458269
F(54) = 1776683621
F(55) = 368225352
F(56) = 2144908973
F(57) = -1781832971
F(58) = 363076002
F(59) = -1418756969
F(60) = -1055680967
F(61) = 1820529360
F(62) = 764848393
F(63) = -1709589543
F(64) = -944741150
F(65) = 1640636603
F(66) = 695895453
F(67) = -1958435240
F(68) = -1262539787
F(69) = 1073992269
F(70) = -188547518
F(71) = 885444751
F(72) = 696897233
F(73) = 1582341984
F(74) = -2015728079
F(75) = -433386095
F(76) = 1845853122
F(77) = 1412467027
F(78) = -1036647147
F(79) = 375819880
F(80) = -660827267
F(81) = -285007387
F(82) = -945834654
F(83) = -1230842041
F(84) = 2118290601
F(85) = 887448560
F(86) = -1289228135
F(87) = -401779575
F(88) = -1691007710
F(89) = -2092787285
F(90) = 511172301
F(91) = -1581614984
F(92) = -1070442683
F(93) = 1642909629
F(94) = 572466946
F(95) = -2079590721
F(96) = -1507123775
F(97) = 708252800
F(98) = -798870975
F(99) = -90618175
F(100) = -889489150
F(101) = -980107325
```

My teacher won't check out such a huge number so in terms of marks I'm all set :) but I'd like to know why my program "misbehaves" when the numbers grow. Is it my fault? Is there something I can do about it? (I'm guessing there is)

Any input would be greatly appreciated!
Thanks in advance!

Edit: *This might be obvious to others but just in case it isn't, my program starts to "misbehave" as of F(48). Up until F(47), it works the way it is supposed to.*

---

### Post by johnl on 2009-10-29
'int' has a limited range of values it can hold.  Not familiar with Java, but I would guess it's probably a 32-bit signed integer.  That means it can store the range +(2^31-1) to -(2^31 - 1).  (32 bits, with one bit reserved for the sign bit).  Once your result gets bigger than that, it 'overflows', into the last (sign) bit, causing the value to appear to be negative.

Check [http://en.wikipedia.org/wiki/Integer_%28computer_science%29](http://en.wikipedia.org/wiki/Integer_%28computer_science%29) for more information.

---

### Post by NovaAesa on 2009-10-30
If you are worried about the teacher trying a very large input, you could try either using the 'long' data type (64 bit signed integer). If that isn't enough, you could have a look at the BigInteger class, which allows indefinitely large integers.

[http://java.sun.com/javase/6/docs/api/java/math/BigInteger.html](http://java.sun.com/javase/6/docs/api/java/math/BigInteger.html)

---

### Post by Redache on 2009-10-30
Yeah what the others have said.

Ints have a limited number and Java wraps around, that's why you see the negative numbers because once it reaches the limit of Int, it goes into the negatives (So if you added the Maximum Positive number with that negative number you'd get the actual answer).

I'd look at using a long just to be one the safe side.

Always choose your types carefully. If it doesn't fit the job, change it :).

---

### Post by jcwmoore on 2009-10-31
the solution to this issue is as others have said.  Just know that your solution is optimal and I seriously doubt any teacher would mark off because of the interger overflow. don't stress.

---

