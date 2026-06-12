---
title: "For old computers, should I use an old linux distro?"
date: 2008-04-27
forum: Other OS Talk
---

### Post by Redsandro on 2008-04-27
Hi, I want a *fast Linux* OS on my old **P2 266MHz** and my **P3 1G laptop**. If I succeed, I might even get my **486** out of the dust as a radio. I tried **Xubuntu** and **Fluxbuntu**, but they are both beat by **WinXP SP2** in speed [SIZE="1"](yes, even on the P2)[/SIZE].

Don't get me wrong, I love **Ubuntu** and I use 8.04 on my P4 and my Core Duo. But when I'm being honest, it pisses me off on any of my slower machines.

There are many 'slim' distro's out there, but as I hear noise about Debian based distro's are fat and slow for old machines, I decided to try **Zenwalk** or **Vectorlinux**.

Now for my question; on my older computers, I better use an older version of Windows. How is this with Linux distro's? Should I download an older image for the P2 and a newer for the P3?

---

### Post by scragar on 2008-04-27
look into both DSL( [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) ) and puppy ( [http://puppylinux.com/](http://puppylinux.com/) ), both are made esspecialy for old computers with limited power and RAm/HD space.

---

### Post by SunnyRabbiera on 2008-04-27
certain distros are more fine tuned for newer computers, and ubuntu is one of them.
But you really dont need an old distro for a old computer, DSL, puppy and even debian might be able to help you out here.

---

### Post by beartard on 2008-04-27
...and even within varying distros  there are more window managers to choose from than the big three environments  (GNOME, KDE, and XFCE).

I remember running fvwm on old computers back in the day.  Windowmaker worked as well.  The key is learning which discrete utilities you'd need to install to get similar functionality as the desktop environments.   Do you need panels?  Which file manager shoul d you choose?  Etc.

I would definitely NOT go with an older distro, as the improvements in the kernel over time help older computers, too.  Plus, you'd be hard-pressed to find support for an older distro nowadays.  Go with a scaled-down distro that gives you absolute choice over what gets installed and run at startup.  Englightenment was seen as a resource hog years ago.  It's considered "light" by today's standards.  It might be worth looking at.

---

### Post by tommcd on 2008-04-27
Zenwalk should run just fine on the P3. It might even do ok on the P2. There is also Deli Linux:
[http://delili.lens.hl-users.com/](http://delili.lens.hl-users.com/)

---

### Post by cardinals_fan on 2008-04-27
Use Zenwalk and a *box WM.

---

### Post by wolfen69 on 2008-04-28
i think the best thing to do is just roll up your sleeves and get busy downloading a few distros. that's how you learn what it good for what. take the advice of what people recommend and burn 6 or 7 cd's. it doesnt have to be a one shot deal. if something doesnt work, just pop in the next cd. it's a good learning experience. and fun. :guitar:

you could also try doing a minimal install. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) that's what i did with the old laptop in my sig.

---

### Post by dptxp on 2008-04-28
Try AntiX , the lighter MEPIS. A typical Linux Desktop OS today shall need more resources than XP, XP came quite a few years back. I had a P100 with 32 MB RAM (finally perished 2 days back). Could run no linux on it. But W-98 was OK.
You can also try Kanotix on the 1G Machine if you have >= 256MB RAM.
DELI is another light-weight Linux, no live CD, Text mode install.

---

### Post by anaconda on 2008-04-28
I would install DSL to one ~100MB partition for speed.

And I would install a very light version of debian stable to the rest of the hd. with fluxbox, or icewm

---

### Post by darrelljon on 2008-04-28
Is it worth considering Debian 2 for old machines? Are the repos still available? Is it worth running a KDE older than 3. Some modern window managers are quite fast like FVWM (which will run on most distros fine). I suppose it depends if by "modern" you mean updated in the last 12 months or simply software that still works with new distros.

---

### Post by cb951303 on 2008-04-28
you might also wanna try arch or slackware ;)

---

### Post by Redsandro on 2008-04-28
Wow, thanks for the many response!

> **scragar said:**
> look into both DSL and puppy, both are made esspecialy for old computers with limited power and RAm/HD space.> **SunnyRabbiera said:**
> (..) DSL, puppy and even debian might be able to help you out here.

After **Xubuntu**, **Fluxbuntu** and internet rumours about other Debian based distro's, I decided to count them out (including **Puppy**). **DSL** is based on **Knoppix**, which I dislike. I might still want to try them on the **P2** though, if I find the courage.

I also tried **Gentoo** on the **P3** yesterday, and it's really too much for me. The *"compile everything"* idea sounded like a *fastest-linux-possible* idea, but it's too time consuming to get stuff working and I had a bunch of errors on basic tasks. Clearly for the pro's, although in my honesty I must laugh at the installer, which looks like it was made by a kid.

> **beartard said:**
> ...and even within varying distros  there are more window managers to choose from than the big three environments  (GNOME, KDE, and XFCE).> **cardinals_fan said:**
> Use Zenwalk and a *box WM.
I prefer **Gnome** above **KDE**, but that's not an option for the older computers. Xfce seems nice and light [SIZE="1"](~60MB lighter than Gnome)[/SIZE]. Even lighter, towards *box (I tried **Fluxbox**), and I'm getting annoyed by the way it works. This is where the I-am-spoiled factor comes into play, but WinXP is my 'possible speed indicator', so I know I don't have to resort to Fluxbox, Blackbox, etc. to get a descent GUI OS.

> **tommcd said:**
> Zenwalk should run just fine on the P3. It might even do ok on the P2. There is also Deli Linux:
[http://delili.lens.hl-users.com/](http://delili.lens.hl-users.com/)
I don't know Deli Linux.. and I don't know IceWM (default). Looks very light. I might want to try that on the P2. Today I installed **Zenwalk** on the P3. Everything goes nice and smooth! The major drawback I experienced in this short experience with Zenwalk is that swapping to Opera makes the window redraw, which takes literally one second. in XP and Ubuntu, this was [SIZE="1"](more or less)[/SIZE] in an instant.

> **wolfen69 said:**
> i think the best thing to do is just roll up your sleeves and get busy downloading a few distros.
I've got Ubuntu(64), Xubuntu, Fluxbuntu, Gentoo, Featherlinux, Knoppix, Fedora, XP(64), OSX, Zenwalk, and to be honest I don't like this game anymore. ;)



[SIZE="1"]PS The info I didn't quote is also well received and taken into concideration. [/SIZE]:)

I keep wondering about new vs old distro's. No support is a big problem unless there's a very complete image out there. But newer versions tend to ask more of your computer. That's a natural proces of a developper wanting to go foreward and include features of their newer equipment in their own OS.

The coming time I will keep Zenwalk on my laptop, though I keep doubting if I should swap for VectorLinux because the package manager makes me feel like there is only 1 person fostering the distro. If I cannot fix the graphic issues I will try something else. I will wait for another weekend with enough spare time before I go and install linux on the P2 (which now still runs Xubuntu and XP in dual boot - the latter being faster and therefore the preferred OS for burning a quick CD).

---

### Post by DJiNN on 2008-04-28
+1 for [antiX]("http://antix.mepis.org/"), runs really well on older machines. If you want a modern(ish) DE, install LXDE, tweak and see what it's like. Or give Arch a try, it's nowhere near as painful as Gentoo. :)

