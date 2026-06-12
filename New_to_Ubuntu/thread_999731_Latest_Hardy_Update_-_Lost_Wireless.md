---
title: "Latest Hardy Update - Lost Wireless"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-12-02
Yesterday morning we had an update of hardy 8.04.1 It knocked out the wireless. I think I may have lost the drivet??? Any ideas on how to get it working again ? PLEASE

---

### Post by CoCoKnots on 2008-12-02
Here is more information I was able to find which may help. I running on a Sony VAIO with an Intel card. Also, you will find a screen shot of my terminal page running sudo lshw -C network. I'm not sure about what I'm doing... Trying to pick up suggestions from previous post.

---

### Post by theozzlives on 2008-12-02
wurse case senerio, you could upgrade to 8.10. I did and don't have to use the ndiswrapper anymore. I use to fight with my Brodcomm card all the time in 8.04.1.

---

### Post by CoCoKnots on 2008-12-02
Thanks, I tried that & never was able to get 'Think Or Swim' Trading software to work...(Required). Too meny conflicts. So I went to 8.04.1 I did not have this problem until yesterday morning when I ran the updates.

---

### Post by theozzlives on 2008-12-02
> **CoCoKnots said:**
> Thanks, I tried that & never was able to get 'Think Or Swim' Trading software to work...(Required). Too meny conflicts. So I went to 8.04.1 I did not have this problem until yesterday morning when I ran the updates.

Did you check to make sure your ndiswrapper and restricted drivers are okay and enabled?

---

### Post by CoCoKnots on 2008-12-02
[I]Did you check to make sure your ndiswrapper and restricted drivers are okay and enabled?
[/I]

I don't know about 'ndiswrapper'... It doesn't look like I have my restricted drivers any longer. What do I need to do to get tham back. And do I need 'ndiswrapper' ?

---

### Post by CoCoKnots on 2008-12-02
OK... I found how to get ndiswrapper from an old post I found. It's downloading now... Then what ?

---

### Post by CoCoKnots on 2008-12-02
I went to System>Admin>SynPkgMgr & did search for & installed 3 files for ndiswrapper. I then tried running:  sudo apt-get install-restricted-modules

I still can not find any restricted drivers in System>Admin>Hardware drivers. Am I looking in the incorrect location ?

---

### Post by CoCoKnots on 2008-12-02
Could someone please tell me how to get restricted drivers back to run a Pro/Wireless 3945ABG 32 bits/33 MHz connection?

---

### Post by cozmicharlie on 2008-12-02
You are looking in the right place.  Very strange that an update would knock out your restricted drivers.  You can find the linux restricted modules in Synaptic.  You may want to try reinstalling them.  Make sure the one for your kernel is installed.  You can check your kernel version in System>administration>System Monitor>System.

Hope this helps

---

### Post by CoCoKnots on 2008-12-02
Thanks Cozmicharlie, It looks like the correct one is installed. Is it possible the card/hardware itself could have somehow been damaged not related to the update? All I know was the wireless was working fine yesterday morning before & during the software update. When I shut the computer down & turned it on again a little later, I had lost the ability to connect to the internet. I am now working with a hard wire connection.

---

### Post by asgard_command on 2008-12-02
I don't know if my problem is connected but seems a big coincidence if not.
I'm running Intrepid on an Intel based Sony Vaio but with an Atheros wireless card.
Yesterday a new update came through which lost me my wireless as well. No longer have a driver showing up in Hardware Drivers.
I am able to get it back by selecting the previous kernel in grub so I assume it was something in the new kernel. Did your update include a new kernel in which case this may work for you.
I haven't been able to investigate further, but don't know how to get my driver back with the new kernel.

---

### Post by CoCoKnots on 2008-12-02
Thanks asgard_command, This sounds exactly like what happened here. How did you access the kernel & what is 'Grub'? Do you have to access this each time you reboot? ...and like you, nothing is showing up in the 'Hardware Drivers' window.

---

### Post by asgard_command on 2008-12-02
The grub is what boots the system and lets you select alternative operating systems. If you get a new kernel with an update the old ones are usually left on letting you select which one to boot from.
This list usually pops up for a few seconds during the boot process.
Have a look at the grub config file and see if it lists more than one kernel.
If I remember rightly it is in /boot/grub/menu.lst

