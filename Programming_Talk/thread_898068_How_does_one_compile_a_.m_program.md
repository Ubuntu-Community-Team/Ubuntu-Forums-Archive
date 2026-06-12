---
title: "How does one compile a .m program???"
date: 2008-08-22
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-08-22
I read some articles over the net for the same. 

There was a command that read
```
octave abc.m
```
It didn't work for me.

I found another tutorial which used the code
[code]cat abc.m | octave</code>

It worked but it gave me the following error message.

[error]error: can't perform indexing operations for <unknown type> type[/error].

Can anyone help.

---

### Post by WW on 2008-08-22
MATLAB files have the extension .m; [Octave](http://www.gnu.org/software/octave/) is a MATLAB clone, and it also uses the extension .m.

Do you have Octave installed?

Can you show us the file abc.m?  Where did you get it?  What is it supposed to do?

---

### Post by 7raTEYdCql on 2008-08-23
This is the script.I installed octave and GNU Plot.


r=input('Enter the radius of the circle:');
z=linspace(0,2*pi,100);
x=r*cos(z);
y=r*sin(z);
plot(x,y,0,0,'+');
title('Circle of radius r')

---

### Post by Ubuntwan on 2008-10-28
In my octave 3.0.0 on ubuntu 8.04 gives proper results up until the plot command. I believe that octave lets the plotting to gnuplot, which has a different command buildup than that of matlab. Change the plot command to something that octave understands (I don't know exactly what it should look like, but there are many sites on the web detailing the differences between matlab and octave) and it should work.

---

### Post by jpkotta on 2009-07-11
The plot() command is mostly the same between Octave and Matlab (years ago, it was different).  The problem is that when the script ends, Octave closes.  The plot window is a child of octave, and thus that closes too.  You need a way to make octave stay running for a while after the main part of the script.  Try any of the following: 
```
sleep(5);
```
```
pause();
```
```
input('Press enter to continue', "s");
```

Also, "compile" is the wrong term.  Octave *evaluates* code.

---

### Post by nvteighen on 2009-07-11
> **jpkotta said:**
> 
Also, "compile" is the wrong term.  Octave *evaluates* code.

Heck... I read the thread title and I immediately thought the OP wanted to compile an Objective-C code (which also have extension .m). I have written a How-to on that topic so I was going to directly post the link... but what a surprise when I saw the discussion was about Octave!

Please, people, **use some kind of indicator on title threads!**. Something like "[Octave] ..." is great and will avoid confusions!

---

### Post by mmix on 2009-07-11
try your functions in freemat

[http://freemat.sourceforge.net/](http://freemat.sourceforge.net/)

---

### Post by lavinog on 2009-07-11
> **jpkotta said:**
> The plot() command is mostly the same between Octave and Matlab (years ago, it was different).  The problem is that when the script ends, Octave closes.  The plot window is a child of octave, and thus that closes too.  You need a way to make octave stay running for a while after the main part of the script.  Try any of the following: 

You can also run octave first then type abc and press enter (assuming it is in the current directory)

---

