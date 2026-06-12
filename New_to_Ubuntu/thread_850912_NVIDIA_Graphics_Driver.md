---
title: "NVIDIA Graphics Driver"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by dkc.com on 2008-07-06
Hi friends,
I have installed Ubuntu 8 LTS on an external hard disk.
When I go to system>Administration>hardware drivers it shows that "NVIDIA Accelerated Graphics Drivers (Latest Cards)" is disabled. When I enable it, it asks for restart.  When I restart, I completely loose the display. Instead i see an off-white blank screen. So I had to reboot the system under recovery mode>xfix>resume and then it worked. I have done this for at least 5 times and without Graphic card it really looks pitiable. 
Can any body help please?

---

### Post by overdrank on 2008-07-06
> **dkc.com said:**
> Hi friends,
I have installed Ubuntu 8 LTS on an external hard disk.
When I go to system>Administration>hardware drivers it shows that "NVIDIA Accelerated Graphics Drivers (Latest Cards)" is disabled. When I enable it, it asks for restart.  When I restart, I completely loose the display. Instead i see an off-white blank screen. So I had to reboot the system under recovery mode>xfix>resume and then it worked. I have done this for at least 5 times and without Graphic card it really looks pitiable. 
Can any body help please?

Hi and what is the model of the graphics card?
Echo :)

---

### Post by bumanie on 2008-07-06
I have an 8600gt that works fine with the ubuutnu driver. What model nvidia card is it?

---

### Post by dkc.com on 2008-07-06
> **overdrank said:**
> Hi and what is the model of the graphics card?
Echo :)

Hi friend,
Thanks for the quick reply.
I think that the Graphic card is 8400 GS but not sure. How to find?

---

### Post by sdennie on 2008-07-06
It's surprising that an 8400M GS would have this problem.  Regardless, you may be able to resolve it by installing and running envyng:

```

sudo apt-get install envyng-gtk
envyng-gtk

```

---

### Post by overdrank on 2008-07-06
> **dkc.com said:**
> Hi friend,
Thanks for the quick reply.
I think that the Graphic card is 8400 GS but not sure. How to find?

And to add to vor you can use the command ```
lspci 
``` in the terminal and look for VGA and this will identify the graphics. :)

---

### Post by dkc.com on 2008-07-06
> **overdrank said:**
> And to add to vor you can use the command ```
lspci 
``` in the terminal and look for VGA and this will identify the graphics. :)
Hi Friend,
I followed the instructions and it installed but I can't see any difference in the display. After doung envy thing i also used 'lspci' and I found the following thing:


dkc@chirag-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
dkc@chirag-laptop:~$ 


does that show that my graphic card has been installed?

---

### Post by overdrank on 2008-07-06
> **dkc.com said:**
> Hi Friend,
I followed the instructions and it installed but I can't see any difference in the display. After doung envy thing i also used 'lspci' and I found the following thing:


```
dkc@chirag-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
[COLOR="Red"]01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)[/COLOR]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
dkc@chirag-laptop:~$ 
```


does that show that my graphic card has been installed?

HI and after vor commands, did envy install the graphics driver and ask you to restart your system? The command I gave just identifies your hardware. Your graphics card is the nvidia 8400

---

### Post by dkc.com on 2008-07-06
> **overdrank said:**
> HI and after vor commands, did envy install the graphics driver and ask you to restart your system? The command I gave just identifies your hardware. Your graphics card is the nvidia 8400

Hi friend,

When I typed 'envyng-gtk' it opened a program in which it showed two options for Graphic Drivers: ATI and NVIDIA. I selected NVIDIA and automatic detection. It installed some packages and asked for restart. I restarted. The only difference that I could notice is that while start up it shows a big screen containing NVIDIA logo but I can't feel any difference in the display. Is there any way to learn whether the Graphic card has been installed?

Thanks.

---

### Post by sdennie on 2008-07-06
Yes.  Try:

```

glxinfo | grep direct

```

If it says, "Yes", you have the proper drivers installed and everything should be running just fine.

---

### Post by overdrank on 2008-07-06
> **dkc.com said:**
> Hi friend,

