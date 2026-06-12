---
title: "Lightest &amp; fastest version of Linux?"
date: 2010-09-08
forum: Recurring Discussions
---

### Post by wombatvvv on 2010-09-08
Hey guys,

I am forced into a crappy XP/Outlook setup at work. I have no idea why, but this runs like an absoulte dog. It takes about 10 minutes just to boot up, and all applications (Photoshop, etc.) run horrible.

The machine I have isn't great, but it's not horrible: a dual-core E2160 at 1.8Ghz with 3GB Ram.

I thought at-least good enough that I could run Ubuntu in a virtual machine and set it up as my development environment. Apparently not to be. It installs and runs just fine, but it runs like a dog, just like Windows. Huge screen-tears on page redraws, etc. and simple programs like web browsers take 30sec+ just to load up. Heaven forbid I try and load two programs at once ... like Firefox and Thunderbird. I'm tapping my fingers for minutes.

Anyway, I also installed Windows 7 in the VirtualBox and was quite surprised to see it ran much more nicely than both my native XP version and also much better than Ubuntu.

Is Windows 7 more lightweight, fast and efficient than Ubuntu? I wouldn't have guessed so, but it looks like it.

What is the lightest and fastest version of Linux that can still be used for development purposes? (I'd want to install Netbeans, etc.)

---

### Post by bodhi.zazen on 2010-09-08
Tons of options, I like Slitaz.

Lots of thread on the same topic, google, distrowatch ...

---

### Post by NightwishFan on 2010-09-08
Speed is in the eye of the beholder. When most people say speed, they generally mean how fast applications load. I agree, some apps load slower on Ubuntu because it does not have a dedicated preloader. Perhaps something for Canonical to look at.

---

### Post by krimzonstarr on 2010-09-08
I second(third?) the DistroWatch idea. If you have the experience, and don't mind "experimenting," you can always try "Linux From Scratch." You build your own system from the kernel up! Also, Mint just released Linux Mint Debian Edition, which can be much more bare-bones than Ubuntu.

If you'd like to stick with the Ubuntu-flavors, there are a few options such as: Lubuntu and Xubuntu.

[http://distrowatch.com/]("http://distrowatch.com/")

---

### Post by wojox on 2010-09-08
What do you have for a graphics card/chip in that thing?

---

### Post by Dragynn on 2010-09-18
Slitaz. And the xvesa version will boot on anything, i would be willing to bet that if i still had my old Commodore 64 that Slitaz would fire right up, lol!

---

### Post by murderslastcrow on 2010-09-18
Tiny Core Linux. Feather Linux and Damn Small Linux are around the same, and quite light (work on 64 MB of RAM in my experience). If you've got under 32 MB of RAM, you should probably just hash out the ten bucks for a crappy desktop with 128 MB of RAM and run some e17 on dat shiz.

---

### Post by snowpine on 2010-09-18
For best performance, you need to install Linux to the hard drive and boot natively. Running in Virtualbox will not unleash the full capabilities of your hardware in my experience.

To answer your specific question, TinyCore (11mb), SliTaz (30mb), or Puppy (130mb) are good choices.

---

### Post by kaldor on 2010-09-18
Woah, anybody else see this weird forums theme?!

On topic, take a look at LMDE (Linux Mint Debian Edition). Not the fastest/lightest, but surely speedy.

---

### Post by Spice Weasel on 2010-09-18
MicroCore.

Or if the command line scares you, try TinyCore, Damn Small or Puppy. Maybe even Crunch Bang for user friendlyness?

Running Ubuntu in a VM on a computer that can barely handle XP will result in instalag. Even Live CDs aren't very good for judging performance, try a RAM distribution.

---

### Post by Ahava591 on 2010-09-19
I would recommend Crunchbang.

-Wait for the Debian version to get out of alpha status.


As for development, I can't see any reason you couldn't add whatever you need to work with using #!.

---

### Post by Rasa1111 on 2010-09-19
is it possible for you to boot from a USB drive?
Ubuntu runs really quick on a nice flash drive. 

 My PC also ran super slow on XP.
Until I would clean the heck out of it, or do a fresh install,
but it was always back to a crawl within a week or two. 

Ubuntu though (full install), runs soo fast I can;t believe it!
Before I got Ubuntu, My dad wanted to try and install windows 7 on it , to see if that would help,
but this thing would barely handle that.
Not much better than XP, or worse,  was the verdict. lol

Then I (re)found Ubuntu..
and it made this old thing like new again, literally. 
Crazy stuff. 

 But maybe a flash drive loaded with Ubuntu would do you good,
if you can do that.
But, i know my ole machine doesnt even give the option to boot from USB. :lol:

---

### Post by mantisdolphin on 2010-11-07
A little late here, but I put Peppermint OS (based on Ubuntu, using Openbox/LXDE) on a six or seven year old Celeron machine with 640MB RAM and it's running the thing beautifully.  I tried Puppy (Lucid 5.1), love it, zippy and wonderful, but a distro can be limited by the ease with which you can access the software repositories.  Trying to find .pet packages of programs I wanted (for a kid's machine) took me too much time.  Peppermint accesses the significant Ubuntu repositories "out of the box," and provides an easy way to add or try out lots of different applications.  

Peppermint seems comparable to Lubuntu or Crunchbang.  You can go lighter and faster, but in the end you need apps too and there is value in not having to spend too much time finding and applying them to your zippy OS of choice.

---

### Post by samjh on 2010-11-07
> **Ahava591 said:**
> I would recommend Crunchbang.

Definitely a +1 for Crunchbang.  My system was only about 200MB at boot-up, and that was with compiz enabled.  Most other distros clock up about 290MB at least.

And because it has a Debian base, there are tons of applications to choose from, and fantastic architectural support as well.

---

### Post by shuttleworthwannabe on 2010-11-07
my vote also goes for Lubuntu--this distro has a future for the old machines, with all the glory of ubuntu repo's.

Only problem is it does not come with what I call essentials of running cloud apps-e.g. if I am behind a proxy, no network proxy exists, so no cloud. (Yes, I know here is a CLI for this, but is not the point).

Lubuntu viva!

---

### Post by The Real Dave on 2010-11-07
[LUbuntu]("http://linuxexpresso.wordpress.com/2010/10/19/moving-swiftly-on/")
[http://linuxexpresso.wordpress.com/2010/11/02/the-cry-of-wolves/](http://linuxexpresso.wordpress.com/2010/11/02/the-cry-of-wolves/)
[Archbang]("http://linuxexpresso.wordpress.com/2010/10/18/archbang-thoughts/")
[Madbox]("http://linuxexpresso.wordpress.com/2010/10/26/another-day-another-distro/")
Crunchbang

all the above get my vote, as being great lightweight OSs :) The above link to short reviews on my site, which will give you the necessary links to download locations and the like. Crunchbang is not yet reviewed officially, but it's a distro I've used quite a bit, and I love Statler :)