Also, TinyMe is well worth a look. It's based around PCLOS, has a great set of apps, uses Openbox as the WM and has a really great (Complete) iconic desktop. Great little distro, and incredibly light on resources. It's comparable to antiX, but antiX is Debian and TinyMe is RPM.

---

### Post by MONODA on 2008-04-29
arch linux would work best but only if you are willing to learn.

---

### Post by cardinals_fan on 2008-04-29
> **Redsandro said:**
> 
I also tried **Gentoo** on the **P3** yesterday, and it's really too much for me. The *"compile everything"* idea sounded like a *fastest-linux-possible* idea, but it's too time consuming to get stuff working and I had a bunch of errors on basic tasks. Clearly for the pro's, although in my honesty I must laugh at the installer, which looks like it was made by a kid.


I prefer **Gnome** above **KDE**, but that's not an option for the older computers. Xfce seems nice and light [SIZE="1"](~60MB lighter than Gnome)[/SIZE]. Even lighter, towards *box (I tried **Fluxbox**), and I'm getting annoyed by the way it works. This is where the I-am-spoiled factor comes into play, but WinXP is my 'possible speed indicator', so I know I don't have to resort to Fluxbox, Blackbox, etc. to get a descent GUI OS.

I keep wondering about new vs old distro's. No support is a big problem unless there's a very complete image out there. But newer versions tend to ask more of your computer. That's a natural proces of a developper wanting to go foreward and include features of their newer equipment in their own OS.

The coming time I will keep Zenwalk on my laptop, though I keep doubting if I should swap for VectorLinux because the package manager makes me feel like there is only 1 person fostering the distro. If I cannot fix the graphic issues I will try something else. I will wait for another weekend with enough spare time before I go and install linux on the P2 (which now still runs Xubuntu and XP in dual boot - the latter being faster and therefore the preferred OS for burning a quick CD).
1. The Gentoo GUI installer was the worst idea since Windows ME.  Who thought that adding a graphical installer to a distro that **requires** use of the command line was a good idea?  Naturally, it works terribly.

2. Xfce is good.  You can use some of Xfce's GUI config programs if you load 'xfce-mcs-manager' at the startup of any *box.  Don't be scared of the xml files!

3. Just pick a minimal distro.  Zenwalk, Vector, KateOS, AntiX, and all the others mentioned above.

4. Zenwalk's package management is its only weakness.  Netpkg is great from the command line, but the GUI is weird and disturbing.

---

### Post by DJiNN on 2008-04-29
> **cardinals_fan said:**
> 1
4. Zenwalk's package management is its only weakness.  Netpkg is great from the command line, but the GUI is weird and disturbing.

I just tried (briefly) Zenwalk v5, and i think the latest incarnation of Netpkg is probably the best yet. :)  Certainly works a lot better than it used to. What don't you like about it? (Just curious)

