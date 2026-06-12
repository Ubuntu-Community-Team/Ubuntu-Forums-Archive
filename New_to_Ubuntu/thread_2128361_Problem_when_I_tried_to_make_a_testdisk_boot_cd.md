---
title: "Problem when I tried to make a testdisk boot cd"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by ivanscs1212 on 2013-03-22
Hi People!!! I am trying to do the following process to make a testdisk cd is in my Ubuntu (10.04 LTS Full updated - kernel linux 2.6.32-45 generic - gnome 2.30.2) but I am having sucess:

Process:
[COLOR=#000000][FONT=sans-serif]This document explains how to create under Linux a LiveCD running FreeDOS that automatically start [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").[/FONT][/COLOR]

[LIST]
[*]Download FreeDOS OEM CD-ROM disc builder assistant
[/LIST]

wget -N [http://www.fdos.info/bootdisks/ISO/FDOEMCD.builder.zip](http://www.fdos.info/bootdisks/ISO/FDOEMCD.builder.zip)
[LIST]
[*]Download the DOS version of TestDisk & PhotoRec
[/LIST]

wget -N [http://www.cgsecurity.org/testdisk-6.12.dos.zip](http://www.cgsecurity.org/testdisk-6.12.dos.zip)
[LIST]
[*][COLOR=#ff0000]Cleanup the work directory if it already exists[/COLOR]
[/LIST]

[COLOR=#ff0000]rm -rf FDOEMCD --What does it do? in this stage this folder not exists. Is It for old instalation?[/COLOR]
[LIST]
[*]Uncompress the archive
[/LIST]

unzip FDOEMCD.builder.zip
[LIST]
[*]Uncompress latest version of TestDisk & PhotoRec
[/LIST]

cd FDOEMCD/CDROOTunzip ../../testdisk-6.12.dos.zipmv testdisk-6.12 testdisk
[LIST]
[*]Create an autorun script
[/LIST]

echo "@ECHO OFF" > AUTORUN.BATecho "CLS" >> AUTORUN.BATecho "CD TESTDISK" >> AUTORUN.BATecho "TESTDISK.EXE" >> AUTORUN.BAT
[LIST]
[*][COLOR=#ff0000]This script must use DOS newlines, not Unix ones[/COLOR]
[/LIST]

[COLOR=#ff0000]unix2dos AUTORUN.BAT  -----  [SIZE=3]I cannot do this either find out the program unix2dos!![/SIZE][/COLOR]
[LIST]
[*][COLOR=#ff0000]Create the iso image using mkisofs ----[SIZE=5]- Below part I cannot do too!!!![/SIZE][/COLOR]
[/LIST]

[COLOR=#ff0000]cd ..mkisofs -o testdisk.iso -p "Christophe Grenier" -publisher "www.cgsecurity.org" -V "TestDisk CD" \-b isolinux/isolinux.bin -no-emul-boot -boot-load-size 4 -boot-info-table -N -J -r \-c boot.catalog -hide boot.catalog -hide-joliet boot.catalog CDROOT[/COLOR]
[LIST]
[*]Boot from this iso image in qemu emulator
[/LIST]

qemu -localtime -boot d -cdrom testdisk.iso -hda disk.dd
[LIST]
[*]If everything is ok, burn the iso
[/LIST]



Please somebody helps me to solve the part that I put comment in Red???


Thank you very much for any help!!! 

I am very happy with ubuntu Its my first linux destop!!  cooooollllll!!!

---

