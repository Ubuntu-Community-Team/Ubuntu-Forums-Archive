---
title: "Ubuntu? Xubuntu? Zubuntu? Huh?"
date: 2013-02-01
forum: Recurring Discussions
---

### Post by puzzledinportorchard on 2013-02-01
This is a silly question, but - at this site it seems important to know which distribution, or flavor, or whatever, of Linux you are using.  The information page I got from the people (FreeGeek) I got the refurbished machine from, who were the ones who put the operating system on, says it's Ubuntu 12.04.1 LTS.  The screen that boots up just before the log-in screen says Xubuntu.  I tried uname -a but nothing is said either way.  Is there a command that will tell me?  I've no idea why it matters, but you good folk seem to think it does, so . . .

---

### Post by mike555 on 2013-02-01
Xubuntu has the classic top bar with a menu icon that looks like a mouse head ......

---

### Post by speechman on 2013-02-01
So I'm a complete newbie to Ubuntu/Linux and I'm also confused by the variants or flavors.  Zubuntu, Chrubuntu, Xubuntu.  

What does all that mean?  

Thanks!

---

### Post by puzzledinportorchard on 2013-02-01
> **mike555 said:**
> Xubuntu has the classic top bar with a menu icon that looks like a mouse head ......
Um - okay.  I'm sure that, with the fullness of time, I will understand the difference.  So I'm running Xubuntu.  And you're right.  I does look like a mouse-head.  Now I've got that image in my mind, I'll always look at that symbol and think, "It's wondering what the hell I'm doing."

And so am I.

---

### Post by BlinkinCat on 2013-02-01
Hi,  

Here is a little more on the subject - 

[http://www.ubuntu.com/project/about-ubuntu/derivatives](http://www.ubuntu.com/project/about-ubuntu/derivatives)

Googlubuntu is a good tool for finding out things - see link in my signature.

Cheers - :)

---

### Post by zealibib slaughter on 2013-02-01
> **puzzledinportorchard said:**
> Um - okay.  I'm sure that, with the fullness of time, I will understand the difference.  So I'm running Xubuntu.  And you're right.  I does look like a mouse-head.  Now I've got that image in my mind, I'll always look at that symbol and think, "It's wondering what the hell I'm doing."

And so am I.


You are not alone. I feel that way a lot.

---

### Post by Grinage on 2013-02-01
I felt that way too at first, but after awhile the quirks from each different flavor grow on you, and for basic core functions they are mostly exactly the same, the difference is the look, feel, and warm fuzzy feelings each different flavor gives you.  Xfe or Xubuntu and Lxe or Lubuntu tend to be lighter weight for older systems, so that you get the sensation of speed and power.

Welcome to your new linux life!

---

### Post by puzzledinportorchard on 2013-02-01
At least you nice people are making us klunks feel welcome, and marginally less bewildered.  For that, and the patience - Thanks!

---

### Post by BlinkinCat on 2013-02-01
> **puzzledinportorchard said:**
> At least you nice people are making us klunks feel welcome, and marginally less bewildered.  For that, and the patience - Thanks!

I think you will find one big happy family here -

Main thing to remember is to stay happy and join in - ):P

---

### Post by drawkcab on 2013-02-01
Welcome.  We're here to help.

Depending on what machine you have, you might consider reinstalling whatever version of 'ubuntu you want.  They're basically the same under hood but with different desktop environments, pre-installed applications and footprints.

---

### Post by puzzledinportorchard on 2013-02-01
Most of the troubles I'm having are either caused or made worse by the machine (not this one I'm on) being offline with no internet connection possible.  So I'm sticking with what works.  But I do miss Gnome. Yet maybe, some day.  Thanks again.

---

### Post by drunkenbrawler on 2013-02-02
Well, you dont need to fresh install ubuntu/Kubuntu etc. You can just add a desktop environment.

And for getting the release info, maybe you can use 

```
[aniket @ aniket-XPS-15z : ~]$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
[aniket @ aniket-XPS-15z : ~]$
```

---

