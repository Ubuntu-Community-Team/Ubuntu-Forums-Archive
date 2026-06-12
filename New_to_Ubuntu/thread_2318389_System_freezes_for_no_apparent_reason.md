---
title: "System freezes for no apparent reason"
date: 2016-03-25
forum: New to Ubuntu
---

### Post by Bewildered_Bob on 2016-03-25
I recently installed 14.04 but for some unexplained reason it freezes regularly while doing "plain vanilla" stuff. The Windows equivalent is "blue screen of death" altho the Ubuntu screen has a maroon background with many identical horizontal characters. Latest software updates have also been installed.

(1) how can this situation be searched in the forum ?
(2) what is needed to report it ?

Thanx.

[I][U]Newbie & Bewildered Bob
[/U][/I]
HP Inspiron 505B
AMD Athlon II X2 250
4 GB RAM
64-bit OS
Integrated NVIDIA GeForce 6150SE nForce 430

---

### Post by QIII on 2016-03-25
Hello!

Could you detail your hardware?

Are you using a proprietary graphics driver?

---

### Post by Bewildered_Bob on 2016-03-25
Thanx for quick reply. The specs have been posted.

Bob

---

### Post by X-RED_Tech on 2016-03-25
What driver are you using for the nvidia card?

---

### Post by sandyd on 2016-03-25
Hi, can you post the output of the following, which will allow us to find more information about your system.

Loaded Kernel Modules
```

lsmod
```

Installed NVIDIA packages
```

dpkg -l | grep 'nvidia\|nouveau'
```

Xorg configuration
```

cat /etc/X11/xorg.conf
ls -l /etc/X11/xorg.conf.d
```

---

### Post by Bewildered_Bob on 2016-03-26
(see later post for details)

---

### Post by mörgæs on 2016-03-27
Help is offered but you are not receiving...?
People are waiting for you to post the output from the commands in # 5.

---

### Post by Bewildered_Bob on 2016-03-28
> **sandyd said:**
> Hi, can you post the output of the following, which will allow us to find more information about your system.

Loaded Kernel Modules
```

lsmod
```

Installed NVIDIA packages
```

dpkg -l | grep 'nvidia\|nouveau'
```

Xorg configuration
```

cat /etc/X11/xorg.conf
ls -l /etc/X11/xorg.conf.d
```
===================================================================
Hello: i am a true NEWBIE to Linux so will some more help capturing the output and including in my response.

(1) how can the results be stored for posting to the forum ?

(2) the 2 cmds for Xorg config when entered show err msg that the file or folder does not exist. I carefully entered the parameters shown twice.
============================================================================================

Stlll Bewildered Bob

---

### Post by Bewildered_Bob on 2016-03-28
Display driver is HP 1.60.0.0 (i think).  Since Win 10 shares the HD with Ubuntu and since Win 10 does not include a compatible display driver, a replacement was loaded instead.

---

### Post by mörgæs on 2016-03-28
> **Bewildered_Bob said:**
> I carefully entered the parameters shown twice.

It's safer to copy and paste the commands into a terminal.

---

### Post by Bewildered_Bob on 2016-04-01
Hello Sandy: since i am a true newbie to Linux i really need help -

(1) the first 2 cmds when entered manually produce displayed output - how can it be directed to a file/folder for posting on forum ?

(2) the 3rd & 4th cmds (xorg.conf) reference an invalid file/folder.

(3) how is copy/paste done in Ubuntu ?

Thanx.

Bewildered Bob

---

### Post by Bewildered_Bob on 2016-04-01
Hello: plz see post # 11 for results of my attempt to enter cmds. Thanx.

Bewildered_Bob

---

### Post by Amy_Milam on 2016-04-01
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by ian-weisser on 2016-04-01
> **Bewildered_Bob said:**
> (1) the first 2 cmds when entered manually produce displayed output - how can it be directed to a file/folder for posting on forum ?
Don't redirect. Simply highlight, copy, paste.

> **Bewildered_Bob said:**
> (3) how is copy/paste done in Ubuntu ?
Use the Edit menu to avoid confusion.
There is a keyboard shortcut, but it's not CTRL+C. The terminal shortcuts are older than the GUI shortcuts you are used to.

---

