---
title: "Suns Indiana team releases Open Solaris"
date: 2008-05-06
forum: Other OS Talk
---

### Post by swoll1980 on 2008-05-06
Sun (Indiana Team) releases [Open Solaris]("http://www.opensolaris.org/"). I don't know about you, but I have to try it. Your thoughts?

---

### Post by Ozor Mox on 2008-05-06
Nice. Downloading now to try in a VM. I'll get back to you.

---

### Post by lswest on 2008-05-06
haha i have a copy of Solaris 10 somewhere on a DVD when they were offering free DVD shipping, but i wasn't very impressed by it.  Might try 2008 sometime.  Looks like it has improved.

---

### Post by swoll1980 on 2008-05-06
> **lswest said:**
> haha i have a copy of Solaris 10 somewhere on a DVD when they were offering free DVD shipping, but i wasn't very impressed by it.  Might try 2008 sometime.  Looks like it has improved.

I never tried it before because of the hoops you had to jump through. Now they have it on a live cd and have added a bunch of easy to use installers, and such to make easier to try

---

### Post by Ozor Mox on 2008-05-06
Result:

Live CD boot menu appears. I select OpenSolaris 2008.05.

A nice blue background with OpenSolaris and the logo on it shows, and a string of full stops are printed for a few seconds. Then they stop.

Not the best experience with an OS I've ever had ;)

---

### Post by aamukahvi on 2008-05-06
Installing as I type on a VirtualBox system w/ 3 HDDs. Need to try what ZFS is all about ;)

---

### Post by swoll1980 on 2008-05-06
> **Ozor Mox said:**
> Result:

Live CD boot menu appears. I select OpenSolaris 2008.05.

A nice blue background with OpenSolaris and the logo on it shows, and a string of full stops are printed for a few seconds. Then they stop.

Not the best experience with an OS I've ever had ;)

If your using VBox you shouldn't have any problems. Did you give the vm enough ram it needs 512mb mine is installing right now. It's got a nice default theme, the installer was nice to

---

### Post by Cifra on 2008-05-06
I have a question -  I think it's been talked about in some podcasts too;

What would be the reason for someone to switch over from a desktop BSD or Linux system to Opensolaris?

---

### Post by Ozor Mox on 2008-05-06
> **swoll1980 said:**
> If your using VBox you shouldn't have any problems. Did you give the vm enough ram it needs 512mb mine is installing right now. It's got a nice default theme, the installer was nice to

I tried upping its RAM. It's on 512 MB now, and it does the full stop bit, then it just says this and does nothing else.

> SunOS Release 5.11 Version snv_86 32-bit
Copyright 1983-2008 Sun Microsystems, Inc. All rights reserved.
Use is subject to license terms.

Oh well, worth a try.

---

### Post by swoll1980 on 2008-05-06
> **Cifra said:**
> I have a question -  I think it's been talked about in some podcasts too;

What would be the reason for someone to switch over from a desktop BSD or Linux system to Opensolaris?

I don't know thats what I'm going to find out though I will learn to use it in the VM then install it to hard disk and see what is better or worse about it

---

### Post by Ozor Mox on 2008-05-06
That's a pretty bad typo right there.

---

### Post by swoll1980 on 2008-05-06
> **Ozor Mox said:**
> That's a pretty bad typo right there.

oops I fixed it. :oops: It's amazing how much damage one letter can do to an entire post.

---

### Post by Ioky on 2008-05-07
I don't know, but I have Solaris instill in my VMware, and I actually have a full copy of lastest Solaris 10. The hardware doesn't really get supported, and too much problems you need to confg or fix before you can actually use it. So I just give up, But I read some information about it, and it seem really cool, but only when you make the system work with your Hardware.

---

### Post by swoll1980 on 2008-05-07
I went balls to the walls and installed it on my laptop. Had to compile Broadcom driver other than that it detected all hardware and is running smoothly. Now I have to figure out how to get used to the fact that it is not Linux I find my self trying to do Linux type things forgetting that it is for the most part completely different. It's like starting from square one. This will allow me to make some comparisons between the two though. I made a promise to my self I would put the same effort into it that I did to learn the Linux way of doing things. I have to admit the I was quick to want to throw the towel in when the nic wouldn't work, but then remembered all the crap I went through with Linux when I first started. It was totally worth it in the end, and hopefully this will be to.

---

### Post by swoll1980 on 2008-05-07
> **Ioky said:**
> I don't know, but I have Solaris instill in my VMware, and I actually have a full copy of lastest Solaris 10. The hardware doesn't really get supported, and too much problems you need to confg or fix before you can actually use it. So I just give up, But I read some information about it, and it seem really cool, but only when you make the system work with your Hardware.

I was told the same thing about Linux when I started using it. I'm glad I am stubborn and don't pay attention to stuff like that.

---

### Post by Cifra on 2008-05-07
What about overall stability?

---

### Post by graabein on 2008-05-07
There's times like these I wish I had another computer with space to waste or just for a sandbox. From what I've seen and read I think OpenSolaris could be really good.

---

### Post by SirThom on 2008-05-07
I always thought of Sun stations as being true workhorses, pretty much ideal computers.
That might just be the marketing, though.  I don't know how they stand up.

---

### Post by Sporkman on 2008-05-07
> **SirThom said:**
> I always thought of Sun stations as being true workhorses, pretty much ideal computers.
That might just be the marketing, though.  I don't know how they stand up.