### Post by Elfy on 2013-02-02
> Is there a command that will tell me? I've no idea why it matters, but you good folk seem to think it does, so . . . Can make a difference to some of the help you'd need and what we can expect you to see. 

```
 echo $DESKTOP_SESSION
```

will be more help to seeing what desktop you're using than

```
lsb_release -a 
```

which tells me I'm using Ubuntu ... I'm not :)

Few links

[http://www.engadget.com/2012/11/30/how-to-pick-a-desktop-environment-in-linux/](http://www.engadget.com/2012/11/30/how-to-pick-a-desktop-environment-in-linux/)

[http://en.wikipedia.org/wiki/Desktop_Linux](http://en.wikipedia.org/wiki/Desktop_Linux)

[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by tahdas on 2013-02-02
> **speechman said:**
> So I'm a complete newbie to Ubuntu/Linux and I'm also confused by the variants or flavors.  Zubuntu, Chrubuntu, Xubuntu.  

What does all that mean?  

Thanks!

ChrUbuntu is a customized version of ubuntu that will run on the chromebook.
[http://chromeos-cr48.blogspot.com/](http://chromeos-cr48.blogspot.com/)

---

### Post by craig10x on 2013-02-02
If you wouldn't mind a dock-like bar on the left which can auto-hide (gives you kind of a mac-osx type feeling) with a nice search function on the top of it, plus just 1 upper panel which is a global menu (which means the functions on top hide until you mouse over them and it also saves space)... then you might like the unity desktop which is what the main version of ubuntu has...you can see screenshots of it on the main ubuntu web site...

The unity dock is kind of like a "shortcuts taskbar" where you can easily place all your favorite and most used applications for quick "1 click" access... ;)

Very modern and kind of cool...and certainly a lot more intuitive then the new "windows 8" (lol)...

---

### Post by I2k4 on 2013-02-03
A bit confusing to newcomers used to Windows, to have to figure out that these derivatives refer mainly to the "desktop environment" as separate from Ubuntu the operating system.  Each of them is a separate project and some are closer to Ubuntu mainstream than others.  

The choice of derivative should depend on a) how much the user likes that desktop environment, b) hardware compatibility, c) what software the developers preinstall, since it wastes time to replace it all, and d) for those who don't like fresh installs of newer versions every few months, is that derivative going to provide long term support "LTS", since some don't (which I learned the hard way).

I tend to like XFCE but Xubuntu seemed to have trouble dealing with finding other storage devices on my netbook and Lubuntu worked well. It's a good point above, that you can simply install other desktop environments - I have KDE on the Lubuntu machine and access to some good alternative software through that.

---

### Post by Bucky Ball on 2013-02-03
Same base install for all the flavours, each one has different default applications and desktop environment, plain and simple.

You can make it less simple by changing any of the above until you wind up with a hybridised Frankenputer!

Have fun exploring, enjoy the learning curve and the forums. The muddy waters do clear and any probs you only need to post a thread. ;)

---

### Post by Bartender on 2013-02-03
I'd like to add a thing or two.

There are real differences between how the Desktop Environments work.  Some you'll like, some you won't.  The standard Ubuntu DE is the most fully-featured, but full-featured also means more work for the PC.  Generally speaking, every feature that adds convenience also adds complexity.

For instance, in Ubuntu you can middle-click your mouse on a file, then drag it to a new destination, and you'll get the Context Menu asking whether you want to copy or move.  Just like a right-click & drag in Windows.  Try this in Xubuntu and nothing happens.

Just yesterday, with the help of a forum member, I was trying to figure out how to create a basic home LAN between two Ubuntu PC's.  PC "A" was running Ubuntu.  On PC "B", an older unit, I'd originally installed Ubuntu, then installed the Lubuntu DE.  

On PC "A", when opening the Home Folder, there was a Bookmark for the local network in the left-hand column.  This small convenience helped me get started building the LAN.  On PC "B", running the Lubuntu DE, there was no Bookmark at all for the network.  I logged off of Lubuntu and into Ubuntu.  Presto change-o, there was the network Bookmark.

