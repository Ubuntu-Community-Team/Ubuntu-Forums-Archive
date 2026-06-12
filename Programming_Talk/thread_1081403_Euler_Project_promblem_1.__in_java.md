---
title: "Euler Project promblem 1.  in java"
date: 2009-02-26
forum: Programming Talk
---

### Post by brian77095 on 2009-02-26
Here is a question form the Euler project web site...

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

I am trying to solve this question in Java...but I am getting the wrong answer and I am not sure why. I know it must be my logic I am not sure what to change....

Since this is just for fun if you like feel free to post your code in a different language or a much simpler java code..

[PHP]


import java.util.*;

import java.io.*;



public class euler1

{


     public static void main(String[] args) throws
						FileNotFoundException    

     {


	int result;
	int result3;
	int sum3;
	int sum;
	sum = 0;
	result3 = 0;
	sum3 = 0;
	while (result3 < 1000)
	{
		sum3 = sum3 + result3;
		result3 = result3 + 3;
		System.out.print (result3 + " ");



	}

	result = 0;

	while (result < 1000)
	{
		sum = sum + result;
		result = result + 5;		
		System.out.print (result + " ");



	}


System.out.println();
System.out.println("the sum is "+ (sum + sum3));
}
}
[/PHP]

the result I get is 266333

If I change the end point to say 10 I get the right sum...even if I change it to 50 I get the right sum....

thanks for the help

Brian

---

### Post by dwhitney67 on 2009-02-26
I got these results with my program:
```

3 5 6 9 10 12 15 18 20 21 24 25 27 30 33 35 36 39 40 42 45 48 50 51 54 55 57 60 63 65 66 69 70 72 75 78 80 81 84 85 87 90 93 95 96 99 100 102 105 108 110 111 114 115 117 120 123 125 126 129 130 132 135 138 140 141 144 145 147 150 153 155 156 159 160 162 165 168 170 171 174 175 177 180 183 185 186 189 190 192 195 198 200 201 204 205 207 210 213 215 216 219 220 222 225 228 230 231 234 235 237 240 243 245 246 249 250 252 255 258 260 261 264 265 267 270 273 275 276 279 280 282 285 288 290 291 294 295 297 300 303 305 306 309 310 312 315 318 320 321 324 325 327 330 333 335 336 339 340 342 345 348 350 351 354 355 357 360 363 365 366 369 370 372 375 378 380 381 384 385 387 390 393 395 396 399 400 402 405 408 410 411 414 415 417 420 423 425 426 429 430 432 435 438 440 441 444 445 447 450 453 455 456 459 460 462 465 468 470 471 474 475 477 480 483 485 486 489 490 492 495 498 500 501 504 505 507 510 513 515 516 519 520 522 525 528 530 531 534 535 537 540 543 545 546 549 550 552 555 558 560 561 564 565 567 570 573 575 576 579 580 582 585 588 590 591 594 595 597 600 603 605 606 609 610 612 615 618 620 621 624 625 627 630 633 635 636 639 640 642 645 648 650 651 654 655 657 660 663 665 666 669 670 672 675 678 680 681 684 685 687 690 693 695 696 699 700 702 705 708 710 711 714 715 717 720 723 725 726 729 730 732 735 738 740 741 744 745 747 750 753 755 756 759 760 762 765 768 770 771 774 775 777 780 783 785 786 789 790 792 795 798 800 801 804 805 807 810 813 815 816 819 820 822 825 828 830 831 834 835 837 840 843 845 846 849 850 852 855 858 860 861 864 865 867 870 873 875 876 879 880 882 885 888 890 891 894 895 897 900 903 905 906 909 910 912 915 918 920 921 924 925 927 930 933 935 936 939 940 942 945 948 950 951 954 955 957 960 963 965 966 969 970 972 975 978 980 981 984 985 987 990 993 995 996 999 
The sum of the values is: 233168

```

See if you can translate this C++ program into Java (it should be easy to do):
```

#include <iostream>
#include <cstdlib>

int main(int argc, char** argv)
{
  unsigned int sum = 0;
  const unsigned int LIMIT = (argc > 1 ? atoi(argv[1]) : 10);

  for (unsigned int i = 3; i < LIMIT; ++i)
  {
    // if the value 'i' is evenly divisible by 3 or 5, then
    // it is a value of interest.
    if (i % 3 == 0 || i % 5 == 0)
    {
      sum += i;
      std::cout << i << " ";
    }
  }
  std::cout << std::endl;
  std::cout << "The sum of the values is: " << sum << std::endl;
}

```

---

### Post by simeon87 on 2009-02-26
The problem is that you're counting a number twice when it is divisible by both 3 and 5

Basically, you're doing:

```

public static void main(String[] args) {
		int sum3 = 0;
		int sum5 = 0;
		for (int i = 0; i < 1000; i++) {
			if (i % 5 == 0) {
				sum5 += i;
			}
		}
		for (int i = 0; i < 1000; i++) {
			if (i % 3 == 0) {
				sum3 += i;
			}
		}
		System.out.println(sum3 + sum5);
	}
```

While the following counts a number only once:

```

public static void main(String[] args) {
		int sum = 0;
		for (int i = 0; i < 1000; i++) {
			if (i % 3 == 0 || i % 5 == 0) {
				sum += i;
			}
		}
		System.out.println(sum);
	}
```

Which is quite similar to the code of dwhitney67.

---

### Post by brian77095 on 2009-02-26
That has to be it....I am counting things twice....I new it was something simple like that....Thanks again...

---

### Post by Simian Man on 2009-02-26
Here is my solution in Ocaml:
```

let rec sum_3_5 i n =
  if i = n then
    0
  else if i mod 3 = 0 then
    i + (sum_3_5 (i + 1) n)
  else if i mod 5 = 0 then
    i + (sum_3_5 (i + 1) n)
  else
    (sum_3_5 (i + 1) n)
in
Printf.printf "Answer = %d\n" (sum_3_5 1 1000)

```

---

### Post by simeon87 on 2009-02-26
Haskell :)

```
euler1 = sum.filter (\x -> x `rem` 3 == 0 || x `rem` 5 == 0) $ [1..999]
```

---

### Post by PythonPower on 2009-02-26
O(1) beats everyone else's O(n)! :p

[PHP]
def inc(n, d): return (d+n-n%d)*(n//d)//2

n = 10**3-1
print(inc(n, 3)+inc(n, 5)-inc(n, 15))[/PHP]

---

### Post by Shin_Gouki2501 on 2009-02-26
Clojure anyone?

---

### Post by Paul Miller on 2009-02-27
> **PythonPower said:**
> O(1) beats everyone else's O(n)! :p


Hehe.  I remember I did that particular problem using paper and pencil with this algorithm.

---

### Post by eightmillion on 2009-02-27
Here's an interesting python solution:

```
sum(set(range(3,1000,3)+range(5,1000,5)))
```

and one that's pretty much identical to the haskell version above:

```
sum(filter(lambda x:x%3==0 or x%5==0,range(1,1000)))
```

and some ruby:

```
(1..999).select{|i|i%3==0 or i%5==0}.inject{|x,y|x+y}
```

---

