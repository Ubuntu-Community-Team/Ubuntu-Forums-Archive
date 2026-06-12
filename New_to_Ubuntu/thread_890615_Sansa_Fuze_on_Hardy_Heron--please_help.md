---
title: "Sansa Fuze on Hardy Heron--please help?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by jd1ckson on 2008-08-15
Hello, All--

first, I have checked every available solution for getting Hardy to see my new 8gb sansa fuze.  None of them worked.  Below is what I've tried:

1)lsusb didn't work--doesn't see my player at all.

2)The player is in MSC mode, not autodetect.

3)The player connects fine to a windows computer

4)I don't have a usb hub, though this was a suggested "fix" (and, frankly, I think having to do that is ridiculous for something that's supposed to "support" linux.

5)There is a fix that says the following command works:
sudo rmmod ehci-hcd; sudo modprobe ehci-hcd

...but Hardy Heron tells me that I don't have ehci-hcd on my computer, so that's no joy, too.


:confused:

Help, anyone????  Why is this so hard, when the device is in MSC mode and should be seen without a hitch?

Currently, my player happily shows itself as "connected", while Linux crosses its arms and sulks in the corner, pretending the Fuze doesn't exist.

Thanks,
~Jen

---

### Post by durand on 2008-08-15
Would there be a way to use the player in Mass Storage mode? There usually is a setting on the player itself to identify it as a computer removable driver rather than as a specific player which might help you...

---

### Post by jd1ckson on 2008-08-15
MSC mode is the mode you use to have the player seen as a mass storage device.  It's already in MSC Mode.

I'm stumped.

---

### Post by durand on 2008-08-15
what does dmesg | less say at the bottom?

---

### Post by jd1ckson on 2008-08-15
Durang, please clarify.  I'm a linux newbie.

Thanks,
~Jen

---

### Post by LowSky on 2008-08-15
did you try to install ehci-hcd

sudo apt-get install ehci-hcd

then try to run those commands

---

### Post by durand on 2008-08-15
Sorry...
Plug in the player, then run this in a terminal (Applications > Accessories > Terminal):
```
dmesg
```
Then paste what it says towards the bottom of the output where it should mention your player and other stuff about it..

and try what LowSky said. Type that command in the terminal as well.

---

### Post by jd1ckson on 2008-08-15
Thanks for the ideas, guys-- I figured out that was a terminal command a few secs ago...

When I get home from work, I will print out the diagnostic info durand requested. 

Then I'll try installing that old usb driver, ehci-hcd, and repeating the suggested process.  (Hopefully this won't affect my existent usb drivers and slow them down?)

If that fails...

I also dropped the $6 for a usb hub, and I'll try that out...



I'd sure like to formulate a simple process for this and post it up to make it easier for others to do, as well.  Thanks for your help!  

~Jen

---

### Post by durand on 2008-08-15
Well, I'm not sure why you would need a usb hub!

---

### Post by jd1ckson on 2008-08-15
hi durand, I have no idea why, but some folks said it worked off of a usb hub, but not off of the regular usb port.  ANyway, there's a bunch of errors when I run that diagnostic test, all related to usb.  They look like this:
[   38.178988] eth1: associated
[   38.179074] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   38.179079] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   38.179084] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   38.179089] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   43.933985] NET: Registered protocol family 10
[   43.934400] lo: Disabled Privacy Extensions
[   43.935071] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.603888] CPU0 attaching NULL sched-domain.
[   47.603897] CPU1 attaching NULL sched-domain.
[   47.611847] CPU0 attaching sched-domain:
[   47.611856]  domain 0: span 03
[   47.611860]   groups: 01 02
[   47.611865]   domain 1: span 03
[   47.611868]    groups: 03
[   47.611872] CPU1 attaching sched-domain:
[   47.611875]  domain 0: span 03
[   47.611878]   groups: 02 01
[   47.611883]   domain 1: span 03
[   47.611886]    groups: 03
[   49.528191] eth1: no IPv6 routers present
[  223.337191] usb 7-2: new high speed USB device using ehci_hcd and address 3
[  223.349040] usb 7-2: configuration #1 chosen from 1 choice
[  223.349409] hub 7-2:1.0: USB hub found
[  223.349597] hub 7-2:1.0: 4 ports detected
[  226.792448] usb 7-2.4: new full speed USB device using ehci_hcd and address 4
[  226.798428] usb 7-2.4: device descriptor read/64, error -32
[  226.825046] usb 7-2.4: device descriptor read/64, error -32
[  226.844533] usb 7-2.4: new full speed USB device using ehci_hcd and address 5
[  226.850668] usb 7-2.4: device descriptor read/64, error -32
[  226.867870] usb 7-2.4: device descriptor read/64, error -32
[  226.887070] usb 7-2.4: new full speed USB device using ehci_hcd and address 6
[  226.922474] usb 7-2.4: device not accepting address 6, error -32
[  226.928197] usb 7-2.4: new full speed USB device using ehci_hcd and address 7
[  226.962658] usb 7-2.4: device not accepting address 7, error -32
[  226.975803] usb 7-2.4: new full speed USB device using ehci_hcd and address 8
[  226.981935] usb 7-2.4: device descriptor read/64, error -32
[  227.017036] usb 7-2.4: device descriptor read/64, error -32
[  227.030455] usb 7-2.4: new full speed USB device using ehci_hcd and address 9
[  227.036116] usb 7-2.4: device descriptor read/64, error -32
[  227.066256] usb 7-2.4: device descriptor read/64, error -32
[  227.183834] usb 7-2.4: new full speed USB device using ehci_hcd and address 10
[  227.279333] usb 7-2.4: device not accepting address 10, error -32
[  227.304886] usb 7-2.4: new full speed USB device using ehci_hcd and address 11
[  227.385680] usb 7-2.4: device not accepting address 11, error -32
[  236.702299] usb 7-2.3: new full speed USB device using ehci_hcd and address 12
[  236.708276] usb 7-2.3: device descriptor read/64, error -32
[  236.722518] usb 7-2.3: device descriptor read/64, error -32
[  236.735993] usb 7-2.3: new full speed USB device using ehci_hcd and address 13
[  236.743039] usb 7-2.3: device descriptor read/64, error -32
[  236.778421] usb 7-2.3: new full speed USB device using ehci_hcd and address 14
[  236.784746] usb 7-2.3: device descriptor read/64, error -32
[  236.798009] usb 7-2.3: device descriptor read/64, error -32
[  236.821202] usb 7-2.3: new full speed USB device using ehci_hcd and address 15
[  236.828081] usb 7-2.3: device descriptor read/64, error -32
[  236.840018] usb 7-2.3: device descriptor read/64, error -32
[  236.859426] usb 7-2.3: new full speed USB device using ehci_hcd and address 16
[  236.887608] usb 7-2.3: device not accepting address 16, error -32
[  236.893202] usb 7-2.3: new full speed USB device using ehci_hcd and address 17
[  236.916236] usb 7-2.3: device not accepting address 17, error -32
[  237.342245] usb 7-2: USB disconnect, address 3
[  237.918221] usb 7-2: new high speed USB device using ehci_hcd and address 18
[  238.052106] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[  238.052131] hub 7-0:1.0: hub_port_status failed (err = -32)
jdickson@dell-desktop:~$

