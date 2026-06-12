---
title: "How to make a boot CDROM"
date: 2005-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by justgreg on 2005-03-23
This is a simple how to make a boot cdrom for Ubuntu.  When I first work with a distribution, I do not let the installation modify the master boot block.  I have other operating system that I use.  I use either a boot floppy or cdrom.  I perfer the boot cdrom.  It boots faster.

I use the console application and commands to do it.
1. create (mkdir iso) a directory "iso" in your home directory.

2. Go to (cd iso) the "iso" directory and then make (mkdir isolinux_builds) the directory "isolinux_builds"
3. Go to (cd isolinux_builds) the "isolinux_builds"

4. Copy (cp) from the boot directory using sudo the kernel to isolinux_builds (current directory)(sudo cp /boot/vmlinuz-2.6.8.1-3-386 vmlinuz)

5. Copy (cp) from the boot directory using sudo the initial image to isolinux_builds (sudo cp /boot/initrd.img-2.6.8.1-3-386 initrd.img)
6. Mount or open the Ubuntu distribution cdrom (place cdrom in reader and it should open automatically)

7. Copy from the cdrom file isolinux.bin to iso_builds using sudo (sudo cp /media/cdrom0/isolinux/isolinux.bin isolinux.bin) 
Use the directory listing command (ls -l) to check the files are present in isolinux_builds

8. Use gedit to make the file isolinux.cfg containing:

default linux
	label linux
	kernel vmlinuz
 	append  root=/dev/hda3  initrd=initrd.img acpi=off

save it and check the directory isolinux_builds for the file. Note, one will have to change root= to the correct partition with your system.

9. Change to (cd iso) "iso" directory (cd ..)

10 To make the iso image one uses mkisofs command using sudo (sudo mkisofs -o boot.iso -b isolinux.bin -c boot.cat -no-emul-boot \ -boot-load-size 4 -boot-info-table ./iso_builds/)

After mkisofs completes, one will have the boot cdrom image (boot.iso).
Use the nautilus program to burn "boot.iso" to a blank cdrom. The nautilus file manager help provides the details.

Enjoy life, Just Greg

---

### Post by mustali on 2006-08-02
Thanks for the tutorial. It helped me out when my GRUB was hosed. Just would like to point out a slight error in your guide - the last word in Step 10 should read 'isolinux_builds' instead of 'iso_builds'

Thanks again.

---

