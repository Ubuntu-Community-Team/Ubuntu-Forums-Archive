---
title: "Installing Ubuntu on ASUS laptop with USB stick"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by jwsturner on 2013-01-21
I also have an ASUS X501U (in fact I bought 5 for family members at Christmas). They cam with Windows 8 installed. They are totally unusable, and not sure if its Win8 or the laptop. I use linux on my main laptop and want to install Linux on to these, however I can't get them to boot from the USB stick, and I can't seem to access the BIOS to change the boot order. From what I've read to access the BIOS I need to press ESC when the initial ASUS logo appears, but it just boots to Windows. Any ideas?

---

### Post by oldos2er on 2013-01-21
Post moved to its own thread.

---

### Post by Nr90 on 2013-01-21
Just mash every delete and every button between F1 and F12 ^^
It's probably one of those.

---

### Post by archery on 2013-01-21
[http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X501U&s=416&hashedid=dFPFCR1MvzCTTcgs&os=&no=1028]("http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X501U&s=416&hashedid=dFPFCR1MvzCTTcgs&os=&no=1028")

Try to enter the BIOS by pressing F2 button when ASUS logo appears.

---

### Post by JKyleOKC on 2013-01-21
Access to the BIOS varies from one manufacturer to the next. The key I've seen most often is DEL, but HP likes to use F10. I don't know about ASUS, and their web site returns absolutely NO results for support of the ASUS X501U model -- which, in itself, may be significant since all of the reviews I could find for it were quite negative.

Win8, out of the box, requires "secure boot" which will make it impossible to boot the machines from anything other than Win8 or one of the not-yet-released distributions of Ubuntu or RedHat that includes secure boot capability. However, to be approved for the "Win8 Compatible" label, an X86 machine (non-Atom CPUs) must have the capability to disable secure boot and allow booting of other systems, so once you get into BIOS be sure to look for that switch and turn secure boot off, as well as changing the boot order! Other tweaks may also be needed; the jury is still out so far as a complete "how to live with secure boot" procedure is concerned.

EDIT: Just saw that archery did manage to find support info, so try his suggestion.

---

### Post by CaptainMark on 2013-01-21
often the boot menu is disabled, so you have to go into the bios and enable the boot menu.

---

### Post by oldfred on 2013-01-21
Welcome to the forums.

Some of the systems with the new Windows 8 secure boot also have a fast boot setting that bypasses UEFI/BIOS and then you only can get back  into UEFI menu from Windows. Not sure of details. It may be called UEFI shell.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
How you boot flash drive is how it will install. It should give two options, one UEFI, and the other legacy/BIOS/CSM/AHCI or whatever.

---

