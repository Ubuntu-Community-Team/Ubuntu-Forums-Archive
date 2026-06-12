---
title: "Can't remaster Feisty Live"
date: 2007-04-29
forum: Packaging and Compiling Programs
---

### Post by pxa270 on 2007-04-29
Hello, I've been trying to remaster a Feisty live cd without any success. 
Specifically, I got the i386-desktop iso, which boots fine in qemu and VPC under Windows. Then, I mounted it and copied the contents in a Linux system with 
  cp -a /cdrom/* /home/user/mycd
changed to /home/user/mycd and tried to generate a new iso (without any customizations yet) from the copied directory with
```
mkisofs -r -V "Custom Ubuntu" -cache-inodes -J -l \ 
 -b isolinux/isolinux.bin -c isolinux/boot.cat \
 -no-emul-boot -boot-load-size 4 -boot-info-table \ 
 -o /tmp/CustomCD.iso .
```
I also deleted the copied isolinux/boot.cat so that mkisofs will generate a new one. This works fine with the Dapper and Edgy iso's (where I would proceed to customize the initrd). With Feisty, under both qemu and VPC the resulting iso would boot and hang at the splash screen with the slider moving back and forth. Pressing Alt-F1 shows that it hangs at the "Loading, please wait" screen, without any further messages. I also tried this with a xubuntu-desktop live cd, with the same results.

Any ideas what I'm doing wrong? Has anybody actually succesfully remastered Feisty live?
Thanks.

ps. I'm not sure what forum to post this question to, but the last one about customizing the live cd was in this one.

---

