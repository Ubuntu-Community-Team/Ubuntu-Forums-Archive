---
title: "software"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by quarkhirad on 2012-06-14
I use Psim in windows to simulate all my electric circuits. Can anyone suggest a free/open source equivalent in ubuntu.

---

### Post by hansdown on 2012-06-14
Hi quarkhirad.

Try electric from synaptic or software center.

---

### Post by quarkhirad on 2012-06-14
> **hansdown said:**
> Hi quarkhirad.

Try electric from synaptic or software center.

Thanks but this looks like its more for ic and asics. I need a simple software to say model a full wave rectifier and see the output waveform with different capacitors.

---

### Post by The Cog on 2012-06-14
qucs is in the repositories: sudo apt-get install qucs
Here is their web page: [http://qucs.sourceforge.net/](http://qucs.sourceforge.net/)

There is also a free jave applet (and downloadable jar file) here: [http://www.falstad.com/circuit/index.html](http://www.falstad.com/circuit/index.html)

---

### Post by mapes12 on 2012-06-14
If you can't find an Ubu equivalent then perhaps consider installing a Virtual Machine package such as VirtualBox. Parallels also have a paid for option. Mine cost me about £7 but it is good. Then install your Windoze OS inside the VM and you can install the software that you have been used to into the Windoze OS, just as you did when you had it on a Windoze box.

The only thing to be mindful of with a VM is that it has to share RAM. In my experience Parallels does this more efficiently than some of the free apps.

EDIT: There is also Wine but I have no idea if the app you want to access is supported in Wine. Back up your stuff inc system using perhaps Remastersys and have a play around to see what works. If it all goes pear shaped your backups will get you back to where you started out.

Good luck!

Mark

---

### Post by quarkhirad on 2012-06-15
> **mapes12 said:**
> If you can't find an Ubu equivalent then perhaps consider installing a Virtual Machine package such as VirtualBox. Parallels also have a paid for option. Mine cost me about £7 but it is good. Then install your Windoze OS inside the VM and you can install the software that you have been used to into the Windoze OS, just as you did when you had it on a Windoze box.

The only thing to be mindful of with a VM is that it has to share RAM. In my experience Parallels does this more efficiently than some of the free apps.

EDIT: There is also Wine but I have no idea if the app you want to access is supported in Wine. Back up your stuff inc system using perhaps Remastersys and have a play around to see what works. If it all goes pear shaped your backups will get you back to where you started out.

Good luck!

Mark

Thanks. The trouble is that virtual box is not FREE and i need a FREE option. The secound trouble is that even if i do get a virtual box free i dont have a windows 7 cd to install windows as my laptop has come with windows 7 preinstalled. The other thing is that mathlab for linux is another NON FREE option instead of the virtual box.

---

### Post by mastablasta on 2012-06-15
oracle virtual box is free (as in free beer) but might not be free as in libre (opensource etc.)
 
you simply download it and install it. it might even be in repositories.

---

### Post by Paqman on 2012-06-15
> **mastablasta said:**
> oracle virtual box is free (as in free beer) but might not be free as in libre (opensource etc.)
 
you simply download it and install it. it might even be in repositories.

It is free (in both senses) and indeed is in the repos. What's not free (as in speech) are the extensions you need to add to get support for things like graphics acceleration and a unified mouse pointer.

---

### Post by afixane on 2012-06-15
Why not try to install PSIM on Wine?? :\

---

