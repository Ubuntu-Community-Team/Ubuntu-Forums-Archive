---
title: "Live CD Customization - problem with initrd and vmlinuz update"
date: 2021-10-30
forum: New to Ubuntu
---

### Post by matias-1999 on 2021-10-30
Hello all, ):P before to post I tried to search on the forum and and I googled a lot but I didn't find any useful information for my problem so I decided to write you hoping to find some precious hints. :)
It's my first post so I put it in the "New to Ubuntu" section to avoid any mistake...


I was customizing an ISO (based on Ubuntu Mate 20 LTS) and I followed this procedure ([https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)) that worked fine because I was able to customize the squashfs etc etc.
  
But when I tried to update also the live cd kernel the distro freezed just after the grub menu.
I just did a copy/paste of the initrd and vmlinuz files (tested on several flavors of Ubuntu 20 and 21 but same problem) and now I'm totally blocked at this point...
 
I did a lot of tests and I had few different log messages but mainly the boot stops after this message:
[HTML]Begin: Running /scripts/casper-remount ... done.[/HTML]


Do you have any idea if something has been changed in the procedure and how I could update the "live cd kernel" or any suggestion to be able to better debug?


Not really useful but FYI I'm testing the ISO files with the last VirtualBOX.

Thank you in advance for any help! :)
Matias

---

