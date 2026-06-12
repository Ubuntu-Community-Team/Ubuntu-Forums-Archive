---
title: "Grub booting error HELP!"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by deamonwalker on 2008-05-01
I recently loaded hardy heron to an external Hdd because I didn&#8217;t have the space on my laptop. When I restart the GRUB file loads and I choose to run Ubuntu or vista. They both work well. The problem is when I unplug the external drive as I do with my laptop all the time. If I restart the computer at any time the GRUB file starts loading then says GRUB error 21. Can someone please help me? This is a real nuisance.
It appears to use the GRUB as an Ubuntu bootmanager(dont really know much about Ubuntu/Linux) and when i choose vista it then runs vista bootmanager fine with the choice of vista and Ubuntu on this too. i just need a way to get rid of GRUB so i can let windows manage the booting. the GRUB must be loaded onto the external Hdd that much is clear, so it cant run properly when the external is unpluged

---

### Post by spiderbatdad on 2008-05-01
Possibly fixable in your BIOS. Look for hdd settings. Set slave to auto.

---

### Post by deamonwalker on 2008-05-01
thanks spiderbatdad,
this didnt help unfortunately because i have a laptop and dont have the option in bios to set drive options. i have made the usb harddrive last in the boot selection tho. any more help would be appreciated

---

### Post by spiderbatdad on 2008-05-01
Not sure. Wondering if your hot-plugging is working properly.
Have you tried different methods, ie. unmounting before reboot...then hotplugging, or booting with cold-plugging...the usb drive connected.

Could be problem in the hardware detection process during boot. So you would want to read the output of ```
dmesg
``` Look for errors and/or suggestions in the output for fixing the problem. These suggestion generally refer to ways to edit the kernel line in menu.lst to include some boot parameters.

---

### Post by deamonwalker on 2008-05-02
i have been reading some other forums and do you think it might be because i installed grub on the usb harddrive?cos thats what i think it did, therefore of coarse grub wouldnt be able to boot properly when the drive isnt connected. can you help me to install grub1.5 onto my internal hdd just to resolve this problem?

---

### Post by spiderbatdad on 2008-05-02
I believe you can do this just by running the live cd and selecting repair bootloader...I 'm sorry I don't have any experience in this task.

---

### Post by Xiong Chiamiov on 2008-05-02
Whether or not it will help you, [Super GRUB disk]("http://www.supergrubdisk.org/") is a very useful tool to have.

---

### Post by rodh on 2008-05-02
Try this link,  it is a great tutorial on grub




[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

