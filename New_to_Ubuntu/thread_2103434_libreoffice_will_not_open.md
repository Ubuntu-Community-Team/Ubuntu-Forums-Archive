---
title: "libreoffice will not open"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by ianb72 on 2013-01-10
I have recently installed Ubuntu 12.10 after running windows 7 and open office for a while, but when I try to open any of my open office spreadsheets or just open LibreOffice all I get is the green splash screen and then it disappears and nothing happens!

Also when I try and open an odt file by clicking on it I again get the green splash screen then I get a white screen with loading document in the bottom left hand corner then that just disappears too!

Any idea's what I can do to get these running properly?

---

### Post by ajgreeny on 2013-01-10
Try renaming the libreoffice folder in your home (/home/user/.config/libreoffice) as libreofficebak, then try again.  Maybe there are some corrupt files in the LO configuration, particularly if it came from a previous OOo configuration;  That is what happened to me when I removed OOo and installed LO originally in 10.04.

Just make sure you don't remove your old LO configuration, just rename it, or you'll lose any templates etc, that you have made.

---

### Post by ianb72 on 2013-01-10
> **ajgreeny said:**
> Try renaming the libreoffice folder in your home (/home/user/.config/libreoffice) as libreofficebak, then try again.  Maybe there are some corrupt files in the LO configuration, particularly if it came from a previous OOo configuration;  That is what happened to me when I removed OOo and installed LO originally in 10.04.

Just make sure you don't remove your old LO configuration, just rename it, or you'll lose any templates etc, that you have made.

That didn't do it, I installed it Libreoffice and Ubuntu onto a blank HD, a complete clean install

---

### Post by iMac71 on 2013-01-10
you might try the following command:```
sudo apt-get install --reinstall -f -y libreoffice
```that should fix any kind of issues that might have happened during the previous installation process.

---

### Post by ibjsb4 on 2013-01-10
If that doesn't work, try opening it in terminal.

```
libreoffice
```

Get any errors?

---

