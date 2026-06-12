---
title: "Want to remove Windows 7 bootloader after Grub install"
date: 2015-08-11
forum: New to Ubuntu
---

### Post by Alistair George on 2015-08-11
Hi I had Linux installed with Grub2 on sda, which I like. Then installed Windows 7 on extended partion, sda which stuffed up the Grub which Ive managed to sort.

Grub comes up with Linux and Windoze options if I choose Windoze(7) there follows Windows Bootloader as well.
So there will be Grub and Windows bootloader on sda.

Is there any method to disable the second bootloader after Grub? Its no big deal but a tad annoying as I used to have Grub2/Linux and Windows 7 with no annoying second Windows bootloader until Windows needed reinstalling.

I thought it could be done within MSconfig but boot options dont seem to allow disable bootloader.

---

### Post by sandyd on 2015-08-11
Sometimes, when windows is reinstalled, windows thinks there are multiple versions and just creates multiple boot entries in the windows boot menu
Run msconfig, then go to the boot tab.
There, select the entry that you are actually supposed to be booting from, and click 'Set as Default". Then, set timeout to 0, and set boot settings to permanant after you have verified it is working on a reboot.

---

### Post by Alistair George on 2015-08-11
> **sandyd said:**
> Sometimes, when windows is reinstalled, windows thinks there are multiple versions and just creates multiple boot entries in the windows boot menu
Run msconfig, then go to the boot tab.
There, select the entry that you are actually supposed to be booting from, and click 'Set as Default". Then, set timeout to 0, and set boot settings to permanant after you have verified it is working on a reboot.

Thanks so much but I did say Id been to msconfig:
In Windows 7 you are not allowed to make the bootloader less than 3 seconds; 0 is unaccepted. This means the bootloader screen is still invasive for longer than 3 seconds even if set to 3.

Any other suggestions appreciated.

> **sandyd said:**
> Sometimes, when windows is reinstalled, windows thinks there are multiple versions and just creates multiple boot entries in the windows boot menu
Run msconfig, then go to the boot tab.
There, select the entry that you are actually supposed to be booting from, and click 'Set as Default". Then, set timeout to 0, and set boot settings to permanant after you have verified it is working on a reboot.

Thanks so much but I did say Id been to msconfig:
In Windows 7 you are not allowed to make the bootloader less than 3 seconds; 0 is unaccepted. This means the bootloader screen is still invasive for longer than 3 seconds even if set to 3.

Any other suggestions appreciated.

> **sandyd said:**
> Sometimes, when windows is reinstalled, windows thinks there are multiple versions and just creates multiple boot entries in the windows boot menu
Run msconfig, then go to the boot tab.
There, select the entry that you are actually supposed to be booting from, and click 'Set as Default". Then, set timeout to 0, and set boot settings to permanant after you have verified it is working on a reboot.

Thanks so much but I did say Id been to msconfig:
In Windows 7 you are not allowed to make the bootloader less than 3 seconds; 0 is unaccepted. This means the bootloader screen is still invasive for longer than 3 seconds even if set to 3.

Any other suggestions appreciated.

---

### Post by sandyd on 2015-08-11
My bad, the option to not display the menu are somewhere else, not in msconfig

Right click on "my computer", choose properties, go to 
Advanced System Settings -> Advanced -> Startup & Recovery, and uncheck "Time to display list of operating systems". Be sure that you already have the right OS selected above before restarting.

---

### Post by Alistair George on 2015-08-12
> **sandyd said:**
> My bad, the option to not display the menu are somewhere else, not in msconfig

Right click on "my computer", choose properties, go to 
Advanced System Settings -> Advanced -> Startup & Recovery, and uncheck "Time to display list of operating systems". Be sure that you already have the right OS selected above before restarting.

What actually happens is you have to check the 'Time to display............' and adjust it to 0, then OS disables the checkbox, but shows the figure '0'

Windows is so annoying sometimes, even that does not work!! Im getting a Windows bootloader which is counting down from about 30 seconds. Starting to wonder if this bootloader is a remnant of the previous Windows 7 distro.

---

### Post by CantankRus on 2015-08-12
Not sure about Windows7 but my XP install has a boot.ini file at the root of my XP partition.
I have 2 XP installs so I see the bootloader for [COLOR="#FF0000"]3[/COLOR] secs, whereupon after that period, the install set as default boots.
If I remove the second install listed under "**[operating systems]**", I see no bootlader and just boots directly into [COLOR="#DAA520"]WINDOWS="SOF2"[/COLOR].

My boot.ini
```
[boot loader]
redirect=usebiossettings
redirectbaudrate=
[COLOR="#FF0000"]timeout=3[/COLOR]
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
**[operating systems]**
multi(0)disk(0)rdisk(0)partition(3)\[COLOR="#DAA520"]WINDOWS="SOF2"[/COLOR] /noexecute=optin /fastdetect /usepmtimer
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect /usepmtimer
```

You will find the boot.ini at the root of your Windows partition.
You can also view, edit and check boot paths by running **msconfig** in Windows.

How many listings do you have under "**[operating systems]**"?

I stopped buying MS products at XP so may be different.
Here's a link to Fixing W7 boot issues. [**_[COLOR="#B22222"]how-to-manually-repair-windows-7-boot-loader-problems[/COLOR]_**]("http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/")
If you do something like this you will probably have to reinstall grub.

---

### Post by Alistair George on 2015-08-12
Hi I think thats particular to XP as there is no Boot.ini in Windows 7.
The bootmanager is showing 2 instances of Win 7, there is only one. I have tried removing the second one in MSIconfig but makes no difference.

Otherwise you gave me another idea which did not work:
C:\Users\Alistair>Bcdedit
The boot configuration data store could not be opened.
Access is denied.

---

### Post by CantankRus on 2015-08-12
Can't help much then as my Windows knowledge stops at XP.
I would be googling for "fix boot Windows 7" as grub appears to be doing it's job.

---

### Post by Alistair George on 2015-08-12
Yes. Thanks for help though. Its a minor issue; if I manage to sort will post solved here.

---

