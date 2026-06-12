---
title: "HP Compaq nx6125 - Install Ubuntu or should install something lighter?"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by jleb on 2014-04-14
Hello,

I am new to this forum so please bear with me if I haven't appropriately followed the guidelines for posting.

I have been given wonderful assistance by Varunendra on another post successfully enabling me to obtain a wireless connection live trialling Ubuntu on my old HP Compaq nx6125. However, in that post moderator Mörgæs suggested my laptop might be too weak and something lighter such as X/Lubuntu (13.10 or  14.04) might be preferable. I've found that during live trialling using a USB flash Ubuntu has been fine but lately after being on it for a couple of hours  the cursor has been starting to move erratically and the screen has  then frozen, requiring me to power-off and re-boot. This no doubt not helped by  my memory being almost full. I also realise that Ubuntu will work much  more smoothly once I have installed it. As the support for Windows XP currently on my system has  been withdrawn I am planning to erase the disc before installing Ubuntu,  which will then also free up a lot of memory. 

Still, I am brand new to this  world and as a beginner I have solely been reading up on Ubuntu as it seems to have the most material at hand to assist me. Considering the age of my laptop  - 8 to 9 years old! - should I be considering something lighter?

Many thanks,

---

### Post by su:bhatta on 2014-04-14
Hi and welcome to the forums. 

You can have a look at Xubuntu, which is medium heavy on resources and Lubuntu which is very light.
Other options for you can be go for a minimal install of Ubuntu and follow it with a Window manager install like XFWM4.

What are the specs of your current system?
Removing XP, now that will not free up memory only disk space. 

[http://lubuntu.net](http://lubuntu.net)
[http://xubuntu.org](http://xubuntu.org)

---

### Post by jleb on 2014-04-14
Hi Bhattabhishek,

Sorry, I meant disk space, not memory! 

My laptop is very basic: AMD Turion 64 Mobile ML-30 processor, 1 GB memory, 55GB hard drive (almost full!)

---

### Post by QIII on 2014-04-14
Hello!

(It goes without saying that you need to back up any important files before you do any of this!)

Even lighter than Lubuntu is an Ubuntu derivative called [Bodhi Linux]("http://www.bodhilinux.com/").  The minimun requirements are very low and the resources utilized are very minimal.  Bodhi will probably run suprisingly fast on that machine.  Bodhi uses the Ubuntu repositories and you can install synaptic on it for package management.

Bodhi has a very active and passionate community.  They should be quite willing to help you along.

I'm not an Ubuntu evangelist, so I don't mind recommending another distribution that might be a more satisfactory choice for those specs.

Best wishes.

---

### Post by su:bhatta on 2014-04-14
No problems jleb.

Have a look at both Xubuntu and Lubuntu. 
Lubuntu should really speed things up.

Download a iso from the link I gave in the first thread and 'Try Lubuntu'  you should see marked improvement in speed.
Other non-Ubuntu options are there too, but really, Lubuntu is worth the first try.

Edit: QIII beat me to it :)

---

### Post by 3rdalbum on 2014-04-14
One gigabyteof Ram and that CPU is enough for Ubuntu.

However, to read between the lines, you probably have an old AMD GPU on that computer, which is not supported well on Linux for 3D. Ubuntu really doesn't work well without good 3D support. On that basis I would recommend Xubuntu or Lubuntu, which both function fine without 3D support.

Ubuntu will work, but the lower 3D capability will cause it to be a bit slow.

---

### Post by jleb on 2014-04-14
Thanks all for your quick and informative responses!

Yes, the video card is a ATI RADEON XPRESS 200M SERIES (from my laptop specs), which, despite being largely computer illiterate, I understand is quite slow.

So the consensus does appear to at least try Xubuntu or Lubuntu. I have been spending my whole time wrapping my head around Ubuntu - it's all a bit daunting, as I am not computer-savvy - but I understand this will have given me a good grounding, despite these operating systems exhibiting different desktops.

---

### Post by QIII on 2014-04-14
Be aware that AMD/ATI has discontinued Linux driver support for that GPU, so don't try to install the proprietary fglrx driver -- or you will have a significant emotional event.

Just stick with the default open source driver that is installed when you install your OS.

---

### Post by jleb on 2014-04-14
Thanks very much for the heads up and for all the feedback!

As I am brand new to all of this and hardly proficient in computing I'll trial Lubuntu to get a feel  - I'll wait to see how that goes but as a raw beginner I'm still leaning towards Ubuntu due to the comfort of the amount of reading material available, including downloadable manuals and reference books. But I'm downloading the Lubuntu iso as I type this, so we'll see!

Thanks again!

---

### Post by jleb on 2014-04-14
I'm currently in Lubuntu trialling it and early impressions are that it is all very comfortable as it is very reminiscent of Windows - maybe a bit too comfy as it lacks the excitement of the new and thrill of discovery that  Ubuntu and its different desktop offers. I'll keep trialling both, though, and see if things change. Lubuntu seems quite responsive and I understand it might be best for this ageing laptop, and yet...

---

### Post by mörgæs on 2014-04-14
If you want something which is both light and diffferent from the classic Windows-inspired desktop you could also try Bodhi Linux.

---

### Post by slooksterpsv on 2014-04-14
Look into elementary OS.

---

### Post by jleb on 2014-04-15
OK, I've given quite a few OS live trails a spin. Elementary is too similar to a certain iOS (I'm personally not a big fan of that aesthetic - yes, I know), Lubuntu is a bit bare bones and I'm not enjoying the Ubuntu desktop as much but Xubuntu seems to hit the sweet spot. I will also admit on this forum that Linux Mint seems very user-friendly but I think I'm ready to move on from a Windows XP-type desktop.

