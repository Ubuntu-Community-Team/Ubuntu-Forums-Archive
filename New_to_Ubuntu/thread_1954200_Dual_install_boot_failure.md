---
title: "Dual install boot failure"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Gazucha on 2012-04-07
Hi people, I have been having seemingly endless Linux nightmares for the last several months now.

This evening I decided to scrap the idea of using Ubuntu, so installed Mint 11 alongside my already dead Ubuntu 11.04 install, which died for no apparent reason last week (just won't turn on).

The install seemed to go fine, however when I restarted the laptop all I receive is the same blank screen I found when trying to boot 11.04.

I can enter bios. The HDD is fine. No grub menu appears, just a few seconds blinking white line in the top left corner then zilch. The fan runs high and just nothing! 


Seems to me that the computer is still trying to boot the 11.04 as I cannot see how a totally fresh install (in fact I have now installed it twice) can fail so completely and utterly.

If no-one has any ideas then I shall just format the entire drive install Mint afresh, delete my Ubuntu account and just consider Ubuntu to be malware in disguise.

Life is too short to suffer 6 months of Ubuntu created stress, headache and poverty.

Any help would be fantastic although I am not holding my breath.[-o<

---

### Post by Basher101 on 2012-04-07
maybe your grub is fried. Try to restore it with this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
see option 2 on how to get it, using a Live CD.

---

### Post by Gazucha on 2012-04-07
How long should it take? Have had a window saying 'scanning systems' which has been there for the last 20 minutes. It says should take several minutes.

I don't have a blank CD so just installed Boot Repair using the Mint 11 live CD.

---

### Post by na5h on 2012-04-07
If you have a backup of your files, doing a fresh install is not a bad idea at all. I suggest you give Ubuntu 12.04 a try when it comes out at the end of this month. 

When upgrading/installing, it is also a good idea to run the distro off the Live CD first, before hitting any upgrade/install buttons. This way, you can make sure that everything is working the way it should. Always remember to make a backup of your files!

---

### Post by CottonCandy on 2012-04-07
[This thread on how to troubleshoot when you end up with a blank screen after booting]("http://ubuntuforums.org/showthread.php?t=1743535") might help. 

> **MAFoElffen said:**
> [B]Are you having these problems?  
[/B]   - Error- "Cannot display this grahics mode"  
  - GRUB_GXFMODE-auto results in **Blank screen problems on Startup**?  (this includes purple or **black screen, flashing cursor,** stuck at splash screen...) 
  - No Grub Menu?  
 [COLOR=Black]

[/COLOR]> **MAFoElffen said:**
> These are my notes that have help people   through the last 5 releases of Ubuntu, up through Ubuntu Natty Narwhal   11.04.  

Basically, we want to make sure that the Grub menu boots. then verify   that the kernel is booting, then that the XServer Session starts and   displays.

[COLOR=Black]Why this sometimes happens: 
[/COLOR]> **MAFoElffen said:**
> Linux distributions such as Ubuntu, basically and simplistically run in  layers like this-->  You have a Linux kernel running.  On top of that  layer, you have a terminal session- running to interact with other  layers.  On top of that, you have an GUI, XTerminal session, X-Wndows,  XServer or also known as an XSession running to have a visually  interactive session running.  **In each version of Ubuntu (and other  distro's) an honest and earnest attempt is made to make each new version  easier to use for a new user, in a way that is pleasing to the eye.    Each of these changes does mean underlying changes in how things relate  to each other layer... on a base that is trying to cover a myriad of  hardware combinations, that users will install that distribution onto.**   Sometimes all of these combinations cannot be "foreseen."  (For instance  when a certain video card type is made by over a dozen different  vendors...) These techniques are similar to the same problems in Unix  and XServer (XServer Host & Client).
 There are thousands upon thousands of computer configurations out there. The fact that it sometimes takes some troubleshooting & tweaking to get any Linux distribution working properly is expected. 

That said, I also suggest installing Ubuntu 11.10. I had to troubleshoot to get 10.10 working and had problems with 11.04 as well but when I installed 11.10 I had hardly any trouble at all.

---

### Post by Gazucha on 2012-04-07
Hi CottonCandy and thanks for the input.

I'm still waiting for Boot Repair to do it's thing...

It was actually 'upgrading' Lol! :) to 11.10 that started all my problems. I had been loving 11.04 for most of 2011 until just before Xmas I pushed the dreaded upgrade button and that killed everything.
It was a tragic shame as I had never been happier with any OS.
I then fresh installed 11.10 after the crash and just didn't like it's 'feel', so went back to 11.04. Fortunately I have everything now backed up although it is 300 miles away. :)

---

### Post by Gazucha on 2012-04-07
Hi again...
 Update, hot off the press...

 Boot Repair worked!!!!!!!!!!!!!!!!!!\\:D/

Thank you all sooo much for your time and input.  Mwah!!!


 I knew SOMETHING would work :)

 However....

 It now boots straight to 11.04 with no option to access the new Mint 'Katya' install.

