---
title: "&quot;Downgrading&quot; from 12.10 w/ no Previous Install. How to?"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by PaulOctopus on 2013-03-18
(First-time Linux experience.)
Over the weekend, I installed 12.10 on an old pc, and I'm afraid I've bitten off more than the pc can chew.
Compaq desktop w/ 512MG/RAM, 1.7G processor.

The pc has an NVIDIA graphics card which has caused some problems. (I can't get the display size correct, so I don't have a launch menu bar. It's off to the left somewhere.) 
In researching fixes for the card issue, I've encountered some opinions that maybe Ubuntu 10 would fit this machine better. (Other opinions are welcome.)
If I were to try Ubuntu 10, or another version, what is the best way to get there from my current install?
(Note: Still have Windows installed, but wanting to dump it as soon as I get Linux running well.)

---

### Post by fantab on 2013-03-18
You will have to reinstall. 

With only 512MB RAM Ubuntu won't run, you need [Lubuntu Alternate Install]("https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall").

---

### Post by mörgæs on 2013-03-18
Which processor exactly are we dealing with?

---

### Post by deadflowr on 2013-03-18
Personally, I'd go to Ubuntu and download 12.04 for it's longer support. Not having to reinstall or upgrade for four years over close to a year is a lot nicer.
Having said that, It's unclear if downgrading will actually solve the graphics problem.

You could give us more information on the set up. Like Graphics Card  and CPU.
At this point we know it's an nvidia card but not much else. Looky here for a little help on getting nvidia card working on  Ubuntu:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Another thing is, Ubuntu is compatible with multiple desktops. Sometimes systems run better with alternative set ups.

You could try installing one or more.
The most widely used would be
Kubuntu
Xubuntu
Lubuntu
Gnome/Classic/Shell

The second post here might give you help in the department:
[http://askubuntu.com/questions/141015/install-desktop-environments-or-use-different-distributions](http://askubuntu.com/questions/141015/install-desktop-environments-or-use-different-distributions)

---

### Post by mörgæs on 2013-03-18
No, forget about Ubuntu. You have already tried 12.10 without luck, and with 512 MB it does not surprise me.

Lubuntu is your best choice.

---

### Post by quequotion on 2013-03-18
You can downgrade, but it's going to be rough.

The process is the same as the upgrade I posted [here]("http://ubuntuforums.org/showthread.php?t=2125296&p=12556231#post12556231") except that:
1. Swap "precise" for "quantal" and vice-versa everywhere.
2. Pin release 12.04 instead of 12.10 (this is the key, as it will force all available packages to downgrade).

There will be complications, like packages that only or don't exist in 12.04 getting in the way of a dependency chain.

---

### Post by jim Kane on 2013-03-18
personalty with you low sys spec i would recommend 
XFCE 4.10 Puppy Linux
[http://sourceforge.net/projects/latestxfcepuppy/](http://sourceforge.net/projects/latestxfcepuppy/)
try the live CD first,

---

### Post by PaulOctopus on 2013-03-20
Thanks, everybody for the replies. I have found many tips on this site and others which have given me many options to consider.
I've got some good Windows chops, but this is my first foray into Linux-World.  
So far, Linux-world reminds me of an enormous salad bar. You can't just say, "how do I make a salad?" Every problem has many possible solutions. It's almost endlessly customizable, so it's up to me to experiment and discover. 

I spent my free time yesterday reading and researching, so I haven't made any changes yet.
 First, I have some extra memory sticks somewhere, so I should be able to add another 256mg--maybe another 512. I'll have to check my parts box.
My graphics card is a problem. It's an nVidia Vanta\VantaLT. Very old. Last driver update in 2005, I think. I'm going to try to live with it. Today, I'll just add the memory.
Then, I'm thinking about Lubuntu or Xubuntu. It's pretty obvious that 12.10 will always be a hassle for this old 'puter.
I'm sure I'll have more questions later. This site has been very helpful so far. Thanks, again.

---

### Post by engineerarun on 2013-03-20
Can you try installing openbox on top of Ubuntu 12.10? Steps here -
[http://linuxg.net/install-openbox-on-ubuntu-12-10/](http://linuxg.net/install-openbox-on-ubuntu-12-10/)



> **PaulOctopus said:**
> Thanks, everybody for the replies. I have found many tips on this site and others which have given me many options to consider.
I've got some good Windows chops, but this is my first foray into Linux-World.  
So far, Linux-world reminds me of an enormous salad bar. You can't just say, "how do I make a salad?" Every problem has many possible solutions. It's almost endlessly customizable, so it's up to me to experiment and discover. 

I spent my free time yesterday reading and researching, so I haven't made any changes yet.
 First, I have some extra memory sticks somewhere, so I should be able to add another 256mg--maybe another 512. I'll have to check my parts box.
My graphics card is a problem. It's an nVidia Vanta\VantaLT. Very old. Last driver update in 2005, I think. I'm going to try to live with it. Today, I'll just add the memory.
Then, I'm thinking about Lubuntu or Xubuntu. It's pretty obvious that 12.10 will always be a hassle for this old 'puter.
I'm sure I'll have more questions later. This site has been very helpful so far. Thanks, again.

---

