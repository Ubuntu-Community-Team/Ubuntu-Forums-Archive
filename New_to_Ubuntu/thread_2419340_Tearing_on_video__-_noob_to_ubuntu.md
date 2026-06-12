---
title: "Tearing on video  - noob to ubuntu"
date: 2019-05-20
forum: New to Ubuntu
---

### Post by 1byte on 2019-05-20
Hi all

Im a new Linux convert :)

I currently run Ubuntu Studio and I notice that when I play video files they all have screen tearing (as if V-Sync was off in a game), This seems to be a widespread issue but the resolutions I could find related to either GPU's I dont have or talked in code, my system is home-made, Ivybridge i5 @ 3.4Ghz, Samsung SSD, 12GB DDR3, Nvidia GTX 650 (tearing on all available drivers in updates repo)

can anyone help me fix this please?
it happens regardles of video type or player (tried VLC, MPV, Parole)

thanks in advance

---

### Post by dino99 on 2019-05-20
Maybe you can grab some warnings/errors logged :
- first try to play a video
- then open 'journalctl -b' from the terminal
- scroll down to the end or so; you might see warning/error (like missing codec)

---

### Post by 1byte on 2019-05-20
I've done that and here is the log, I don't notice anything?, I installed all the codecs in the software section
it looks like a Vertical Sync issue, is there no way to turn V-SYNC on>?

  journalctl -b

```
-- Logs begin at Mon 2019-05-13 11:45:11 BST, end at Mon 2019-05-20 19:21:12 BST. --
May 20 18:59:59 HALinux kernel: microcode: microcode updated early to revision 0x21, date = 2019-02-13
May 20 18:59:59 HALinux kernel: Linux version 4.15.0-50-lowlatency (buildd@lcy01-amd64-013) (gcc version 7.3.0 (Ubuntu 7.3.0-16ub
May 20 18:59:59 HALinux kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-50-lowlatency root=UUID=5697747c-767d-4458-b1c7-ce0
May 20 18:59:59 HALinux kernel: KERNEL supported cpus:
May 20 18:59:59 HALinux kernel: Intel GenuineIntel
May 20 18:59:59 HALinux kernel: AMD AuthenticAMD
May 20 18:59:59 HALinux kernel: Centaur CentaurHauls
May 20 18:59:59 HALinux kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
May 20 18:59:59 HALinux kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
May 20 18:59:59 HALinux kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
May 20 18:59:59 HALinux kernel: x86/fpu: xstate_offset[2]: 576, xstate_sizes[2]: 256
May 20 18:59:59 HALinux kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
May 20 18:59:59 HALinux kernel: e820: BIOS-provided physical RAM map:
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000ddf44fff] usable
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x00000000ddf45000-0x00000000ddfcefff] reserved
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x00000000ddfcf000-0x00000000ddfcffff] ACPI data
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x00000000ddfd0000-0x00000000de0effff] ACPI NVS
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x00000000de0f0000-0x00000000de9c1fff] reserved
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x00000000de9c2000-0x00000000dea64fff] type 20
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x00000000dea65000-0x00000000dea65fff] usable
May 20 18:59:59 HALinux kernel: BIOS-e820: [mem 0x00000000dea66000-0x00000000deaa8fff] ACPI NVS
lines 1-24
```

---

### Post by ajgreeny on 2019-05-20
Which DE version of Ubuntu are you using, and what compositor are you using within that DE?

I am not a gnome user so not sure how or if compton works in that DE, nor what it uses as the default compositor, but if you use the standard gnome version try installing and using compton to see if that give you better video performance.

---

### Post by 1byte on 2019-05-28
I aint got a clue... whatever comes as default in Ubuntu Studio lol... I am new to Linux and  most of what you just said went over my head

---

### Post by mc4man on 2019-05-28
Is this an 'optimus' type setup?  If  not sure Install inxi (sudo apt install inxi), run and post results.
```
inxi -CG
```

**If it is** and you're using the nvidia gpu then this could help
```

echo "options nvidia_drm modeset=1" | sudo tee /etc/modprobe.d/zz-nvidia-modeset.conf
```
```
sudo update-initramfs -u 
```
reboot and see..

If no change to revert - 
```
sudo rm /etc/modprobe.d/zz-nvidia-modeset.conf
```
```
sudo update-initramfs -u 
```
reboot

---

