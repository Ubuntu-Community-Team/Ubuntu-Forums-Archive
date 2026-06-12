---
title: "Looking to install Ubuntu on Gateway M-6750"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by TheDemonHell on 2008-07-12
I'm hoping to install Ubuntu onto my Gateway M-6750 laptop. Its full specs can be found [here]("http://support.gateway.com/s/Mobile/2008/Avalon/1015078R/1015078Rcl6.shtml") and any help would be extremely nice. I'm looking for any help to get the Wireless and the Webcam working, as well as step by step since I'm still relatively green to Linux, although I am also more then willing to go into the command line with good directions. Vista is not acceptable by any standards, and I see no reason to stay with Vista, if it was not for my girlfriend and her wanting to see me over webcam. If I remember correctly, aMSN would let me use Webcam, for I have Ubuntu on my main system (no configuring was needed, thankfully) and have only used the Terminal to install XMMS (though a walkthough) and Satanic Linux (same thing)

I will also be posting this on the Hardware and Laptops part of the forum too. Thanks for any and all help in advance.

---

### Post by kool_kat_os on 2008-07-12
test it out with the live cd....


i doubt that was your question tho...

---

### Post by TheDemonHell on 2008-07-12
Afraid it doesn't.

I've already got it installed, it's now to configure the webcam and the wireless.

I'm posting this from my desktop since the wireless isn't working out of the box.

---

