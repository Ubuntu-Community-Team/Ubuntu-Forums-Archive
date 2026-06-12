---
title: "m4a file wont open ! =("
date: 2008-10-22
forum: New to Ubuntu
---

### Post by swimm3r137@gmail.com on 2008-10-22
My friend sent me a email with a m4a formatted sound file attached.  I tried to open it via gmail using ubuntu and it says this- 

/tmp/Sigma Nu Anthem-2.m4a could not be opened, because the associated helper application does not exist. Change the association in your preferences.

---

### Post by mlentink on 2008-10-22
afaik m4a is Apple's proprietary format used on iTunes. So it's unlikely you will be able to play such a file out of the box.

---

### Post by DFlame on 2008-10-22
Have you [Installed the restricted extras package](https://help.ubuntu.com/community/RestrictedFormats)?

DFlame

---

### Post by Pconfig on 2008-10-22
> **DFlame said:**
> Have you [Installed the restricted extras package](https://help.ubuntu.com/community/RestrictedFormats)?

DFlame

And more specifically:

[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)

;)

---

### Post by swimm3r137@gmail.com on 2008-10-22
ive installed everything you've asked me too from both replies, but it still won't work.... same error message.  anyone have any ideas?

---

### Post by nu2this on 2008-10-22
Bear in mind I'm not sure, but have you d/l'd that mp4 to your PC?  If so, try VLC.

---

### Post by Teamgeist on 2008-10-23
Try ```
sudo apt-get install faac
```

---

### Post by mjwhitfield on 2008-10-23
> **mlentink said:**
> afaik m4a is Apple's proprietary format used on iTunes. So it's unlikely you will be able to play such a file out of the box.

It's not Apples format:
> Audio-only MPEG-4 files generally have a .m4a extension. This is especially true of non-protected content.

Generally, m4a files are AAC in a wrapper.

---

### Post by Flimm on 2008-10-23
Try saving it to your home directory or to the desktop, and opening from there.

---

