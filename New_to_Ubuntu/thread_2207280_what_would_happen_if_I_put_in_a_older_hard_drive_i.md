---
title: "what would happen if I put in a older hard drive into the computer I have now"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-02-22
I am new with all this and I just don't know.
I have a computer running Ubuntu 13.5, I had another computer running the same thing, but was a different make & module. Both are SATA hard drives. One computer died and is just too old to keep fixing. I would like to get the files off the hard drive. I was thinking I could just plug it into the other computer and get the files. But not knowing anything about computers, I would hate to kill or hurt the one that is still working, doing this. So I thought I would ask? is this fine to do or is there another way of retrieving the files off the hard drive?

---

### Post by Vladlenin5000 on 2014-02-22
There are two different and unrelated issues here.
One is the hardware part. I don't recommend anyone saying "*But not knowing anything about computers*" to mess with hardware parts. It usually is a recipe for disaster. That said, just connecting another SATA drive should be easy enough for a 4 years old child (OK, just kidding here... 5yo is more like it). Then comes the second part...
Permissions... That depends on the file system of the second drive, the one retrieved from the old computer - you forgot to mention what OS was it running, file system of the driver (how was it formated)... -. It also depends on whether it is encrypted or not, etc. Please post more details.

PS - Don't open multiple threads for the same issue...

---

### Post by squakie on 2014-02-22
Do you know anything about working on the hardware at all?  It is a relatively simple thing to do, but if you have no knowledge about working with the hardware it may be a little hard to explain.  You don't need a detailed knowledge, just a very basic one.  Do you know what a SATA data cable looks like?  Do you know what the SATA jack on the motherboard looks like?  Do you know what a SATA power cable looks like?  If so, you can do this.  It's a matter of powering off, unpluggin the power cord, opening the case, mounting the drive in an empty "slot", connecting the SATA power cable and connecting the SATA data cable to the drive and to the motherboard, then closing the case back up, connect the power cord and turn the PC on.

---

### Post by Dennis N on 2014-02-22
You can also just purchase an external enclosure for your old SATA drive which will connect it to your USB port. In this way it can then be used like any other external USB connected hard drive. Many sell for $15 - $20 at places like Amazon or New Egg.

---

### Post by Vladlenin5000 on 2014-02-22
It really isn't that simple... The hardware part surely is and I already commented on that. The other part is actually accessing the contents due to different user permissions. Assuming the second drive was retrieved from a PC running Ubuntu - it seems so now that I red the OP for the second time plus his/her other thread - then most certainly the contents (MP3???) are inside the old PC's main user personal folder, area that could also be encrypted or even the whole drive itself. This is the *real* issue, not connecting the disk, be it internally or in an external enclosure. That a 5yo can do but even to barely scratch the surface of the concepts about file systems, user permissions, etc. one need to be 10yo at least...

---

### Post by EZZ9 on 2014-02-22
Ok, let me expand I know how to plug in the other hard drive that's easy. Come on?  I want to know is it going to run with the other hard drive? Is there a butting heads think I have to deal with the two hard drives running the same Ubuntu 13.4? Are there any configuring programs I need to do? Can I just plug it in and everything will just work fine?

"PS - Don't open multiple threads for the same issue" WHAT are you talking about? Don't assume my other questions are about this computer???

---

### Post by Vladlenin5000 on 2014-02-22
If you make no changes to the boot sequence the computer will boot from where it always booted, the second disk will be ignored for the time being regardless of its contents. That's a non-issue, totally... What I'm afraid of is after all that trouble and effort you won't be able to access its contents if that's your intention. If you want to just add a second drive and format it clean then it's fine and you can do it from your running Ubuntu with the proper tools like *gparted*. You CAN'T do the same for the drive where the system is running - obviously - but the added drive is just that, another drive. Again, assuming you won't change the boot order, that is.

PS1 - Sorry about the confusion but you know, it's also about a second drive... Man, you must have loads of drives. Don't you by any chance have a +2TB one to spare? Oh, and BTW you can mark the other thread as solved because there's really nothing else to add unless, of course, there's something in the link you don't understand.
PS2 - There's no such thing as Ubuntu 13.5 or 13.4. It's either 13.04 or 13.10 (13 = 2013 / 04 = April / 10 = October). If you're running 13.04 then seriously consider upgrading to 13.10 or use the latest 12.04 LTS. Never 13.04 which has reached EOL (end of life).

---

### Post by Impavidus on 2014-02-23
The new computer will boot from its own hard drive, ignoring the old one you inserted. After you have logged in, you can mount the old hard drive and copy the files. If the user IDs don't match, you may not have permission to do so, but then you can use sudo. If the drive is encrypted things get more complicated.

Alternatively, if the hardware on both machines is sufficiently compatible, you can change the boot order and boot your new computer from the old hard drive and have access to the drive immediately, encrypted or not. This won't work if you have for example different proprietary graphics drivers installed.

---

### Post by EZZ9 on 2014-02-23
Ok, I don't think I have encrypted it, I don't know what that is, sounds sad but I just don't know. It is from an old computer that died and was wondering if I could get the files off of it. PLEASE don't mix this question up with others I have asked, I am running two computers. One for Meda the other for writing & net.

---

### Post by Vladlenin5000 on 2014-02-23
OK. :)

So go ahead and install the second drive. Start your computer as usual and you'll see it starts the same way as it ever did. The only difference now being the extra drive which won't even be mounted unless you tell the system to do so. If you use the standard Ubuntu (with Unity) you'll see a new icon (drive) in your launcher (the left bar), just click it and it'll be mounted and a file manager window will open. Then you should be able to navigate in the old drive's folders - assuming the full drive isn't encrypted -; the files you're looking for are probably somewhere inside /home/your_old_username in the usual Documents, Music, etc. folders. At this point - now assuming the /home isn't encrypted either - you should be asked for authentication (username/password). I don't know exactly how it looks like or how and when it comes because I never done this way before. 
Post back any errors you found or other oddities. We'll comment/troubleshoot from there.

---

### Post by jlguru on 2014-02-23
> **Dennis N said:**
> You can also just purchase an external enclosure for your old SATA drive which will connect it to your USB port. In this way it can then be used like any other external USB connected hard drive. Many sell for $15 - $20 at places like Amazon or New Egg.

+! on this answer. I have one of these plugged into this computer as I write this. Works fine w/ Ubuntu 12.04 and Windows 7.

Live long, and prosper

---

### Post by EZZ9 on 2014-02-24
Cool good to know. So how do I make this one solved?

---

### Post by Vladlenin5000 on 2014-02-24
I think is in thread tools in the top of the page...

---

### Post by Iowan on 2014-02-24
> **EZZ9 said:**
> Cool good to know. So how do I make this one solved?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by EZZ9 on 2014-02-24
Mark as solved. Ok How, I don't see a solved button. lol

---

### Post by deadflowr on 2014-02-25
> **EZZ9 said:**
> Mark as solved. Ok How, I don't see a solved button. lol

Do you not see a Mark this thread as solved in the Thread Tools dropdown options?

---

### Post by EZZ9 on 2014-02-25
lol its hiding got it thanks

---

