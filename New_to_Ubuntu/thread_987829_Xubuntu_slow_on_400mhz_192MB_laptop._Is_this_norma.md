---
title: "Xubuntu slow on 400mhz 192MB laptop. Is this normal?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by skippyscamp on 2008-11-19
Is it normal for xubuntu and applications constantly max out the processor on an old laptop? I just did my first linux install from the live CD of xubuntu 8.10 onto a Toshiba laptop with an 400mhx AMD K6 processor and 192 MB ram, 4G HDD. I had to select "Install with ACPI workaround" or install would hang at the language selection.

xubuntu so far is much more processor-intensive than than the Windows2000 it replaced. Viewing the top bar CPU monitor, simply moving the cursor bumps the CPU to 25% or so, and typing this post on firefox regularly gets the CPU into 75% range. Loading a web page pegs the CPU at 100% for the duration of the load, and scrolling down a page can take minutes.

With no applications running, system monitor shows CPU 0% for all applications except for monitor, which hovers at 50-60%.

Did I do something wrong?

---

### Post by kerry_s on 2008-11-19
with xubuntu probably, try the straight debian version.
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso)

---

### Post by vgots on 2008-11-19
> **skippyscamp said:**
> Is it normal for xubuntu and applications constantly max out the processor on an old laptop? I just did my first linux install from the live CD of xubuntu 8.10 onto a Toshiba laptop with an 400mhx AMD K6 processor and 192 MB ram, 4G HDD. I had to select "Install with ACPI workaround" or install would hang at the language selection.

xubuntu so far is much more processor-intensive than than the Windows2000 it replaced. Viewing the top bar CPU monitor, simply moving the cursor bumps the CPU to 25% or so, and typing this post on firefox regularly gets the CPU into 75% range. Loading a web page pegs the CPU at 100% for the duration of the load, and scrolling down a page can take minutes.

With no applications running, system monitor shows CPU 0% for all applications except for monitor, which hovers at 50-60%.

Did I do something wrong?

Well, there's something about system requirements for Xubuntu in Wikipedia:
> Xubuntu can be installed with one of 2 CDs, both requiring at least 1.5GB of hard drive space. Installing with the Desktop CD requires 192 MB of RAM, while the Alternate CD (which uses a text based installer), requires 64 MB of RAM, and also allows access to additional options for the installation.[2] Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

Maybe you will be interested in Fluxubuntu for your laptop?

---

### Post by skippyscamp on 2008-11-20
Thanks, from my other searches, I think you're both right. xubuntu needs more ram than I have. It's going to have to be an even lighter linux than xubuntu. Damn Small Linux looks like a good option too, since I'm a linux noob.

---

### Post by snowpine on 2008-11-20
Yes, it is normal... the 2008 version of Xubuntu has higher hardware requirements than the 2000 version of Windows. :)

My vote for most user-friendly-yet-lightweight variant of Ubuntu is called Crunchbang. It is a totally unsupported "remix" that uses a windows manager called Openbox. I like it for Linux beginners because it comes standard with a lot of things Xubuntu doesn't, like flash, mp3, skype, etc. yet somehow manages to be faster. It uses the same "guts" as Ubuntu so most of the tutorials and tips you read on this website will also work in Crunchbang. I would not recommend Fluxbuntu at this point, as the project is defunct. 

If you want to leave the Ubuntu family, Debian is very similar (Ubuntu is based on Debian) but seems to be a bit faster for most people. Debian Lenny (the "testing" version--but don't let that scare you) with the Xfce desktop is the closest to Xubuntu. If you are a techie and are up to the challenge (it's a very cutting edge "stable unstable" variant of Debian), there is also Sidux with Xfce, which has incredible hardware detection for old hardware. 

Then there are the non-Debian distros designed specifically for older hardware. These are typically the fastest options. DSL, Puppy, and SliTaz are probably the most popular around here. SliTaz is my favorite of those, Puppy is probably the easiest to get started on, and DSL is the most "geeky old school" in my opinion. 

Finally, you can create your own slimmed-down version of just about any Linux. What you do is install a minimal command line, then install a lightweight windows manager (Openbox, Fluxbox, IceWM, etc) or desktop environment (LXDE is very user-friendly) and the applications you need. You can do this with any distro (Ubuntu, Debian, Arch, Slackware, etc.) if you are the do-it-yourself type.

Good luck!

---

### Post by LowSky on 2008-11-20
Personally DSL or Puppy is the way to go, they have a good amount of support and run on nearly anything

---

### Post by cardinals_fan on 2008-11-20
I'd check out SliTaz loram on that machine.

---

### Post by mikjp on 2008-11-22
> **skippyscamp said:**
> xubuntu so far is much more processor-intensive than than the Windows2000 it replaced.

Yes it is. Xubuntu is not much easier for the hardware than Ubuntu is. In my opinion, Xubuntu is too much for P1000 + 256 Mb -- I've trimmed down all the unneeded services and still the machine sometimes grinds something on the hardware for more than 30 minutes making the machine totally unusable. 

Try something lighter, like VectorLinux, Slackware or Debian if you want a system using apt-get.

---

### Post by ksennin on 2008-11-28
I think at those ranges the ram is very determinant.  I have xubuntu 7.10 on a 667mhz dell optiplex GX110 and it works fine with ram maxed out to 512mb.  It slows down noticeably when opening multiple tabs in firefox but for light browsing, text processing, skype and children's games (SuperTux!) it runs decently.  Only in full featured gmail do I see lags in display while typing reply mails.

I did use a few of Kmandla's tips on speeding up, though. (Thanks!)

And I do add a recommendation for Crunchbang.  I was surprised at how efficiently it worked, and how many things were preinstalled.  The desktop wallpaper selection in the live cd is sparse to say the least, but do not let that scare anyone away from a pretty good recombined distro.

---

### Post by halitech on 2008-11-28
> **kerry_s said:**
> with xubuntu probably, try the straight debian version.
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso)

+1 for this. I have it running on a P266 with 96 meg of ram and while it's not as smooth as my desktop (P4) it is completely usable. Here's a good how to from the debian site

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

