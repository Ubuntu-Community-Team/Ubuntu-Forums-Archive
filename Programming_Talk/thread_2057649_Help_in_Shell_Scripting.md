---
title: "Help in Shell Scripting"
date: 2012-09-14
forum: Programming Talk
---

### Post by Mohan1289 on 2012-09-14
Hi guys i just started Shell scripting today and doing a very basic Shell script but i am not getting the correct output i don't now why please help me.

I am using Ubuntu 12.10
[B]
The code[/B] i written is:

#!/bin/bash
echo Enter Sides
read l
read b
area='expr $l \* $b'
echo The area of rectangle with sides $l and $b is $area
echo Enter radius
read r
area='expr $r \* $r \22'
area='expr $area / 7'
echo The area of circle with radius $r is $area

The **Output** i'm getting is:

Enter sides
9
8
The area of rectangle with sides 9 and 8 is **expr $l\ *$b**
Enter Radius
15
The area of the circle with radius 15 is **expr $area / 7**

What's wrong in my shell script??

---

### Post by kjohri on 2012-09-14
For substituting the command output in `command`, single back quotes need to be used.

```
#!/bin/bash
echo Enter Sides
read l
read b
area=`expr $l \* $b`
echo The area of rectangle with sides $l and $b is $area
echo Enter radius
read r
area=`expr $r \* $r`
area=`expr $area \* 22`
area=`expr $area / 7`
echo The area of circle with radius $r is $area
```

---

### Post by Lars Noodén on 2012-09-14
> **kjohri said:**
> For substituting the command output in `command`, single back quotes need to be used.


It's even more clear to use $()

```
area=$(expr $l \* $b)

```

---

### Post by Mohan1289 on 2012-09-14
> **kjohri said:**
> For substituting the command output in `command`, single back quotes need to be used.

```
#!/bin/bash
echo Enter Sides
read l
read b
area=`expr $l \* $b`
echo The area of rectangle with sides $l and $b is $area
echo Enter radius
read r
area=`expr $r \* $r`
area=`expr $area \* 22`
area=`expr $area / 7`
echo The area of circle with radius $r is $area
```


Thanks for the help kiohri

---

### Post by Mohan1289 on 2012-09-14
> **Lars Noodén said:**
> It's even more clear to use $()

```
area=$(expr $l \* $b)

```

Can i use like that too instead of  back quotes` 
 				 				[Lars Noodén]("http://ubuntuforums.org/member.php?u=168643")

---

### Post by Lars Noodén on 2012-09-14
Yes, they're used in about the same way. $() can even be nested if the occasion needs it.

It might be worth skimming through these three guides to see if anything stands out as useful:

[list]
[*] [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[*] [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[*] [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[/list]

---

### Post by Mohan1289 on 2012-09-14
Hi guys i am newly joined in Ubuntu forums and i am very beginner of   programming. I wish to have strong programming skills in shell scripting   and to gain profound knowledge on Ubuntu Operating system and  languages.
Please  suggest me some programs/projects which may help to improve my knowledge.
I am  practical person i learn things by work rather than reading, So can you  guys please suggest me what to do....

---

### Post by Lars Noodén on 2012-09-14
The only two additional resources that I can recall just now are these:

[list]
[*] [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[*] [http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
[/list]

Those with the Wooledge pages linked in the post above ought to be a good start. 

One of the places that Ubuntu uses shell scripts is in the System V init scripts.  Those are slowly going away to be replaced by Upstart, but those that have not been moved to Upstart can be found in /etc/init.d/

---

### Post by Mohan1289 on 2012-09-14
Thanks Lars

---

### Post by Vaphell on 2012-09-14
when using bash *expr* is not required
you can easily perform integer math inside (())

```
$ b=10; c=12
$ ((a=b*b/7))
$ echo $a
14
$ a=$(( c*c/7 ))
$ echo $a
20
```

note that integer division doesn't deal with fractions at all and you need to use bc command in order not to lose precision.

```
$ a=$( echo "$b*$b/7" | bc -l )
$ echo $a
14.28571428571428571428
$ a=$( echo "$c*$c/7" | bc -l )
$ echo $a
20.57142857142857142857
```

---

### Post by Mohan1289 on 2012-09-14
Thank you Vaphell. I am very New to both Linux and Shell Scripting i wish to learn about Both Scripting and Linux. 

Thank you

---

### Post by Habitual on 2012-09-14
These references may come in handy:

[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
and
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by Mohan1289 on 2012-09-14
Thankyou Habitual

---

### Post by Some Penguin on 2012-09-15
> **Mohan1289 said:**
> Hi guys i am newly joined in Ubuntu forums and i am very beginner of   programming. I wish to have strong programming skills in shell scripting   and to gain profound knowledge on Ubuntu Operating system and  languages.
Please  suggest me some programs/projects which may help to improve my knowledge.
I am  practical person i learn things by work rather than reading, So can you  guys please suggest me what to do....

One very traditional sort of thing to try is building a postfix calculator -- e.g. parsing "5 6 10 * +" in such a way that its execution could be modeled as

```

    +
   / \
  5   *
     / \
    6   10

```

and evaluating accordingly.  It's commonly used as a very basic introduction to stacks.

---

### Post by Mohan1289 on 2012-09-21
er... Sorry guys due to some technical problems i am unable to connect to the internet :D.

---

### Post by Mohan1289 on 2012-09-25
> **Some Penguin said:**
> One very traditional sort of thing to try is building a postfix calculator -- e.g. parsing "5 6 10 * +" in such a way that its execution could be modeled as

```

    +
   / \
  5   *
     / \
    6   10

```

and evaluating accordingly.  It's commonly used as a very basic introduction to stacks.

I am sorry i don't understand the problem.. 
i mean how can display a tree like that??
what's a POST FIX calculator? what does it do?

---

### Post by Vaphell on 2012-09-25
postfix calculator means that the operation to perform is listed AFTER the numbers.
3+4 would be written as 3 4 + (you can read it as 'there are 2 numbers, now add them)

That graph shows the order of operations
5 (6 10 *) +
to calculate the sum you need to multiply first and the graph shows it - * is one of the arguments required to produce the addition.

---

### Post by Mohan1289 on 2012-09-25
> **Vaphell said:**
> postfix calculator means that the operation to perform is listed AFTER the numbers.
3+4 would be written as 3 4 + (you can read it as 'there are 2 numbers, now add them)

That graph shows the order of operations
5 (6 10 *) +
to calculate the sum you need to multiply first and the graph shows it - * is one of the arguments required to produce the addition.

So The Answer for the above example is 65?

---

