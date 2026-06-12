---
title: "HOWTO: Double Clock Speed Problem"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-10-13
This is a HOWTO about a problem which can be very annoying and which affects mainly the computers with AMD64 processor (but not only) with some motherboards (e.g. my motherboard: MSI RS480). If you notice that the mouse pointer freezes randomly and everything goes slow then you might be affected by the &#8220;Double Clock Speed&#8221; problem.

Make sure this is your problem:

open:  Applications &#8211; System Tools - "System Monitor" (from the menu in GNOME). If you  have only KDE (then maybe you're using Kubuntu) you should install System Monitor by using Synaptic (as I've noticed &#8220;KSysguard&#8221; in KDE doesn't detect the problem). Click on &#8220;Resources&#8221;: you will see  &#8220;CPU1&#8221;: and the percentage of usage of your processor. If the percentage is high (try this without any programs running), i.e. something like 50% or more then you have this problem.

Another test: play an mp3 in Totem (or another app). If it goes too fast then you have this problem

[COLOR="Red"]UBUNTU 64bit SECTION[/COLOR]

NOTE: this trick works on 64bit systems ONLY (if you want to use Ubuntu 32bit you should look at the end of the page or you will have to patch your kernel, something which will not be dealt in this HOWTO).

I had this problem and I solved it thanks to NickB's help, so all the credits go to him. Thanks again Nick.

Alberto

[You need a kernel 2.6.12.x or higher (and a 64 bit Ubuntu system of course).
The one which comes with Ubuntu Breezy is ok.]
 
1) Launch &#8220;Terminal&#8221; (or &#8220;Konsole&#8221;) (the command line) and prompt:
sudo gedit /boot/grub/menu.lst
(or if you use KDE put kate instead of gedit, or nano if you haven't them, which is unlikely)

look for these lines:

## ## Start Default Options ## ## default kernel options ## default kernel options for automagic boot options ## If you want special options for specific kernels use kopt_x_y_z ## where x.y.z is kernel version. Minor versions can be omitted. ## e.g. kopt=root=/dev/hda1 ro # kopt=root=/dev/hda2 ro console=tty0 [COLOR=Red]no_timer_check [/COLOR]

Just add  [COLOR=Red]no_timer_check[/COLOR] in the kopt line (exactly where you see it in the example above, LEAVE THE REST OF YOUR FILE UNTOUCHED)

3) Save the file and restart your computer (otherwise the trick might not work)

4) After you have restarted your computer open &#8220;Terminal&#8221; (or Konsole) and prompt:

sudo update-grub

5) restart your computer again


Enjoy!

--------------------------------------------------------------------------------------------------------------------------------
[COLOR=Red]UBUNTU 32BIT SECTION[/COLOR]

This trick doesn't work for everyone (it depends on your hardware). For this reason I suggest you to try it on an Ubuntu Livecd


1) 

a) [COLOR="Red"]If you haven't installed Ubuntu 32 bit yet...
[/COLOR]
The only way to find out without installing Ubuntu 32bit is to use an Ubuntu (32-bit) LIVECD and to try to prompt one (and ONLY 1 PER TIME) of the following options at boot:

1) noapic nolapic
OR
2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll
OR
6) noapic acpi=noirq nolapic


If you don't know how to do it follow these steps:
Boot the Ubuntu live CD
You will see a screen with the Ubuntu logo and the word "boot:" at the bottom of the page (if you don't do anything for several seconds the Livecd will go ahead and you won't be able to type anything)
type (the words will appear beside "root:") "Live + the boot option" (e.g. "Live noapic nolapic") and press Enter

Then the livecd should work as usual.

[COLOR="Blue"]OTHERWISE[/COLOR]

b) [COLOR="Red"]If you have installed Ubuntu...[/COLOR]
If you have installed Ubuntu and you want to see if it works for you:

Turn on your computer and keep pressing "ESC" until you get to the GRUB menu.

Select your kernel with your keyboard arrows (DO NOT PRESS ENTER) and Press "e".
Then you will see 3 lines:
```
root (hd0,0)
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash
initrd	/boot/initrd.img-2.6.12-10-k7
```

Select the line which begins with the word "kernel" and press "e" to edit it.

Add one [ONLY ONE i.e. only 1) or only 2) ] of the following things at the end of the line:

1) noapic nolapic
so that it will look like this:
```
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapic
```
OR
2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll
OR
6) noapic acpi=off
OR
7) noapic acpi=noirq nolapic
OR
8 ) clock=pmtmr notsc
OR
9) notsc

Then get off the text field and press "b" to boot the kernel.

See if it works. 
If Ubuntu DOESN'T boot, it hangs or you can't use your internet connection just reboot and follow the instructions again but try with option 2) or 3), 4), etc. until you solve your problem.

When you find the boot options which work for you [ 1), 2) or 3), etc. ] you have to set them permanently (because the options you have jsut set will only last until you reboot).

Follow the first part of the guide (the one about Ubuntu 64 bit) and put the options which work for you (e.g. "noapic nolapic") instead of "no_timer_check".

Enjoy!

Alberto

---

### Post by tseliot on 2005-12-27
Hey guys, I have updated the guide with a new instruction (which solved the problem on my father's computer).
It's for Ubuntu 32bit. Now noapic won't make your computer hang!


Check it out!

---

### Post by poofyhairguy on 2005-12-27
[QUOTE=tseliot]Hey guys, I have updated the guide with a new instruction (which solved the problem on my father's computer).
It's for Ubuntu 32bit. Now noapic won't make your computer hang!


Check it out![/QUOTE]


Thanks. After reading your guide I feel better! I thought my computer was just unstable with Ubuntu!

---

### Post by tseliot on 2005-12-27
[QUOTE=poofyhairguy]Thanks. After reading your guide I feel better! I thought my computer was just unstable with Ubuntu![/QUOTE]
I'm glad it helped you :)

---

### Post by cdhotfire on 2005-12-27
Seems, Ive seen this before. Anyhow, ill post here also.  For me the only thing that works is, noapic apci=off. With AMD64 cpu and running 32 bit Ubuntu.

---

### Post by duhriddler on 2006-01-09
I've tried every tip listed here, and none of them work completely.
"noapic nolapic": Crashed before it finished booting
"noapic acpi=noirq": Fixed the clock speed problem, but broke my internet connection. "eth0 not ready" or some error like it.
"noapic apci=off": Fixed the clock speed problem, but broke my internet connection. "eth0 not ready" or some error like it.
"no_timer_check": Did absolutely nothing. I knew that it wouldn't work, but I had to try anyway.

My computer:
HP a1130n
The only additions are a eVGA nVidia GeForce 5500 graphics card, a Logitech MX518 mouse, and a 60 Gb hard drive on which Kubuntu 5.10 resides. Here are the base specs, if it helps.
[http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&os=228&product=483902&lang=en&cc=us&docname=c00388382](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&os=228&product=483902&lang=en&cc=us&docname=c00388382)

I must admit that I'm a Linux newbie, but I am absolutely sure that I followed all of the steps as they were listed. So, am I going to be stuck at double speed forever?

---

### Post by tseliot on 2006-01-10
[QUOTE=duhriddler]I've tried every tip listed here, and none of them work completely.
"noapic nolapic": Crashed before it finished booting
"noapic acpi=noirq": Fixed the clock speed problem, but broke my internet connection. "eth0 not ready" or some error like it.
"noapic apci=off": Fixed the clock speed problem, but broke my internet connection. "eth0 not ready" or some error like it.
"no_timer_check": Did absolutely nothing. I knew that it wouldn't work, but I had to try anyway.

My computer:
HP a1130n
The only additions are a eVGA nVidia GeForce 5500 graphics card, a Logitech MX518 mouse, and a 60 Gb hard drive on which Kubuntu 5.10 resides. Here are the base specs, if it helps.
[http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&os=228&product=483902&lang=en&cc=us&docname=c00388382](http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&os=228&product=483902&lang=en&cc=us&docname=c00388382)

I must admit that I'm a Linux newbie, but I am absolutely sure that I followed all of the steps as they were listed. So, am I going to be stuck at double speed forever?[/QUOTE]
My father's computer has an MSI 7093 motherboard and I solved its problem with "noapic acpi=noirq" and the internet (ethernet) connection works.

"noapic nolapic" makes the computer hang at boot.

My father's computer is a Compaq presario but you know Compaq and HP are almost the same thing (I think HP owns Compaq, I mght be wrong though).
I'm currently using the latest BIOS and it solved a bug which made the entire computer freeze in Linux. Unfortunately currently there's no bios available for your computer at the moment.

Another thing you should do from the BIOS is to set the preferred graphic card (select PCI-E instead of PCI) otherwise you might have some problems.


By the way which version of Ubuntu are you using, 32bit(x86) or 64bit (AMD64)?

---

### Post by duhriddler on 2006-01-10
I'm using Kubuntu 32-bit version 5.10. I was trying out the 64-bit version, but there were some programs that didn't work in it because it was 64-bit. Also, I heard it was a little on the buggy side. I already have the latest BIOS installed, so that shouldn't be an issue. My graphics card is PCI, so setting it to PCI-E probably isn't a good idea... So basically I'm stuck playing games twice as fast and having it be 10:00 PM at 6:00 PM.

---

### Post by tseliot on 2006-01-10
[QUOTE=duhriddler]I'm using Kubuntu 32-bit version 5.10. I was trying out the 64-bit version, but there were some programs that didn't work in it because it was 64-bit. Also, I heard it was a little on the buggy side. I already have the latest BIOS installed, so that shouldn't be an issue. My graphics card is PCI, so setting it to PCI-E probably isn't a good idea... So basically I'm stuck playing games twice as fast and having it be 10:00 PM at 6:00 PM.[/QUOTE]
Sorry, maybe I didn't read your post too carefully.

1) How can you use a Geforce 5500 if your motherboard hasn't got an AGP slot???

Have a look at the motherboard's specs:[http://www.msicomputer.com/product/p_spec.asp?model=RS480M2-IL&class=mb]("http://www.msicomputer.com/product/p_spec.asp?model=RS480M2-IL&class=mb")

Maybe you have another motherboard :confused: 

2) Try this instead of the boot parameters in the guide (i.e. noapic nolapi, etc.): 
```
notsc
```

