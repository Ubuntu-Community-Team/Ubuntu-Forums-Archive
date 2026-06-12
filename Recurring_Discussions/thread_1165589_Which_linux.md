---
title: "Which linux?"
date: 2009-05-20
forum: Recurring Discussions
---

### Post by americano70e10 on 2009-05-20
I know you've probably seen thousands of posts like this but here's my question. I'm planning to install a linux distro on my friends computer (don't worry, I'm not forcing him to do it, he asked me to) but his computer is really old.. Like 10 years old. The hardware is a 850 mghz amd processor with 160 mb RAM and I believe a 16 mb graphics card, so REALLY old. SO I did some searching around to try to find a linux distro that would be easy to use and didn't have a very high system requirements. He'll basically be using the computer to listen to music, internet, MSN and word processor, so nothing too complicated. Is there a linux distro today that is able to deliver all that and not be very heavy? I did that test on that site (sorry can't remember the site) that would point out a good distro for me to use, and the result was for me to install opensuse. But I don't know, I though opensuse was like ubuntu if not heavier. I also though about xubuntu that would be lighter but I don't know if it's light enough. I'm welcome to any suggestion.

---

### Post by lisati on 2009-05-20
I managed to get Puppy Linux installed on a machine which was less well-endowed in the way of specs.

---

### Post by Marlonsm on 2009-05-20
Take a look at DSL (damn small linux). I've never tried it myself, but I've hard it'd run very well even on that computer

---

### Post by dmizer on 2009-05-20
> **americano70e10 said:**
> The hardware is a 850 mghz amd processor with 160 mb RAM and I believe a 16 mb graphics card, so REALLY old.

I have several laptops with those specs. Xubuntu works very nicely with them. I suggest Hardy rather than Jaunty though.

---

### Post by americano70e10 on 2009-05-20
Alright will give those a try. Thanks for your input.

---

### Post by Keithhed on 2009-05-20
> **lisati said:**
> i managed to get puppy linux installed on a machine which was less well-endowed in the way of specs.

+1

---

### Post by gymophett on 2009-05-20
Here are my top choices:
1) Crunchbang Linux
2) Puppy Linux
3) Xubuntu
4) Xubuntu, then change XFCE to LXDE and it will run like lightning. :)

---

### Post by XubuRoxMySox on 2009-05-21
[Crunchbang]("http://crunchbanglinux.org") is designed for those old machines and runs awesomely on mine. It is Ubuntu-based, so it'll be somewhat familiar to you. One of the reasons it's so quick is that has no desktop environment. Only the window manager (Openbox).

