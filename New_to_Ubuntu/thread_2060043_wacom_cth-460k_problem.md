---
title: "wacom cth-460/k problem"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by tago on 2012-09-19
Hi, i have a little problem with my bamboo p&t cth-460/k. When boot my pc the tablet don't start, i must unplug and replug and then it works.
Thanks in advance and sorry for my english

---

### Post by Favux on 2012-09-19
Hi tago,

Weclome to Ubuntu forums!


What release of Ubuntu are you using?

When you first boot do you see **wacom** in **lsmod**?  In other words enter in a terminal after a boot when the tablet isn't working:
```
lsmod |grep wacom
```
There is a good chance that your Xorg.0.log in /var/log will tell us what's going on.  You can open it in gedit and search **Wacom**.  If you do that you should see a section where Xorg tries to hot plug your tablet on start and a second one when you manually do the hot plug.  The difference between the two may be a clue.

P.S.:  Please don't double post.

---

### Post by tago on 2012-09-19
Hi Favux,
Sorry for double post, it was a mistake...
I use 12.04...
When I'm at home, try and let you know, thanks for reply.

---

### Post by tago on 2012-09-19
Hi, the result of lsmod is:
wacom                   51812    0
and in Xorg.0.log file, i don't have any entries

when i plug the wacom:
i have the same result for lmod 
and in the Xorg.0.log file i have this:

---

### Post by Favux on 2012-09-19
OK the lsmod (list modules) shows the wacom.ko (wacom) is auto-loading.  That's the usb kernel driver/module for Wacom tablets.

Do you see wacom entries in Xorg.0.log for when it fails on boot?

The Xorg.0.log looks normal after you do the hot plug.

Are you plugged directly into a usb port on the computer or through a hub?  If directly into the computer have you tried a different port?

---

### Post by tago on 2012-09-19
I don't see any entries and yes i plug the usb port directly and i have try another but don't works....

---

### Post by Favux on 2012-09-19
> I don't see any entries
Interesting.  Why wouldn't there be Wacom entries in Xorg.0.log on boot up?

Hmmm.

Maybe there is some delay or hang with the wacom.ko loading?  Let's try this.  To the list of modules in the modules file in /etc add **wacom** to the bottom of the list:
```
gksudo gedit /etc/modules
```
Then restart.  Let's see if "forcing" the wacom.ko to load changes anything.

---

### Post by tago on 2012-09-19
I try but don't works, think the problem occurs when turn off the pc, cause when restart with wacom plugged, it works...

---

### Post by Favux on 2012-09-19
> I try but don't works
So adding wacom to the modules file didn't help.
> think the problem occurs when turn off the pc, cause when restart with wacom plugged, it works... 
I don't think I understand what you are saying.

That sounds like the tablet does work with a restart but not a cold boot.  Almost like the tablet needs to warm up a little?  If so that suggests something like a capacitor on the tablet is going bad.

---

### Post by tago on 2012-09-19
I don't think, cause i have windows in dual boot and when i use win the tablet start at boot, before choose the system in the grub...

---

### Post by Favux on 2012-09-19
Alright.  My best guess is still that something is going wrong with kernel module loading on your system.  So when the X Server starts (the Xorg.0.log) the wacom.ko isn't available.  Without the kernel usb driver the Wacom X driver doesn't see the tablet and that's why there aren't any Wacom entries in Xorg.0.log.  It is available shortly after the X Server (your gui) comes up.  Which is why you see wacom in lsmod and why a hot plug then works.

Does the tablet work right away if you log out and then log back in?

A reinstall of Ubuntu might fix it and could be the simplest thing.  I'm not sure it is worth trying to track down what is happening in **dmesg**.  Maybe you can live with it?

Maybe try, when the tablet is working, running this command in a terminal:
```
sudo depmod -a
```
That will rebuild all module dependencies.  Then restart, maybe several times.

---

### Post by tago on 2012-09-20
Nothing to do, not works...
As I said, for me, the problem occurs when turn off the pc.
Exist a method for turn off the tablet, before turn off the pc?

---

### Post by Favux on 2012-09-20
> Exist a method for turn off the tablet, before turn off the pc? 
Not that I know about, other than unplugging it.

If this is a driver problem, where it doesn't shut down the tablet gracefully, you might want to try posting on linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)  Maybe one of the developers will help.

---

### Post by tago on 2012-09-20
Ok, i'll try...

---

### Post by tago on 2012-09-21
Nothing to do...
Installed new driver but the problem is not solved.
Not a big problem but...

---

### Post by Favux on 2012-09-21
> Not a big problem but... 
Well sure...

But as far as I know you are the only one reporting the problem.  I'm not getting any new ideas as to what could be going on.  I'd suggest turning on debugging (see **man wacom** in a terminal).  But the Xorg.0.log doesn't show anything when you boot so no point to turning debugging on.

Do you see any error messages after a fresh boot before you do the hotplug with?
```
dmesg |grep [Ww]acom
```
If so what changes do you see with that command after you hotplug the tablet?

At this point I'm wondering if something is going on with your install's usb handling.  And it has nothing to do with Wacom.

---

### Post by tago on 2012-09-21
After a fresh boot the message is:
[   23.666089] usbcore: registered new interface driver wacom
[   23.666091] wacom: v1.53:USB Wacom tablet driver
and when plug:
[   23.666089] usbcore: registered new interface driver wacom
[   23.666091] wacom: v1.53:USB Wacom tablet driver
[15730.395709] input: Wacom Bamboo 2FG 4x5 Pen as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.0/input/input16
[15730.405683] input: Wacom Bamboo 2FG 4x5 Finger as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.1/input/input17

other usb hardware works fine...

I try to install another distro (fedora), in a partition of my HD, and the problem is the same.

---

### Post by Favux on 2012-09-21
OK, what we're seeing is that the device nodes are not created after a start but then are created with a hotplug:
```
[15730.395709] input: Wacom Bamboo 2FG 4x5 Pen as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.0/input/input16
[15730.405683] input: Wacom Bamboo 2FG 4x5 Finger as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.1/input/input17
```
So the problem isn't likely to be with Xorg/udev because the same rules work with a hotplug.  And that may apply to the wacom.ko kernel module/driver.  If it isn't hanging during start up that is.

But why would the X driver, wacom_drv.so from xf86-input-wacom, reject the tablet at startup but then pick it up after a hotplug?  And if it was rejecting it there should be error messages in Xorg.0.log where it tells you what's going wrong and it telling you it is unloading the wacom module.  In this case the wacom module it is talking about would be the wacom_drv.so not the kernel module wacom.ko.

So it comes back to a usb problem, apparently just with wacom.ko.  No clue.  Other people should be reporting this if it was just a wacom.ko problem.

---

### Post by tago on 2012-09-21
ok, then I have to live with this little bother...
thanks anyway!

---

