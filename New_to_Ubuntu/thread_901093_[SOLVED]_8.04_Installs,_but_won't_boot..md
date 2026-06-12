---
title: "[SOLVED] 8.04 Installs, but won't boot."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by csk1007 on 2008-08-26
First off, I searched through the topics for about 10 minutes, I'm sure someone has run into this issue, but I was so tired of scanning through all the topics, so I decided to just post a new one.

The Setup
Core 2 Duo E8400
4GB DDR2 800 Ram
nVidia 8800GT (I know there are driver issues here)
Western Digital 400GB HDD

So, when I tried to install from the regular CD (which I downloaded and burned) it didn't recognize the hard drive in either the x64 or i386 in the partition scanner. It was just a blank page. 

I went and downloaded the alternate install, and it detected the hard drives just fine, and it even installed just fine.

After I restarted the computer, Ubuntu took about 5 minutes or so, and didn't start. Just a command line came up, called BusyBox 1.1.3. The commands were very limited, and it wasn't Bash, so I am not sure where to go from here. I think the problem is that the video won't start, because it doesn't have drivers. I have the linux driver on a USB disk, but I don't know how to get it to read it, install it, or even get Ubuntu to boot so I can do that.

Right now I am confused and frustrated because I have spent hours, and I bet I will be spending many more.

Any clues? Ideas? I'm willing to answer any questions.

Thanks in advance!

---

### Post by Michael.Godawski on 2008-08-26
Did you try to boot into the fail safe mode? I mean safe graphic mode?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by csk1007 on 2008-08-26
Actually, after about 8 or 9 installs, Ubuntu finally loaded.

Weird... Now to try to figure out how to install nVidia drivers.

---

### Post by OffAxis on 2008-08-26
To install the nvidia drivers for ubuntu it's 
**System-->Administration-->Restricted Drivers Manager**

Just put a check in the box as Administrator.

---

### Post by csk1007 on 2008-08-26
I've read that somewhere before, but there is no "restricted" drivers option anywhere. There's a regular "drivers manager", but it doesn't give any options. I've tried looking for it, but its not anywhere. I'll take a screen shot tonight if you guys don't believe me.

---

