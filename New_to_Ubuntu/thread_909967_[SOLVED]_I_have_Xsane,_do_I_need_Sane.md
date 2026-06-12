---
title: "[SOLVED] I have Xsane, do I need Sane?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by egalvan on 2008-09-04
Running Kubuntu 8.04.1. 
Restricted repos, and medibuntu.

Synaptic shows
 libsane, xsane, xsane-common, xsane-doc   as installed
 sane    not installed.

Do I need sane?

Thanks

ErnestG

---

### Post by Sef on 2008-09-04
You should be able to scan without installing sane, if your scanner is detected.  xsane is a gui for sane.  (GUI - Graphical User Interface - use a mouse instead of the command line)  Does your scanner work?  If not, then what make and model do you have?

---

### Post by egalvan on 2008-09-04
thanks for the input.

yes, my scanner works.

it's a cannon lide 60.


But if xsane is a front-end for sane, then if I don't have. or need, sane, is xsane needed?


I'm confused because I thought sane was needed to run scanners.

ErnestG

---

### Post by egalvan on 2008-09-12
Bump.

My scanner works.

I don't have sane installed,

 xsane is installed

And I'm still wondering...

Is sane needed? 

Is xsane needed?

---

### Post by philinux on 2008-09-12
If you scanner works no worries.

[http://www.xsane.org/doc/sane-xsane-doc.html](http://www.xsane.org/doc/sane-xsane-doc.html)

---

### Post by bobnutfield on 2008-09-12
I believe you will find that if you have xsane installed, then you also have sane installed.  xsane, already mentioned is just the GUI front end to sane, which originally was run from the command line.  Open a terminal and type:

> whereis sane

I believe you will get output showing it located in /etc/sane.d and /usr/share/sane

---

### Post by philinux on 2008-09-12
Yes Bob thats interesting. I get this

```
 whereis sane 
sane: /etc/sane.d /usr/lib/sane /usr/lib64/sane /usr/share/sane /usr/share/man/man7/sane.7.gz

```

I have a default install. Xsane in installed but sane is not. Curious.

---

### Post by bobnutfield on 2008-09-12
> **philinux said:**
> Yes Bob thats interesting. I get this

```
 whereis sane 
sane: /etc/sane.d /usr/lib/sane /usr/lib64/sane /usr/share/sane /usr/share/man/man7/sane.7.gz

```

I have a default install. Xsane in installed but sane is not. Curious.


The sane commands will still work from the command line, but the sane-utilities may not be installed so commands like:

> sane-find-scanner

will not work but will invite you to install the program if you want it.  But, for xsane to work, it is built on the original sane program which as I mentioned was originally just a command line program.  The name sane is an acronym for "Scanning Now Easy".  The program used to drive me nuts trying to scan from a parallel port.  But, now that it is a mature program and can be used exlusively with the GUI, I haven't tried any sane commands in the terminal for years now.

---

### Post by egalvan on 2008-09-12
> **bobnutfield said:**
> I believe you will find that if you have xsane installed, then you also have sane installed.  xsane, already mentioned is just the GUI front end to sane, which originally was run from the command line.  Open a terminal and type:



I believe you will get output showing it located in /etc/sane.d and /usr/share/sane

Yes, I tried that, and found a bunch of configuration-type files in etc/sane, and Xsane-type stuff in usr/share/sane.
And I quote:

 "Interesting"


The reason I think I don't have 'sane' installed on my machine is that Synaptic shows it as not installed (the "installed version" is blank)
Does this not mean that 'sane' is NOT installed? 
(if not, boy is my face red :) )

This is what started my whole thread....

I bought a Canon Lide60 scanner at a pawn shop, plugged it in my new Ubuntu install, and it worked. Wow.
I decided to install that fancy 'Xsane' front-end, and found it installed, and 'sane' as blank.

So that confused the jimminies out of me ( a highly technical term you young whipper-snapping computer users have yet to learn, I see), and I ended up here.

:popcorn:

---

### Post by kaibob on 2008-09-12
Deleted by Kaibob.

---

### Post by JKyleOKC on 2008-09-12
> **egalvan said:**
> 
The reason I think I don't have 'sane' installed on my machine is that Synaptic shows it as not installed (the "installed version" is blank)
Does this not mean that 'sane' is NOT installed? 
(if not, boy is my face red :) )

Actually, Synaptic's list appears to be obtained from the database of installed programs rather than by searching all possible locations for executables. I'd say that you DO have sane "installed" in that the program is present in your system and working, but it's "not installed" so far as Synaptic is concerned because it came in as part of the xsane installation. Without the sane executables, xsane could not work.

I just ran into a similar situation with legacy nvidia drivers that I installed using nvidia's own file rather than using Synaptic. They didn't show up as present in Synaptic; to get rid of them I had to search them out and rm them individually.

---

### Post by egalvan on 2008-09-12
> **JKyleOKC said:**
> Without the sane executables, xsane could not work.


I know I have Xsane, because I can run it. I was just mightily confused when Synaptic showed 'sane' as not present.

And I've finally understood the relationship between apt, apt-get, aptitude and Synaptic. Along with the workings of the data-base they use, and how installing/removing items "outside" of this framework can cause un-resolved problems. Many Linux installs died to bring me this information. :)

One step closer to Gnu/Linux Nirvana

:popcorn:

---