### Post by A4006 on 2008-07-12
You can use NDISwrapper [http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/") to get your wireless card working with windows drivers, as for the webcam, no can do, I don't even own one.

---

### Post by TheDemonHell on 2008-07-12
How do I install the NDISwrapper? Is it in the repositories of Ubuntu?

Edit: Also, since currently I'm running Vista, I'll go looking for the XP drivers for the Wireless. I think I saw them somewhere.

---

### Post by nothingspecial on 2008-07-12
If you can get a wired connection while you sort this it will be easier.
Can yo u post the output of 

```
lspci
```

---

### Post by TheDemonHell on 2008-07-12
I'll give it a shot when I return, I need to go to work for now.

---

### Post by TheDemonHell on 2008-07-13
So I just tried my webcam under Ubuntu using Softphone and it works. 

Now to get the wireless working.

---

### Post by TheDemonHell on 2008-07-13
> **nothingspecial said:**
> If you can get a wired connection while you sort this it will be easier.
Can yo u post the output of 

```
lspci
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
ubuntu@ubuntu:~$ 

Now it's needing to be more urgent, I need this done in six hours, because Vista isn't working. Sorry for the time limit now guys.

---

### Post by nothingspecial on 2008-07-13
I`ve fixed wireless on a few ubuntu laptops but I don`t consider myself an expert.
However I`ve found this 
[http://ubuntuforums.org/showpost.php?p=4210510&postcount=6](http://ubuntuforums.org/showpost.php?p=4210510&postcount=6)

---

### Post by nothingspecial on 2008-07-13
Sorry if the card looks different in that post, don`t worry, I got the link from here - 
[http://ubuntuforums.org/showthread.php?t=843398](http://ubuntuforums.org/showthread.php?t=843398)

---

### Post by TheDemonHell on 2008-07-13
But how do I install NTSWrapper or whatever? I've yet to have that answered.

---

### Post by nothingspecial on 2008-07-13
```
sudo apt-get install ndiswrapper ndisgtk
```

ndisgtk will give you a nice easy gui to install your driver with.

---

### Post by TheDemonHell on 2008-07-13
> **nothingspecial said:**
> ```
sudo apt-get install ndiswrapper ndisgtk
```

ndisgtk will give you a nice easy gui to install your driver with.

Might be because I'm on the liveCD, but it's telling me 
ubuntu@ubuntu:~$ sudo apt-get install ndiswrapper ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
ubuntu@ubuntu:~$ 

I'm assuming a repository issue?

---

### Post by Jaded Misanthrope on 2008-07-13
Shouldn't you install Ubuntu properly before you try to make things work on it?

---

### Post by nothingspecial on 2008-07-13
Correct. As far as I know you will not be able to fix your wireless on the live cd. Even if you do you`ll have to do it again once you install.
The important point is that there is a solution. Therefore you know it will work.

It will be tricky but at least you know it can be done. 

BTW there`s nothing better than fixing your wireless card to get you started with linux.;)

---

### Post by TheDemonHell on 2008-07-13
I admit I should but right now, I'd like to see if I can get it working first. 

If it refuses to work, I will go back to trying to recover Vista. 

But thank you for nothing there Jaded.

---

### Post by nothingspecial on 2008-07-13
I`m afraid I have to go to bed now but I`ll bet there`s someone way more qualified than me that`ll help. 
Hope you sort it :)

---

### Post by TheDemonHell on 2008-07-13
OKay, thank you very much NothingSpecial. It's great to hear that it's going to work.

---

### Post by Jaded Misanthrope on 2008-07-13
> **TheDemonHell said:**
> But thank you for nothing there Jaded.

I told you that you would probably have to install Ubuntu before you try to get things working; what's wrong with that, exactly? It's hardly as if I said 'screw you moron install the god damn OS' (just for the record, I don't think that; it was just an example of what I didn't say to try and highlight that I was trying to be constructive).

---

### Post by TheDemonHell on 2008-07-13
Okay, the NDISWrapper is installed, but I don't understand what to do now. I downloaded the driver but I don't see how I install it.

---

### Post by TheDemonHell on 2008-07-13
Bumping for easy instructions I hope

---

### Post by TheDemonHell on 2008-07-13
Another selfless bump, I need easy help and am confused after installing NDISWrapper. 

Can someone help give me step-by-step? Linux is installed, it's the last thing I'm missing.

---

### Post by halitech on 2008-07-13
if you have installed ndiswrapper-common and ndisgtk, have the driver files for your wireless card, you should be able to run ndisgtk (will be under System - Administration - Windows Wireless drivers) to install your driver. Just browse to where the driver is and select the inf file.

---

### Post by TheDemonHell on 2008-07-13
The only thing is that I have no INF file, not from the zip from earlier, nor from my searching for my drivers for XP.

---

### Post by TheDemonHell on 2008-07-13
would  NDISWrapper work with a Vista driver? I might have solved my own issues if yes.

---

### Post by oilchangeguy on 2008-07-13
check out this link:
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

read the firmware installation section.
i own a m-675, and am thinking about installing mandriva one spring 2008 on it. and found this link from mandriva's site.

---

### Post by halitech on 2008-07-13
it may work with the vista driver but you need to make sure you have an INF file and a SYS file or it won't work at all. I think the 2000/XP drivers are the best option cause they've been around and seem to be more stable then vista but won't hurt to give it a try.

---

### Post by TheDemonHell on 2008-07-13
> **oilchangeguy said:**
> check out this link:
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

read the firmware installation section.
i own a m-675, and am thinking about installing mandriva one spring 2008 on it. and found this link from mandriva's site.

I'm still green and that still made no sense. I'm not using that one for my driver, I already had someone give me a zip with a different driver but with no INF file.

So, no offense my good sir, but how does this help? All this is doing is making me scratch my head, puzzled.

---

### Post by TheDemonHell on 2008-07-13
Turns out I only have exes, no INF files from my install disk. Looks like I need to keep looking.

---

### Post by oilchangeguy on 2008-07-13
> **TheDemonHell said:**
> I'm still green and that still made no sense. I'm not using that one for my driver, I already had someone give me a zip with a different driver but with no INF file.

So, no offense my good sir, but how does this help? All this is doing is making me scratch my head, puzzled.

you open a terminal and type the command shown for ubuntu.

---

### Post by TheDemonHell on 2008-07-13
so will this boxcutter (I'm guessing that's it's name) will work with my wireless?

---

### Post by TheDemonHell on 2008-07-13
the Make part of the command isn't working.

---

### Post by halitech on 2008-07-13
not sure but code you open a terminal and post back the output of
```
lsusb
```
thats a lower case L, not the number 1 just in case you aren't copying and pasting

---

### Post by TheDemonHell on 2008-07-13
paul@paul-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
paul@paul-laptop:~$

---

### Post by halitech on 2008-07-13
> **TheDemonHell said:**
> paul@paul-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. [/COLOR]
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
paul@paul-laptop:~$

it looks like you have a realtek chip in the wireless card you have. hopefully I'll have an answer and files for you shortly

---

### Post by halitech on 2008-07-13
ok, I have the 2 files you need loaded here:

[http://macdonaldfamily.ath.cx/personal/broadcom/](http://macdonaldfamily.ath.cx/personal/broadcom/)

save these 2 files somewhere that you know where they are and then we can install them

---

### Post by TheDemonHell on 2008-07-13
Sorry about being late, they are saved now.

---

### Post by halitech on 2008-07-13
ok, now go to System - Administration - Windows Wireless Drivers. From there you should get an option to browse for the file. It should then show as saved and installed

---

### Post by TheDemonHell on 2008-07-13
It says the hardware isn't present.

---

### Post by halitech on 2008-07-13
the card is still installed in the machine?

---

### Post by TheDemonHell on 2008-07-13
It's built in, yes. So it has not been removed.

---

### Post by TheDemonHell on 2008-07-14
Bumping up for more help.

---

### Post by TheDemonHell on 2008-08-04
Can anyone give me any more help?

---

### Post by cjrobertso on 2008-09-13
I didn't have time to go through all the posts so maybe this solution has all ready been tried. I have a new gateway similar to yours. Due to my issues with vista (microsoft's black sheep operating system) I have installed ubuntu 8 on my machine. I have dual partitions to permit me to run vista only when necessary. I believe your machine is the ultra-portable version of my laptop. I think the card inside is a realtek 8170. Try downloading the windows drivers from realtek's site. Then use synaptics package manager to install ndisgtk (I think thats the name for ndiswrapper. If not search for ndiswrapper). Once installed, go to system->administration->windows wireless drivers. Select the win98 driver. You could try the XP or vista driver but I didn't have much luck with either. Once you install the driver you should be able to use the network manager to access a wireless network. I can't guarantee success but only because I am not sure of which card you have.

---

### Post by BurnedKirby on 2008-11-28
> **halitech said:**
> ok, I have the 2 files you need loaded here:

[http://macdonaldfamily.ath.cx/personal/broadcom/](http://macdonaldfamily.ath.cx/personal/broadcom/)

save these 2 files somewhere that you know where they are and then we can install them

Hmm. I also have a M-6750 and would greatly appreciate it if someone hosts a link that isn't broken that has the two files.
Like the creator of this topic, my wireless and webcam isn't working. I need Ubuntu for the video editing program Cinelerra, and really would like to get this fixed.

Problems so far (for me anyway..)-

Wireless card (drivers need to be installed)
Webcam (drivers ""                     "")
Brightness Control
USB Wireless Mouse (probably no hope for fixing this driver issue because no one would be interested in this)

Well that's what I can remember so far...



I'm not sure if my version of ndiswrapper is the most recent version, but I have tried using it to install the driver and failed...


Its on about a 50gb partition, and I usually use Vista on it instead..




stephen@Solstice:~$ lsusb
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
stephen@Solstice:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. [COLOR="Red"]**Unknown device**[/COLOR] 2a08 (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
stephen@Solstice:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

stephen@Solstice:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:e5:18:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66100 (64.5 KB)  TX bytes:66100 (64.5 KB)

stephen@Solstice:~$


[Information for Gateway Laptop model M-6750]("http://support.gateway.com/s/Mobile/2008/Avalon/1015078R/1015078Rsp4.shtml")
[(more info)]("http://support.gateway.com/s/Mobile/2008/Avalon/1015078R/1015078Rnv.shtml")

---

### Post by BurnedKirby on 2008-11-28
Surely there must be someone who can solve this conundrum?.. Or will this topic be buried like the last one I made...

---

### Post by BurnedKirby on 2008-11-29
For the love of Gateway computers, someone please at least attempt to notice the existence of this topic!

---

### Post by cechmaster on 2012-02-07
Little outdated but I have the same problem as you BurnedKirby and OP.

Gateway M-6750
Ubuntu 11.10 

I installed ndiswrapper and installed the drivers for the wireless. 
Still not working. I don't think it's even showing up as a wireless card.

Could anyone help?

Thanks, 

Let me know what you need. Its a little of a pain for me getting outputs because I have no internet connection on the lapytop.

---

### Post by overdrank on 2012-02-07
Hi and please start a new thread with your issues. Thread closed.

---

