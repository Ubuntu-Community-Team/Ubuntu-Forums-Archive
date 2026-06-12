---
title: "How do i enable Desktop Effects?."
date: 2008-03-10
forum: Philippine Team
---

### Post by killer_d76 on 2008-03-10
need help mga bossing!.. how do i enable my desktop effects para ma-enable ko po yung cube sa laptop ko!..

yung laptop ko po ay neo empriva 520.. salamat po!

---

### Post by loell on 2008-03-10
try to know your video card, if its capable of running desktop effects, 
look up the name in **System** menu --> **Administration**--> **Screens and Graphics**--> in the **Card** tab.

---

### Post by killer_d76 on 2008-03-10
thanks loell!. i'll try that a soon as i get home, and i'll post the result as well! ;)

---

### Post by wersdaluv on 2008-03-11
Kung kaya, System->Preferences->Appearance->Visual Effects Tab. :)

---

### Post by SunnyRabbiera on 2008-03-11
hopefully you have good specs.

---

### Post by killer_d76 on 2008-03-12
thanks for the reply guys.. okey here's what i found out, i need to open windows xp for me to find this one out.. i got "Mobile Intel (R) 945GM Express Chipset Family" graphic card on my laptop.. is this capable of handling such graphics like enabling the "cube"? if so how? thanks

---

### Post by loell on 2008-03-12
it seems it can run compiz, so have you tried what wersdaluv suggested?

if it generates an error, you might have to edit your xorg.conf to use an intel driver.

do tell us what happens when you enable it.

---

### Post by killer_d76 on 2008-03-12
yes loell, i have tried what wersdaluv have suggested,i went to system> preferences> appearance> visual effect tab and i tried all the choices still no good  "Desktop Effects could not be disabled" pa din.. pano i-e-edit yung xorg.conf? thanks

---

### Post by loell on 2008-03-12
basically, you'll have to edit xorg.conf by ie( ```
sudo nano /etx/X11/xorg.conf
``` and edit the text from there.

anyhow, do this in the console ```
cat /etc/X11/xorg.conf
```
copy paste the output here.

and lets see if it needs editing.

---

### Post by bharadwaj on 2008-03-12
> **killer_d76 said:**
> need help mga bossing!.. how do i enable my desktop effects para ma-enable ko po yung cube sa laptop ko!..

yung laptop ko po ay neo empriva 520.. salamat po!

which language is that? Isn't this forum strictly tony for English?

Anyway as far as I understand from the thread try this link it is very easy one...

[http://www.arsgeek.com/?p=1313](http://www.arsgeek.com/?p=1313)

---

### Post by loell on 2008-03-12
> **bharadwaj said:**
> which language is that? Isn't this forum strictly tony for English?


hi, you are in the ubuntu philippine loco forum, we use both Tagalog/filipino and english.

---

### Post by killer_d76 on 2008-03-12
bharadwaj, thanks for that helpful link... ;) the language we use here are tagalog/filipino which is our native language and english!.

loell, i followed what you have said and here is the result..

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection


-- thanks

---

### Post by loell on 2008-03-12
first, backup your xorg.conf

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup 
```

then edit xorg.conf by

```
sudo gedit /etc/X11/xorg.conf 
```

in the device section , replace it with, or copy and paste this

> 
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection


then save it. and restart your laptop.


if for some reason this will fail ie(X has failed), you'll be in the command line only, so you'll have to restore your previous xorg.conf

```
sudo cp /etc/X11/xorg.conf.backup  /etc/X11/xorg.conf
```

then just restart.

---

### Post by dodimar on 2008-03-12
bharadwaj, apologies for the confusion.. welcome to Ubuntu **Philippines** forums...

ragarding sa Desktop effects,, hehe,, wala pa akong alam dyan..

---

### Post by killer_d76 on 2008-03-12
hi loell, just tried what you have suggested, and after restarting my laptop, i got a black screen but it has given me a chance to configure it back to a viewable screen.. :(

---

### Post by killer_d76 on 2008-03-13
after a few search on the net, i come up with this site: 

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

and this has something to do with my intel video card driver.. i was able to download the latest version in .tar, and i don't know how to install it.

---

### Post by loell on 2008-03-13
hindi yan driver, bios tool yan,  i'm not sure if you really need it, but maybe worth a try,  or maybe not.

---

### Post by killer_d76 on 2008-03-13
i tried it and now i'm not able to open my synaptic manager :( (see other thread)...

---

### Post by loell on 2008-03-13
oh my, :) what are you doing? ;)  I don't know how putting beryl sources for fiesty in gutsy will help achieve desktop effects on your intel card.