Also, for the OP, what about "[Sidux]("http://www.sidux.com")".... it's a modern OS, very fast, based on Debian, but very good on older machines for some reason. It takes some work but it's a very good distro.

---

### Post by LinuxGuy1234 on 2008-04-29
> **Redsandro said:**
> Hi, I want a *fast Linux* OS on my old **P2 266MHz** and my **P3 1G laptop**. If I succeed, I might even get my **486** out of the dust as a radio. I tried **Xubuntu** and **Fluxbuntu**, but they are both beat by **WinXP SP2** in speed [SIZE="1"](yes, even on the P2)[/SIZE].

Don't get me wrong, I love **Ubuntu** and I use 8.04 on my P4 and my Core Duo. But when I'm being honest, it pisses me off on any of my slower machines.

There are many 'slim' distro's out there, but as I hear noise about Debian based distro's are fat and slow for old machines, I decided to try **Zenwalk** or **Vectorlinux**.

Now for my question; on my older computers, I better use an older version of Windows. How is this with Linux distro's? Should I download an older image for the P2 and a newer for the P3?

You could try installing the A, N and AP sets from the Slackware distribution. You can download the CD ISOs of Slackware, they work on 486s and above.

---

### Post by gameryoshi600 on 2008-04-29
try out dsl. thats what i am doing but am not sure too

---

### Post by cardinals_fan on 2008-04-29
> **DJiNN said:**
> I just tried (briefly) Zenwalk v5, and i think the latest incarnation of Netpkg is probably the best yet. :)  Certainly works a lot better than it used to. What don't you like about it? (Just curious)

The search feature angers me - I want it to just search for packages, not make me fight with the installed/new/updated checkboxes.  It's hard to get detailed info on packages (though this has improved).

---

### Post by Bungo Pony on 2008-04-30
For anything less than 128M of RAM, DSL is the way to go. For anything with 128M or more RAM that will NOT run Ubuntu, TinyMe is fantastic. BTW, I was able to run Ubuntu Fiesty quite smoothly on a P3 833MHz with 1G of RAM.

For anything 486 or older (and I might get slammed for this), Windows or DOS is the way to go. Those old versions of Windows are a lot lighter than any currently supported Linux distro. Even my P133 is a bit sluggish with DSL, but ran Win95 quite nicely.

---

### Post by Redsandro on 2008-05-02
Thanks for all the suggestions!

I tried some of the mentioned distro's [SIZE="1"](only briefly because of time management issues :P)[/SIZE] on my **Pentium Mobile 1GHz/512MB** and I seem to prefer **Zenwalk**.

I ditched real ugly ones immediately because I want something descent on it (comparable to **XP**), but from the rest, **Zenwalk** seems to boot about the fastest! Ok **DSL** was faster booting, but it seems like the target audience would be my **Pentium 2** instead. Still, the boot time of all I tried pisses me off because XP [SIZE="1"](which I also installed for media center purposes because there seems to be no way in hell anything other than Ubuntu 7.10 (not even 8.04) understands my tv-out)[/SIZE] fresh installed boots literally 10 times faster. Below 10 seconds (with SP3). I am sure that will increase somewhat, but never ever by 1000%. On a *laptop* that's valuable.

For my **P2 266MHz/96MB** I will try **AntiX**, **DSL** or **Vector**. But my laptop has priority because I only use the P2 occasionally, as browser, IM, jukebox and mediaplayer when I'm visiting my parents [SIZE="1"](my old room, old music, old computer, DOSbox, nostalgia)[/SIZE].

---

### Post by greghill on 2008-05-02
I just purchased a refurbished (read "cleaned up") for my son and paid $40 total for it from a re-cycle depot. It is a 486 with 256 MB Ram and a 40 Gb HD and Windows 2000 Pro.
I split the hard drive and installed Mepis 6.0 (the newer versions of Ubuntu would not even load the live CD, I suspect not enough memory).
I have to tell you I was shocked at how fast the thing runs. Even after installing and configuring gnome on it, it's lightning fast and fully functional.You don't have to "do without".
So, no. You don't have to install an old version of Linux on old machines. Mepis 6.0 should do the trick, and you'll find there are about 230 or so updates after the install. From start to finish, the install/configuration/tweaking took about 4.5 hours.
You can get it here:
[http://ftp.uwsg.indiana.edu/linux/mepis/released/old/](http://ftp.uwsg.indiana.edu/linux/mepis/released/old/)

or you can try a little newer version here:
[http://ftp.uwsg.indiana.edu/linux/mepis/released/](http://ftp.uwsg.indiana.edu/linux/mepis/released/)

I can't vouch for the 6.5 version, as I have not tried it, but it's available as well as the new version 7.0.

---

### Post by Redsandro on 2008-05-08
Interesting!
Can I ask why you tried an older version in stead of 7?

---

### Post by greghill on 2008-05-08
Just didn't have a copy of the latest version in my case at the time. I knew that 6.0 was rock steady so I used it. No regrets.
Today I downloaded v 7.0 and installed it on my main box (dual boot with Ubuntu). So far it's right on the money, even though it did not see my wide screen monitor at 1440x900.

---

