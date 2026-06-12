---
title: "Looking for a less buggy version/distro than 8.04"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by nandor73 on 2008-05-30
Hello Ubuntu community,
 
I started using Ubuntu (8.04) a week ago, and I've been beleaguered with bugs such as [Nautilus not preserving timestamps]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499"), [PDF readers printing]("https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/148334") [the boxes around links]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/156643"), [Rhythmbox not able]("http://ubuntuforums.org/showthread.php?t=734093") [to save tag edits]("https://bugs.launchpad.net/rhythmbox/+bug/127510"), and now I'm finding some issues with PCMan (which I installed to avoid the Nautilus issue) and with the logout screen.

These bugs are killing me!  I know there are workarounds for some of these, but more and more, I desperately want something that just works.  A big part of me strongly identifies with the feelings of [this recent post]("http://ubuntuforums.org/showthread.php?t=812469").  However, for me, staying with Windows is an absolute last resort, as Microsoft clearly seems more interested in introducing tons of new buggy features (in Vista) rather than just making a reliable product (XP) better.  I'm not much of a hardcore computer guy - XP works pretty well for me, and if I could use it forever, I would.  If Vista were a BETTER version of XP, I'd sign right on!  But Vista appears to be clearly worse than XP, and it looks like every few years or so, Microsoft is going to be pushing an OS that screws everything up.  I do NOT look forward to every few years changing to something that completely changes the design and is incompatible with some of my applications.  Since I'm going to have to do that anyway, I may as well just switch to Linux and go through this awful process JUST ONCE.

My questions for you, dear reader:


(1)  Am I assuming correctly that the overall design of the Ubuntu desktop doesn't change much from version to version (e.g., so I don't have to hunt around for things with every new version)?

(2)  Am I assuming correctly that many of the bugs in 8.04 are due to the fact that it was just released last month, and that some/most of these bugs will go away after the next couple of point releases?

(3)  If (2) is true, I would prefer to use an older version of Ubuntu that is less buggy, and then to upgrade to 8.04 later on, after these bugs have been ironed out.  Would you have a suggestion?  I was thinking of 6.06, since that was the last LTR.  However, is that *too* old?  The two most important considerations for me are that (a) I really, really want to have an older version of Nautilus that doesn't have [that awful timestamp problem]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499") (which seems to [not be a problem with 7.10]("http://adventuresinswitching.blogspot.com/2008/05/file-modification-dates-changed-in.html"), or presumeably earlier), and (b) I absolutely need VirtualBox OSE, which is my lifeline to XP (which I doubt I'll be able to completely leave).

(4)  Generally, is Ubuntu more buggy than other distros like Debian or OpenSuSE?  I know that every distro has to strike a balance between being current/having new features and being stable/fixing bugs.  I've read that Ubuntu is a little more on the adventurous side (current/features) than some of the others.  What do you think?


Overall, my preference is for a distro that is stable and has the bugs mostly fixed (as opposed to having all those new, sexy features).  Is it enough to always use a slightly older version of Ubuntu, or should I go for a more conservative distro like Debian?


Thanks for putting up with my long post,

Nate

---

### Post by Kobalt on 2008-05-30
If you feel unsatisifed by the LTS releases of Ubuntu, you should go towards Debian Stable. IMHO, it's a step further into system stability priority.

---

### Post by ugm6hr on 2008-05-30
I'm no expert, since I've only played with 4 distros for more than an hour, but here's my view...

> Overall, my preference is for a distro that is stable and has the bugs mostly fixed (as opposed to having all those new, sexy features). Is it enough to always use a slightly older version of Ubuntu, or should I go for a more conservative distro like Debian?

Sounds like Debian (stable) is more your cup of tea.  As you say - a choice of where in the continuum of stability vs innovation is the key.

> Generally, is Ubuntu more buggy than other distros like Debian or OpenSuSE? I know that every distro has to strike a balance between being current/having new features and being stable/fixing bugs. I've read that Ubuntu is a little more on the adventurous side (current/features) than some of the others. What do you think?

