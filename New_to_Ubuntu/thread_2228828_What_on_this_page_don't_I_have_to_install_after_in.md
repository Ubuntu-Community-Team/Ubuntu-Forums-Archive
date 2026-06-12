---
title: "What on this page don't I have to install after installing Trusty Tahr 14.04?"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by J Tinsby on 2014-06-09
hello,

This page [http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr](http://howtoubuntu.org/things-to-do-after-installing-ubuntu-14-04-trusty-tahr) is telling me that I had better run all these commands after my install of ubuntu 14.04. Are they really all necesary? I hate to install a lot of extraneous stuff that will take up space and never be used. Yes I am brand new to Linux and I assume that everyone knows more than I at this point, but I'm learning a bit at a time. 

At the least I'd like to have vlc player working, so far that's proven fruitless, but aside from that glitch is all the listed stuff a 'must have' ? I have already tried the kde DE thinking that might make vlc work but it didn't, I ended up blowing out the partitions and re-installing ubuntu. No harm done it just cost me a bit of time that's all.

Thank you!


J T :D

---

### Post by QIII on 2014-06-09
Hello!

You don't *have *to install any of that.  You may decide that you *want *to install *some *of it.

Everyone has their own list of "must haves" that they put together and publish on the web.

I would recommend synaptic because it is a much more finely grained tool than the Software Center, but you don't *have *to install it.

Just bookmark that page if you'd like, run Ubuntu for a while, figure out what you'd like to have and install it.  We're here to help.

---

### Post by Vladlenin5000 on 2014-06-09
I&#7743; glad you asked because I disagree with many (too much actually) parts of your linked article. The article should be understood as a (very) personal opinion, it isn't 'gospel', far from it.
Especially for a newbie: ALWAYS install the software versions already in the Ubuntu repositories therefore ignore everything about VLC and GIMP (and others). If you want install them from the Software Center.
Other comments:
 - Start with #8 of that list. It's ridiculous to suggest that only after messing a lot with the OS.
 - You don't need Y PPA Manager, the GNOME repository (unless you intend to install the GNOME desktop environment), the Web8 PPA for Oracle Java (unless you really need that proprietary Java flavor instead of the open-source one which is included) within the ubuntu-restricted-extras package) and you certainly don't need PPAs for VLC or GIMP.\
 - You need [LibDVDCSS]("http://www.videolan.org/developers/libdvdcss.html") for playing commercial "copy-protected" DVDs but PLEASE ignore that rubbish stemming from the authors obsession with cutting edge software. After installing VLC from the software center, please use this instructions and this instructions only: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
**- You don't need #2 and I strongly advice against it**
- You don't need Chrome - obviously - but it's generally safe (FOSS purists will recommend Chromium instead; Chrome is based on Chromium but includes proprietary code from Google). It's up to you.

Here's my suggestions:
1. You can select and install the additional drivers - if applicable - right after this first boot after installation; reboot when done. Then...
2. Do ```
sudo apt-get update && sudo apt-get dist-upgrade
```
3. Install any software you want from the software center ONLY. You can install other software not included in Ubuntu by means of PPAs or other methods only when you understand the implications and risks and, most important, when you know how to revert those changes if something goes wrong.

---

### Post by deadflowr on 2014-06-09
+1 to what QIII stated.
You don't need any of that stuff, or at least most of it.
synaptic is a good thing to have, makes install/remove/updating easy; when you learn how to use it.
(And it's really easy to learn)

But to a finer point, what about vlc wasn't working?
Was it not loading the player, or was it not playing the contents?

---

### Post by DogMatix on 2014-06-09
I wouldn't install anything else until you realise you need it. As QIII mentions, just use your fresh Ubuntu for a while if it doesn't provide somehing you want thats the time to start looking at installing more stuff. 

There always seem to be a bunch of "Things to do after installing <new ubuntu version>" articles. I'd say the answer is nothing until you want to.

---

### Post by Impavidus on 2014-06-09
Let me see...
1: I didn't.
2: I didn't.
3: I added 1 PPA, but not one of those mentioned.
4,5,6: You should get a pop-up automatically if updates are available.
7: I installed maybe three of those packages, so they are not really essential. Note that gimp is included by default on Xubuntu, which I use.
8: I didn't need any.
9: I didn't.
10: Occasionally some clean-up can be good, but that list of commands doesn't really make sense.

---

### Post by J Tinsby on 2014-06-10
> **deadflowr said:**
> +1 to what QIII stated.
You don't need any of that stuff, or at least most of it.
synaptic is a good thing to have, makes install/remove/updating easy; when you learn how to use it.
(And it's really easy to learn)

But to a finer point, what about vlc wasn't working?
Was it not loading the player, or was it not playing the contents?

hi deadflower,

Thanks to you and ***all the others*** who replied to my query, I thought there was too much stuff there that 'needed;' to be installed, especailly after a fresh install!

To answer your question about vlc it was doing a bit of both. I got vlc from the USC and then I installed the 2 libraries that were called for and ran the line about restricted material. On a first boot and upon insertion of a dvd, vlc would open and play the dvd just fine, IE: all menus worked, good sound etc. If I ejected the disc and waited a bit, then put the disc back in the tray, vlc wouldn't open or if it did I got a message from the program saying " vlc cannot play disc on /dev/sr0 see log for details ( paraphasing here). If I tried to run the dvd by using the 'open disc' command in vlc it would fail too with a similiar message. I should mention too, that at times the icon in the dock would remain "open" even if the physcial tray was in fact closed. If I rebooted linux, it would behave the same way, play the dvd one time only and then quit. After all that over and over again, I installed the kde DE thinking that another DE would/might make it work. It did not help anything, but I learned a lot from the experience! lol and rather than risk running all that code to remove kde, I simply blew out my partitions and started over! To date I have not installed vlc or any of the necessary libraries or commands. I note that I do have 2 optical drives but only used /dev/sr0 for all the testing so as not to confuse the results. I will say that using the second drive didn't work either, even if i changed the path statement to point vlc to it.

Hard for me to imagine I am the only one in the world that has had this problem,and if it's a bug, why hasn't anyone caught it and got it sorted? I like vlc because normally it will play virturally any file type. I don't as a rule sit in front of my monitor and watch movies, I simply was using the dvd as a test since it was handy. But still it should work, imho. I never got to try other forms of media I was so caught up in making dvd's play! <sigh>

Thank you all very much! I am happy to be in a forum where there is so much help available for someone like myself who knows little or nothing about linux. I always wanted to try it out and now here I am doing it! If only I'd started years ago I'd be so much futher along in my understanding. I like to work with music files and edit photos and was curious to see what I could do in that respect in linux, compared to the MS OS. I am aware of Audacity and Gimp and will be trying to use GPG since I use PGP on XP ( that's all I use XP for btw) the system is a triple boot XP, Win & and Ubuntu fwiw.

Regards and thanks!

J T

---

### Post by LastDino on 2014-06-10
I generally resorted to those ''what to do lists'' when I came over from Windows, it is good place to learn how to install and uninstall software, plus few other things like names of popular software you may or may not want as most users use something similar on Windows and these usually serve as good Linux counterparts. 

If VLC isn't working for you, try MPlayer, it is there in software center. I'm one of the synaptic fans, so plus one there as well. Get used synaptic and your life will be much easier :3


On that note, you only need to learn how to  from these lists, there is no need to follow these kind of lists to T to install anything on any platform.

---

### Post by J Tinsby on 2014-06-10
HI Dino,

I see it there in the USC and there is an add on called "Graphical front end for su"............. something to get as well or give it a miss?

Thanks for the tip!

J T

---

### Post by LastDino on 2014-06-11
Sorry, I made a typo in last post, its a ''SMplyaer'', though there is software called MPlayer as well.

---

