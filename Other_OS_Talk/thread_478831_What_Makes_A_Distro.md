---
title: "What Makes A Distro?"
date: 2007-06-19
forum: Other OS Talk
---

### Post by opticyclic on 2007-06-19
After having tried out several recently I realised how similar many are.
Is a distro merely a choosing the various options available in the following categories?
[LIST]
[*]Kernel
[*]Display Manager
[*]Packaging Style (rpm/deb)
[*]Pre-installed applications
[*]Artwork/Themes
[/LIST]

All of which you can setup/customise yourself in your first distro.
If so, this begs the question why do people rave about one distro over another?

Or am I missing something here?

E.g. what would be the difference between Fedora 7 and Kubuntu 7.04 if I set the themes to be the same and set the default applications to be the same?
The GDM, themes and apps would make them look identical wouldn't they?
I think the rpm/deb situation would be the only real difference.

Are people that make distros just repackaging a combination of many other peoples work or do they actually make any contribution themselves?

---

### Post by kevinlyfellow on 2007-06-19
Distros differentiate themselves from each other by have slight variations in the kernel and different default packages and configurations (especially compile time options).  If you were willing to compile different pieces of software (especially the kernel), you could very well start using fedora and make a system that is exactly like debian.  Of course this would take more work than its worth.

This news story may be interesting to you.  Its about a debate at a LUG about what a distro is.

