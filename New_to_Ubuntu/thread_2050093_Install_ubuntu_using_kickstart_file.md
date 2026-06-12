---
title: "Install ubuntu using kickstart file"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-08-30
[COLOR=Black]Hi,
[/COLOR][B][FONT=Arial][SIZE=2][COLOR=Black][URL="http://askubuntu.com/questions/26310/where-do-i-add-boot-parameters-to-use-ks-cfg"]_Where do I add boot parameters to use ks.cfg _
[/URL][/COLOR][/SIZE][/FONT][/B]

 created a kickstart file ks.cfg.
Where i want to place the ks.cfg  in ISO file in order to make it as unattended installation.

Thanks,
mohan

---

### Post by pmohankumar on 2012-08-31
Hi,

* I created a kickstart file and pasted in the extracted folder from "ubuntu-10.04.3-alternate-i386.iso" .

* Then i edited the text.cfg in isolinux folder.

[B]default install
label autoinstall
  menu label ^Automatically Install Ubuntu
  kernel /install/vmlinuz
  append file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz ks=cdrom:/ks.cfg --
label install
  menu label ^Install Ubuntu
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet --
label check
  menu label ^Check disc for defects
  kernel /install/vmlinuz
  append  MENU=/bin/cdrom-checker-menu initrd=/install/initrd.gz quiet --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80[/B]

* In the above code, after ks=cdrom:/ks.cfg, i entered "--" instead of "-" which was in forum. iam wright or i need to change.

* At last  i tried to Reconstitute the ISO file using the command
**mkisofs -D -r -V “$IMAGE_NAME” -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ~/autoinstall.iso**

* But i got error output like this 

[B]"I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Use genisoimage -help
to get a list of valid options.

Report problems to [email]debburn-devel@lists.alioth.debian.org[/email]."

Kindly guide me regarding this.
[/B]

---

### Post by pmohankumar on 2012-08-31
Reference link : [http://askubuntu.com/questions/26310/where-do-i-add-boot-parameters-to-use-ks-cfg](http://askubuntu.com/questions/26310/where-do-i-add-boot-parameters-to-use-ks-cfg)

---

### Post by pmohankumar on 2012-08-31
Hi,

what is the charset of utf-8

---

