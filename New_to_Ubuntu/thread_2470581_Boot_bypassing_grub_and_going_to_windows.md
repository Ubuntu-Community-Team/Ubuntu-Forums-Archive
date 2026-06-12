---
title: "Boot bypassing grub and going to windows"
date: 2022-01-04
forum: New to Ubuntu
---

### Post by psychohermit on 2022-01-04
Greetings folks.

I just had an SSD installed and reinstalled ubuntu 20.04.3.

The install went fine but now I can't get my grub menu to come up. I have disabled fast boot in windows. What else can I try?

It's an HP Envy Touchsmart notebook

It's booting in efi mode as far as I know. One troubling observation, the /boot/efi directory is empty.

Thanks,
--glenn

---

### Post by spinnekop62 on 2022-01-05
I assume you have checked in your bios the boot order - is grub/ubuntu in there and before windows?

---

### Post by oldfred on 2022-01-05
Ubuntu installer uses efibootmgr to set boot order in UEFI.
HP system do not seem to work with the changes made with efibootmgr either during install or later if you try to change order with efibootmgr.
Not sure if it is some sync with BCD in Windows or just HP not working with Linux tools.

Most with HP do update UEFI to latest version. And then change boot order in UEFI settings (not UEFI menu).

Can you boot Ubuntu ok from UEFI boot menu? Some that only boot Ubuntu occasionally just use the UEFI menu.
Grub only boots working Windows, so after some Windows updates it will reset itself to first & turn on fast start up. Then you have to use UEFI boot menu to boot again.

HP - escape + F9 for boot menu, F10 for UEFI/bios setup

---

### Post by psychohermit on 2022-01-05
I can boot ubuntu from F9 boot options.  Changing the boot order with efibootmgr doesn't work.  If I run efibootmgr it shows ubuntu as the first boot, but rebooting and looking again windows is the first boot option.  I tried to update the efi from HP but I can't find it.  Thanks, --glenn

---

### Post by psychohermit on 2022-01-05
I even updated the bios, hoping to get a submenu under OS Boot Manager, no joy.  Thanks, --glenn

---

### Post by tea for one on 2022-01-06
> **psychohermit said:**
> It's booting in efi mode as far as I know. 

You can double check the boot mode via the terminal:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

Secondly, can you confirm:-

Power On > Press F9 > You can see entries for both Ubuntu and Windows?
Power On > Press F10 > System Configuration > UEFI Boot Order > OS Boot Manager > Only Ubuntu?

---

### Post by psychohermit on 2022-01-06
Power on > Press F9 > I have entries for OS Boot Mgr, and ubuntu.  Power on > Press F10 > System Configuration > UEFI Boot Order > OS Boot Mgr > No submenu under OS Boor Mgr .  It's definitely booting in UEFI mode.   Thanks, --glenn

---

### Post by tea for one on 2022-01-07
> **psychohermit said:**
> The install went fine but now I can't get my grub menu to come up. I have disabled fast boot in windows. What else can I try?

Power off the PC > Power on > Press F9 > Select Ubuntu > Immediately tap Esc (one second intervals)?
Does Grub appear?

---

### Post by oldfred on 2022-01-07
Post this:
sudo efibootmgr -v

change boot order - use the numbers you want from above in this example
sudo efibootmgr -o 0,1,2
See also
man efibootmgr

Grub uses efibootmgr to reset boot order. Most with HP find it only works once.
But change in UEFI does work. If you do not have UEFI that allows changes you may just have to use f9 to choose.


similar?
HP Touchsmart 15
[http://ubuntuforums.org/showthread](http://ubuntuforums.org/showthread).

---

### Post by psychohermit on 2022-01-07
power off the pc, power on press F9. I have a seection of ubutnu, or OS Boot Mgr.  Select ubutnu, and the grub menu comes up,  I changed the boot order with efibootmgr to put linux first but I doesn't take after rebooting windows is first again.  Thanks, --glenn  ```
 glenn@LinuxBox:~$ sudo efibootmgr -v [sudo] password for glenn:  BootCurrent: 0003 Timeout: 0 seconds BootOrder: 0002,3002,0003,2001,2002,2003 Boot0000* Internal EFI Shell	MemoryMapped(11,0xaa248010,0xaaa4800f)/FvFile(c57ad6b7-0515-40a8-9d21-551652854e37)RC.... Boot0001* Internal EFI Shell	MemoryMapped(11,0xa9ae8010,0xaa2e800f)/FvFile(c57ad6b7-0515-40a8-9d21-551652854e37)RC.... Boot0002* Windows Boot Manager	HD(1,GPT,3da7dec9-bd9a-4a19-a30e-400c630ef687,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.................... Boot0003* ubuntu	HD(1,GPT,3da7dec9-bd9a-4a19-a30e-400c630ef687,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi) Boot0004* Internal EFI Shell	MemoryMapped(11,0xa9ae8010,0xaa2e800f)/FvFile(c57ad6b7-0515-40a8-9d21-551652854e37)RC.... Boot2001* USB Drive (UEFI)	RC Boot2002* Internal CD/DVD ROM Drive (UEFI)	RC Boot3000* Internal Hard Disk or Solid State Disk	RC Boot3002  Internal Hard Disk or Solid State Disk	RC Boot3003* Internal Hard Disk or Solid State Disk	RC 
```

---

### Post by yancek on 2022-01-08
I have two HP laptops and have been unable to use efibootmgr to make any changes in the BIOS although it is simple enough to do  manually with the arrow and F5/F6 keys in the BIOS.  It seems very strange to me that when you access Boot Options using F9, you see Ubuntu but do not see Ubuntu under the BIOS option (F10).  If that's the case, I don't know if there is a way to boot Ubuntu other than what you are now using.

---

