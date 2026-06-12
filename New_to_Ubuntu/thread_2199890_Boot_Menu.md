---
title: "Boot Menu"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by br.smith99 on 2014-01-16
[FONT=arial]So recently i decided to give linux a try and heard that Ubuntu was a great starting point, with me being very uneducated in this field, i went ahead and installed ubuntu 12.04 LTS with the Wubi installer on a separate external HDD. Well within the last couple of days i have had no luck to get ubuntu working correctly at the start up! It will always provides me with an error statement when i try to load it up stating [/FONT][COLOR=#242424][FONT=arial]*** "missing or corrupted file: \ubuntu\winboot\wubildr.mbr"***[/FONT][/COLOR][COLOR=#242424][FONT=arial] although i checked the directory and the file was in the correct folder and i have tried to replace the file! I have tried to re-install ubuntu (with wubi) many times but this does not seem to work. Anyways, with my frustration towards the installation of ubuntu i went to youtube to look for solutions and found this video: [/FONT][/COLOR][http://www.youtube.com/watch?v=6_92aKSu4Es](http://www.youtube.com/watch?v=6_92aKSu4Es)[COLOR=#242424][FONT=arial] i went into the command prompt and entered "bcdedit" then "bcdedit /delete {current}" (current was my identifier code). I thought this would solve the problem but it made it worst, now i no longer see the Windows 7 boot option! so i believe when i entered those commands to delete the current identifier that deleted the windows 7 boot option! I dont think that i damaged the OS but rather deleted the boot menu option for windows 7. Since then i have no idea how to get it back. please help i am very lost and any help is very appreciated! [/FONT][/COLOR]:) I am wondering i some their is a command in ubuntu, once i install it correctly, if i can regain the windows 7 option in the Windows Boot Manager/Loader?

---

### Post by whitesmith on 2014-01-16
Have you tried disconnecting the external HDD and seeing what happens? Windows forums have tools and techniques for repairing that OS. Have you looked there? It is** not** Ubuntu that prints "missing or corrupted file: G:\ubuntu\winboot\wubildr.mbr" since Ubuntu doesn't know what is meant by "G:\" (Linux would use something like sdb1, sdc2 or some such designation.) This is of no help now, but in the future beware of geeks bearing videos! Good luck to you.

---

### Post by br.smith99 on 2014-01-16
Okay thanks for the input! Also i mistaken the error message, it didnt include the "G:" Also i dont think i have to repair the OS but simply get the Windows 7 Boot option back because i ran several memory diagnostic tests and it did not show up with any problems.

---

### Post by hakuna_matata on 2014-01-16
> [FONT=arial][COLOR=#242424]***"missing or corrupted file: G:\ubuntu\winboot\wubildr.mbr"***[/COLOR][/FONT]
This a well known error message if you try to install Ubuntu with wubi in [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") mode. The main problem is that the Windows Boot Manager for [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") is only able to load Windows. 

Official solution for UEFI: [http://www.ubuntu.com/download/deskt...ows-installer]("http://www.ubuntu.com/download/desktop/windows-installer:"):
> Please use a [64-bit flavour]("http://www.ubuntu.com/download/desktop") of Ubuntu, installed directly to its own partition 
rather than using the Windows installer.

The headline is unprecise. Windows 8 is not the real problem. It is only important if you install Windows in UEFI mode.

> [COLOR=#242424][FONT=arial]Since then i have no idea how to get it back.[/FONT][/COLOR]
e.g.: [http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm[FONT=arial][/FONT]]("http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm")
...but it is a Windows issue.

---

### Post by monkeybrain20122 on 2014-01-16
Please don't use wubi. It is no longer supported, buggy and it is not a real Ubuntu install so it is going to give you wrong impression about performance etc. Also chances are not too many people would be able to help with Wubi problems because most here don't use it.

Do a partition and do a real install, or better, since you have an external drive, just install Ubuntu there (install bootloader in the external drive, say /dev/sdb, the default is install it to your internal drive, you don't want that)

---

### Post by br.smith99 on 2014-01-16
Thank you for the helpful info i greatly Appreciate it! :D but the problem is i dont see the windows 7 option in the "Windows Boot Menu" due to the commands i ran to fix ubuntu, which were unsuccessful! All i need to know is how to get the Windows 7 option back in the boot manager!

---

### Post by oldfred on 2014-01-16
To fix Windows BCD you have to run the Windows repairs. See link above by hakuna_matata.
You need a Windows repairCD or flash drive from any version of the same 64 bit or 32 bit Windows.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by br.smith99 on 2014-01-24
> **hakuna_matata said:**
> This a well known error message if you try to install Ubuntu with wubi in [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") mode. The main problem is that the Windows Boot Manager for [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") is only able to load Windows. 

Official solution for UEFI: [http://www.ubuntu.com/download/deskt...ows-installer]("http://www.ubuntu.com/download/desktop/windows-installer:"):


The headline is unprecise. Windows 8 is not the real problem. It is only important if you install Windows in UEFI mode.


e.g.: [http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm](http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm)
...but it is a Windows issue.

[COLOR=#333333][FONT=Segoe UI][COLOR=#000000]Thank you very much for the guide but i have a problem: [/COLOR][COLOR=#000000][http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm](http://pcsupport.about.com/od/fixtheproblem/ht/rebuild-bcd-store-windows.htm) I am getting stuck on step 5: [/COLOR]*Since the BCD store exists and lists a Windows installation, you'll first have to "remove" it manually and then try to rebuild it again.*[/FONT][/COLOR]
[COLOR=#333333][FONT=Segoe UI]*[I]At the prompt, execute the bcdedit command as shown and then press **Enter:***[/I][/FONT][/COLOR]
*[I]**[B][I]bcdedit /export c:\bcdbackup***[/B][/I][/I]*[I]**[B][I][B][I]It gives me an error message saying: "The store export operation has failed. The requested system device cannot be found."***[/I][/B][/B][/I][/I]

---

### Post by hakuna_matata on 2014-01-25
First of all, good Windows fora are more helpful than Ubuntu fora, because it is not important why you deleted Windows menu entry.

Nevertheless, here is my opionion:
> **br.smith99 said:**
> *[I]**[B][I][B][I]The requested system device cannot be found.***[/I][/B][/B][/I][/I]
This means that C: doesn't exist.

Maybe, it is no problem.

Try to mount system partition as device s: and locate to s:\EFI\Microsoft
```
mountvol s: /s
s:
cd \EFI\Microsoft

```

If there are no error messages replace in every step c:\ with s: e.g.:
> bcdedit /export **s:**bcdbackup 
Note the missing backslash after s:

---

### Post by br.smith99 on 2014-01-25
Thanks for the response but it seems that it stills give me an error message about: *[I]**[B][I][B][I]"The store export operation has failed. The requested system device cannot be found." or "Invalid parameters" ***[/I][/B][/B]**[/I][/I]though [FONT=Arial, Helvetica, sans-serif][COLOR=#242424]After a bit i have tried using a system repair disc and executing the Startup repair and System Recovery/Restore but so far none of those have been able to solve the boot selection problem!  Nothing seems to work and im getting more and more worried! Maybe could i re install the OS and it will not delete my data on my drives?

[/COLOR][/FONT]

---

### Post by oldfred on 2014-01-25
It probably is Windows repairs that are needed and Boot-Repair cannot fix most of those.
But it may be best to see where you are at in detail to suggest further repairs.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by br.smith99 on 2014-01-25
How might i go about installing this Bootinfo repair disk? Sorry but i know very little. All i need is the Windows 7 Boot Selection Entry back. And im pretty sure it has to do with the commands i entered in cmd regarding bcdedit

---

### Post by oldfred on 2014-01-25
BootInfo Link has instructions on installing to Ubuntu live installer or your Ubuntu install. Or you can download a full repairCD or ISO.

But it seems like you really need Windows repairs from a Windows repair flash drive which you can make from Windows, but need access to another working copy of Windows that is same 32 or 64 bit.

Some third party Windows repair tools may also work.
       [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

 [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

---

### Post by br.smith99 on 2014-01-25
Alright just to fill you in, i dont have ubuntu installed on the computer, i already made a repair windows cd from my old computer that im using but nothing is working. I have done multiple system restores and many boot up repair tests within the windows repair cd but it is not working! all i need is the windows 7 entry back into my boot selection so i may start it up again! i know it has to do with the bcd edit commands in the cmd

---

### Post by br.smith99 on 2014-01-25
and i can also access the command prompt from the Repair CD, if that info helps?

---

### Post by hakuna_matata on 2014-01-25
> *[I]**[B][I][B][I]"Invalid parameters"***[/I][/B][/B][/I][/I]

refers to .... 
```
mountvol s: /s
```
or
```
bcdedit /export **s:**bcdbackup 			 		
```
or an other command ?

A Windows forum can't help you? :confused:

---

### Post by oldfred on 2014-01-25
Is your old computer not the same 32 or 64 bit Windows 7 as new computer. That may be part of the issue.

Then I might try some of the third party Windows repair tools.

---

### Post by br.smith99 on 2014-01-25
They are both 64 bit, I was wondering maybe if i reinstall the OS to the computer would it wipe all data from my drives? And will that new clean install of the window OS solve the bcd problem? or is their something more simple?

---

### Post by oldfred on 2014-01-25
My last Windows was XP, so I do not know. 
Most full installs erase all data.

---

### Post by br.smith99 on 2014-01-25
> **oldfred said:**
> My last Windows was XP, so I do not know. 
Most full installs erase all data.

Hmmm okay should i just contact Microsoft windows support for further help?

---

### Post by Mark Phelps on 2014-01-26
For help with Windows problems, you should really go to a Windows forum.  The Win7 forums (sevenforums.com) has a tutorial on how to use a Win7 install DVD to reinstall Win7 while retaining your apps and data.  You need to go there to view it.

---

