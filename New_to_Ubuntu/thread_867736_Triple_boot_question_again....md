---
title: "Triple boot question again..."
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Rishi87 on 2008-07-23
So, here's the deal. I am totally noob in Linux. I searched for this on the internet, but couldn't find a satisfactory answer.

I have Windows XP on my D: partition and Vista on my C: partition. I want to install Ubuntu in D:. What should i do? Can you recommend me a good Flavour of Linux to start with? Will an installation of Ubuntu harm my Windows installation?:confused:

---

### Post by abhiroopb on 2008-07-23
Its actually quite simple.

First of all you're going to have to stop thinking about partitions as C:, D:, etc. 

Basically from what I understand you have two partitions right? And you want to remove XP and install Ubuntu, or do you want to have 3 OSes loading?

---

### Post by abhiroopb on 2008-07-23
Its actually quite simple.

First of all you're going to have to stop thinking about partitions as C:, D:, etc. 

Basically from what I understand you have two partitions right? And you want to remove XP and install Ubuntu, or do you want to have 3 OSes loading?

---

### Post by Rishi87 on 2008-07-23
I want to have 3 OSes and i have 4 partitions. C,D,E,F and 250 GB HDD.

---

### Post by philinux on 2008-07-23
First thing to do is to download the iso file for the livecd.

[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Once downloaded burn it as an image, at 4x speed, don't unpack the file.

Make sure your bios is set to boot from cdrom first.

Then boot the live cd and see if it runs on your rig.

---

### Post by Rishi87 on 2008-07-23
OK, i am going to download Ubuntu and back in a while. Thanks a lot to all of you.

---

### Post by Dutch70 on 2008-07-23
If you have been wondering about Linux and which
distribution you should try you can take this short quiz and
it will give you it's best guess.

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

Edit: well, I see you opted to Ubuntu...Good choice!

---

### Post by philinux on 2008-07-23
Forgot to say.

When the cd boots choose the menu item that is "Check cd for Defects"

Let it run it takes a while. Then it will reboot the system.

Choose Option 1 then "Try ubuntu without installing"

See if you get net access etc. It's a lot slower than a full install as it's running your pc from the cdrom and memory.

---

### Post by Rishi87 on 2008-07-23
Sorry for my weird questions here as i am a newbie. Then what to do for Linux partition? Will it affect my windows file system? I am currently downloading Ubuntu 8.04 desktop cd.

---

### Post by Dutch70 on 2008-07-23
It shouldn't affect your file system, but grub will take over your bootloader. This site may help with partitioning...
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I would just take it slow. As philinux said above after you burn the live cd, you can boot to the live cd and select "try without installing"
just to check everything out. It will run much slower from the cd than it will from your hard disk, but its worth it.

Alternatively, you can use the live cd to install ubuntu directly into windows, vista or xp(with wubi). just as you would install any other program, then it will run normally and you can also uninstall it the same way. See [http://wubi-installer.org/](http://wubi-installer.org/) and [http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))

Dutch

---