I just hope all will be fine, when you install something.

can you do a ```
lspci
```
copy and paste the output here.

---

### Post by killer_d76 on 2008-03-13
..actually the beryl did get me to jump into Linux!.. here you go..

arvin@arvin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
arvin@arvin-laptop:~$

---

### Post by killer_d76 on 2008-03-13
though everytime i try codes given to me.. i pray hard hoping that i won't brick my laptop!

---

### Post by loell on 2008-03-13
in order to run beryl and compiz-fusion, you must sort out your video driver first, so even if you try to install beryl now it actually won't run.

 currently your using vesa driver for your video card which is a fallback as ubuntu did not use the intel driver for your video card, have you notice  ubuntu is slower and XP is snappier in your laptop?

I'm puzzled why gutsy didn't use the intel driver for your laptop

look at this [http://math.dartmouth.edu/~sarunas/X60sGutsy.html]("http://math.dartmouth.edu/~sarunas/X60sGutsy.html")

desktop effects is being automatically enabled  and it uses the same intel video card as your laptop. 

this needs further reading, maybe i can find some time later tonight. 

can you look through XP and look at the name of the display? and the maximum resolution in xp for the display.

oh, if your in doubt of the cli commands that people gives you that may cause havoc on your system, i suggest search and read about this commands.  it will make you at ease on what to execute and what not to.

---

### Post by pmcastillo on 2008-03-13
Guys, meron na ba kayong nakita effect na pagnagcu-CUBE may FIRE effect sa paligid? May idea kayo paano iyon?

Tapos meron pa akong nakita yung mga Programs/Windows... nakalutang sa Cube...

---

### Post by killer_d76 on 2008-03-13
thank you so much for the help loell, i was not able to install Gutsy on my laptop at first and i need to type in pcia=off (if i remember it right) for the laptop to be able to install ubuntu properly, and now everytime i reboot my laptop i see this message that i need to reboot my laptop with pnpbios=off :confused: what does that mean?

---

### Post by killer_d76 on 2008-03-13
hi loell, i've looked through XP, is this the one you're asking for? (see attached pic)

---

### Post by loell on 2008-03-13
> **killer_d76 said:**
> thank you so much for the help loell, i was not able to install Gutsy on my laptop at first and i need to type in pcia=off (if i remember it right) for the laptop to be able to install ubuntu properly, and now everytime i reboot my laptop i see this message that i need to reboot my laptop with pnpbios=off :confused: what does that mean?

ah i see, this may explain why this did not detect your intel video card, you put **acpi=off** 

can you do, ```
cat /boot/grub/menu.lst
``` paste the output here, i wanna see the boot parameters youre using.

---

### Post by killer_d76 on 2008-03-13
thanks loell, i'll try that later.. ;)

---

### Post by killer_d76 on 2008-03-14
hi loell.. here's the boot grub list you wish to see.. thanks in advance ;)



arvin@arvin-laptop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=13d6574c-c66a-4f0c-b1e5-166f07200c9a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi=off

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=13d6574c-c66a-4f0c-b1e5-166f07200c9a ro quiet splash acpi=off
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=13d6574c-c66a-4f0c-b1e5-166f07200c9a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

arvin@arvin-laptop:~$

---

### Post by loell on 2008-03-14
backup your menu.lst , ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup 
```

next edit it

```
sudo gedit /boot/grub/menu.lst
```

copy and paste this at the end

```

title Testing Ubuntu 7.10, kernel with acpi ON
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=13d6574c-c66a-4f0c-b1e5-166f07200c9a ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

save, then restart your laptop and then choose the last item in your boot menu. see if theres an error.

 I also took the initiative to ask **NEO**, if theres an updated bios  version for 520gx and they said they have and they can update it in there service center.  

it might be worth  updating it  , as newer bios firmware is essential to boot the kernel properly.

---

### Post by killer_d76 on 2008-03-14
hi loell, thanks for all the help, i have tried the codes that you have provided but still it can't  seem to enable the desktop effect, anyways, i'll pay a visit to their service center and have its bios updated.. their service center is just located at 4th Floor CYBERZONE @ the SM MEGAMALL.. i'll keep posted thanks for your help ;) :KS:KS:KS

---

### Post by killer_d76 on 2008-03-14
hi loell, i just noticed one thing.. looking at the codes you gave to me.. 

title Testing Ubuntu 7.10, kernel with [COLOR="Red"]acpi ON[/COLOR]
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=13d6574c-c66a-4f0c-b1e5-166f07200c9a ro quiet splash [COLOR="Red"]acpi=off[/COLOR]
initrd /boot/initrd.img-2.6.22-14-generic
quiet

is that supposed to be off or on?.. thanks

---

### Post by loell on 2008-03-14
when you don't declare **acpi=off,** acpi will be enabled automatically, so no need of declaring it as **acpi=on**.

---

### Post by killer_d76 on 2008-03-16
hi loell, i haven't had my laptop bios updated yet, after holyweek i'll be able to pay a visit to the service center, out of curiosity i tried changing the acpi=off to acpi=on on the code that you have given me, when i restart the laptop it didn't open Ubuntu!, it only shows the ubuntu word during start up and the orange progress bar, as soon as the progress bar begins to fill in, it will shutdown and go back to option wherein i can choose which OS i wish to run to.. just like the first time when i was trying to install Ubuntu on my laptop.. and whe i changed acpi=on again.. i was able to open Ubuntu!.

---

### Post by pmcastillo on 2008-03-19
> **pmcastillo said:**
> Guys, meron na ba kayong nakita effect na pagnagcu-CUBE may FIRE effect sa paligid? May idea kayo paano iyon?

Tapos meron pa akong nakita yung mga Programs/Windows... nakalutang sa Cube...

Finally, napalutang ko na yung windows, at saka may fiery-effect na... ^_^

[img]http://img341.imageshack.us/img341/2961/screenshotbl6.png[/img]

---

### Post by killer_d76 on 2008-04-13
hi guys.. i was able to have my laptop bios updated at NEO Service Center at Mega Mall last thursday (great service! ;) thanks), but unfortunately, the errors are still there (bios bugs) and i still can't activate desktop effect :(.

