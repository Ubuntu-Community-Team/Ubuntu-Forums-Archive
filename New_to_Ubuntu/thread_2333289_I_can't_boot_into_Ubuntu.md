---
title: "I can't boot into Ubuntu"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by kimsk132 on 2016-08-08
Dear community,

Ubuntu worked fine last night until I ran software update and restarted it. It just disappeared from my boot options. I tried adding the grubx64 efi file to my BIOS and chose to boot from it, and it still booted right into Windows. I also tried boot-repair using a USB flash drive. It didn't work. Here's the paste bin I got:
[http://paste.ubuntu.com/22740098/](http://paste.ubuntu.com/22740098/)
My machine: Acer Aspire E5-473G-785H
Any help would be appreciated.

Thank you.

Edit: I disabled Secure Boot, removed the EFI entry, and added the entry back again. Now it works even after I re-enable Secure Boot! But I have a lot of extra options in GRUB I'm pretty sure I don't need. Why is that? Is there anyway I can restore GRUB back to what it was without those extra options?

---

### Post by oldfred on 2016-08-09
With Acer you have to enable "trust" on the .efi files.

It looks like Boot-Repair saw a variety of additional .efi files in the ESP - efi system partition and created a new 25_custom boot file. Those all were created by Boot-Repair and you can edit out any you do not want or even all of them.

You cannot boot Windows from grub if secure boot is on (unless they finally have fixed it?)

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 


 [http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)

---

### Post by kimsk132 on 2016-08-09
Dear oldfred,

Yes, I can boot into Windows from grub even with secure boot on. There was no problem until I ran that software update.
I took a look at that 25_custom file, and everything in it seems to represent all the extra options I don't need. Can I just delete the file all together?
And how do I restore the backup should I need those options?

Thank you.

---

### Post by oldfred on 2016-08-09
You can turn off execute bit, then turn that back on later if desired.
sudo chmod a-x /etc/grub.d/25_custom
sudo chmod a+x /etc/grub.d/25_custom
or
Just rename it to 25_custom or rerun Boot-Repair.
sudo mv /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
Restore
sudo mv /etc/grub.d/bkp25_custom /etc/grub.d/25_custom

And 
then run this to include entries into grub menu.
sudo update-grub

---

### Post by kimsk132 on 2016-08-11
It works like a charm! Thank you, Fred.

---

