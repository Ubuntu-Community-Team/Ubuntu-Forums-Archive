---
title: "Dual boot (Win7+Ubuntu14.04): Can't boot Windows7"
date: 2015-01-26
forum: New to Ubuntu
---

### Post by Lalaith on 2015-01-26
Hello all, 

I recently reinstalled Windows 7 and after it, reinstalled Ubuntu to have my Asus U31SD in dual boot.
I booted once into Windos 7, then I went to Ubuntu. Today I tried to boot Win again but it can't boot: windows asks me to choose between booting on several Safe Modes or start Windows normally. In both "Safe Mode" and "start normally" gets stuck saying that some system file may be corrupted and restarts the computer.
My laptop doesn't have CD reader, so can't simply put the windows live CD to repair windows!
I don't have a clue what is happening because the only time I booted into Win was just to check I could boot, and shut down the computer again.

So I thought it would be because of grub: I followed the steps from the Community Help wiki: Boot Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)), but still can't boot into Win.
These are the results from the Boot-Repair:
[http://paste.ubuntu.com/9887673/](http://paste.ubuntu.com/9887673/)


Any help will be much appreciated :)

---

### Post by Mark Phelps on 2015-01-27
Looks like GRUB is defaulting to boot from the first Windows partition -- and that is your Recovery partition.

The second partition has the boot flag and that is your OS partition.  Try booting from that and seeing if that makes a difference.

---

### Post by Lalaith on 2015-01-27
I solved the issue, I'll post here what I did in case is useful to anyone else.

Thanks for the suggestion Mark Phelps, but I could access Windows 7 and Windows Recovery Environment from Grub, so the problem was not where Grub is pointing to. 
That's why I suspected that the problem was not in the Grub or Ubuntu side.

So what I did:
Since windows 7 was a new installation, I simply booted the Windows Recovery Environment and re-install Windows 7 in the same partition again. Then, when I first boot windows I got the System Preparation Tool 3.14. 
(here I followed the steps in [http://forum.computerbild.de/windows-7/system-preparation-tool-3-14-a_96428.html](http://forum.computerbild.de/windows-7/system-preparation-tool-3-14-a_96428.html) . Basically: Apply OOBE without "Generalize" and with Shut-down Options: Reboot).
My computer rebooted aftwer a while and I was able to configure Windows for the end-user. I ***guess*** that failing to do this step was preventing Windows from installing all necessary "System registry files". (A list of files that should be there: [http://answers.microsoft.com/en-us/windows/forum/windows_vista-system/windows-failed-to-load-because-the-system-registry/7a529e93-0397-478d-974a-129e11aebac5](http://answers.microsoft.com/en-us/windows/forum/windows_vista-system/windows-failed-to-load-because-the-system-registry/7a529e93-0397-478d-974a-129e11aebac5))

---