When I typed 'envyng-gtk' it opened a program in which it showed two options for Graphic Drivers: ATI and NVIDIA. I selected NVIDIA and automatic detection. It installed some packages and asked for restart. I restarted. The only difference that I could notice is that while start up it shows a big screen containing NVIDIA logo but I can't feel any difference in the display. Is there any way to learn whether the Graphic card has been installed?

Thanks.

If you see the nvidia splash screen then your drivers are installed. Are you still experiencing the off white screen you described in your first post?
Edit to slow lol :)

---

### Post by s3a on 2008-07-06
You should now have the proprietary driver installed. I guess you can check by running a game or whatever since I think it's only proprietary drivers that have good 3d acceleration support.

---

### Post by dkc.com on 2008-07-06
> **vor said:**
> Yes.  Try:

```

glxinfo | grep direct

```

If it says, "Yes", you have the proper drivers installed and everything should be running just fine.

Hi friend,

It says yes when I typed 'glxinfo | grep direct' but the video file runs weirdly as usual. It doesn't give a proper display on the screen like windows.

thanks.

---

### Post by overdrank on 2008-07-06
> **dkc.com said:**
> Hi friend,

It says yes when I typed 'glxinfo | grep direct' but the video file runs weirdly as usual. It doesn't give a proper display on the screen like windows.

thanks.

Hi and this is not windows. You can install the nvidia settings via synaptic manager and then use them to adjust your screen. use the alt, F2 keys and the command ```
gksu nvidia-settings
```
:)

---

### Post by dkc.com on 2008-07-06
> **overdrank said:**
> Hi and this is not windows. You can install the nvidia settings via synaptic manager and then use them to adjust your screen. use the alt, F2 keys and the command ```
gksu nvidia-settings
```
:)


Hi Dear Friend,

I feel as if I hurt a hardcore linux user by comparing it to windows. If so, I am sorry. 

But this is 'Absolute Beginner Talk' and there are and there will be plenty of hardcore windows user who are trying to use Linux. I am not a geek and don't want to use linux to show off but really want to use it for my day to day purpose and video playing is one of them for which my wife wife uses the laptop quite often. If she won't get the results as good as windows, she want care to use any other OS.

When I used 'gksu nvidia-settings' it opened up a programme and certain setting things which are beyond my understanding. Although I will try to configure few things and will let you know as soon as possible.

Thanks.

---

### Post by PmDematagoda on 2008-07-06
There is no problem in talking about Windows, but if you do want to actually hold a full discussion about it then you are advised to use the Windows section in the forum to do that.

About your problem, what average FPS(Frames Per Second) does glxgears give?

---

### Post by sdennie on 2008-07-06
> **dkc.com said:**
> 
I feel as if I hurt a hardcore linux user by comparing it to windows. If so, I am sorry. 


Impossible.  We hardcore linux users are smug enough that any insults just fly right by.  :)

---

### Post by overdrank on 2008-07-06
> **dkc.com said:**
> Hi Dear Friend,

I feel as if I hurt a hardcore linux user by comparing it to windows. If so, I am sorry. 

But this is 'Absolute Beginner Talk' and there are and there will be plenty of hardcore windows user who are trying to use Linux. I am not a geek and don't want to use linux to show off but really want to use it for my day to day purpose and video playing is one of them for which my wife wife uses the laptop quite often. If she won't get the results as good as windows, she want care to use any other OS.

When I used 'gksu nvidia-settings' it opened up a programme and certain setting things which are beyond my understanding. Although I will try to configure few things and will let you know as soon as possible.

Thanks.

Hi and no you did not hurt my feelings at all. :)
I was just stating that this is not window as like using mandriva or any OS. I understand you are not a geek and may not want to learn that much about a operating system. I started with Ubuntu and dual booted with windows until I became comfortable with ubuntu and stick with it. If it is not for you or your wife then that is it no hard feelings at all. Have you install all the restricted formats and codecs for the video's?
Edit and as you see the user's vor, PmDematagoda, and myself are members of the Beginners team to help new comers to Ubuntu :)

---

### Post by dkc.com on 2008-07-06
> **vor said:**
> Impossible.  We hardcore linux users are smug enough that any insults just fly right by.  :)

Oh,

That's really cool. I hope i can be one of you but by no means I tried to insult anybody in any ways.

I think after some tweaking videos run properly but I am still not satisfied with the result in browser.

Thanks.

---

