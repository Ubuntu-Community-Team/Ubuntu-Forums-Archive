---
title: "GRUB bootloader not working (I think?) and error message when I start Ubuntu"
date: 2017-05-21
forum: New to Ubuntu
---

### Post by adhdluke on 2017-05-21
When I installed Ubuntu 16.04 alongside Windows 10, everything went fine. No files were lost from partitioning, and Ubuntu was impressing me around every corner with how fast and beautiful MATE looks. However, when I shut off my computer for the second time after installing Ubuntu, I got an error message that said something about the bootloader or something similar. It's my fault for not taking a picture. Anyways, I got this error several times after starting my computer, and it would send me to a screen that looked similar to a simple boot menu from a motherboard. If I selected Ubuntu from this list, it would start the GRUB bootloader (assuming I'm correct on what that is) and then I could choose to start Ubuntu.
Now that isn't even a thing anymore, and my computer just boots into Windows when I start it. I have to do the shift+restart to even get into Ubuntu.
The error message that I get says: "Sorry, Ubuntu 16.04 has experienced an internal error. If you notice further problems, restart your computer."
I have had no problems at all after getting Ubuntu to boot other than this error message, and I can't copy and paste the error. It has a bunch of drop-down menus or something like that.
If anyone has any idea what the problem is, and how to get back into the normal bootloader, please help.

---

### Post by ajgreeny on 2017-05-21
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by adhdluke on 2017-05-21
When I run the tool to create a system report, it doesn't give me the link. It just give me this: [http://paste2.org/](http://paste2.org/)

---

### Post by oldfred on 2017-05-21
You must be third or fourth person that says the only got the paste bin site, not an entry. But others get it to work.
How exactly did you use Boot-Repair. What version? The older ISO or use ppa to install into Ubuntu's live installer?
We may need to file a bug report on Boot-Repair.

---

### Post by shridhar-kapshikar on 2017-05-22
You can refer to below link,
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Else, if you would like to disable these annoying popups[COLOR=#242729][FONT=Arial] please follow below steps,

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Check the status:[/FONT][/COLOR]
sudo systemctl status apport
[COLOR=#242729][FONT=Arial]Edit the /etc/default/apport file:[/FONT][/COLOR]
sudo nano /etc/default/apport
[COLOR=#242729][FONT=Arial]Change the value enabled=1 to enabled=0[/FONT][/COLOR]

---

### Post by adhdluke on 2017-05-22
I just followed the steps to install boot-repair from the terminal.

[CODE]
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

---

### Post by SuperFreak on 2017-05-22
Out of curiosity I tried Boot Repair on my PC that has not been changed and produced URLs of Boot Summaries without issue. This time there was no URL but it produced a ***text file*** with a boot summary

---

### Post by oldfred on 2017-05-22
Added bug report to Boot-Repair.
Seem related to creation of pastebin site.
[https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778)

Unknown website, please post a bugreport to request this pastebin to be added ([http://paste.ubuntu.com](http://paste.ubuntu.com))
[EMAIL="SET@_progressbar1.pulse"]SET@_progressbar1.pulse[/EMAIL]()
Unknown website, please post a bugreport to request this pastebin to be added ([http://paste.debian.net](http://paste.debian.net))

If you add that it also affects you, it helps highlight that a fix is needed.

If you look in /var/log you can drill down to the report.
Mine was at:
/var/log/boot-sav/log

---

### Post by adhdluke on 2017-05-23
I found the log file. (I think.)

I copied it and created a pastebin for it.

[https://pastebin.com/LCpWLx6u](https://pastebin.com/LCpWLx6u)

---

### Post by oldfred on 2017-05-23
You show that you have an HP. Which is one problem.
And Secure Boot on, often easier with it off, but you do have signed kernels, so it should work with it on.
But you then can only boot from UEFI boot menu.

Grub only boots Windows that is working. And Secure boot must be off as chain of signed bits & pieces is somehow lost.
So you then have to boot Windows from UEFI boot menu.

Grub also only boots working Windows, if secure boot is off. So if Windows needs chkdsk or is hibernated, it would not boot Windows and then best to have Windows repair disk or full installer with repair console. Windows also will turn fast start/hibernation back on with major updates.

You can ignore the warning from Boot-Repair on far from start of disk. That is for older BIOS systems using IDE that only can boot from files located in first 137GB of hard drive. Not seen that issue with any newer UEFI based system and AHCI, not IDE configuration on drive.

I would turn UEFI Secure Boot off, but still boot in UEFI mode. 
I might run Boot-Repair's advanced mode and tick the 'use the standard efi file'. That copies shimx64.efi to /EFI/Boot/bootx64.efi which is a fallback or hard drive boot. Below are several threads where users manually copied files, before Boot-Repair did it, Which you can also do.
You may also need an UEFI entry to use that. Many HPs already have a hard drive boot entry that works. Current bootx64.efi is just a copy of the Windows .efi boot file.

Some just use the UEFI one time boot entry to boot the ubuntu entry when they want Ubuntu. That should work.

If you do run Boot-Repair it will see all the .efi HP utility files in the ESP and think you want to boot them from grub menu. It adds a new 25_custom which adds all those as new grub boot options. Most delete or remove the 25_custom.

Also in link in my signature below.
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114) 

      
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]
[/URL]

---

### Post by adhdluke on 2017-05-25
I can't get secure boot to turn off. I get to the BIOS screen and disable it, save, and exit, but it doesn't actually turn off. All the other changes save, but this one doesn't. When I go back, it just says secure boot is on again.

---

### Post by oldfred on 2017-05-25
Do you have latest UEFI/BIOS from HP for your model?
Vendors often have issues that they have to fix. May not be in list of fixes either.

What model HP is your system?

---

### Post by adhdluke on 2017-05-27
I think it's a Pavilion 17 Laptop, not sure the exact model number.

---

### Post by oldfred on 2017-05-27
Microsoft has required vendors to allow users to turn off UEFI Secure Boot.
So if an issue check HPs site and if nothing their contact them, just do not mention Linux as then they immediately say they do not support Linux.

---

