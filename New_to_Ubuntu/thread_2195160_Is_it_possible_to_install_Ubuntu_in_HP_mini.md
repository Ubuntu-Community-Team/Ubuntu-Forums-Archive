---
title: "Is it possible to install Ubuntu in HP mini"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by charitosha on 2013-12-22
Hello everyone I'm new to this forum as i'm new to ubuntu....
Recently i decided to try ubuntu to see how it is.
I'm trying to install it(12.04) in my HP Mini 210-2000(1.66 Ghz, 1Gb ram) and even to have a dual boot to choose from :-k
I did downloaded the iso file, i did make my USB bootable via unetbootin and changed the boot order, but when i try to actually install it, the display remains black with the cursor at the top left corner...

is it because it;s just 1gb of ram (should i place 2gb?) or it's just incompatible with the netbook???


Any help would be really appreciated...
P.S. i did look at the Official documantations and in the forum before posting but i didn't find anything for my...case

---

### Post by PaulW2U on 2013-12-22
I have a Samsung netbook with similar specifications. Ubuntu, Xubuntu and Lubuntu all run fine on it although Ubuntu is a little slower than the other two.

Did you download the 32-bit or 64-bit ISO?

You'll need to 32-bit version of course (i386 in the filename, not amd64).

---

### Post by charitosha on 2013-12-23
of course i downloaded the 32-bit version, and thats kinda the problem, i followed the procedure step by step...
I think for a reason (although it does sees the usb key) it doesn't run the program that is there....
In the usb should i put ubuntu in a file with a certain name??? Or should i also put some kind of a DOS-file???
I mean i don't want to have ubuntu in a windows partition as you can do with WUBI, but to install it in a different partition that windows won't see/recognize
If something is not clear or more info is needed tell me about it

---

### Post by mkmanifesto on 2013-12-23
You shouldn't have any problems installing Ubuntu 12.04 on an HP Mini. I had it installed on mine when I owned one. 

Have you tried testing the bootable USB drive on another computer just to verify it is working?

---

### Post by charitosha on 2013-12-24
my news so for...
have the same problem, after i change the boot order the display goes black with the cursor at the top left corner.
so for i have tried: ubuntu-12.04.3-desktop-i386.iso and ubuntustudio-12.04.3-dvd-i386.iso I also tried the autodownload option from LiLi. Actually when i tried to run ubuntu-12.04.3-desktop-i386 live in windows, it started normally but then it got stuck in the ubuntu loading screen. Any thoughts why whould that happen?
I did try to install it to my desktop pc to see if the usb is the problem BUT it run at the first try(when i tried it thought i had and ubuntustudio-12.04.3-dvd-i386.iso in the usb, does it matter that it was the studio version???) 
Well i'm kinda lost... any advice is really welcomed

---

### Post by grahammechanical on 2013-12-24
When we run the Ubuntu live session we should first of all get a purple screen with tow icons at the bottom of the screen. Do you get that purple screen? If so you can do this.

1) at the first purple screen press Enter
2) at the language screen select the language (default is English) and press Enter.
3) at the Try - Install Ubuntu screen press F6. A small menu will apear to the bottom right of the screen.
4) scroll down the F6 menu and select nomodeset and press Enter
5) press Esc to get back to the Try - Install Ubuntu screen.
6) Try Ubuntu should be selected so press Enter.

See if the live session loads. From the live session we also get an option to install Ubuntu. There are several options in the F6 menu. We select them in the same way. We may need to experiment with a combination of options in order to get the live session loading.

By the way, the Ubuntu flavours use the same installer. It is called ubiquity. So, if we get this kind of problem it does not go away by trying a different flavour. May I give some more advice? When it comes to installing do not tick to install third party software. That will install a proprietary video driver and that may cause problems after installation and on the first reboot. We can activate a proprietary video driver after installation using the Additional Drivers utility. And we can also install that third party software from the Ubuntu Software Centre by searching for Ubuntu Restricted Extras. I put in test installs of Ubuntu and I always do things this way. Never have a problem.

Regards.

---

### Post by charitosha on 2013-12-26
so i was able to run ubuntu live and there on the desktop was the option to install ubuntu...
 but on the second page(after i choose the language) it says that i don't have at least free 4.4gb which is not correct, i have around 100 gb free..) and it doesn't let me continue the instalation proccess from there.
 is there another way to overcome this problem or should i use this gparted partition???
 also, is space available is it possible to put more than one live program in the same USB stick/key???

P.S. the thing is that when i go to the details(in ubuntu) it does sees my hdd correct capacity

---

### Post by coffeecat on 2013-12-26
The problem with HP machines with Windows 7 is that HP has used up your full allocation of 4 primary partitions, so even if you have space on your hard drive, you cannot add any extra partitions. This is not a limitation of Ubuntu or Gparted, but of the MBR partition table. But there is a way of solving this.

With HP machines and Windows 8, you don't have the 4 primary partition limit, but you do have a UEFI BIOS and a GUID partition table which add their own complications. 

