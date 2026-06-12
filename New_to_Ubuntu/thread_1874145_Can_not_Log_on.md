---
title: "Can not Log on"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by Billum on 2011-11-02
Hi I have just installed ubantu it seemed to go ok when finished it ejected the disc toled me to remone it and boot up, it started up ok untill the logon I entered my user name ok the it asked for my pass word but I could not enter it none of the keys would work can you help Bill

---

### Post by Jaybyrrd on 2011-11-02
See if you can login via terminal:

Ctrl+Alt+F2

Then it should ask for login information. Do it.

Then 

```

sudo service lightdm stop
startx

```

And you should get thrown into the GUI environment as your user. I don't know how to fix that your password won't type but that should at least get you logged in.

I am assuming you are using Oneiric Ocelot, and that you use lightdm, if you use GDM, change lightdm to gdm, or whatever you are using.

---

### Post by haqking on 2011-11-02
> **Billum said:**
> Hi I have just installed ubantu it seemed to go ok when finished it ejected the disc toled me to remone it and boot up, it started up ok untill the logon I entered my user name ok the it asked for my pass word but I could not enter it none of the keys would work can you help Bill

if you are a console or terminal then passwords do not locally echo which means it looks like nothing is being typed, type it anyways and press enter.

If it is GDM/LDM then there should be some feedback though masked.

Text based there is no feedback though

cheers

---

### Post by Jaybyrrd on 2011-11-02
Oh, I kind of assumed he was in GDM or lightDM and having this issue. Didn't think he might be in terminal and never seen it before. :O

---

### Post by haqking on 2011-11-02
> **Jaybyrrd said:**
> Oh, I kind of assumed he was in GDM or lightDM and having this issue. Didn't think he might be in terminal and never seen it before. :O

yeah he probably is at GDM or LDM, but sometimes it boots to text mode, or he might of installed server by accident and so again will be in text mode

---

### Post by Garland Fox on 2011-11-02
When my wife had 10.04 installed sometimes the keyboard does not respond on her hp dual boot machine. we unplug the usb keyboard and plug it back in the kb works ok.

---

### Post by Billum on 2011-11-04
Hi thanks all for your help but it was my fault I had installed server insted of desktop now ok:D

---

### Post by haqking on 2011-11-04
> **Billum said:**
> Hi thanks all for your help but it was my fault I had installed server insted of desktop now ok:D

thought so ;-)

remember to use thread tools to mark thread as solved

---

