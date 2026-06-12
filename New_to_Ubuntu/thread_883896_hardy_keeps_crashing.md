---
title: "hardy keeps crashing"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by dee7o on 2008-08-08
Specs:
HP Pavilion dv 9300
2gb ram
AMD turion64x2
Nvidia Geforce Go 6150
UBUNTU 8.04 (64 bit)



I'm almost a complete noob to linux. I installed ubuntu once before through vmware and was very happy with it. In fact I loved it. I got a new machine with vista on it but I have grown so frustrated with vista that I decided to get rid of it and go back to xp with a ubuntu hardy dual boot. I installed ubuntu without any problems but  very little works properly. The out-of-box experience is absolutely horrible. It took me ages to find the right wireless driver...but I did and now it works. Sound took ages to configure and I pretty much did it by luck. It was also a pain the butt installing compiz because it wasn't working properly...now it is. My graphics card drove me insane but now it's working (ummm...kind of :S) My remaining problems (for which I have been searching for a solution for 2 weeks) are:

1- My computer keeps freezing. I am having to do 10-15 hard reboots every day. When it freezes, all I get is a white screen with static. I can't do anything on the computer. If I am typing a document, I am always at risk of losing everything. It might have to do with my graphics card driver...i don't know. I tried the restricted drivers...no success. I tried to manually download drivers...no success. Finally, a driver through Envy worked for me. Except that while it ran compiz well....this freezing started. I get static at the welcome screen, splash screen and when I shut down as well.  Add to that, when it freezes, I have to go into ubuntu recovery and fix broken packages and xserver to get back to my operating system on anything except the lowest resolution. When I do that, it reverts back to an old driver and lo and behold compiz doesnt work anymore!!! I have no idea what to do. I can't get compiz AND everything else working at the same time.

2- I thought for a period of time that firefox might be causing my problems. So I tried to download epiphany. It downloads, except that it isn't added to my applications menu as it should be. I tried everything with that, still no solution. Anyway, I gave up on epiphany because my pc freezes regardless of whether I am on firefox or not.

I really have no idea what to do now. I love the way ubuntu is set up. Compiz looks great but what is the use if it doesn't work. And I think I'm gonna fry my hard drive if I keep doing hard reboots. This just isn't going to work. Could the reason for this be that I installed the 64 bit version? I am running out of options. If noone has any ideas could someone at least explain to be how to remove ubuntu hardy and possibly recommend another distro with better out-of-box compatibility? 

Thanks :)

---

### Post by anotherdisciple on 2008-08-08
All distros will require some tweaking... have you tried linux mint? It's based on ubuntu... so it will be familiar.... and it's got a lot of tweaking already done for you.

---

### Post by dee7o on 2008-08-08
Sorry to sound ignorant, but could u give me a quick summary as to how I can remove hardy and install linuxmint? My system has 4 partitions. Also, do u think that is the only solution to my problems or is it possible to stop this screen freeze thing. I don't mind tweaking but I am running out of ideas and I can't really tweak much on a pc that keeps crashing!! :)

---

### Post by phidia on 2008-08-08
You can try and use the open source "nv" driver in place of the "nvidia" driver to find out if the crashing is caused by that. 
Unfortunaely there are reports of bugs with Hardy and crashing or lockups seems to be an oft reported symptom. You could-because of your problems-install Gutsy there doesn't seem to be the same level of reports with that by any means.
Looking at other distros is an option too try distrowatch.com IMO opensuse and sabayon offer an excellant OS.

---

### Post by dca on 2008-08-08
I figure I'd chime in, I did have an P4 clone box that indicated it was EM64T and could handle 64-bit OS installs.  Installed Ubuntu (probably, can't remember) 7.04 on it and the same thing that you're experienced happened.  Having to reboot, constant freezing.  Could never figure out if it was a kernel issue, a particular silent running app in the background, whatever.  Finally installed the 32-bit desktop and the problems seemed to disappear.  Maybe it really wasn't 64-bit compliant, who knows?
 
The only reason why I find your instance odd is because it sounds like really new hardware that's definitely 64-bit iron...

---

### Post by phidia on 2008-08-08
> **dee7o said:**
> Sorry to sound ignorant, but could u give me a quick summary as to how I can remove hardy and install linuxmint? My system has 4 partitions. Also, do u think that is the only solution to my problems or is it possible to stop this screen freeze thing. I don't mind tweaking but I am running out of ideas and I can't really tweak much on a pc that keeps crashing!! :)

