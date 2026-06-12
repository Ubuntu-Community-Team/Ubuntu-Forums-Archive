---
title: "Bluetooth: 16.04 doesn't work; 15.10 does work; any chance 18.04 will work?"
date: 2018-01-15
forum: New to Ubuntu
---

### Post by kate.t on 2018-01-15
Hello all,

Having struggled mightily with connecting Bluetooth speakers and headphones in Ubuntu 16.04 with no luck whatsover (despite trying every fix I could find with google, and with excellent suggestions given here on this forum), I tried a diagnostic procedure mentioned on a different website.

It had been suggested on this forum that my major problem was interference on the 2.4GHz band. That was a very sensible suggestion since it's a known problem and no other solution was panning out. Over, the weekend, however, I came across a comment on another forum where it was suggested to try Bluetooth on Ubuntu 15.10 first to see if the problem was with 16.04. The commenter said that 16.04 basically "broke" Bluetooth functionality.

With nothing to lose, I decided to try that by loading Ubuntu 15.10 on a bootable DVD disk, and trying it out from the CD/DVD drive. To my shock and amazement, Bluetooth connected with my devices beautifully on the first try, with no problems. "Interference" did not prevent success. (The streaming audio still stutters a bit initially on my Tower Stereo speakers, but then it becomes smooth shortly thereafter.)

My question is this: is it better to regress from 16.04 to 15.10 in order to gain Bluetooth functionality without having to run from a bootable disk, or should I wait until April and try out 18.04?

I have seen websites describing the upcoming 18.04 version as being different in many ways from 16.04, and I've seen several comments that 18.04 will offer "better Bluetooth support". I'm not sure what that means. Does that mean the developers will have redesigned the whole Bluetooth setup (I don't know what to call it). Or will they simply be starting out with 16.04's setup and tweaking it further? 

If I decide to install 15.10, will there be aspects of that operating system which will conflict with my current programs? In other words, are there any incompatibilities I should know about?

Thanking you in advance for your thoughts on the matter!

Kate

---

### Post by Impavidus on 2018-01-16
Ubuntu 15.10 is old and dead. It hasn't had any security fixes in a year and a half. Don't use it. But have you tried a live disk of 17.10.1? 18.04 will have many changes compared to 16.04, but most of those changes are already present in 17.10.1.

---

### Post by kate.t on 2018-01-16
Impavidus,

Thanks for the suggestion! In the course of trying to find a solution to the problems with 16.04, I ran into complaints about Bluetooth and 17.10, too. However, I think your suggestion is a great idea. I lose nothing by trying it, and I'll be getting some idea of what 18.04 will be like.

If it turns out that my Bluetooth situation is still bleak on 17.10.1, then I will just use the 15.10 boot disk for those occasions when I'm desperate for streaming music. I won't install it in any event.:)

---

### Post by kate.t on 2018-01-16
Impavidus,

Ooops. Here's an update: it looks like I won't be trying 17.10.1 after all. I checked out the release notes and this is what I found out:

"Incompatibility with BIOS in certain Lenovo, Acer systems 

A  bug in the Linux 4.13 kernel shipped in Ubuntu 17.10 can leave users  unable to update any of their BIOS settings, including their system&#8217;s  boot order, after booting this version of Ubuntu. 


A  kernel with a fix for this issue will be available in zesty-updates  shortly, but, the Ubuntu 17.10 installer images still contain the kernel  with this bug.  Users with affected systems should not upgrade to  Ubuntu 17.10 **or boot an Ubuntu 17.10 installer image**  until this issue as resolved.  Doing so may result in your computer  requiring professional servicing in order to restore BIOS functionality.  
A full list of known affected models can be found in [1734147]("https://bugs.launchpad.net/bugs/1734147"). 


If  you have already installed Ubuntu 17.10 on an affected system, you may  not immediately notice this problem because Ubuntu will continue to boot  from disk.  To verify whether your system has been affected by this  bug, create a USB stick with the Ubuntu 16.04 desktop image and try to  boot it.  If you are able to boot it, your system has most likely not  been impacted by this bug."

I have a Lenovo G50-70, and when I checked the list of affected models, mine was on the list. I'm sure glad I read the release notes, because I don't want my BIOS corrupted! It's a shame, but I guess I'll just be waiting for 18.04 in April.

Thanks again!
Kate

 
[h=2][/h]

---

### Post by JonPaul on 2018-01-16
What about trying 14.04 LTS. That is still supported.... [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

---

### Post by kate.t on 2018-01-16
JonPaul,

Thanks for the suggestion! That sounds like a good idea. I even remember using 14.04 on another laptop and there wasn't any problem with using Bluetooth then. 

Now all I have to do is decide whether to run it on disk until April or install it now.

Do you (or anyone else) know whether there might be compatibility problems if I roll back from 16.04 to 14.04? I mean, in terms of programs or anything else I should know about. (I still don't know enough about Ubuntu to frame this question more accurately; I just want to make sure I don't end up somehow in a world of hurt -- because I need this laptop for work.)

Thanks,
Kate

---

### Post by Impavidus on 2018-01-16
> **kate.t said:**
> Impavidus,

Ooops. Here's an update: it looks like I won't be trying 17.10.1 after  all. I checked out the release notes and this is what I found out:

"Incompatibility with BIOS in certain Lenovo, Acer systems 

A  bug in the Linux 4.13 kernel shipped in Ubuntu 17.10 can leave users   unable to update any of their BIOS settings, including their system&#8217;s   boot order, after booting this version of Ubuntu. 

Yes, there is a nasty bug present in 17.10, and that's why they released  17.10.1. Normally the interim releases don't get any point releases,  but because this was such a severe bug they made one this time. The  17.10.1 live disk should be safe to use. It seems they haven't updated the release notes...

> **kate.t said:**
> JonPaul,

Thanks for the suggestion! That sounds like a good idea. I even remember using 14.04 on another laptop and there wasn't any problem with using Bluetooth then. 

Now all I have to do is decide whether to run it on disk until April or install it now.

Do you (or anyone else) know whether there might be compatibility problems if I roll back from 16.04 to 14.04? I mean, in terms of programs or anything else I should know about. (I still don't know enough about Ubuntu to frame this question more accurately; I just want to make sure I don't end up somehow in a world of hurt -- because I need this laptop for work.)

Thanks,
Kate
Downgrading isn't supported so that means a clean install of 14.04. You'll get older versions of most applications, which may not be compatible with the documents and config files made by the applications on 16.04 &#8211; although most of the time it works. The lighter flavours of Ubuntu 14.04 are no longer supported.

You can also dual boot 16.04 and some other supported release, if you have room on your hard drive. That should run faster than a live disk.

---

### Post by kate.t on 2018-01-16
Impavidus,

Thanks for the clarification! I will try 17.10.1 as a live disk and then see if I want to upgrade to it.

Best regards,
Kate

---

### Post by mc4man on 2018-01-16
I don't think it's 16.04 per se, likely more specific hardware and or methods used.
Here in 16.04 bluetooth speakers work just fine for me, within a couple of seconds of turning on the speaker it pairs & auto-connects
(the auto connect feature I added as a pulseaudio patch I suggested for 17.10 was not backported to 16.04.

16.04 got some bluetooth & pulseaudio updates, 18.04 a bit more so for many functionality will be good. However some hardware, particularly headsets,  may still be deficient.

---

