---
title: "Ubuntu 16.04.5 boots into &quot;minimal bash-like editing&quot; screen"
date: 2018-09-03
forum: New to Ubuntu
---

### Post by mykeyblader on 2018-09-03
I'm a complete noob when I comes to Ubuntu. I can type in a command line and google things in the hopes of finding answers to my problems but I've run into a problem I'm not sure I can fix.


I just bought a Win 10 laptop and shrunk the C partition and made a D partition to make room for Ubuntu(a 500GB partition so there is plenty of room) and used Wubi to install Ubuntu 16.04.5 on the D drive. It says that I have to restart to finish the action so I reboot my laptop.

On the first reboot after install, I get a SecureBoot issue so I disable SecureBoot in the UEFI BIOS, and I also change the boot order so Ubuntu boots first.

Now when I reboot Ubuntu it gives me a black screen with a command line that says something along the lines of 

GNU GRUB version *something*
Minimal bash-like editing is supported. TAB lists possible file or device completions

I googled the problem in search of a solution, and from what I understand the error has something to do with there being no OS to boot to, and that recovery media is required. However I didn't use recovery media, I used Wubi. 

I can still boot to Windows. Is there anything I can do to fix this problem?

I really appreciate all the help/advice you can give me

---

### Post by Impavidus on 2018-09-03
Wubi is dead. It has been dead for years, mostly because it's incompatible with UEFI, which is the standard way to install Windows since Windows 8. At least, I think that was the problem. So, no, you can't install Ubuntu that way. Wubi should have left an uninstaller in Windows. Try to use that. Then consider installing Ubuntu as a prober dual boot or in a virtual machine.

Anyway, Wubi was limited to 30GB and installed in a file (a virtual partition) on an NTFS partition. Making a 500GB partition for it is a bit pointless. The whole idea behind Wubi was that you could install Ubuntu without changing any partitions, allowing for easy removal.

[https://ubuntuforums.org/showthread.php?t=2229766](https://ubuntuforums.org/showthread.php?t=2229766)

---

