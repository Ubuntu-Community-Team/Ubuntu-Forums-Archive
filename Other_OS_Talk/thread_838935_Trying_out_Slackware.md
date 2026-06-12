---
title: "Trying out Slackware"
date: 2008-06-24
forum: Other OS Talk
---

### Post by kk0sse54 on 2008-06-24
Now that summer has rolled around and I got a lot more time I have been thinking about trying out Slackware just to learn about linux a bit more. My main desktop has Hardy, Debian, and XP already installed on it so I was thinking about using an older computer. What I was wondering was does Slackware run well on 256 MB RAM? Or is it not worth it and I might as well install it on my primary desktop with 1 GB RAM  in maybe say Virtualbox?

---

### Post by danielph on 2008-06-24
It should run on this box but you will be limited to what you put on it. Maybe you should think about installing Slackware without installing KDE or Gnome and go for a lighter window manager perhaps such as fluxbox, openbox or icewm for example and investigate some light alternate applications to install. You will also get some good advice at linuxquestions.org as Slackers tend to hang out there.

---

### Post by kk0sse54 on 2008-06-24
It definitely will be a lighter WM as I'm  using openbox in Debian right now and I'm loving it. Thanks for the link I'll check it out.

---

### Post by mikjp on 2008-06-25
Don't forget to read the Slackbook, [http://www.slackbook.org/](http://www.slackbook.org/). It is a great source of information, just like [http://slackwiki.org/Main_Page](http://slackwiki.org/Main_Page). LinuxPackages is a great source for more packages etc, just see [http://linuxpackages.net/](http://linuxpackages.net/) 


My P100 with 40MB has Slackware 11.0 installed on it. At the moment no X, but I have used the same hardware with Blackbox and IceWM. Works for me.

Mikko

---

### Post by Barrucadu on 2008-06-25
It will run great on that. My laptop has 256MB of RAM and I was running Gutsy with a ton of compiz effects and AWN, and various other memory-eating eyecandy on it. It still ran very fast.

---

### Post by kk0sse54 on 2008-06-25
> **Barrucadu said:**
> It will run great on that. My laptop has 256MB of RAM and I was running Gutsy with a ton of compiz effects and AWN, and various other memory-eating eyecandy on it. It still ran very fast.
Did you go with the minimal installation because I have tried Xubuntu 8.04 on my computer and it was still kinda sluggish although once I got rid of compiz it became faster.

---

### Post by cardinals_fan on 2008-06-25
Slack is fast and clean.  Enjoy!

---

### Post by kk0sse54 on 2008-06-25
I'm setting up the computer to dual boot Slackware and FreeBSD.I finished installing FreeBSD and I have to say I am really liking it so far. Few question about Slack though is it hard to install different desktop environments like xfce and openbox because I know that there really isn't much of a package manager. I also heard that it can be rock hard stable if set up correctly and that most of the configuration is through editing config files but does it require high maintenance and frequent editing of config files or is it more like once you get it up you're good to go? Last one another beginner question because i have never done this before, but I saw that they use an older Kernel in the name of stability but can I compile my own newer Kernel?

---

### Post by cardinals_fan on 2008-06-25
> **C!oud said:**
> I'm setting up the computer to dual boot Slackware and FreeBSD.I finished installing FreeBSD and I have to say I am really liking it so far. Few question about Slack though is it hard to install different desktop environments like xfce and openbox because I know that there really isn't much of a package manager. I also heard that it can be rock hard stable if set up correctly and that most of the configuration is through editing config files but does it require high maintenance and frequent editing of config files or is it more like once you get it up you're good to go? Last one another beginner question because i have never done this before, but I saw that they use an older Kernel in the name of stability but can I compile my own newer Kernel?
Once you set up Slack, it will only stop running if you screw it up.  Packages are only updated when you choose to update them (no automatic updates here), so it's very stable.  It's not too hard to get a GUI up and running, and you'll learn a lot from handling your own dependencies.  If you're feeling lazy, it's pretty easy to install SLAX (usually used as a live CD).  Once installed, you get a relatively pure Slack system with a minimal yet very functional KDE setup.  The most important config files are all in /etc/rc.d, where you set up the daemons that run at startup.

Slackware 12.1 has kernel version 2.6.24.5, is there any reason you'd want a newer one?

---

### Post by fibster on 2008-06-25
Slackware 12.1,

you will love it. 256 ram you can use kde with no effects just fine. although xfce would be much faster, I just prefer kde in slackware. Check out Linux Questions slackware site, that is the main forum there, massive help and good people.

---

### Post by mikjp on 2008-06-26
Oh, I forgot to mention [Absolute Linux](http://www.pcbypaul.com/absolute/). It's based on Slack 12.1.

---

### Post by kk0sse54 on 2008-06-26
> **cardinals_fan said:**
> 
Slackware 12.1 has kernel version 2.6.24.5, is there any reason you'd want a newer one?

More out of curiosity , about the SLAX and the absolute linux I already just got the regular slackware torrents downloaded so it's just a matter of burning them and starting the installation. I have tried slax before though with the LG3D desktop environment on a liveCD and I really enjoyed it. Thanks for the help everyone :)

---

### Post by Antman on 2008-06-26
> **mikjp said:**
> Oh, I forgot to mention [Absolute Linux](http://www.pcbypaul.com/absolute/). It's based on Slack 12.1.
I didn't know that Absolute is based on Slackware...:KS
I have to try this now. ;)

---

### Post by kk0sse54 on 2008-06-26
](*,) popped in the slack cd and was trying to partition my hard drive (which stupidly I had FreeBSD installed taking up the full drive) when it wouldn't let me make any partitions nor would it allow me through Gparted from other liveCDs. Quick google search revealed that you can't shrink a FreeBSD so I will have to wipe the BSD partition meaning that I'm probably going to hold off from Slackware for at least a little bit.

---

### Post by cardinals_fan on 2008-06-26
> **C!oud said:**
> ](*,) popped in the slack cd and was trying to partition my hard drive (which stupidly I had FreeBSD installed taking up the full drive) when it wouldn't let me make any partitions nor would it allow me through Gparted from other liveCDs. Quick google search revealed that you can't shrink a FreeBSD so I will have to wipe the BSD partition meaning that I'm probably going to hold off from Slackware for at least a little bit.
It depends on whether the partitioner can handle FreeBSD partitions (UFS, correct?).

---

### Post by kk0sse54 on 2008-06-26
Yes it's ufs. When I tried to partition it it couldn't. Gparted definitely doesn't recognize it said it was either an unknown file system or damaged, but from what I read it doesn't matter because a FreeBSD partition can only be enlarged not shrunken through growfs but all the webpages I visited about it were from around 2002 so maybe things have changed a little which is why I'm going to head over to some BSD forums and ask around. Hopefully  there's an answer because I really like FreeBSD and I'm too lazy to reinstall :D

---

### Post by cardinals_fan on 2008-06-26
DragonFlyBSD is a live CD (command line only, of course).  It's based off FreeBSD, so it might be able to handle the partitions.

---

### Post by zmjjmz on 2008-06-27
Can OpenBSD resize FreeBSD partitions?
Because there's a LiveCD version of OpenBSD called OliveBSD.

---

### Post by kk0sse54 on 2008-06-27
Thanks for the ideas guys but the replies I got in the FreeBSD forums said that it cannot be done so I'm just going to install Slack and then reinstall FreeBSD.

---