If you want to give it some "Windowsy" familiarity and simplicity, then add the uber-lightweight [LXDE]("http://lxde.org") desktop environment. It adds very little "weight" and makes Crunchbang look like Win98. Crunchbang and LXDE play nice together as long as you let PCMan (LXDE's built-in file manager) run the desktop.

Applications are found in */usr/share/applications* and appear as icons! Just drag and drop the ones you want to your desktop.

Wallpapers can be added to */usr/share/lxde/wallpapers* to customize it. 

This "customized Crunchbang" makes my old Gateway run at mind-bending speed, and LXDE makes it so simple that my family thought they were using Windows until I told them - "nope! That's Linux!"  Heh heh, I loved doing that.

-Robin

---

### Post by americano70e10 on 2009-05-21
Actually I have tried crunchbang linux here on my pc. But I don't know. While it was still (with no running applications) it used up 170mb of RAM. And with a limit of 160 mb on my friend's I'd say it wouldn't run smoothly on my friends computer. May be it's the way I set it up. But will give it a try with the things you mentioned.

---

### Post by snowpine on 2009-05-21
> **americano70e10 said:**
> Actually I have tried crunchbang linux here on my pc. But I don't know. While it was still (with no running applications) it used up 170mb of RAM. And with a limit of 160 mb on my friend's I'd say it wouldn't run smoothly on my friends computer. May be it's the way I set it up. But will give it a try with the things you mentioned.

Crunchbang probably used more ram because you have more available... Linux likes to use more ram if available to speed things up. On my 256mb laptop, Crunchbang only uses about 80mb. 

Still, I think your friend's computer is borderline for Crunchbang with only 160mb. I second the previous recommendation for Puppy or Damn Small.

---

### Post by mamamia88 on 2009-05-21
i really like dsl.  i installed it on my 10 year old pc and it was super fast loading almost entirely out of ram.  if all you need is a word processor, internet browser, and simple games you can't really go wrong.

---

### Post by XubuRoxMySox on 2009-05-21
[SIZE="5"][Slax]("http://slax.org")[/SIZE] is ultra light weight for very old hardware.

I played around with [Slax]("http://slax.org") for a bit too. That was super-duper [COLOR="Magenta"]lightweight[/COLOR] and fast, and uses a KDE-style desktop! It's not meant to be installed - you run it from a USB stick. I, however, being the playful little rule-breaker I am, actually installed it on a really old 'puter and it flies along at speeds approaching the **[COLOR="Green"]trans-warp[/COLOR]** threshold!

Here's how:

Download the "iso" file from [Slax]("http://slax.org") and write it to a CD (remember it's an *image* file, so don't just burn it as a data file).

Assuming you have a previous Linux installation on the drive, you can use those partitions and just delete the contents.

Then run Slax from the live CD. You'll be automatically logged in as root.

Before setting up Slax, delete anything already on the partition you will use for Slax. To find the partition, click "System," which will open the file manager. Then click "Storage Media." Following "Location," you'll see "System:/media/" and then what the computer calls the partition (something like "sda1"). Write that down, you'll need it later.

Copy and paste (it'll say "paste URL" - same thing) the two folders, "boot" and "Slax" from the CD to that partition on the hard drive (to find the CD, click the Up arrow).

Now we set up the boot loader: Open the terminal and type
```
cd ../mnt/(partition)/boot
``` (insert the computer's name for that partition you wrote down to where it says "(partition)." <ENTER>
Then ```
.liloinst.sh
``` <ENTER>

Turn the computer off and restart, and you'll be **[COLOR="Purple"]running Slax from the hard drive![/COLOR]** Just remember to remove the CD, LOL.

And remember to type ```
startx
``` at the start of every session to get it going.

I have it on an ancient old machine, but it's a little scary running as root. But that's a whole 'nother debate...

-Robin
With thanks to Guy Shipard for the tutorial [here]("http://natureheals.info/linux/slax/setuhd.html")

---

### Post by mohitchawla on 2009-05-21
Puppy linux.

---

### Post by SushiR on 2009-05-21
> **americano70e10 said:**
> I know you've probably seen thousands of posts like this but here's my question. I'm planning to install a linux distro on my friends computer (don't worry, I'm not forcing him to do it, he asked me to) but his computer is really old.. Like 10 years old. The hardware is a 850 mghz amd processor with 160 mb RAM and I believe a 16 mb graphics card, so REALLY old. SO I did some searching around to try to find a linux distro that would be easy to use and didn't have a very high system requirements. He'll basically be using the computer to listen to music, internet, MSN and word processor, so nothing too complicated. Is there a linux distro today that is able to deliver all that and not be very heavy? I did that test on that site (sorry can't remember the site) that would point out a good distro for me to use, and the result was for me to install opensuse. But I don't know, I though opensuse was like ubuntu if not heavier. I also though about xubuntu that would be lighter but I don't know if it's light enough. I'm welcome to any suggestion.
Have a look at Vector Linux: [http://vectorlinux.com/products](http://vectorlinux.com/products)

---

### Post by americano70e10 on 2009-05-21
> **snowpine said:**
> Crunchbang probably used more ram because you have more available... Linux likes to use more ram if available to speed things up. On my 256mb laptop, Crunchbang only uses about 80mb. 

Cool! I didn't know that!



I got some very good suggestions, I'm going to pass them on to my friend so he'll be able to choose. Thanks for the input guys!

---