---

### Post by bonixavier on 2010-11-07
Puppy is very nice.

If you want something more powerful, but still light and fast, go with Arch.

---

### Post by Gremlinzzz on 2010-11-07
> **wombatvvv said:**
> Hey guys,

I am forced into a crappy XP/Outlook setup at work. I have no idea why, but this runs like an absoulte dog. It takes about 10 minutes just to boot up, and all applications (Photoshop, etc.) run horrible.

The machine I have isn't great, but it's not horrible: a dual-core E2160 at 1.8Ghz with 3GB Ram.

I thought at-least good enough that I could run Ubuntu in a virtual machine and set it up as my development environment. Apparently not to be. It installs and runs just fine, but it runs like a dog, just like Windows. Huge screen-tears on page redraws, etc. and simple programs like web browsers take 30sec+ just to load up. Heaven forbid I try and load two programs at once ... like Firefox and Thunderbird. I'm tapping my fingers for minutes.

Anyway, I also installed Windows 7 in the VirtualBox and was quite surprised to see it ran much more nicely than both my native XP version and also much better than Ubuntu.

Is Windows 7 more lightweight, fast and efficient than Ubuntu? I wouldn't have guessed so, but it looks like it.

What is the lightest and fastest version of Linux that can still be used for development purposes? (I'd want to install Netbeans, etc.)

Sounds like a commercial for windows 7 and a slam for ubuntu .u don't want help go with your choice  Windows 7.

---

### Post by NightwishFan on 2010-11-07
Windows 7 is slower than Ubuntu on 512mb of ram. :) I have happy to find this out. We do have catching up to do in some areas though.

---

