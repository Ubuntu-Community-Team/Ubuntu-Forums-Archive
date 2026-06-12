---
title: "Problem with NetBeans installation"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ^^viktor^^ on 2008-08-25
I`m trying to install Netbeans 6 and the first time I started it i forgot to install JavaSDK so i closed it and installed Java.
The next time I ren it i got this
[[IMG]http://img209.imageshack.us/img209/3341/screenshotbo6.png[/IMG]](http://imageshack.us)
I reinstaled java two times and I even installed NetBeans form Synaptic and when I start it I get the same thing.

What chould be the problem!?

---

### Post by Crafty Kisses on 2008-08-25
Do you have the package **libsvn-java** installed?

---

### Post by ^^viktor^^ on 2008-08-25
No I didn`t have that. :)
But installing it didn`t do anything.

---

### Post by Crafty Kisses on 2008-08-25
Post the results of > java --version

---

### Post by ^^viktor^^ on 2008-08-25
This is what i get:
> The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm


---

### Post by mrmorris on 2008-08-25
Are you by any chance running Compiz?

---

### Post by ^^viktor^^ on 2008-08-26
Yes I am.
Is that a problem?

---

### Post by ^^viktor^^ on 2008-08-27
Anyone?? :(

---

### Post by AxiomShell on 2008-08-27
> **^^viktor^^ said:**
> Yes I am.
Is that a problem?

Compiz and Swing don't get along sometimes.

Are you using OpenJDK or Sun's JDK?

---

### Post by ^^viktor^^ on 2008-08-27
Sun`s. But the last time I had Swing with Compiz and it was working fine.

---

### Post by AxiomShell on 2008-08-27
> **^^viktor^^ said:**
> Sun`s. But the last time I had Swing with Compiz and it was working fine.

Ok. Make sure you have at least Java 6 Update 1 and follow these instructions:

[http://ubuntuforums.org/showthread.php?t=515942]("http://ubuntuforums.org/showthread.php?t=515942")

Then post the outcome here.

---

### Post by paris_alex on 2008-10-04
Hi! i've got the same problem... with Java applications in general... you need to export AWT_TOOLKIT before running the java app:

export AWT_TOOLKIT=MToolkit

Alternatively, you can switch to metacity before running. Check out the thread [here]("http://ubuntuforums.org/showthread.php?t=802228&highlight=netbeans+metacity").

Do feedback if this helps.. ;-)

[Paris]("http://www.loveparishotel.com/")

---

