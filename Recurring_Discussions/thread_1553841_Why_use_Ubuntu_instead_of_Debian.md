---
title: "Why use Ubuntu instead of Debian?"
date: 2010-08-15
forum: Recurring Discussions
---

### Post by fremantle on 2010-08-15
ive been using ubuntu for like about a year now. i know that ubuntu is based on debian, like many other distros. so this just hit me, why would i use ubuntu when i can use debian itself?? i mean its like how im using ubuntu, instead of linux mint (which is based on ubuntu).

what are the differences between debian and ubuntu? why should users prefer ubuntu over debian?

---

### Post by fatality_uk on 2010-08-15
Not really a support question! It has been asked many times and a lot of answers given. The fact is, it's a preference.

Check this link
[http://lmgtfy.com/?q=differences+between+debian+and+ubuntu](http://lmgtfy.com/?q=differences+between+debian+and+ubuntu)

---

### Post by cariboo on 2010-08-15
This has been asked and answered so many times we've lost count. Moved to Recurring.

---

### Post by admiralspark on 2010-08-15
It's all a matter of preference. 
Simple answer:
Debian is more stable. Debian is committed to open source and Ubuntu (Canonical) is committed to being easy-to-use. Debian is run by independent programmers etc, and Ubuntu is run by a company. Oh, and Ubuntu has deviated from Debian so much that they're not really 100% compatible anymore.

---

### Post by uRock on 2010-08-15
Saying Debian is more stable is like saying Windows XP is more stable than Windows 7. Newer software is bound to have glitches/bugs, whereas old stuff is ussually more stable.

Ubuntu has newer software and makes installing and maintaining the system mush easier. Once you get Debian installed, you have to add PPAs and install the supported versions of the programs you want.

Honestly, if you are that interested in Debian, then install it in another partition or in a VirtualBox to see how it works. Do keep in mind that the virtual install take s the fun of installing drivers out of the equation, which makes a big difference when trying to install to the HDD.

---

### Post by Kellemora on 2010-08-15
Hi Fremantle

In a nutshell?

Ubuntu is/was virtually Turn-key, as in a package deal......
Still is if you use 8.04 Hardy!
Debian you have to install almost everything manually........
And learn WHAT to install too!  And what will work with it as well.....

TTUL
Gary

---

### Post by aysiu on 2010-08-15
I have an HP Mini 1120nr, and for that, Ubuntu is a lot easier to install and use.

You can read [here](http://www.psychocats.net/ubuntucat/debian-stable-on-the-hp-mini/) about the difficulties I had trying to get Debian working on the HP Mini.

---

### Post by XubuRoxMySox on 2010-08-15
They seem to be more and more different from each other with every new release. Ubuntu modifies the kernel itself as well as some really wicked cool stuff that is unique to the Ubuntu family. **The installer**, for instance! The Ubiquity installer is uniquely Ubuntu's (and it's derivatives). Debian is only now finally getting a graphical installer that doesn't come close to Ubiquity's simplicity and ease.

Hardware "just works" right out of the box for Ubuntu users, where Debian users have to find and install software for their hardware to work. That's part of what Ubuntu has done with the **kernel**.

I built my own Debian (Testing, Xfce) from scratch using the netinstall. Very easy to install (but not nearly as simple and "newbie friendly" as Ubuntu's Ubiquity). I put in only what I need and use, and nothing that I didn't want. But it took days of Googling and trial and error to find all the software and drivers and stuff I needed to get sound and other peripherals working properly. *After the better part of a week's work*, I finally had my perfect home-brewed Debian mixture that worked. And what I ended up with was not all that different from Xubuntu!! That was kinda humbling. I could have saved myself all that trouble and had a near-perfect "Debian Testing/Xfce" mixture working right out of the box in about 10 minutes, simply by using Xubuntu.

Ubuntu "tames" Debian. It makes Debian's awesomness, beauty, and power available to us "ordinary users" who would rather run applications than run the OS. I really doubt that any non-technically inclined newbie who just wants a great OS would invest all the time and effort and trial-and-error that it took me to make Debian work as wonderfully as Xubuntu does.

That's the difference.

Ubuntu is "**Linux for human beings.**" Some folks in the Debian community would like to make Debian easy too, but there is such resistance to "dumbing it down" that others have had to step in and do what  Debian would not (yet). Ubuntu is *just one among many* to step forward and bring Debian's awesomeness to the desktop, making it available and usable to us ordinary folks. There are many others. Like Mepis, Sidux, Knoppix, Crunchbang, and many more.

-Robin

---

### Post by fremantle on 2010-08-15
hm. i totally get it now. but why wont debian try to make their distro more user friendly and out-of-the-box like ubuntu? and another thing, does ubntu releases depend on debian releases? .. correct me if i am wrong, but i dont think debian is released as frequently as ubuntu. so how does it all work out.

---

### Post by Bluesan on 2010-08-15
> **fremantle said:**
> hm. i totally get it now. but why wont debian try to make their distro more user friendly and out-of-the-box like ubuntu? and another thing, does ubntu releases depend on debian releases? .. correct me if i am wrong, but i dont think debian is released as frequently as ubuntu. **so how does it all work out.**

Why not try it, then you'll know. You can get the latest stable version here:

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

And, here's a good tutorial to get you started:

[http://www.howtoforge.com/the-perfect-desktop-debian-lenny](http://www.howtoforge.com/the-perfect-desktop-debian-lenny)

Let us know how you come out...

---

### Post by NightwishFan on 2010-08-15
The reason I stopped using Debian is the release schedule. I do not like the concept of rolling releases to get newer software and the new two year cycle of Debian Stable is a bit out of date for my laptop. Backports are available of course though I prefer the Ubuntu way to be just left of bleeding edge. :)

Also, Ubuntu packages are generally configured with sensible defaults when Debian packages usually are like blank slates. For example, Compiz on Debian has no options enabled and must be manually configured. Ubuntu has Compiz set up to a usable default, and can then be configured at will.

Also rumors that Debian is lighter are only half true. Debian does have less installed for all of it's desktop meta packages, but the same can be done manually on Ubuntu. I managed to get an Ubuntu server down to using only 13mb of RAM as reported by free -m. (A few modules and initramfs items blacklisted).

That being said, they both have advantages and disadvantages in policy, and are much different than say Ubuntu/Mint are. Really it is up to the users own needs to which they use, and to decide specific questions should be asked.

---

### Post by aysiu on 2010-08-15
> **fremantle said:**
> but why wont debian try to make their distro more user friendly and out-of-the-box like ubuntu? Debian's goal isn't to be user-friendly. Both Debian and Ubuntu are trying to strike a balance between usability and Free software ideals. Of the two, Debian tends to stick closer to the Free software ideals, so the out-of-the-box usability suffers a little relative to Ubuntu. > and another thing, does ubntu releases depend on debian releases? .. correct me if i am wrong, but i dont think debian is released as frequently as ubuntu. so how does it all work out. Debian has multiple branches (stable, testing, unstable, experimental). Stable is the official release and happens once every few years. Unstable is "rolling" (which means it's updated all the time, not once every few months or every few years). Ubuntu is based on Debian unstable.

---

### Post by fremantle on 2010-08-15
so... can we say that ubuntu is similar to linux mint?? coz linux mint is based on ubuntu and it adds extra packages, softwares and codecs to make it more user friendly...now thats what ubuntu is doing with debian,

---

### Post by aysiu on 2010-08-15
> **fremantle said:**
> so... can we say that ubuntu is similar to linux mint?? coz linux mint is based on ubuntu and it adds extra packages, softwares and codecs to make it more user friendly...now thats what ubuntu is doing with debian,
Linux Mint is much more like Ubuntu than Ubuntu is like Debian.

I know some Minters aren't going to like me saying this, but Linux Mint is basically Ubuntu with a different theme, some proprietary codecs preinstalled, one taskbar instead of two, and a couple of little extra graphical menus (like one for whether desktop icons or shown or not).

---

### Post by fremantle on 2010-08-15
> **aysiu said:**
> Linux Mint is much more like Ubuntu than Ubuntu is like Debian.

I know some Minters aren't going to like me saying this, but Linux Mint is basically Ubuntu with a different theme, some proprietary codecs preinstalled, one taskbar instead of two, and a couple of little extra graphical menus (like one for whether desktop icons or shown or not).

thank you! thats exactly what i think about linux mint. its like my current lynx with a greenish theme and iconset plus a some extras. i do not know how it became so popular.. but on the other hand, linux mint served the community greatly by spreading ubuntu to new linux users.

---

### Post by Nick_Jinn on 2010-08-25
> **uRock said:**
> Saying Debian is more stable is like saying Windows XP is more stable than Windows 7. Newer software is bound to have glitches/bugs, whereas old stuff is ussually more stable..

I am not sure that is a sound argument. I am not 100% sure that XP is more stable or will be for long, but I am not sure that pointing out a reason why something is more stable is an argument against it being more stable. The reality is the reality and labeling it doesnt change it. 


Windows XP with service pack 1 is older and LESS stable than XP with Service Pack 2. 
Mint is more updated and more stable 'out of the box' because its NEWER, but Ubuntu only needs the updates to catch up.


I think there are more reasons why Debian is more stable than Ubuntu besides that it came out first. Debian will likely always be more stable than Ubuntu and Ubuntu will likely always be an easier introduction for novices.

---

### Post by dandoz on 2012-09-28
You know what is really annoying?  Googling the phrase "why not use Debian instead of Ubuntu" and the first hit is this forum, where the question was asked and everyone is piling on and screaming "Google it!"

---

### Post by overdrank on 2012-09-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

