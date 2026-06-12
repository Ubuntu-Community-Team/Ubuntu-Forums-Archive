---
title: "Printer Problems"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by forseti42 on 2008-04-25
I followed the instructions I found on this page to set up my DCP-130C, but alas it still doesn't work.  It worked before on Gutsy, but it doesn't want to work on Hardy.

Attached is what my terminal displays.

---

### Post by forseti42 on 2008-04-25
This page is what i followed:
[http://ubuntuforums.org/showthread.php?t=512309](http://ubuntuforums.org/showthread.php?t=512309)

---

### Post by forseti42 on 2008-04-25
I have a paper due tomorrow so I need to get this fixed urgently!

---

### Post by forseti42 on 2008-04-25
Bump

---

### Post by David Andersson on 2008-04-26
Just a hunch:
The error "mkdir: cannot create directory `/var/spool/lpd/dpc130c': No such file or directory" may cause subsequent operations to fail. Maybe the deb assumes the parent directory /var/spool/lpd already exists, but it does not. Can you check if the directory exists:

```
ls -dl /var/spool/lpd
```

If it says "No such file or directory" then create it using

```
sudo mkdir /var/spool/lpd
```

and try install dcp130clpr-1.0.1-1.i386.deb again.

EDIT: Now I have installed a Brother DCP-350C using the instructions at Brother ([http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html)).
I had the same error as forseti42 had in step 4, I did "sudo mkdir /var/spool/lpd", repeated step 4 and continued. Then everything seems to have worked all right. I can print the test page from both the web-interface and from System > Administration > Printing configuration tool.

---

