---
title: "How to sort 3 integers"
date: 2008-07-28
forum: Programming Talk
---

### Post by D.Sync on 2008-07-28
How to sort 3 integers number and display them as in the question below:

> Write a program that sorts three integers.  The integers are entered from the console and stored in 

variables num1, num2 and num3, respectively.  The program sorts the numbers so that num1 <= num2 <= num3.

So far I only managed to code it as:

```
import java.util.*;

public class q4 {
    public static void main(String[] args) {
    System.out.println("Enter the first number");
    Scanner input1 = new Scanner (System.in);
    int num1 = input1.nextInt();
    
    System.out.println("Enter the second number");
    Scanner input2 = new Scanner (System.in);
    int num2 = input2.nextInt();
    
    System.out.println("Enter the third number");
    Scanner input3 = new Scanner (System.in);
    int num3 = input3.nextInt();     
    
    if ((num1 < num2) && (num2 < num3)) {
    System.out.println(num1 + " < " + num2 + " < " + num3);
    }
    
    if ((num1 < num2) && (num2 > num3)) {
    System.out.println(num1 + " < " + num3 + " < " + num2);
    }
    
    if ((num1 > num2) && (num2 > num1)) {
    System.out.println(num3 + " < " + num2 + " < " + num1);
    }
     
    if ((num1 > num2) && (num2 < num3)) {
    System.out.println(num2 + " < " + num3 + " < " + num1);
    }    
}

}
```

I find it quite messy and it display nothing if any 2 or more integer is the same. 

Any idea to solve it / optimize it?

---

### Post by X-dark on 2008-07-28
I don't think is good for you to have your program made by other people. But we can help you.
First read again the question. You have to put the smaller value in num1 and the greater in num3.
So first sort your integers then display the result.

---

### Post by D.Sync on 2008-07-28
I'm kinda new to the sort / swap thing so I would definitely need some help here.

Btw, is array suitable to use here? Didn't know and learn much about array. :(

---

### Post by X-dark on 2008-07-28
No need of array. All your need is an extra variable to temporary storing.

Then if you have determined (with some if) that num2 < num3 < num1

```

temp = num1;
num1 = num2;
num2 = num3;
num3 = temp;

```

---

### Post by samjh on 2008-07-28
A simplified bubble sort would be the easiest thing to use for this.

To get started:
[http://en.wikipedia.org/wiki/Bubble_sort](http://en.wikipedia.org/wiki/Bubble_sort)

But in your case, you can just:
```
REPEAT 2 TIMES
    IF num1 > num2 THEN swap
    IF num2 > num3 THEN swap
DO REPEAT
```

But if you take a good hard look at the problem, you'll find you don't actually need to compare num2 and num3 twice.  Your list of three numbers will always be sorted within three comparisons.  Do it using a pen and paper and see for yourself.

So...
```
IF num1 > num2 THEN swap
IF num2 > num3 THEN swap
IF num1 > num2 THEN swap
```

To implement swap, imagine having two containers (red and blue) of fruits, and a third empty container (green).  How will you swap the fruits in the two containers using the green one?
```
TAKE FRUIT FROM red PUT INTO green
TAKE FRUIT FROM blue PUT INTO red
TAKE FRUIT FROM green PUT INTO blue
```

One of the best ways to solve a problem in coding, is to not actually code anything.  Take out a trusty piece of paper and a good old-fashioned pencil, and work it out on paper.  Make analogies with real life problems and write down the steps on how you solve the real life analogy.

---

### Post by X-dark on 2008-07-28
Yeah but considering the experience of D.Sync, a simple algorithm which he can have thought of may be a better idea. Bubble sort may be more efficient but it's better to begin with a simple algorithm.

---

### Post by samjh on 2008-07-28
> **X-dark said:**
> Yeah but considering the experience of D.Sync, a simple algorithm which he can have thought of may be a better idea. Bubble sort may be more efficient but it's better to begin with a simple algorithm.

Yeah I agree.

But I think that if he can figure out how to implement bubble sort, he'll be well on his way to solving more complex sorting problems.  If he just looks at the minimal solution to this particular problem, then his growth is limited. ;)

But then, I'm someone who likes to throw people in the deep end (with a life-line obviously). :p

---

### Post by dribeas on 2008-07-28
> **D.Sync said:**
> I find it quite messy and it display nothing if any 2 or more integer is the same. 

Any idea to solve it / optimize it?

To optimize, read previous comments.

To solve the 'equals not showing' learn to use 'else' statements so that you always output something. That is what you would do in real life, either you print a,b else you print b,a.

```

if ( a < b ) {
} else {
   // we don't really care if a==b or a > b, the sequence b,a is ordered
}
// another option:
if ( a <= ) {
   // this will print a,b whether a < b or a == b
}

```

---

### Post by lisati on 2008-07-28
Just a quick rhetorical question (I already have an answer in mind): What is the essence of sorting?

(The need for arrays in real-life sorting applications and the relative merits of various sorting algorithms can come later)

---

