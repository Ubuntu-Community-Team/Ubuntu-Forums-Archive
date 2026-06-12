---
title: "Basic C Problem"
date: 2012-04-08
forum: Programming Talk
---

### Post by clayman35 on 2012-04-08
Guys, I have a problem about Secant Method. I'm trying to find roots of a function ax^2+bx+c. 

[IMG]http://upload.wikimedia.org/wikipedia/en/math/f/9/8/f9808321e7d8c7dc390ff7f0f1fe826d.png[/IMG]

This is Secant Method's formula and this is the code that I've written:

> #include <stdio.h>
#include <stdlib.h>
#include <math.h>

double f(double a, double b, double c, double x)
{
double result;
result=(a*x*x)+(b*x)+c;
return(result);
}

int main()
{
 int counter=1;
 double x0,x1,x2,a,b,c;
 printf("Please enter the coefficients a,b,c of equation: \n");
 scanf("%lf %lf %lf", &a,&b,&c);
 printf("Please enter two initial numbers: \n");
 scanf("%lf %lf", &x0,&x1);
        do
        {
            x2=x1-((f(a,b,c,x1)*(x1-x0))/(f(a,b,c,x1)-f(a,b,c,x0)));
            x0=x1;
            x1=x2;
            printf("The root of stage %d is: %.3lf\n",counter,x1);
            counter++;
        }while(fabs(x1-x0)>0.0001);
 printf("The root is %.1lf.\n",x1);
 printf("The iteration number is %d.\n", counter-1);

 return 0;
}


In this method, you must choose an interval to find the root. For example, if our function is x^2-7x+12, our roots are x=4 and x=3 as you know. To find 3 via Secant Method, you must choose an interval which contains 3, for example (0,3.5). 

At this stage, I've tried to find the roots of x^2+2x+1 in other words x=-1. To find it, I've chosen the interval (-2,0) but the result is stupid.

[IMG]http://i43.tinypic.com/jinqdw.png[/IMG]

How can I fix it ? Thanks for your helps...

---

### Post by roelforg on 2012-04-08
Are you just trying to find the parabole crosses the x-axis?
If so, here's the formulea (from my old math book):
x=-(b/(2a))-(sqrt(b^2-4ac)/(2a)) v x=-(b/(2a))+(sqrt(b^2-4ac)/(2a))
Or the top of the parabole:
x=-(b/(2a))

Edit:
Really?
Using windows?
If it works for you, great for you. I just really don't like windows.

---

### Post by clayman35 on 2012-04-08
Yes, I'm trying to find it but I must do this by Secant Method, this is my homework :)

---

### Post by roelforg on 2012-04-08
You're not allowed to ask for homework here.

---

### Post by clayman35 on 2012-04-08
But why ? I've already did this but I have a little problem. I think this is not important and I hope that you'll be tolerant to me.

---

### Post by roelforg on 2012-04-08
You're asking to fix / improve / check your homework

---

### Post by GeneralZod on 2012-04-09
With the values of x0 & x1 you've chosen, the very first iteration divides by 0, which is undefined.

---

### Post by lisati on 2012-04-09
> **roelforg said:**
> You're not allowed to ask for homework here.
Although we don't actually do the homework for people, we don't mind being asked for help when someone gets stuck.

---

### Post by 3Miro on 2012-04-09
> **clayman35 said:**
> But why ? I've already did this but I have a little problem. I think this is not important and I hope that you'll be tolerant to me.

Absolutely every numerical method may or may not converge depending on a set of conditions. If you are going to use a numerical method, you should always know what those conditions are and do your best to justify "why" and "how" your problem satisfied those conditions. Things like nan and inf show you that there is something wrong, however, a failed numerical method can give you something that looks like a perfectly reasonable answer and yet be completely wrong.

x^2-7x+12 satisfies the condition, x^2+2x+1 does not. (there are conditions on f(x) and then there are conditions on the initial guess, there are values of x1 and x2 for which x^2-7x+12 will fail also)

You ask why we don't want to help people with homework? Maybe you are supposed to discover what is wrong for yourself and not get an answer from one of us, and if we give you the answer, then we are undermining the efforts of your teacher. And if the homework counts as a significant portion of my grade, then getting help on an on-line forum is straight out academic dishonesty. I would like the engineer who builds my house to know how to find answers to his/her questions from reputable sources (i.e. books and peer-reviewed papers) and not some random strangers on-line.

---

### Post by fallenshadow on 2012-04-10
As soon as I saw maths I ran away from my PC... sorry I don't like maths! :lolflag:  Edit:actually maybe its because I suck at them. :S

---

### Post by roelforg on 2012-04-10
> **lisati said:**
> Although we don't actually do the homework for people, we don't mind being asked for help when someone gets stuck.

I was under the impression he wanted us to fix his code,
not to give him pointers to what he did wrong so he can fix it, my bad.

---

