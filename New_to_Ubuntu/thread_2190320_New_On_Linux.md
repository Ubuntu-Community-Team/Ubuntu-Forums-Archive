---
title: "New On Linux"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by helderctiago on 2013-11-26
Hello everyone, im a new person os this side...and i have a few questions in my mind. I have a Asus N56VZ and i would like to know if all the hardware components will work fine and perfectly (fn + ... Nvidia Graphic....Intel Graphic...) ? [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG] i have the Windows 8 and i would like to install a fresh and new Linux Ubuntu partion. But im afraid to make any mistake on MBR ( i think is this ) when later i back to windows 8 if i didn't adapt very well on linux [IMG]http://forums.linuxmint.com/images/smilies/icon_sad.gif[/IMG]...and my question is this is anything i should be concern ? For anything windows program im thinking to use the VirtualMachine to do it.
Im thinking about installing then LTS version, but when the new LTS comes do i need to re-install all over again ? : ( or i can just update it ? Im a little bit afraid about moving to a new SO, cause this is more based on commands to installs apps and configurations, which advices can you guys give it to me ? Should i dual boot with windows 8 or a fresh and new only Linux SO on laptop ? cause i know myself and if i find a tiny error or something i cant fix i will be back for windows 8 :( and i don't want :\ 
I heard that dual boot can damage our hard-drive ? :\ its true ? My first thought was install only the Linux Ubuntu and with the VM work on Windows 8 if i need anything from there...the second tought was the dual boot but like i said i will always go for the windows :( 
In case that i remove windows, and do a clean and fresh install and then i back for windows do i need to be careful with MBR or something like that ? Dunno how that works, and if anything happens it is fixeble with no problems for the hard-drive ?
Where i can change or modify or install new themes ? they use many resouces from the computer using them ? or because its Linux this is fast fast xD hehehehhe ? 

Sorry for the stupid questions but im new here :\  

Best regards,
Namoush

---

### Post by leeper69 on 2013-11-26
Hi helderctiago
  I hope this helps the easest way and the one which will not do anything to your windows 8 is to install another hard drive to your system and install ubuntu to it. the first thing to do after installing the new drive is to choose the new drive as your boot drive in bios.then start the ubuntu install and be shure to pick the new drive to install ubuntu. The next lts version of ubuntu wont be out for 6 more months if you dont want to wait you should be able to upgrade from ver 12.4 to ver 14.4.
installing ubuntu is much easer and faster than installing windows just be carfule and you will do just fine. you dont need to know how to use the terminal to install programs there are gui tools like ubuntu software center and synaptic that will do this.
I hope I answered all your questions and welcome to ubuntu linux.
ps: I have never ruind a drive and at worst have had to reinstall ubuntu to fix grub the boot loader that lets you chose whether you want to use windows or ubuntu linux.

---

### Post by electrohandyman501 on 2013-11-26
In answer to another of your questions, if you are concerned about hardware compatibility, download and burn a live boot dvd/usb and try it on your hardware to make sure it will work. Then think about your hard drive install options.
I've modified my laptop HD partitions and am dual booting with 12.10. I'm also using VMWare with my W7 install for evaluating other linux versions.

---

### Post by slooksterpsv on 2013-11-26
> I have a Asus N56VZ and i would like to know if all the hardware components will work fine and perfectly (fn + ... Nvidia Graphic....Intel Graphic...) ?

I'm not sure you may want to test that out by booting off of the live cd/dvd and testing it. The live cd just holds everything in memory, nothing is saved, and you can test out if your hardware functions correctly first.

> 
 i have the Windows 8 and i would like to install a fresh and new Linux Ubuntu partion. But im afraid to make any mistake on MBR ( i think is this ) when later i back to windows 8 if i didn't adapt very well on linux ...and my question is this is anything i should be concern ? 


Do you know if your hard drive is MBR or GPT? The difference will make this a lot smoother and simpler of an installation. If you have Windows 8 and it's UEFI it's probably GPT for the EFI partition. In Windows you can check this via diskmgmt.msc

> For anything windows program im thinking to use the VirtualMachine to do it.

You can do almost everything in Virtualization except gaming so if you're a gamer, Virtualization won't give you the frames you need to run newer games.

> Im thinking about installing then LTS version, but when the new LTS comes do i need to re-install all over again ? : ( or i can just update it ?
Usually with LTS's or any major new release you should reinstall, but you should just be able to update. Updating to the newest release has been getting better so it may just work fine. I reinstall personally.

> Im a little bit afraid about moving to a new SO, cause this is more based on commands to installs apps and configurations, which advices can you guys give it to me ? Should i dual boot with windows 8 or a fresh and new only Linux SO on laptop ? 
I heard that dual boot can damage our hard-drive ? 

Everything a typical user would need to do has a GUI. You have Software center for installing software, you have many GUI tools to help configure the system just like you need. It's very rare (and more in a support type scenario) that a standard user needs the terminal/cli/command line, but we are here to help you if you need help.

First no dual-booting won't damage your hard drive.

Personally, I say if you have UEFI and GPT, dual-boot. It is so easy cause here's pretty much what you do:
Use windows and resize your Windows 8 disk - let's say it's allocated 420GB because you may have 4-6 other partitions. Resize the one that is 420GB down to about 380GB (so 380GB for Windows 40GB for Ubuntu or however you want to set the spectrum). I usually if I need Windows more just allocate about 40GB to Ubuntu (right now I have 220GB on my Elementary OS cause I'm in it more).

> In case that i remove windows, and do a clean and fresh install and then i back for windows do i need to be careful with MBR or something like that ? Dunno how that works, and if anything happens it is fixeble with no problems for the hard-drive ?
Your recovery files are going to be on the hard drive some where so be sure you see if you can make backup DVDs or a backup drive FIRST!!! Otherwise you may have to contact acer and order a $60 set of DVDs that have the recovery stuff for your computer.

> Where i can change or modify or install new themes ? they use many resouces from the computer using them ? or because its Linux this is fast fast xD hehehehhe ?

You can change it in the Settings area I think. I don't use Ubuntu itself I use Elementary OS which is based off of Ubuntu. It doesn't use up resources really. Linux is really fast and streamlined. My computer takes about 5 min. for Windows 8.1 to boot. Linux, I'm up to go in about 30 seconds.

Finally, one last thing!

Welcome to the Ubuntu Community Forums, don't hesitate to ask questions, you can search and see if it's already been asked, but don't stress about if you ask the same question, it happens. We're here to help you how we can. This is a wonderful community, but if people start to give you problems, let me know and I can reach out to a mod.

Welcome =D

---

### Post by fantab on 2013-11-26
First of all, Dual Booting Windows and Ubuntu will NOT damage your HDD. 
Secondly, it will be good idea to dual-boot, until such time you are very comfortable using Linux/Ubuntu.
Thirdly, IMO, you should always do a fresh install of LTS... because it is just that 'clean' and 'fresh'. If you stick to LTS versions then you will be installing every 2yrs. since LTS is released every two years and supported for 5 yrs. So whenever you do an upgrade to next LTS make it a fresh install.

You need to learn a bit more about dual-booting, especially since Windows8 uses UEFI, and has other idiosyncrasies we need to understand and address before installing Ubuntu along with Windows8. The following links will get you started:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Also find out what is 'Fast Startup', 'Fast Boot', 'Secure Boot', UEFI and GPT before you go on to install Ubuntu. Linux has a learning curve, we cannot skip it.
Clarify all your doubts before you proceed. 

Good Luck.

---

### Post by helderctiago on 2013-11-27
Thanks for all the help, i will be doing the dual boot so i can test and give more experience to my self and anything that i need i can go to the other partion the Windows 8. Should i re-size the partion on the windows or i can do it when i choose the operation "install alongside with windows 8" on the linux instalation ? oh and one more thing installion will ask if i want to install the grub or anything else ? Cause just in case i want to delete the Linux partion should i be able to load the windows 8 without any problem or need to fix the mbr like use the windows 8 DVD and use the comands to fix that ? One more question, any problem if i install an app the do a grub customize ( im thinking about the Super Boot Manager )  ?  
So i can make it nice and pretty when to choose the SO :)
Ohh and if i delete the Linux this grub change will delete too ? or will stay and have to clean it with Windows 8 or something like that..
Sorry for asking this or anything stupid :(

Thanks for the help everyone :) 

best regards,

---

### Post by leeper69 on 2013-11-27
Hi helderctiago you can use the install disk to install grub over. and it is portable so you can take one with you wherever you go and boot from diferent computers. you can also help other windows users recover there files before thay reinstall
I have tryed super boot manager mostly for its abilaty to choose the default desktop aftera a newer version of ubuntu was installed after the lts version and it worked for that i havent used in a while though.

---

### Post by Val87 on 2013-11-27
To put it simply. I have installed Ubuntu on a good few machines. Even the earlier versions, all the hardware seemed to work fine. With version 13.10 everything worked perfectly. I am happy to see that more and more people are deciding to switch and stop kissing Microsofts butt. :)  It took me a while before i made a complete decision, i have been running it now for a month, and managed to play all my Windows games on it. It is becoming more and more stable with every update. Good luck exploring Linux.

---

### Post by fantab on 2013-11-27
> **helderctiago said:**
>  Should i re-size the partion on the windows or i can do it when i choose the operation "install alongside with windows 8" on the linux instalation ?
 oh and one more thing installion will ask if i want to install the grub or anything else ? Cause just in case i want to delete the Linux partion should i be able to load the windows 8 without any problem or need to fix the mbr like use the windows 8 DVD and use the comands to fix that ? 
One more question, any problem if i install an app the do a grub customize ( im thinking about the Super Boot Manager )  ?  So i can make it nice and pretty when to choose the SO :)
Ohh and if i delete the Linux this grub change will delete too ? or will stay and have to clean it with Windows 8 or something like that..

Yes you should '[Shrink the Windows8 partition]("http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/")' and make space for Ubuntu before you proceed. You should use ONLY Windows tools to manage Windows partitions and ONLY Linux tools to manage Linux partitions.
Grub will install automatically. Just make sure you boot your Ubuntu install DVD/USB in UEFI mode. See this [HOW TO]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").
No, don't use any app to customize grub. I would advice against it. Keep it simple. Grub menu screen will show for only 10secs by default, how it looks shouldn't matter. However this can be done easily without any 'customizer app'.
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
If and when you do delete Ubuntu then grub will also delete, however there will be its entries in the EFI parition you have to remove those entries later. No biggie.

Also you don't have to worry about MBR, because in all probablity you have EFI and EFI does not work from MBR.

**I hope that you've read all the information in links I have provided in my earlier post and here**. 
Don't just go ahead in your excitement and install Ubuntu; with Window8 in the picture its not as simple as it used to be if you don't understand the concepts involved.
Since you are asking about MBR, I am assuming you don't yet have an idea of what EFI booting is. Get a hang of it first. 

Try to answer the following as cheklist to see if you are ready:

Do you have UEFI boot?
Do you have an EFI parittion?
Do you have GUID partition Table [GPT] on your HDD?
Do you have 'Fast Startup' enabled in Windows 8?
Do you have 'Secure Boot' enabled in BIOS?
Do you have 'Fastboot' enabled in BIOS?
Do you have 'Intel SRT' in Bios?
Do you have 'Hybrid Graphics'?

We don't want you to get frustrated trying to install Ubuntu as a dual-boot option. It is very easy to get frustrated.

Good Luck and Regards...

---

### Post by helderctiago on 2013-11-28
> **fantab said:**
> Yes you should '[Shrink the Windows8 partition]("http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/")' and make space for Ubuntu before you proceed. You should use ONLY Windows tools to manage Windows partitions and ONLY Linux tools to manage Linux partitions.
Grub will install automatically. Just make sure you boot your Ubuntu install DVD/USB in UEFI mode. See this [HOW TO]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").
No, don't use any app to customize grub. I would advice against it. Keep it simple. Grub menu screen will show for only 10secs by default, how it looks shouldn't matter. However this can be done easily without any 'customizer app'.
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
If and when you do delete Ubuntu then grub will also delete, however there will be its entries in the EFI parition you have to remove those entries later. No biggie.

Also you don't have to worry about MBR, because in all probablity you have EFI and EFI does not work from MBR.

**I hope that you've read all the information in links I have provided in my earlier post and here**. 
Don't just go ahead in your excitement and install Ubuntu; with Window8 in the picture its not as simple as it used to be if you don't understand the concepts involved.
Since you are asking about MBR, I am assuming you don't yet have an idea of what EFI booting is. Get a hang of it first. 

Try to answer the following as cheklist to see if you are ready:

[COLOR=#000000]Do you have UEFI boot?[/COLOR]
[COLOR=#000000]Do you have an EFI parittion?[/COLOR]
[COLOR=#000000]Do you have GUID partition Table [GPT] on your HDD?[/COLOR]
[COLOR=#000000]Do you have 'Fast Startup' enabled in Windows 8?[/COLOR]
[COLOR=#000000]Do you have 'Secure Boot' enabled in BIOS?[/COLOR]
[COLOR=#000000]Do you have 'Fastboot' enabled in BIOS?[/COLOR]
[COLOR=#000000]Do you have 'Intel SRT' in Bios?[/COLOR]
[COLOR=#000000]Do you have 'Hybrid Graphics'?[/COLOR]


We don't want you to get frustrated trying to install Ubuntu as a dual-boot option. It is very easy to get frustrated.

Good Luck and Regards...

Tanks for your help and effort to trying to help me :)

I will try to answer the questions you ask :

Do you have UEFI boot?
- Yes i have the UEFI boot cause i can boot from the USB and appears the black screen with the options ( but when i try to select the first option which is the live th screen goes black and nothing happens - first problem i have )

Do you have an EFI parittion?
- I dont know.

Do you have GUID partition Table [GPT] on your HDD?
- Yes i have the fastboot enable.

Do you have 'Fast Startup' enabled in Windows 8?
- Yes i have the fastboot enable.

Do you have 'Secure Boot' enabled in BIOS?
-Yes i have the secure boot enable, don't know if i need to disable it cause im afraid i mess with anyhting or the performance of the laptop change...

Do you have 'Fastboot' enabled in BIOS?
- Yes i have the fastboot enable.

Do you have 'Intel SRT' in Bios?
- Yes i have the fastboot enable.

Do you have 'Hybrid Graphics'?
- If this means it is two graphic cards and they need to switch yeah i have and i will install bumblebee linux.

I dont know when i need to disable or enable the options, cause im afraid to mess up with the laptop and damage anything and dont know much about this stuff :( but well im here to learn :)

best regards,

---

### Post by fantab on 2013-11-28
Lets see... 

> **helderctiago said:**
> Tanks for your help and effort to trying to help me :)

I will try to answer the questions you ask :

Do you have UEFI boot?
- Yes i have the UEFI boot cause i can boot from the USB and appears the black screen with the options ( but when i try to select the first option which is the live th screen goes black and nothing happens - first problem i have )
[COLOR=#008000]This you should check in the BIOS, aka UEFI and check under BOOT, you will see something like "Boot Mode", tell us what mode it is set to.[/COLOR]

Do you have an EFI parittion?
- I dont know.
[COLOR=#008000]Look at the partitions from Windows 8, if you have 250Mb-500Mb FAT32 partition with 'boot' flag then you have an EFI partition[/COLOR]

Do you have GUID partition Table [GPT] on your HDD?
- [s]Yes i have the fastboot enable.[/s]
[COLOR=#008000]Not sure how to find out from Windows8... but if you have EFI partition then it can be confirmed that you have GPT.[/COLOR]

Do you have 'Fast Startup' enabled in Windows 8?
- [s]Yes i have the fastboot enable.[/s]
[COLOR=#008000]FastStartup is different from 'Fastboot'. FastStartup in Windows8 keeps the OS in hibernation and does not allow you to shutdown the PC, even though it appears as if you've shutdown.
You have to [**disable Faststartup**]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows8 if you want to boot another OS or run Live DVD/USB. Because technically, your PC has not shutdown, its in a advanced 'hibernation.' [/COLOR]

Do you have 'Secure Boot' enabled in BIOS?
-Yes i have the secure boot enable, don't know if i need to disable it cause im afraid i mess with anyhting or the performance of the laptop change...
[COLOR=#008000][/COLOR][COLOR=#008000]No, need to disable 'Secure Boot'. Ubuntu can install with it enabled.[/COLOR]

Do you have 'Fastboot' enabled in BIOS?
- Yes i have the fastboot enable.
[COLOR=#008000]You have to [**disable 'Fastboot'**]("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm"). (Some have reported that it can be re-enabled after Ubuntu is successfully installed). This is an Intel feature that skips some BIOS checks to allow you to boot faster... not really important. I'd rather have the BIOS run those checks.[/COLOR]

Do you have 'Intel SRT' in Bios?
-[s] Yes i have the fastboot enable.[/s]
[COLOR=#008000]If your laptop came pre-loaded with a SSD then the chances are you have In[/COLOR][COLOR=#008000]tel SRT. This 'Smart Response Technology' lets SSD to be used as a cacheing device, this speeds up Hard Disk performance. However it uses RAID and that creates problems when trying to install Ubuntu. Ubuntu won't install. You have to disable it, if you have it, in BIOS, change the SATA MODE in Bios to 'AHCI' from RAID.[/COLOR][COLOR=#008000][/COLOR]

Do you have 'Hybrid Graphics'?
- If this means it is two graphic cards and they need to switch yeah i have and i will install bumblebee linux.
[COLOR=#008000]Yes, that is correct. Until you install bumblebee or 'additional driver' for you graphics, you have use '[**NOMODESET**]("http://ubuntuforums.org/showthread.php?t=1613132")' Option during boot, both with LiveDVD/USB and the installed OS.[/COLOR] [COLOR=#008000]Nomodeset will also solve your 'black screen' issue.[/COLOR]

I dont know when i need to disable or enable the options, cause im afraid to mess up with the laptop and damage anything and dont know much about this stuff :( but well im here to learn :)

best regards,

Have you prepared a **[Windows8 REPAIR DISC]("http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html")**? this is NOT OEM 'Recovery'. Make one. NOW.

With 'nomodeset' you should be able to boot your Ubuntu DVD/USB, don't install straight away, "Try Ubuntu without installing" first. From the desktop open Terminal [ctrl + alt +t] and post the output of the following commands:

```
sudo parted -l
sudo fdisk -l
```

Good Luck...

---

### Post by helderctiago on 2013-11-28
This is what i get on BIOS MODE, im burning the Live DVD on a DVD-RW :) so i can load it later....so what should i disable ?
My laptop didn't got a SSD so im assuming i don't have the "[COLOR=#000000]*Intel SRT" on it :o *[/COLOR]

---

### Post by fantab on 2013-11-28
Do you see, under 'Boot', 'Launch CSM'? Well that is to enable 'Legacy BIOS Boot'... It means you have UEFI enabled. Good.
**Disable 'Fastboot'** for now. We can enable it later when we have a dual-boot all set up.

You probably don't have Intel SRT. However, just to check, look under 'SATA Configuration' to see what mode it is set to. I expect to see 'AHCI'. 
Also check and tell us what you see under 'Graphics Configuration'.

---

### Post by helderctiago on 2013-11-29
Ok i just checked the Sata Configuration and it is on AHCI mode like you said, i created a partion for the linux ( made it 40GB ) will try to boot ir later and give you more information.

---

### Post by helderctiago on 2013-11-29
Can't boot, same things even with that disable...don't know what's wrong :\

---

### Post by fantab on 2013-11-29
What kind of errors do you see? What happens when you try to boot... It could be that you need to change the Boot Priority to boot from 'CD/DVD Drive' or 'USB in BIOS', have you set it accordingly? Perhaps you need to "add a new boot option"...
Post a screen-shot of your HDD showing all its partitions from, Windows Disk Management.
Also post what you see under 'Graphics Configuration' in BIOS.

---

