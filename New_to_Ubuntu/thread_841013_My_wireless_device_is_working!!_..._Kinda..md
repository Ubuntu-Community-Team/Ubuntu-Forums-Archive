---
title: "My wireless device is working!! ... Kinda."
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Cheesecakeman on 2008-06-26
So anyways, I installed ndiswrapper, installed the drivers, and the thing started working. Kind of.

it said it was connecting to the network, even had the name of the network listed, and it just didn't work. Worried that possibly the signal was down, I hopped on my old laptop (the one I'm on now) and tried the connection. It worked, so I think theres something wrong with how it was installed or something.

I'm gunna list two things that I think are going on here.

#1: I choose the wrong driver before, but never uninstalled it, because I have no idea how to.
#2: It came up with some sort of error when I made it, uh, what was the words they used... "Load the driver to memory"

This command was used to do this:

```
  sudo depmod -a
  sudo modprobe ndiswrapper
```

and to check for errors, I typed in:

```
 tail /var/log/messages
```

which gave me this mararky, also everytime I restart I have to do that command again because the wireless option and all of its menu's go away. Ya know, it'll show a list of wireless connections. All that dissappears and I have to retype in that command. 

The Malarky:

Oh...crud. It's not letting me get the malarky right now. I'll get back to you on that -_-

Ok here is the malarky.

Jun 25 20:15:26 Miracle kernel: [  119.539999] UDF-fs: No VRS found
Jun 25 20:17:03 Miracle kernel: [  216.297967] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Jun 25 20:17:03 Miracle kernel: [  216.527438] usb 4-6: reset high speed USB device using ehci_hcd and address 2
Jun 25 20:17:04 Miracle kernel: [  216.757985] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
Jun 25 20:17:19 Miracle kernel: [  231.773013] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
Jun 25 20:17:19 Miracle kernel: [  231.773025] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Jun 25 20:17:19 Miracle kernel: [  231.773047] ndiswrapper (mp_halt:259): device ce82f480 is not initialized - not halting
Jun 25 20:17:19 Miracle kernel: [  231.773052] ndiswrapper: device eth%d removed
Jun 25 20:17:19 Miracle kernel: [  231.773081] ndiswrapper: probe of 4-6:1.0 failed with error -22
Jun 25 20:17:19 Miracle kernel: [  231.773106] usbcore: registered new interface driver ndiswrapper

Also, this time the device isn't working at all. Good times >.<

---

### Post by cdtech on 2008-06-26
Let's see your wireless info:
lshw -C network

And your driver that you installed with ndiswrapper:
ndiswrapper -l

---

### Post by Cheesecakeman on 2008-06-26
Alrighty.

Description: Ethernet interface
Product: RTL-8139/8139C/8139C+
Vendor: Realtek Semiconductor CO., Ltd.
Physcial id: 2
bus info: pci@0000:02:02.0
Logical name: eth0
Version: 10
Serial: 00:40:2b:3f:3e:46
Width: 32 bits
Clock: 33mhz
Capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 mingnt=32 module=8139too multicast=yes

the other command did this

athfmwdl : Driver installed
netwg11t: Driver installed, Device present


On a side note, why can't I put the resolution anything higher then 640? That's rather annoying! Is it because when I installed I had it in safe graphics mode? when it wasn't it was dreadfully slow. 256mb of ram aint enough i guess >.<

---

### Post by Methuselah on 2008-06-26
On the resolution issue, what kind of graphics card do you have?

```

lspci | grep VGA

```

---

### Post by Cheesecakeman on 2008-06-26
Oh, and also, I'd really like that uninstall command. Uninstall everything and try a different driver- I own the CD so I can pick and choose between 98 and win2k/XP.

I've heard that one may work and the other might, so yeah. Can I please have a uninstall command? :P



To that dude /\

VGA compatible Intel corperation 82845G/GL[Brookedale-G}/GE Chipset intergrated graphics device. (Rev 01)

But I used ubuntu once before on the same computer (Feisty Fawn) and it was fine then. Although, I uninstalled it that day. Same problem- Wireless issue.

---

### Post by Cheesecakeman on 2008-06-26
Ignore that. I figured out the command, but it doesn't work.

ndiswrapper -r

It said "Inappropriate ioctl for device"

Help?

---

### Post by Methuselah on 2008-06-26
I couldn't get the right resolutions with my ATI card unless I configured X the 'old fashioned' way.

If you have the stomach for it try the following procedure:
[You might want to print it because you won't be able to run firefox with X down]

Close your programs/save work and do CTRL+ALT+BACKSPACE to kill X.
After login screen comes up, hit CTRL+ALT+F2 to get a terminal.

Type Username <enter> then Password <enter>
[password won't be echoed]

Become root user:
```

sudo su

```

Shut down the gnome display manager:
```

/etc/init.d/gdm stop

```

Back up your current xorg.conf:
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig

```

Let X try to configure itself
```

X -configure

```

Test it out:
```

X -config /root/xorg.conf.new

```

At this point you should see a rather unattractive screen with an 'X' cursor. Hopefully you notice that your resolution is also quite good.

***If you get crashes or hangups here forget the following step.
***Kill X [CTRL+ALT+BACKSPACE] if necessary and go straight to the step headed **WRAP UP**.

Kill X with CTRL+ALT+BACKSPACE
Copy the auto-generated xorg.conf to the expected location
```

cp /root/xorg.conf.new /etc/X11/xorg.conf

```

**WRAP UP**
Start gdm:
```

/etc/init.d/gdm start

```

Exit the root terminal
```

exit

```

Hit ALT+F7 to get back to the login screen and login.
The screen resolutions dialog should list some better resolutions now if you don't already have a rather nice one.

The worked for me to get widescreen resolutions in my setup.
If you have problems and wish to go back to what you had before you can
Restore the backup of xorg.conf
```

sudo cp /etc/X11/xorg.conf.orig /etc/X11/xorg.conf

```

---

### Post by Cheesecakeman on 2008-06-27
Alright, I got my screen resolution to work out but the wireless device still isn't. Also, I can't seem to get it to load up the drivers when I restart, that ndiswrapper -m command, I think that was the name of it, isn't working properly. 

After doing a bit of reading, I found that it is not good to use the drivers on the CD, rather use ndiswrapper tested drivers. I think that this might be my problem... But unfortunatly I have no idea where to look. Can you please help?

Oh, this helps a lot
[https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)
Seems appropriate :P

---

