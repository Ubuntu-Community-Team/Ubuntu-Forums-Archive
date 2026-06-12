---
title: "Kind of beginner: changed 20-intel.conf and now my screen is black/ unable to mount r"
date: 2017-03-31
forum: New to Ubuntu
---

### Post by helplessguy on 2017-03-31
I was trying to turn my fn keys on.
Therefore I used this guys advise: [http://askubuntu.com/questions/866437/function-keys-do-not-work-brightness-sound-ubuntu-16-04](http://askubuntu.com/questions/866437/function-keys-do-not-work-brightness-sound-ubuntu-16-04)
saying:
2. Create **.CONF** file  
[LIST]
[*]Open Terminal 
[*]type (or copy/paste): sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf 
[*]Paste this in the file line for line:   Section "Device" Identifier  "card0" Driver      "intel" Option      "Backlight"  "intel_backlight" BusID       "PCI:0:2:0" EndSection 
[*]SAVE and CLOSE file 
[/LIST]
After restarting my computer went black, and gave me the choice of: 1Ubuntu 2 someting like: extended option 3 memory test
pressing Ubuntu it says:
**[B]kernel panic-not syncing: VFS: unable to mount root fs on  unknown block(0,0)         **[/B]

Is there a way to get back. And not reinstall and loose my files?
Would be really thankfull for any help.


PS:Sorry if I am in the wrong forum, cant really tell which one I am in.

---

### Post by yetimon_64 on 2017-03-31
Did you follow all three of the steps at that link you posted? Or did you, as your opening post suggests to me, only carry out the second step (that you posted here)?

What I am wondering is if you also added the "acpi_osi=" boot parameter to the /**etc**/default/grub file and whether you also updated grub as well. **Note:** the answer on askubuntu actually has the wrong path for the file to be edited and has it shown as /usr/default/grub instead. /usr/default/grub does NOT exist normally, it should actually be /**etc**/default/grub in that answer.

A possible "simple fix" for this would be to boot to a live usb/dvd image and remove the file you created at /usr/share/X11/xorg.conf.d/20-intel.conf. Then reboot back and see if the kernel panic is stopped, if it is I would suggest you follow the link again and make sure you also add the acpi_osi boot parameter and do the updating of grub again.

At this stage, and only by going on your first post details, I think you may have inadvertently triggered the kernel panic by missing out the boot parameter and the grub update.

If you can access the installation from a live image boot, removing the file you added is a pretty simple exercise which should allow you to have another go at fixing the function keys. Regards, yeti.

---

### Post by leunam12 on 2017-03-31
Have you tried undoing what you did? Boot from USB and find that file that .conf file and delete what you added to it. If you created that file (you didn't have a 20-intel.conf file before), then rename it or delete it and see what happens when you reboot.

---

