---
title: "[SOLVED] Shutdown Errors"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by jamesrfla on 2008-08-03
When I go to shutdown my Ubuntu computer it goes through fine until I get this first picture attachment. Then it sits their so I hit the power button on the front of my computer and I get this second picture attachment. Any ideas on what is causing this?

---

### Post by jamesrfla on 2008-08-03
Also if this will help. I see it says system halt or something then I hear the hard drive shutoff then 5 sec later is comes up with those errors above.

---

### Post by billgoldberg on 2008-08-03
More people, including me, are getting these errors.

It's nothing to worry about.

---

### Post by jamesrfla on 2008-08-03
> **billgoldberg said:**
> More people, including me, are getting these errors.

It's nothing to worry about.

I know but I have to manually hold down the power button to get it to shut off.

---

### Post by blue_shift on 2008-08-03
Might be no good, but you could try shutting down from the command line and see if that makes any difference. It's worth a go.
```
sudo shutdown -h now
```

---

### Post by billgoldberg on 2008-08-03
> **blue_shift said:**
> Might be no good, but you could try shutting down from the command line and see if that makes any difference. It's worth a go.
```
sudo shutdown -h now
```

```
sudo shutdown
```

will do just fine.

---

### Post by madsmeg on 2008-08-03
or a

```
sudo halt
```

:)

---

### Post by jamesrfla on 2008-08-03
Okay I will try ```
sudo shutdown
``` and see what happens.

---