Google helped me figure out how to create a network Bookmark to PC "A" in the Lubuntu Home Folder, but it took a little bit of extra effort on my part that wasn't necessary when running the Ubuntu DE.

So, what I'm saying is that first impressions can be misleading.  You can install the Xubuntu DE on top of an Ubuntu install and see an immediate improvement in responsiveness.  But that responsiveness is largely because the Xubuntu DE has less of the "bells & whistles" provided by the fully-featured Ubuntu DE.  It's important to understand that when exploring some of the "lighter-weight" DE's.

---

### Post by Bucky Ball on 2013-02-03
On PC B you simply issue the command:

nautilus

... and you will have the same file manager. Sounds like you installed lubuntu-desktop on B and not the DE, lxde. Anyway ...

*Thread moved to **Recurring Discussions**.*

---

### Post by Max Blyss on 2013-02-03
Xubuntu or Lubuntu are both excellent places to start if you're totally new.  They are trouble free, and won't likely give you any confusion right away if you're running low spec stuff, or can't support compositing.

Also, a little more traditional in the desktop area.

(Not knocking Unity, it's just quite a departure if you've never used anything other than Win.)

---

### Post by craig10x on 2013-02-04
Although if you ever played around a bit with a mac in an apple store, and liked it, unity might not seem too strange, except that the "dock" is on the left side inside of the bottom of the screen, but it can "auto-hide" just like it does on a mac...
And it also has the "global menu" top panel, just like the mac does...

You can also make the icons on the unity dock much smaller, because by default they are kind of large (adjustment available in the system settings for that)...

---

### Post by montag dp on 2013-02-04
> **Bartender said:**
> I'd like to add a thing or two.

There are real differences between how the Desktop Environments work.  Some you'll like, some you won't.  The standard Ubuntu DE is the most fully-featured, but full-featured also means more work for the PC.  Generally speaking, every feature that adds convenience also adds complexity.

For instance, in Ubuntu you can middle-click your mouse on a file, then drag it to a new destination, and you'll get the Context Menu asking whether you want to copy or move.  Just like a right-click & drag in Windows.  Try this in Xubuntu and nothing happens.Small correction, Unity isn't really any more "fully-featured" than KDE; therefore Kubuntu is just as fully-featured as standard Ubuntu.  To your example, Dolphin (the file manager in KDE) gives a context menu just like you described.  On the other hand, Xubuntu and Lubuntu are lightweight desktop environments and could probably be considered less fully-featured.

In general, though, the different *untus are the same except for the desktop environment and installed software, as others have said.

---

### Post by mamamia88 on 2013-02-05
> **puzzledinportorchard said:**
> This is a silly question, but - at this site it seems important to know which distribution, or flavor, or whatever, of Linux you are using.  The information page I got from the people (FreeGeek) I got the refurbished machine from, who were the ones who put the operating system on, says it's Ubuntu 12.04.1 LTS.  The screen that boots up just before the log-in screen says Xubuntu.  I tried uname -a but nothing is said either way.  Is there a command that will tell me?  I've no idea why it matters, but you good folk seem to think it does, so . . .

Different gui but same base system.  For example xubuntu is ubuntu with the xfce gui.

---

### Post by deadflowr on 2013-02-05
Actually, is there such a distro as zubuntu?

And if so, what desktop does it run?

---

### Post by Bucky Ball on 2013-02-05
> **deadflowr said:**
> Actually, is there such a distro as zubuntu?

And if so, what desktop does it run?

Just let your fingers do the walking ...

[http://www.omegamoon.com/blog/index.php?entry=entry081030-074514](http://www.omegamoon.com/blog/index.php?entry=entry081030-074514)

Doesn't look like it's seen much action in awhile, though.

---

### Post by Peripheral Visionary on 2013-02-05
Actually I pronounce Xubuntu like Zoo-**bun**-tu.  Like Xylophone or Xenia.

12.04 runs better and faster on my old computer than Windows XP did brand new, and it's alot easier to use.

---

