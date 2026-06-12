---
title: "C++ Compiler &amp; Editor Q(Newbie)"
date: 2006-06-09
forum: Programming Talk
---

### Post by Dooq on 2006-06-09
Hello every one,
I want to ask if Kubuntu 6.06 LTS has a C++ Compiler ? or should i install it ? If not How can I install it from comand line ?

What is the Best Developer Editor in the Linux ? I was use PHPExpertEditor in Windows now i need good one in the linux :) .

Regards,
Dooq

---

### Post by Sef on 2006-06-09
Have you installed build-essential?  

Kmenu > Systems > Konsole

kdesu aptitude install build-essential

---

### Post by Dooq on 2006-06-09
No i have not.
I'll install it now and try it.
Thank's for your help.
Regards

---

### Post by Dooq on 2006-06-11
I Alrady download it(build-essential),But i don't know how to use it or where can find it ??

Any Help please?

---

### Post by frenkel on 2006-06-11
[QUOTE=Dooq]I Alrady download it(build-essential),But i don't know how to use it or where can find it ??

Any Help please?[/QUOTE]
You installed it? Or just downloaded?
Install it, then make a file like hello.cpp with the editor of your choice. Then compile it like this:
> g++ -o hello hello.cpp

---

### Post by kaamos on 2006-06-11
And if you want an IDE, install anjuta

---

### Post by rplantz on 2006-06-11
I'm running gnome, and I use gedit. If you create a Makefile, the Tools->Build command (or F8) executes the make command.

I played with kate (in Kubuntu) a bit. It is also very good. I'm quite sure that it also has a means for executing make from within the editor.

I've used IDEs in other environments, but not in Linux. I prefer a simpler, more generic development environment. The IDE I used the most, CodeWarrior, seemed to change often. I spent too much time learning new "features."

---

### Post by Dooq on 2006-06-11
Thank you every one,The compiler work ok now.
But I need good editor.
There is minimum feature must be in any good editor
I don't want it to give me that form:
if ( $a == 1 )
{
print 'I Love Linux';
}

I want my code be beutifull:
if ( $a == 1 )
{
          print 'I Love Linux';
}

I want to to do that auto

I need it easy and sample i dont need IDE

is there any good one ?

Thanks

---

### Post by Harleen on 2006-06-12
As you are using KDE, you should take a look at kate. It's an editor with syntax highlighting for various languages and auto intention. It can also collapse functions and loops and is part of standard KDE. Definitly a good editor to start with.

---

