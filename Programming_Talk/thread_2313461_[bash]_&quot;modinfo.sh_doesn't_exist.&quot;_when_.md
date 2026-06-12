---
title: "[bash] &quot;modinfo.sh doesn't exist.&quot; when using GRUB2 built from source"
date: 2016-02-12
forum: Programming Talk
---

### Post by faissaloo on 2016-02-12
So I'm trying to write a script that creates a 512mb disk image with GRUB 2.02 on it (built from source), but I keep getting:
```
./grub-install: error: /usr/local/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
```
Here's my code (must be run with sudo):
```
#!/bin/bash
#Create filesystem
echo "Creating filesystem"
dd if=/dev/zero of=out.img bs=1 count=0 seek=512M
mkdosfs -F 32 -n efi-boot out.img
mount out.img /mnt
cd /usr/src/

#GRUB
echo "Downloading GRUB 2.02"
wget ftp://alpha.gnu.org/gnu/grub/grub-2.02~beta2.tar.xz
echo "Decompressing GRUB 2.02 tarball"
tar xpvf grub-2.02~beta2.tar.xz
cd /usr/src/grub-2.02~beta2
echo "Building GRUB 2.02"
./autogen.sh
CFLAGS=-m32 CPP="gcc -E" ./configure --host=i386-pc-linux-gnu #CFLAGS=-m32 to make sure we use 32-bit GCC to compile GRUB, CPP="gcc -E" fixes GRUB using CPP when it should be using GCC for compilation
make
echo "Installing GRUB 2.02"
mkdir -p /mnt/boot/grub
./grub-install /dev/loop0 --boot-directory=/mnt --modules part_msdos --no-floppy
echo "GRUB 2.02 installation complete"

```
Please help, I've been trying to get this working for ages and I still have no idea what's wrong here.

---

### Post by faissaloo on 2016-02-12
Solved, I should have been using ./configure with the --prefix=/mnt option and then done make and then make install.

---