---

### Post by Drakkor on 2008-04-14
Sorry to butt in here,but I have the same basic question as the op, but maybe at a different point. I have gotten compiz-fusion to work on other ubuntu editions,so I know my video card can handle it. Had the rotation cube,and skydomes,and fire paint,etc. But now with Hardy, I have enabled visual effects,and have wobbly windows,but it seems on this screen,there was a "settings" tab on the bottom to configure cube,skydomes, firepaint,etc. So now I don't see how to get the cube !
:confused:

---

### Post by wersdaluv on 2008-04-14
> **Drakkor said:**
> Sorry to butt in here,but I have the same basic question as the op, but maybe at a different point. I have gotten compiz-fusion to work on other ubuntu editions,so I know my video card can handle it. Had the rotation cube,and skydomes,and fire paint,etc. But now with Hardy, I have enabled visual effects,and have wobbly windows,but it seems on this screen,there was a "settings" tab on the bottom to configure cube,skydomes, firepaint,etc. So now I don't see how to get the cube !
:confused:

You have to use compizconfig-settings-manager

---

### Post by Drakkor on 2008-04-14
Thanks,guys, got it working again !! :)
I couldn't remember the compizconfig-settings-manager  :)

---

### Post by killer_d76 on 2008-04-15
good to hear that you were able to make it work since day 1.. sigh.. i found this nice disro (puppy linux) that can be fused with compiz, will this solve my problem?.. i like ubuntu a lot, but it seems that my laptop don't, and do you think changing distro will make this do the cube thing?

---

### Post by Drakkor on 2008-04-15
Sorry,never used puppy linux,  maybe see if they have a forum,or support. It is cool though,lol !  :)

---

### Post by killer_d76 on 2008-04-15
**drool**  sigh.. aside from the fact that Ubuntu is free and have great support.. this cube thing is what made me decide to jump into the Linux world.. but i got frustrated because i was not able to make this work on my laptop.. i come to a point where in i would like to sell my laptop and buy a new one that is compatible with Ubuntu ,but, because my son, my wife and even my 3yrs old daughter is already comfortable using this distro, and this distro is really great, i have to ditch it and have to try a different distro hoping that i could make the cube thing to work. so i decided to keep it the laptop for its sentimental value :) ..  i was able to log-in on Linux Puppy forum and looks like it has a great support as well, but having same color (am not a racist though) and true blooded "pinoy" to chat with is great, specially to Loell who had been very helpfull with my issues here... sigh

---

### Post by loell on 2008-04-16
ahh, sigh.. I  feel your frustration, an excitement that is rather short lived by a hardware issue.  been there too ;).  i've read that you'll b trying puppy? yeah puppy is a good one too.. :)

---

