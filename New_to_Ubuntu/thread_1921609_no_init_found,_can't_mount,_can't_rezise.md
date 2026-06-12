---
title: "no init found, can't mount, can't rezise"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by munuWayne on 2012-02-07
[FONT=Bitstream Charter, serif][SIZE=2]**I was trying to eliminate the grub menu by messing with /etc/grub.d/30_os-prober.  I experimented on my computer (which has 10.04 netbook edition and 11.10) before trying it for work.  Now I can't boot 10.04 at all (11.10 works fine).  When I boot 10.04 I get the following prompt:**[/SIZE][/FONT]
 

 [FONT=Ubuntu Mono][SIZE=2]No init found.  Try passing init=bootarg.[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]BusyBox v1.13.3 (Ubuntu 1=1.13.3-1ubuntu11)built-in shell (ash)[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Enter 'help' for a list of built-in commands.[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2](initramfs)[/SIZE][/FONT]
 
 [FONT=Bitstream Charter, serif][SIZE=2]**The following are the results I get from trying things I've found on the forums.**[/SIZE][/FONT]
 
 

 [FONT=Ubuntu Mono][SIZE=2]root@fixme!:~# resize2fs /dev/sda1 [/SIZE][/FONT]
 [FONT=Ubuntu Mono][SIZE=2]resize2fs 1.41.14 (22-Dec-2010) [/SIZE][/FONT]
 [FONT=Ubuntu Mono][SIZE=2]Please run 'e2fsck -f /dev/sda1' first. [/SIZE][/FONT]
 

 [FONT=Ubuntu Mono][SIZE=2]root@fixme!:~# e2fsck /dev/sda1[/SIZE][/FONT]

 [FONT=Ubuntu Mono][SIZE=2]fsck from util-linux 2.19.1[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]e2fsck 1.41.14 (22-Dec-2010)[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]The filesystem size (according to the superblock) is 37568512 blocks[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]The physical size of the device is 35014279 blocks[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Either the superblock or the partition table is likely to be corrupt![/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Abort<y>? no[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]/dev/sda1 contains a file system with errors, check forced.[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Pass 1: Checking inodes, blocks, and sizes[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Pass 2: Checking directory structure[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Pass 3: Checking directory connectivity[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Pass 4: Checking reference counts[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Pass 5: Checking group summary information[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Error reading block 35127296 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? [/SIZE][/FONT] 
 
 [FONT=Bitstream Charter, serif][SIZE=2]*****followed by lots of “error writing/reading block 356....” &#8594; yes***[/SIZE][/FONT]
 [SIZE=2]                                   “[/SIZE][FONT=Bitstream Charter, serif][SIZE=2]***force**rewrite**” &#8594; **yes***[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Block bitmap differences:  +(35127296--35135519) +(35651584--35659807) +(36175872--36184095) +(36700160--36708383) +(37224448--37224458) +(37224464--37224474) +(37224480--37230111)[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Fix<y>? [/SIZE][/FONT] 
 
 [FONT=Bitstream Charter, serif][SIZE=2]*****followed by lots more  “ error writing/reading block 357....”  &#8594;  yes***[/SIZE][/FONT]
 [FONT=Bitstream Charter, serif][SIZE=2]***                 “force rewrite” &#8594; yes***[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]/dev/sda1: 212641/9396224 files (0.5% non-contiguous), 32916695/37568512 blocks[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]Error writing block 35127296 (Invalid argument) while writing block and inode bitmaps.  Ignore error<y>? yes[/SIZE][/FONT]
 
 [FONT=Bitstream Charter, serif][SIZE=2]*****followed by lots more “error writing/reading block 357....”  &#8594; yes***[/SIZE][/FONT]
 [FONT=Bitstream Charter, serif][SIZE=2]***                 “force rewrite” &#8594; yes***[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]…[/SIZE][FONT=Bitstream Charter, serif][SIZE=2]**.and it leads to nowhere once it has worked through all the errors.**[/SIZE][/FONT]
 
 
 [FONT=Ubuntu Mono][SIZE=2]root@fixme!:~# mount /dev/sda1[/SIZE][/FONT]
 
 [FONT=Ubuntu Mono][SIZE=2]mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab[/SIZE][/FONT]
  

 [SIZE=2][COLOR=black]
[/COLOR][/SIZE]
 [FONT=Bitstream Charter, serif][SIZE=2][COLOR=black]**Still won't boot, still can't mount. I've tried resizing the partition, mounting (see Terminal text above , etc. Memtest seemed to come up fine. Is there anything else I can try (or retry) ?  I've tried the systemrescuecd to no avail but I get the same messages as above in terminal and errors that don't allow me to do anything when I try gparted. :confused:**[/COLOR][/SIZE][/FONT]
 [SIZE=2][COLOR=black]
[/COLOR][/SIZE]
 [FONT=Bitstream Charter, serif][SIZE=2][COLOR=black]**I just want to recover my files in 10.04!  Please help!**[/COLOR][/SIZE][/FONT]

[FONT=Bitstream Charter, serif][SIZE=2][COLOR=black][B]Thanks for your time.
[/B][/COLOR][/SIZE][/FONT]

---

