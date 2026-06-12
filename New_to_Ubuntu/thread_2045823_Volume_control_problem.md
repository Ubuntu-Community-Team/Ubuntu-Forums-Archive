---
title: "Volume control problem"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by thedarkwingduck on 2012-08-22
I'm having trouble wit the volume control. It seems to be disabled.
I have sound coming out of the speakers but very quietly.

[IMG]http://i48.tinypic.com/33w48ra.png[/IMG]


(full disclosure: I am a n00b)

I've searched around and haven't found this problem (!?)
Its a new install of Ubuntu.
It did work.
I saw one post where someone booted into LinuxMint LiveCD and that appeaed to fix it (?) -- I booted back into the LiveCD, but surely thats not broken it.

Help?

---

### Post by sandyd on 2012-08-22
***Moved to ABT***

---

### Post by eneskuray on 2012-08-22
can you find your speakers at list in sound settings?

---

### Post by racoon23 on 2012-10-28
> **eneskuray said:**
> can you find your speakers at list in sound settings?

Hello,
I'm having the same problem on Ubuntu 12.10. I can listen to sound/music with Rythmbox / Totem but the main control volume is greyed out.
It seems to work fine in the login screen, but once logged in it looks exactly like OP's picture:

[IMG]http://img62.imageshack.us/img62/8356/soundissue1.png[/IMG]


I can't find my sound card or whatever should be in sound settings:

[IMG]http://img4.imageshack.us/img4/8734/capturedu20121028084124.png[/IMG]

 Thank you for taking time out to help me!

---

### Post by racoon23 on 2012-10-28
Ok I think I figured out what my problem was, I changed my /home partition after installing Ubuntu to a NTFS one and all directories/files belonged to root. After modifying my /etc/fstab to grant permissions on it, rebooting, chown-ing files and again rebooting, everything was back to normal.

---