### Post by killer_d76 on 2008-04-17
i've tried puppy last night.. and to say the least.. i'm impressed! :KS :KS :KS.. in terms of speed! :guitar: astig!.. to think i just boot from the dvd where i burned Puppy!.. compiz was possible.. but it looks like it's a long way to get to it!.. 

by the way, i was able to make ubuntu boot properly with acpi=on now!.. hhmmm.. looks like there is hope for me to enable "cube" to work for this laptop! (i was able to make the "cube effect" to work.. but on Windows XP! :lolflag:    )

---

### Post by Drakkor on 2008-04-18
Go killer !  It seems you have the "right stuff",lol   
Good luck !  :)

---

### Post by killer_d76 on 2008-04-19
...hhhmm i was able to make compiz to work on my laptop when i used Puppy :confused:, there must be something wrong that i have done during installation that makes compiz not to work on my laptop, or is it on Neo laptop only?, my friends laptop (also a NEO laptop) , compiz is not working on his laptop as well.. even desktop effect! :confused:

---

### Post by killer_d76 on 2008-04-26
i tried running 8.04 on CD and to my surprise.. "desktop effect is enabled!" and all the effects are working properly!, which was my first issue with "gutsy"!.. now my question is "how do i uninstall/remove gutsy and fresh install "8.04" without affecting my wifes "window$" :confused:

---

### Post by mobster on 2008-04-27
Killer... Install hardy the way you install gusty in that way you will still have the windows operating system and a dual boot.

Guys have you tried installing Emerald Theme Manager in Hardy? i can't run it properly what seem's to be the problem :(

---

### Post by killer_d76 on 2008-04-27
i did tried that already but what's happening is that hardy don't want to erase gutsy and i will end up with triple boot laptop (window$, gutsy and hardy).. although i have an option to manually do the partition but i don't know which one to delete?..

---

### Post by fmontserrat on 2008-04-27
> **killer_d76 said:**
> i did tried that already but what's happening is that hardy don't want to erase gutsy and i will end up with triple boot laptop (window$, gutsy and hardy).. although i have an option to manually do the partition but i don't know which one to delete?..

Have you tried formating your EXT3 partition? This is what I remembered doing with my laptop since I previously installed Gutsy on this partition:

1. In the "Prepare Disk Space" screen, select "Manual".
2. In the "Prepare Partitions" screen, select and edit the EXT3 partition where Gutsy is installed (mine is /dev/sda6/). Remember: NTSF is for XP, FAT32 is for your documents (if you have a separate partition for it), and SWAP is your swap file.
3. On editing the EXT3 partition, choose "ext3 file system" (or something close to that), check the "Format" box and mound point to "/". The "/" is your root partition.

That should do the trick. Make sure you backup your files just in case. The last thing you want to do is delete everything your hard drive. Good luck!

---

### Post by killer_d76 on 2008-04-27
WWWOOOHHHOOOO!!!!!.... i'm sooo happy!!!.. i was able to clean install 8.04 without deleting my wife's window$!!!.. what i did was i go to GPartition and delete gutsy there!.. then i install hardy and boom!.. gutsy out.. hardy in!.. check this out!

[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/Screenshot-Desktop.png[/IMG]

---

### Post by raxso on 2008-04-28
way to go killer_d76 .... :)

---

### Post by killer_d76 on 2008-05-20
i find "cube effect" very helpful  when i'm doing a lot of things on my laptop, and my son wish to have the same effect on his Windows XP.. wish granted!.. look what i have done!... hehehe


[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/3dXP.png[/IMG]




[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/3DXP2sideview.png[/IMG]

---

### Post by pendletone on 2008-05-20
slick! :)

---

### Post by killer_d76 on 2008-05-20
and here's a screenshot of my 8.04 desktop wiht AWN dock!

[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/Screenshot2.png[/IMG]

---

### Post by killer_d76 on 2008-05-20
[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/Screenshot1.png[/IMG]

---

### Post by jepong on 2008-05-20
ingit ako! astig mga desktop nyo!!!

Anyway para sa mga newbie... I found this site you can get a script to test if Compiz will work sa machine mo or sa current setup mo.  

[http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")

---

### Post by killer_d76 on 2008-05-21
here's the software i used this one is better (Windows XP).. but it messed up the function keys on my laptop! :)


[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/3Ddesktop.png[/IMG]

---

### Post by killer_d76 on 2008-05-21
check out my Windows Boot logo screen hehehe... Pirated Edition!

[IMG]http://i254.photobucket.com/albums/hh110/arvin_domingo/3832.jpg[/IMG]

---

