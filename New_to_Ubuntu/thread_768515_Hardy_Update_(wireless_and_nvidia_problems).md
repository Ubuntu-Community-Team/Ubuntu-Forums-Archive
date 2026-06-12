---
title: "Hardy Update (wireless and nvidia problems)"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-04-26
My plan was to update to hardy yesterday, if there were any problems I'd sort them out, if it took too much effort I'd revert back to my saved image of Gutsy.

After the update, the computer restarted. 

**First problem:**

I got an error during boot. Something along the lines of VFS filesystem error, kernel panic. And i froze there. So i reset my laptop and tried again, this time going into grub and changing the kernel from 2.6.22 (which had been set as default) to 2.6.24-16-generic (which I assumed was the new linux kernel. I have had this problem before, but it doesn't seem all that major in any case.

After boot I logged in (resolution was off) and it asked me to install the proprietary nvidia drivers. Unfortunately my wireless did not seem to work as the networks were not showing up in network manager. SO I connected it to a wired network, and installed the nvidia drivers. Restarted computer.
[B]
Second Problem[/B]

The resolution was still off but I thought that my wireless was more important to deal with first. So I went online and looked at various solutions. Basically what I discovered was that the new kernel was using a different set of drivers to that off the previous kernel and so this was causing compatibility issues. So, I decided to simply use the older kernel as a temporary method. During boot I opened up grub and used the 2.6.22-14-generic kernel. On start up the wireless worked. Of course this was only a temporary solution.

[B]
Third Problem:[/B]

The resolution was still off. So I installed nvidia-settings and tried launching it. And I got the following error:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

So I run sudo nvidia-xconfig and get something along the lines of the following:

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Configured Video Device" must have a Driver
line.

I did not know what to do, so I restarted my computer and still I got the same nvidia error. I could potentially use the nv drivers, as this gave me my native resolution (1280x800) but dual monitors did not work. So that is why nvidia-settings was essential.

As such I was completely at a loss, I tried everything over and over again. Nothing worked.

So, finally I decided to go back to gutsy. Now if these two major issues can be dealt with I can try hardy again.

Unfortunately I cannot leave hardy running and try and sort these things out (as I actually need to use my computer). However, if these issues have come up with others then perhaps solutions have also been found.

Thanks!

---

### Post by nicedude on 2008-04-26
Need more info to figure anything out. First to get wifi help you need to list your exact wifi chipset so somebody can help. If you don't know and can't figure out then list PC exact model. As for the kernel panic I don't know about that one. For your Nvidia troubles I would google "envy" go to the authors website & download the new version for hardy and install & run it. It will download from Nvidia the newest driver for your card. Ubuntu staff doesn't recomend the envy program but I found it superior for my system & allot of other people have good luck with it too.

---

### Post by ghost_ryder35 on 2008-04-26
validation error could be because the xorg.conf file is incomplete
run 
```

sudo dpkg-reconfigure xserver-xorg


```
to rebuild the configuration file, and then try 'nvidia-config' again

---

### Post by abhiroopb on 2008-04-26
Thanks,

Firstly I don't want to run envy because I have heard of problems arising out of it. Also it seems to be an "Automatix" like fix. I'd rather wait and see if the ubuntu developers can find a solution. What is strange is that it worked fine, and some weird change must have caused this problem.

My complete computer information is included in my signature, and I think my wireless card is an Intel Wireless 3945ABG

---

### Post by abhiroopb on 2008-04-26
Wrong post

---

### Post by abhiroopb on 2008-04-26
> **ghost_ryder35 said:**
> validation error could be because the xorg.conf file is incomplete
run 
```

sudo dpkg-reconfigure xserver-xorg


```
to rebuild the configuration file, and then try 'nvidia-config' again


I've heard ([http://ohioloco.ubuntuforums.org/showthread.php?t=739127&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=739127&page=2)) that this solution has basically become useless in hardy. In any case I tried this and similar things as mentioned in that thread. But yes an incomplete file does seem to be the culprit. Thanks for trying!

---

### Post by abhiroopb on 2008-05-09
Basically I'm sticking to gutsy. But is there any solution to this problem in the upcoming future?

---

### Post by maramot on 2008-05-09
> **abhiroopb said:**
> 
Second Problem[/B]

The resolution was still off but I thought that my wireless was more important to deal with first. So I went online and looked at various solutions. Basically what I discovered was that the new kernel was using a different set of drivers to that off the previous kernel and so this was causing compatibility issues. So, I decided to simply use the older kernel as a temporary method. During boot I opened up grub and used the 2.6.22-14-generic kernel. On start up the wireless worked. Of course this was only a temporary solution.

[B]
Third Problem:[/B]

The resolution was still off. So I installed nvidia-settings and tried launching it. And I got the following error:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

So I run sudo nvidia-xconfig and get something along the lines of the following:

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Device section "Configured Video Device" must have a Driver
line.

I did not know what to do, so I restarted my computer and still I got the same nvidia error. I could potentially use the nv drivers, as this gave me my native resolution (1280x800) but dual monitors did not work. So that is why nvidia-settings was essential.

As such I was completely at a loss, I tried everything over and over again. Nothing worked.

So, finally I decided to go back to gutsy. Now if these two major issues can be dealt with I can try hardy again.

Unfortunately I cannot leave hardy running and try and sort these things out (as I actually need to use my computer). However, if these issues have come up with others then perhaps solutions have also been found.

Thanks!

You got that error from nvidia-settings exactly because you reverted to the gutsy kernel version. I've been banging my head for the last two days until I found out that the kernel version was the reason for it all. I've had the same problem as you. You have to go to your menu.lst and change the kernel version to the one you reverted from: 2.6.24.16-generic Once you do this, you'll be able to simply pick the resolution you want from the nvidia-settings applet. At least for me it worked perfectly. Here's a link: [http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19)

---

### Post by abhiroopb on 2008-05-09
Ah but I think you missed my other point, the reason I used the older kernel was apparently because there were some driver updates for the newer kernel, updates which broke my wifi. So I thought I'd use the older kernel (which fixed my wifi), which was more important at the time. In any case it seems to be a case of either my wifi or my graphics!

---

### Post by maramot on 2008-05-09
Hmm, I saw you first point (about the wifi) and I was afraid it would turn out like that :( Is there really no way around it? If you can make your graphics work, try looking for other solutions for enabling your wifi driver. That's all I can think of... That intel model is popular enough, doesn't it work with ndiswrapper? What behavior do you get? Errors, IP not being assigned etc..?

Personally, I have the following problem which emerged after I installed Hardy - after I log in, it takes me about a minute to be able to open internet pages even though my wireless meter is loaded and full. I can't ping any address for the first minute or so, even though I seem to be connected to my home wireless network. I'm not sure wether this is a Hardy or a firefox issue though. Including this beta 3.5 as a browser installed by default was a *very* bad idea.

---

### Post by abhiroopb on 2008-05-09
So basically after I installed Heron, my wifi didn't work. I actually uninstalled nvidia in gutsy and then upgraded. Then I can't remember but I either tried to install nvidia or not. Basically the wifi wasn't working which was a bigger priority. And so I hunted around and for some reason the driver has been changed to something else in the newer kernel and the solution people were using was to use the older kernel.

Anyway so I don't have that much time to hunt around for a solution, but once my holiday starts I'll try again, perhaps even a clean install.

Thanks for the suggestion though, at least I know the graphics card is no problem!

---

### Post by maramot on 2008-05-10
My own wifi adapter was too new a model to be supported by Gutsy (Broadcom Corporation BCM4310 USB Controller
) so I had to download the windows driver for it and emulate it through ndiswrapper. Hardy kept that configuration so my wifi is still working, although I have to disconnect and connect once again to the wifi network every time I log in. This didn't seem to be e firefox 3.5 problem so it's either Hardy or the router causing this, but I bet on Hardy because I haven't changed any settings of the router and the other computer at home (running mac os Tiger) is has no such problems.

Try using ndiswrapper and windows drivers for your wifi card. These might work for you.

---

### Post by abhiroopb on 2008-05-10
Thanks for the help, but personally this seems like way more effort than I'm willing to put in. ACtually I don't mind putting int he effort, but the consequence of it not working, is me having to put back my backed up image! So, do you think the Ubuntu team will fix this issue? I find it strange that they took something that was fine in gutsy and then changed it!! How strange.

I don't know, I mean my gutsy is working fine (albeit without hibernation, and a few kinks i sometimes come across). Otherwise its not as though hardy (on the surface) is such a big change to gutsy. If I don't have any problems with gutsy and I DO have problems with hardy is it at all worth upgrading? Maybe I should just wait for the next release, or at least they fix the issues in hardy.

---

### Post by maramot on 2008-05-12
What have they done to the wireless support is beyound me as well. :) Ndiswrapper is the popular method and it's described in many threads and in the ubuntu howto for wireless.

Cheers!

---

### Post by abhiroopb on 2008-06-07
BUMP:

Would just like an update from those in the know/those using hardy whether the problem with the wireless card (as noted in the start of this thread) has been dealt with. It is the only thing holding me back from upgrading!

---

### Post by abhiroopb on 2008-06-14
NB:

Marking thread as solved because I have found a solution for the wireless issue, and everything else seems to be working now.

Wireless solution: [http://ubuntuforums.org/showthread.php?t=828753&highlight=hardy+nvidia+7400+wireless+intel](http://ubuntuforums.org/showthread.php?t=828753&highlight=hardy+nvidia+7400+wireless+intel)

---

