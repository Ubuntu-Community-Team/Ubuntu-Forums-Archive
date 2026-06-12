---
title: "File descriptor 63 (pipe:[81655]) leaked on lvs invocation. Parent PID 7506: /bin/bas"
date: 2021-07-23
forum: New to Ubuntu
---

### Post by karastift on 2021-07-23
My System:
[LIST]
[*]Samsung EVO SSD 500GB (NTFS) - Windows 10
[*]Toshiba HDD 1TB (NTFS) - Games
[*]SanDisk SSD 1TB (NTFS) - Personal Files
[*]Crucial SSD 240GB - Ubuntu LTS
[/LIST]
Problem:
I was using Windows for a long time, but then I installed Ubuntu on a different hard drive. My PC still boots into Windows.
I tried to change the boot order in my UEFI BIOS, but i the selectable options, there was no Ubuntu entry nor the Crucial SSD.
I can boot into Ubuntu with these steps: boot into Windows -> Settings -> Recovery -> Advanced restart -> select device to boot from -> "ubuntu".
I want a menu on boot where I can choose between Ubuntu and Windows.
I tried to repair GRUB, but in the repairing process an error (title) was thown and it didnt work:

[https://paste.ubuntu.com/p/6j8vWgKpXg/](https://paste.ubuntu.com/p/6j8vWgKpXg/)

Does anyone know how to achieve the selectable boot?

---

### Post by karastift on 2021-07-23
[B]My Solution:
[/B]1. boot into windows
2. open powershell or cmd as administrator
3. enter this command: [COLOR=#242729][FONT=ui-monospace]bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi[/FONT][/COLOR]

---

### Post by tea for one on 2021-07-23
Your Windows 10 OS is in hibernation state as detailed:-

[COLOR="#0000FF"]Lines 37 - 40[/COLOR] Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

---

