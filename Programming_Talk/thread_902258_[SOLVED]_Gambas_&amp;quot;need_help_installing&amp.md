---
title: "[SOLVED] Gambas &amp;quot;need help installing&amp;quot;"
date: 2008-08-27
forum: Programming Talk
---

### Post by red13 on 2008-08-27
I have tried every way to sunday to install this program. I followed the instructions on the website "all of them" also downloaded the .tar pkg that later told me I needed a bunch of other files that I can't find to get.
I have tried the deb repository "doesn't work" tried the pkg in current Ubuntu repository "no luck".
So whats up peeps is this a inside crowd app or what? Why all the secrecies and need for jumping through hoops just to use a vb style program?
I like the vb style of programming and don't have any intrest in learning another language.
Any help for my piece of mind would be great!!!!
I am currently running a c2duo system with hybrid studio,compiz,metacity,GTK2,Gnome desktop.

Thanks in advance :)

---

### Post by Kadrus on 2008-08-27
Do you have build-essential installed?
```
sudo apt-get install build-essential
```
```
sudo apt-get update
```
```
sudo apt-get install gambas gambas2
```
This should work,if it doesn't;post the output.

---

### Post by red13 on 2008-08-27
Have the build-essential, however with having all the repositories that come with Ubuntu I can't seem to locate gambas.

---

### Post by cmay on 2008-08-27
> have the build-essential, however with having all the repositories that come with Ubuntu I can't seem to locate gambas. 

i think its called gambas2 now. i have had it but i could not figure it out.
its in the official ubuntu repo and you should be able to locate whit the add remove programs menu.
hope it helps.

---

### Post by red13 on 2008-08-27
Yeah tried that no go,missing files for the gambas2 in synaptic.
I mislabled this thread it should of been gambas2 instead of gambas guess the fustration of failed attempts at installing something that is included in the repositories in uncomplete form made me weary and unattentive to what I was writing.

thanks for the interst though :) 
the struggle continues

---

### Post by red13 on 2008-08-27
problem solved it appears I was 2 steps ahead of the instructions over here:[http://gambasdoc.org/help/install/ubuntu?show](http://gambasdoc.org/help/install/ubuntu?show).
guess all I needed was to step back breathe and recheck my steps :)

---

