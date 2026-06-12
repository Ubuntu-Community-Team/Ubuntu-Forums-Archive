---
title: "Uninstall of Ubuntu and removal of GRUB"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by hellopaul on 2008-10-10
Hello.

I am in the process of uninstalling Ubuntu on a dual-boot Ubuntu/Vista machine. I am not an Ubuntu or Vista expert (it's not my machine - I mostly use a Mac). After reading a few of the threads on uninstalling Ubuntu, most of which involved downloading strange bits of software with no explanation and using them to modify my hard disc in strange ways, I decided to nose through the disc management control panels in Windows, and just deleted the partitions containing the ubuntu installation (I hope).

When I restarted, the usual GRUB thing loaded, but just reported an 'error 22' and sat there, doing nothing...presumably looking for an Ubuntu installation to load. How can I remove GRUB (now that no OS loads at all:confused:) and (if it's still there!) load up Vista? If I've fried my Vista OS, it's not THAT much of a disaster - it's a fairly new machine (with not much in the way of valuable files on it) and I still have the recovery DVD - which (very unhelpfully) just has the potential to wipe the HD and reinstall Vista. I rather hoped it might have some form of disc tools on it, but that's apparently too much to ask of Windows and Toshiba.

Well, I'm hoping there's just some easy way I can get to a command prompt or something before GRUB loads, type a few commands and make everything better. Maybe. Any suggestions? Please?! It's my wife's computer and it was my idea to install Ubuntu instead of Vista (it's faster, leaner, more secure etc.etc.) but won't work with the USB modem she has (all right - it MIGHT work if I spend many hours downloading and installing patches and typing obscure code) so it's back to lardy Vista for now. I hope. She's not happy that I've (maybe) killed her machine.

---

### Post by kellemes on 2008-10-10
You have a vista installation disc?
If so.. have you tried this?
```
1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr, and then press ENTER.
```

There is nothing wrong with your Vista install, you only need to rewrite the MBR with the Windows bootloader..

---

### Post by hellopaul on 2008-10-10
Ah, kellemes, if only it was so easy! (But thank you very much for your very prompt suggestions anyway!)

The only disc I have is a Toshiba 'recovery disc' which does not give me any of these options - it really seems to be a worst case scenario disc - it just wants to erase everything and put the machine back to the exact state it was in when it left the factory. It gives the reassuring message "WARNING - your hard disk will be completely erased!". Helpful.

I do have (slow) internet access (obviously or I wouldn't be submitting this!) and can download/burn CDs/DVDs, so if anyone knows of a magic cure I can download, please tell me!

---

### Post by lykwydchykyn on 2008-10-10
I believe there is a program on the ubuntu boot cd called mbr, which if memory serves is supposed to write a windows-style master boot record.  

The testdisk program also might work.  If these are not on the Ubuntu disc, they are probably on this one:

[http://www.sysresccd.org](http://www.sysresccd.org)

---

### Post by SunnyRabbiera on 2008-10-10
Say what is this USB modem you are having issues with?
Perhaps we could help you fix it.

---

### Post by estyles on 2008-10-10
If worst comes to worst, you can reinstall grub, and make a small grub partition (your problem is that you deleted grub, but it is still installed to the mbr, which means that when your computer starts up, it looks for your grub files to tell it how to load, and doesn't find them because you've deleted them).  Then you can modify the menu.lst to include Windows Vista as the only option, set the menu to hide on startup, and put a timeout of 0 seconds.  That will get you where you need to go.

If your other options aren't available/don't work, then it should be simply enough to reinstall grub from a Live CD.  Post here if you want more detailed instructions, and either I can post it when I have more time and access to my Ubuntu machine, or someone else can post it...  It's not terribly difficult.

---

### Post by kellemes on 2008-10-11
[Super Grub Disk]("http://www.supergrubdisk.org/") to the rescue!
[How to remove Grub and fix Windows boot.]("http://www.supergrubdisk.org/wiki/UninstallGRUB")

You should download the iso, burn the iso, and boot the pc using this disk. It's a pretty cool toy.

---