Shall I just open a new thread or am I missing something really basic?

---

### Post by westie457 on 2012-04-07
Hi have just come to this thread. Great that it is working.

All you have to do now should be to update grub in the terminal ```
sudo update-grub
```

If for some reason this does not work then go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and follow the instructions to download run the program and post the RESULTS.txt file so we can look at where it has gone wrong.

Thank you

---

### Post by Gazucha on 2012-04-07
Hi there,
 I am not too hot on running commands.

 Downloaded and extracted to the download folder but I keep getting 'no such file or directory' responses from the Terminal????????????????????!!!!!!!!!!!!!!!!!!!! 

After following the instructions, I am entering, sudo bash /home/gaz/Downloads/boot_info_script.sh

What am I missing?

 Anyway, I'm tired and off to bed. Enough Ubuntu stress...

Please leave any replies and I'll try again later.

Happy Easter everyone.

---

### Post by CottonCandy on 2012-04-07
I am no expert in the terminal, but perhaps try  sudo bash /Downloads/boot_info_script.sh  instead? 
I think the terminal defaults to your home folder so typing /home/gaz may be confusing it. If the prompt in terminal is gaz@computername:~$  then that may be it. 

From what I've heard, it's usually much better to do a fresh install than upgrade. Good thing you backed up your files!

---

### Post by Gazucha on 2012-04-18
Hi again chaps,  haven't been able to get online this last week and now having problems posting.      Anyway the Boot info script 'issue' was just that I needed to write the filename EXACTLY as it had been downloaded - not per instructions that came with...      Here is the file output, any help would be great.     In case you have forgotten, I'm looking to have the option to boot either of the 2 installed Operating Systems.       Thanks.

---

