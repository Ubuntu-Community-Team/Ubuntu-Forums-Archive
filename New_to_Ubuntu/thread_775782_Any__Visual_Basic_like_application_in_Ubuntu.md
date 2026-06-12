---
title: "Any  Visual Basic like application in Ubuntu?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by kshtjsnghl on 2008-04-30
Hi everyone
  
  I had to build some project and for that i needed visual basic or rather visual studio to that effect. 
  
   But I dont want to switch to windows again so i just wanted to know if there is any application that is similar to visual basic.

thanks

---

### Post by joselin on 2008-04-30
Try [Gambas]("http://gambas.sourceforge.net/")


Regards

---

### Post by aeiah on 2008-04-30
whilst gambas looks quite nice, im assuming this is for school, yes? if so they'll probably want to look at your source code etc and whilst gambas is similar to visual basic, it isnt the same, and it isnt compatible. they may have problems with anything you submit using gambas, or indeed using anything that isnt visual basic.

---

### Post by pedro_orange on 2008-04-30
> **kshtjsnghl said:**
> Hi everyone
  
  I had to build some project and for that i needed visual basic or rather visual studio to that effect. 
  
   But I dont want to switch to windows again so i just wanted to know if there is any application that is similar to visual basic.

thanks

You might want to Dual boot / virtualize a Windows environment to achieve this. Virtuabox and Vmware are good tools.

Mono is about, but I think thats mostly C#. Might be wrong tho.

---

### Post by Dylnuge on 2008-04-30
> **pedro_orange said:**
> Mono is about, but I think thats mostly C#. Might be wrong tho.

Mono actually does VB quite nicely:

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

That should get you started.

You might also want to check out some other languages, since VB is very OS-Specific. How about Python?

---

### Post by kshtjsnghl on 2008-04-30
hey i saw that page and really its a nice application

 but on the download page they dont have corresponding package for ubuntu while those of red hat , open suse,etc. are there
 
 how and which one should i download??
 and then how to install it.

---

### Post by WinterWeaver on 2008-04-30
isn't mono in the repos?

EDIT: just checked on Edgy... Monodevelop is in the repos.

---

### Post by pedro_orange on 2008-04-30
> **WinterWeaver said:**
> isn't mono in the repos?

EDIT: just checked on Edgy... Monodevelop is in the repos.

On hardy:

```
pedro@pedro-laptop:~$ apt-cache search monodevelop
monodevelop - C/C++/C#/Boo/Java/Nemerle/ILasm/ASP.NET Development Environment
monodevelop-nunit - NUnit plugin for MonoDevelop
monodevelop-versioncontrol - VersionControl plugin for MonoDevelop
stetic - GNOME and GTK+ GUI designer
```

---

### Post by kshtjsnghl on 2008-04-30
Ohh i am sorry 
i got it now
Actually i just looked on the site and not in my synaptics..:)
thanks for the reply...

---

