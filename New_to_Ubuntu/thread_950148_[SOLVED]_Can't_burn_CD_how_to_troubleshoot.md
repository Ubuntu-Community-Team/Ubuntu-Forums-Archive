---
title: "[SOLVED] Can't burn CD: how to troubleshoot"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Frogbarf on 2008-10-16
After nearly two months, I've finally gotten around to trying to burn a CD on a new machine. Can't do it. It's an audio CD I'm trying to duplicate for a friend who can't make backup copies on his ancient Win 2000 machine. Shortly after Sound Juicer gets into the write phase, it comes up with "Error writing to the disk".

Brasero didn't succeed either.

It's quite possible that this is a hardware problem since it's a new drive, but since the guys who built the machine for me are Windows guys, I need to make sure it's the hardware before I go running to them for a replacement drive. At the very least, if what I've got is a problem with configuration, say, or permissions, if I replace the drive, I'll still be in the same boat as I am now.

Even if it's a hardware problem, surely there's evidence in a log file somewhere, no?:confused:

Advice gratefully received.

PS: Here in Canada, it's legal to copy CDs. We pay a special tax on each blank that goes to a performing rights collective.


More info:

Tried Brasero. It failed too. Different error message. Log shows:

[I]BraseroCdrdao stderr: HUP
BraseroCdrdao process finished with status 1
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroCdrdao stopping
BraseroCdrdao got killed
Session error : unknown (brasero_burn_record burn.c:2273)[/I]

Solution: after trying Sound Juicer, Brasero, and CDRDAO, I concluded this was a hardware problem because they all gave similar error messages at the same place in the burn process. Replacing the DVD/CD drive with a CD drive known to function gave flawless burn using Brasero.

In case anyone is interested in my experiences with different burners, Brasero seems to be the easiest to use to copy an Audio CD, but CDRDAO, even though it's command line, turned out to be pretty easy to use too.

Thanks to those who suggested solutions. You're all great people.

---

### Post by earthpigg on 2008-10-16
> **Frogbarf said:**
> an audio CD I'm trying to duplicate for a friend,

you may want to clarify by making a statement that your intent is to help his friend back up media that he legally owns, lest your thread get closed for seeking advice on piracy :)

edit: tried different burning programs? brasero, etc

---

### Post by SuperSonic4 on 2008-10-16
It is either hardware or software :p

Personally, I think it is software in this case, try using K3B or Brasero. For me (on kubuntu) k3b has never caused problems

---

### Post by eternalnewbee on 2008-10-16
Could also be a problem with the cd...
Have you tried anotherone?

---

### Post by eternalnewbee on 2008-10-16
I agree with Supersonic on Brassero ( I use Gnome).

---

### Post by ww711 on 2008-10-16
You mention sound juicer in your post, are you trying to make a mp3 album or a 1:1 copy of the CD?


Assuming you are making an exact copy with Brasero and used the 'Disc Copy- Create 1:1 a copy of a CD/DVD' button in Brasero, this should be straightforward.

Is the CD in a good physical state? e.g. no scratches, etc? Can you playback the music CD?

As others have suggested, try another program buring program as mentioned, k3b.

---

