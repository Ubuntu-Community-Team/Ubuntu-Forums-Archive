---
title: "Untraceable error when trying to install Ubuntu server 18.04"
date: 2018-09-22
forum: New to Ubuntu
---

### Post by snattack on 2018-09-22
Hello,

New to this forum, so sorry if there are similar posts.

I'm trying to install Ubuntu 18.04, but I can't manage to boot from the USB install media. I've done the process before on several computers.

The installer goes through the entire boot process, but it get stuck on what looks like "top half" of a login screen, then with 2 second intervals, there are an error message flashing, which is displayed so shortly that it's impossible to read. I tried taking a photo with my cell phone camera, but it too slow to get it sharp enough to be readable.

This flashing happens 4 times, then it's get stuck with a blank black screen and cursor blinking.

Pause/break on the keyboard doesn't work for some reason.

Any suggestion how to troubleshoot this annoying error? First step is to be able to read what is says =)

Best,
Andreas

---

### Post by TheFu on 2018-09-22
Does it work if you  boot from the install media and choose "Try Ubuntu"?

---

### Post by snattack on 2018-09-22
> **TheFu said:**
> Does it work if you  boot from the install media and choose "Try Ubuntu"?

Is that an option in the regular grub boot menu? The only option was to "Check Disk for errors", and I did that, returned "No Errors".

I will try with a non-server-version tomorrow.

---

### Post by TheFu on 2018-09-23
I missed you were using the Server version. Sorry. 

Yes, using a desktop ISO will let you "Try Xubuntu" whatever the desktop version is.  I'd find the smallest one, just to reduce the download time.  I would avoid the normal, default, Ubuntu Desktop.  It can come in handy to have one lying around.  Almost any issue can be fixed using alternate bootable media.  I use Ubuntu-Mate for this sort of stuff, but Xubuntu, Lubuntu would be perfectly fine too.  Just use the exact same release as you want to install the server version.

---

### Post by snattack on 2018-09-23
So, some clarity:

First: Ubuntu Desktop starts and works as supposed. I tried re-writing the Server-installation to the same stick: No luck, same error.

Second: It is possible - in the server edition - to select other terminal tty:s through the F2-Fx keys. So the problem seems to be that the actual installer doesn't start.

I'll try tomorrow to find a way to manually start the installer. Any idea how this can be achieved?

---

