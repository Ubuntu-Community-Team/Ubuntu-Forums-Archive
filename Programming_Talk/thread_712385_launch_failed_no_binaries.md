---
title: "launch failed no binaries"
date: 2008-03-01
forum: Programming Talk
---

### Post by StOoZ on 2008-03-01
I keep getting this message in eclipse (latest version)
this is when im trying to create a new C++ project (I've downloaded the C++ version of eclipse), and empty project.
I add a new cpp file, create a simple 'hello world' code, and press 'run' and I get this messege.
now , when I use the already made templates that are included, it works like a charm.
any idea how to solve this??

---

### Post by mike_g on 2008-03-01
Maybe its telling you that you need to compile the project before running it? I don't know, I have never used eclipse myself.

---

### Post by StOoZ on 2008-03-01
Well im a newbie, but not that stupid, of course I compiled it.
:(

---

### Post by amingv on 2008-03-01
> **StOoZ said:**
> Well im a newbie, but not that stupid, of course I compiled it.
:(

And linked/built it?
Not saying you're stupid, but stuff happens sometimes...

<edit>
> **StOoZ said:**
> ...when I use the already made templates that are included, it works like a charm.

Also, pressing the compile button doesn't ensure it's compiled; double check for syntax errors.
</edit>

---

### Post by StOoZ on 2008-03-01
well your help is much appreciated ! 
but I decided to dump eclipse, and moved to netbeans.
eclipse and I started on the wrong foot.. :)

---

### Post by tommyhakinen on 2008-04-19
Try adding the correct Binary Parser. Project -> Properties -> C/C++ Build ->Settings ->Binary Parsers, check the "PE Windows Parser"

---

### Post by applejay on 2008-09-04
thanks tommyhakinen! adding that binary parser worked for me!

---

### Post by feewang on 2008-09-24
I have done it as you said. But It still appear that message.And I work it on ubuntu.

---

### Post by kiddinge on 2009-12-31
This worked for me:

sudo apt-get install g++

---

### Post by jakehockey10 on 2010-03-08
> **kiddinge said:**
> This worked for me:

sudo apt-get install g++


What does this mean?

---

### Post by Zugzwang on 2010-03-09
> **jakehockey10 said:**
> What does this mean?

This command is to be typed in using a terminal window. It calls the "sudo" program, which is installed along with Ubuntu, to call the "apt-get" program which has the purpose of installing new packages (among others). The command written thus installs the default C++ compiler in GNU/Linux, namely "g++" from the GNU compiler collection. 

Note that in Ubuntu, it does not suffice to install the "g++" package for compiling your first C++ program (thus, the statement by kiddinge is misleading). Rather you should install the "build-essential" package as only this makes sure that other files needed for building C++ programs are installed as well.

---

### Post by oshamajik on 2011-02-25
If you do not have g++

sudo aptitude install build-essential

Then restart eclipse and try running your code (make sure you build the project first).

---

