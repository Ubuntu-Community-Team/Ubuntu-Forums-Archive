---
title: "Making a loop in fibonacci series in java"
date: 2023-02-24
forum: Programming Talk
---

### Post by ronakmehta on 2023-02-24
I'm attempting to develop a programme that will locate the nth term in a Fibonacci sequence (it has to be non-recursive, by the way). It must be capable of accepting any two numbers from the user and using them as the first two keywords.


For example, if the user enters f1 = 2 and f2 = 3, the series will be 2, 3, 5, 8, 13, 21, and so on.

```
[COLOR=var(--highlight-keyword)][FONT=inherit]import[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] java.util.Scanner;[/FONT][/COLOR]
[COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]fibs[/FONT][/COLOR]
{
  [COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]static[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]main[/FONT][/COLOR][FONT=inherit](String[] args)[/FONT]
  {
    [COLOR=var(--highlight-namespace)][FONT=inherit]Scanner[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]keyboard[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]Scanner[/FONT][/COLOR](System.in); [COLOR=var(--highlight-comment)][FONT=inherit]// readying keyboard for input[/FONT][/COLOR]
    [COLOR=var(--highlight-namespace)][FONT=inherit]int[/FONT][/COLOR] f1, f2, n, fib;
    System.out.println([COLOR=var(--highlight-variable)][FONT=inherit]"Please enter a vaule for F(1):"[/FONT][/COLOR]);
    f1 = keyboard.nextInt();
    System.out.println([COLOR=var(--highlight-variable)][FONT=inherit]"Please enter a vaule for F(2):"[/FONT][/COLOR]);
    f2 = keyboard.nextInt();
    System.out.println([COLOR=var(--highlight-variable)][FONT=inherit]"Please enter a vaule for n :"[/FONT][/COLOR]);
    n = keyboard.nextInt();

    [COLOR=var(--highlight-keyword)][FONT=inherit]if[/FONT][/COLOR] ((f1<[COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR])||(f2<[COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR])||(f1>[COLOR=var(--highlight-namespace)][FONT=inherit]1000[/FONT][/COLOR])||(f2>[COLOR=var(--highlight-namespace)][FONT=inherit]1000[/FONT][/COLOR])||(n<[COLOR=var(--highlight-namespace)][FONT=inherit]1[/FONT][/COLOR]))
    {
      System.out.println([COLOR=var(--highlight-variable)][FONT=inherit]"Please try again"[/FONT][/COLOR]);
      [COLOR=var(--highlight-keyword)][FONT=inherit]return[/FONT][/COLOR];
    }
    [COLOR=var(--highlight-keyword)][FONT=inherit]else[/FONT][/COLOR]
    {
      [COLOR=var(--highlight-namespace)][FONT=inherit]int[/FONT][/COLOR] i;
      [COLOR=var(--highlight-keyword)][FONT=inherit]for[/FONT][/COLOR] (i=[COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR]; i<n; i++)
      {

        fib=f1+f2;
        f1=f2;
        f2=fib;
        System.out.println( fib );

      }


    }
  } [COLOR=var(--highlight-color)][FONT=inherit]}[/FONT][/COLOR]
```

The user can also specify the phrase they wish to appear.


I've completed the most of the curriculum (I believe), but I'm having two issues.
The software must count f1 and f2 as terms 1 and 2 when determining the nth term. I can't get it to do this because it counts the third number as the first.
The software prints all the numbers up to the nth term, but I just want the nth term to be printed.
I've been working on this for a long now, and I've been reading this [article]("https://www.scaler.com/topics/fibonacci-series-in-java/") for that. I'm quite new to Java; I attended an introductory class in it two years ago and am now in the next level up; I'm experiencing some difficulties, so any assistance would be greatly appreciated!

---

### Post by slickymaster on 2023-02-24
*Thread moved to **Programming Talk**.*

---

