---
title: "Extreme Instability Of 11.10"
date: 2011-10-31
forum: Recurring Discussions
---

### Post by ted_001 on 2011-10-31
Dear All,
am I alone in finding 11.10 highly unstable?
I've used Linux since the advent of Red Hat 4.2, and over the years I've used most of the well known distributions.  But I've never had so many problems with any distribution as I've had with 11.10.  It's far more unstable than say Win95.
The symptoms are these:-
1.  There is a problem with usage of the computer resources (perhaps memory or the CPU).  This means that applications often become greyed out, and the computer refuses to accept any kind of input from the mouse or keyboard.  This tends to happen most when file transfers are happening in the background.  In the worst case scenarios the computer crashes completely, and will accept no input of any kind, and the only thing to do is to turn it off and on.
2.  The computer crashes when external USB hard drives are connected, and the 'Safely Remove' option is chosen.  The computer crashes completely, the 'Caps' and 'Scroll' lights flash on and off, and the computer will accept no input of any kind, and the only thing to do is to turn it off and on.
3.  It's difficult to know whether turning the computer off and on causes this third problem.  The computer will not boot at all.  The BIOS sees the SATA hard drive, but the boot process lands me into a console screen.  There is a ram disk with a full file system, but the ram disk seems to have lost the hard drive.  The only solution to this has been to boot from the Ubuntu installation CD, and use the 'Try Ubuntu' live disk.  The hard disk is recognised, by not mountable.  The only way to restore the system is to use 'gparted' to perform a file system check and repair on the hard drive, after which the hard disk will boot.
4.  These instabilities were far worse when the computer was upgraded from 11.04 to 11.10, but they have still continued even after a clean install of 11.10.
I have put hard disks with both WinXP and eCS 2.0 (i.e. OS/2) into the machine and there are no problems, so I don't think that this is an issue with the mother board or processor.
I respectfully suggest that Canonical withdraws Ubuntu 11.10 on a temporary basis until some of these issues are ironed out.
Best wishes,
Ted

---

### Post by Elfy on 2011-10-31
Thread moved to Recurring Discussions.

---

### Post by ted_001 on 2011-10-31
Dear forestpiskie,
I am disappointed that my post, which I believe was courteous and well meaning has not started a mature discussion, but has been relegated to a back water.
Best wishes,
Ted

---

### Post by philinux on 2011-10-31
> **ted_001 said:**
> Dear forestpiskie,
I am disappointed that my post, which I believe was courteous and well meaning has not started a mature discussion, but has been relegated to a back water.
Best wishes,
Ted

I would recommend you post a separate support thread for each issue. Also provide details so people can help you. Such as pc specs graphics card details etc etc.
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

In addition you could raise a bug report at launchpad for each issue.

I've got two machines running 11.10 without a single hitch as have many others.

You problems **could** be related to your specific hardware.

