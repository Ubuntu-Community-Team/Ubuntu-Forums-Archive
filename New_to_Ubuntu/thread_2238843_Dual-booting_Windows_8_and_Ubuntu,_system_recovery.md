---
title: "Dual-booting Windows 8 and Ubuntu, system recovery on Windows,now Windows won't start"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by Lukas_Engedal on 2014-08-10
First of all, I am well aware that there are probably dozens of posts on the forum with people having similar problems, but second of all, I am more or less a complete noob when it comes to the more advanced aspects of computers such as dual booting and the whole startup process. So although I have already looked through dozens of similar posts and tried out a range of different things, there are always differences between what I'm seeing on my computer and what I read on the forum, and blindly following the advice from other posts on the forum hasn't really fixed my problem so far, so I was hoping someone could help me with my specific situation.

I am on a Lenovo Z500 laptop, which came with Windows 8 preinstalled when I bought it about 2 years ago. As far as I recall I then created a new partition on which I installed Ubuntu, blindly following instructions I problably found on this very forum. Following that, every time i booted up the computer I was greeted with the grub start up screen with like 7 or 8 different options, and by trial and error i discovered that choosing the "Windows Boot UEFI Recovery" option started Windows 8, while the other Windows 8 options just led to various error messages.
Everything was fine then untill today, when I got tired of my computer being so slow and decided to do a system recovery on Windows using Lenovo's One-Key recovery system to restore Windows to the state it was in when I bought the computer. I thought that would restore my computer to it's original state, thereby deleting Ubuntu, but that unfortunately did not happen. When i start up my computer now, all of the Windows options on the grub screen leads to error messages, and even Ubuntu gives error messages before starting up.
So therefore I was hoping you could help me fix my computer so that I can actually start Windows, and maybe also give me some advice on how to correctly get rid of Ubuntu again, now that I don't need it anymore.

The Windows options I can choose between, and corresponding errors, on the grub start-up screen is:

Windows UEFI recovery bkpbootmgfw.efi:
Error: no such device: C26C-DC81
Error: file '/EFI/Microsoft/Boot/bkpbootmgfw.efi' not found

Windows Boot UEFI recovery:
Error: no such device: C26C-DC81
Error: file '/EFI/Boot/bkpbootmgfw.efi' not found

Windows Recovery Environment (loader) (on /dev/sda3):
Error: can't find command 'drivemap'
Error: invalid EFI file path

Windows 8 (loader) (on /dev/sda5):
error: no such device 58A47257A4723798
Error: can't find command 'drivemap'
Error: invalid EFI file path

Notably I've tried using boot-repair, which gives me the following error message and link:
'grub-efi-amd64-signed purge cancelled. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]'
[http://paste.ubuntu.com/8008585/](http://paste.ubuntu.com/8008585/)

If there's any more information you need let me know, I really hope someone here can help me.
Thanks for any help in advance.

/Lukas

---

### Post by oldfred on 2014-08-10
Are you still running 12.10?
You should all sorts of errors from your sources.list with quantel versions. Those repositories are now closed.
 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

It does look like you had run Boot-Repair's buggy UEFI. With older versions it allowed Windows to boot as grub2's os-prober did not find UEFI installs and it was a work around for many UEFI systems where vendor has modified UEFI to only boot Windows.

Your Windows menu entry to boot on sda5 would be a BIOS type boot that your old grub2 os-prober incorrectly found. It would never have worked with UEFI. Fixed with newer versions of grub2.

Can you directly boot Windows from UEFI menu? (not grub?)

If you can boot both Windows & Ubuntu you do not need rename and we can give you just an efi boot entry for Windows that is like what the new os-prober creates. But you really should update to a current version of Ubuntu.

---

