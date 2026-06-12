---
title: "Java errors"
date: 2008-11-25
forum: Programming Talk
---

### Post by brian77095 on 2008-11-25
When I compile I am getting these error codes....



symbol  : variable outfile
location: class 3893
		outfile.println("The odd numbers between the first number and last number = ", (odd_num + ""));
		^
A2ga4003893.java:60: cannot find symbol
symbol  : variable outfile
location: class 3893
		outfile.println("Sum of the squares of the odd numbers between the first number and second number = ", oddsq_sum);
		^

The first problem looks like the =  but that is in "" marks so I thought it would just print that out not look at it or evaluate it...

again the next one looks like it is with the word "first" but that is in "" marks as well..

thanks for the help

brian77095 = "the guy on the Java short bus"

---

### Post by brian77095 on 2008-11-25
got it... needs a F on outFile...


I do have another question....when I compiled it the little ^ error code was pointing to the line below were it was suppose to.  I did not see that or notice it until I posted the error here.  Why is that?

so on my CL screen the pointer was in a diff. place than when I cut and pasted it here....

---

### Post by mdawg414 on 2008-11-26
I'm not sure I totally understand the question but if you are asking what I think you are asking it must have something to do with the copy and paste from the console. Were you compiling your program in the console or through some other IDE?

---

