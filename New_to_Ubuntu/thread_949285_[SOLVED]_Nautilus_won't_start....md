---
title: "[SOLVED] Nautilus won't start..."
date: 2008-10-16
forum: New to Ubuntu
---

### Post by djsjbh on 2008-10-16
[FONT="Arial"][SIZE="3"][/SIZE][/FONT]

Hi folks, I'm trying to gain permissions over a HD that I just formatted in ext3. I'm typing gksudo nautilus but I'm not getting the graphical user interface. Instead, root is opening. I'm trying to change permissions and I thought I needed the gui (I remember doing this a couple of months ago), what am I doing wrong this time?

---

### Post by iaculallad on 2008-10-16
> **djsjbh said:**
> [FONT="Arial"][SIZE="3"][/SIZE][/FONT]

Hi folks, I'm trying to gain permissions over a HD that I just formatted in ext3. I'm typing gksudo nautilus but I'm not getting the graphical user interface. Instead, root is opening. I'm trying to change permissions and I thought I needed the gui (I remember doing this a couple of months ago), what am I doing wrong this time?

Root is opening? How is that? Running **gksudo nautilus** will automatically open upon input of correct authentication.

---

### Post by TeaSwigger on 2008-10-16
You have a box pop up you mean? There should be a line where you enter your password. Then hit ok. Nautilus should then open, and whatever you do will be as the "root" / "administrator" account. Be very careful doing anything as root of course.

You don't need a gui to change permissions on anything, you can do that in a terminal with "sudo" at the start of the command to do the command as root. That may not be what you're after, just clarifying.

---

### Post by djsjbh on 2008-10-16
The root file browser is opening rather than the Nautilus gui. I'm also getting an error...

Net usershare: cannot not open usershare directory. error 255

also...

nautilus: 6053 Warning: unable to add monitor


my monitor works just fine. I'm not sure what is going on here.

---

### Post by TeaSwigger on 2008-10-16
You might be interested in this page:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

You have tried to open Nautilus from a terminal, and in the process you can see these errors in the terminal? Nautilus is the file browser, for your user or as root. Since your system seems to be working ok for you, those errors may be ignored; perhaps look into them separately or ask about them specifically later on at your convenience as to what, if anything, should be done.

---

### Post by djsjbh on 2008-10-16
Thank you folks...the web page helped.

---

