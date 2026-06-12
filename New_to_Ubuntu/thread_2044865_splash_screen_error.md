---
title: "splash screen error"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by hnf a on 2012-08-20
i want to ask how to fix my splash screen that looks like bar-code,i have try liveCD but no prob found in there except the resoluton but after i install it the splash screen become like this
 [http://img35.imageshack.us/img35/898/hsa0251.jpg](http://img35.imageshack.us/img35/898/hsa0251.jpg)

---

### Post by Bashing-om on 2012-08-20
hnf a ....Hi !
 Seems you have a graphics driver problem.

 Boot the live CD, hold down shift key==>on the boot options screen, choose to boot with "nomodeset".....when ubuntu boots up go to system=>administration=hardware drivers .. should install a driver for your card.....

  Please advise of your results.   regards <==BDQ

---

### Post by hnf a on 2012-08-23
boot on live CD or just insert liveCD then boot normally and hold shift? i have boot with live CD and choose nomodeset and is working but after that what should i do choose try me or just reboot to normal boot sequence i have download the driver but isn't working yet .i have three of them

---

### Post by Bashing-om on 2012-08-23
hnf a;

  Looking good. Let's get you logged into your system, and see what we have to do yet (if anything).
First things first: Boot to your installed system, just after the bios screen clears - hold down the shift key to enable ubuntu's boot options screen. The default kernel should be highlighted at this point. Press the "e" key to edit the boot parameters. Now, look for the line similar to this: /linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro   quiet splash $vt_handoff // : With the arrow key arrow down to this line, and arrow across to "quiet splash" after quiet splash ..insert "nomodeset" by typing nomodeset . ctl-x to continue booting. Do you boot to your login ?

 If you boot to the login screen, go ahead and log into your system. Do you like what you see ? If you like your graphics as it is now .... all that is left to do is make the nomodset permanent by editing your /etc/default/grub file to reflect the above. Else, install alternate graphics drivers.

                Regards <==BDQ

---

### Post by hnf a on 2012-08-24
thanks for the reply i've try that, i press e and choose linux as you suggest :/boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff but there another think in the middle of the ro  and  quiet splash there some command i guess like this :acpi_osi=Linux acpi_backlight=vendor.

i've try few way before you suggest this guide like this :sudo sed "s/\(GRUB_CMDLINE_LINUX=\)\"\"/\1\"acpi_osi=Linux acpi_backlight=vendor\"/" /etc/default/grub -i and its work but for few moment about 2 or 3 time boot after that it's back to error and the ubuntu logo is too small to read

---

### Post by Bashing-om on 2012-08-24
hnf a; 
  Wow, looks like you have been fighting with this problem for a while.
(by the way, if my english(language usage) is not perceived well, I will try to improve my communications))...
Let's do this. To establish a foundation to work from... I suggest that the kernel command line (the one with the quiet splash in the line) be edited back to a basic "nomodeset $vt7_handoff" ...be aware this is a one time boot option will not ill-effect your system. This is a text-log-in; and maybe able to catch any error codes generated; after logging in with username and pass word enter :
```
sudo service lightdm start
```if your DE is unity, else gdm vice lightdm if gnome DE.
 What we want to do is boot into ubuntu and if required find/install an appropriate graphics driver.[INDENT]kindly regarding <==BDQ
[/INDENT]

---

### Post by hnf a on 2012-08-25
where did i suppose to login to text-log-in ? tty or when booting the ubuntu?

---

### Post by Bashing-om on 2012-08-25
hnf a;
 My apologies for not being clear with my suggestion.
On my last missive, try and boot into your installed system. Edit the kernel command line.  On thinking about it, the $vt_handoff parameter may force login to the graphical user interface (GUI)//if so, let's also edit it out also.... keep the process as simple as possible.
If your system boots with only "nomodeset" will only be temporary until the system starts up and assumes control. For now I just want to get up with some kind of a user interface and pretty it up at a later point. OK ?

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by hnf a on 2012-08-25
so you mean i must make the process as simple as possible. i have change the command to nomodeset $vt_handoff

---

### Post by Bashing-om on 2012-08-25
yes ..... I am awaiting results// for my information; does leaving the $vt_handoff in the boot line boot to the GUI login screen ?

[INDENT]BDQ
[/INDENT]

---

### Post by hnf a on 2012-08-29
i'm sorry for late reply, i've try what you suggest but i'm afraid there nothing change, i have encoutered some bug in launchpad and it identified as bug #10..... I've found how to fix it but make my desktop even worst so i reinstall the ubuntu it fix the splash screen but only the shut down the startup splash screen is same. Sory for my bad english

---

### Post by Bashing-om on 2012-08-29
When you boot from the live CD with the "nomodeset" parameter, can you then continue to boot into the operating system?
If you can boot into the operating system; use the hardware drivers utility to install another graphics driver.

and no need to apologize for your english // it is done well. Any other language than one's own is difficult to master. (compared to the english language ubuntu language is easier!)
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by hnf a on 2012-09-01
i'm sorry for late reply,i've done what you suggest but i'm afraid the problem doesn't fix. few day ago i have problem with launcher and i found the solution but it just make it worst so i reinstall my ubuntu and it fix the shutdown splash screen but the startup splash screen still error,sorry for my bad english

---

### Post by Bashing-om on 2012-09-01
I do regret my inability to communicate with you.
situation: if parameter "nomodeset" is employed in the kernel boot line; You can boot into your operating system.
  a. required: edit /etc/default/grub  //to make the above change permanent.
solution:[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
  a. Study the above tutorial
  b. implement the recommended fix.


As you require further assistance, please ask.
When the graphics problem is resolved; please mark thread as solved.

[INDENT]my kindest regards <==BDQ
[/INDENT]

---

### Post by hnf a on 2012-09-03
i'm really sorry i don't mind to post the same subject twice i don't see theres 2 pages,i will try the Noapic and nolapic mode because the nomodeset is not working

---

### Post by Bashing-om on 2012-09-03
Posting twice is not an issue, However the "nomodeset" option not working is a concern.

  I was under the impression that you were able to boot into your operating system with that parameter set in the kernel boot line at the grub menu.

  I will await your further advisement.

[INDENT]respectfully <==BDQ

[/INDENT]

---

### Post by hnf a on 2012-09-15
thanks Bashing-om for the guide, now my problem is fixed by changing the graphic card to amd and until now the boot screen looks good with ubuntu text appear but not when i boot up,but its ok

---

### Post by Bashing-om on 2012-09-15
Good !

If you do not desire to see the text on your screen: put the "quiet splash" parameters back into the /etc/default/grub file ) if you do so remember to re-write the config files with sudo update-grub).

[INDENT][INDENT]regards <==BDQ
[/INDENT][/INDENT]

---

