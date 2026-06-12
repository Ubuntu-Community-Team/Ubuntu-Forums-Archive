---
title: "Won't play audio CD's"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2008-04-25
This seems strange. When I pop a data disk into my CD/DVD drive it mounts automatically and a window opens up automatically on the desktop, showing me the contents of the disk. All is well.

Yet when I pop in an audio CD nothing happens. No programs open up. No window. I looked in the "media" folder and it doesn't appear to be mounting. It shows up in the left pane of "Computer" as "CD-ROM disk" (which appears when I pop an audio disk in), but a folder doesn't appear in the right pane...as it does when I insert an audio CD. So I'm guessing that for some reason, it's not mounting audio CD's.

Any ideas? I'm using Mint Gutsy. I've tried this with six pre-recorded audio CD's and none show up.

---

### Post by philphil on 2008-04-26
does this help? [http://ubuntuforums.org/showthread.php?t=77146](http://ubuntuforums.org/showthread.php?t=77146)

---

### Post by SpongeBob SquarePants on 2008-04-26
> **philphil said:**
> does this help? [http://ubuntuforums.org/showthread.php?t=77146](http://ubuntuforums.org/showthread.php?t=77146)

Hi Phil,

Thanks for the reply. No it doesn't help. The problem is not that a program isn't auto-starting per se. The problem is that when I install an audio CD, it doesn't appear to mount. Yet when I insert a data CD it does.

---

### Post by Kosimo on 2008-04-26
> **SpongeBob SquarePants said:**
> Hi Phil,

Thanks for the reply. No it doesn't help. The problem is not that a program isn't auto-starting per se. The problem is that when I install an audio CD, it doesn't appear to mount. Yet when I insert a data CD it does.

Try installing audacious (from add & remove programs)

Open Audacious, then right click, plugin services, ADD CD.

Works out of the box.

Hope it helps.

---

### Post by SpongeBob SquarePants on 2008-04-26
> **Kosimo said:**
> Try installing audacious (from add & remove programs)

Open Audacious, then right click, plugin services, ADD CD.

Works out of the box.

Hope it helps.

Hi there,

Thanks for you reply. The problem isn't finding a program to play audio. It's that Mint isn't seeing the music files for some reason.

If I insert a pre-recorded CD, it shows up in "Computer" under "Places" as "CD ROM disk", but no folder mounts under /media. If I insert a CD-R disk of music I've made using K3b, it shows up under Places as "blank CD-R disk", and the Serpentine dialogue box opens up asking me if I want to create a CD. So MINT is seeing that there's a CD in there. And I've burnt loads of .ISO files. But for some reason, when it's a audio CD....I'm not sure what's happening. A folder doesn't appear in /media (as it does when I insert a data disk. So does that mean it's not mounting? Yet a CD icon appears under places when I insert and audio CD.....and it can at least see a blank disk has been inserted....plus I can burn .ISO files. Yet when I insert a music CD no folder mounts, and Mint can't seem to see any audio tracks.

---

### Post by philphil on 2008-04-26
what do you get when run this command in the terminal ```
 sudo mount /media/cdrom 
``` (with an audio CD inserted)?

---

### Post by SpongeBob SquarePants on 2008-04-26
> **philphil said:**
> what do you get when run this command in the terminal ```
 sudo mount /media/cdrom 
``` (with an audio CD inserted)?

I get.....

myname:~$ sudo mount /media/cdrom
[sudo] password for myname:
mount: special device /dev/hdc does not exist
myname:~$

However, even with a data disk in, using the command you gave, I get the same error message, yet the data disk clearly mounts as I can see the information.

---

### Post by philphil on 2008-04-26
hmp, yeah ok....

ummm....have you tried playing the CD in your media player anyway? can your media player see the CD?

---

### Post by SpongeBob SquarePants on 2008-04-26
> **philphil said:**
> hmp, yeah ok....

ummm....have you tried playing the CD in your media player anyway? can your media player see the CD?

Hi Phil,

Trying to play it in my media player was what alerted me to the problem in the first place. Amarok came back with a "Could not read audion CD" message, which made me try a few other media applications. None of them can see the CD. 

This is what made me start looking to see if it was mounting properly. It doesn't appear to be. Yet when I put in a data CD it mounts with no problem at all. Quite strange.

---

### Post by mc4man on 2008-04-26
audio cds don't 'mount' per se, so they won't show up in /media, /dev, ect. What you should see on desktop or in computer is Audio Disk, you can't have playback till then. I'll try a little searching though info specfic to mint may be sparse. Here's same issue - unfortunately 'resolved' by fresh install
[http://www.uluga.ubuntuforums.org/showthread.php?t=739743](http://www.uluga.ubuntuforums.org/showthread.php?t=739743)
you could insert a disk then run  dmesg | tail   -maybe something interesting will show up
note: last line of  CDROM not ready.  Make sure there is a disc in the drive. 
- would normally be expected

---

### Post by SpongeBob SquarePants on 2008-04-26
> **mc4man said:**
> audio cds don't 'mount' per se, so they won't show up in /media, /dev, ect. What you should see on desktop or in computer is Audio Disk, you can't have playback till then. I'll try a little searching though info specfic to mint may be sparse. Here's same issue - unfortunately 'resolved' by fresh install
[http://www.uluga.ubuntuforums.org/showthread.php?t=739743](http://www.uluga.ubuntuforums.org/showthread.php?t=739743)
you could insert a disk then run  dmesg | tail   -maybe something interesting will show up
note: last line of  CDROM not ready.  Make sure there is a disc in the drive. 
- would normally be expected

Thanks a lot. Bad news for me I guess. His problem is the exact same one as mine, and interestingly, his CD ROM is the same one as mine too. Who'd have though that cheap crap would be so problematic. Anyway, I'll probably try installing Ubuntu in the morning...and give that a bash. 

Thanks for everyone's efforts. Much appreciated.

---

### Post by Dwarfyperson on 2008-11-08
I encountered the same problem, however, a little bit of poking around the repos solved it. i believe tha package was cd-utils, or possibly paranoia0-utils. in any case it shows up under a search for cdda. This does not allow the disc to be mounted or to show up automatically on the desktop, or in fact to be browsed at all. It does allow the audio to be played using exaile (or whatever your media player of choice is) and ripped using sound-juicer (or whatever your cd ripper of choice is). I figured I would post this so no one else decides to re-install when it really isn't nescessary.

EDIT: just checked, the package is libcdio-utils. This should install libcdio-paranoia0 as a dep. I also installed libcdio-cdda0, not sure if that one is required. Anyway, hope this helps.

---