---

### Post by jd1ckson on 2008-08-15
I tried using sudo apt-get install ehci-hcd, but I got the following error:

E: Couldn't find package ehci-hcd

:confused:

It seems this is the problem, but I don't know how to fix?

Thanks for your help....

---

### Post by durand on 2008-08-16
Hmm, it does look like a problem with your USB ports.  echi-hcd is a kernel module which is part of every install so there is no package for it...I really should have read it fully first...

You can try it in other linux distributions to see if the problem is actually to do with your ports or ubuntu though this may be a bit annoying...First try running ubuntu from the live cd to see if it shows up. Then try some others (Fedora, openSUSE, Linux Mint, etc) because I'm not sure if its a hardware or software problem..
Maybe thats why they told you to use a usb hub...? Well, you're just going to have to experiment because those last few lines in dmesg aren't exactly normal linux output...

---

### Post by jd1ckson on 2008-08-16
I think it's something to do with Hardy Heron.  The usb ports work fine--they see pen drives and external drives other than the fuze.  The computer is a new dell inspiron 1525...came with Feisty Fawn and got updated to Hardy Heron.  I'm hesitant to roll back to Feisty, because I have a classroom environment that requires brand-name java, and it took me maaaaany hours of research and frustration to get java up and running.

Sigh.  I guess I'll just have to use my boyfriend's computer to manage my music--I just think it's insane, because the fuze is supposed to function as an MSC device, it's in MSC mode, and it works fine with Windows.  They shouldn't be able to put "Linux Compatible" on the side of something that has so many problems.

Thanks for trying, though.

Cheers,
~Jen

---

### Post by durand on 2008-08-16
Sorry that I couldn't be more helpful :(

---

### Post by jawinterton on 2008-09-04
sudo rmmod ehci-hcd; sudo modprobe ehci-hcd worked for me.

---

### Post by jaygo on 2008-09-04
running "lsusb" (that's the letter L), either from the terminal or from the run box (alt + f2), works great. You don't need root either. Run it and wait about five seconds and it should show up.

I'm guessing this is an issue with the hardware/firmware of the fuze.

---

### Post by treggmo on 2008-09-05
My built-in webcam was not recognized by Hardy so I searched extensively and found a command that did the trick.
With the Fuze plugged in, in a terminal type:

sudo update-usbids

Then run "lsusb" and see if the Fuze is recognized.
Hope it works for you.

---

### Post by ScottHW on 2009-01-09
Just wanted to drop a quick note to let everyone know my experiences.

I had the exact same symptoms (I've flashed my Revision 1 8GB Fuze with Firmware V01.01.22A).

Of course, since I'm running Linux, I don't want to have any kind of messing around with the Sansa software nonsense.  This is just file transfers, I mean come on1

I tried **fdisk -l** and **mount -l** myself to see why the thing wasn't showing up when I plugged it in.  Then I came across this thread.  I hadn't remembered to try **lsusb**

Well, when I typed it, after 5 seconds, the Fuze just mounted on it's own.  Originally, lsusb didn't display anything connected.  But somehow just probing that for display caused Ubuntu to pick-up the Fuze.

I'll post this over in the Sansa forums, too.  I keep track of that one, and have made suggestions for improvements in the firmware.  Looks like maybe they should take a look at this issue, too.

I guess now I have a relatively easy, working solution; just a quick lsusb will mount the device.  I wish it would work like it's supposed to, tho... :/


Oh, and after it did auto-mount, I tried fdisk again.  What a mess!
(the relevant part)
```

Disk /dev/sdb: 8187 MB, 8187281408 bytes
252 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15624 * 512 = 7999488 bytes
Disk identifier: 0x--------

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       49804      122866   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(49803, 223, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(122865, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       10797      134711   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10796, 206, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(134710, 140, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      119681      243594   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(119680, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(243593, 203, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      184696      184699       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(184695, 104, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(184698, 243, 33)
Partition 4 does not end on cylinder boundary.

```

---