[http://www.linux.com/article.pl?sid=07/05/07/2027212](http://www.linux.com/article.pl?sid=07/05/07/2027212)

---

### Post by juxtaposed on 2007-06-19
In theory, you'd think they would all be mostly the same. Oddly though, different distros seem very different to me. It's hard to explain.

---

### Post by Nikron on 2007-06-20
> **juxtaposed said:**
> In theory, you'd think they would all be mostly the same. Oddly though, different distros seem very different to me. It's hard to explain.

Not really.  All the (major) distros use different kernels, different package manager, different initscripts, and so on.  Ubuntu and Mint aren't very different, but as you can see different (modified) _everything_ Gentoo and Debian are completely different.

Personally, I think the biggest difference are in order, the package manager, the initscripts, and the kernel between distros

---

### Post by gamelord12 on 2007-10-17
Let's say you didn't have a specific distro installed and you just installed the kernel and other necessary items on top of it (if that's even possible)...could you find another package manager and whatever else makes a distro unique without them coming from a specific distro?  I don't plan on attempting this, I'm just trying to see how things work.  

Reworded: "Are there third-party package managers that you could download separate from a distro?"  and "Is it possible to install the kernel and start building a makeshift distro by installing desktop environments and such on top of it without installing a distro?"

---

### Post by SunnyRabbiera on 2007-10-17
its how everythings done.
For example despite how similar ubuntu and fedora are in apps and default desktop environment (gnome) under the hood they are quite different.
The most obvious is of course RPM and .deb but there are others, fedora uses YUM and ubuntu uses apt, ubuntu is targeted at the average user while fedora is targeted at performance, and of course ubuntu is more multimedia ready.
Now take a look at my current distro PClinux, by all respects its not all that different from mandriva but its use of apt and synaptic is what makes it stand out, I find PClinux to be the best RPM based distro as it handles its dependencies well compared to other RPM based distros.
There is a lot of similarities between PClinux and Ubuntu but the two have different goals and ways of doing things.

---

### Post by gamelord12 on 2007-10-17
Care to elaborate?  First give a technical explanation and then give a simplified witty little analogy if you can.

---

### Post by SunnyRabbiera on 2007-10-17
> **gamelord12 said:**
> Care to elaborate?  First give a technical explanation and then give a simplified witty little analogy if you can.

Sure, for one PClinux comes with flash and junk out of the box while ubuntu does not, PClinux is a bit more "media ready" in some respects but it is rather easy to do so on ubuntu.
Its philosophy and approach that matters here, PClinux's approach is to have a system that the windows user can feel comfortable with, its philosophy is to deliver a desktop ready linux that doesnt take a lot to make it media ready.
Ubuntu also targets the desktop user as well but it does not automatically give things like flash out of the box due to philosophical reasons, and perhaps legal ones as well. Ubuntu is definitely more FSF friendly then PClinux due it not giving codecs and junk out by default.
But in ubuntu's credit it is easy to get it media and codec ready, synaptic and its add and remove applet give it a great edge to make it easy.
Both have their flaws and strong points, I do not really prefer one to the other although currently I use PClinux... I like them both.

---

### Post by gamelord12 on 2007-10-17
Lol, that's not what I was asking about.  I know why they can't let things like DVD playback and mp3 playback be available on the initial use, but I was actually asking how are they different "under the hood"?  Is there anything stopping me from just downloading the programs that make one distro different from another?  For instance, Ubuntu 7.10 can write to NTFS while 7.04 can't.  What's stopping me from downloading that program that lets me do that rather than needing to upgrade my whole distribution?  They're running on the same kernel which I understand is the code that interacts with the hardware on a machine level, and everything else is built on that.  Am I right?

---

### Post by SunnyRabbiera on 2007-10-17
well in terms of under the hood distros vary on what they bring to the kernel, PClinux for example brings alot from mandriva in its setup, the hardware database is not really different between the two however mandriva might have a few more drivers here and there enabled by default.
Ubuntu also brings a lot to its kernel, but things to vary from version to another... Ubuntu is kind of weird on how it works, what works in version a of it might not work in version b...

---

### Post by TheThinker on 2007-10-18
Don't forget that many distros are unique due to how much system resources they take up. Puppy, for instance, is very lightweight, uses little RAM, yet is quite functional for its size and can be installed on very old PCs. Similarly, Xubuntu is lightweight in comparison to Ubuntu, which now runs on my younger-brother's **9yr-old 366mhz Emachine Celeron Computer**!! And that's on version 7.04. ;)

It's also important to note how efficient with resources certain distros are. You can have a very lightweight distro that is ridiculously inefficient with memory if it's not built right.

---

### Post by igknighted on 2007-10-18
> **TheThinker said:**
> Don't forget that many distros are unique due to how much system resources they take up. Puppy, for instance, is very lightweight, uses little RAM, yet is quite functional for its size and can be installed on very old PCs. Similarly, Xubuntu is lightweight in comparison to Ubuntu, which now runs on my younger-brother's **9yr-old 366mhz Emachine Celeron Computer**!! And that's on version 7.04. ;)

It's also important to note how efficient with resources certain distros are. You can have a very lightweight distro that is ridiculously inefficient with memory if it's not built right.

I disagree with this greatly.  Any distro can be made this light.  I can install Fedora or Gentoo or Mandriva or Suse or any distro I choose with Xfce and lightweight apps.  There is nothing inherent about Xubuntu that makes it any lighter than Mandriva or Suse with the same desktop and apps.

Any distro could be built from scratch.  This is basically what LFS is.  Building from scratch.  Follow the blueprints of any distro and you could build that one from scratch.  This would be a TON of work, but certainly possible.  There are differences in code between these.  As mentioned, Fedora and Ubuntu and all the other distros patch their OS independently so there could be subtle differences.  Distros often write their own hardware detection algorithms and many are different.  But in the end, you could almost always make one act just like another, it just might be a lot of work.

---

### Post by TheThinker on 2007-10-22
> **igknighted said:**
> I disagree with this greatly.  Any distro can be made this light.  I can install Fedora or Gentoo or Mandriva or Suse or any distro I choose with Xfce and lightweight apps.  There is nothing inherent about Xubuntu that makes it any lighter than Mandriva or Suse with the same desktop and apps.

Any distro could be built from scratch.  This is basically what LFS is.  Building from scratch.  Follow the blueprints of any distro and you could build that one from scratch.  This would be a TON of work, but certainly possible.  There are differences in code between these.  As mentioned, Fedora and Ubuntu and all the other distros patch their OS independently so there could be subtle differences.  Distros often write their own hardware detection algorithms and many are different.  But in the end, you could almost always make one act just like another, it just might be a lot of work.

Exactly what are you disagreeing me with? I never said you can't make a light distro from scratch, or edit a current distro to be lightweight,  and my conclusion is quite true; you CAN make a bloated distro, even with Linux. My post was based how distros work "out of the box" so to speak, and had little to do with how ambitious a user may be to change them to their tastes.

Yes, there is nothing inherent with Xubuntu, but what makes it different from Ubuntu is exactly what I was talking about; its use of system resources.

---

### Post by igknighted on 2007-10-22
> **TheThinker said:**
> Exactly what are you disagreeing me with? I never said you can't make a light distro from scratch, or edit a current distro to be lightweight,  and my conclusion is quite true; you CAN make a bloated distro, even with Linux. My post was based how distros work "out of the box" so to speak, and had little to do with how ambitious a user may be to change them to their tastes.

Yes, there is nothing inherent with Xubuntu, but what makes it different from Ubuntu is exactly what I was talking about; its use of system resources.

But Ubuntu is an exception here, in that Ubuntu is one of the few distro's that simply dumps a pre-fabricated image onto your hard drive.  The normal installers (not the live installers) for Mandriva, Fedora and the installers for Suse, Debian and Slackware all offer different profiles.  There is no "standard install" per se.  I guess you could call the default packages that are selected the "default", but they are there with expectation that you will change them, unlike Ubuntu which does all the picking for you.  So Fedora and Suse do not need a "Xfsuse" or anything like that... it is all there on the disk for you.

Which brings me to my main point of contention with your statements.  Your claim is that it is important to consider "how heavy/light" a distro is when choosing.  I say this is rubbish.  You are given on a default disk for most distro's all the packages needed to have a heavy or light system.  This IS the default.  So just because Ubuntu makes this more difficult, it is hardly the norm.  Almost any distro can, right out of the box using only the default disk, be just as light or full featured as others.  It's not about doing lots of work.  Pop in the Suse DVD or CD set and you will see a choice between KDE, Gnome, Xfce, Fluxbox and even Enlightenment IIRC.  Choose the DE/WM you want, review your package list, and install away.  It's nothing special, and the system is just as light (if using the DVD image on a computer without a DVD burner, a large flash drive will suffice).

Also, I really don't consider K/X/Ubuntu to be different distro's... merely different installers for the same distro.  You could get any one of those systems by starting with the same CD (the server CD) and adding.  This is essentially taking the install procedure from above, splitting it into several specialized disks and taking the choice away from the user.  Sure you get the convenience of less to download, but you lose the ability to choose.  I prefer the previous, but my point remains.  If you think of the various Ubuntu "distributions" as a different way of chopping up the same install procedure as I detailed above, it really is no different.  I think the repositories define the distro, rather than the installer.  Even a small (say 10-20 package) extra repo could make the difference between two distro's, but if they draw from the same sources, they are simply different installers.  NOTE: This is my opinion, not any fact written down anywhere.

---

### Post by TheThinker on 2007-10-23
Then I guess there is no such thing as a distro then. Fine. Tomato TomAto.

---

### Post by igknighted on 2007-10-23
> **TheThinker said:**
> Then I guess there is no such thing as a distro then. Fine. Tomato TomAto.

now you're getting it

---

### Post by rudeboyskunk on 2007-10-23
I would think it would be possible to just download the kernel and then all the necessary tools (Gnome, Firefox, etc) as tar.gz packages.

How else did the folks do it in the old days?  (i.e., early 90s)

---