### Post by Gazucha on 2012-04-18
For some reason this isn't posting clearly but please try and make sense of this...
```
                     Boot Info Script 0.61      [1 April 2012]   ============================= Boot Info Summary: ===============================   => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for (,msdos1)/boot/grub on this drive.  sda1: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:  Ubuntu 11.04     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda3: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  Unknown     Boot sector info:   sda5: __________________________________________________________________________      File system:            Boot sector type:  -     Boot sector info:      Mounting failed:   mount: unknown filesystem type ''  sda6: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:  Linux Mint 11 LXDE     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda7: __________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:   ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 160.0 GB, 160041885696 bytes 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *    205,160,448   312,580,095   107,419,648  83 Linux /dev/sda3               2,046   205,160,447   205,158,402   5 Extended /dev/sda5         156,252,160   205,160,447    48,908,288  82 Linux swap / Solaris /dev/sda6               2,048   153,108,479   153,106,432  83 Linux /dev/sda7         153,110,528   156,248,063     3,137,536  82 Linux swap / Solaris   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/mapper/cryptswap1 cc0bd3d5-fded-4962-98eb-6fb62425bddd   swap        /dev/sda1        e5121463-8b06-41f3-9b6f-b6fb4d8f9552   ext4        /dev/sda6        2db00d84-aba7-474e-ae9f-bce1cb9c61d7   ext4        /dev/sda7        9eaf7011-d00e-4641-9f7c-fb7ec840a89e   swap         ========================= "ls -R /dev/mapper/" output: =========================  /dev/mapper: control cryptswap1  ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)   =========================== sda1/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga   insmod video_bochs   insmod video_cirrus }  insmod part_msdos insmod ext2 set root='(/dev/sda,msdos1)' search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=auto   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ext2 set root='(/dev/sda,msdos1)' search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 set locale_dir=($root)/boot/grub/locale set lang=en_US insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray if background_color 44,0,30; then   clear fi ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### if [ ${recordfail} != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3; then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode if [ "$linux_gfx_mode" != "text" ]; then load_video; fi menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	set gfxpayload=$linux_gfx_mode 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos1)' 	search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e5121463-8b06-41f3-9b6f-b6fb4d8f9552 ro   quiet splash vt.handoff=7 	initrd	/boot/initrd.img-2.6.38-8-generic } menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	set gfxpayload=$linux_gfx_mode 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos1)' 	search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 	echo	'Loading Linux 2.6.38-8-generic ...' 	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=e5121463-8b06-41f3-9b6f-b6fb4d8f9552 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.38-8-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos1)' 	search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 	linux16	/boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos1)' 	search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Linux Mint 11 LXDE, 2.6.38-8-generic (/dev/sda6) (on /dev/sda6)" --class gnu-linux --class gnu --class os { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos6)' 	search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=2db00d84-aba7-474e-ae9f-bce1cb9c61d7 ro quiet splash vt.handoff=7 	initrd /boot/initrd.img-2.6.38-8-generic } menuentry "Linux Mint 11 LXDE, 2.6.38-8-generic (/dev/sda6) -- recovery mode (on /dev/sda6)" --class gnu-linux --class gnu --class os { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos6)' 	search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=2db00d84-aba7-474e-ae9f-bce1cb9c61d7 ro single 	initrd /boot/initrd.img-2.6.38-8-generic } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ### --------------------------------------------------------------------------------  =============================== sda1/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # #                 proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda1 during installation UUID=e5121463-8b06-41f3-9b6f-b6fb4d8f9552 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda5 during installation #UUID=fe138e3e-ace2-4c7b-8a2e-4c7b80a60846 none            swap    sw              0       0 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 /dev/mapper/cryptswap1 none swap sw 0 0 --------------------------------------------------------------------------------  =================== sda1: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)   109.961174011 = 118.069911552  boot/grub/core.img                             1  102.578113556 = 110.142410752  boot/grub/grub.cfg                             1  102.492187500 = 110.050148352  boot/initrd.img-2.6.38-8-generic               2  109.960430145 = 118.069112832  boot/vmlinuz-2.6.38-8-generic                  1  102.492187500 = 110.050148352  initrd.img                                     2  109.960430145 = 118.069112832  vmlinuz                                        1  =========================== sda6/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga   insmod video_bochs   insmod video_cirrus }  insmod part_msdos insmod ext2 set root='(/dev/sda,msdos6)' search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=auto   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ext2 set root='(/dev/sda,msdos6)' search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 set locale_dir=($root)/boot/grub/locale set lang=en_US insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=10 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### insmod part_msdos insmod ext2 set root='(/dev/sda,msdos6)' search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 insmod png if background_image /boot/grub/linuxmint.png; then   true else   set menu_color_normal=white/black   set menu_color_highlight=black/light-gray   if background_color 44,0,30; then     clear   fi fi ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/06_mint_theme ### insmod part_msdos insmod ext2 set root='(/dev/sda,msdos6)' search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 insmod png if background_image /boot/grub/linuxmint.png ; then   set color_normal=white/black   set color_highlight=white/light-gray else   set menu_color_normal=white/black   set menu_color_highlight=white/light-gray fi ### END /etc/grub.d/06_mint_theme ###  ### BEGIN /etc/grub.d/10_linux ### if [ ${recordfail} != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3; then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode if [ "$linux_gfx_mode" != "text" ]; then load_video; fi menuentry 'Linux Mint 11 LXDE, 2.6.38-8-generic (/dev/sda6)' --class linuxmint --class gnu-linux --class gnu --class os { 	recordfail 	set gfxpayload=$linux_gfx_mode 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos6)' 	search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=2db00d84-aba7-474e-ae9f-bce1cb9c61d7 ro   quiet splash vt.handoff=7 	initrd	/boot/initrd.img-2.6.38-8-generic } menuentry 'Linux Mint 11 LXDE, 2.6.38-8-generic (/dev/sda6) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os { 	recordfail 	set gfxpayload=$linux_gfx_mode 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos6)' 	search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 	echo	'Loading Linux 2.6.38-8-generic ...' 	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=2db00d84-aba7-474e-ae9f-bce1cb9c61d7 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.38-8-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/10_lupin ### ### END /etc/grub.d/10_lupin ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos6)' 	search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 	linux16	/boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos6)' 	search --no-floppy --fs-uuid --set=root 2db00d84-aba7-474e-ae9f-bce1cb9c61d7 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos1)' 	search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=e5121463-8b06-41f3-9b6f-b6fb4d8f9552 ro quiet splash vt.handoff=7 	initrd /boot/initrd.img-2.6.38-8-generic } menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os { 	insmod part_msdos 	insmod ext2 	set root='(/dev/sda,msdos1)' 	search --no-floppy --fs-uuid --set=root e5121463-8b06-41f3-9b6f-b6fb4d8f9552 	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=e5121463-8b06-41f3-9b6f-b6fb4d8f9552 ro single 	initrd /boot/initrd.img-2.6.38-8-generic } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ### --------------------------------------------------------------------------------  =============================== sda6/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # #                 proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda6 during installation UUID=2db00d84-aba7-474e-ae9f-bce1cb9c61d7 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda7 during installation UUID=9eaf7011-d00e-4641-9f7c-fb7ec840a89e none            swap    sw              0       0 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 --------------------------------------------------------------------------------  =================== sda6: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)    12.135765076 = 13.030678528   boot/grub/core.img                             1   12.133666992 = 13.028425728   boot/grub/grub.cfg                             1   28.321289062 = 30.409752576   boot/initrd.img-2.6.38-8-generic               2   12.133277893 = 13.028007936   boot/vmlinuz-2.6.38-8-generic                  1   28.321289062 = 30.409752576   initrd.img                                     2   12.133277893 = 13.028007936   vmlinuz                                        1  ======================== Unknown MBRs/Boot Sectors/etc: ========================  Unknown BootLoader on sda3  00000000  39 6d 1b 00 54 6d 1b 00  63 6d 1b 00 71 6d 1b 00  |9m..Tm..cm..qm..| 00000010  7e 6d 1b 00 86 6d 1b 00  9e 6d 1b 00 ac 6d 1b 00  |~m...m...m...m..| 00000020  c4 6d 1b 00 d2 6d 1b 00  df 6d 1b 00 f1 6d 1b 00  |.m...m...m...m..| 00000030  fd 6d 1b 00 0d 6e 1b 00  28 6e 1b 00 36 6e 1b 00  |.m...n..(n..6n..| 00000040  48 6e 1b 00 55 6e 1b 00  61 6e 1b 00 72 6e 1b 00  |Hn..Un..an..rn..| 00000050  88 6e 1b 00 98 6e 1b 00  aa 6e 1b 00 bb 6e 1b 00  |.n...n...n...n..| 00000060  d2 6e 1b 00 e1 6e 1b 00  f5 6e 1b 00 0d 6f 1b 00  |.n...n...n...o..| 00000070  18 6f 1b 00 2d 6f 1b 00  41 6f 1b 00 51 6f 1b 00  |.o..-o..Ao..Qo..| 00000080  67 6f 1b 00 78 6f 1b 00  85 6f 1b 00 8f 6f 1b 00  |go..xo...o...o..| 00000090  a5 6f 1b 00 b8 6f 1b 00  ca 6f 1b 00 e0 6f 1b 00  |.o...o...o...o..| 000000a0  ec 6f 1b 00 f7 6f 1b 00  07 70 1b 00 11 70 1b 00  |.o...o...p...p..| 000000b0  1f 70 1b 00 32 70 1b 00  47 70 1b 00 55 70 1b 00  |.p..2p..Gp..Up..| 000000c0  6e 70 1b 00 7b 70 1b 00  8d 70 1b 00 a1 70 1b 00  |np..{p...p...p..| 000000d0  ad 70 1b 00 c0 70 1b 00  cd 70 1b 00 e3 70 1b 00  |.p...p...p...p..| 000000e0  f6 70 1b 00 0b 71 1b 00  24 71 1b 00 39 71 1b 00  |.p...q..$q..9q..| 000000f0  50 71 1b 00 5e 71 1b 00  78 71 1b 00 8f 71 1b 00  |Pq..^q..xq...q..| 00000100  ab 71 1b 00 c5 71 1b 00  de 71 1b 00 f6 71 1b 00  |.q...q...q...q..| 00000110  0f 72 1b 00 1a 72 1b 00  28 72 1b 00 37 72 1b 00  |.r...r..(r..7r..| 00000120  4d 72 1b 00 67 72 1b 00  80 72 1b 00 90 72 1b 00  |Mr..gr...r...r..| 00000130  ad 72 1b 00 b8 72 1b 00  c5 72 1b 00 dc 72 1b 00  |.r...r...r...r..| 00000140  e9 72 1b 00 f6 72 1b 00  00 73 1b 00 0c 73 1b 00  |.r...r...s...s..| 00000150  20 73 1b 00 31 73 1b 00  44 73 1b 00 5b 73 1b 00  | s..1s..Ds..[s..| 00000160  67 73 1b 00 72 73 1b 00  87 73 1b 00 a1 73 1b 00  |gs..rs...s...s..| 00000170  b8 73 1b 00 d0 73 1b 00  e7 73 1b 00 fb 73 1b 00  |.s...s...s...s..| 00000180  12 74 1b 00 22 74 1b 00  2d 74 1b 00 3b 74 1b 00  |.t.."t..-t..;t..| 00000190  56 74 1b 00 6b 74 1b 00  7e 74 1b 00 92 74 1b 00  |Vt..kt..~t...t..| 000001a0  a1 74 1b 00 ad 74 1b 00  c2 74 1b 00 db 74 1b 00  |.t...t...t...t..| 000001b0  f1 74 1b 00 fd 74 1b 00  0e 75 1b 00 15 75 00 fe  |.t...t...u...u..| 000001c0  ff ff 82 fe ff ff 02 30  50 09 00 48 ea 02 00 20  |.......0P..H... | 000001d0  20 00 05 fe ff ff 01 00  00 00 01 38 20 09 00 00  | ..........8 ...| 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200   =============================== StdErr Messages: ===============================  xz: (stdin): Compressed data is corrupt
```

