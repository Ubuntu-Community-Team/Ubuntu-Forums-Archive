---
title: "ACPI error on bootup"
date: 2022-08-23
forum: New to Ubuntu
---

### Post by potshot on 2022-08-23
I upgraded my old ubuntu to the new version and am getting this error msg about ACPI error and 


have no idea what it is.  I still get into ubuntu ok though.  So any advice on this?

---

### Post by pantazi on 2022-08-23
Similar to this thread:


[https://ubuntuforums.org/showthread.php?t=2477426](https://ubuntuforums.org/showthread.php?t=2477426)

Check my answer.

---

### Post by potshot on 2022-08-24
Thanks pantazi but it didn't work.  I am still getting the error msg's on startup.  I have updated Ubuntu and still
get errors though.  Ubuntu still seems to work ok, so I will just have to live with it for awhile though.

---

### Post by pantazi on 2022-08-25
Thank you for replying potshot.

The answer I gave cured it for me after extensive searching. Perhaps as tea for one suggested it is kernel related.

---

### Post by tea for one on 2022-08-25
Does your /etc/default/grub file include the added parameter (in blue)?
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#0000FF"]loglevel=3[/COLOR]"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true
```

---

### Post by potshot on 2022-08-25
I am new and still learning nano. However it looks just like your example.  The log level 3 is in the file.

---

### Post by tea for one on 2022-08-26
After editing the file, did you run:-```
sudo update-grub
```

---

### Post by potshot on 2022-08-26
Yes and it shows up when I run the file from terminal after leaving sudo to do other things.

---

### Post by potshot on 2022-08-26
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290929&stc=1[/IMG]I have tried to attach log in screen error msg.

---

### Post by potshot on 2022-08-28
I think I will try Mint linux and see if it works better.  Thanks for all the replies.

---

### Post by potshot on 2022-08-29
I downloaded Linux Mint and tried it and found that the same error msg's came up
as with Ubuntu.  Since Mint is based on Ubuntu i guess they use the same
bootup routine, so I'm getting the same error.  So I will wait and see if some
later updates to these distros will fix it.

---

### Post by pantazi on 2022-08-30
This offers some sort of explanation.

[https://linux.org/threads/acpi-error-after-installing-ubuntu-22-04.40993/](https://linux.org/threads/acpi-error-after-installing-ubuntu-22-04.40993/)

---

