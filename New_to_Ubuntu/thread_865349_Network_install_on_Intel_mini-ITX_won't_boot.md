---
title: "Network install on Intel mini-ITX won't boot"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by brons2 on 2008-07-20
Hello, I bought a Intel mini-ITX board yesterday for $39.99 at Fry's, model D201GLY2.  It has an embedded Celeron 1.2 processor and is fanless.  I also bought 1GB of memory for it as well.  I intend on using it as a low-power homemade NAS.

Machine has no CD or floppy, so I made a bootable USB key to install Ubuntu and Samba.  That seemed to go OK after some trial and error.  Network install ran smooth and fast, thanks to 8Mb Internet connection.

But after installation and reboot, the machine does not pick up on the installation and gives a message "No bootable device -- insert boot disk and press any key"

I have had this problem occur twice now, once with the first drive, a SATA drive.  On the SATA drive, the problem was so bad, it hung the machine after Ubuntu install and reboot.  I thought maybe that there was some conflict between between the SATA3.0 drives and the board, since the board only supports SATA1.5.  (I will keep working on this, apparently there is a jumper setting, but I don't have any of the tiny jumpers it requires)

The second drive I tried was an old 30GB PATA drive, which had a dual boot Windows 98/XP configuration on it.  When I hooked that one up, it tried to boot into Windows so I had some confidence that it would work once I went through the install process.  I figured I would try Xubuntu this time too, probably a bit more appropriate to this low powered machine.  No such luck, same problem.  At least this time it doesn't hang the machine, but you can't do anything either other than hit OK to continue.

I do have access to a CD drive, but I'd rather not go through yet another install.  Help!

---

### Post by brons2 on 2008-07-20
Never mind, I gave up and hooked up a CD-Rom and installed from CD.  That worked OK.

Now, to get Prime95 working for a stress test.

---

