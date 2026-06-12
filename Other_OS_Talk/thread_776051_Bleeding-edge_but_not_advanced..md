---
title: "Bleeding-edge but not advanced."
date: 2008-04-30
forum: Other OS Talk
---

### Post by SomeGuyDude on 2008-04-30
That's what I'm looking for.

I love my Compiz, I don't care what DE out of KDE/GNOME/XFCE (no -boxes), I don't want to spend two hours setting it up in text commands, and I want the software on the cutting edge of brand new even if it's not all perfect.

What would you suggest? If you say Hardy with all updates and repositories enabled, then that means I'm good, but what else is out there?

---

### Post by ibutho on 2008-04-30
Fedora and Mandriva ship with compiz. They even have nifty GUI tools to enable/disable the 3D effects. In the case of Mandriva, you can enable/disable 3D effects from the login manager, which is good if things don't work as they should.

---

### Post by SomeGuyDude on 2008-04-30
And their packages tend to be on the edge? That's a big thing I'm aiming for. Fedora 9's coming out soon, I'm thinking about downloading the beta.

---

### Post by mips on 2008-04-30
Gentoo, Arch etc. Just enable the testing repos if you want really bleeding edge. Normal arch suites me fine.

---

### Post by SomeGuyDude on 2008-04-30
Arch intimidates the hell out of me. Any distro that requires a 58 page manual to get it set up counts as "advanced" to me. I'll work up to it eventually, but I ain't there yet.

---

### Post by LaRoza on 2008-04-30
> **SomeGuyDude said:**
> Arch intimidates the hell out of me. Any distro that requires a 58 page manual to get it set up counts as "advanced" to me. I'll work up to it eventually, but I ain't there yet.

It is also very easy to install if you don't have anything special to do.

---

### Post by SomeGuyDude on 2008-04-30
> **LaRoza said:**
> It is also very easy to install if you don't have anything special to do.

Hm.

Well, the semester's over and I have an external HD to back up all my crap. It's not like nuking my drive would really mess anything up for me. I might want to read the guide again.

What worries me though, is it looks like setting up my wireless, my display, and all of that takes a hell of a lot more work than anything I've ever run into before.

---

### Post by mips on 2008-04-30
> **SomeGuyDude said:**
> Arch intimidates the hell out of me. Any distro that requires a 58 page manual to get it set up counts as "advanced" to me. I'll work up to it eventually, but I ain't there yet.

You are exaggerating a bit there i think.

Arch really is not that hard to install. If you can read and follow the wiki you will be fine. Arch is easier than Gentoo from persoanl experience.

See [http://ubuntuforums.org/showthread.php?t=767749](http://ubuntuforums.org/showthread.php?t=767749) for another users experience.

Everybody goes, "Oh no, Arch is way to hard". Once they try it though they change their tune.

I challenge you to try Arch, you will actually be suprised how easy it is. All you have to do is follow the Beginners & Official install wiki.

Edit:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by SomeGuyDude on 2008-04-30
Well that's what I'm getting at. Look at the size of those two pages. I didn't pull the 58 page out of my butt either, it's in the beginner guide: "You may wish to print out this guide as a 58 page book which will serve as a useful Arch Linux user reference."

There comes a line that makes me wonder just how much "work" I'm willing to put into an OS, and I'm concerned that Arch is on the wrong side of it. The Beginner's Guide is 54 pages in OpenOffice copied and pasted, the Install Guide is 34. You have to admit, that's intimidating.

But, again, I got time. I'll do it as soon as the ISO finishes downloading. You're ON! :lolflag:

EDIT: Installing now. Using another laptop in the house for guide-reading and such. Wish me luck!

---

### Post by mips on 2008-04-30
How much of those '58' pages are commands you simply copy and paste and how much is just text explaining what is going on? The commands are not that many to be honest. I just went through the beginners guide again and it really is not that long command wise with stuff to do.

Either way, the choice is yours at the end of the day.

---

### Post by mips on 2008-04-30
> **SomeGuyDude said:**
> I'll do it as soon as the ISO finishes downloading. You're ON! :lolflag:

EDIT: Installing now. Using another laptop in the house for guide-reading and such. Wish me luck!

Which ISO did you use?

Good luck!

---

### Post by SomeGuyDude on 2008-04-30
No I agree there, 100%. My point was just that the sheer amount of text is intimidating for someone who isn't used to an OS that needs more than "hit okay five or six times and you're set".

EDIT: the i686 one for the new RC1. I figure if I'm going Arch, I might as well get the latest version!

---

### Post by mips on 2008-04-30
> **SomeGuyDude said:**
> 
EDIT: the i686 one for the new RC1. I figure if I'm going Arch, I might as well get the latest version!

Cool, thats what i just did on my desktop. 64bit FTP install for me. The Core iso will work fine, you might just find that there are updated packages available once you have installed. Dunno which one you are using.

---

### Post by ibutho on 2008-04-30
> **SomeGuyDude said:**
> And their packages tend to be on the edge? That's a big thing I'm aiming for. Fedora 9's coming out soon, I'm thinking about downloading the beta.
Fedora is bleeding edge. Mandriva is conservative, but you can install new packages from backports.

---

### Post by SomeGuyDude on 2008-04-30
Well this already sucks. I apparently did something wrong in my network settings so trying the "ping -c 3 www.google.com" got me "network is unreachable" and I don't have a bally clue what to do next.

EDIT: I get a "destination host unreachable" now. Wow. I would shoot myself if I didn't have a second machine to look **** up with.

---

### Post by SomeGuyDude on 2008-04-30
I'm running, however I've got the following problems:

1) GIANT FONTS ON MY LOGIN WINDOW. No idea how to fix them.