If you know the partition you have Hardy installed on all you need to do is remember that and install whatever you choose onto that partition.

---

### Post by dee7o on 2008-08-08
Is it possible to download gutsy from the ubuntu website because I tried and all I can find is 8.04 32 bit or 64 bit. And if so, how to I get rid of the ubuntu I currently have? Is there an uninstall option for hardy before I do a clean install of gutsy?

---

### Post by dca on 2008-08-08
> **phidia said:**
> You can try and use the open source "nv" driver in place of the "nvidia" driver to find out if the crashing is caused by that. 
Unfortunaely there are reports of bugs with Hardy and crashing or lockups seems to be an oft reported symptom. You could-because of your problems-install Gutsy there doesn't seem to be the same level of reports with that by any means.
Looking at other distros is an option too try distrowatch.com IMO opensuse and sabayon offer an excellant OS.

+1 on the nVidia, good point.  If you're not fed up w/ Hardy, perhaps using alternate graphics driver may help.

---

### Post by dee7o on 2008-08-08
> **dca said:**
> +1 on the nVidia, good point.  If you're not fed up w/ Hardy, perhaps using alternate graphics driver may help.

Sounds like a good idea, but I have no idea how to do it. Any suggestions? Is it something I should do through the command lines?

---

### Post by dee7o on 2008-08-08
I agree that its almost definately my graphics card. 
1- the static I get on startup, login and shut down (this happens regardless of whether compiz is on or off)
2- the freezing thing only happens with compiz which should be compatible with my geforce go 6150 except that i can't find a driver that actually works. 
3- After crashing if I do a normal reboot, I go a loooooow resoultion screen where my icons don't even fit on my desktop (and I don't have many) 
4- I've read people have similar problems running hardy on some nvidia cards. 

So now what?

---

### Post by dca on 2008-08-08
The few times I've had to mess around w/ nVidia graphics cards, I just used envy right after clean install and all updates installed of Ubuntu desktop edition. 
 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 
 
...don't ask why, I just never bothered going into the 'Add/Remove Software' under 'Applications' main menu bar and installing nVidia from there. It could've been a paranoia from not knowing which driver/module was for which generation of nVidia graphics card.

---

### Post by phidia on 2008-08-08
> My computer keeps freezing. I am having to do 10-15 hard reboots every day. When it freezes, all I get is a white screen with static. I can't do anything on the computer. If I am typing a document, I am always at risk of losing everything. It might have to do with my graphics card driver...i don't know. I tried the restricted drivers...no success. I tried to manually download drivers...no success. Finally, a driver through Envy worked for me. Except that while it ran compiz well....this freezing started.

Guess I quoted you to remind everyone helping of when you said the freezing started.
You need to uninstall all past versions of the nvidia driver I think. when you have tried to install the nvidia driver even unsuccessfully, stuff gets left in your system and that could cause or contribute to the problems your seeing. There are threads here specifically on how to uninstall past nvidia drivers-I'll insert the links if I can find them. 
The bigger issue, I think, is why hardy has had such a difficult time discovering the hardware and providing a way to enable the nvidia driver.

Added: I'll take the risk of arousing the ire of envy fans but I think the ubuntu way of enabling the driver should work or bug reports should be filed.

---

### Post by phidia on 2008-08-08
Ok post #10 at [this thread]("http://ubuntuforums.org/showthread.php?t=765411&highlight=uninstall+nvidia") gives a method that looks right for removing the old nvidia crud. Hope that helps.

---

### Post by dee7o on 2008-08-08
Ok over the last 20 mins my pc crashed 3 times. Compiz was not even running. The last time it happened, I couldn't even get back into ubuntu. It's not a hardware thing because with XP this doesn't happen. I am trying the nvidia thing one more time. Otherwise, I am going back to xp because while I like ubuntu, I treasure my hard drive considerably more

---

### Post by philinux on 2008-08-08
Install nvidia-settings from synaptic or

sudo apt-get install nvidia-settings

It turns up in system>admin.

Use it to check your driver and settings.

And you can try booting into recovery mode and when the menu appears choose xfix.

---

### Post by dee7o on 2008-08-08
lol i did a clean install of hardy. Let's see what happens now.

---

