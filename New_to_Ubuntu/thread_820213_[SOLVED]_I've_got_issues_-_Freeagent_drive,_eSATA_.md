---
title: "[SOLVED] I've got issues - Freeagent drive, eSATA expresscard, and more!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by SeanLor on 2008-06-06
Greetings, folks! I've never used Linux of any form, and am now sorry I wasted years defaulting to Windows. The community is freakin awesome, the open source nature is all kinds of cool, I'm beyond impressed! 

That being said, I'm having a few issues getting everything set up - this truly is a horse of a different colour. I'm your average joe windows user, with little to no knowledge of programming lingo and very limited experience with a command prompt. That being said, you can basically assume you're responding to an orangutan that's somehow learned to type; step by step help would be much appreciated, whenever possible. Alright, my issues thus far are as follows:

I've got a Dell Inspiron 1525, very basic laptop, with Ubuntu & Vista both successfully installed. I have an external hard drive (seagate freeagent 750) that Ubuntu recognized once, but now it doesn't; all the media I wanted access to lives there, and I miss it dearly. I've tried resetting the drive's sleep cycle to 'never' & safely removing it in Vista, but Ubuntu still won't pick it up. The drive can connect via USB, or by eSATA to a 54mm expresscard (which my system doesn't currently acknowledge either.)

I'd also like to know how to go about viewing media on my TV, connected by s-video; the desktop, windows and whatnot show up on the tv screen, but when I try to watch a video, the player itself shows up but it's just a black screen where the video should be. Stuff plays just fine on the laptop screen, it's just on the TV that the issue lies.

Any and all advice would be much appreciated. I'll sacrifice a goat to appease the Linux gods, if need be. Or bake you some cookies, if you're ever Alberta bound. Or generally sing your praises on high, take your pick. Thanks in advance!

---

### Post by finito on 2008-06-06
well I am at the office but I can you try to goto system -> preferences - > Removable media (it should be name something like that) and then goto one of the tabs there should be an option to auto mount usb drive (i have to get back home for the exact name of the option)

One more thing what is the File system type of your hard drive, NTFS or FAT? if you don't know go into windows right click on your hard drive and goto properties it will say over there.

As for the TV thing I don;t have much experience in dealing with that.

---

### Post by SeanLor on 2008-06-06
Man, that's some quick response! Thanks for getting back to me. So:

The file system is NTFS, and when I went to 'removable media' there isn't an option for removable usb drives; there's PDAs, cameras, scanners, etc, but no drive option that I can see. And the TV issue is definitely back burner, no worries there.

---

### Post by finito on 2008-06-06
well assuming that it worked before I suppose you have ntfs-3g installed just in case try 'sudo apt-get install ntfs-3g' in Terminal. I will have to get back home for the exact tab.

---

### Post by finito on 2008-06-06
here try this:
[http://ubuntuforums.org/showthread.php?t=785263&highlight=usb+drive](http://ubuntuforums.org/showthread.php?t=785263&highlight=usb+drive)

---

### Post by SeanLor on 2008-06-06
Excellent, okay; I had previously copied & pasted some terminal suggestions from other threads, just had no bloody clue what I accomplished. Still don't, for that matter,but I suppose that's beside the point. after changing to the eSATA interface, going back into windows, fiddling around a bit, safely removing hardware again, & restarting Ubuntu, the drive is recognized. Woo hoo! As for the nfts-config tool, the drive shows up & it says <click here to set a mount point>. Vas is das? Where should I be mounting said drive so as it'll show up automatically next time? Thanks much for the help - I'll check back in the morn, it's getting late over here. Have a good morn/aft/eve/night. Damn time zones. ;^)

---