---

### Post by Gazucha on 2012-04-25
How do I post the results in their original form?

---

### Post by strask on 2012-04-25
Maybe try copying it to [http://paste.ubuntu.com](http://paste.ubuntu.com) ? Not sure what went wrong with your first attempt. :\

---

### Post by oldfred on 2012-04-26
If you run the bootinfoscript from Boot-Repair it will automatically upload it and give a link.

You post looks like you have no line endings. It should just be a text file that you copy  and paste in a message then highlight and post in code tags.

---

### Post by YannBuntu on 2012-04-26
> **westie457 said:**
> All you have to do now should be to update grub in the terminal ```
sudo update-grub
```

Not needed. This has already be done automatically bu Boot-Repair. :)

> **westie457 said:**
> go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and follow the instructions to download run the program and post the RESULTS.txt file so we can look at where it has gone wrong.

Or easier: just click on the "Create BootInfo report" button of Boot-Repair, and indicate the URL that will appear. ;)

> **Gazucha said:**
> Have had a window saying 'scanning systems' which has been there for the last 20 minutes.

This should not happen with recent versions of Boot-Repair. Please update Boot-Repair each time before using it.

---

### Post by Gazucha on 2012-04-29
Hope this works...  [http://paste.ubuntu.com/954812/](http://paste.ubuntu.com/954812/)  Thanks for all the replies. :)

---

### Post by oldfred on 2012-04-29
@Gazucha
Boot script looks normal to me. Partition organization is a bit unusual but should be workable.

Can you boot into sda1? And from grub menu what happens if you try to boot into sda6. And it it does not work what happens when you try recovery mode?

---

### Post by YannBuntu on 2012-05-02
> **Gazucha said:**
>  It now boots straight to 11.04 with no option to access the new Mint 'Katya' install.

Please run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "Uncomment GFXMODE" option, then apply.
Note the new URL that will appear and indicate it to us.
Then reboot and tell us if you see the GRUB menu.

---

### Post by Gazucha on 2012-05-15
Url is ... [http://paste.ubuntu.com/988941/](http://paste.ubuntu.com/988941/)   gonna reboot now.

---

### Post by YannBuntu on 2012-05-15
core.img is missing. You may have to select also the "Place GRUB into : sda" option.

---

### Post by Gazucha on 2012-05-15
Obviously still no Boot Options, so how do I place Grub into :sda  is it in Boot Repair?  Thanks again for the help btw.

---

### Post by YannBuntu on 2012-05-15
Yes, it is in the "GRUB location" tab.

---

### Post by Gazucha on 2012-05-25
Says that GRUB is already in sda...  (check the attachment)    Apologies for the delayed responses but I am travelling a lot and don't have regular internet access.

---

### Post by YannBuntu on 2012-05-25
In your last URL you had the grub-setup:139 error. It has been fixed in the last version of Boot-Repair.
Please update Boot-Repair, click the "Recommended repair" and indicate the new URL that will appear.

---

### Post by Gazucha on 2012-06-18
Hi Yann, 
Again I apologise for the delayed response (I'm on the road a lot), so I ran Boot Repair but still the same Ubuntu only start-up..
 Running it again now and will post the url.. 

Cheers mate. :)

---

### Post by Gazucha on 2012-06-18
[http://paste.ubuntu.com/1048216/](http://paste.ubuntu.com/1048216/)

---

### Post by mansonfan78 on 2012-06-18
I'm wondering if the grub menu just got accidentally set to "hidden".  Have you tried holding down the shift key when booting?

---

### Post by YannBuntu on 2012-06-19
Hi

> **Gazucha said:**
> [http://paste.ubuntu.com/1048216/](http://paste.ubuntu.com/1048216/)

You forgot to [tick the "Uncomment GFXMODE" option]("http://ubuntuforums.org/showpost.php?p=11898622&postcount=19")...

---

### Post by Gazucha on 2012-06-19
[http://paste.ubuntu.com/1048981/](http://paste.ubuntu.com/1048981/) is the new URL... In the middle of something right now so can't reboot. I did uncheck it previously though.
 Do you think holding 'shift' will help?

 Cheers.

---

### Post by Gazucha on 2012-06-19
ok, now i need help...

 re-booted and it just went straight to ubuntu again... so, re-booted holding ´shift' and it showed ´grub loading´before the computer switched off.
 now whether i hold ´shift´, ´ésc´, or ´control´ or simply nothing, the computer just switches itself off moments after displaying the compaq logo.

 it is a good thing that i have a sense of humour....   

 help...............................

---

### Post by Gazucha on 2012-06-19
strange things happening..

 now boots back into ubuntu.. no sign of mint. 

 seems my computer has a sense of humour too..

---

### Post by YannBuntu on 2012-06-19
> **Gazucha said:**
> [http://paste.ubuntu.com/1048981/](http://paste.ubuntu.com/1048981/) is the new URL... In the middle of something right now so can't reboot. I did uncheck it previously though.
 Do you think holding 'shift' will help?

It may help, but normally you shouldn't need it.

I just updated the PPA for your case. Please wait for all packages to be ready on [this page]("https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages") (green tick), then run Boot-Repair, update it, tick the "GFXMODE" option, apply, indicate the new URL. Reboot and tell if better or not.

Better laughing than crying ;)

---

### Post by Gazucha on 2012-07-01
Cheers Yann,
 on a friends comp right now but will get mine online tomorrow and try again.
 
Thanks again for all 
the support...

---

### Post by Gazucha on 2012-08-04
Hi Yann,
 
unfortunately we are still booting straight into Ubuntu.

 Would be nice to resolve this before I buy a new Hard Drive. It doesn't make Ubuntu look good, I'm sorry to say.

 Let's see. :)

---

### Post by Gazucha on 2012-09-19
Hi Yann,

WooHoo!!\\:D/

Problem solved.. and loving having Ubuntu and Mint.

Maybe someone can explain this one, but after all our attempts, I had obviously given up](*,)
However, I had recently bought a new Ram stick and when installed, immediately on Start-up I found my long, lost, Dual-Boot menu screen. :shock:

Sooo....

Thanks to everyone who has offered advice and their time.

My suggestions if anyone else has this problem, 

 ...first run Boot Repair - as described earlier in this thread, then remove and re-install (or replace) their memory (RAM). 
Before, I had one 1Gb Hynix and one 512Mmb Kingston (didn't work)[-X , Now have two 1Gb Hynix and it works every time..:lolflag:=D>:grin:

Cheers Yann!

):P

---

### Post by YannBuntu on 2012-09-19
Good job :)
(I'm not hardware specialist, but I had already heard that having different kinds of RAM sticks can cause problems. Now I have the confirmation!)

---

