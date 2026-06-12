---
title: "Problem with boot menu and cant get boot menu! please help"
date: 2015-03-02
forum: New to Ubuntu
---

### Post by garry7 on 2015-03-02
hi Guys ,
So my issue is i have Ubuntu 14.4 install and window 10 preview . and every time i start my laptop it directly goes to window but i need to get the boot menu to choose my OS . now i have to go to window's recovery option and then choose Ubuntu there and then use ubuntu . i try boot repair as well it tell me to use below comment.
i try this comment on window and i am getting this error
C:\Users\Garry>bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
The boot configuration data store could not be opened.
Access is denied.
please help :)

---

### Post by oldfred on 2015-03-03
Did you install Ubuntu in BIOS/CSM/Legacy mode? The two boot modes are not compatible and you have to reboot to switch from one to the other.

Best to see details, post link to summary report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What brand/model computer?
Boot-Repair can totally uninstall grub-pc and install grub-efi-amd64 to convert to UEFI in its advanced mode. Be sure to boot in UEFI mode.

    Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
    [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

