---
title: "Installed alongside Windows 8 but can't get back to Windows...?"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by alexp76 on 2013-03-30
Hello, first post here so be kind :-)

I have just installed Ubuntu 12.10 alongside Windows 8 successfully, having followed guidance on this forum. However, the links to Windows in what i think must be GRUB (start up screen?) don't work. 

I have gone back into Ubuntu and run the disk check thingummy, and it gives me this URL:

[http://paste.ubuntu.com/5661574](http://paste.ubuntu.com/5661574)

Can anyone help please?

Alex.

---

### Post by oldfred on 2013-03-30
So does Ubuntu boot ok? And you get grub menu.
This entry should work.
 > menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root ECFB-D799
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

But you may need secure boot on. 
Some systems work with secure boot on or off. Others require it on to boot Windows. 

And some only boot the Windows bootmgrw.efi file and Boot-Repair has to rename files as a work around. But if you can boot Ubuntu you should not need the rename function.

---

### Post by alexp76 on 2013-03-30
Put that into Terminal, and it gives me a bash error?

Since last posted, tried turning off secure boot, and doing another boot-repair, which gives this message:

Please write on a paper the following URL:
[http://paste.ubuntu.com/5662024/](http://paste.ubuntu.com/5662024/)

If  you still experience boot problems, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!

The boot files of [The OS now in use - Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Not sure i understand either of these requirements...

---

### Post by oldfred on 2013-03-30
That should just be the Windows entry in your grub menu. You probably just see first line or the menuentry that is in quotes. What happens when you try that entry in grub? With both secure boot on and with it off?

---

### Post by alexp76 on 2013-03-30
Thank you Old Fred, sorted it out by turning off the secure boot and running the boot-repair. I still have 4 GRUB options though, is it possible to streamline this down?<br><br>And, apologies if your last post is telling me how to do this...?

---

### Post by oldfred on 2013-03-30
Your BootInfo report only showed two entries. Did grub2's os-prober run and add its entries. They will never work as they are the old BIOS boot entries that do not work with  efi. Bug report is now getting old, but still not fixed.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

You can turn off os-prober and manually edit 25_custom to remove extra entries if you want. Post back for details if you need them.

---

