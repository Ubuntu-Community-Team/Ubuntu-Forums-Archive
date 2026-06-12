---
title: "How do you mount a zen ipod?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by harryliddic on 2008-09-09
The manual for aramok says to mount an ipod before transfering music. I made two directories one /dev/zen and the other /mnt/zen and tried to mount them but got the error message: not in fstab ot mstab. The zen ipod is hooked to a usb hub running from a port on my computer. There is no mention of it in lshw. Should I hook to one of the direct usb ports? Does anyone know how to edit fstab correctly? Should I take up the piano?

---

### Post by txcrackers on 2008-09-09
Get rid of the directories you made - they won't be used and, no, you don't need to modify fstab. The piano thing is entirely up to you.

Typically, if you plug in a USB device that the system can handle, it'll try to automount it for you. So, yes, try plugging it in directly. Also make sure you have *libmtp* installed - it's a dependency of Amarok.

(P.S. "Zen" isn't an iPod - it's a portable music player from Creative Labs, whereas Apple makes the iPods.)

---

### Post by Zzl1xndd on 2008-09-09
The Zens are made by Creative and are not iPods. An iPod is an Apple Product, for most creative Zens you need to use the MTP settings.

---

### Post by harryliddic on 2008-09-09
amarok wants preconnect connect command i.e. 'mount %d' and wants a pre-disconncect command i.e. 'eject %d'

---

### Post by Zzl1xndd on 2008-09-09
Do you have the model for the Zen? Just wanna make sure we get the easiest way for you to do this.

---

### Post by harryliddic on 2008-09-09
creative zen 16gb, its black with a video screen and cost about $175

---

### Post by anjilslaire on 2008-09-09
Part of the trick is libmtpfs for the Zens. Check my howto:

[http://anjilslaire.wordpress.com/2008/05/16/creative-zen-v-plus-on-kubuntu/]("http://anjilslaire.wordpress.com/2008/05/16/creative-zen-v-plus-on-kubuntu/")

---

### Post by Zzl1xndd on 2008-09-09
:) anjilslaire beat me to the punch, I was just about to post I link to his blog.

---

### Post by anjilslaire on 2008-09-09
> **tweakedenigma said:**
> :) anjilslaire beat me to the punch, I was just about to post I link to his blog.

Wow, I noticed that that's a relatively popular post (10+ hits per day), but I didn't think people recommended it.

I'm humbled :)

Edit:
Hopefully his 16gig will work the same way

---

### Post by harryliddic on 2008-09-09
aramok is red flagging all my transfers what could be the the problem; they are all mp3's  everything when smooth as butter until that

---

### Post by anjilslaire on 2008-09-09
Clear your queue, cleanly disconnect (with the disconnect button) & try again. Ocasionally, I've had Amarok choke on me when transfering files. It may have just been a hiccup.

---

### Post by harryliddic on 2008-09-10
I have seemingly tried everything including your instructions. Could it be that most of this songs come from a mounted windows drive(  why am I not in windows doing this? because I am a windows 2000 holdout and the disk that came with zen is XP.)

---

### Post by anjilslaire on 2008-09-10
hmm, that could be. Move a few to a linux drive and try the transfer. That should narrow down a partition issue.

Edit:
Try mounting the NTFS drive as writeable. That may help as well.

---

### Post by harryliddic on 2008-09-10
while I wait til SRV cd is ripped. Could it be that I am using a playlist to fill the queue rather than individual songs. With the windows partiton it is a pointer pointing to a pointer pointing to a pointer etc.

---

### Post by Zzl1xndd on 2008-09-10
I would bet that is your problem.

---

