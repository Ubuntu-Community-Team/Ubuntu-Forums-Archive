---
title: "kdevelop konsole missing in 8.10"
date: 2008-11-03
forum: Programming Talk
---

### Post by zenkaon on 2008-11-03
Hello,

I have just upgraded to 8.10 and find that the handy konsole at the bottom of kdevelop is missing. Yet from a terminal (in gnome) I can type konsole and up pops a konsole.

So konsole is installed and works. Kdevelop is installed and works, yet the 2 don't seem to play together.

Does anybody know what I have to do to get konsole to work down the bottom of kdevelop?

---

### Post by tovarish on 2008-11-05
I have the same problem. I think this is because konsole is part of kde4 and kdevelop is part of kde3. Unless 8.10 figures out a way to include konsole from kde3 it wont work with kdevelop.

tovarish

---

### Post by tendu on 2008-12-23
Same issue... I've tried with both KDE and GNOME environment and this is the same, the konsole tab is present in kdevelop but that's it!

This functionality is important (I think), they have to fix that! Well, they should :)

---

### Post by zdenek_ on 2008-12-31
Hello,
I had same problem with Mandriva 2009.

After installing kdebase-konsole-3.5.10-6mdv2009.0.i586.rpm
(package with kde3 konsole), Konsole tab is visible.

(* Package with kde4 konsole is also installed. 
   No package remove necessary *)

Zdenek

---

### Post by Infloop on 2008-12-31
I had the same problem on ubuntu 8.10 and the problem was solved.
I uninstalled konsole 4.3 that I had and install konsole 3.5 instead using the link here

[http://launchpadlibrarian.net/13473504/konsole_3.5.9-0ubuntu7_amd64.deb](http://launchpadlibrarian.net/13473504/konsole_3.5.9-0ubuntu7_amd64.deb)

and my konsole is now visible on kdevelop.

---

### Post by Infloop on 2009-05-05
The link to download the konsole package is
[http://packages.ubuntu.com/hardy/konsole](http://packages.ubuntu.com/hardy/konsole)

---

### Post by varundeshpande on 2009-08-16
hi,
i have same problem but i am using ubuntu 9.04. kdeveloper 3.5.3 
i am unable to install konsole 3.5

please help me

---