And if it doesn't work try this:
```
clock=pmtmr notsc
```

3) I have noticed you mispelled a boot parameter:
It's noapic acpi=off (and not "noapic apci=off")


Tell me if one of the parameters suggested above works

---

### Post by duhriddler on 2006-01-10
1) [http://www.newegg.com/Product/Product.asp?Item=N82E16814130255](http://www.newegg.com/Product/Product.asp?Item=N82E16814130255)
2) Tried both, both left me at a blinking _ . I also tried the "noapic nolapi" thing again and wrote down the error messages on the screen after the "OK, booting kernel...":
[4294671.514000] BIOS bug, local APIC #0 not detected!...
[4294671.566000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0

Perhaps you can get more from them than I can...
3) I wrote it down correctly on a sticky note, but I cut/pasted a misspelled version of it. Oh well, no biggie.

---

### Post by tseliot on 2006-01-11
[QUOTE=duhriddler]1) [http://www.newegg.com/Product/Product.asp?Item=N82E16814130255](http://www.newegg.com/Product/Product.asp?Item=N82E16814130255)
2) Tried both, both left me at a blinking _ . I also tried the "noapic nolapi" thing again and wrote down the error messages on the screen after the "OK, booting kernel...":
[4294671.514000] BIOS bug, local APIC #0 not detected!...
[4294671.566000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0

Perhaps you can get more from them than I can...
3) I wrote it down correctly on a sticky note, but I cut/pasted a misspelled version of it. Oh well, no biggie.[/QUOTE]
1) Ok , try these options:
```
noapictimer
```

OR

```
noapictimer irqpoll
```

2) If the options above do not work you can use the 64bit version of Ubuntu (AMD64) and use "no_timer_check" which will work for sure.