### Post by irv on 2010-11-07
> I am forced into a crappy XP/Outlook setup at work. I have no idea why, but this runs like an absoulte dog. It takes about 10 minutes just to boot up, and all applications (Photoshop, etc.) run horrible.
> I also installed Windows 7 in the VirtualBox and was quite surprised to see it ran much more nicely than both my native XP version and also much better than Ubuntu.
In your OP you made the above two statements, and based on them I would like to ask a couple of questions. Do you work for a big company or a small one? the reason I as is because I don't know if you have a IT dept. that takes care of your PC's. If your PC will run Win7 in a VirtualBox, why not install it fresh on the HD and then do a clean install of Ubuntu on it's own partition. You can even create a separate NTFS partition to share files between both OS'.
The next question would be, will your employer let you do this? If not get a netbook or laptop and take it to work, that way you would not have anything personal on a company PC.
I was in a IT position when I was working, and we would not let the employees put personal thing on computer because we were responsible for licensing issues. Again, I do not know your circumstances.

---

### Post by Shining Arcanine on 2010-11-07
> **NightwishFan said:**
> Speed is in the eye of the beholder. When most people say speed, they generally mean how fast applications load. I agree, some apps load slower on Ubuntu because it does not have a dedicated preloader. Perhaps something for Canonical to look at.

Gentoo Linux can be made to match the eye of the beholder to the best ability that open source can be made to match such a thing. It only requires a little more effort on the part of the end-user in terms of understanding and maintaining the system and much more effort in terms of installing the system for the first time.

---

### Post by NightwishFan on 2010-11-07
To be honest I doubt that a little unless you sacrifice functionality and cut other corners. (Such as disable certain compile options that some may want or need).

---

### Post by bodhi.zazen on 2010-11-08
> **Shining Arcanine said:**
> Gentoo Linux can be made to match the eye of the beholder to the best ability that open source can be made to match such a thing. It only requires a little more effort on the part of the end-user in terms of understanding and maintaining the system and much more effort in terms of installing the system for the first time.

I tend to disagree with that as well. Gentoo takes more effort to learn and maintain, especially if you want to "optimize" it for "speed". Most optimizations, IMO, do not add much and you can match the speed with a minimal install of most any distro and add only what you want.

I used to use Gentoo, it is great for learning, but it takes a long time to maintain, IMO, and, again IMO, watching gentoo compile gets old after a while.

---

### Post by LeMeun on 2010-11-10
out of the blue question, can we install slitaz applications such as tazpkgbox, wifibox,... on ubuntu?
are they both debian base OS?

---

### Post by smellyman on 2010-11-10
> **LeMeun said:**
> out of the blue question, can we install slitaz applications such as tazpkgbox, wifibox,... on ubuntu?
are they both debian base OS?

slitaz is independent

---

### Post by LeMeun on 2010-11-11
too bad my wifi is working on slitaz but not on Ubuntu 10.04 lts, the wifibox detect it and load the right firmware and driver without problem which does not append with Ubuntu my favorite OS.
link to my [thread]("http://ubuntuforums.org/showthread.php?t=1618092").

---

### Post by Shining Arcanine on 2010-11-11
> **wombatvvv said:**
> Hey guys,

I am forced into a crappy XP/Outlook setup at work. I have no idea why, but this runs like an absoulte dog. It takes about 10 minutes just to boot up, and all applications (Photoshop, etc.) run horrible.

The machine I have isn't great, but it's not horrible: a dual-core E2160 at 1.8Ghz with 3GB Ram.

I thought at-least good enough that I could run Ubuntu in a virtual machine and set it up as my development environment. Apparently not to be. It installs and runs just fine, but it runs like a dog, just like Windows. Huge screen-tears on page redraws, etc. and simple programs like web browsers take 30sec+ just to load up. Heaven forbid I try and load two programs at once ... like Firefox and Thunderbird. I'm tapping my fingers for minutes.

Anyway, I also installed Windows 7 in the VirtualBox and was quite surprised to see it ran much more nicely than both my native XP version and also much better than Ubuntu.

Is Windows 7 more lightweight, fast and efficient than Ubuntu? I wouldn't have guessed so, but it looks like it.

What is the lightest and fastest version of Linux that can still be used for development purposes? (I'd want to install Netbeans, etc.)

For masochists, there is Linux from Scratch:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

For everyone else, there is Gentoo Linux:

[http://www.gentoo.org/](http://www.gentoo.org/)

---