The other commercially-backed "open" distros (i.e. Fedora / openSUSE) are equally buggy, since they are testing grounds for enterprise editions.  Debian does not fall into this category.  CentOS is the "free" community version of RedHat Enterprise, but is primarily aimed at servers (like RH).

Non-commercial distros also vary in their emphasis on stability.  I believe one of the most stable (apart from Debian) is slackware.

---

### Post by sdennie on 2008-05-30
1) That's a fairly safe assumption.  Things change in minor ways, new features are added, etc.  After years of Ubuntu usage, the only drastic change I've seen is having compiz on by default on supported hardware.  Even that is generally considered an added featured.  Overall, if you are using gnome, things change but, the rarely change in radical ways between releases.

2) That's probably also true.  As 8.04 will be supported for quite some time, some decisions were made to include software that wasn't 100% completely ready to be released (FireFox 3 being the most noteworthy example).  Though, after a month, most of those problems seem to be resolving themselves (FF3 RC1 is in the proposed repo for example).  Ubuntu isn't quite like Windows in that you are best waiting for the first Service Pack to actually install (so, a year) but, there will be bugs at release time and, unless you are immediate and dire need to upgrade to the newest version, it's perfectly reasonable to wait a month or two for things to stabilize a bit before upgrading.

3) Maybe.  If your problems are known in 8.04 and don't exist in 7.10 then, sure, install 7.10, watch the bug reports for 8.04 and when they are resolved, upgrade.  7.10 is still supported for long time and works great so, there is no harm in doing this.

4) Some Ubuntu releases seem very conservative and others seem slightly less conservative.  You have to realize that the vast majority of the software in distros come from the same non-inhouse sources (so, stuff they are not directly involved in developing).  Hardy looked at the state of the software they wanted to include, decided on risk/reward within the perspective of something that's going to be supported for several years and went with it.  It's a never ending tradeoff.  It would be hard to claim one vendor is more stable than another.

---

### Post by SlappyPappy on 2008-05-30
I would try running 8.04 and 7.10 side by side if possible. I'm currently using 7.10 and it's super stable for me and I'm really happy where I'm at with Linux. I don't know if 7.10 will address all your issues but that's why it might be nice to use both for a bit. 

That's what I'll be doing when I move up to 8.04, testing it out to be sure it's what I want.

A word of warning about Debian, it's nice and all but a beat bleak and boring. I used it and then I started to add some things to warm it up a bit. The next thing you know, I made it totally unusable. That's why I think Ubuntu is so nice. It's a bit more current and lively to use compared to something that is rock solid like Debian. But hey, if that's what you want, by all means, go for it!

Good luck friend!

---

### Post by nandor73 on 2008-05-30
Thanks so much for your opinions.  Vor (#4), you brought up a point I never thought about before - since LTR releases are intended to stick around for a while, some of their software may be beta versions (e.g., Firefox), and thus initially be *less* stable than usual for a new release.

At this point, I'm considering first trying out 7.10, and then if that is still too buggy for my taste, going for Debian.  And I don't care if Debian is boring ... although, knowing me, I am a little in danger of tinkering with it enough to mess it up, like SlappyPappy (#5).

Any other opinions out there?  Is OpenSuSE really as buggy as Ubuntu, as ugm6hr (#3) has said?  I'll be checking this post off and on over the next few days - your comments are appreciated!

---

### Post by ukripper on 2008-05-30
i would agree with others. Try 7.10 until your Hardy bugs are fixed and then upgrade when you are ready as 7.10 support is till April 2009, you have plenty of time till then to make decison!

---

### Post by ajgreeny on 2008-06-01
For the timestamp problem in nautilus, try either gnome-commander or perhaps thunar (the xfce file manager) instead, neither of which have the problem with timestamp changing.  I agree that was a potential killer of a bug, and it was only luck that I could re-restore my /home files with the correct dates after my 8.04 install, as I noticed in time and hadn't backed up again after the first time I used 8.04, thus overwriting the dates of everything on the backup.

---

