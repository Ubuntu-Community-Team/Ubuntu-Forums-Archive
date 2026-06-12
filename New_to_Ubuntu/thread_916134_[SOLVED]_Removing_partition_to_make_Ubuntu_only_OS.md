---
title: "[SOLVED] Removing partition to make Ubuntu only OS"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by jrsc109 on 2008-09-10
OK - I have Ubuntu 8.04 installed as a dual boot with WinXP.

However, I'm having such fun with Ubuntu, I want to can XP altogether.

How can I (a) uninstall XP or (b) expand the Ubuntu install to overwrite the XP partition and use the whole drive.

Please note I am a complete newbie, and if the answer is re-install, I won't be losing much to start again.

Help much appreciate.

---

### Post by cdtech on 2008-09-10
Learn to use the Live CD. If you boot into the Live CD get to the desktop go to "System > Administrator > Partition editor", there you can delete partitions, size, expand and format.

You can just delete the Windows partition then expand the Ubuntu partition into the unallocated space.

Hope this helps......

---

### Post by tangibleorange on 2008-09-10
> **jrsc109 said:**
> OK - I have Ubuntu 8.04 installed as a dual boot with WinXP.

However, I'm having such fun with Ubuntu, I want to can XP altogether.

How can I (a) uninstall XP or (b) expand the Ubuntu install to overwrite the XP partition and use the whole drive.

Please note I am a complete newbie, and if the answer is re-install, I won't be losing much to start again.

Help much appreciate.

to be honest, if you're willing to reinstall, it's probably worth it. that way, you can just select "use entire disk" at the partitioning stage rather than having to edit your partitions manually and possibly edit your /etc/fstab file.

---

### Post by acidsolution on 2008-09-10
use mkfs command 

see man page for the more :)

---

### Post by cdtech on 2008-09-10
A lot of users will just reinstall when it comes to problems or complicated situations rather than learn the system. This is a great place to start learning, I think. I recommend that you keep a document of steps that you take on everything you do within Ubuntu. I have a complete change log that I keep current on everything I do.

---

### Post by anjilslaire on 2008-09-10
Please, to make upgrading/reinstalling your OS easier in the future, set /home in its own partition. This will allow you to completely format your OS partition "/" and reinstall without losing any settings or preferences. 

Here:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by jrsc109 on 2008-09-11
Thanks to everyone for your responses.

I decided, since I wasn't too far down the line, to do a complete re-install.

Now am one very happy Ubuntu user - looking forward to a stable future...

Thanks:)

---

