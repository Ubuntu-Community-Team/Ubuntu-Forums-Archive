---
title: "Ubuntu really slow, other questions..."
date: 2008-10-19
forum: New to Ubuntu
---

### Post by cjmabry25 on 2008-10-19
Well, since this is my first post I'd like to say Hi, and that Ubuntu is amazing.:)

Anyways, I installed Ubuntu 8.04 from a Live CD, got everything working as it should, but it is REALLY slow. I ran Windows XP Media Center Edition on this PC before, and it was very fast. But now, when i try to open, for example, gedit and Firefox with multiple tabs, it is very slow. I have compiz-fusion installed with desktop cube and some other things enabled, and Firefox constantly goes black-and-white, not responding, if I open multiple tabs or, for instance, try to click on the applications, places, or System buttons at the top of the screen. I installed the AMD64 version of Ubuntu because I have an AMD Athlon 64 processor. Did I go wrong here? Or is my computer just not fast enough to run ubuntu with Compiz-Fusion? I'd really appreciate some steps to figure out what is making my computer so slow. Like something to type into the terminal or something? And I'm, if you haven't already noticed, a Linux noob. I've searched the forums for this same problem, but the answers were a little confusing and I, with my current knowledge, am having a hard time applying them to my situation. 

Thanks

System Specs:
Dell Dimension C521 w/
Ati Radeon x1300 Video Card
512 mb RAM
AMD Athlon 64 3200+

---

### Post by anubhavrocks on 2008-10-19
Can you disable Compiz and see if its affects the performance?

---

### Post by cjmabry25 on 2008-10-19
> **anubhavrocks said:**
> Can you disable Compiz and see if its affects the performance?

I can disable all of the effects manually in the Compiz options window, but how do i disable the whole program? Maybe go into system monitor and end the processes? Sorry, again, I'm a Linux noob :(

And thanks for the extremely fast response

---

### Post by luctor on 2008-10-19
press ALT+F2 keys on your keyboard.
enter 'metacity --replace' (without the quotes)

that's it: compiz is disabled
I think that disabling desktop effects in preference->appearance does the same.

I also thought that my Ubuntu was a bit slow, so I disabled compiz. Didn't have any effect on the speed though.
I'm now running Intrepid Beta (8.10) and I think it feels a bit faster.

---

### Post by luctor on 2008-10-19
Oops, just read your specs .. 512 mb ram ..
get at least 1gb ..
your system is probably using the swap partition all the time ..
Or maybe you could install a lighter version of ubuntu called Xubuntu. Haven't tried it myself though

---

### Post by cjmabry25 on 2008-10-19
> **luctor said:**
> Oops, just read your specs .. 512 mb ram ..
get at least 1gb ..
your system is probably using the swap partition all the time ..
Or maybe you could install a lighter version of ubuntu called Xubuntu. Haven't tried it myself though

Ya, I know, 512 mb is pretty low. I'm upgrading to a gig, maybe a gig and a half soon. It's wierd though. It's not always slow. I just enabled a butt-load of effects on Compiz- everythings running fine. I guess it's just when I try to multi-task, which is obvious. I could do this in windows though... I guess Compiz puts a strain on system use. Thanks for your help though. More RAM, here I come!

And while I'm here - I'm trying to install LMMS. I downloaded the .deb from the lmms site, ran it, but I get an error - "some dependencies could not be satisfied:lmms-common' or something like that. I went to synaptic, installed lmms and lmms-common, so does this install lmms? If so, where can I find it to run it? Even if I try to run the .deb after this I still get dependences errors :(

Thanks SOOOO much for your help so far!

---

### Post by Christmas on 2008-10-19
Compiz requires a pretty powerful video graphics card, so you'd probably be better off with Compiz disabled (that is, if you have a weak graphics card). I also recommend to try KDE, which for me was always ten times faster than GNOME (Kubuntu 8.04 LTS is the distribution with KDE3).

About LMMS: isn't it included in the repositories? In Debian's Lenny repositories it is. Try:
```
sudo apt-get install lmms
```
If you want to try and compile and install the latest version from [here](http://lmms.sourceforge.net/), use:
```
sudo apt-get build-dep lmms
```
Then uncompress the source, cd into the directory and use
```
./configure
make
sudo make install

```
Also, read [here](http://lmms.sourceforge.net/wiki/index.php?title=Installation). Hope this helps.

Edit: Now I see you already installed it via Synaptic. Try ALT+F2 and type *lmms*, it should run. You can see where applications are installed by typing in a terminal:
```
whereis application_name
```
For example, *whereis lmms*, then run it either as /usr/bin/lmms or just lmms (the second works because the system searches for it in the directories in your $PATH, an environment variable which includes /usr/bin too.

You may also try Audacity, *sudo apt-get install audacity* (or install it from Synaptic, it's the same thing).

---

### Post by cjmabry25 on 2008-10-19
> **Christmas said:**
> Compiz requires a pretty powerful video graphics card, so you'd probably be better off with Compiz disabled (that is, if you have a weak graphics card). I also recommend to try KDE, which for me was always ten times faster than GNOME (Kubuntu 8.04 LTS is the distribution with KDE3).

About LMMS: isn't it included in the repositories? In Debian's Lenny repositories it is. Try:
```
sudo apt-get install lmms
```
If you want to try and compile and install the latest version from [here](http://lmms.sourceforge.net/), use:
```
sudo apt-get build-dep lmms
```
Then uncompress the source, cd into the directory and use
```
./configure
make
sudo make install

```
Also, read [here](http://lmms.sourceforge.net/wiki/index.php?title=Installation). Hope this helps.

Edit: Now I see you already installed it via Synaptic. Try ALT+F2 and type *lmms*, it should run. You can see where applications are installed by typing in a terminal:
```
whereis application_name
```
For example, *whereis lmms*, then run it either as /usr/bin/lmms or just lmms (the second works because the system searches for it in the directories in your $PATH, an environment variable which includes /usr/bin too.

You may also try Audacity, *sudo apt-get install audacity* (or install it from Synaptic, it's the same thing).

Alright thanks! It's already installed and I just typed LMMS and now It's started! Thanks again, and I just wanna say this is the fastest and most helpful responses I have ever received on any forum. I hope  to learn more about Linux and become a regular here! :) See ya!

---

### Post by tuberculo on 2008-10-21
My system is very slow too. Firefox takes more than a minute to open. The symptoms are similar to yours.

---

### Post by damispyderbyte on 2008-10-21
I have the same system as yours, and it all runs very quickly. Make sure you have up to date ati drivers. Even with 512 it should zip along.....
Have you tried KDE or Xbuntu?

---

### Post by tuberculo on 2008-10-21
I don't think the problem is memory, cause I have 2 GB.

---

