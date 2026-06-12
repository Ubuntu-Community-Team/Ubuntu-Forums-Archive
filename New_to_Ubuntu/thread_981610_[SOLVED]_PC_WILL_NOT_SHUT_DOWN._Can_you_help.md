---
title: "[SOLVED] PC WILL NOT SHUT DOWN. Can you help?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-13
Ubunteros,

I'm running 8.04LTS. When I click the red icon to shut down my PC the PC goes through the motions but in the very end the Ubuntu logo still stays on the monitor and PC just "hangs". It never turns itself off.

Can anyone assist?

Thank you!

---

### Post by Crafty Kisses on 2008-11-13
What happens if you run this command?
```
sudo shutdown -r now
```

---

### Post by suomalainen on 2008-11-13
This command that you offered re-booted my PC.

---

### Post by Crafty Kisses on 2008-11-13
OK that's good. Have you tried removing splash from the boot options?

---

### Post by suomalainen on 2008-11-13
No I haven't. How is that done? If you can walk me through that would be very much appreciated....!!

---

### Post by Crafty Kisses on 2008-11-13
First you need to run this command in the terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
```
That will copy your GRUB menu list, just in case, after you've ran that, run this command:
```
sudo gedit /boot/grub/menu.lst
```
Once you see the text editor pop up, you need to find your Ubuntu kernel and remove the words **quite** and **splash**. Here's an example of what you would see first:
```
title		Ubuntu, kernel 2.6.27.6
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27.6 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.27.6
savedefault
boot
```
Then this is what you need to change it to:
```
title		Ubuntu, kernel 2.6.27.6
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27.6 root=/dev/hda2 ro
initrd		/boot/initrd.img-2.6.27.6
savedefault
boot
```
Once you've done that, save it and close text-editor, then run this command:
```
sudo update-grub
```
Then reboot and see if it still hangs when you shutdown.

---

### Post by sirebral on 2008-11-13
My guess is it is a driver that is failing to shut off.  Probably a network device. (not saying Codename is wrong, just an issue from experience)

How are you connected to the internet?

---

### Post by suomalainen on 2008-11-13
This is what the line looked like that I changed based on your instructions.

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22a25f48-3152-43e1-81a3-9ab7b91ce2bc ro
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22a25f48-3152-43e1-81a3-9ab7b91ce2bc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

The change I made did not help... PC still hangs.

What else can I do?

---

### Post by sirebral on 2008-11-13
Please answer my question.

---

### Post by suomalainen on 2008-11-13
I'm connected to internet via broadband cable modem.

---

### Post by suomalainen on 2008-11-13
I re-edited the string that Codename asked me to change. The reason is because all kinds of messages started to appear when I tried to shut down. I couldn't read them as they went too fast.

Now I'm back to where I started. Ubuntu splash screen just hangs and never turns off.

---

### Post by sirebral on 2008-11-13
hmm.  Are you using ndiswrapper to use your modem?

Just curious.  I have had a similar problem with older versions and even with 8.10 briefly.  I have a wireless USB adapter.  I just unplugged the adapter and got a screen of text that was showing my PC's connection attempting and failing several times before it gave up. (and then shut down)

You might try disconnecting any USB devices that are running, or just unplugging your modem.

---

### Post by suomalainen on 2008-11-13
I'm not trying to connect to the Internet. I'm trying to turn my PC off.... MY computer doesn't want to turn off.

---

### Post by sirebral on 2008-11-13
> **suomalainen said:**
> I'm not trying to connect to the Internet. I'm trying to turn my PC off.... MY computer doesn't want to turn off.

yeah, I know that.  Please re-read my post.

---

### Post by iponeverything on 2008-11-13
> **suomalainen said:**
> This is what the line looked like that I changed based on your instructions.

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22a25f48-3152-43e1-81a3-9ab7b91ce2bc ro
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22a25f48-3152-43e1-81a3-9ab7b91ce2bc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

The change I made did not help... PC still hangs.

What else can I do?

The point of the above exercise was not to fix the problem, we don't what the problem is yet.  It was to identify where it is hanging.

---

### Post by suomalainen on 2008-11-13
It hasn't anything to do with being ON or connected to the Internet.

I had this problem before and had to edit a few lines. MY fault is that I deleted the instructions when I reinstalled 8.04...

---

### Post by suomalainen on 2008-11-13
still won't shut down.........

---

### Post by suomalainen on 2008-11-14
Pc's been on all night and still won't turn off.

---

### Post by sathiskumarmsk on 2008-11-14
Have you tried poweroff command

---

### Post by suomalainen on 2008-11-14
No. What is the power off command? Will it turn my PC off automatically when I want to shut down my PC for the night?

Do I need to use special command each time????

Please tell me more..

---

### Post by philinux on 2008-11-14
When it hangs at shutdown it's fairly safe to button it. However until solved use

sudo shutdown now

Is it an old motherboard. Mine did this and I had to to add acpi=force to the kernel line in grub.

---

### Post by suomalainen on 2008-11-14
The:

sudo shutdown now

Command did not work. It only re-booted my PC. It even brought me into some sort of a DOS looking recovery screen... Really odd to see.

I do have older motherboard.

How do I edit the line you suggest???

---

### Post by philinux on 2008-11-14
Mine was pre 2000 and it gave a line at boot saying sort of "old bios acpi=force required".

I found a newer bios and flashed it to cure this problem.

Before editing grub do you see that sort of message?

---

### Post by sathiskumarmsk on 2008-11-14
ALSO TRY shutdown -k command..watch the terminal output..

---

### Post by sathiskumarmsk on 2008-11-14
shutdown -h this command halts your system after shutdown..

---

### Post by fourscore on 2008-11-14
Try this -  First  LogOff and then  ShutDown from the login screen.

---

### Post by suomalainen on 2008-11-14
Thanks for the input everyone:

During start-up I'm receiving this line. See also attachment:

"ACPI: no DMI BIOS year, acpi-force is required to enable ACPI"

Not sure if it means anything????

Also added what I see during start-up. I.E. the very first screen.

Look forward to replies in getting this issue resolved.

---

### Post by unutbu on 2008-11-14
[list=1]
[*]**If the problem is related to networking**
First try this: Open a terminal and type
```

