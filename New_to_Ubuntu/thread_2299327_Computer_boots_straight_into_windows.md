---
title: "Computer boots straight into windows"
date: 2015-10-17
forum: New to Ubuntu
---

### Post by tadeusz3 on 2015-10-17
[FONT=arial]Hi![/FONT][FONT=arial]
So I wanted to install Ubuntu alongside Windows 10 on my HP laptop. I installed it from a live USB but after the installation was successfully completed and I rebooted the computer and Windows launched immediately. I inserted the USB and rebooted the laptop again, selecting the "Try Ubuntu without installing" option  and downloaded boot-repair. I ran the repair with the "purge Grub before installing" option selected and followed all the steps successfully but when I restarted my computer it went straight to windows again. I also tried running the *bcdedit /set {bootmgr} path\EFI\ubuntu\shimx64.efi* command that boot-repair told me to but received a message :[/FONT]
[FONT=arial]"The element data type specified is not recognized, or does not apply to the specified entry." [/FONT]
[FONT=arial]My pastebin link: [http://paste.ubuntu.com/12822613/](http://paste.ubuntu.com/12822613/)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I would be very grateful if anyone could tell me how to open ubuntu without the USB.[/FONT]

---

### Post by sudodus on 2015-10-17
Welcome to the Ubuntu Forums :-)

There is no bootloader in your internal drive.

[quote=Boot Repair's bootinfo]=================== Advices
Please disable SecureBoot in the BIOS. Then try again.Do you want to continue?

...

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi[/quote]

Does it help according to these tips?

---

### Post by tadeusz3 on 2015-10-17
I have disabled SecureBoot, I have set the boot order to start with "os boot manager", and when i tried this command again: bcdedit /set {bootmgr} path\set\EFI\ubuntu\shimx64.efi even though it said that the operation was completed successfully, when I restarted the computer it booted straight into windows again.

> There is no bootloader in your internal drive.

Shouldn't boot-repair have fixed this? Is there any way I can install a bootloader manually?

[COLOR=#000000][I]

[/I][/COLOR]

---

### Post by sudodus on 2015-10-17
In UEFI mode you need no bootloader at the head of the drive, if things are set for correctly. See this link

[http://ubuntuforums.org/showthread.php?p=13372169#post13372169](http://ubuntuforums.org/showthread.php?p=13372169#post13372169)

I would think boot-repair should fix it. Have you shut off all hibernation and fast boot in Windows?

---

### Post by tadeusz3 on 2015-10-17
I disabled hibernation and fast boot as you said. I'm very sorry, but i don't quite understand the link you posted. Could you please explain how this information could help me? Unfortunately I'm not that great with computers.

---

### Post by sudodus on 2015-10-17
It helps a lot that you have supplied the BootInfo report.

I have no really good idea how to help, but I know that there are other people at the Ubuntu Forums who know more than I how to solve this kind of problems. Let us hope one of them will find your thread soon and help you.

---

### Post by yancek on 2015-10-17
Check the microsoft site below explaining how to disable hibernate to make sure you did it correctly.  You might try a full shut down after the change and see if that has any effect.  I don't use windows or UEFI so can't suggest anything else.

[https://support.microsoft.com/en-us/kb/920730](https://support.microsoft.com/en-us/kb/920730)

---

### Post by chopra on 2015-10-17
Are you able to remove the battery from the machine? (you may have to unscrew it) If so, you can reinsert it and restart. If disabling fast boot and hibernate didn't help, this would be something to try.  If it works properly after this, it means fast boot or hibernate isn't turned off properly.  If it doesn't, I don't know what the problem could be.

---

### Post by Geoffrey_Arndt on 2015-10-18
This is worth a try . . . scroll down to the answer for posters query.   

[http://askubuntu.com/questions/554690/hp-uefi-doesnt-boot-ubuntu-automatically](http://askubuntu.com/questions/554690/hp-uefi-doesnt-boot-ubuntu-automatically)

(This is worth saving for other folks also having HP computers, which do a ****-poor implementation of the UEFI standards).   

And HP does a ton of Unix/Linux business . .

Note:  in above thread, read the link at the Launchpad thread - lot's of possibilities for HP machines.

More Info here:   [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win)

---

### Post by tadeusz3 on 2015-10-18
> I have no really good idea how to help, but I know that there are other people at the Ubuntu Forums who know more than I how to solve this kind of problems. Let us hope one of them will find your thread soon and help you.
Thank you. I'm very grateful for your advice.

> Check the microsoft site below explaining how to disable hibernate to make sure you did it correctly. You might try a full shut down after the change and see if that has any effect. I don't use windows or UEFI so can't suggest anything else.

Those are the steps I followed, unfortunately it didn't help.

> Are you able to remove the battery from the machine? (you may have to unscrew it) If so, you can reinsert it and restart. If disabling fast boot and hibernate didn't help, this would be something to try. If it works properly after this, it means fast boot or hibernate isn't turned off properly
I did this and it didn't seem to make any difference.

I only just realised that I can boot into ubuntu using F9 in startup :oops:, so I'm sorry for wasting your time. While this isn't the perfect solution I don't mind doing this a few times a day, so I'm going to mark this thread as solved.
I'm very grateful for all the great advice you all offered me and I'm looking forward to using Ubuntu and posting on these forums :)

---

### Post by sudodus on 2015-10-18
Congratulations to a working solution (not perfect but working) :KS

Thank you for sharing the solution.

---

### Post by Geoffrey_Arndt on 2015-10-18
Yes, the one-time uefi firmware method.   HP has the UEFI locked-down to the point that this may be the only method ever to boot Ubuntu (or ANY non MS operating system).    There are other solutions BUT, MS updates can and will re-write the efi bootloader files per information at "Ask Ubuntu".

Glad you found the solution for your pc ! ):P

---