2) Sudo doesn't seem to let me do anything. I get this:

```
[crew@home ~]$ sudo pacman -S firefox

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

Password: 
[crew@home ~]$ 
```

3) Where is a GUI for installing anything? Is there a synaptic equivalent for Arch?

I'm going to give it a day or so, but I have to admit I'm finding it terribly uninviting.

---

### Post by Barrucadu on 2008-04-30
1) Tried changing the GDM theme?
2) Did you enter your password, or cancel? That message indicates it is working - it shows up the first time.
3) There are a few GUI front-ends for pacman, but I can't think of any off the top of my head.

---

### Post by Exershio on 2008-04-30
> **SomeGuyDude said:**
> 2) Sudo doesn't seem to let me do anything.

You need to add yourself to the sudo permissions file.

Type **visudo** while logged on as root. Add the following:
**YOUR_NAME   ALL=(ALL) ALL**
of course, replacing YOUR_NAME with your user name.

More information here:
[http://wiki.archlinux.org/index.php/Sudo](http://wiki.archlinux.org/index.php/Sudo)

---

### Post by Antman on 2008-04-30
> **SomeGuyDude said:**
> That's what I'm looking for.

I love my Compiz, I don't care what DE out of KDE/GNOME/XFCE (no -boxes), I don't want to spend two hours setting it up in text commands, and I want the software on the cutting edge of brand new even if it's not all perfect.

What would you suggest? If you say Hardy with all updates and repositories enabled, then that means I'm good, but what else is out there?

Fedora and Sidux would give you "Bleeding Edge."

---

### Post by cardinals_fan on 2008-04-30
DesktopBSD.  Enough said.

---

### Post by SomeGuyDude on 2008-05-01
> **Antman said:**
> Fedora and Sidux would give you "Bleeding Edge."

Fedora seems my bet now. I'm getting the GNOME version of the Fedora 9 preview as we speak.

I want to thank all you Arch guys. Arch is, no joke, an AWESOME OS... for some. I found the amount of configuration necessary a little too daunting. If I had someone to almost literally hold my hand through it, I'd spend a few days making it work. But at this stage, it's more work than I want to put into an OS.

---

### Post by yssida on 2008-05-01
Try Debian Sid. Be prepared for things breaking every few weeks or so.

---

### Post by SomeGuyDude on 2008-05-01
Well it took a whopping 10 minutes to install Fedora and while I'm not sure what it'll do with my resources (GNOME is GNOME, I assume?), I admit it's nice. However, I'm in that place I was when I got rid of Windows: I feel a little "bare" since I'm no longer in an OS I felt like I knew intimately.

---

### Post by mips on 2008-05-01
> **SomeGuyDude said:**
> 
3) Where is a GUI for installing anything? Is there a synaptic equivalent for Arch?


Shaman

You don't seem to have a lot of patience, spent less than 3hours before you just gave up.
Don't try Gentoo and possibly stay away from Sidux as well as they are going to require a bit of time.

At the end of the day use what you feel comfortable with, enjoy :)

---

### Post by miggols99 on 2008-05-01
You probably won't be able to use this now, but in a few months (or maybe a month if you're adventurous) time you may want to try KDEmod's distro which includes everything to make installing/configuring it a little bit easier. This means a Pacman frontend (Shaman), a system configuration panel (Arxin) and an installer (Tribe). drf and boom1992 have been doing a great job with them :)

[http://kdemod.ath.cx/wiki](http://kdemod.ath.cx/wiki)

A working installer and ISO will be available around the end of this month (Alpha 1).

And yes I hope you'll like my great artwork ;)

Personally I don't like Fedora...it was horrible on my laptop...

---

### Post by LeoSolaris on 2008-05-01
I'm going to be starting on Arch next week, right after my finals are over. I'm dedicating May and some of June to getting it set up and tweaked. If it's easier to do than I think it will be, I may start on Linux from Scratch early. I'm not really planning on starting that till summer break next year.

Leo

---

### Post by Playa1313 on 2008-05-01
I'm kind of in the same position as SomeGuyDude.

Hardy x64 and compiz does not mix well with my graphics card, so I have been searching around for a x64 distro that is not too much different from Ubuntu that I'd have to learn everything all over again.

I have heard Arch is a VERY good OS, but I am kind of intimidated by things I've heard about it, along with that documentation page.

Any suggestions?

Thanks.

---

### Post by cardinals_fan on 2008-05-01
I thought that Arch was very good, but not worth the effort when I could install DragonFlyBSD in less time ;)

---

### Post by Antman on 2008-05-04
> **cardinals_fan said:**
> I thought that Arch was very good, but not worth the effort when I could install DragonFlyBSD in less time ;)
I wonder how DragonFlyBSD behaves with laptops and wifi?!?

---