If I went with Xubuntu I'd also be looking to download LibreOffice Writer, VLC and a better music player (RhythmBox?), so would I be better off installing Ubuntu then choosing the KFCE desktop?

---

### Post by mörgæs on 2014-04-16
The desktop environment does not restrict your choice of applications. Mix and match!

---

### Post by Canterwood on 2014-04-16
Like mörgæs said, all the *buntu distro's use the same base so you can use all applications regardless of what desktop environment you use. There's a major difference between Linux and Windows that requires some explanation you might benefit from.

Contrary to Windows, Linux has a core that can function wonderfully without any graphical front-end. You could conceivably operate your computer entirely from the command line. In a lot of situations this way of doing things is a lot more powerful than using a GUI (= Graphical User Environment) but for the average user having one is at least comfortable.

Here's where it gets exciting: Once you have installed a Linux operating system of choice, you're free to choose whatever graphical front-end that fits your needs. In your case using a light one like XFCE or LXDE would be preferable, but there's a wealth of choices available to you. Let's say you've installed Ubuntu and are not happy with Unity's performance (Unity is the default desktop environment for Ubuntu), then you could start a terminal and type:

```
sudo apt-get install xubuntu-desktop
```

And this command will install the complete Xubuntu experience for you. Just log out, click the sprocket icon next to your username and choose Xubuntu.

Like I said, there's a ton of options, so don't be afraid to Google around for a new and exciting one! Best of luck, and remember to have fun using Ubuntu!

---

### Post by su:bhatta on 2014-04-16
You can also try:

```
sudo apt-get install gnome-session-flashback
```

See if you like that Desktop Environment=DE.

There are many other choices which are very different than anything you have used.
I use two very uncommon DE's: FVWM-crystal, and Windowmaker. Others that come to mind are *Box DE's like Openbox.

These are low on resources and very customizable, But then again there is a steep learning curve.
I repeat, you really have to read up or you will wind up in a desktop, where you have no clue to get anything to work.
In case you have the time and want to play around, you can give a try.

---

