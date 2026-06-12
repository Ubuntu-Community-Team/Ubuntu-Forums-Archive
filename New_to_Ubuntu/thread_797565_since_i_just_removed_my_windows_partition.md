---
title: "since i just removed my windows partition"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-05-17
Im solely running ubuntu, should i  do a clean re install of hardy  after resizing my partition?

---

### Post by nowin4me on 2008-05-17
Isnt a clean reinstall wiping your whole harddrive?

---

### Post by Joeb454 on 2008-05-17
Yes it is, and to the OP, if you want to then go ahead :) Just make sure you back everything up first :)

---

### Post by PatrickMoore on 2008-05-17
of course. im just wondering if its a better idea then just leaving things as is

---

### Post by heatpumpcontrol on 2008-05-17
Why reinstall? If your installation is working I would just use partition Editor to adjust the size of your partitions. Why risk the chance of having issues on the next install..? 

Just resize....

---

### Post by nowin4me on 2008-05-17
> **heatpumpcontrol said:**
> Why reinstall? If your installation is working I would just use partition Editor to adjust the size of your partitions. Why risk the chance of having issues on the next install..? 

Just resize....

Maybe s/he doesn't want windows anymore

---

### Post by SlappyPappy on 2008-05-17
I wouldn't bother. I've cloned my Gutsy from 20GB to 60GB to 120GB and each time I was going to an equal sized partition and then resizing to take advantage of the extra space. 

No problems at all.  :)

---

### Post by PatrickMoore on 2008-05-17
sounds like a plan i think ill save myself any issues and resize instead

---

### Post by Raccoon1400 on 2008-05-17
You can mess around with partitions all you want without reinstalling.

---

### Post by heatpumpcontrol on 2008-05-17
> **nowin4me said:**
> Maybe s/he doesn't want windows anymore

OK, Using Partition Editor will allow you to delete the Windows partition and allocate the empty space elsewhere as deemed necessary. 

Now you can then edit your grub to remove the Windows boot option and therefor it would no longer be displayed as an option. 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bksup
sudo gedit /boot/grub/menu.lst
```

Remove the reference to Windows or just comment them out by adding a '#' without the quotes, in front of the references to the Windows boot options.

---

### Post by heatpumpcontrol on 2008-05-17
Oh one quick note before you delete the partitions, is your Windows partition the first partition? If it is then you'll have to edit grub to tell it the new location (hda1 or sda1 or hda2 or sda2) of your linux partition. Otherwise grub will be pointing to a non-bootable location/partition.

Post your grub here and maybe we can all help before you start messing with the partitions.

```
gedit /boot/grub/menu.lst
```

This will aid you later and save you the headaches I went through when I first started with linux

---

### Post by Joeb454 on 2008-05-17
> **heatpumpcontrol said:**
> Oh one quick note before you delete the partitions, is your Windows partition the first partition? If it is then you'll have to edit grub to tell it the new location (hda1 or sda1 or hda2 or sda2) of your linux partition. Otherwise grub will be pointing to a non-bootable location/partition.

Post your grub here and maybe we can all help before you start messing with the partitions.

```
gedit /boot/grub/menu.lst
```

This will aid you later and save you the headaches I went through when I first started with linux

You will need root privileges to edit the menu.lst, so you would run ```
gksudo gedit /boot/grub/menu.lst
``` :)

---

### Post by heatpumpcontrol on 2008-05-17
> **Joeb454 said:**
> You will need root privileges to edit the menu.lst, so you would run ```
gksudo gedit /boot/grub/menu.lst
``` :)

Yes true but I just want her/him to post the grub menu for us to see so that we may help...

---

### Post by Joeb454 on 2008-05-17
If the OP has removed their Windows partition they just need to delete the Windows part :) they can always comment it out (using #) first to make sure it won't break

---

### Post by PatrickMoore on 2008-05-17
> **Joeb454 said:**
> If the OP has removed their Windows partition they just need to delete the Windows part :) they can always comment it out (using #) first to make sure it won't break

ive partitioned a cleared windows as a boot option everything is all ubuntu now...

 wishfull thinking but does anyone know why im getting little glitches when i start my computer up and shut it down i can post pictures if it helps. 

 im just really anal retentive and want everything running perfectly

---

### Post by heatpumpcontrol on 2008-05-17
post your pics if you can...

---

### Post by PatrickMoore on 2008-05-17
i know its of poor quality i had to take it with my camera. basically that flashes for a millisecond then it starts loading ubuntu...

---

### Post by heatpumpcontrol on 2008-05-17
Not sure what these lines might be but I also get some horizontal lines at boot up but I believe this might be a result of the video drivers being activated and deactivated during both processes. Some might have a better explanation but I wouldn't worry about it. It might not be what you want to see but just as long a everything else works fine during normal operation... you're OK.

---

