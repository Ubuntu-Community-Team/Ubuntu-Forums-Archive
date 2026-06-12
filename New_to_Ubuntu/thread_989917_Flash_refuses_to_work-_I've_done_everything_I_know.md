---
title: "Flash refuses to work- I've done everything I know. Have Gnash."
date: 2008-11-22
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-11-22
I have Ubuntu down, most of it is just a learning curve, a bit convoluted, but I'm getting (?) it.

I have almost everything working, I think, EXCEPT FLASH. I cannot believe how hard it is to get flash to work. It's driving me nuts.

I read everything I could find, followed the ubuntu guide, etc. Made sure multiverse is enabled. Ran sudo get-apt install flashplugin-nonfree, have Gnash Shockwave flashplayer enabled in firefox, STILL cannot see flash. Before, nothing showed up in youtube. Now, there is a white space instead of "you don't have flash installed", and it seems to be gnash, but no picture, no video, no sound, nothing. I am lost. Can anyone help? I really did try looking up everything I could find before I posted, trying not to be a total bum.

I'm guessing it's another case of a magic line of code I must recite in terminal and magically things get fixed, without me having any clue of what I just did.

---

### Post by Monotoko on 2008-11-22
Yepp, magic line of terminal code :P

first code:
```
sudo apt-get remove flashplugin-nonfree
```

then this is the code you need
```
sudo apt-get install ubuntu-restricted-extras
```

Il tell you what you just did too:

sudo = do as root
apt-get = get a package from apt
install = install the package you get

ubuntu-restricted-extras -> a good package that has java, flash, etc in it

Basically we have just removed the old version of flash you installed, and installed the extras package

---

### Post by tuskenraider on 2008-11-22
i went and downloaded the deb from adobe.....  worked for me...  oh and i had a sound issue but there was a fix for that too that i found on the forums.  Sorry i couldnt be more help!


tusken

---

### Post by BastardNamban on 2008-11-22
Forgive me, I forgot to mention a couple things-
Of course, first I went to adobe's site, downloaded the .deb, 2x actually,
and that didn't work. I know that flash only works for x86.


Monotoko, actually, I had already installed restricted extras, but I did exactly what you said, and did both commands in order.

Still, same situation.

And that is why I am still confused.

---

### Post by Monotoko on 2008-11-22
hmm, when you installed the restricted extras, did it give any sort of error message while installing flash?

---

### Post by BastardNamban on 2008-11-22
(ME@COMP):~$ sudo apt-get remove flashplugin-nonfree
[sudo] password for (ME): 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 111654 files and directories currently installed.)
Removing flashplugin-nonfree ...
(ME@COMP):~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
_______________________________________________________________

That's all I got.

---

### Post by BastardNamban on 2008-11-22
....So no, no errors. I'm as puzzled as you are!

---

### Post by vdalmonte on 2008-11-22
your solution works fine for me. the only flash site that don't work on my comp is myspace

---

### Post by silverwolf636 on 2008-11-22
> **vdalmonte said:**
> your solution works fine for me. the only flash site that don't work on my comp is myspace

That's the same place I'm having problems: MySpace.

---

