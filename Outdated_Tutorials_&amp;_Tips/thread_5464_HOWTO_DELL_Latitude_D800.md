---
title: "HOWTO: DELL Latitude D800"
date: 2004-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by spirospr on 2004-11-18
Hardware specs :

15.4'' WSXGA
Intel Pentium M 1.7
512 MB RAM
GeForce4 4200GO
Broadcom internal modem
Dell True Mobile 802.11g (based on broadcom94306 chip)
Sigmatel audio card
Firewire
Broadcom Ethernet
Bluetooth

This “how to” is not full at the moment. It's about the solutions for problems i came up after installing Ubuntu 4.10. Expect updates since i will try to use all of my devices.

The solutions are for the devices which not worked at all or worked with problems. These are :

1.No sound card – wireless devices recognized
2.Display resolution was too low (600x800) after boot up
 
_Sound – Wireless_

The problem with sound and wireless card after searching is a bug that creates a irq conflict. The solution is adding acpi_irq_isa=7 in boot options. This is how :

[COLOR=Red]sudo nano /boot/grub/menu.lst[/COLOR]

#Find this line 

[COLOR=Red]kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda4 ro quiet splash[/COLOR]

#make it look like this

[COLOR=Red]kernel          /boot/vmlinuz-2.6.8.1-3-386 acpi_irq_isa=7 root=/dev/hda4 ro quiet splash[/COLOR]

Save it and reboot. After rebooting you should have no problems with you sound. If so check volume controls in Gnome.In order to make your wireless work you will need to install ndiswarpper because broadcom is not recognized by the kernel. This will allow us to use windows drivers for the wifi card. So do these :

#install ndiswrapper

[COLOR=Red]sudo aptget-install ndiswrapper-utils[/COLOR]

#or do it through synaptic by searching (Generally i prefere synaptic since it retrieves dependences if needed and installations are done smoothly).
#now we will install the windows drivers which must be transferred in some location of our partition

[COLOR=Red]sudo ndiswrapper -i bcmwl5.inf [/COLOR]

#if you have the  .inf file in another directory from the one that you are you will have to enter the entire path to the file. For example /home/cat/desktop/bcmwl5.inf.
#now we will activate the device

[COLOR=Red]sudo modprobe ndiswrapper[/COLOR]

#normally after that you will see the wifi indicator , in not removed from desktop , to be activated

Now you should make a network profile from Gnome 

Computer--->System Configuration--->Networking

Select “Add”  “wireless”  select “wlan0” for device make the choices that suit for your network and finish it. This should be all. Some say that after you should add a line in the file /etc/modules saying “ndiswrapper”  in order the driver to load but i did not since it loaded without it.  
 
_Resolution – Install Nvidia Drivers _ 

It is not required to install nvidia drivers to increase the resolution but one way or another i wanted the drivers to be installed. I am not going to describe how to install nvidia drivers since others have made that already . Following the instructions of the link following you should have no problems : 
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

Thank's to [COLOR=Red]sp0ck[/COLOR] i managed to achieve 1680x1050 resolution. Here is the solution he found  :

Edit /etc/X11/XF86Config-4 and scroll down to the "Monitor" section and change the values to


Section "Monitor"

    Identifier "Generic Monitor"
    HorizSync 30-107
    VertRefresh 50-185
    Option "DPMS"
    Modeline "1280x800" 159.74 1280 1296 1552 1664 800 800 815 835
    ModeLine "1680x1050" 214.51 1680 1800 1984 2288 1050 1051 1054 1103

EndSection

_Sound Buttons on keyboard_

I managed to make the volume control keys (volume up-down,mute) on my keyboard to work by doing this :

Select Computer--->Desktop Prferences--->Keyboard Shortcuts

Then select the volume up,down,mute and specify the key for the shortcut by pressing the specific keys on your keyboard. This should work just fine , as in windows. 

Well that is all for now. I hope that this will help others with same hardware as me. Sory if something is mising but please feel free to  notify me because it is a long "how to" and i might missed sth. So as i said wait updates to be done.