First question: Is that a Windows 7 or Windows 8 HP mini?

Second question. In the Ubuntu live session, open Gparted and take a screenshot (Alt+PrtSrn) and then post the screenshot so that we can see what your partition layout is like.

---

### Post by amjjawad on 2013-12-26
> **grahammechanical said:**
> By the way, the Ubuntu flavours use the same installer. It is called ubiquity. So, if we get this kind of problem it does not go away by trying a different flavour.

If we are talking about a graphical problem, that statement is true. If we are talking about Memory Usage, I am sure you know Xubuntu and Lubuntu both use 'less' memory than Ubuntu when it comes to Ubiquity :)

---

### Post by amjjawad on 2013-12-26
> **charitosha said:**
> Hello everyone I'm new to this forum as i'm new to ubuntu....
Recently i decided to try ubuntu to see how it is.
I'm trying to install it(12.04) in my HP Mini 210-2000(1.66 Ghz, 1Gb ram) and even to have a dual boot to choose from :-k
I did downloaded the iso file, i did make my USB bootable via unetbootin and changed the boot order, but when i try to actually install it, the display remains black with the cursor at the top left corner...

is it because it;s just 1gb of ram (should i place 2gb?) or it's just incompatible with the netbook???


Any help would be really appreciated...
P.S. i did look at the Official documantations and in the forum before posting but i didn't find anything for my...case

Hello and Welcome to Ubuntu Forums,

I have installed Xubuntu 12.04.3 on HP Mini with VIA CPU with 512MB RAM and the machine worked liked a charm.

With 1GB RAM, I strongly suggest to use different flavours either Xubuntu 12.04.3 LTS (or 13.10) or even lighter Lubuntu 13.10.

It could be a corrupted image (ISO). Have you checked: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) to the ISO you downloaded?

What version of UNetbootin are you using? I had some problems with a previous version.

While on the Live Session, what is the output of:

```
sudo lshw -C display
```

You should see something similar to:

```
*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)


```

---

### Post by kurt18947 on 2013-12-26
I have an HP Mini100 w/ 1 GB RAM. I too am dual booting Mint 16 & Lubuntu 13.10.  I did remove all partitions and created 3 new partitions - 2 ext4 & 1 swap.  Mint 16 works, Lubuntu is faster. Mine has a Broadcom wifi chip so needed an alternative network connection briefly to download the restricted Broadcom firmware.  Except for that minor glitch, it's been a smooth ride.

---

### Post by charitosha on 2013-12-26
well the thing is that i want to boot from usb and when i used gparted it only saw my usb...
anyway here is my partition layout from win7, hope it's what you asked...
i'll keep trying till it's done...  :-)

---

### Post by coffeecat on 2013-12-26
> **charitosha said:**
> well the thing is that i want to boot from usb and when i used gparted it only saw my usb...
anyway here is my partition layout from win7, hope it's what you asked...
i'll keep trying till it's done...  :-)

It's as I thought - you have four primary partitions and you can't do a thing until one of them has been deleted.

This is what I did with my HP Mini:

Made sure I had made a set of recovery DVDs with the HP utility in Windows. 
Backed up the contents of the HP_TOOLS partition.
Deleted the HP_TOOLS partition.
Shrunk the Windows C: partition from within Windows using Disk Management. You **must** use Windows to shrink your C: partition.
Used Gparted to create an extended partition in the space freed up from shrinking the C: partition. - You need to use Gparted from the Ubuntu live session for this and the next step.
Used Gparted to create ext4 and swap logical partitions in the extended partition.
Used the "Something Else" option to install Ubuntu to the logical partitions I had already created.

Since you are a beginner, do not do any of this until you are sure how to proceed. For instance, you will need advice on how big to make your Linux partitions and how to use Gparted. Ask any questions you need, and people will be able to help you.

There are other ways of doing this. For instance, you could delete the recovery partition - some people prefer this - but if you do, you **must** create a set of recovery DVDs first. Again, I suggest you do not proceed until you have explored all options and have appropriate advice.

---

### Post by charitosha on 2013-12-27
well 1st question: where is the Terminal? I mean i searched and found out that if press Ctrk+Alt+T it will open, but i couldn't found where it is by myself...

when i insert in the Terminal: sudo lshw -C display
```

description: VGA compatible controller
product: VirtualBox Graphics Adapter
vendor: InnoTek Systemberatung GmbH
physical id: 2
bus Info: pci@0000:00:02.02
version: 00
width: 32 bits
clock: 33Mhz
capabilities: vga_controler bus_master
configuration: latency=0
resources: memory:e0000000-e0ffffff

```
so is the output ok?
2nd question: how do i Copy the contents of e.g. recovery and hp_tools partitions? i also want to Copy them in a sd-card.
3rd: will 17 gb be enough space just to run ubuntu with ecplise and notepad++?


I mean if i get the 17 gb to linux, after that it would just be shrinking the Windows partition and adding to Linux, right???

---

### Post by coffeecat on 2013-12-27
@charitosha, before we go any further...