sudo /etc/init.d/networking stop
```

Then try shutting down. If it works, it means that the shutdown problem is related to
networking.

In that case, try this [http://ubuntuforums.org/showpost.php?p=6098072&postcount=6](http://ubuntuforums.org/showpost.php?p=6098072&postcount=6).
If that does not do the trick, try [http://ubuntuforums.org/showpost.php?p=6069946&postcount=6](http://ubuntuforums.org/showpost.php?p=6069946&postcount=6). That solution is ugly, but it seems to work for some people (and as long as the problem is related to networking). 

[*]**If the problem is solvable with acpi=force:**
If you find that stopping networking does not solve the problem, try booting with kernel option acpi=force. Here is an example of success using this method:
[http://ubuntuforums.org/showpost.php?p=5879657&postcount=10](http://ubuntuforums.org/showpost.php?p=5879657&postcount=10)

This page explains how to boot with kernel options like acpi=force: [http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4)

[*]**If the problem is solvable with apm**
If acpi=force does not work, try this 
[http://ubuntuforums.org/showpost.php?p=6289063&postcount=5](http://ubuntuforums.org/showpost.php?p=6289063&postcount=5). If that does not work, try this
[http://ubuntuforums.org/showpost.php?p=5586513&postcount=3](http://ubuntuforums.org/showpost.php?p=5586513&postcount=3)
[/list]

---

### Post by philinux on 2008-11-14
> **suomalainen said:**
> Thanks for the input everyone:

During start-up I'm receiving this line. See also attachment:

"ACPI: no DMI BIOS year, acpi-force is required to enable ACPI"

Not sure if it means anything????

Also added what I see during start-up. I.E. the very first screen.

Look forward to replies in getting this issue resolved.

Yep thats the problem I had. As Unutbu says adding acpi=force to the kernel line in grub will solve it. Unless there is a kernel update then you have to edit grub again. 
Or find a newer bios and update it. Updating bios can be risky.

---

### Post by suomalainen on 2008-11-14
philinux,

So you really had this problem too???

Can you help me with "Unless there is a kernel update then you have to edit grub again."

How do I edit grub???? I'm unsure about this and what I must edit exactly. Can you assist me?

As a side note. I thought in System under either "Preferences" OR "Administration" I could learn what type of motherboard I have, but I can't seem to find these details. Do you know where I must look to know what model motherboard I have.

I opened my machine up to look this way but I couldn't see anything relating to model etc...

Thanks for the help....

---

### Post by philinux on 2008-11-14
gksudo gedit /boot/grub/menu.lst

Scroll down to this bit. Example only. Add the bit in red to the end of the 3rd line starting **kernel.** Then save changes.
```
## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        8b0dea6a-f902-4412-8746-a6f9ee7cc32f
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=8b0dea6a-f902-4412-8746-a6f9ee7cc32f ro splash quiet [COLOR=Red]**acpi=force **[/COLOR]
initrd        /boot/initrd.img-2.6.27-7-generic

```

---

### Post by benc123 on 2008-11-14
thANKS

---

### Post by xebian on 2008-11-14
> **suomalainen said:**
> Pc's been on all night and still won't turn off.

How about pulling the plug off the wall?  Need to teach misbehaving PC who is the Master.:)

---

### Post by xebian on 2008-11-14
> **suomalainen said:**
> This command that you offered re-booted my PC.

Of course the -r option is reboot.

It should be

[COLOR="Red"]sudo shutdown -h now[/COLOR]

---

### Post by suomalainen on 2008-11-14
philinux,

That took care of the issue! Thanks so much!

P.S. I sent a thanks for you.

---