[edit] it could be kernel and your hardware. There is a new kernel in proposed. It will appear in update manager when it's ready.
[http://status.qa.ubuntu.com/reports/kernel-bugs/reports/sru-report.html](http://status.qa.ubuntu.com/reports/kernel-bugs/reports/sru-report.html)

---

### Post by 3rdalbum on 2011-10-31
Not sure how Canonical is going to fix bugs that haven't been properly reported. To me, your problems sound very much like bad RAM or another hardware issue. You don't recall an entire OS version just because somebody experiences some problems that are probably unrelated to the underlying software.

---

### Post by Ric_NYC on 2011-10-31
Yatahbuw

---

### Post by Ric_NYC on 2011-10-31
Yet
Another
Threat 
About 
How 
Bad
Unity 
Works

---

### Post by BigSilly on 2011-10-31
> **ted_001 said:**
> Dear All,
am I alone in finding 11.10 highly unstable?
I've used Linux since the advent of Red Hat 4.2, and over the years I've used most of the well known distributions.  But I've never had so many problems with any distribution as I've had with 11.10.  It's far more unstable than say Win95.
The symptoms are these:-
1.  There is a problem with usage of the computer resources (perhaps memory or the CPU).  This means that applications often become greyed out, and the computer refuses to accept any kind of input from the mouse or keyboard.  This tends to happen most when file transfers are happening in the background.  In the worst case scenarios the computer crashes completely, and will accept no input of any kind, and the only thing to do is to turn it off and on.
2.  The computer crashes when external USB hard drives are connected, and the 'Safely Remove' option is chosen.  The computer crashes completely, the 'Caps' and 'Scroll' lights flash on and off, and the computer will accept no input of any kind, and the only thing to do is to turn it off and on.
3.  It's difficult to know whether turning the computer off and on causes this third problem.  The computer will not boot at all.  The BIOS sees the SATA hard drive, but the boot process lands me into a console screen.  There is a ram disk with a full file system, but the ram disk seems to have lost the hard drive.  The only solution to this has been to boot from the Ubuntu installation CD, and use the 'Try Ubuntu' live disk.  The hard disk is recognised, by not mountable.  The only way to restore the system is to use 'gparted' to perform a file system check and repair on the hard drive, after which the hard disk will boot.
4.  These instabilities were far worse when the computer was upgraded from 11.04 to 11.10, but they have still continued even after a clean install of 11.10.
I have put hard disks with both WinXP and eCS 2.0 (i.e. OS/2) into the machine and there are no problems, so I don't think that this is an issue with the mother board or processor.
I respectfully suggest that Canonical withdraws Ubuntu 11.10 on a temporary basis until some of these issues are ironed out.
Best wishes,
Ted

I haven't had any of these problems OP. What is your spec? Did you check that you meet the [minimum requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition"), as it sounds like you might not have enough juice to run it. FWIW, my spec (below) runs Ubuntu 11.10 beautifully. I definitely think bug reporting is the way to go for you.

---

### Post by dvanzo on 2011-10-31
Hi!

I'm suffering the same bad experience with 11.10... Vostro 1500, 4Gb Ram, Nvidia 8600M GT.
This notebook works every single day since 9.10 up to 10.10 (current install). Everything works. 
Just to try the new version, I made a fresh 11.10 install to an external drive... The live CD worked perfect! Everything ok too... Then installed it... Never could make it work... No graphics... tried gdm, no luck... Againg to lightdm then it showed the greeter... Entered password..., character screen (something about checking battery....) and again to the login screen...
Installing 10.10 to the same external disk works like a charm...
Really, dont understand why I cant use the last version when the previous one did...

Regards, and sorry my english!!

---

### Post by noneofthem on 2011-11-26
I am having problems, too since I upgraded to 11.10. First my graphics card performance went down, then I lost my sound and at last I even lost my wifi connection. Apart from that programs like Transmission, Rhythmbox, LibreOffice and even Nautilus would freeze/or crash randomly. After reinstalling everything about a week later, I got my sound and wifi back. Graphics performance is still bad and I still get random crashes sometimes. Yesterday, I was just watching a YouTube video with the current Google Chrome and I got logged out! This is not what a final release should behave like. 11.10 feels like an early beta version to me. The media is blaming Unity for the loss of users. I think many people may have changed their distribution due to stability problems. I tried OpenSUSE 12.1 and Fedora 16. I didn't like either of them. Also I am not a fan of Gnome 3. It looks great, but it's unusable for me as it is right now. What good is a great looking desktop, if you cannot work with it? Unity feels much better and I wish they would get rid of the random freezes and crashes in 11.10. It could be awesome!

---

### Post by vasa1 on 2011-11-26
> **noneofthem said:**
> ... I wish they would get rid of the random freezes and crashes in 11.10. It could be awesome!
Random events are quite difficult to fix. If something was reproducible it should be easier to analyse.

For example, I haven't encountered any freezes/crashes/unsolicited log-outs etc. Maybe there's some hardware issue?

You should open a new thread for each issue and give as much of your hardware specs as possible.

---

### Post by noneofthem on 2011-11-26
> **vasa1 said:**
> Random events are quite difficult to fix. If something was reproducible it should be easier to analyse.

For example, I haven't encountered any freezes/crashes/unsolicited log-outs etc. Maybe there's some hardware issue?

You should open a new thread for each issue and give as much of your hardware specs as possible.

Hello there,

you are quiet right. I am a software developer myself and I know how hard it can be sometimes to fix things on different machines. However, I do not have these issues with other distributions and all Ubuntu versions prior to 11.10 were running well on this machine. Also, a lot of people seem to have problems with wifi and sound running 11.10 from what I can tell from the forums. I sent in some a bug report to canonical, too. I hope they can fix this.

---

### Post by vasa1 on 2011-11-26
> **noneofthem said:**
> ... I sent in some a bug report to canonical, too. I hope they can fix this.
If you include the bug number here it would be nice.

---

### Post by Copper Bezel on 2011-11-26
I had random X crashes, gnome-settings-daemon crashes (which seemed to take GTK3 applications with them,) and a number of other issues soon after upgrading, but most of those things have just seemed to go away with recent updates. I fixed some of the smaller problems with settings tweaks, but most of the real bugbears have more or less just gone away. So I can empathize with the initial reaction, certainly, even though 11.10 seems ultimately to be a very nice release.

---

### Post by 3rdalbum on 2011-11-27
EDIT: Whoops, I've already posted to this thread already saying exactly the same thing :-)

---

### Post by rudihawk on 2011-11-28
Mine has been pretty rock solid. 

I am using Gnome-shell instead of Unity though, so that might be the difference?

---

### Post by vasa1 on 2011-11-28
> **rudihawk said:**
> Mine has been pretty rock solid. 

I am using Gnome-shell instead of Unity though, so that might be the difference?

And I'm not seeing the type of instability reported either **but with Unity**. I upgraded on the first day 11.10 was released and haven't had a single crash. If it matters, I was using Unity on 11.04 as well and that was also stable. That's why I feel it may have something to do with individual tweaks/settings or hardware.

---

### Post by asifnaz on 2011-11-28
I am using 11.10 with unity . It crashes and freezes sometimes but not very often to make it unusable .

But it is not as stable as I could want Linux to be . actually windows 7 is way far more stable than Ubuntu 11.10 

I have not paid anything to canonical so I am fine with it

---

### Post by rudihawk on 2011-11-29
> **vasa1 said:**
> And I'm not seeing the type of instability reported either **but with Unity**. I upgraded on the first day 11.10 was released and haven't had a single crash. If it matters, I was using Unity on 11.04 as well and that was also stable. That's why I feel it may have something to do with individual tweaks/settings or hardware.

Yep, I agree. Even when I was using Unity it was solid and stable.

---

### Post by Copper Bezel on 2011-11-29
And, conversely, all of my early stability problems were under Gnome Shell, so. = )

---