### Post by jamesrfla on 2008-08-03
Okay the code ```
sudo shutdown
``` didn't work in terminal. The ```
sudo shutdown -h now
``` worked in terminal but still got the same errors. I will try ```
sudo halt
``` next.

---

### Post by blue_shift on 2008-08-03
You could force it if that doesn't work.
```
sudo halt -f
```

---

### Post by jamesrfla on 2008-08-04
> **blue_shift said:**
> You could force it if that doesn't work.
```
sudo halt -f
```

Yeah that didn't work. I went ahead and did some test with a new power supply, disabling acpi in the BOIS and enabling it, and editing GRUB startup options. No luck and still getting errors.

---

### Post by ibuclaw on 2008-08-05
Presuming that all tasks have ending and the kernel is just waiting for a certain signal that will never reach. It should be alright to use the SysMagicReq keys to complete the shutdown.

That is pressing:
**Alt+Printscreen+R**
**Alt+Printscreen+S**
**Alt+Printscreen+U**
**Alt+Printscreen+O**

This will also provide a safer way to shutdown until you can figure out the root of the problem.

Regards
Iain

---

### Post by Jordanwb on 2008-08-05
> **jamesrfla said:**
> I know but I have to manually hold down the power button to get it to shut off.

Yeah, that's not good for the ole Hard Drive. Has this happened since you installed Ubuntu? If not I think it may be a problem with ACPI, the kernel and your motherboard.

---

### Post by jamesrfla on 2008-08-05
> **Jordanwb said:**
> Yeah, that's not good for the ole Hard Drive. Has this happened since you installed Ubuntu? If not I think it may be a problem with ACPI, the kernel and your motherboard.

I wasn't able to install anything using this hard drive except Ubuntu when I uses acpi=off. Any ideas?

---

### Post by Jordanwb on 2008-08-05
It seems - from what you said - that the hard drive (or some other component) doesn't support ACPI, which is why you can't shutdown. Linux uses ACPI to spin down and stop the hard drives and other stuff.

---

### Post by jamesrfla on 2008-08-05
To add if this will help when I hit shut down I see all of the bar disapera and then I heard the hard drive like shutdown and then come back on. Then after about 30 sec I get the first screen shot then I press the power button (not holding it down) and I get the secound screen shot. Then it just sits thier and I hold down the power button so it will turn off. I tried disabling ACPI in the BOIS and renabling it. I think the hard drive was the problem in the first place. Any ideas?

---

### Post by unutbu on 2008-08-05
jamesrfla, you might want to try [http://ubuntuforums.org/showpost.php?p=5497534&postcount=28](http://ubuntuforums.org/showpost.php?p=5497534&postcount=28)
(the second part directed to matchstich, starting with the command "gksu gedit /etc/modules").

In the instructions you are asked to boot with
kernel option "apm=on". If you know how to boot with kernel options, great. If not, read
[http://ubuntuforums.org/showpost.php?p=5495458&postcount=25](http://ubuntuforums.org/showpost.php?p=5495458&postcount=25)
starting where it says "To try it for just one boot:". The explanation is for "acpi=force", but just change that to "apm=on".

---

### Post by jamesrfla on 2008-08-05
> **unutbu said:**
> jamesrfla, you might want to try [http://ubuntuforums.org/showpost.php?p=5497534&postcount=28](http://ubuntuforums.org/showpost.php?p=5497534&postcount=28)
(the second part directed to matchstich, starting with the command "gksu gedit /etc/modules").

In the instructions you are asked to boot with
kernel option "apm=on". If you know how to boot with kernel options, great. If not, read
ttp://ubuntuforums.org/showpost.php?p=5495458&postcount=25
starting where it says "To try it for just one boot:". The explanation is for "acpi=force", but just change that to "apm=on".

So you want me to get rid of the Kernel option acpi=off and put in apm=on? Will this instructions mess up network manager?

---

### Post by unutbu on 2008-08-05
> **jamesrfla said:**
> So you want me to get rid of the Kernel option acpi=off and put in apm=on instead?

No, you can try them both together.

> Will this instructions mess up network manager?

I don't think this will affect network manager, but I'm not sure. To make the instructions safer, here are instructions on how to revert the changes:

Since the instructions for booting with kernel option "apm=on" will only last for one boot, the next time you boot up, the "apm=on" kernel option will be gone, and you should be able to boot up as usual.

Then to remove the edits:

```
sudo rm /etc/modprobe.d/power
gksu gedit /etc/modules
```
Remove the line which says 'apm'; it should be the last line of the file.

That's it. Then your system should be the same as it is now.

---

### Post by jamesrfla on 2008-08-06
unutbu your post worked!! I just did the instructions and it shut down the right way after rebooting. I still have to use the Kernel options acpi=off and apm=on in order to boot and shut down the right way. I also tried disabling and enabling ACPI in the BOIS but that didn't change anything. I hope it is all right to use the acpi=off and apm=on. Thanks for all your help!!:guitar:

---

### Post by DSL5 on 2008-08-07
jamesrfla, could you please post exactly what you did? I am having the same problem and I can't get this fix to work.
thank you.

---

### Post by jamesrfla on 2008-08-07
> **unutbu said:**
> jamesrfla, you might want to try [http://ubuntuforums.org/showpost.php?p=5497534&postcount=28](http://ubuntuforums.org/showpost.php?p=5497534&postcount=28)
(the second part directed to matchstich, starting with the command "gksu gedit /etc/modules").

In the instructions you are asked to boot with
kernel option "apm=on". If you know how to boot with kernel options, great. If not, read
[http://ubuntuforums.org/showpost.php?p=5495458&postcount=25](http://ubuntuforums.org/showpost.php?p=5495458&postcount=25)
starting where it says "To try it for just one boot:". The explanation is for "acpi=force", but just change that to "apm=on".

I clicked the first link and did all the instructions their. Then I rebooted and went into the GRUB config and added apm=on. What is it exactly you need help on  DSL5?

---

### Post by DSL5 on 2008-08-07
the grub config at /boot/grub/menu.lst or did u edit it directly at the GRUB dualboot menu?

---

### Post by jamesrfla on 2008-08-07
When you turn on your computer before you see Ubuntu boot you see this GRUB thing and it only lasts for two seconds. I just go in their and add apm=on and then press enter and press b to boot. Then I login and shutdown. If it worked like it did for me I boot up again and go back again to the GRUB and add apm=on. The after I login I make the changes to GRUB permanently so I don't have to do it every time I boot up. Any questions just ask. :)

---

### Post by DSL5 on 2008-08-07
when I go to edit the Grub during boot, I see:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c0cd042e-2354-4034-9756-602968678e52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

which line do I add apm=on to?

(srry, I'm a total newbie at this)

---

### Post by jamesrfla on 2008-08-07
It is okay. Alot of people hear are new to like me sorta. When you get their you need to go down to Kernel. Then press E and then go to the end. Then make sure you type amp=on separate from the other stuff. Just press space then put it apm=on but make sure it is not two spaces from the other stuff. Then press enter and then B.

---

### Post by DSL5 on 2008-08-07
ok, so i just re-booted adding apm=on to the end of the Kernel line. now what.

---

### Post by jamesrfla on 2008-08-07
If you have already done this [http://ubuntuforums.org/showpost.php?p=5497534&postcount=28](http://ubuntuforums.org/showpost.php?p=5497534&postcount=28) then just try to shutdown and see if it will turn off the right way. When I first did it seemed like it was just going to do the same thing again and give me errors but just give it a few. If after a few and you get that error message then you did something wrong.

---

### Post by DSL5 on 2008-08-07
after adding "apm" to the bottom of the /etc/modules, it looks like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2

apm power_off=1
apm
```

