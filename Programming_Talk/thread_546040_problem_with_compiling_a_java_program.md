---
title: "problem with compiling a java program"
date: 2007-09-08
forum: Programming Talk
---

### Post by threefcata on 2007-09-08
hi i have started to compile java programs using javac, and i wrote this simple program for this purpose:

import java.util.Scanner;

public class test
{
	public static void main(String arg1[])
	{
		Scanner s = new Scanner(System.in);
		String str = s.nextLine();
		System.out.println(s);
	}
}

but when i compile i got this error...

bash>javac test.java -cljava-6-sun-1.6.0.00/jre/lib
----------
1. ERROR in test.java (at line 1)
        import java.util.Scanner;
               ^^^^^^^^^^^^^^^^^
The import java.util.Scanner cannot be resolved
----------
2. ERROR in test.java (at line 7)
        Scanner s = new Scanner(System.in);
        ^^^^^^^
Scanner cannot be resolved to a type
----------
3. ERROR in test.java (at line 7)
        Scanner s = new Scanner(System.in);
                        ^^^^^^^
Scanner cannot be resolved to a type
----------
3 problems (3 errors)

i installed jdk6 from repo

so what's the problem?

thank you in advance..

---

### Post by Vadi on 2007-09-08
I haven't programmed in java since... well, may, and should start again.

But isn't it String args[], not arg1?

It looks like all of your woes are from the import statement not going through.

Try this:


import java.util.*;

(I believe when java compiles a program, it'll include only the necessary libraries auto, so don't worry, it won't include every library in util, only scanner)

---

### Post by threefcata on 2007-09-08
replaced the first line...still the same

bash>javac test.java
----------
1. ERROR in test.java (at line 7)
        Scanner s = new Scanner(System.in);
        ^^^^^^^
Scanner cannot be resolved to a type
----------
2. ERROR in test.java (at line 7)
        Scanner s = new Scanner(System.in);
                        ^^^^^^^
Scanner cannot be resolved to a type
----------
2 problems (2 errors)

i think the problem is with the classpath and that stuff..what should i set for the classpath when i install the jdk6 from the repo?

---

### Post by Vadi on 2007-09-08
Oh I forgot about the classpath.

I don't know, I installed the 'ubuntu restricted' package from add/remove, it installed java and flash for me without any tinkering. I haven't tried compiling stuff though yet.

---

### Post by tenmillionmilesaway on 2007-09-08
it looks like you could be compiling with the gcj java compiler.  To be sure you are using the sun java compiler run this:
```
sudo update-alternatives --config java
```
and make sure you choose the sun 6 one.

you cold also try
 ```
sudo update-alternatives --config javac
```
to make sure that you are using the sun javac rather than the gcj one.

Also the name of the String array variable in the main method is irrelevant, so long as it is a valid variable name.

---

### Post by blackhowling on 2007-09-08
using Eclipse for programming with java might help

---

### Post by threefcata on 2007-09-08
> **tenmillionmilesaway said:**
> 
you cold also try
 ```
sudo update-alternatives --config javac
```
to make sure that you are using the sun javac rather than the gcj one.

Also the name of the String array variable in the main method is irrelevant, so long as it is a valid variable name.

oh my! this works!
i did sudo update-alternatives --config java before but never thought of the javac thing!

thank you sooo much, and the same to all of you!

> **blackhowling said:**
> using Eclipse for programming with java might help

things like eclipse are way to memory-consuming for my mere 256M on my thinkpad X31..can't understand why these kind of things being soooo big...:confused:

---

### Post by Vadi on 2007-09-08
Yeah really. Notepad++, javac, and you're good to go.

T41 here :D

---

### Post by threefcata on 2007-09-08
seems like lotz of people are using linux on thinkpads..:)

btw which is a more suitable text editor for coding? i'm using vim currently.

---

### Post by Vadi on 2007-09-08
I prefer Notepad++. It's for Windows, but it's an open source app, and works great in wine.

Has really nice syntax highlighting for a ton of languages, nice search & replace features that support regex, even tabs out code for you right (for C/C++). Great program overall, and free as in free beer and... whatever the other thing is.

---

### Post by threefcata on 2007-09-08
hmmm...sounds nice..may give it a shot.

---

### Post by andyrobo60 on 2007-09-08
I think its meant to be 

```
public static void main(String[] args)
```

---

### Post by dwhitney67 on 2007-09-09
> **threefcata said:**
> seems like lotz of people are using linux on thinkpads..:)

btw which is a more suitable text editor for coding? i'm using vim currently.

Vim is great!  I've heard other raving about Eclipse.  But for me, it's vi... err, vim.

---

### Post by dwhitney67 on 2007-09-09
> **tenmillionmilesaway said:**
> it looks like you could be compiling with the gcj java compiler.  To be sure you are using the sun java compiler run this:
```
sudo update-alternatives --config java
```
and make sure you choose the sun 6 one.

you cold also try
 ```
sudo update-alternatives --config javac
```
to make sure that you are using the sun javac rather than the gcj one.

Also the name of the String array variable in the main method is irrelevant, so long as it is a valid variable name.

Thank you for this post.  This is another reason why Ubuntu should not be considered as a platform for development.  There are too many variables associated with the Ubuntu distro to make it a serious competitor to other Linux distros.

It would be nice if the install CD for Ubuntu would query the operator (installer) if they would wish to setup their system as a development system.  It's annoying that at every corner, one must install, or reconfigure their Ubuntu system to behave and support basic tools that other distros include by default (when configuring as a development system).  If I were to install JDK, and then later find out that the Sun javac is not being used but instead the gcj (what the heck is that anyway?), I would be pissed.  Why is there a gcj installed??

As a software developer and Linux/Unix aficionado since 1988, I have come to realize that Ubuntu is slated more towards those that do not care to develop software, but instead towards those that just want a multimedia platform.  That's cool, but I do feel a breeze coming through the "Window".

Don't get me wrong.  I will continue to use Ubuntu for personal use, but for work that earns me my livelihood, forget it.

---

### Post by Vadi on 2007-09-09
Good post.

I didn't read anywhere on Ubuntu's site that it's a development platform anyway, so you got it spot on.

---

### Post by CptPicard on 2007-09-09
> **dwhitney67 said:**
> There are too many variables associated with the Ubuntu distro to make it a serious competitor to other Linux distros.

This particular Java thing actually comes from Debian, which I also use (on servers), and Ubuntu just tends to add more of the "it just works out of the box" flavour to it. Java is, incidentally, the only thing I've had to configure like this, and it's far superior to installing a JDK completely by hand, for example.

> Don't get me wrong.  I will continue to use Ubuntu for personal use, but for work that earns me my livelihood, forget it.

I configured my Ubuntu box about two years back within a few days, have been upgrading ever since, and use it to earn my livelihood. If the update-alternatives system is too obscure for you to use to configure once and run ever since... tough :)

(As a side note, I migrated from Gentoo)

---

