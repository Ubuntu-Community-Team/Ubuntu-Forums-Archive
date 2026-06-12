---
title: "Reinstall of 11.10 walk through?"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by pokerkid on 2012-06-03
Can someone walk me through how to reinstall 11.10 after I upgraded to 12.04. I am having problems with 12.04 such as random log offs when I am watching videos. I don't like it and it seems no one knows how to solve this problem. I want to do this without a CD if possible. I just want to download 11.10 and have that replace 12.04. Thanks.

---

### Post by Bucky Ball on 2012-06-03
No way of doing that. You need to reinstall (clean) from CD or USB stick. There, unfortunately, is no going back. You can't rollback to a previous release.

My rule of thumb? Wait for a few months after a new release before installing. Inevitably there are bugs to iron out. I refuse to go anywhere near 12.04 for anything serious as I need stable, reliable production machines. I'll be running 10.04.4 for the next year then doing a minimal install of 12.04 myself. ;)

A fairly common practice is to have a stable Ubuntu installed on one partition and a spare partition for new releases. That way, you always have your favourite, stable, squeeze while you can test the invariably buggy new release on the other partition. You have a stable release to fall back on when/if the other breaks.

---

### Post by drs305 on 2012-06-03
If you have the 11.10 ISO file on your computer you can add an entry for it in your grub menu and from that menu you can boot into the ISO and install from there. But as was mentioned, you will have to do a full installation and will either overwrite you old installation or have to put it on a new partition.

If this is what you want to do I'll provide a bit more information.

---

### Post by Bucky Ball on 2012-06-03
> **drs305 said:**
> If you have the 11.10 ISO file on your computer you can add an entry for it in your grub menu and from that menu you can boot into the ISO and install from there. 

Interesting. Thanks for that tip ... ;)

Will this then behave like you were installing from CD/USB? (Sorry to the OP for getting a little off topic. ;))

---

### Post by drs305 on 2012-06-03
> **Bucky Ball said:**
> Interesting. Thanks for that tip ... ;)

Will this then behave like you were installing from CD/USB? (Sorry to the OP for getting a little off topic. ;))

Yes. There are a couple of extra things you have to do but once started it installs the same. 

Here are the two links. If the OP wants specifics I can give the important things from each as neither is independent or totally necessary. (Nor is the rescue prompt needed).
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

[ISO Booting with Grub 2 ]("http://ubuntuforums.org/showthread.php?t=1549847")

---

### Post by pokerkid on 2012-06-03
> **drs305 said:**
> Yes. There are a couple of extra things you have to do but once started it installs the same. 

Here are the two links. If the OP wants specifics I can give the important things from each as neither is independent or totally necessary. (Nor is the rescue prompt needed).
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

[ISO Booting with Grub 2 ]("http://ubuntuforums.org/showthread.php?t=1549847")

Thanks for your response. I do not have any installation software.  
I installed ubuntu about a year ago from a CD and I don't know where it is. I subsequently updated and ungraded gradually as the new OS came out. I just updated to 12.04 and the system just logs me out whenever I am watching videos. I have no idea what the problem is and others have reported this as a BUG issue with no known solution yet. 

In any event, what I would like to do is back up my hard-drive and run a fresh install of Ubuntu 11.10. However, I have no idea how to do that anymore. Question#1: Is there a hard-drive back-up program that I can download from Ubuntu software???

If you are willing to do a write up on that, I would be grateful. I would be doing everything on 12.04 with Gnome Classic because I hate Unity interface.

---

### Post by Guitar John on 2012-06-03
Before you go through all of that, is it possible that you have a heat issue.  I had a similar problem (using 11.10) where the computer would randomly shut down when watching videos on YouTube or Vimeo.  

I noticed that the fan was usually blowing out really hot air right before this happened.  I used canned air and blew out a surprising amount of dust.  After this, the problem ceased.

Just a thought.

---

### Post by pokerkid on 2012-06-03
> **Guitar John said:**
> Before you go through all of that, is it possible that you have a heat issue.  I had a similar problem (using 11.10) where the computer would randomly shut down when watching videos on YouTube or Vimeo.  

I noticed that the fan was usually blowing out really hot air right before this happened.  I used canned air and blew out a surprising amount of dust.  After this, the problem ceased.

Just a thought.

I just cleared all that out 2 weeks ago...sure it is possible BUT I wasn't having the problem until moments after updating to 12.04. 
So, it is unclear. Can I download heat guage or something to monitor temps?

---

### Post by Bucky Ball on 2012-06-03
If you cleaned things out a couple of weeks ago I doubt this is the issue. You would feel the hot air blowing from the machine when it crashes and you wouldn't need a heat gauge for that.

I would say 12.04 is the culprit, or something therein. Do you have all codecs installed?

---

### Post by pokerkid on 2012-06-03
> **Bucky Ball said:**
> If you cleaned things out a couple of weeks ago I doubt this is the issue. You would feel the hot air blowing from the machine when it crashes and you wouldn't need a heat gauge for that.

I would say 12.04 is the culprit, or something therein. Do you have all codecs installed?

Yeah, cool air is blowing out the back. 

Hmm, I heard of them "codecs" but I have no idea how to find them on ubuntu. I am a newbie to all this. PLease advise

---

### Post by Bucky Ball on 2012-06-04
In software centre you might try looking for ubuntu-restricted-extras. That should install all the codecs you need (but be aware that some of these are third party/proprietary drivers, not open source). ;)

---

### Post by pokerkid on 2012-06-04
looks like I already had them..._but thanks._ I think it is a bug with the new version that has yet to be worked out...I'll just have to reinstall 11.10 for now

---

### Post by birdie1234 on 2012-06-04
No way of doing that

---

