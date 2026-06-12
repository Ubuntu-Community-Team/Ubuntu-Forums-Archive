---
title: "Acer Aspeire ES-132 cannot able to install kubuntu"
date: 2017-01-02
forum: New to Ubuntu
---

### Post by prasadk77 on 2017-01-02
Hi 
I have Acer Aspire ES-132 laptop and i tried to install ubuntu as well as kubuntu on the same. The installation was successful but after rebooting i can get grub menu. 

I tried changing bios option secure boot Enable/Disable but same issue. 

Can anyone please help. 

Also the installation is very very slow.

---

### Post by Autodave on 2017-01-02
What are the specs of your machine?  Are you installing from a USB or disc?

When you say that the installation was slow, approx. how long did it take?

---

### Post by oldfred on 2017-01-02
All Acer have a unique UEFI requirement of setting an UEFI password and enabling "trust" on the ubuntu/grub .efi boot files from within UEFI.

Also some versions mention needing to downgrade UEFI, but newer ones say very newest UEFI from Acer works. So make sure you have newest UEFI from Acer.

       Acer Aspire R5-417T
[https://ubuntuforums.org/showthread.php?t=2346815](https://ubuntuforums.org/showthread.php?t=2346815)
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
   Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162)
cat /proc/cpuinfo  | grep 'name'| uniq
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by prasadk77 on 2017-01-03
I have Acer Aspire ES1-132-C5UF laptop which is newly launched. Its N3350 processor with 2gb ram and 500gb hdd. Bios doesnt have any option as UEFi. Only secure boot Enable/Disable option is there.

Also find attached screenshot of the bios for your reference.

I tried installing from USB and CD both ways it is very slow. 
 The installation was successful but after rebooting i can NOT get grub menu. ( Sorry in my first post i have not written NOT)
After rebooting it says no bootable device found

---

### Post by oldfred on 2017-01-03
If you click on the Set Supervisory Password and add a password, does it then open more entries?
Is v1.08 the newest UEFI from Acer for your machine?

---

### Post by prasadk77 on 2017-01-04
Yes V1.08 is latest.

I did set supervisor password but options available is only to change secure boot to enable and disable

---

### Post by oldfred on 2017-01-04
After you set password, you do not get extra lines like this?
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431) 

About all I can suggest is contact Acer. But generally first level help desk will say they just support Windows.

---

### Post by fpl2 on 2017-01-15
I had the same issue with the Acer ES1-132-C0VW. 
I contacted Acer and they told me the Boot Mode and selecting trusted UEFI files options are missing in the BIOS, i should wait for a BIOS update and hope it will be enabled...

I found this instruction to add the UEFI entry with the rEFIind bootloader:
[http://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html](http://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html) 

That didn't work for me because the netbook reinstalls the Windows Bootloader automatically after it's deleted.

My solution:
I installed the rEFInd boot loader into /boot/efi/EFI/Microsoft/Boot (where Windows bootloader files are located on my machine).
Then i deleted bootmgfw.efi and renamed refind_x64.efi to bootmgfw.efi.
After that it booted into the rEFInd bootloader and from there you can boot in any bootloader you want.
(Documentation for rEFInd: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/))

Maybe one of those approaches will work for you. Took me way too long to figure it out...

---

