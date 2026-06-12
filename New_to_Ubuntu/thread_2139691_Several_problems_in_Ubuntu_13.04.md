---
title: "Several problems in Ubuntu 13.04"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by Sunlight7 on 2013-04-27
Hello there!

I have encountered a couple of problems since i started with Ubuntu 13.04 yesterday.

The first problem is that Spotify don't respond to my media keys. I have googled a bit but i don't know how to do half of it. I found this guide: [http://kothar.net/blog/spotifydbus.html](http://kothar.net/blog/spotifydbus.html) which people seems to like, but i don't know what to do with it. Lol. So if anybody could just write a very, very simple walkthrough, that would be perfect.

The second problem is that i would like to edit my top-right corner meny. For example remove my network-icon and Ubuntu One-icon to save space.

My third problem involves Truecrypt, which i have downloaded a .tar.gz file with a file inside. I have edited it so that it could run as a program, but when i click it, it opens in gedit or something.

My fourth problem is that my graphics card fan is running at high speed. I am using the x-org driver cause the AMD driver didn't work with my two screens at all. The card is two 5770 in crossfire.

My fifth question is how i can open the file browser in admin/sudo? Before i could just type "sudo nautilus".

---

### Post by grahammechanical on 2013-04-27
> [COLOR=#000000]My fifth question is how i can open the file browser in admin/sudo? Before i could just type "sudo nautilus".[/COLOR]

Did you not get an error message advising to run sudo apt-get install gksu?

When you have installed gksu then ```
gksudo nautilus
``` will work. Apparently gksu is depreciated. It supposed to be replaced by something called pkexec (safer apparently) but it does not work on 64bit Ubuntu just yet.

I doubt very much that we can edit the notifications in the top panel. That is the design of Ubuntu that will go right through to Ubuntu mobile devices.

---

### Post by Frogs Hair on 2013-04-27
> [COLOR=#000000]The second problem is that i would like to edit my top-right corner meny. For example remove my network-icon and Ubuntu One-icon to save space.[/COLOR]

There is some options in the dconf editor to hide some indicators an the nm applet is one of them. I have Gnome Classic/ Gnome shell installed so the one displayed may not apply to unity.

---

### Post by Sunlight7 on 2013-04-28
Thanx! :D

---

### Post by Sef on 2013-04-28
To make sure that all of your problems get answered, it is best to post each one in a separate thread with an appropriate title.

---

