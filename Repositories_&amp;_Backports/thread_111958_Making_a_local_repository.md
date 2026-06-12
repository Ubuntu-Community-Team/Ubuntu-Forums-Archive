---
title: "Making a local repository ?"
date: 2006-01-03
forum: Repositories &amp; Backports
---

### Post by GAJ on 2006-01-03
Hello all,

I wonder if possible to make our own repository on our local HD within Ubuntu ?

The gall is to put some foreign ubuntu deb packages into this "local owner" repository then use it to update or install within Synaptic instead of manual installation (as we have to do with Firefox 1.5 or OOo 2 for instance).

I don't find anywhere something about that on 
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) nor 
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto) : is it not possible ?

Thanks,

---

### Post by KingBahamut on 2006-01-03
[http://doc.gwos.org/index.php/ISO_image_source](http://doc.gwos.org/index.php/ISO_image_source)

Hope this helps.

---

### Post by GAJ on 2006-01-04
Hello Bill and all,

Thank you Bill, but it is not exactly what I search... I would like to mount a normal directory as repository, to be able to push easy my own deb packages into it, then rebuild easy the deb list of this directory as "local repository", then update Synaptic, then install these own deb packages via Synaptic to remain the deb system correct for my Ubuntu system.

How can I do that ?

---

### Post by dutch_boi1 on 2006-01-04
hello,

i have been wanting to do that also..because alot of my own burnt cd's wont work in synaptic , because it says it cant find any deb packages :S. so i was wondering also if it is possible to make a folder on my dekstop, fill it with downloaded .deb files, then add that folder into the repositories in synaptic, so it searches the folder , and can hopefully update from there...installing the manual way through the terminal is very annoying:mad: 

thankx

---

### Post by Seth on 2006-01-04
Hi,

See this wikipage I wrote for the official wiki.

[https://wiki.ubuntu.com/LocalAptGetRepositoriesTrivial]("https://wiki.ubuntu.com/LocalAptGetRepositoriesTrivial")

It's intended for developers, but will work for a personal repository too. Just update your own sources.list instead of the pbuilder's copy.

Also, you don't need to set up a webserver. Just use a **file:/** URL in sources.list. The important part is the **scan.sh** script; you'll need it to set up your own repository.

---

### Post by GAJ on 2006-01-06
Thanks Seth, all seems to work within synaptic (update is ok, the software appears good within), but on the last step when I install the software I get : 
<<W: error file:/home/guy/LocalRepository/binary/binary/openoffice.org-base_2.0.1-2_i386.deb
  File not found>>
So what's wrong ?
Thanks again for your time,

---

### Post by GAJ on 2006-01-06
Well a 1/2 solution : look at the path, there is 2 'binary' folders... Since I have only one, I have put a link to it within it... And thats works fine now.

I wonder why this problem of 2 same folders within the install path - not written in sources.list but in error while installing - so if you have an explanation, thank you !

BTW : thank you too for this tutorial, this helped me a lot understanding a bit these thinks... :)

---