P.S. For those who don't have internet from their laptop they can't use "sudo apt-get" or synaptic to get the required packages, so they can find it and download it from another pc from here
[http://archive.ubuntu.com/](http://archive.ubuntu.com/)

---

### Post by choulth on 2004-11-18
Thanks, you saved my day!  \\:D/

---

### Post by herweg on 2004-11-19
This is a great howto, I would like to add that it also works on my Dell Inspiron 8200. I have one question though - up until I read this, I have been using pci=noacpi to get sound working on my machine. Is there any benefit to using acpi_irq_isa=7?

---

### Post by spirospr on 2004-11-19
[QUOTE=herweg]This is a great howto, I would like to add that it also works on my Dell Inspiron 8200. I have one question though - up until I read this, I have been using pci=noacpi to get sound working on my machine. Is there any benefit to using acpi_irq_isa=7?[/QUOTE]

I don't know because i have not test this setting , but if it is working right i don't think there is a reason for you to change your settings.
Testing around is the best thing ...

---

### Post by Jeconais on 2004-11-19
Thanks a lot - that kernel modifier has my laptop sounds working perfectly.

---

### Post by mr_ed on 2004-11-27
Sweet HOWTO!

That was totally painless!

One caveat:  Make sure that you type the correct filename.  Mine extracted as all caps, and I entered it as lowercase.  I ended up having to remove the folder, since doing an ndiswrapper remove wouldn't get rid of the stuff that installed.

---

### Post by tux61 on 2004-12-27
:D 

Thanks a lot for your howto !

---

### Post by theBlackDragon on 2005-01-11
What to do if you have an Intel PRO/Wireless 22OOBG card?

The default Ubuntu kernel includes it it seems, but it doesn't work, it doesn't create any devices, but lsmod does list the modules...

Is it advisable to install the drivers from source over the ones that Ubuntu provided? Or will that only get me into more trouble?

tia

---

### Post by Rob on 2005-01-11
I've had to adapt the boot options to get the sound working on my Dell Inspiron 8200 too, and have a suggestion for a change to your howto.

This part should be done slightly differently:-

> #Find this line 

kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda4 ro quiet splash

#make it look like this

kernel /boot/vmlinuz-2.6.8.1-3-386 acpi_irq_isa=7 root=/dev/hda4 ro quiet splash

If done as above the next time the kernel is updated (for example applying security updates using Synaptic) the acpi_irq_isa=7 bit will be removed when the menu.lst file is automatically regenerated. Instead do it as evane describes in [this thread](http://ubuntuforums.org/showthread.php?t=4258):-

> add acpi_irq_isa=7 to the default kernel options line in /boot/grub/menu.lst... for example

# kopt=root=/dev/hda7 ro acpi_irq_isa=7

then run sudo update-grub, and make sure you kernel line has that extra statement like so... kernel /vmlinuz-2.6.8.1-3-686 root=/dev/hda7 ro acpi_irq_isa=7 quiet splash

Reboot and your should issues should be resolved...

It took me a while to work out why I had to keep fixing the sound on my laptop until I realised the menu.lst file is being regenerated automatically.

Hope this helps,

Rob.

---

### Post by nico on 2005-01-16
My sound worked using the automagic rules in the grub file on a Dell Latitude 600, thanks alot for this post!!

---

### Post by sp0ck on 2005-01-30
> 
For me in order to increase the resolution , during reconfiguration of the xfree86 while selecting monitor , i choosed easy install , i selected the 17'' and finished the installation.
After that i could increase the resolution in gnome till 1400x1050 which is adequate for me at the moment. I haven' t manage to make higher resolution , but i think it has to do with upplying specific monitor specifications such as vertical and horizontal sync. This is done if selecting expert installtion and giving the information , but i can't find mine yet.


I just figured out how to increase the resolution to 1680x1050 @ 85 Hz on my D800.

Edit **/etc/X11/XF86Config-4** and scroll down to the *"Monitor"* section and change the values to

[I]
Section          "Monitor"
 [INDENT]             Identifier        "Generic Monitor"
               HorizSync        30-107
               VertRefresh    50-185
               Option            "DPMS"
               Modeline        "1280x800"      159.74 1280    1296    1552    1664 800     800 815 835
               ModeLine        "1680x1050"  214.51  1680 1800 1984 2288  1050 1051 1054 1103[/INDENT]
EndSection
[/I]

Enjoy!

---

### Post by m0bilitee on 2005-02-01
Most of the things in this post apply to the D600 (Sound, ndiswrappers, keyboard stuff). The video card is different on a D600 (non nVidia), so maybe this thread could be renamed D600/D800 and the model specific stuff noted? That would help out others as much as it helped me on the D600 I just got!

M0b

---

### Post by Lindo on 2005-02-01
I don't know if i should post here but i think you guys will show me another place to post if necessary  ;) 

I just installed ubuntu on my Dell Inspiron 8600c, which is very alike to the d800 and the d600 it also uses the broadcom drivers for wireless lan and normal lan. I tried to apply this howto to my system but it didnt work, because i need to be on the internet to do it, and since my wireless and my normal lan are not detected it won't work.
Anyone any thoughts how to get my lan to work? Help would be appreciated since im a total n00b to ubuntu  :p

---

### Post by sp0ck on 2005-02-02
The D800 laptop will hang when you close the lid, this is a kernel bug with Ubuntu. A workaround to that problem is available here

[http://www.ubuntulinux.org/support/documentation/howto/dellat](http://www.ubuntulinux.org/support/documentation/howto/dellat)

It would be nice if we can add this to the HOWTO, just to make it complete.

---

### Post by m0bilitee on 2005-02-02
Hmmm...I smell the need to develop a full  "Ubuntu Dell Laptop" HOWTO....

---

### Post by m0bilitee on 2005-02-02
[QUOTE=Lindo]I don't know if i should post here but i think you guys will show me another place to post if necessary  ;) 

I just installed ubuntu on my Dell Inspiron 8600c, which is very alike to the d800 and the d600 it also uses the broadcom drivers for wireless lan and normal lan. I tried to apply this howto to my system but it didnt work, because i need to be on the internet to do it, and since my wireless and my normal lan are not detected it won't work.
Anyone any thoughts how to get my lan to work? Help would be appreciated since im a total n00b to ubuntu  :p[/QUOTE]

Lindo - does this page help?

[http://mysite.verizon.net/negatron/linux/libranet8600.html](http://mysite.verizon.net/negatron/linux/libranet8600.html)

Apparently the 8600c uses a Broadcom chipset, but not the same as the Latitude series ones. This guy needed to recompilete the kernel with the drivers added in.  He's using Libranet which is Debian based, but I think the info might be helpful.

---

### Post by sp0ck on 2005-02-02
[QUOTE=m0bilitee]Hmmm...I smell the need to develop a full  "Ubuntu Dell Laptop" HOWTO....[/QUOTE]


Ditto! It could a generic Dell + Ubuntu HOWTO which talks about specific model numbers and the workarounds.

---

### Post by Lindo on 2005-02-02
Hey m0bilitee, i came across that same site just a while ago, i also downloaded those drivers and tried to install. 

Only thing is that i don't know how to recompile the kernel.  ](*,) 
I already looked at this guide:[http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto)  , but what i make from that is that i need to aptget something first, which i cannot do since I'm not connected to the internet by any means.

So, any thoughts on how to solve this problem ? :-s

---

### Post by Lindo on 2005-02-03
*bump*

---

### Post by m0bilitee on 2005-02-05
[QUOTE=Lindo]Hey m0bilitee, i came across that same site just a while ago, i also downloaded those drivers and tried to install. 

Only thing is that i don't know how to recompile the kernel.  ](*,) 
I already looked at this guide:[http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto)  , but what i make from that is that i need to aptget something first, which i cannot do since I'm not connected to the internet by any means.

So, any thoughts on how to solve this problem ? :-s[/QUOTE]

How did you install in the first place, CDROM?  There should be a kernel source package on that if that's how you did it from the start.

---

### Post by spirospr on 2005-02-19
[QUOTE=sp0ck]I just figured out how to increase the resolution to 1680x1050 @ 85 Hz on my D800.

Edit **/etc/X11/XF86Config-4** and scroll down to the *"Monitor"* section and change the values to

[I]
Section          "Monitor"
 [INDENT]             Identifier        "Generic Monitor"
               HorizSync        30-107
               VertRefresh    50-185
               Option            "DPMS"
               Modeline        "1280x800"      159.74 1280    1296    1552    1664 800     800 815 835
               ModeLine        "1680x1050"  214.51  1680 1800 1984 2288  1050 1051 1054 1103[/INDENT]
EndSection
[/I]

Enjoy![/QUOTE]


That worked fine. I will include it to my how to......

Thank you

---

### Post by waverate on 2005-03-04
spirospr,

I have a D800 with Ubuntu 4.10 (kernel 2.6.8.1-5-386).  I followed this post to increase the screen resolution and to get the wireless NIC working.

Screen Resolution:  Originally set to 1600x1200, it jumped to 1920x1200 after I added the Modeline lines as you described.  It looks great and it is now at the same resolution as the Windows boot.

Wireless NIC: Sound had no problem working.  I have added the acpi_irq_isa=7 and nolapic to the kernel boot and I have installed ndiswrapper.    I see the ndiswrapper loaded with lsmod (ndiswrapper 88592  0) but the Wireless Link Monitor still says that there are no wireless devices.

Any suggestions?

cheers,
  WaevRate

---

### Post by Skid on 2005-03-05
I've the same problem, however I've got an adaptec ultra pcmcia wifi card - if I restart the pcmcia services, I get unsupported card in slot x (where x is the slot that the wifi card is in, 0 or 1).

I've also had some problems regarding "append a working root=" option to your config, after updating kernel - fix - compile the IDE chipset drivers into the kernel, and NOT as modules (as the top most IDE flag is set for a module, so it's trying to first of all load the IDE module, then the chipset module)

Also, it helped removing the scsi stuff for it, and using noscsi as a boot option.

---

### Post by Emerick on 2005-05-17
[QUOTE=theBlackDragon]What to do if you have an Intel PRO/Wireless 22OOBG card?

The default Ubuntu kernel includes it it seems, but it doesn't work, it doesn't create any devices, but lsmod does list the modules...

Is it advisable to install the drivers from source over the ones that Ubuntu provided? Or will that only get me into more trouble?

tia[/QUOTE]

For Hoary, you can install the latest driver from [http://ipw2200.sf.net](http://ipw2200.sf.net) and follow their instructions.
Be aware that you need to TOTALLY delete the actual driver before install the new one.

I own an Inspiron 8000 with this wireless card, my problem is for firewire. When i plug an external firewire harddrive, a message like this one ```
May 11 21:33:00 localhost ieee1394.agent[2097]: ... no drivers for IEEE1394 product 0x/0x/0x
May 11 21:33:00 localhost ieee1394.agent[2105]: ... no drivers for IEEE1394 product 0x/0x/0x 
``` showing up in /var/log/messages.

Anyone have an answer for that, I've been digging this problem for 3 days, and no came up.

---

### Post by pravit on 2005-05-29
I have a D800 too. I tried the acpi_irq_isa=7 line but with no luck. My wireless net card is working fine, though. I get the Ubuntu sounds on startup and when opening folders and so on, but no sounds in my programs like games and Skype. Any suggestions?

---

### Post by mikitz on 2007-11-09
Just installed Gutsy on a Dell Latitude D800 and it worked great. Have to install the restricted nvidia driver and enable it afterwards.

---

### Post by alst on 2008-01-08
Anyone running D800 with 4200 Go and newer 7.10 Gutsy Gibbon?
I don't seem to be able to get higher resolutions than 1200x800 and unfortunately that's a bit low :(

I guess nowdays it's /etc/X11/xorg.conf controlling the video on a default installation.

Over and out!

---

### Post by jonmcc33 on 2008-03-20
> **alst said:**
> Anyone running D800 with 4200 Go and newer 7.10 Gutsy Gibbon?
I don't seem to be able to get higher resolutions than 1200x800 and unfortunately that's a bit low :(

I guess nowdays it's /etc/X11/xorg.conf controlling the video on a default installation.

Over and out!

Running 1920x1200 myself with a fresh install of 7.10

---

### Post by alst on 2008-03-24
I guess there are different versions of the d800?
I have 64mb on my graphic chip and it's a geforce 4200 go. And I seem unable to run such resolutions.

---

### Post by gnuneo on 2010-09-30
hi, i'm using:

"Ubuntu 10.04 LTS - the Lucid Lynx"

and there is no "/etc/X11/XF86Config-4" file anymore, it seems.

looking at alst's post, i find it is supposed to now be "etc/X11/xorg.conf" controlling the monitor resolution, and that gives:
"
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection"

--so, i was wondering where to put the extra coding in to achieve the higher resolutions? Many many thanks in advance, and i'd just like the thank the Ubuntu team for producing an absolutely first class product.

within a couple of years, why would *anyone* choose a MS product as their main platform? Higher security, easier to use (getting there), and no corporate control humming in the background.

so the only question left is: WHY is Ubuntu not standard installation in schools? And, of course, ...how can i increase my resolution on Lucid Lynx on the Dell D800? :)

---