> **charitosha said:**
> 
```

product: VirtualBox Graphics Adapter

```

Have you installed Ubuntu as a guest OS in VirtualBox? That is, did you install VirtualBox in Windows and then Ubuntu in VirtualBox?

---

### Post by charitosha on 2013-12-27
well after i downloaded the iso file i burnt it -(when the procedure was over, virtualbox was in the usb)- to the USB via LinuxLive USB creator. 
So i did installed LiLi ...

---

### Post by coffeecat on 2013-12-27
That's not at all clear. Give us a step by step description of what you did with the Ubuntu ISO. Also - what exactly are you doing now to start Ubuntu? Are you starting it while Windows is running?

The reason I ask is that VirtualBox is not the way to go with only 1GB RAM.

---

### Post by charitosha on 2013-12-28
> **coffeecat said:**
> That's not at all clear. Give us a step by step description of what you did with the Ubuntu ISO. Also - what exactly are you doing now to start Ubuntu? Are you starting it while Windows is running?

The reason I ask is that VirtualBox is not the way to go with only 1GB RAM.

ok so, i downloaded the iso file. Via LinuxLive USB creator i burnt it in the USB, when the proccess was over in the USB there was virtualbox and virtualize_this_key(runs ubuntu automatically in virtualbox).
As things are right now if boot order changed(to run from the USB first) nothing happens...
So while Windows7 is running i plug in the USB and run ubuntu Live. I understand that 1gb ram is low but it's what i've got now, (hoping to upgrade it to 2gb soon...)
Hope it's detailed enough, if not please say so...

And something else i do get couple of error while running ubuntu live in Windows...
1st : it appears in the ubuntu loading screen : buffer I/O error on device zram0 logical block 63478.
after that the loading is over and i see ubuntu desktop.
2nd : it appears when everything on the ubuntu desktop has loaded and it's sort to say, good to go
it says> title: ubiquity-dm crashed with XStartupError in run():X Server exited with return code 1.

when i close that notice i'm still in ubuntu live and it's running normally.

so what's the problem(that i am not aware of), shouldn't i just free some partition space and install ubuntu?

---

### Post by coffeecat on 2013-12-28
In your first post you said that you used [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable USB from the Ubuntu ISO. Which is what I would have expected if you are using Windows. [Linux Live USB]("http://www.linuxliveusb.com/en/download") is an interesting one which I had not come across before. But with only 1GB RAM, I suggest you don't use it. As far as I can see, you are running Ubuntu inside VirtualBox inside Windows. I'm amazed it runs at all with only 1GB RAM.

I suggest you use a USB created with unetbootin in order to run a live session of Ubuntu or one of the other less memory demanding variants such as Xubuntu or Lubuntu as suggested by others. When you come to install, please bear in mind what I posted about the 4 primary partition limitation and what you can do about it. I suggest you search the forum for other threads about installing Ubuntu to a HP machine. All HP machines with Windows 7 have this 4 primary partitions already used problem, and other threads on this will give you useful information. Do not bother with threads about Windows 8 HP machines because they have UEFI BIOS with GUID partition tables which do not have the 4 primary partition limitation, but present other problems which are not relevant to your situation.

---

### Post by charitosha on 2013-12-29
I am in need of your help and advice.
I'm at the point where i want to copy the recovery and hp_tools partitions in a sd card and then delete the original partitions to free some space for ubuntu.
The problem is that althought i copied both partitions the same way only hp_tools is recognized (not even the free space of the sd card is shown) 
the program that i used is minitools partition, if anyone something better please tell...
so how i should overcome this issue???

---

### Post by coffeecat on 2013-12-29
First thing - you can't just copy the files in the recovery partition. You would need to clone the actual partition, and the app I would use for that is either Acronis or Macrium Reflect free.

Second thing. Now that you have deleted the HP_TOOLS partition, you don't need to delete the recovery partition. Now that you have only three primary partitions, you can shrink the Windows C: partition to give you enough space to create an extended partition for the Ubuntu logical partitions. Personally, I would **never** delete the recovery partition, even if I had made a set of recovery DVDs.

Don't forget to use the Windows Disk Management tool to shrink the C: partition, but use Gparted from Ubuntu to create the extended partition.

If you're worried about the wasted 103MB at the end of the drive where the HP_TOOLS partition used to be, I'd suggest you forget about it. It's a tiny amount to lose.

---

### Post by charitosha on 2013-12-31
Almost there!!! :D

I'm in the instalation procceess! 
 i made some free partition space for ubuntu, 
i choose to do the standart installation, to install ubuntu along with other OS
and as i was happy for getting through the instalation , 
it got stuck at the "welcome!" window at the bottom of which, there is a "detecting file systems" bar... 
(apologies for my poor english...)

can anyone tell me what is the issue???

---

### Post by charitosha on 2014-01-12
Is it possible to install Ubuntu in HP Mini? Yes but i did upgrated my ram to 2gb. after that it's just standart proccess if you don't mess anything...

---