They've always seemed slow to me compared to linux boxes...

---

### Post by SirThom on 2008-05-07
> **Sporkman said:**
> They've always seemed slow to me compared to linux boxes...

I've never had the opportunity to actually use one to any extent.

I think of them mainly as tools for mathematicians and engineers.  I'm thinking of the older ones that I am familiar with with the monitone (amber?) CRTs.  How did you use yours?

---

### Post by Sporkman on 2008-05-07
> **SirThom said:**
> I've never had the opportunity to actually use one to any extent.

I think of them mainly as tools for mathematicians and engineers.  I'm thinking of the older ones that I am familiar with with the monitone (amber?) CRTs.  How did you use yours?

We have NT, Linux, and Solaris machines all networked together where I work (I work in the semiconductor industry, so there's alot of engineering activity). I used to have a Sun machine as my workstation as well, but now I have a Red Hat linux machine.

Basically, when I run a big job on a Sun machine (such as a large code compile, or a big EDA spin, etc), it tends to run 2-3x slower than linux. Now granted, maybe the Sun boxes are older & slower, who knows, but basically for any serious computing here, we use linux or Windows. In fact, I think I heard that they're phasing out the Sun workstations, as the performance vs. cost ratio doesn't measure up to the cheap & fast linux machines.

---

### Post by swoll1980 on 2008-05-07
> **Cifra said:**
> What about overall stability?
It's stable everything has gone smooth so far

> **Sporkman said:**
> They've always seemed slow to me compared to linux boxes...

It's not slow it's at least as fast as Ubuntu was on the same rig

The problem I'm having is my laptop is not really good for anything other than internet and multimedia it doesn't have enough resources to run virtual machines or anything interesting like that. In the multimedia aspect the opensolaris is at a disadvantage as I have yet to find a way to install the necessary codecs to listen to music or watch video whether it be a dvd, avi, or wmp. The package manager is still in development and is painfully slow at this time. I'm going to through it on my desktop so I can get a more accurate assessment of it's pros/cons

---

### Post by regomodo on 2008-05-07
no wonder why i thought indiana reminds me of Debian. Just found out Ian Murdock was the head of the project.

---

### Post by swoll1980 on 2008-05-09
Well I give up I just can't get it to work, and the amount of resources to study are extremely limited. I'm not saying it's not usable, it's just not usable for me right now. maybe if I went to school for a couple years I would be able to figure it out, but I'm hopelessly lost, am throwing in the towel.

---

### Post by DreamcastJack on 2008-05-09
I ran the LiveCD and everything was detected w/out any problems.  but I just dont have the time or an extra PC to learn the basis of Solaris.  I'll log it into my "to learn later files"

---

### Post by GerryB on 2008-05-10
Tried the Solaris Live CD yesterday. Works like a charm. Detected the Nividia card...video, sound, everything works. Even compiz fusion once activated works well ...rotating cube, etc...I think you would have to buy their office suite though. No OpenOffice offered and I don't know if it would even be installable on this system.... I'm posting from a MaryanLinux live CD and I can't find the proper keys for hyphens and brackets. Other than that though, E17 works well on this, much better than OpenGeu..

---

### Post by aamukahvi on 2008-05-10
> **GerryB said:**
> Tried the Solaris Live CD yesterday. Works like a charm. Detected the Nividia card...video, sound, everything works. Even compiz fusion once activated works well ...rotating cube, etc...I think you would have to buy their office suite though. No OpenOffice offered and I don't know if it would even be installable on this system.... I'm posting from a MaryanLinux live CD and I can't find the proper keys for hyphens and brackets. Other than that though, E17 works well on this, much better than OpenGeu..
I will suppose that you mean Open Solaris since that's what this thread is about. You can install OpenOffice from the repos. Package name is "openoffice".

P.s. I think OpenSolaris deserves its own subsection on this forum. There are already many for individual linux distros...

---

### Post by exploder on 2008-05-10
I tried the OpenSolaris Live CD on two machines. I could not get networking going on either machine... I liked what I saw and it could become very good with better hardware support. 

I thought the speed of the OS was decent and the default applications were alright. The artwork used was very nice, wallpaper, icons, gnome-splash, etc.

I will be keeping an eye on OpenSolaris's development.It's a good start!

---

### Post by GerryB on 2008-05-11
> **aamukahvi said:**
> I will suppose that you mean Open Solaris since that's what this thread is about. You can install OpenOffice from the repos. Package name is "openoffice".

P.s. I think OpenSolaris deserves its own subsection on this forum. There are already many for individual linux distros...

Yes, OpenSolaris - there is no other live CD. OpenOffice is in the repos as a teaser. No information is available on it and if you try to install it you'll wait forever for the system to evaluate the package. To be fair, since it's there in name, maybe it isn't ready yet. Yes, I agree, OpenSolaris should have its own subsection.

---

### Post by mybunche on 2008-05-11
I have tried the liveCD and everything worked fine except my wifi, it didn't detect my wireless USB dongle so I couldn't get online. Apart from that, the artwork was good and behaved like any other live CD. With good hardware detection and if there is a much improved package installer it will give Linux and BSD a good run. Technically it will be a good OS in the future. It is for reasons other than the technical that I support Ubuntu. 

Have  a question though:
Is the kernal in opensolaris the same as the kernal in solaris proper?

---

