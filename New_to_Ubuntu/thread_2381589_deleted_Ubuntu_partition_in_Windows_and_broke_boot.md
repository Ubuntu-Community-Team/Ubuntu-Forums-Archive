---
title: "deleted Ubuntu partition in Windows and broke boot..."
date: 2018-01-02
forum: New to Ubuntu
---

### Post by hughc2 on 2018-01-02
I recently bought an Lenovo ideapad 320. I'm not a fan of Windows so I set it us as a dual boot - Windows 10 and Ubuntu 16.04.3 LTS. This worked fine, but I pretty soon realised I was using Windows more than Ubuntu. And then I started getting notifications in Windows telling me I was running out of disk space. So I decided I would delete Ubuntu and just run Windows...

Foolishly I didn't look up the best way to do this and just went ahead and deleted the Ubuntu partitions in disk manager.

Now the laptop won't boot. When I switch it on I get to a "GNU GRUB" screen. I've had a look around online on this forum and elsewhere but can't find any instructions about how to fix this...

I have a Windows 10 boot USB and an Ubuntu boot USB. No disk drive in the ideapad.

Please can someone give me clear instructions about how to fix this

Many thanks

---

### Post by hughc2 on 2018-01-02
[COLOR=#111111][FONT=Ubuntu]Aha! [/FONT][/COLOR][https://askubuntu.com/a/861292/775209](https://askubuntu.com/a/861292/775209)[COLOR=#111111][FONT=Ubuntu]

"[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]If you type [/FONT][/COLOR]exit[COLOR=#111111][FONT=Ubuntu] it will then take you back to the options where you can select your Windows Partition.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Doing this will allow you to access your Windows OS and use it as normal temporaraly, until you can re-install the Kernals and unistall Ubuntu properly.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]"

[/FONT][/COLOR]This works for me!

Next question is - can anyone advise me on how to [COLOR=#111111][FONT=Ubuntu]re-install the Kernals and unistall Ubuntu properly?

Thanks[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-01-02
That will work only if your machine boots using UEFI, so if you get nowhere with that above option go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and I believe if using BIOS also has an option in "Advanced". to restore a basic Windows Bootloader.

---

### Post by yancek on 2018-01-02
If you wanted to remove Ubuntu Linux and just use windows, you've gone about it in a backwards fashion as you have learned.  The first thing you would need to do is to set the windows bootloader to first priority in your BIOS BEFORE removing Ubuntu.  From your post, I would guess that you had both windows 10 and Ubuntu installed UEFI and were using the Ubuntu Grub EFI bootloader to boot both.   Since you have deleted the Grub files that no longer works.

Have you tried booting and entering the BIOS and setting windows first?  Generally there is an option under the Boot tab for Windows Boot Manager or similar.  If you haven't resolved this, getting and running boot info as suggested is the next best step as long as you do NOT try to make any changes.

---

### Post by 0N3 on 2018-01-03
I'm guessing you had secure boot disabled in your bios to boot Ubuntu and Windows? Turn on secure boot should boot into your windows.

---