my /etc/modprobe.d/power was empty before i added "options apm power_off=1 realmode_power_off=1" to it.

Is this right?

---

### Post by jamesrfla on 2008-08-07
I went to /etc/modprobe.d/power and the only thing I saw was options apm power_off=1 realmode_power_off=1

---

### Post by DSL5 on 2008-08-07
ok, so now the OS shutsdown (Thank you!!!), but the computer itself stays on.

Ugh..i feel like everytime I solve one problem I find another.....

---

### Post by jamesrfla on 2008-08-07
So you have to hold down the power button for it to shut down? I just have to press the shutdown button on the top right of the desktop and hit shutdown and it turns off all the way. This solution should make the computer shutdown all the way including itself.

---

### Post by DSL5 on 2008-08-07
After Ubuntu shuts down, I have to hold the power button to get the computer to turn off.....

---

### Post by jamesrfla on 2008-08-07
Okay maybe you did something wrong. It should shut off all the way. Try this 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Now open to edit:

```
gksudo gedit /boot/grub/menu.lst
```

If you just add the options to each kernel manually, the changes will be deleted when the file is autoupdated later. So rather than doing it like that, find the line that says something like
Code:

# defoptions=splash quiet

And change it to something like
Code:

# defoptions=splash irqpoll

or using whatever parameters are necessary on your system. Do the same for the altoptions line (for the recovery mode kernel):
Code:

# altoptions=(recovery mode) single

and change to something like
Code:

# altoptions=(recovery mode) single irqpoll

Save and close the file, now regenerate it with the new options:
Code:

```
sudo update-grub
```

Change irqpoll to apm=on. Be very careful when you do this!!

---

### Post by ellalan on 2008-08-07
Hi DSL5
Open the Terminal and type: sudo gedit /boot/grub/menu.lst
Then find the line:
kernel /boot/vmlinvz-2.6.xx-xx- generic root.........ro quiet splash
Just after splash leave a space and Type: acpi=force
This worked for me and hope it does the job for you as well.
All the best.

---

### Post by matchstich on 2008-08-07
ok, from what i gather from reading this: it is the hard drive itself that does not

support the shut down sequence?


so, i should be able to swap out hard drives and it will shut down, right?

have a few of them. 

gotta love freecycle.com

gonna try that.  putting in different drives and see what happens

will post back.

thanks


putting in a different drive did not work ,  still the same problem


but, adding acpi=force shuts off the hard drive.

---

### Post by DSL5 on 2008-08-07
actually, with a lot of proding and help from a friend of mine who decided to tell me of his vast Linux knowledge today, I was able to pinpoint my problem. It seems that there is not a acpi for Ubuntu that supports my computer (Toshiba A105-S361). Apparently, this is a common problem and as of right now, there is no solution.

---

### Post by jamesrfla on 2008-08-08
> **DSL5 said:**
> actually, with a lot of proding and help from a friend of mine who decided to tell me of his vast Linux knowledge today, I was able to pinpoint my problem. It seems that there is not a acpi for Ubuntu that supports my computer (Toshiba A105-S361). Apparently, this is a common problem and as of right now, there is no solution.

Another option that you could try if you did the instructions on the link and added apm=on to the GRUB file permanently is to add acpi=off to the GRUB file. Just put acpi=off in front of apm=on and then save the file and do ```
sudo update-grub
``` If that doesn't work you can always get rid of acpi=off and just leave apm=on.

---