This also has a setting for the delay that the menu is shown for at boot up check this is set to 10 seconds or something which gives you time to see the menu.

---

### Post by CoCoKnots on 2008-12-02
[I]"The grub is what boots the system and lets you select alternative operating systems. If you get a new kernel with an update the old ones are usually left on letting you select which one to boot from.
This list usually pops up for a few seconds during the boot process.
Have a look at the grub config file and see if it lists more than one kernel.
If I remember rightly it is in /boot/grub/menu.lst

This also has a setting for the delay that the menu is shown for at boot up check this is set to 10 seconds or something which gives you time to see the menu".[/I]

Ok... How do I see this stuff ?  And how do I get the system to use the old kernel instead?  I'm new to Ubuntu in the last year. 'Learning a lot (Thanks to everyone here), But still a couple of pages back from the rest.

---

### Post by CoCoKnots on 2008-12-02
[I]..."This also has a setting for the delay that the menu is shown for at boot up check this is set to 10 seconds or something which gives you time to see the menu".
[/I]

How do I access this file & re-configure it ?

---

### Post by CoCoKnots on 2008-12-02
If this problem is a result of a bug in a kernel from the last update, is there any way of un-installing the last update &/or re-installing the previous kernel ?

---

### Post by cozmicharlie on 2008-12-02
Open a terminal and type the following.
 ```
sudo gedit /boot/grub/menu.lst
```

Approx line 19 you have a line that reads "timeout".  Thier should be a number.  Whatever it is replace it with 10.  Make sure it is not commented out (i.r. it has a #).  This will give you 10 seconds when the grub boot loader is loading and you will see a list of installed kernels.  Just us the up/down arrow key to move the last kernel (they should be in order top to bottom).  It should then boot into the old kernel.

Also.  Check out these links for trouble shooting wireless.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by CoCoKnots on 2008-12-02
I found the timeout you were pointing out...

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

I changed the 3 to 10.
I also tried the two links you included. In the second link it recommended
ndiswrapper -l in the terminal window... It found nothing.

I then ran lspci -nn as outlined... Is came back with lspci command not found.???

---

### Post by CoCoKnots on 2008-12-02
I rebooted the system. The loading process now gives a 10 second count before proceeding... I still did not see anything about kernels or their order listed.

---

### Post by coolbrook on 2008-12-02
In terminal type

```
uname -a
```

and post the result here.

---

### Post by CoCoKnots on 2008-12-02
Here is the snapshot...

---

### Post by coolbrook on 2008-12-02
Search synaptic for instances of 2.6.24-22 and remove anything related to it.  When you reboot you should be back to the previous kernel version and have your wireless again.  At that point go back into synaptic and  re-install the new kernel (the objects you removed 2.6.24-22 with generic) and be sure to include the one that has restricted modules in the name. 

Ensure you also install these packages

linux-ubuntu-modules-2.6.24-22-generic
linux-generic
linux-image-generic

Reboot and try again.

---

### Post by CoCoKnots on 2008-12-02
I found what you are lookinf for... But as you can see, they were not installed. Do I just simply need to check & install this ?

---

### Post by coolbrook on 2008-12-02
Those ones is the image aren't the ones

Try a search for keywords 2.6.24-22 and generic.

---

### Post by CoCoKnots on 2008-12-02
is this the one ?

---

### Post by coolbrook on 2008-12-02
Yes that's one of them.  The rest should be in the result of your search.

---

### Post by CoCoKnots on 2008-12-02
Yes, I found more... I need to un-install all of these, correct ?

---

### Post by coolbrook on 2008-12-02
Correct.  "Mark for removal."

---

### Post by CoCoKnots on 2008-12-02
Ok... Removed all the files as marked. I then rebooted the computer but the wirless never kicked in. No light or sign of a signal. I need to take a break & pick up my son at the airport. I should be back on later. I want to thank you very much for all your efforts. Hope to talk to you again.

---

### Post by ugm6hr on 2008-12-03
[http://ubuntuforums.org/showthread.php?t=1000871](http://ubuntuforums.org/showthread.php?t=1000871)

Thread closed.

---