3) If you don't like Ubuntu 64bit you can try PCLinuxOS which is 32bit but doesn't seem to be affected by this bug (it uses noapic nolapic by default but it doesn't hang).
Another OS you could try is OpenSuse

---

### Post by duhriddler on 2006-01-11
Yes! "noapictimer irqpoll" worked! Thanks for your help, and sorry to bother you.

---

### Post by tseliot on 2006-01-11
[QUOTE=duhriddler]Yes! "noapictimer irqpoll" worked! Thanks for your help, and sorry to bother you.[/QUOTE]
Ok, I'll add it to the guide then.

---

### Post by David Valentine on 2006-01-12
"noapictimer irqpoll" also worked for me--I had tried all the other suggestions to no avail.  I'm running Breezy 32 bit (K7) on an MSI RS480 with an AMD Sempron 64-bit CPU.  Thanks for all your help in squashing this rather nasty bug!

---

### Post by tseliot on 2006-01-13
[QUOTE=David Valentine]"noapictimer irqpoll" also worked for me--I had tried all the other suggestions to no avail.  I'm running Breezy 32 bit (K7) on an MSI RS480 with an AMD Sempron 64-bit CPU.  Thanks for all your help in squashing this rather nasty bug![/QUOTE]
Thanks for reporting. Yes, it's a nasty bug.

---

### Post by ammiel on 2006-01-15
hey  noapictimer irqpoll worrks best by not going crazy like.. 60% of the time.. maybe less, is there anything else i could do?  Thanks a lot! please help..


- Mikeeeeee(((((((sssssseee wwwhhhhatttt     iiiii      mmmmeeeeeeaaaaaaannn        ;;;;;;;))

---

### Post by tseliot on 2006-01-16
[QUOTE=ammiel]hey  noapictimer irqpoll worrks best by not going crazy like.. 60% of the time.. maybe less, is there anything else i could do?  Thanks a lot! please help..


- Mikeeeeee(((((((sssssseee wwwhhhhatttt     iiiii      mmmmeeeeeeaaaaaaannn        ;;;;;;;))[/QUOTE]
did you try:
```
noapic nolapic
```
OR
```
noapic acpi=noirq
```

What are the results with those options?

---

### Post by ammiel on 2006-01-16
i have, they all delay the problem but not too well, I've tried everything in this thread and noapictimer irqpoll and noapictimer work the best but it still comes and goes

---

### Post by bulldog5 on 2006-01-17
Just thought I'd post my results for anyone with similar hardware...

HP a1250n
ATI XPress chipset
AMD Athlon 64 X2 3800+
ATI X800 XL
32-bit Ubuntu 5.10 with kernel 2.6.12-10-k7-smp

I tried every combination of solutions listed in this thread, and the only one that works is "noapic acpi=noirq"

Hope this helps!

---

### Post by ammiel on 2006-01-17
iiiii        hhhhhaaaaaaaaaatttttttteeeeeee       tttttthhhhhhhhhiiiiiiiiiissss        bbuuuggggggggggggg!!!!!!!!!!!!!!!!!!!!!

---

### Post by tseliot on 2006-01-17
[QUOTE=ammiel]iiiii        hhhhhaaaaaaaaaatttttttteeeeeee       tttttthhhhhhhhhiiiiiiiiiissss        bbuuuggggggggggggg!!!!!!!!!!!!!!!!!!!!![/QUOTE]
The repeated keys and therefore repeated letters... I know it's part of the bug.

Don't you worry, I'll find another workaround to your problem. 
I know how annyoing that problem can be.

---

### Post by ammiel on 2006-01-17
Thanks a lot man, I owe you, you seem the only one in world tackling the problem.

- Mike

---

### Post by revmouse on 2006-01-19
I have a HP Pavilion zv6233nr series that was affected by this bug. HP Support released a BIOS patch that resolved this issue for me. 

There is also an open bug on the Linux kernel bugzilla for this issue.
[http://bugzilla.kernel.org/show_bug.cgi?id=3927]("http://bugzilla.kernel.org/show_bug.cgi?id=3927")

Before the BIOS patch, the only fix that would work for me was appending disable_timer_pin_1 to my kernel boot options. Now that I've applied the BIOS patch, Linux works fine without any boot options.

---

### Post by tseliot on 2006-01-19
[QUOTE=ammiel]Thanks a lot man, I owe you, you seem the only one in world tackling the problem.

- Mike[/QUOTE]
As Revmouse said, a BIOS update might help you. If it doesn't solve the problem it is likely that the computer won't freeze (or lose the internet connection) with the boot parameters of my guide any more (that's what happened to my father's computer).

---

### Post by ammiel on 2006-01-19
Nope I checked I have Award BIOS v 6.00 and the latest version is 6.  And my system doesnt hang or my internet connection.... I'm putting all these parameters on the boot line is it possible i messed up and put them in the wrong place?

---

### Post by tseliot on 2006-01-20
[QUOTE=ammiel]Nope I checked I have Award BIOS v 6.00 and the latest version is 6.  And my system doesnt hang or my internet connection.... I'm putting all these parameters on the boot line is it possible i messed up and put them in the wrong place?[/QUOTE]
Could you try PCLinuxOS and see if you have the same problem there?

---

### Post by sfabel on 2006-01-20
I have a HP Pavillon t3818.de here and there is a BIOS patch. How can I apply it without having to install Windows again?

Thanks,
Stephan

---

### Post by tseliot on 2006-01-20
[QUOTE=sfabel]I have a HP Pavillon t3818.de here and there is a BIOS patch. How can I apply it without having to install Windows again?

Thanks,
Stephan[/QUOTE]
Perhaps you can use a windows bootdisk but I don't know what kind of patch it is. Can you post the link to this patch?

---

### Post by danish_demon on 2006-01-20
when i go into grub and press 'e' on the kernel version i get a bunch of options: root, boot, and a few others.  which one do i select (by pressing 'e') to add the "noapic nolapic"?  do i still use the kernel version XXX-9 when i have 10 installed?

thanks,
a noob

---

### Post by tseliot on 2006-01-20
[QUOTE=danish_demon]when i go into grub and press 'e' on the kernel version i get a bunch of options: root, boot, and a few others.  which one do i select (by pressing 'e') to add the "noapic nolapic"?  do i still use the kernel version XXX-9 when i have 10 installed?

thanks,
a noob[/QUOTE]
The longest line, you can't miss it. It begins with kernel /boot/vmlinuz- or something like that.

---

### Post by danish_demon on 2006-01-20
[QUOTE=tseliot]The longest line, you can't miss it. It begins with kernel /boot/vmlinuz- or something like that.[/QUOTE]

alright, i made it to step five (rebooting after sudo update-grub) and now my system appears to have screwed up.  when it is booting up, at the "loading modules" section, it gives two errors: "usb 5-1: device not accepting address 4, error -110" and the same error but with address 5.  then it hangs at "starting hotplug system..."

what's going on here?

---

### Post by tseliot on 2006-01-20
[QUOTE=danish_demon]alright, i made it to step five (rebooting after sudo update-grub) and now my system appears to have screwed up.  when it is booting up, at the "loading modules" section, it gives two errors: "usb 5-1: device not accepting address 4, error -110" and the same error but with address 5.  then it hangs at "starting hotplug system..."

what's going on here?[/QUOTE]
1) Try to disable USB legacy from your BIOS
2) If it doesn't solve the problem, follow this part of the guide: "b) If you have installed Ubuntu..." and try the other boot options  (other than "noapic nolapic") such as "noapic acpi=noirq" OR "noapictimer irqpoll".

---

### Post by danish_demon on 2006-01-20
[QUOTE=tseliot]1) Try to disable USB legacy from your BIOS
2) If it doesn't solve the problem, follow this part of the guide: "b) If you have installed Ubuntu..." and try the other boot options  (other than "noapic nolapic") such as "noapic acpi=noirq" OR "noapictimer irqpoll".[/QUOTE]

couldn't figure out how to disable usb from bios, and neither of those two other options worked.  this was working fine until after the update-grub thing.  any other ideas?  how can i get to that file i altered in the previous step and change it back?

edit: is usb emulation the same thing as usb legacy? cuz i saw an option in the bios to disable that.

edit: tried in recovery mode, and when it got to starting hotplug subsystem it started giving out a bunch of azt timeout errors.

edit: never mind, i just reinstalled ubuntu and will leave that stupid clock problem alone

---

### Post by tseliot on 2006-01-21
[QUOTE=danish_demon]couldn't figure out how to disable usb from bios, and neither of those two other options worked.  this was working fine until after the update-grub thing.  any other ideas?  how can i get to that file i altered in the previous step and change it back?[/QUOTE]
You can remove the boot option from the GRUB menu as soon as you turn on your computer (this removal won't be permanent but you will lose it on next reboot). This is described in the following part of the guide:
[QUOTE=]b) If you have installed Ubuntu...
If you have installed Ubuntu and you want to see if it works for you:
as soon as you turn on your computer after the bios you will see a the word "GRUB" etc. press ESC until it gets you to Grub boot menu and select kernel 2.6.12-9 (Breezy's default kernel) from the list and press "e" to edit the line and add:
noapic nolapic

then get off the text field and press "b" to boot the kernel.

2) If it works then follow the first part of the guide (form point 1 to point 5) and put "noapic nolapic" instead of "no_timer_check"

OR
If your computer hangs when you use "noapic" you might want to try these other instructions (instead of noapic nolapic):

noapic acpi=noirq

OR

noapictimer irqpoll[/QUOTE]

Then after you have booted successfully you can modify the file menu.lst in order to make your choice of boot option permanent.

[QUOTE=danish_demon]edit: is usb emulation the same thing as usb legacy? cuz i saw an option in the bios to disable that.[/QUOTE]
Just try it.

---

### Post by ammiel on 2006-01-23
[QUOTE=tseliot]Could you try PCLinuxOS and see if you have the same problem there?[/QUOTE]

I haven't tried it under PCLinuxOS specifically, but under other distros on the new kernel i have the same exact problem.

---

### Post by tseliot on 2006-01-24
[QUOTE=ammiel]I haven't tried it under PCLinuxOS specifically, but under other distros on the new kernel i have the same exact problem.[/QUOTE]
I said that because PCLinuxOS solved the problem for me.

---

### Post by fitzman49 on 2006-01-24
To anyone that can help,

I just bought a Compaq Presario with a AMD Sempron 3200+ processor and integrated LAN and threw Ubuntu on.  My problem is after i got everything up and running that my clock is running twice as fast as it should.  I have read the how to that tseliot has written and tried: noapic nolapic, no_timer_check, noapic acip=noirq, eveything in this forum and other forums including the 64 bit instructions but when these all are used they dont let my integrated LAN to work.  I was just wondering if there is any other possible way to get my lan to work wihile slowing down the clock.

Please im desperate!!!!!!!!!!!

---

### Post by tseliot on 2006-01-25
[QUOTE=fitzman49]To anyone that can help,

I just bought a Compaq Presario with a AMD Sempron 3200+ processor and integrated LAN and threw Ubuntu on.  My problem is after i got everything up and running that my clock is running twice as fast as it should.  I have read the how to that tseliot has written and tried: noapic nolapic, no_timer_check, noapic acip=noirq, eveything in this forum and other forums including the 64 bit instructions but when these all are used they dont let my integrated LAN to work.  I was just wondering if there is any other possible way to get my lan to work wihile slowing down the clock.

Please im desperate!!!!!!!!!!![/QUOTE]
I know it's an annoying bug. I think you should:
1) update your BIOS (by Compaq) bacause it might remove the problem with you LAN when using my boot options.
2) If the BIOS update doesn't solve the problem, Try PCLinuxOS, which doesn't seem to be affected by this problem.

---

### Post by fitzman49 on 2006-01-25
[QUOTE=tseliot]I know it's an annoying bug. I think you should:
1) update your BIOS (by Compaq) bacause it might remove the problem with you LAN when using my boot options.
2) If the BIOS update doesn't solve the problem, Try PCLinuxOS, which doesn't seem to be affected by this problem.[/QUOTE]

Tried to find some way to update the BIOS but doesnt seem to have any on the horrible compaq site.  Do you think that if i bought a PCI nic card and used that instead of my integrated nic would sove the problem?  Im fairly new to ubuntu so im just guessing here.

---

### Post by tseliot on 2006-01-25
[QUOTE=fitzman49]Tried to find some way to update the BIOS but doesnt seem to have any on the horrible compaq site.  Do you think that if i bought a PCI nic card and used that instead of my integrated nic would sove the problem?  Im fairly new to ubuntu so im just guessing here.[/QUOTE]
I really don't know if it would work (I've never tried it).

You could install Ubuntu 64bit and use the "no_timer_check" boot option which shouldn't touch your card.

Or, if you want a 32 bit system use PCLinuxOS.

At least until I find a secure way to solve the problem (maybe with a kernel patch I found)

---

### Post by noigeaR on 2006-01-25
an easy fix for problems with the clock running too fast is to **disable the spread spectrum option** in the bios!

---

### Post by fitzman49 on 2006-01-25
[QUOTE=tseliot]I really don't know if it would work (I've never tried it).

You could install Ubuntu 64bit and use the "no_timer_check" boot option which shouldn't touch your card.

Or, if you want a 32 bit system use PCLinuxOS.

At least until I find a secure way to solve the problem (maybe with a kernel patch I found)[/QUOTE]

im such an idiot...i didnt read the "whole" posting and i ended up fixing it by putting in "noapictimer irqpoll".  i thank you for your help tseliot and applaud your efforts in helping me and everyone else out with this problem.

---

### Post by kryptondog on 2006-01-27
tseliot, you're a god!  I have the same set up as Fitzman and I was just about to throw in the towel until I tried noapictimer irqpoll.  Thank you so much!  With that taken care of, every single aspect of Ubuntu is working perfectly for me now.  I'm happy :cool:

---

### Post by mdmarmer on 2006-01-27
It depends on the board but HP (and possibly other vendors) have BIOS updates (flash) which help some of these problems ... Check the vendor's site.

Mike

---

### Post by ammiel on 2006-01-29
I burned PCLinuxOS today and not sure if it gives me the speed problem, however the CD install does!!

It keeps crashing during install :(

---

### Post by tseliot on 2006-01-30
[QUOTE=ammiel]I burned PCLinuxOS today and not sure if it gives me the speed problem, however the CD install does!!

It keeps crashing during install :([/QUOTE]
Sorry, pal. I'll figure something out :-k .

---

### Post by beerorkid on 2006-02-01
after a post that led me here, it is all good.  YOU ROCK!!

I might not be the best reader of instructions, but I was confused on where to add the options.  I kept on adding them on the boot line instead of the kernel line.

I rebooted so many times with different boot options that the thing had to do the "30" check.

maybe dumb down the main post to tell peeps exactly where to add the test entries?

Heck i am embarresed on the fact that I did not edit the correct line, others might as well.

shamefully yours,
beerorkid.

---

### Post by tseliot on 2006-02-01
[QUOTE=beerorkid]maybe dumb down the main post to tell peeps exactly where to add the test entries?

Heck i am embarresed on the fact that I did not edit the correct line, others might as well.

shamefully yours,
beerorkid.[/QUOTE]
You're absolutely right. The guide is not clear enough. I haven't had the time to fix it because I was studying for an exam.

Thanks for your feedback.

EDIT: Guide UPDATED!

---

### Post by Schrollini on 2006-02-03
I thought I would toss another data point at you.

I just got a Compaq Presario SR1730Z, with an Athlon 3500+, running 5.10 i386.  It suffered from this clock doubling problem, but the "noapictimer irqpoll" option solved it.

Also, I noticed that the clock problem was correlated with processor throttling: if the clock was running double speed, the processor stayed pegged at full speed instead of throttling back like it should.  Additionally, some of the other options did clear up the clock problem at the expense of screwing up the network interface.  I don't know if this info will help someone squash this bug for good or not.

Thanks for the HOWTO.

---

### Post by beerorkid on 2006-02-03
hmmmm...  kind of odd.  By messing the network interface did you mean completely disables it, or slows it down?

I noticed that my internet seems much slower after using the "noapic nolapic", and nvivia drivers (thanks again tselliot).  It seems it buffers? or takes a while to access the NIC.  I might try another option than "noapic nolapic"

---

### Post by tseliot on 2006-02-03
[QUOTE=beerorkid]hmmmm...  kind of odd.  By messing the network interface did you mean completely disables it, or slows it down?

I noticed that my internet seems much slower after using the "noapic nolapic", and nvivia drivers (thanks again tselliot).  It seems it buffers? or takes a while to access the NIC.  I might try another option than "noapic nolapic"[/QUOTE]
"noapic nolapic" can disable (COMPLETELY) your ethernet card but I doubt it can slow down the connection.

Instead if you don't solve the problem (with the options I provide) of the Double clock speed your internet connection will go half of its normal speed.

---

### Post by beerorkid on 2006-02-03
Thanks.

I am wondering if anybody knows what is causing this to happen though (the double clock speed issue)

Might it be caused by certian motherboards or chipsets?  I know mine is made by asus for HP, although you see no mention for it on the asus site.

It is almost working good enough for me.  I am soooooooooo happy that I have my main computer using linux.  I would hope that dapper will have this bug fixed.  heck I might even give it a try now.

---

### Post by tseliot on 2006-02-03
[QUOTE=beerorkid]Thanks.

I am wondering if anybody knows what is causing this to happen though (the double clock speed issue)

Might it be caused by certian motherboards or chipsets?  I know mine is made by asus for HP, although you see no mention for it on the asus site.

It is almost working good enough for me.  I am soooooooooo happy that I have my main computer using linux.  I would hope that dapper will have this bug fixed.  heck I might even give it a try now.[/QUOTE]
Unfortunately it's a kernel bug. Only some AMD64 motherboards are affected by the problem. Installing Dapper won't solve the problem.

This means that every time you install Ubuntu or any other distro you'll have to use the boot options I suggest in my guide.

BTW if you have problems with your connection you might try the other boot options in the guide (instead of "noapic nolapic").

---

### Post by Schrollini on 2006-02-04
[QUOTE=beerorkid]hmmmm...  kind of odd.  By messing the network interface did you mean completely disables it, or slows it down?
[/QUOTE]

The network connection was slowed down significantly, altough it would still work.  Pings of my DSL box (modem? router? What's the correct name of that doohickey?) would take 1-2 seconds, as opposed to the 1-2 milliseconds they take now.

But, as I said, the "noapictimer irqpoll" option solved both problems.

---

### Post by beerorkid on 2006-02-04
sweeeeeeeeet

that did it.  Thanks for the help.

---

### Post by tseliot on 2006-02-04
the Boot Options 6 and 7 have been added to the guide thanks to the help of other users.

Your feedback is appreciated

---

### Post by paxjapan on 2006-02-17
hello world
this week i was looking at my replies and i was thinking of what went wrong with this computer my friend recently change my mother board power supply and this was all used/ also he instaled   
everything in double/ clients,burners,cd,ext /some time i am loading my modules and my synchronizing clock to ntp,ubuntulinux,org (failed) /can it be a double clock speed problem????

also when i am looking at files on my tv it freeze and also i can*t look at 2 files one after an other /

it looks like when i removed one burner and removed a cliente things got better/before i was on amule and linux manually/i am thingking of removing my extras and to get back on what i had before??????:-k 

i know i am slow on this but i have learnd to take my time and i thank-you all for your help
paxjapan

---

### Post by kenweill on 2006-02-17
I used
noapic apic=off

Well, it works. Or, is the second parameter wrong? Should it be acpi=off instead of apic=off?

Im not sure if its wrong but it works.

---

### Post by tseliot on 2006-02-18
[QUOTE=kenweill]I used
noapic apic=off

Well, it works. Or, is the second parameter wrong? Should it be acpi=off instead of apic=off?

Im not sure if its wrong but it works.[/QUOTE]
"noapic" should be the same as "apic=off"
acpi is another thing. Nonetheless if that works for you you can keep on using it ;) .

---

### Post by tseliot on 2006-02-18
[QUOTE=paxjapan]hello world
this week i was looking at my replies and i was thinking of what went wrong with this computer my friend recently change my mother board power supply and this was all used/ also he instaled   
everything in double/ clients,burners,cd,ext /some time i am loading my modules and my synchronizing clock to ntp,ubuntulinux,org (failed) /can it be a double clock speed problem????

also when i am looking at files on my tv it freeze and also i can*t look at 2 files one after an other /

it looks like when i removed one burner and removed a cliente things got better/before i was on amule and linux manually/i am thingking of removing my extras and to get back on what i had before??????:-k 

i know i am slow on this but i have learnd to take my time and i thank-you all for your help
paxjapan[/QUOTE]
I'm not sure to understand what the problem is. Nonetheless I guess a clean install of Ubuntu might help you

---

### Post by dahgremlin on 2006-02-20
Another temporary fix for this is to disable apic in your bios if you have the option. I have an MSI RS480M-IL Motherboard and doing this worked for me.:mrgreen:

---

### Post by HughR on 2006-03-02
Thanks for creating this HowTo.  I'm actually a Fedora Core 4 user, but your HowTo helped me with this problem.  I've posted my experience in [http://bugme.osdl.org/show_bug.cgi?id=3927#c149](http://bugme.osdl.org/show_bug.cgi?id=3927#c149)

Summary: for my machine (HP Pavilion a1250n based on Athlon 64 3800+ x2 with ATI Radeon Xpress 200 (RS482) chipset; x86_64 FC4, with updates), the double speed clock symptom is eliminated via disable_timer_pin_1 but there are still symptoms that are probably related:
- errors like this in dmesg output: APIC error on CPU0: 40(40)
- /proc/interrupts show unreasonable interrupt counts

Who else is experiencing these symptoms?

---

### Post by tseliot on 2006-03-03
[QUOTE=HughR]Thanks for creating this HowTo.  I'm actually a Fedora Core 4 user, but your HowTo helped me with this problem.  I've posted my experience in [http://bugme.osdl.org/show_bug.cgi?id=3927#c149](http://bugme.osdl.org/show_bug.cgi?id=3927#c149)

Summary: for my machine (HP Pavilion a1250n based on Athlon 64 3800+ x2 with ATI Radeon Xpress 200 (RS482) chipset; x86_64 FC4, with updates), the double speed clock symptom is eliminated via disable_timer_pin_1 but there are still symptoms that are probably related:
- errors like this in dmesg output: APIC error on CPU0: 40(40)
- /proc/interrupts show unreasonable interrupt counts

Who else is experiencing these symptoms?[/QUOTE]
My father had the same problem. That error shouldn't affect the functioning of your computer.

BTW I also wrote a guide for Fedora about that although it's not as up-to-date as this guide for Ubuntu:
[http://forums.fedoraforum.org/showthread.php?p=427473#post427473]("http://forums.fedoraforum.org/showthread.php?p=427473#post427473")

---

### Post by neko18 on 2006-03-07
Thanks for the help, this (adding "noapic nolapic") worked for me


---
GRUB MBR
19.3GB Ubuntu Breezy 5.10: /dev/hda2
667MB Swap: /dev/hda5
20GB Windows XP Home: /dev/hda1
Compaq Presario v2000
AMD Mobile Sempron
Some ATI Gfx. Card
256MB RAM
---

Again, thanks

---

### Post by beerorkid on 2006-03-09
OK I kinda got it working correctly before yet some things were messed up.  My ehternet was much slower.  anyway I did not investigate the problem thoroughly enough or something.  Maybe the recent update of this excelent howto is way more up to date.  I gave up.  Came back though.

I got it working with "noapic nolpic"
and doing the sudo update-grub

I had given up and have been using vmware player to run ubuntu.  I even tried VLOS which had the same problem

Anyways I followed you updated guide and I am kicking.  I was comtemplating buying a new full sized ATX mobo and case just to get ubuntu or some linux working.  It all good now.

THANK YOU TSELLIOT  you are a king above men.  I bow down to your guidence torards all those afflicted by this problem.

Thanks

noapic nolapic

---

### Post by tseliot on 2006-03-10
[QUOTE=beerorkid]OK I kinda got it working correctly before yet some things were messed up.  My ehternet was much slower.  anyway I did not investigate the problem thoroughly enough or something.  Maybe the recent update of this excelent howto is way more up to date.  I gave up.  Came back though.

I got it working with "noapic nolpic"
and doing the sudo update-grub

I had given up and have been using vmware player to run ubuntu.  I even tried VLOS which had the same problem

Anyways I followed you updated guide and I am kicking.  I was comtemplating buying a new full sized ATX mobo and case just to get ubuntu or some linux working.  It all good now.

THANK YOU TSELLIOT  you are a king above men.  I bow down to your guidence torards all those afflicted by this problem.

Thanks

noapic nolapic[/QUOTE]
Hey, thanks. I wrote this guide because I have had that problem and I know how much annoying it can be.

---

### Post by beerorkid on 2006-03-14
Just a note:
I have had good luck with this guide.  But my tinkering nature led me to try out dapper flight 5.  The double clock speed was not an issue.
Even recognized my audigy 4 sound card. \\:D/  (my breaking point with breezy)

Thanks for your excelent guides

Now to break it by trying to get XGL going :evil: 

for reference:
HP sr1750nx
AMD 64 3500+
evga nvidia 6800 GS
audigy 4

---

### Post by Absolute on 2006-04-03
I have Ubuntu 5.10 64-bit, and unfortunately the fix 'no_timer_check'  didn't work for me.  It would appear to work for an hour or so, but around 30-40 minutes into a video it would become jumpy, and my system clock would leap ahead by minutes.

I did some more checking into the problem, trying every kernel option I could from the Documentation/kernel-parameters.txt file, but didn't have any permanent success.

I discovered another parameter that wasn't mentioned before, however:  notsc
From the documentation:
```
notsc
  Don't use the CPU time stamp counter to read the wall time. 
  This can be used to work around timing problems on multiprocessor systems 
  with not properly synchronized CPUs. Only useful with a SMP kernel
```

I added that option in instead, and haven't had any time issues in the last 4 days.  For reference, this is where I learned of the option:  [http://www.x86-64.org/lists/discuss/msg03747.html](http://www.x86-64.org/lists/discuss/msg03747.html)

---

### Post by tseliot on 2006-04-05
[QUOTE=Absolute]I have Ubuntu 5.10 64-bit, and unfortunately the fix 'no_timer_check'  didn't work for me.  It would appear to work for an hour or so, but around 30-40 minutes into a video it would become jumpy, and my system clock would leap ahead by minutes.

I did some more checking into the problem, trying every kernel option I could from the Documentation/kernel-parameters.txt file, but didn't have any permanent success.

I discovered another parameter that wasn't mentioned before, however:  notsc
From the documentation:
```
notsc
  Don't use the CPU time stamp counter to read the wall time. 
  This can be used to work around timing problems on multiprocessor systems 
  with not properly synchronized CPUs. Only useful with a SMP kernel
```

I added that option in instead, and haven't had any time issues in the last 4 days.  For reference, this is where I learned of the option:  [http://www.x86-64.org/lists/discuss/msg03747.html](http://www.x86-64.org/lists/discuss/msg03747.html)[/QUOTE]

I wrote about it in a post of mine on page 1 of this thread but I forgot to include it in my guide. Ah, my memory...

Thanks for reporting

---

### Post by damu on 2006-04-05
Thanks soooo much Tseliot fot this one!  U're a :KS 

Here is my config :

MB : ASUS AV8 Deluxe
proc : X2 3800+
2 Go of DDR
1 ultra ata HD
1 sata HD

I couldn't boot on smp kernel. It would just hang during the boot process. I sent a bug report, but with no much feedback. Then, I discovered that if my computer was wired to the router, I could boot, but the system had some very strong DCSS (Double Clock Speed Syndrom   :D  ) . I just uninstall this wireless card, and tried again but with no success

And then ...

...I found...
** your thread** !
, and after a couple of attempts, I  found the one line which would save my day : 
> clock=pmtmr notsc

Now, the  world seems to be a much  better place to live in, with a dual core computer working perfectly.  
ok, now it makes sense to install VMware so that I can run Macromedia Director MX and Flash MX from Ubuntu, and never dual boot anymore!!!!

Thhhaannks

---

### Post by tseliot on 2006-04-08
[QUOTE=damu]ok, now it makes sense to install VMware so that I can run Macromedia Director MX and Flash MX from Ubuntu, and **never dual boot anymore**!!!![/QUOTE]
That makes me so happy :)

---

### Post by Ramses de Norre on 2006-05-16
I've figured out apic is causing me to have this problem, but all the options which disable apic make my machine hang at "setting disk parameters" when my NEC dvd drive is connected.

This is really a problem because I really need this dvd drive and the time bug is driving me crazy!

Do you have any clue about this issue? It seems you know quite a lot about the problem.

I own you big time if you're able to fix this for me!

---

### Post by tseliot on 2006-05-17
[QUOTE=Ramses de Norre]I've figured out apic is causing me to have this problem, but all the options which disable apic make my machine hang at "setting disk parameters" when my NEC dvd drive is connected.

This is really a problem because I really need this dvd drive and the time bug is driving me crazy!

Do you have any clue about this issue? It seems you know quite a lot about the problem.

I own you big time if you're able to fix this for me![/QUOTE]
I had the same problem but this fixed it:
```
noapictimer irqpoll
```

---

### Post by Ramses de Norre on 2006-05-18
Ok, this worked once. I booted up and my dvd drive didn't cause any boot problems (did not have the time to test wether it works though..). But when I shut down and reboot my bios cannot load the settings for the drive. 
My hard disks are showing up in the post messages with an identifier line and then a line with their settings but my dvd drive only has this identifier line, nothing happens for a minute or so and then my bios just skips to the other drives..
Grub wont load neither.
If I unplug the dvd drive and reboot everything works fine again..
Any clue on how to solve this?

---

### Post by tseliot on 2006-05-18
[QUOTE=Ramses de Norre]Ok, this worked once. I booted up and my dvd drive didn't cause any boot problems (did not have the time to test wether it works though..). But when I shut down and reboot my bios cannot load the settings for the drive. 
My hard disks are showing up in the post messages with an identifier line and then a line with their settings but my dvd drive only has this identifier line, nothing happens for a minute or so and then my bios just skips to the other drives..
Grub wont load neither.
If I unplug the dvd drive and reboot everything works fine again..
Any clue on how to solve this?[/QUOTE]
That's a hardware issue (otherwise it won't affect the BIOS). I suggest you to replace you dvd drive with a new one.

---

### Post by Ramses de Norre on 2006-05-20
When I boot with the drive disconnected and without any noapic option and then reboot with the drive connected he'll work perfectely. With and without the noapictimer irqpoll. 
But when I use this option (which will work perfectely yhe first time) and then reboot he wont be recognized. So it is related to the options from the former boot.


I have no clue on how to work around this though..

---

### Post by tseliot on 2006-05-20
[QUOTE=Ramses de Norre]When I boot with the drive disconnected and without any noapic option and then reboot with the drive connected he'll work perfectely. With and without the noapictimer irqpoll. 
But when I use this option (which will work perfectely yhe first time) and then reboot he wont be recognized. So it is related to the options from the former boot.


I have no clue on how to work around this though..[/QUOTE]
Did you try to swap the drive with another one to see if anything changes?

---

### Post by Ramses de Norre on 2006-05-20
Ok I have been testing it and this are my results, all boots were with noapictimer irqpoll set as boot option, and another hard disk was connected to sata1.
```
primary master: hard disk
primary slave: none
secondary master: dvd drive
secondary slave: none

hard disk worked, bios hung on dvd drive and grub didn't get loaded.
``` ```
primary master: hard disk
primary slave: none
secondary master: cd-rw drive
secondary slave: none

hard disk worked, bios hung on cd-rw drive and grub didn't load.
``` ```
primary master: hard disk
primary slave: none
secondary master: hard disk
secondary slave: none

only first hard disk worked, bios didn't load second, grub didn't load
``` ```
prim master: hard disk
prim slave: hard disk
ide2 not used

Both drives worked
``` ```
prim master: hard disk
prim slave: dvd drive
ide2 not used

Both drives worked
``` ```
prim master: hard disk
prim slave: dvd drive
sec master: hard disk
sec slave: none

All drives worked
``` ```
prim master: hard disk
prim slave: dvd drive
sec master: hard disk
sec slave: none

The same set up as the previous one, but the bios hung on the hard disk on ide2..
``` 
It seems that my ide2 doesn't work after a noapictimer irqpoll boot, only strange thing is that it did once.. I'm not sure what conclusion to make.
Would it be the motherboard or the bios that causes this? Or maybe something else..

---

### Post by tseliot on 2006-05-20
[QUOTE=Ramses de Norre]It seems that my ide2 doesn't work after a noapictimer irqpoll boot, only strange thing is that it did once.. I'm not sure what conclusion to make.
Would it be the motherboard or the bios that causes this? Or maybe something else..[/QUOTE]
1) Did you try the other boot parameters?

If so,I really wouldn't know how to help you.

2) Did you try Dapper Drake? Does the problem persist in Dapper?

---

### Post by Yohumbus on 2006-05-20
I would just like to throw this out there for people still having problems with this... I used to have to have disable_timer_1 (or something similar) as a boot option to fix the problem with my laptop (used a sempron 32 bit) but as of kernel 2.6.15-22 (or 15-21 not sure) the problem was fixed and I no longer need that boot option. If any of you are willing to try I would suggest you install dapper drake and use the new kernel it offers to try and fix this. Im not sure about it fixing any other processors or 64 bit though.. if someone wants to look at the kernel changelog that'd be cool too.

---

### Post by Ramses de Norre on 2006-05-22
I ran a dapper live session and indeed the problem was solved. But I don't have the time to go through the hassle of dist-upgrading right now so I guess I'll live without the dvd drive untill the end of june.

(Or pull it out of the case and connect it as slave to ide1 when really necessary, I ran the live session like this.)

---

### Post by blknit on 2006-05-23
From kernel 2.6.16 changelog:

commit f9262c12c0084ddba445a9a42e98994018e51400
Author: Andi Kleen <ak@suse.de>
Date:   Wed Mar 8 17:57:25 2006 -0800

    [PATCH] i386: port ATI timer fix from x86_64 to i386 II
    
    ATI chipsets tend to generate double timer interrupts for the local APIC
    timer when both the 8254 and the IO-APIC timer pins are enabled.  This is
    because they route it to both and the result is anded together and the CPU
    ends up processing it twice.
    
    This patch changes check_timer to disable the 8254 routing for interrupt 0.
    
    I think it would be safe on all chipsets actually (i tested it on a couple
    and it worked everywhere) and Windows seems to do it in a similar way, but
    to be conservative this patch only enables this mode on ATI (and adds
    options to enable/disable too)
    
    Ported over from a similar x86-64 change.
    
    I reused the ACPI earlyquirk infrastructure for the ATI bridge check, but
    tweaked it a bit to work even without ACPI.
    
    Inspired by a patch from Chuck Ebbert, but redone.

---

### Post by tseliot on 2006-05-23
[QUOTE=blknit]From kernel 2.6.16 changelog:

commit f9262c12c0084ddba445a9a42e98994018e51400
Author: Andi Kleen <ak@suse.de>
Date:   Wed Mar 8 17:57:25 2006 -0800

    [PATCH] i386: port ATI timer fix from x86_64 to i386 II
    
    ATI chipsets tend to generate double timer interrupts for the local APIC
    timer when both the 8254 and the IO-APIC timer pins are enabled.  This is
    because they route it to both and the result is anded together and the CPU
    ends up processing it twice.
    
    This patch changes check_timer to disable the 8254 routing for interrupt 0.
    
    I think it would be safe on all chipsets actually (i tested it on a couple
    and it worked everywhere) and Windows seems to do it in a similar way, but
    to be conservative this patch only enables this mode on ATI (and adds
    options to enable/disable too)
    
    Ported over from a similar x86-64 change.
    
    I reused the ACPI earlyquirk infrastructure for the ATI bridge check, but
    tweaked it a bit to work even without ACPI.
    
    Inspired by a patch from Chuck Ebbert, but redone.[/QUOTE]
Very interesting... Thanks for the information

---

### Post by agurk on 2006-05-24
Very nice guide tseliot, just a minor detail; your options 3 and 6 are identical (noapic acpi=off).

---

### Post by tseliot on 2006-05-25
[QUOTE=agurk]Very nice guide tseliot, just a minor detail; your options 3 and 6 are identical (noapic acpi=off).[/QUOTE]
Thanks, I've fixed it up

---

### Post by blknit on 2006-05-28
Upgraded to dapper !
No more double clock speed problem on a MS-7168 RS480 based m/b !!

Thanks to the kernel developers and bug submitters !!

---

### Post by gbharris@cox.net on 2006-06-17
[QUOTE=tseliot]The repeated keys and therefore repeated letters... I know it's part of the bug.

Don't you worry, I'll find another workaround to your problem. 
I know how annyoing that problem can be.[/QUOTE]

[QUOTE=bulldog5]Just thought I'd post my results for anyone with similar hardware...

HP a1250n
ATI XPress chipset
AMD Athlon 64 X2 3800+
ATI X800 XL
32-bit Ubuntu 5.10 with kernel 2.6.12-10-k7-smp

I tried every combination of solutions listed in this thread, and the only one that works is "noapic acpi=noirq"

Hope this helps![/QUOTE]

Hello tseliot,

Regarding Bulldogs post.  I have this very set up but just change the Gcard to a ATI x1800xt.  What I have been looking for is how to overclock my AMD X2 3800+.  The  xp home DOS bios will not let me, so I have been searching far and wide for a solution. Please forgive me if I am totally in the wrong place, but I was wondering if I would install  Ub on a partition and overclock from there while i game, then unclock when I go back to xp?   Sorry if I took up your time.  Best wishes  Greg

---

### Post by tseliot on 2006-06-17
[QUOTE=gbharris@cox.net]Hello tseliot,

Regarding Bulldogs post.  I have this very set up but just change the Gcard to a ATI x1800xt.  What I have been looking for is how to overclock my AMD X2 3800+.  The  xp home DOS bios will not let me, so I have been searching far and wide for a solution. Please forgive me if I am totally in the wrong place, but I was wondering if I would install  Ub on a partition and overclock from there while i game, then unclock when I go back to xp?   Sorry if I took up your time.  Best wishes  Greg[/QUOTE]
Ubuntu does not install a BIOS. I don't know if the bootloader options can work for Windows. I guess not.

I suggest you to read the manual of your Motherboard. Perhaps you can overclock by setting the jumpers.

---

### Post by tseliot on 2006-06-17
[QUOTE=blknit]Upgraded to dapper !
No more double clock speed problem on a MS-7168 RS480 based m/b !!

Thanks to the kernel developers and bug submitters !![/QUOTE]
I can confirm it. The bug has disappeared in Dapper (my father has a RS480 based mobo)

---

### Post by sguart on 2006-06-19
[QUOTE=gbharris@cox.net]Hello tseliot,

Regarding Bulldogs post.  I have this very set up but just change the Gcard to a ATI x1800xt.  What I have been looking for is how to overclock my AMD X2 3800+.  The  xp home DOS bios will not let me, so I have been searching far and wide for a solution. Please forgive me if I am totally in the wrong place, but I was wondering if I would install  Ub on a partition and overclock from there while i game, then unclock when I go back to xp?   Sorry if I took up your time.  Best wishes  Greg[/QUOTE]


This thread is not about overclocking. There are lots of information out there about overclocking. Overclocking has to do with your motherboard bios and cpu. You should search for overclocking with your cpu and motherboard and you should come up with something. Your motherboard might not allow overclocking, guessing from your post ("The  xp home DOS bios will not let me"), then you will need a buy a new motherboard that allows it.

sg

p.s. BIOS is before any OS is loaded so DOS, XP, Ubuntu doesn't make a difference.

---

### Post by devilkin on 2006-09-22
Hmm. I have a similar problem, where movies played with (g)mplayer run too fast, and also flash video's played using a 32bit chroot.

Could this be the reason? I have no idea what package that "System Information" thing is referred in the beginning tho... Can't seem to find it!

---

### Post by beerorkid on 2006-09-22
> **devilkin said:**
> Hmm. I have a similar problem, where movies played with (g)mplayer run too fast, and also flash video's played using a 32bit chroot.

Could this be the reason? I have no idea what package that "System Information" thing is referred in the beginning tho... Can't seem to find it!

sounds like it.

system monitor is something you can add to your panel.

right click panel --> add to panel -- system monitor.

---

### Post by devilkin on 2006-09-22
> **beerorkid said:**
> sounds like it.

system monitor is something you can add to your panel.

right click panel --> add to panel -- system monitor.

Hmm. Well, using kubuntu... What package do I have to apt-get?

---

### Post by devilkin on 2006-09-24
Ok. Using noapic no_timer_check fixed my problems too. Abit KN9-SLI board.

---

### Post by msak007 on 2006-09-24
Adding "noapictimer" fixed it for me, but is there a way to have this automatically appended to my kernel options whenever there's an update? It's annoying to get an update, and then forget to add that option and run into the same problem after a reboot and have to manually edit the grub menu to add it.

---

### Post by tseliot on 2006-10-01
> **msak007 said:**
> Adding "noapictimer" fixed it for me, but is there a way to have this automatically appended to my kernel options whenever there's an update? It's annoying to get an update, and then forget to add that option and run into the same problem after a reboot and have to manually edit the grub menu to add it.

Sure. Can you post the content of your /boot/grub/menu.lst ?

---

### Post by Ramses de Norre on 2006-10-01
In your /boot/grub/sources.list is a line ```
# defoptions=quiet splash
```
you need to add "noapictimer" to the end of that line.
Don't mind the "#", that's absolutely normal.

---

### Post by handy on 2006-10-23
> **Ramses de Norre said:**
> In your /boot/grub/sources.list is a line ```
# defoptions=quiet splash
```
you need to add "noapictimer" to the end of that line.
Don't mind the "#", that's absolutely normal.

We don't have one of those in Edgy ?

---

### Post by msak007 on 2006-10-23
> **Ramses de Norre said:**
> In your /boot/grub/sources.list is a line ```
# defoptions=quiet splash
```you need to add "noapictimer" to the end of that line.
Don't mind the "#", that's absolutely normal.

Sorry I never responded to say thanks and let you know that fixed it (on my Dapper desktop). 

handy: I just checked my laptop that's running Edgy and I do have that option there as well. It's on line 88 in my menu.lst, but I added a couple lines at the beginning for gfxboot so in yours it might be line 85.

---

### Post by handy on 2006-10-25
> **msak007 said:**
> Sorry I never responded to say thanks and let you know that fixed it (on my Dapper desktop). 

handy: I just checked my laptop that's running Edgy and I do have that option there as well. It's on line 88 in my menu.lst, but I added a couple lines at the beginning for gfxboot so in yours it might be line 85.

Thanks for your reply.

I tried it but it has no effect unfortunately :( 

This seems is the only problem I found with Edgy so far! :)

---

### Post by tseliot on 2006-10-25
> **handy said:**
> Thanks for your reply.

I tried it but it has no effect unfortunately :( 

This seems is the only problem I found with Edgy so far! :)

What's your problem exactly? And which Motherboard/CPU affects?

---

### Post by handy on 2006-10-26
Thanks for your reply.

My keyboard timing is out, it seems to lag & then race, which causes lots of duplicated letters & some missed ones.

I tried unsuccessfully to solve it in the Repeat Keys dialog & ended up turning Repeat Keys off.

My motherboard is a Gigabyte GA-K8ns Ultra-939 with 64bit 3500 AMD CPU. (my signature has all the spec's)

I'm running the 32bit Edgy.

---

### Post by sillyxone on 2006-11-02
Turion64, no problem under Dapper 64bit

install Edgy 64bit fresh, no problem on startup, but after waking up from suspend, got into "double clock speed" state. Can easily tell by open "Adjust date and time" and look at the second races.

What works:
  noapic nolapic
  noapictimer
  noapic acpi=off

what didn't work:
  no_timer_check (into kopt line)
  noapic irqpoll

---

### Post by sillyxone on 2006-11-04
correction: the fix I reported was not stable. At first, I got the message: Disabling IRQ #177 everytime I modprobe ndiswrapper. Later on, the message does not appear anymore, but then the double-clock-speed problem is back. And now I couldn't fix the bug at all (tried noapic nolapic notsc noapictimer noirq irqpoll)

I'm going back to Dapper since I need a stable development environment. I sure will install Edgy again once those bugs have been cleared. So far, what I love about Edgy:
- clear and beautiful fonts
- faster speed overall (not including the double clock speed)
- "aticonfig --enable-monitor" doesn't kick me back to login screen when switching screen
- fglrx works much better (I has distorted texts in 3D mode in Dapper)
- NetworkManager doesn't need to be restarted after suspend

What push me back to Dapper:
- double clock speed
- unable to adjust screen brightness
- white screen on login sometimes (ATI X200, fglrx/ati). It happened on Dapper too but I was able to fix by Ctrl-Alt-F1 then switch back to Ctrl-Alt-F7

---

### Post by sillyxone on 2006-11-28
I just reinstalled Edgy fresh from CD. Installed NetworkManager 0.6.3, ndiswrapper 1.9 (driver 1.28 ). This time, when I boot up, my laptop paused a long time when enabling the wireless with a message about invalid irq #177  and told me to try irqpoll option.

Now once I added irqpoll as a boot option, not only the double speed clock problem is gone, I now can use power button to display the shutdown menu, use the sleep key to suspend, and use the shortcut keys to increase/decrease screen brightness.

I don't know exactly what's going on but I'm happy now. Just one "irqpoll" option solved all problems (didn't work last time). Another difference is that I didn't install fglrx yet, comparing to last time, and don't plan to give it a try.

---

### Post by cuplex on 2007-06-03
Thanks for this Thread!!!
Well after testing alot! i found my problem! 
take a look here:
[http://ubuntuforums.org/showpost.php?p=2775242&postcount=319](http://ubuntuforums.org/showpost.php?p=2775242&postcount=319)


maybe this helps some ppl!

---

### Post by cor2y on 2007-06-09
This works with Feisty as well for those experiencing the slow downs and strange lockups.
I myself thought it was the gnome network manager applet but it wasn't that it was this clock speed issue.
Never had this problem in the previous releases of ubuntu.

---

### Post by ashraf87 on 2007-06-23
i'm new with ubuntu.. is my motherbord are bad??

sorry for my poor english

p/s: what is the BSOD??

---

### Post by dannyboy79 on 2007-06-25
> **ashraf87 said:**
> i'm new with ubuntu.. is my motherbord are bad??

sorry for my poor english

p/s: what is the BSOD??
How are we suppose to know what motherboard you have if you don't tell us??? Also, BSOD is the **B**lue **S**creen **O**f **D**eath from the Windows environment.

---

### Post by jdesai on 2007-09-24
Thanks much. I am running gutsy and this bug still exists - Thanks for the solution. The option
   noapic acpi=off
worked for me. I am running AMD/nVidia.

---

### Post by spegru on 2007-12-29
I used the "noapic acpi=off" option to fix my setup (32 bit kubuntu on 64 bit AMD hardware. It certainly fixed the problem.

I have one question though: Isn't APIC  to do with power mangement?
Does this mean the setup will now run hotter/ use more power?

spegru

---

### Post by Alazar on 2008-02-16
[  24.32732] PCI: Cannot allocate resource region 3 of device 0000:00:00.0

Laptop: Asus A6Rp
32-bit system
Video: ATi Radeon X200M

I tried all commands :
noapic acpi=noirq
noapictimer irqpoll
noapic nolapic
noapic acpi=off
noapictimer
noapic acpi=noirq nolapic
clock=pmtmr notsc

what i shall do?

---

### Post by spegru on 2008-02-17
I've just had to reinstall linux because of this, but it showed me an important part of the problem I think.

I'd used the acpi=off option previously (it was the only one that worked - and noapic was not needed). This had the undesirable side effect of preventing screen savers coming on and that the shutdown commands didn't work either. 

This suddenly became alot worse the other day due to a kernel update that meant my nvidia drivers stopped working leaving me without a GUI. I know how to fix that by editing xorg.conf - but I couldn't edit it due to the uncontrollable text cursor!

So any way I decided it was time for a refresh and I installed PCLinux OS 2007 - which has no double speed problem!

However  its kernel is an old one: v2.6.18.8 - which doesn't support the Digital TV I want. So I downloaded and installed a much newer kernel 2.6.22.15. 

Guess what: DVB works ok but the double speed problem is back!

It seems that the kernel introduced a problem somewhere in between Kernels 2.6.18.8 and 2.6.22.15!

Now I suppose I have to choose between double speed or no power control or no DVB!. Fortunately though the different kernels are now grub boot options so at least I can choose!

---

### Post by Alazar on 2008-02-17
Does anybody have the same problem?

---

### Post by Alazar on 2008-02-20
Pfff, up topic...

---

### Post by spegru on 2008-02-23
By the way I can confirm that the acpi=off option prevents the system from shutting down properly from desktop commands and that if you push the physical power button the system shuts off instantly. (In fact screen savers do work after all)

So although acpi=off works, its very crude.

I am sure that at some point not too long ago,  I had no doublespeed, proper power control, and dvb all at the same time. I now assume this was with an earlier kernel, but I do not remember which one - it was in ubuntu maybe 4 months ago.


There must be a better way to solve the double speed problem!

(yes I did try the ones in  this thread but no other worked so far) 


spegru

---

### Post by spegru on 2008-03-02
Ah Ha - A better solution!

I found in a bug report on opensuse but it seems to work

Add the following to the boot option in grub

clocksource-tsc

Apparently this prevents the kernel picking up two timers

DVB and everything now.

Works for me!

---

### Post by spegru on 2008-03-02
Ah Ha - A better solution!

I found in a bug report on opensuse but it seems to work

Add the following to the boot option in grub

clocksource=tsc

Apparently this prevents the kernel picking up two timers

DVB and everything now.

Works for me!

---

### Post by zipppz on 2008-05-29
AMD Athlon x64 (single core)
Motherboard chipset: nforce 2 SLI
Geforce 8600 GTS
Hardy Heron x64
generic kernel updated

Hello everyone
My problem is that I don't have the chance to add any boot option to the kernel since I cannot see the Grub screen. All I get is a black screen with the backlight on. I try to enter the system through a virtual console but that doesn't work for the same reason: I see nothing. Sometimes I even can't see the POST screen, and in the rare ocassions I do, it seems the cpu speed is so fast that I can't enter the BIOS settings (I wanted to try disabling Hyper Threading). Still, I can log in and enter the system, though with no graphical environment. I discovered that running a CD or DVD and blindly clicking in the desktop and opening lots of windows sometimes would force the X to work again, and that's how I managed to edit grub's menu.lst and add the no_timer_check to the kopt line, -which didn't work. At this point, I really don't know what else could I try, in the case that I manage to edit menu.lst once again. Any suggestions?

Best regards

---

### Post by Azuu on 2009-07-11
what do we do if we are using grub 1.95 and have no menu.lst anymore?
Edit:
This is much simpler and should be added to the first page of the thread, get grub2.
Once you have grub2 fully installed, get rid of the menu.lst and instead edit the grub.cfg with gedit (save as grub2.cfg, do command rm grub.cfg, open grub2.cfg, save as grub.cfg), you are then confronted with a much simpler looking file to edit.

just copy and paste your change after the splash bit.

---

### Post by liblamb on 2009-11-03
I had this problem in Intrepid, not in Jaunty, and now it is back again in Karmic. It sucks. Anyway, for those trying to find the correct Grub2 file to edit, look for /etc/default/grub. I added acpi=off there and my computer now runs at normal speed. The Grub2 page at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) was a big help.

---

### Post by mk00l on 2009-12-06
Same problem seen in Karmic
I activated only recently the "hyper threading" in Bios on a MSI 865 PE  (HT emulates 2 CPU's in one) and suspect it's causing this issue as I didn't noticed this problem before (was on Fedora but HT caused my system to crash so i disabled it and initially in Karmic I didn't noticed that while HT was disabled)

After 35 min uptime:
 sudo ntpdate ntp.ubuntu.com 
 6 Dec 17:02:50 ntpdate[2895]: step time server 91.189.94.4 offset 9.151671 sec
 
Output for```
 lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
...

```Output for ```
cat /sys/devices/system/clocksource/clocksource0/available_clocksource
tsc hpet acpi_pm
```I modified my /etc/default/grub with:

GRUB_CMDLINE_LINUX="notsc"

Then update grub:
```

sudo update-grub
sudo grub-setup /dev/sda

```Reboot...

Looks good:
```
cat /sys/devices/system/clocksource/clocksource0/available_clocksource
hpet acpi_pm

```

After 35 min uptime:
sudo ntpdate pool.ntp.org
 6 Dec 17:44:44 ntpdate[3059]: adjust time server 91.189.94.4 offset 0.008858 sec

---

### Post by spegru on 2011-02-08
I hadn't had any problem with this until this morning, after some updates. No sorry I didnt notice what they were!
Now the double speed problem on this PC is back!
I did a fix by editing /etc/default/grub using gedit to add the command line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=tsc"
and followed it by
sudo update-grub

It's the clocksource=tsc that does it.
Problem is it seems to be running too slow now, just as before I had problems with TSC before and finished up using PMTMR instead, but that option doesnt appear to work any more.

Any ideas?

---

### Post by spegru on 2011-02-11
I managed to get it back to normal speed by adding acpi=off to the grub setup
However what I cant understand is why this happened. It was working fine for over a year and then suddenly, a problem again.
I'd really prefer to leave acpi on as it seems to be designed for power control
What happened to clocksource=pmtmr? that worked for ages until one day I noticed it was working without

Is there some thing in Bios I need to do?

---

### Post by spegru on 2011-02-24
I still haven't found a better way than acpi=off, bit it is a problem because with this set the pc doesn't shut down properly - hanging at the very last stage until I press the power button (I presume this is because acpi is off)
Anyone got a better idea for the double speed problem?



BTW if you want to try different things at startup you don't have to update grub inside the system every time, you can do it  from the startup screen where it asks what OS to boot etc. select your choice of OS and press 'e'. This brings up a grub edit screen that works only for that time. Edit items you like and when finished do 'ctrl-x' to boot with those parameters. Changes don't stick of course so next time you will have to do the same, but at least it's useful if you  want to try things out quickly, and it's probably less risky too, because it's only a temporary change!

---

### Post by dannyboy79 on 2011-02-25
Using 10.10 and it's all up to date via apt. I have a gateway t-series laptop and it keeps just shutting off when in use on AC power between 1 to 2 hours. Could this solution above help that? I am not sure what to do at this point. The fan is always full speed and hot hot air is always spitting out. I think I have acpi installed. Not sure if awhile back I didn't also install laptop-utils or something like that. I can provide any info you may need. Been running Ubuntu on desktops since back to Feisty but this is the first time I installed it on a laptop. Any help would be greatly appreciated.

---

### Post by dannyboy79 on 2011-03-01
Bump

---

### Post by spegru on 2011-03-04
It's possible that laptop-mode-tools is involved becuase ACPI does get involved in power management. I think it switches ACPI off. I had that problem on an Acer laptop recently and had to install the tools to stop a problem with screen when on battery. I think to tools has a setup file somewhere where you can set options.
As an easy test why not simply try booting from a live cd and seeing if the same happens

---

