---
title: "[Boot Repair Error] Dual Booting Lenovo Y500 with Windows 8.1 and Ubuntu 14.04"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by ankur-1502 on 2014-05-31
[FONT=arial]I have Lenovo Y500 with Windows 8.1. I recently installed a new mSATA on my system and installed a fresh windows 8.1 booting with UEFI on that. I wanted to dual boot and took following steps


1. Created a Unibootin Live USB, and tried to boot that EFI USB. The USB would boot but wont go past the first screen (Where we select to Try Ubuntu or Install 0r Install OEM ie a command line like screen)


2. I tried Try Ubuntu and Install, none of them seem to work, just the blank screen.


3. Changed boot to Legacy support and Legacy first, tried booting with Live USB (LiLi tool), that worked I had a purple screen that carried me to GUI where I clicked try ubuntu and then installed it from there.


4. I chose the unallocated space on the new mSATA ssd. I created a '/' mount, swap area and BIOS boot on that. NOTE: WINDOWS WAS BOOTING FROM THE SAME SSD.


5. After installation, nothing would boot. I went into boot menu and forced boot into Windows to select the boot as UEFI first. Windows worked fine after that


6. Again went to the boot menu (F12), forced to boot via the same USb and then tried boot repair. It detected EFI and asked me to run some commands.

[/FONT]
[FONT=arial]It eventually fails, following is the error log[/FONT]

```
[FONT=arial] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013][/FONT]


[FONT=arial]============================= Boot Info Summary: ==============================[/FONT][FONT=arial]=[/FONT]

[FONT=arial] => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector [/FONT]
[FONT=arial]    434911232 of the same hard drive for core.img. core.img is at this [/FONT]
[FONT=arial]    location and looks in partition 112 for .[/FONT]
[FONT=arial] => No boot loader is installed in the MBR of /dev/sdb.[/FONT]
[FONT=arial] => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.[/FONT]

[FONT=arial]sda1: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       ntfs[/FONT]
[FONT=arial]    Boot sector type:  Windows 8/2012: NTFS[/FONT]
[FONT=arial]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        [/FONT]

[FONT=arial]sda2: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       vfat[/FONT]
[FONT=arial]    Boot sector type:  Windows 8/2012: FAT32[/FONT]
[FONT=arial]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.[/FONT][FONT=arial]efi [/FONT]
[FONT=arial]                       /EFI/Microsoft/Boot/bootmgr.[/FONT][FONT=arial]efi [/FONT]
[FONT=arial]                       /EFI/Microsoft/Boot/memtest.[/FONT][FONT=arial]efi[/FONT]

[FONT=arial]sda3: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       [/FONT]
[FONT=arial]    Boot sector type:  -[/FONT]
[FONT=arial]    Boot sector info: [/FONT]
[FONT=arial]    Mounting failed:   mount: unknown filesystem type ''[/FONT]

[FONT=arial]sda4: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       ntfs[/FONT]
[FONT=arial]    Boot sector type:  Windows 8/2012: NTFS[/FONT]
[FONT=arial]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        /bootmgr /Windows/System32/winload.exe[/FONT]

[FONT=arial]sda5: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       ext4[/FONT]
[FONT=arial]    Boot sector type:  -[/FONT]
[FONT=arial]    Boot sector info: [/FONT]
[FONT=arial]    Operating System:  Ubuntu 14.04 LTS [/FONT]
[FONT=arial]    Boot files:        /boot/grub/grub.cfg /etc/fstab[/FONT]

[FONT=arial]sda6: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       swap[/FONT]
[FONT=arial]    Boot sector type:  -[/FONT]
[FONT=arial]    Boot sector info: [/FONT]

[FONT=arial]sda7: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       BIOS Boot partition[/FONT]
[FONT=arial]    Boot sector type:  Grub2's core.img[/FONT]
[FONT=arial]    Boot sector info: [/FONT]

[FONT=arial]sdb1: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       ntfs[/FONT]
[FONT=arial]    Boot sector type:  Windows 8/2012: NTFS[/FONT]
[FONT=arial]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        [/FONT]

[FONT=arial]sdb2: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       ntfs[/FONT]
[FONT=arial]    Boot sector type:  Windows 2000/XP: NTFS[/FONT]
[FONT=arial]    Boot sector info:  According to the info in the boot sector, sdb2 starts [/FONT]
[FONT=arial]                       at sector 0. But according to the info from fdisk, [/FONT]
[FONT=arial]                       sdb2 starts at sector 414492672.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        [/FONT]

[FONT=arial]sdb3: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       ntfs[/FONT]
[FONT=arial]    Boot sector type:  Windows 8/2012: NTFS[/FONT]
[FONT=arial]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        [/FONT]

[FONT=arial]sdb4: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       ntfs[/FONT]
[FONT=arial]    Boot sector type:  Windows 8/2012: NTFS[/FONT]
[FONT=arial]    Boot sector info:  No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        [/FONT]

[FONT=arial]sdc1: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]______________[/FONT]

[FONT=arial]    File system:       vfat[/FONT]
[FONT=arial]    Boot sector type:  SYSLINUX 4.04 2011-04-18[/FONT]
[FONT=arial]    Boot sector info:  Syslinux looks at sector 3667584 of /dev/sdc1 for its [/FONT]
[FONT=arial]                       second stage. SYSLINUX is installed in the  directory. [/FONT]
[FONT=arial]                       No errors found in the Boot Parameter Block.[/FONT]
[FONT=arial]    Operating System:  [/FONT]
[FONT=arial]    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg [/FONT]
[FONT=arial]                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys[/FONT]

[FONT=arial]============================ Drive/Partition Info: =============================[/FONT]

[FONT=arial]Drive: sda ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]_________[/FONT]

[FONT=arial]Disk /dev/sda: 240.1 GB, 240057409536 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]

[FONT=arial]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/FONT]

[FONT=arial]/dev/sda1                   1   468,862,127   468,862,127  ee GPT[/FONT]


[FONT=arial]GUID Partition Table detected.[/FONT]

[FONT=arial]Partition    Start Sector    End Sector  # of Sectors System[/FONT]
[FONT=arial]/dev/sda1           2,048       616,447       614,400 Windows Recovery Environment (Windows)[/FONT]
[FONT=arial]/dev/sda2         616,448       821,247       204,800 EFI System partition[/FONT]
[FONT=arial]/dev/sda3         821,248     1,083,391       262,144 Microsoft Reserved Partition (Windows)[/FONT]
[FONT=arial]/dev/sda4       1,083,392   360,316,927   359,233,536 Data partition (Windows/Linux)[/FONT]
[FONT=arial]/dev/sda5     360,316,928   418,910,207    58,593,280 Data partition (Linux)[/FONT]
[FONT=arial]/dev/sda6     418,910,208   434,911,231    16,001,024 Swap partition (Linux)[/FONT]
[FONT=arial]/dev/sda7     434,911,232   434,931,711        20,480 BIOS Boot partition[/FONT]

[FONT=arial]Drive: sdb ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]_________[/FONT]

[FONT=arial]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes[/FONT]
[FONT=arial]256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]

[FONT=arial]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/FONT]

[FONT=arial]/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT[/FONT]

[FONT=arial]/dev/sdb1 ends after the last sector of /dev/sdb[/FONT]

[FONT=arial]GUID Partition Table detected.[/FONT]

[FONT=arial]Partition    Start Sector    End Sector  # of Sectors System[/FONT]
[FONT=arial]/dev/sdb1           2,048   414,490,623   414,488,576 Data partition (Windows/Linux)[/FONT]
[FONT=arial]/dev/sdb2     414,492,672 1,859,151,871 1,444,659,200 Data partition (Windows/Linux)[/FONT]
[FONT=arial]/dev/sdb3   1,859,151,872 1,911,580,671    52,428,800 Data partition (Windows/Linux)[/FONT]
[FONT=arial]/dev/sdb4   1,911,580,672 1,953,523,711    41,943,040 -[/FONT]

[FONT=arial]Drive: sdc ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]_________[/FONT]

[FONT=arial]Disk /dev/sdc: 16.0 GB, [/FONT][16008609792]("tel:16008609792")[FONT=arial] bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]

[FONT=arial]Partition  Boot  Start Sector    End Sector  # of Sectors  Id System[/FONT]

[FONT=arial]/dev/sdc1    *             32    31,266,815    31,266,784   c W95 FAT32 (LBA)[/FONT]


[FONT=arial]"blkid" output: ______________________________[/FONT][FONT=arial]______________________________[/FONT][FONT=arial]____[/FONT]

[FONT=arial]Device           UUID                          [/FONT][FONT=arial]         TYPE       LABEL[/FONT]

[FONT=arial]/dev/loop0                    [/FONT][FONT=arial]                          squashfs   [/FONT]
[FONT=arial]/dev/loop1       07a4e6c3-228c-cd4a-be87-[/FONT][FONT=arial]7b34153cff39   ext2       [/FONT]
[FONT=arial]/dev/sda1        3810765B10762054              [/FONT][FONT=arial]         ntfs       Recovery[/FONT]
[FONT=arial]/dev/sda2        DC78-3FE8                     [/FONT][FONT=arial]         vfat       [/FONT]
[FONT=arial]/dev/sda4        D43C8B063C8AE2BA              [/FONT][FONT=arial]         ntfs       [/FONT]
[FONT=arial]/dev/sda5        4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f   ext4       [/FONT]
[FONT=arial]/dev/sda6        d4efb222-69e0-4202-9110-[/FONT][FONT=arial]43943f2b7446   swap       [/FONT]
[FONT=arial]/dev/sdb1        62286AEC286ABEA3              [/FONT][FONT=arial]         ntfs       New Volume[/FONT]
[FONT=arial]/dev/sdb2        01CE4BCCB7477C10              [/FONT][FONT=arial]         ntfs       My Drive[/FONT]
[FONT=arial]/dev/sdb3        8C06475E06474882              [/FONT][FONT=arial]         ntfs       LENOVO[/FONT]
[FONT=arial]/dev/sdb4        A2BE4906BE48D487              [/FONT][FONT=arial]         ntfs       PBR_DRV[/FONT]
[FONT=arial]/dev/sdc1        0C14-EF27                     [/FONT][FONT=arial]         vfat       MYLINUXLIVE[/FONT]

[FONT=arial]==============================[/FONT][FONT=arial]== Mount points: ==============================[/FONT][FONT=arial]===[/FONT]

[FONT=arial]Device           Mount_Point              Type       Options[/FONT]

[FONT=arial]/dev/loop0       /rofs                    squashfs   (ro,noatime)[/FONT]
[FONT=arial]/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=[/FONT][FONT=arial]0022,codepage=437,iocharset=[/FONT][FONT=arial]iso8859-1,shortname=mixed,[/FONT][FONT=arial]errors=remount-ro)[/FONT]


[FONT=arial]=========================== sda5/boot/grub/grub.cfg: ===========================[/FONT]

[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]
[FONT=arial]#[/FONT]
[FONT=arial]# DO NOT EDIT THIS FILE[/FONT]
[FONT=arial]#[/FONT]
[FONT=arial]# It is automatically generated by grub-mkconfig using templates[/FONT]
[FONT=arial]# from /etc/grub.d and settings from /etc/default/grub[/FONT]
[FONT=arial]#[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/00_header ###[/FONT]
[FONT=arial]if [ -s $prefix/grubenv ]; then[/FONT]
[FONT=arial]  set have_grubenv=true[/FONT]
[FONT=arial]  load_env[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]if [ "${next_entry}" ] ; then[/FONT]
[FONT=arial]   set default="${next_entry}"[/FONT]
[FONT=arial]   set next_entry=[/FONT]
[FONT=arial]   save_env next_entry[/FONT]
[FONT=arial]   set boot_once=true[/FONT]
[FONT=arial]else[/FONT]
[FONT=arial]   set default="0"[/FONT]
[FONT=arial]fi[/FONT]

[FONT=arial]if [ x"${feature_menuentry_id}" = xy ]; then[/FONT]
[FONT=arial]  menuentry_id_option="--id"[/FONT]
[FONT=arial]else[/FONT]
[FONT=arial]  menuentry_id_option=""[/FONT]
[FONT=arial]fi[/FONT]

[FONT=arial]export menuentry_id_option[/FONT]

[FONT=arial]if [ "${prev_saved_entry}" ]; then[/FONT]
[FONT=arial]  set saved_entry="${prev_saved_[/FONT][FONT=arial]entry}"[/FONT]
[FONT=arial]  save_env saved_entry[/FONT]
[FONT=arial]  set prev_saved_entry=[/FONT]
[FONT=arial]  save_env prev_saved_entry[/FONT]
[FONT=arial]  set boot_once=true[/FONT]
[FONT=arial]fi[/FONT]

[FONT=arial]function savedefault {[/FONT]
[FONT=arial]  if [ -z "${boot_once}" ]; then[/FONT]
[FONT=arial]    saved_entry="${chosen}"[/FONT]
[FONT=arial]    save_env saved_entry[/FONT]
[FONT=arial]  fi[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]function recordfail {[/FONT]
[FONT=arial]  set recordfail=1[/FONT]
[FONT=arial]  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]function load_video {[/FONT]
[FONT=arial]  if [ x$feature_all_video_module = xy ]; then[/FONT]
[FONT=arial]    insmod all_video[/FONT]
[FONT=arial]  else[/FONT]
[FONT=arial]    insmod efi_gop[/FONT]
[FONT=arial]    insmod efi_uga[/FONT]
[FONT=arial]    insmod ieee1275_fb[/FONT]
[FONT=arial]    insmod vbe[/FONT]
[FONT=arial]    insmod vga[/FONT]
[FONT=arial]    insmod video_bochs[/FONT]
[FONT=arial]    insmod video_cirrus[/FONT]
[FONT=arial]  fi[/FONT]
[FONT=arial]}[/FONT]

[FONT=arial]if [ x$feature_default_font_path = xy ] ; then[/FONT]
[FONT=arial]   font=unicode[/FONT]
[FONT=arial]else[/FONT]
[FONT=arial]insmod part_gpt[/FONT]
[FONT=arial]insmod ext2[/FONT]
[FONT=arial]set root='hd0,gpt5'[/FONT]
[FONT=arial]if [ x$feature_platform_search_hint = xy ]; then[/FONT]
[FONT=arial]  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]else[/FONT]
[FONT=arial]  search --no-floppy --fs-uuid --set=root 4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]    font="/usr/share/grub/unicode.[/FONT][FONT=arial]pf2"[/FONT]
[FONT=arial]fi[/FONT]

[FONT=arial]if loadfont $font ; then[/FONT]
[FONT=arial]  set gfxmode=auto[/FONT]
[FONT=arial]  load_video[/FONT]
[FONT=arial]  insmod gfxterm[/FONT]
[FONT=arial]  set locale_dir=$prefix/locale[/FONT]
[FONT=arial]  set lang=en_US[/FONT]
[FONT=arial]  insmod gettext[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]terminal_output gfxterm[/FONT]
[FONT=arial]if [ "${recordfail}" = 1 ] ; then[/FONT]
[FONT=arial]  set timeout=10[/FONT]
[FONT=arial]else[/FONT]
[FONT=arial]  if [ x$feature_timeout_style = xy ] ; then[/FONT]
[FONT=arial]    set timeout_style=menu[/FONT]
[FONT=arial]    set timeout=10[/FONT]
[FONT=arial]  # Fallback normal timeout code in case the timeout_style feature is[/FONT]
[FONT=arial]  # unavailable.[/FONT]
[FONT=arial]  else[/FONT]
[FONT=arial]    set timeout=10[/FONT]
[FONT=arial]  fi[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]### END /etc/grub.d/00_header ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/05_debian_theme ###[/FONT]
[FONT=arial]set menu_color_normal=white/black[/FONT]
[FONT=arial]set menu_color_highlight=black/[/FONT][FONT=arial]light-gray[/FONT]
[FONT=arial]if background_color 44,0,30; then[/FONT]
[FONT=arial]  clear[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]### END /etc/grub.d/05_debian_theme ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/10_linux ###[/FONT]
[FONT=arial]function gfxmode {[/FONT]
[FONT=arial]    set gfxpayload="${1}"[/FONT]
[FONT=arial]    if [ "${1}" = "keep" ]; then[/FONT]
[FONT=arial]        set vt_handoff=vt.handoff=7[/FONT]
[FONT=arial]    else[/FONT]
[FONT=arial]        set vt_handoff=[/FONT]
[FONT=arial]    fi[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]if [ "${recordfail}" != 1 ]; then[/FONT]
[FONT=arial]  if [ -e ${prefix}/gfxblacklist.txt ]; then[/FONT]
[FONT=arial]    if hwmatch ${prefix}/gfxblacklist.txt 3; then[/FONT]
[FONT=arial]      if [ ${match} = 0 ]; then[/FONT]
[FONT=arial]        set linux_gfx_mode=keep[/FONT]
[FONT=arial]      else[/FONT]
[FONT=arial]        set linux_gfx_mode=text[/FONT]
[FONT=arial]      fi[/FONT]
[FONT=arial]    else[/FONT]
[FONT=arial]      set linux_gfx_mode=text[/FONT]
[FONT=arial]    fi[/FONT]
[FONT=arial]  else[/FONT]
[FONT=arial]    set linux_gfx_mode=keep[/FONT]
[FONT=arial]  fi[/FONT]
[FONT=arial]else[/FONT]
[FONT=arial]  set linux_gfx_mode=text[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]export linux_gfx_mode[/FONT]
[FONT=arial]menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-4ef170a3-[/FONT][FONT=arial]7880-43ab-8101-1e14d18ce77f' {[/FONT]
[FONT=arial]    recordfail[/FONT]
[FONT=arial]    load_video[/FONT]
[FONT=arial]    gfxmode $linux_gfx_mode[/FONT]
[FONT=arial]    insmod gzio[/FONT]
[FONT=arial]    insmod part_gpt[/FONT]
[FONT=arial]    insmod ext2[/FONT]
[FONT=arial]    set root='hd0,gpt5'[/FONT]
[FONT=arial]    if [ x$feature_platform_search_hint = xy ]; then[/FONT]
[FONT=arial]      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]    else[/FONT]
[FONT=arial]      search --no-floppy --fs-uuid --set=root 4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]    fi[/FONT]
[FONT=arial]    linux    /boot/vmlinuz-3.13.0-27-[/FONT][FONT=arial]generic root=UUID=4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f ro  quiet splash $vt_handoff[/FONT]
[FONT=arial]    initrd    /boot/initrd.img-3.13.0-27-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-4ef170a3-[/FONT][FONT=arial]7880-43ab-8101-1e14d18ce77f' {[/FONT]
[FONT=arial]    menuentry 'Ubuntu, with Linux 3.13.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-[/FONT][FONT=arial]advanced-4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f' {[/FONT]
[FONT=arial]        recordfail[/FONT]
[FONT=arial]        load_video[/FONT]
[FONT=arial]        gfxmode $linux_gfx_mode[/FONT]
[FONT=arial]        insmod gzio[/FONT]
[FONT=arial]        insmod part_gpt[/FONT]
[FONT=arial]        insmod ext2[/FONT]
[FONT=arial]        set root='hd0,gpt5'[/FONT]
[FONT=arial]        if [ x$feature_platform_search_hint = xy ]; then[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        else[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root 4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        fi[/FONT]
[FONT=arial]        echo    'Loading Linux 3.13.0-27-generic ...'[/FONT]
[FONT=arial]        linux    /boot/vmlinuz-3.13.0-27-[/FONT][FONT=arial]generic root=UUID=4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f ro  quiet splash $vt_handoff[/FONT]
[FONT=arial]        echo    'Loading initial ramdisk ...'[/FONT]
[FONT=arial]        initrd    /boot/initrd.img-3.13.0-27-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]    }[/FONT]
[FONT=arial]    menuentry 'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-[/FONT][FONT=arial]recovery-4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f' {[/FONT]
[FONT=arial]        recordfail[/FONT]
[FONT=arial]        load_video[/FONT]
[FONT=arial]        insmod gzio[/FONT]
[FONT=arial]        insmod part_gpt[/FONT]
[FONT=arial]        insmod ext2[/FONT]
[FONT=arial]        set root='hd0,gpt5'[/FONT]
[FONT=arial]        if [ x$feature_platform_search_hint = xy ]; then[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        else[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root 4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        fi[/FONT]
[FONT=arial]        echo    'Loading Linux 3.13.0-27-generic ...'[/FONT]
[FONT=arial]        linux    /boot/vmlinuz-3.13.0-27-[/FONT][FONT=arial]generic root=UUID=4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f ro recovery nomodeset [/FONT]
[FONT=arial]        echo    'Loading initial ramdisk ...'[/FONT]
[FONT=arial]        initrd    /boot/initrd.img-3.13.0-27-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]    }[/FONT]
[FONT=arial]    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-[/FONT][FONT=arial]advanced-4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f' {[/FONT]
[FONT=arial]        recordfail[/FONT]
[FONT=arial]        load_video[/FONT]
[FONT=arial]        gfxmode $linux_gfx_mode[/FONT]
[FONT=arial]        insmod gzio[/FONT]
[FONT=arial]        insmod part_gpt[/FONT]
[FONT=arial]        insmod ext2[/FONT]
[FONT=arial]        set root='hd0,gpt5'[/FONT]
[FONT=arial]        if [ x$feature_platform_search_hint = xy ]; then[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        else[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root 4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        fi[/FONT]
[FONT=arial]        echo    'Loading Linux 3.13.0-24-generic ...'[/FONT]
[FONT=arial]        linux    /boot/vmlinuz-3.13.0-24-[/FONT][FONT=arial]generic root=UUID=4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f ro  quiet splash $vt_handoff[/FONT]
[FONT=arial]        echo    'Loading initial ramdisk ...'[/FONT]
[FONT=arial]        initrd    /boot/initrd.img-3.13.0-24-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]    }[/FONT]
[FONT=arial]    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-[/FONT][FONT=arial]recovery-4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f' {[/FONT]
[FONT=arial]        recordfail[/FONT]
[FONT=arial]        load_video[/FONT]
[FONT=arial]        insmod gzio[/FONT]
[FONT=arial]        insmod part_gpt[/FONT]
[FONT=arial]        insmod ext2[/FONT]
[FONT=arial]        set root='hd0,gpt5'[/FONT]
[FONT=arial]        if [ x$feature_platform_search_hint = xy ]; then[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        else[/FONT]
[FONT=arial]          search --no-floppy --fs-uuid --set=root 4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f[/FONT]
[FONT=arial]        fi[/FONT]
[FONT=arial]        echo    'Loading Linux 3.13.0-24-generic ...'[/FONT]
[FONT=arial]        linux    /boot/vmlinuz-3.13.0-24-[/FONT][FONT=arial]generic root=UUID=4ef170a3-7880-43ab-[/FONT][FONT=arial]8101-1e14d18ce77f ro recovery nomodeset [/FONT]
[FONT=arial]        echo    'Loading initial ramdisk ...'[/FONT]
[FONT=arial]        initrd    /boot/initrd.img-3.13.0-24-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]    }[/FONT]
[FONT=arial]}[/FONT]

[FONT=arial]### END /etc/grub.d/10_linux ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/20_linux_xen ###[/FONT]

[FONT=arial]### END /etc/grub.d/20_linux_xen ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/25_custom ###[/FONT]

[FONT=arial]menuentry "Windows UEFI bootmgfw.efi" {[/FONT]
[FONT=arial]search --fs-uuid --no-floppy --set=root DC78-3FE8[/FONT]
[FONT=arial]chainloader (${root})/EFI/Microsoft/Boot/[/FONT][FONT=arial]bootmgfw.efi[/FONT]
[FONT=arial]}[/FONT]

[FONT=arial]menuentry "Windows Boot UEFI loader" {[/FONT]
[FONT=arial]search --fs-uuid --no-floppy --set=root DC78-3FE8[/FONT]
[FONT=arial]chainloader (${root})/EFI/Boot/bootx64.efi[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]### END /etc/grub.d/25_custom ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/30_os-prober ###[/FONT]
[FONT=arial]### END /etc/grub.d/30_os-prober ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/30_uefi-firmware ###[/FONT]
[FONT=arial]### END /etc/grub.d/30_uefi-firmware ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/40_custom ###[/FONT]
[FONT=arial]# This file provides an easy way to add custom menu entries.  Simply type the[/FONT]
[FONT=arial]# menu entries you want to add after this comment.  Be careful not to change[/FONT]
[FONT=arial]# the 'exec tail' line above.[/FONT]
[FONT=arial]### END /etc/grub.d/40_custom ###[/FONT]

[FONT=arial]### BEGIN /etc/grub.d/41_custom ###[/FONT]
[FONT=arial]if [ -f  ${config_directory}/custom.cfg ]; then[/FONT]
[FONT=arial]  source ${config_directory}/custom.cfg[/FONT]
[FONT=arial]elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then[/FONT]
[FONT=arial]  source $prefix/custom.cfg;[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]### END /etc/grub.d/41_custom ###[/FONT]
[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]==============================[/FONT][FONT=arial]= sda5/etc/fstab: ==============================[/FONT][FONT=arial]==[/FONT]

[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]
[FONT=arial]# /etc/fstab: static file system information.[/FONT]
[FONT=arial]#[/FONT]
[FONT=arial]# Use 'blkid' to print the universally unique identifier for a[/FONT]
[FONT=arial]# device; this may be used with UUID= as a more robust way to name devices[/FONT]
[FONT=arial]# that works even if disks are added and removed. See fstab(5).[/FONT]
[FONT=arial]#[/FONT]
[FONT=arial]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT]
[FONT=arial]# / was on /dev/sda5 during installation[/FONT]
[FONT=arial]UUID=4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f /               ext4    errors=remount-ro 0       1[/FONT]
[FONT=arial]# swap was on /dev/sda6 during installation[/FONT]
[FONT=arial]UUID=d4efb222-69e0-4202-9110-[/FONT][FONT=arial]43943f2b7446 none            swap    sw              0       0[/FONT]
[FONT=arial]UUID=DC78-3FE8    /boot/efi    vfat    defaults    0    1[/FONT]
[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]=================== sda5: Location of files loaded by Grub: ====================[/FONT]

[FONT=arial]           GiB - GB             File                          [/FONT][FONT=arial]       Fragment(s)[/FONT]


[FONT=arial]=========================== sdc1/boot/grub/grub.cfg: ===========================[/FONT]

[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]if loadfont /boot/grub/font.pf2 ; then[/FONT]
[FONT=arial]    set gfxmode=auto[/FONT]
[FONT=arial]    insmod efi_gop[/FONT]
[FONT=arial]    insmod efi_uga[/FONT]
[FONT=arial]    insmod gfxterm[/FONT]
[FONT=arial]    terminal_output gfxterm[/FONT]
[FONT=arial]fi[/FONT]

[FONT=arial]set menu_color_normal=white/black[/FONT]
[FONT=arial]set menu_color_highlight=black/[/FONT][FONT=arial]light-gray[/FONT]

[FONT=arial]menuentry "Try Ubuntu without installing" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.[/FONT][FONT=arial]seed boot=casper quiet splash --[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]menuentry "Install Ubuntu" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.[/FONT][FONT=arial]seed boot=casper only-ubiquity quiet splash --[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]menuentry "OEM install (for manufacturers)" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.[/FONT][FONT=arial]seed boot=casper only-ubiquity quiet splash oem-config/enable=true --[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]menuentry "Check disc for defects" {[/FONT]
[FONT=arial]    set gfxpayload=keep[/FONT]
[FONT=arial]    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --[/FONT]
[FONT=arial]    initrd    /casper/initrd.lz[/FONT]
[FONT=arial]}[/FONT]
[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]========================= sdc1/syslinux/syslinux.cfg: ==========================[/FONT]

[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]
[FONT=arial]# D-I config version 2.0[/FONT]
[FONT=arial]include menu.cfg[/FONT]
[FONT=arial]default vesamenu.c32[/FONT]
[FONT=arial]prompt 0[/FONT]
[FONT=arial]timeout 50[/FONT]
[FONT=arial]ui gfxboot bootlogo[/FONT]
[FONT=arial]------------------------------[/FONT][FONT=arial]------------------------------[/FONT][FONT=arial]--------------------[/FONT]

[FONT=arial]=================== sdc1: Location of files loaded by Grub: ====================[/FONT]

[FONT=arial]           GiB - GB             File                          [/FONT][FONT=arial]       Fragment(s)[/FONT]


[FONT=arial]================= sdc1: Location of files loaded by Syslinux: ==================[/FONT]

[FONT=arial]           GiB - GB             File                          [/FONT][FONT=arial]       Fragment(s)[/FONT]


[FONT=arial]============== sdc1: Version of COM32(R) files used by Syslinux: ===============[/FONT]

[FONT=arial] syslinux/chain.c32           [/FONT][FONT=arial]      :  COM32R module (v4.xx)[/FONT]
[FONT=arial] syslinux/gfxboot.c32         [/FONT][FONT=arial]      :  COM32R module (v4.xx)[/FONT]
[FONT=arial] syslinux/vesamenu.c32        [/FONT][FONT=arial]      :  COM32R module (v4.xx)[/FONT]

[FONT=arial]======================== Unknown MBRs/Boot Sectors/etc: ========================[/FONT]

[FONT=arial]Unknown GPT Partiton Type[/FONT]
[FONT=arial]a4bb94ded106404da1a6bfd50179d6[/FONT][FONT=arial]ac[/FONT]

[FONT=arial]==============================[/FONT][FONT=arial]= StdErr Messages: ==============================[/FONT][FONT=arial]=[/FONT]

[FONT=arial]cat: /tmp/BootInfo-iS2P4HTG/Tmp_[/FONT][FONT=arial]Log: No such file or directory[/FONT]
[FONT=arial]cat: /tmp/BootInfo-iS2P4HTG/Tmp_[/FONT][FONT=arial]Log: No such file or directory[/FONT]
[FONT=arial]cat: /tmp/BootInfo-iS2P4HTG/Tmp_[/FONT][FONT=arial]Log: No such file or directory[/FONT]
[FONT=arial]File descriptor 9 (/proc/17483/mounts) leaked on lvscan invocation. Parent PID 8795: bash[/FONT]
[FONT=arial]File descriptor 63 (pipe:[61625]) leaked on lvscan invocation. Parent PID 8795: bash[/FONT]
[FONT=arial]  No volume groups found[/FONT]

[FONT=arial]ADDITIONAL INFORMATION :[/FONT]
[FONT=arial]=================== log of boot-repair 2014-05-30__21h54 ===================[/FONT]
[FONT=arial]boot-repair version : 3.199~ppa40~saucy[/FONT]
[FONT=arial]boot-sav version : 3.199~ppa40~saucy[/FONT]
[FONT=arial]glade2script version : 3.2.2~ppa47~saucy[/FONT]
[FONT=arial]boot-sav-extra version : 3.199~ppa40~saucy[/FONT]
[FONT=arial]boot-repair is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)[/FONT]
[FONT=arial]ls: cannot access /home/usr/.config: No such file or directory[/FONT]
[FONT=arial]CPU op-mode(s):        32-bit, 64-bit[/FONT]
[FONT=arial]bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=[/FONT][FONT=arial]nodeadkeys locale=us_us  persistent noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.[/FONT][FONT=arial]seed boot=casper initrd=/casper/initrd.lz splash -- maybe-ubiquity[/FONT]

[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]=================== os-prober:[/FONT]
[FONT=arial]/dev/sda5:Ubuntu 14.04 LTS (14.04):Ubuntu:linux[/FONT]

[FONT=arial]=================== blkid:[/FONT]
[FONT=arial]/dev/loop0: TYPE="squashfs"[/FONT]
[FONT=arial]/dev/loop1: UUID="07a4e6c3-228c-cd4a-be87-[/FONT][FONT=arial]7b34153cff39" TYPE="ext2"[/FONT]
[FONT=arial]/dev/sda1: LABEL="Recovery" UUID="3810765B10762054" TYPE="ntfs"[/FONT]
[FONT=arial]/dev/sda2: UUID="DC78-3FE8" TYPE="vfat"[/FONT]
[FONT=arial]/dev/sda4: UUID="D43C8B063C8AE2BA" TYPE="ntfs"[/FONT]
[FONT=arial]/dev/sda5: UUID="4ef170a3-7880-43ab-8101-[/FONT][FONT=arial]1e14d18ce77f" TYPE="ext4"[/FONT]
[FONT=arial]/dev/sda6: UUID="d4efb222-69e0-4202-9110-[/FONT][FONT=arial]43943f2b7446" TYPE="swap"[/FONT]
[FONT=arial]/dev/sdb1: LABEL="New Volume" UUID="62286AEC286ABEA3" TYPE="ntfs"[/FONT]
[FONT=arial]/dev/sdb2: LABEL="My Drive" UUID="01CE4BCCB7477C10" TYPE="ntfs"[/FONT]
[FONT=arial]/dev/sdb3: LABEL="LENOVO" UUID="8C06475E06474882" TYPE="ntfs"[/FONT]
[FONT=arial]/dev/sdb4: LABEL="PBR_DRV" UUID="A2BE4906BE48D487" TYPE="ntfs"[/FONT]
[FONT=arial]/dev/sdc1: LABEL="MYLINUXLIVE" UUID="0C14-EF27" TYPE="vfat"[/FONT]


[FONT=arial]1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.[/FONT]

[FONT=arial]Windows not detected by os-prober on sda4.[/FONT]

[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]

[FONT=arial]Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/[/FONT][FONT=arial]Microsoft/Boot/bootmgfw.efi[/FONT]
[FONT=arial]Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/[/FONT][FONT=arial]bootx64.efi[/FONT]

[FONT=arial]=================== sda5/etc/grub.d/ :[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 21:31 grub.d[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 21:21 grub.d.bak[/FONT]
[FONT=arial]total 76[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  9424 Apr 11 06:51 00_header[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  6058 Apr 10 11:58 05_debian_theme[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 11608 Apr 11 06:51 10_linux[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 10412 Apr 11 06:51 20_linux_xen[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root   311 May 30 21:31 25_custom[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 11692 Apr 11 06:51 30_os-prober[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  1416 Apr 11 06:51 30_uefi-firmware[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root   214 Apr 11 06:51 40_custom[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root   216 Apr 11 06:51 41_custom[/FONT]
[FONT=arial]-rw-r--r-- 1 root root   483 Apr 11 06:51 README[/FONT]




[FONT=arial]=================== sda5/etc/default/grub :[/FONT]

[FONT=arial]# If you change this file, run 'update-grub' afterwards to update[/FONT]
[FONT=arial]# /boot/grub/grub.cfg.[/FONT]
[FONT=arial]# For full documentation of the options in this file, see:[/FONT]
[FONT=arial]#   info -f grub -n 'Simple configuration'[/FONT]

[FONT=arial]GRUB_DEFAULT=0[/FONT]
[FONT=arial]#GRUB_HIDDEN_TIMEOUT=0[/FONT]
[FONT=arial]GRUB_HIDDEN_TIMEOUT_QUIET=true[/FONT]
[FONT=arial]GRUB_TIMEOUT=10[/FONT]
[FONT=arial]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX_DEFAULT="[/FONT][FONT=arial]quiet splash"[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX=""[/FONT]

[FONT=arial]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT]
[FONT=arial]# This works with Linux (no patch required) and with any kernel that obtains[/FONT]
[FONT=arial]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT]
[FONT=arial]#GRUB_BADRAM="0x01234567,[/FONT][FONT=arial]0xfefefefe,0x89abcdef,[/FONT][FONT=arial]0xefefefef"[/FONT]

[FONT=arial]# Uncomment to disable graphical terminal (grub-pc only)[/FONT]
[FONT=arial]#GRUB_TERMINAL=console[/FONT]

[FONT=arial]# The resolution used on graphical terminal[/FONT]
[FONT=arial]# note that you can use only modes which your graphic card supports via VBE[/FONT]
[FONT=arial]# you can see them in real GRUB with the command `vbeinfo'[/FONT]
[FONT=arial]#GRUB_GFXMODE=640x480[/FONT]

[FONT=arial]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT]
[FONT=arial]#GRUB_DISABLE_LINUX_UUID=true[/FONT]

[FONT=arial]# Uncomment to disable generation of recovery mode menu entries[/FONT]
[FONT=arial]#GRUB_DISABLE_RECOVERY="true"[/FONT]

[FONT=arial]# Uncomment to get a beep at grub start[/FONT]
[FONT=arial]#GRUB_INIT_TUNE="480 440 1"[/FONT]



[FONT=arial]/boot/efi detected in the fstab of sda5: UUID=DC78-3FE8     (sda2)[/FONT]
[FONT=arial]=================== UEFI/Legacy mode:[/FONT]
[FONT=arial]BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.[/FONT]
[FONT=arial]EFI in dmesg.[/FONT]
[FONT=arial][    0.000000] ACPI: UEFI 00000000af7fc000 000236 (v01 LENOVO CB-01    00000001 ACPI 00040000)[/FONT]
[FONT=arial]SecureBoot maybe enabled.[/FONT]


[FONT=arial]=================== PARTITIONS & DISKS:[/FONT]
[FONT=arial]sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.[/FONT]
[FONT=arial]sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.[/FONT]
[FONT=arial]sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.[/FONT]
[FONT=arial]sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.[/FONT]
[FONT=arial]sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.[/FONT]
[FONT=arial]sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2.[/FONT]
[FONT=arial]sdb3    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb3.[/FONT]
[FONT=arial]sdb4    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb4.[/FONT]

[FONT=arial]sda    : GPT,    BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes[/FONT]
[FONT=arial]sdb    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes[/FONT]


[FONT=arial]=================== parted -l:[/FONT]

[FONT=arial]Model: ATA Crucial_CT240M50 (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 240GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/4096B[/FONT]
[FONT=arial]Partition Table: gpt[/FONT]

[FONT=arial]Number  Start   End    Size    File system     Name                          Flags[/FONT]
[FONT=arial]1      1049kB  316MB  315MB   ntfs            Basic data partition          hidden, diag[/FONT]
[FONT=arial]2      316MB   420MB  105MB   fat32           EFI system partition          boot[/FONT]
[FONT=arial]3      420MB   555MB  134MB                   Microsoft reserved partition  msftres[/FONT]
[FONT=arial]4      555MB   184GB  184GB   ntfs            Basic data partition          msftdata[/FONT]
[FONT=arial]5      184GB   214GB  30.0GB  ext4[/FONT]
[FONT=arial]6      214GB   223GB  8193MB  linux-swap(v1)[/FONT]
[FONT=arial]7      223GB   223GB  10.5MB                        [/FONT][FONT=arial]                        bios_grub[/FONT]


[FONT=arial]Model: ATA ST1000LM024 HN-M (scsi)[/FONT]
[FONT=arial]Disk /dev/sdb: 1000GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/4096B[/FONT]
[FONT=arial]Partition Table: gpt[/FONT]

[FONT=arial]Number  Start   End     Size    File system  Name                  Flags[/FONT]
[FONT=arial]1      1049kB  212GB   212GB   ntfs         Basic data partition  msftdata[/FONT]
[FONT=arial]2      212GB   952GB   740GB   ntfs                          [/FONT][FONT=arial]     msftdata[/FONT]
[FONT=arial]3      952GB   979GB   26.8GB  ntfs         Ba                    msftdata[/FONT]
[FONT=arial]4      979GB   1000GB  21.5GB  ntfs         Ba                    hidden[/FONT]


[FONT=arial]Model:  Staples (scsi)[/FONT]
[FONT=arial]Disk /dev/sdc: 16.0GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=arial]Partition Table: msdos[/FONT]

[FONT=arial]Number  Start   End     Size    Type     File system  Flags[/FONT]
[FONT=arial]1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba[/FONT]

[FONT=arial]=================== parted -lm:[/FONT]

[FONT=arial]BYT;[/FONT]
[FONT=arial]/dev/sda:240GB:scsi:512:4096:[/FONT][FONT=arial]gpt:ATA Crucial_CT240M50;[/FONT]
[FONT=arial]1:1049kB:316MB:315MB:ntfs:[/FONT][FONT=arial]Basic data partition:hidden, diag;[/FONT]
[FONT=arial]2:316MB:420MB:105MB:fat32:EFI system partition:boot;[/FONT]
[FONT=arial]3:420MB:555MB:134MB::Microsoft reserved partition:msftres;[/FONT]
[FONT=arial]4:555MB:184GB:184GB:ntfs:Basic data partition:msftdata;[/FONT]
[FONT=arial]5:184GB:214GB:30.0GB:ext4::;[/FONT]
[FONT=arial]6:214GB:223GB:8193MB:linux-[/FONT][FONT=arial]swap(v1)::;[/FONT]
[FONT=arial]7:223GB:223GB:10.5MB:::bios_[/FONT][FONT=arial]grub;[/FONT]

[FONT=arial]BYT;[/FONT]
[FONT=arial]/dev/sdb:1000GB:scsi:512:4096:[/FONT][FONT=arial]gpt:ATA ST1000LM024 HN-M;[/FONT]
[FONT=arial]1:1049kB:212GB:212GB:ntfs:[/FONT][FONT=arial]Basic data partition:msftdata;[/FONT]
[FONT=arial]2:212GB:952GB:740GB:ntfs::[/FONT][FONT=arial]msftdata;[/FONT]
[FONT=arial]3:952GB:979GB:26.8GB:ntfs:Ba:[/FONT][FONT=arial]msftdata;[/FONT]
[FONT=arial]4:979GB:1000GB:21.5GB:ntfs:Ba:[/FONT][FONT=arial]hidden;[/FONT]

[FONT=arial]BYT;[/FONT]
[FONT=arial]/dev/sdc:16.0GB:scsi:512:512:[/FONT][FONT=arial]msdos: Staples;[/FONT]
[FONT=arial]1:16.4kB:16.0GB:16.0GB:fat32::[/FONT][FONT=arial]boot, lba;[/FONT]


[FONT=arial]=================== mount:[/FONT]
[FONT=arial]/cow on / type overlayfs (rw)[/FONT]
[FONT=arial]proc on /proc type proc (rw,noexec,nosuid,nodev)[/FONT]
[FONT=arial]sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)[/FONT]
[FONT=arial]udev on /dev type devtmpfs (rw,mode=0755)[/FONT]
[FONT=arial]devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=[/FONT][FONT=arial]0620)[/FONT]
[FONT=arial]tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,[/FONT][FONT=arial]mode=0755)[/FONT]
[FONT=arial]/dev/sdc1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=[/FONT][FONT=arial]0022,codepage=437,iocharset=[/FONT][FONT=arial]iso8859-1,shortname=mixed,[/FONT][FONT=arial]errors=remount-ro)[/FONT]
[FONT=arial]/dev/loop0 on /rofs type squashfs (ro,noatime)[/FONT]
[FONT=arial]none on /sys/fs/cgroup type tmpfs (rw)[/FONT]
[FONT=arial]none on /sys/fs/fuse/connections type fusectl (rw)[/FONT]
[FONT=arial]none on /sys/kernel/debug type debugfs (rw)[/FONT]
[FONT=arial]none on /sys/kernel/security type securityfs (rw)[/FONT]
[FONT=arial]tmpfs on /tmp type tmpfs (rw,nosuid,nodev)[/FONT]
[FONT=arial]none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=[/FONT][FONT=arial]5242880)[/FONT]
[FONT=arial]none on /run/shm type tmpfs (rw,nosuid,nodev)[/FONT]
[FONT=arial]none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=[/FONT][FONT=arial]104857600,mode=0755)[/FONT]
[FONT=arial]none on /sys/fs/pstore type pstore (rw)[/FONT]
[FONT=arial]systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,[/FONT][FONT=arial]name=systemd)[/FONT]
[FONT=arial]gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)[/FONT]
[FONT=arial]/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,[/FONT][FONT=arial]blksize=4096)[/FONT]
[FONT=arial]/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)[/FONT]
[FONT=arial]/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,[/FONT][FONT=arial]blksize=4096)[/FONT]
[FONT=arial]/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)[/FONT]
[FONT=arial]/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,[/FONT][FONT=arial]blksize=4096)[/FONT]
[FONT=arial]/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,[/FONT][FONT=arial]blksize=4096)[/FONT]
[FONT=arial]/dev/sdb3 on /mnt/boot-sav/sdb3 type fuseblk (rw,nosuid,nodev,allow_other,[/FONT][FONT=arial]blksize=4096)[/FONT]
[FONT=arial]/dev/sdb4 on /mnt/boot-sav/sdb4 type fuseblk (rw,nosuid,nodev,allow_other,[/FONT][FONT=arial]blksize=4096)[/FONT]


[FONT=arial]=================== ls:[/FONT]
[FONT=arial]/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent[/FONT]
[FONT=arial]/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb4 size slaves stat subsystem trace uevent[/FONT]
[FONT=arial]/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent[/FONT]
[FONT=arial]/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent[/FONT]
[FONT=arial]/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk ecryptfs fd full fuse hidraw0 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sdb sdb1 sdb2 sdb3 sdb4 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhost-net video0 zero[/FONT]
[FONT=arial]ls /dev/mapper:  control[/FONT]

[FONT=arial]=================== hexdump -n512 -C /dev/sda1[/FONT]
[FONT=arial]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT]
[FONT=arial]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|[/FONT]
[FONT=arial]00000020  00 00 00 00 80 00 80 00  ff 5f 09 00 00 00 00 00  |........._......|[/FONT]
[FONT=arial]00000030  00 64 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.d..............|[/FONT]
[FONT=arial]00000040  f6 00 00 00 01 00 00 00  54 20 76 10 5b 76 10 38  |........T v.[v.8|[/FONT]
[FONT=arial]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/FONT]
[FONT=arial]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/FONT]
[FONT=arial]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/FONT]
[FONT=arial]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/FONT]
[FONT=arial]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/FONT]
[FONT=arial]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/FONT]
[FONT=arial]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/FONT]
[FONT=arial]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/FONT]
[FONT=arial]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/FONT]
[FONT=arial]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/FONT]
[FONT=arial]000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|[/FONT]
[FONT=arial]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/FONT]
[FONT=arial]00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|[/FONT]
[FONT=arial]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/FONT]
[FONT=arial]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/FONT]
[FONT=arial]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/FONT]
[FONT=arial]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/FONT]
[FONT=arial]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|[/FONT]
[FONT=arial]00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|[/FONT]
[FONT=arial]00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|[/FONT]
[FONT=arial]00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|[/FONT]
[FONT=arial]000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|[/FONT]
[FONT=arial]000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|[/FONT]
[FONT=arial]000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|[/FONT]
[FONT=arial]000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|[/FONT]
[FONT=arial]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|[/FONT]
[FONT=arial]00000200[/FONT]
[FONT=arial]ls /mnt/boot-sav/sda2/2:[/FONT]

[FONT=arial]=================== hexdump -n512 -C /dev/sda2[/FONT]
[FONT=arial]00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|[/FONT]
[FONT=arial]00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|[/FONT]
[FONT=arial]00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|[/FONT]
[FONT=arial]00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]00000040  80 01 29 e8 3f 78 dc 4e  4f 20 4e 41 4d 45 20 20  |..).?x.NO NAME  |[/FONT]
[FONT=arial]00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|[/FONT]
[FONT=arial]00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|[/FONT]
[FONT=arial]00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|[/FONT]
[FONT=arial]00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|[/FONT]
[FONT=arial]00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|[/FONT]
[FONT=arial]000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|[/FONT]
[FONT=arial]000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|[/FONT]
[FONT=arial]000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|[/FONT]
[FONT=arial]000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|[/FONT]
[FONT=arial]000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|[/FONT]
[FONT=arial]000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|[/FONT]
[FONT=arial]00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|[/FONT]
[FONT=arial]00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|[/FONT]
[FONT=arial]00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|[/FONT]
[FONT=arial]00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|[/FONT]
[FONT=arial]00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|[/FONT]
[FONT=arial]00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|[/FONT]
[FONT=arial]00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|[/FONT]
[FONT=arial]00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|[/FONT]
[FONT=arial]00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]*[/FONT]
[FONT=arial]000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|[/FONT]
[FONT=arial]000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|[/FONT]
[FONT=arial]000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|[/FONT]
[FONT=arial]000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|[/FONT]
[FONT=arial]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|[/FONT]
[FONT=arial]00000200[/FONT]

[FONT=arial]=================== hexdump -n512 -C /dev/sda4[/FONT]
[FONT=arial]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT]
[FONT=arial]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 10 00  |........?.......|[/FONT]
[FONT=arial]00000020  00 00 00 00 80 00 80 00  ff 77 69 15 00 00 00 00  |.........wi.....|[/FONT]
[FONT=arial]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]00000040  f6 00 00 00 01 00 00 00  ba e2 8a 3c 06 8b 3c d4  |...........<..<.|[/FONT]
[FONT=arial]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/FONT]
[FONT=arial]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/FONT]
[FONT=arial]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/FONT]
[FONT=arial]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/FONT]
[FONT=arial]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/FONT]
[FONT=arial]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/FONT]
[FONT=arial]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/FONT]
[FONT=arial]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/FONT]
[FONT=arial]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/FONT]
[FONT=arial]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/FONT]
[FONT=arial]000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|[/FONT]
[FONT=arial]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/FONT]
[FONT=arial]00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|[/FONT]
[FONT=arial]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/FONT]
[FONT=arial]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/FONT]
[FONT=arial]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/FONT]
[FONT=arial]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/FONT]
[FONT=arial]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|[/FONT]
[FONT=arial]00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|[/FONT]
[FONT=arial]00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|[/FONT]
[FONT=arial]00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|[/FONT]
[FONT=arial]000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|[/FONT]
[FONT=arial]000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|[/FONT]
[FONT=arial]000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|[/FONT]
[FONT=arial]000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|[/FONT]
[FONT=arial]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|[/FONT]
[FONT=arial]00000200[/FONT]

[FONT=arial]=================== hexdump -n512 -C /dev/sdb1[/FONT]
[FONT=arial]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT]
[FONT=arial]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|[/FONT]
[FONT=arial]00000020  00 00 00 00 80 00 80 00  ff 97 b4 18 00 00 00 00  |................|[/FONT]
[FONT=arial]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]00000040  f6 00 00 00 01 00 00 00  a3 be 6a 28 ec 6a 28 62  |..........j(.j(b|[/FONT]
[FONT=arial]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/FONT]
[FONT=arial]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/FONT]
[FONT=arial]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/FONT]
[FONT=arial]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/FONT]
[FONT=arial]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/FONT]
[FONT=arial]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/FONT]
[FONT=arial]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/FONT]
[FONT=arial]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/FONT]
[FONT=arial]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/FONT]
[FONT=arial]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/FONT]
[FONT=arial]000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|[/FONT]
[FONT=arial]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/FONT]
[FONT=arial]00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|[/FONT]
[FONT=arial]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/FONT]
[FONT=arial]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/FONT]
[FONT=arial]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/FONT]
[FONT=arial]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/FONT]
[FONT=arial]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|[/FONT]
[FONT=arial]00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|[/FONT]
[FONT=arial]00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|[/FONT]
[FONT=arial]00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|[/FONT]
[FONT=arial]000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|[/FONT]
[FONT=arial]000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|[/FONT]
[FONT=arial]000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|[/FONT]
[FONT=arial]000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|[/FONT]
[FONT=arial]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|[/FONT]
[FONT=arial]00000200[/FONT]

[FONT=arial]=================== hexdump -n512 -C /dev/sdb2[/FONT]
[FONT=arial]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT]
[FONT=arial]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|[/FONT]
[FONT=arial]00000020  00 00 00 00 80 00 80 00  ff bf 1b 56 00 00 00 00  |...........V....|[/FONT]
[FONT=arial]00000030  03 00 00 00 00 00 00 00  ff bb 61 05 00 00 00 00  |..........a.....|[/FONT]
[FONT=arial]00000040  f6 00 00 00 01 00 00 00  10 7c 47 b7 cc 4b ce 01  |.........|G..K..|[/FONT]
[FONT=arial]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|[/FONT]
[FONT=arial]00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|[/FONT]
[FONT=arial]00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|[/FONT]
[FONT=arial]00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|[/FONT]
[FONT=arial]00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|[/FONT]
[FONT=arial]000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|[/FONT]
[FONT=arial]000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|[/FONT]
[FONT=arial]000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|[/FONT]
[FONT=arial]000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|[/FONT]
[FONT=arial]000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|[/FONT]
[FONT=arial]000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|[/FONT]
[FONT=arial]00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|[/FONT]
[FONT=arial]00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|[/FONT]
[FONT=arial]00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|[/FONT]
[FONT=arial]00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|[/FONT]
[FONT=arial]00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|[/FONT]
[FONT=arial]00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|[/FONT]
[FONT=arial]00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|[/FONT]
[FONT=arial]00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|[/FONT]
[FONT=arial]00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|[/FONT]
[FONT=arial]00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|[/FONT]
[FONT=arial]000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|[/FONT]
[FONT=arial]000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|[/FONT]
[FONT=arial]000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|[/FONT]
[FONT=arial]000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|[/FONT]
[FONT=arial]000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|[/FONT]
[FONT=arial]000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|[/FONT]
[FONT=arial]00000200[/FONT]

[FONT=arial]=================== hexdump -n512 -C /dev/sdb3[/FONT]
[FONT=arial]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT]
[FONT=arial]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 d0 6e  |........?....h.n|[/FONT]
[FONT=arial]00000020  00 00 00 00 80 00 80 00  ff ff 1f 03 00 00 00 00  |................|[/FONT]
[FONT=arial]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]00000040  f6 00 00 00 01 00 00 00  82 48 47 06 5e 47 06 8c  |.........HG.^G..|[/FONT]
[FONT=arial]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/FONT]
[FONT=arial]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/FONT]
[FONT=arial]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/FONT]
[FONT=arial]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/FONT]
[FONT=arial]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/FONT]
[FONT=arial]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/FONT]
[FONT=arial]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/FONT]
[FONT=arial]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/FONT]
[FONT=arial]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/FONT]
[FONT=arial]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/FONT]
[FONT=arial]000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|[/FONT]
[FONT=arial]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/FONT]
[FONT=arial]00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|[/FONT]
[FONT=arial]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/FONT]
[FONT=arial]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/FONT]
[FONT=arial]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/FONT]
[FONT=arial]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/FONT]
[FONT=arial]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|[/FONT]
[FONT=arial]00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|[/FONT]
[FONT=arial]00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|[/FONT]
[FONT=arial]00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|[/FONT]
[FONT=arial]000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|[/FONT]
[FONT=arial]000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|[/FONT]
[FONT=arial]000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|[/FONT]
[FONT=arial]000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|[/FONT]
[FONT=arial]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|[/FONT]
[FONT=arial]00000200[/FONT]

[FONT=arial]=================== hexdump -n512 -C /dev/sdb4[/FONT]
[FONT=arial]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/FONT]
[FONT=arial]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 f0 71  |........?....h.q|[/FONT]
[FONT=arial]00000020  00 00 00 00 80 00 80 00  ff ff 7f 02 00 00 00 00  |................|[/FONT]
[FONT=arial]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]00000040  f6 00 00 00 01 00 00 00  87 d4 48 be 06 49 be a2  |..........H..I..|[/FONT]
[FONT=arial]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/FONT]
[FONT=arial]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/FONT]
[FONT=arial]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/FONT]
[FONT=arial]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/FONT]
[FONT=arial]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/FONT]
[FONT=arial]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/FONT]
[FONT=arial]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/FONT]
[FONT=arial]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/FONT]
[FONT=arial]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/FONT]
[FONT=arial]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/FONT]
[FONT=arial]000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|[/FONT]
[FONT=arial]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/FONT]
[FONT=arial]00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|[/FONT]
[FONT=arial]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/FONT]
[FONT=arial]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/FONT]
[FONT=arial]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/FONT]
[FONT=arial]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/FONT]
[FONT=arial]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|[/FONT]
[FONT=arial]00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|[/FONT]
[FONT=arial]00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|[/FONT]
[FONT=arial]00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|[/FONT]
[FONT=arial]000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|[/FONT]
[FONT=arial]000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|[/FONT]
[FONT=arial]000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|[/FONT]
[FONT=arial]000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|[/FONT]
[FONT=arial]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/FONT]
[FONT=arial]000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|[/FONT]
[FONT=arial]00000200[/FONT]

[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]=================== df -Th:[/FONT]

[FONT=arial]Filesystem     Type       Size  Used Avail Use% Mounted on[/FONT]
[FONT=arial]/cow           overlayfs  785M  127M  618M  18% /[/FONT]
[FONT=arial]udev           devtmpfs   3.9G   12K  3.9G   1% /dev[/FONT]
[FONT=arial]tmpfs          tmpfs      794M  1.2M  793M   1% /run[/FONT]
[FONT=arial]/dev/sdc1      vfat        15G  1.9G   14G  13% /cdrom[/FONT]
[FONT=arial]/dev/loop0     squashfs   923M  923M     0 100% /rofs[/FONT]
[FONT=arial]none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup[/FONT]
[FONT=arial]tmpfs          tmpfs      3.9G  1.1M  3.9G   1% /tmp[/FONT]
[FONT=arial]none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock[/FONT]
[FONT=arial]none           tmpfs      3.9G   76K  3.9G   1% /run/shm[/FONT]
[FONT=arial]none           tmpfs      100M   36K  100M   1% /run/user[/FONT]
[FONT=arial]/dev/sda1      fuseblk    300M  238M   63M  80% /mnt/boot-sav/sda1[/FONT]
[FONT=arial]/dev/sda2      vfat        96M   26M   71M  27% /mnt/boot-sav/sda2[/FONT]
[FONT=arial]/dev/sda4      fuseblk    172G   25G  147G  15% /mnt/boot-sav/sda4[/FONT]
[FONT=arial]/dev/sda5      ext4        28G  3.7G   23G  15% /mnt/boot-sav/sda5[/FONT]
[FONT=arial]/dev/sdb1      fuseblk    198G  3.2G  195G   2% /mnt/boot-sav/sdb1[/FONT]
[FONT=arial]/dev/sdb2      fuseblk    689G  402G  288G  59% /mnt/boot-sav/sdb2[/FONT]
[FONT=arial]/dev/sdb3      fuseblk     25G  3.5G   22G  14% /mnt/boot-sav/sdb3[/FONT]
[FONT=arial]/dev/sdb4      fuseblk     20G   12G  9.0G  56% /mnt/boot-sav/sdb4[/FONT]

[FONT=arial]=================== fdisk -l:[/FONT]

[FONT=arial]Disk /dev/sda: 240.1 GB, 240057409536 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=arial]Disk identifier: 0x0bfcbcc6[/FONT]

[FONT=arial]Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1               1   468862127   234431063+  ee  GPT[/FONT]
[FONT=arial]Partition 1 does not start on physical sector boundary.[/FONT]

[FONT=arial]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes[/FONT]
[FONT=arial]256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=arial]Disk identifier: 0x5b34a80f[/FONT]

[FONT=arial]Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdb1               1  4294967295  [/FONT][2147483647]("tel:2147483647")[FONT=arial]+  ee  GPT[/FONT]
[FONT=arial]Partition 1 does not start on physical sector boundary.[/FONT]

[FONT=arial]Disk /dev/sdc: 16.0 GB, [/FONT][16008609792]("tel:16008609792")[FONT=arial] bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x00000000[/FONT]

[FONT=arial]Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)[/FONT]


[FONT=arial]EFI detected. Please check the options.[/FONT]
[FONT=arial]=================== Advices[/FONT]
[FONT=arial]The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.[/FONT]
[FONT=arial]Do you want to continue?[/FONT]

[FONT=arial]=================== Recommended repair[/FONT]
[FONT=arial]Recommended-Repair[/FONT]
[FONT=arial]This setting will purge (in order to sign-grub upgrade version) and reinstall the grub-efi-amd64-signed of sda5, using the following options: upgrade-grub       sda2/boot/efi,[/FONT]
[FONT=arial]Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot backup-and-rename-efi-files[/FONT]


[FONT=arial]Quantity of real Windows: 1[/FONT]
[FONT=arial]Mount sda2 on /mnt/boot-sav/sda5/boot/efi[/FONT]
[FONT=arial]ls /mnt/boot-sav/sda5/boot/efi/2:[/FONT]
[FONT=arial]No sda5/boot/efi/efi/ ubuntu/mint folder[/FONT]
[FONT=arial]chroot /mnt/boot-sav/sda5 apt-get -y --force-yes update[/FONT]
[FONT=arial]Purge the GRUB of sda5[/FONT]
[FONT=arial]Install last GRUB version in /mnt/boot-sav/sda5/etc/apt/[/FONT][FONT=arial]sources.list[/FONT]
[FONT=arial]chroot /mnt/boot-sav/sda5 apt-get -y --force-yes update[/FONT]
[FONT=arial]grub-efi-amd64-signed available[/FONT]

[FONT=arial]0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 176 not upgraded.[/FONT]
[FONT=arial]DEBCHECK debOK, grub-efi-amd64-signed[/FONT]
[FONT=arial]DEBCHECK debOK[/FONT]
[FONT=arial]shim-signed available[/FONT]
[FONT=arial]linux-signed-generic available[/FONT]
[FONT=arial]Please type: sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda5" apt-get install -fynsudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub* shim-signed linux-signed*[/FONT]
[FONT=arial]Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Microsoft/Boot/bootmgfw.[/FONT][FONT=arial]efi[/FONT]
[FONT=arial]Presence of EFI/Boot file detected: /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Boot/bootx64.efi[/FONT]

[FONT=arial]=================== sda5/etc/grub.d/ :[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 22:15 grub.d[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 21:21 grub.d.bak[/FONT]
[FONT=arial]total 4[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 311 May 30 21:31 25_custom[/FONT]


[FONT=arial]/boot/efi detected in the fstab of sda5: UUID=DC78-3FE8     (sda2)[/FONT]
[FONT=arial]shim-signed available[/FONT]
[FONT=arial]linux-signed-generic available[/FONT]
[FONT=arial]Then type: sudo chroot "/mnt/boot-sav/sda5" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic[/FONT]
[FONT=arial]Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Microsoft/Boot/bootmgfw.[/FONT][FONT=arial]efi[/FONT]
[FONT=arial]Presence of EFI/Boot file detected: /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Boot/bootx64.efi[/FONT]

[FONT=arial]=================== sda5/etc/grub.d/ :[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 22:15 grub.d[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 21:21 grub.d.bak[/FONT]
[FONT=arial]total 72[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  9424 Apr 11 06:51 00_header[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  6058 Apr 10 11:58 05_debian_theme[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 11608 Apr 11 06:51 10_linux[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 10412 Apr 11 06:51 20_linux_xen[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 11692 Apr 11 06:51 30_os-prober[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  1416 Apr 11 06:51 30_uefi-firmware[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root   214 Apr 11 06:51 40_custom[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root   216 Apr 11 06:51 41_custom[/FONT]
[FONT=arial]-rw-r--r-- 1 root root   483 Apr 11 06:51 README[/FONT]




[FONT=arial]=================== sda5/etc/default/grub :[/FONT]

[FONT=arial]# If you change this file, run 'update-grub' afterwards to update[/FONT]
[FONT=arial]# /boot/grub/grub.cfg.[/FONT]
[FONT=arial]# For full documentation of the options in this file, see:[/FONT]
[FONT=arial]#   info -f grub -n 'Simple configuration'[/FONT]

[FONT=arial]GRUB_DEFAULT=0[/FONT]
[FONT=arial]GRUB_HIDDEN_TIMEOUT=0[/FONT]
[FONT=arial]GRUB_HIDDEN_TIMEOUT_QUIET=true[/FONT]
[FONT=arial]GRUB_TIMEOUT=10[/FONT]
[FONT=arial]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX_DEFAULT="[/FONT][FONT=arial]quiet splash"[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX=""[/FONT]

[FONT=arial]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT]
[FONT=arial]# This works with Linux (no patch required) and with any kernel that obtains[/FONT]
[FONT=arial]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT]
[FONT=arial]#GRUB_BADRAM="0x01234567,[/FONT][FONT=arial]0xfefefefe,0x89abcdef,[/FONT][FONT=arial]0xefefefef"[/FONT]

[FONT=arial]# Uncomment to disable graphical terminal (grub-pc only)[/FONT]
[FONT=arial]#GRUB_TERMINAL=console[/FONT]

[FONT=arial]# The resolution used on graphical terminal[/FONT]
[FONT=arial]# note that you can use only modes which your graphic card supports via VBE[/FONT]
[FONT=arial]# you can see them in real GRUB with the command `vbeinfo'[/FONT]
[FONT=arial]#GRUB_GFXMODE=640x480[/FONT]

[FONT=arial]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT]
[FONT=arial]#GRUB_DISABLE_LINUX_UUID=true[/FONT]

[FONT=arial]# Uncomment to disable generation of recovery mode menu entries[/FONT]
[FONT=arial]#GRUB_DISABLE_RECOVERY="true"[/FONT]

[FONT=arial]# Uncomment to get a beep at grub start[/FONT]
[FONT=arial]#GRUB_INIT_TUNE="480 440 1"[/FONT]



[FONT=arial]/boot/efi detected in the fstab of sda5: UUID=DC78-3FE8     (sda2)[/FONT]
[FONT=arial]Unhide GRUB boot menu in sda5/etc/default/grub[/FONT]
[FONT=arial]Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Microsoft/Boot/bootmgfw.[/FONT][FONT=arial]efi[/FONT]
[FONT=arial]Presence of EFI/Boot file detected: /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Boot/bootx64.efi[/FONT]

[FONT=arial]=================== sda5/etc/grub.d/ :[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 22:15 grub.d[/FONT]
[FONT=arial]drwxr-xr-x  2 root root    4096 May 30 21:21 grub.d.bak[/FONT]
[FONT=arial]total 72[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  9424 Apr 11 06:51 00_header[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  6058 Apr 10 11:58 05_debian_theme[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 11608 Apr 11 06:51 10_linux[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 10412 Apr 11 06:51 20_linux_xen[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root 11692 Apr 11 06:51 30_os-prober[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root  1416 Apr 11 06:51 30_uefi-firmware[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root   214 Apr 11 06:51 40_custom[/FONT]
[FONT=arial]-rwxr-xr-x 1 root root   216 Apr 11 06:51 41_custom[/FONT]
[FONT=arial]-rw-r--r-- 1 root root   483 Apr 11 06:51 README[/FONT]




[FONT=arial]=================== sda5/etc/default/grub :[/FONT]

[FONT=arial]# If you change this file, run 'update-grub' afterwards to update[/FONT]
[FONT=arial]# /boot/grub/grub.cfg.[/FONT]
[FONT=arial]# For full documentation of the options in this file, see:[/FONT]
[FONT=arial]#   info -f grub -n 'Simple configuration'[/FONT]

[FONT=arial]GRUB_DEFAULT=0[/FONT]
[FONT=arial]#GRUB_HIDDEN_TIMEOUT=0[/FONT]
[FONT=arial]GRUB_HIDDEN_TIMEOUT_QUIET=true[/FONT]
[FONT=arial]GRUB_TIMEOUT=10[/FONT]
[FONT=arial]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX_DEFAULT="[/FONT][FONT=arial]quiet splash"[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX=""[/FONT]

[FONT=arial]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT]
[FONT=arial]# This works with Linux (no patch required) and with any kernel that obtains[/FONT]
[FONT=arial]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT]
[FONT=arial]#GRUB_BADRAM="0x01234567,[/FONT][FONT=arial]0xfefefefe,0x89abcdef,[/FONT][FONT=arial]0xefefefef"[/FONT]

[FONT=arial]# Uncomment to disable graphical terminal (grub-pc only)[/FONT]
[FONT=arial]#GRUB_TERMINAL=console[/FONT]

[FONT=arial]# The resolution used on graphical terminal[/FONT]
[FONT=arial]# note that you can use only modes which your graphic card supports via VBE[/FONT]
[FONT=arial]# you can see them in real GRUB with the command `vbeinfo'[/FONT]
[FONT=arial]#GRUB_GFXMODE=640x480[/FONT]

[FONT=arial]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT]
[FONT=arial]#GRUB_DISABLE_LINUX_UUID=true[/FONT]

[FONT=arial]# Uncomment to disable generation of recovery mode menu entries[/FONT]
[FONT=arial]#GRUB_DISABLE_RECOVERY="true"[/FONT]

[FONT=arial]# Uncomment to get a beep at grub start[/FONT]
[FONT=arial]#GRUB_INIT_TUNE="480 440 1"[/FONT]



[FONT=arial]/boot/efi detected in the fstab of sda5: UUID=DC78-3FE8     (sda2)[/FONT]

[FONT=arial]*******lspci -nnk | grep -iA3 vga[/FONT]
[FONT=arial]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 750M] [10de:0fe4] (rev a1)[/FONT]
[FONT=arial]Subsystem: Lenovo Device [17aa:3802][/FONT]
[FONT=arial]01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)[/FONT]
[FONT=arial]Subsystem: Lenovo Device [17aa:3977][/FONT]
[FONT=arial]*******[/FONT]

[FONT=arial]grub-install: info: executing modprobe efivars 2>/dev/null.[/FONT]
[FONT=arial]grub-install: info: Looking for /sys/firmware/efi ...[/FONT]
[FONT=arial]grub-install: info: ... not found. Looking for /proc/device-tree ...[/FONT]
[FONT=arial]grub-install: info: ... not found.[/FONT]
[FONT=arial]grub-install: error: /usr/lib/grub/i386-pc/modinfo.[/FONT][FONT=arial]sh doesn't exist. Please specify --target or --directory.[/FONT]
[FONT=arial],.[/FONT]
[FONT=arial]GRUB too old for SecureBoot. Please report this message to [/FONT][EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

[FONT=arial]chroot /mnt/boot-sav/sda5 efibootmgr -v[/FONT]
[FONT=arial]Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.[/FONT]
[FONT=arial]Try 'modprobe efivars' as root.[/FONT]

[FONT=arial]chroot /mnt/boot-sav/sda5 uname -r[/FONT]
[FONT=arial]Kernel: 3.13.0-24-generic[/FONT]
[FONT=arial]WinEFI detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)[/FONT]

[FONT=arial]Reinstall the grub-efi of sda5[/FONT]
[FONT=arial]grub-install: error: /usr/lib/grub/i386-pc/modinfo.[/FONT][FONT=arial]sh doesn't exist. Please specify --target or --directory.[/FONT]
[FONT=arial]grub-install : exit code of grub-install :1[/FONT]
[FONT=arial]Error: no grub*.efi generated. Please report this message to [/FONT][EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

[FONT=arial]Add /mnt/boot-sav/sda5/boot/efi efi entries in /mnt/boot-sav/sda5/etc/grub.d/[/FONT][FONT=arial]25_custom[/FONT]
[FONT=arial]Adding custom /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Microsoft/Boot/bootmgfw.[/FONT][FONT=arial]efi[/FONT]
[FONT=arial]Adding custom /mnt/boot-sav/sda5/boot/efi/[/FONT][FONT=arial]EFI/Boot/bootx64.efi[/FONT]
[FONT=arial]sda2/bootx64.efi already added[/FONT]
[FONT=arial]sda2/bootmgfw.efi already added[/FONT]

[FONT=arial]---- Grub-install verbose[/FONT]
[FONT=arial]/usr/sbin/grub-install: 1: /usr/sbin/grub-install: cannot create n\F0 \F0 T T @T @DD P\E5td \8C\D2\8C\D2L\8C\D2Ll9l9 Q\E5td R\E5td \F0= \F0=n\F0=n /lib64/ld-linux-x86-64.so.2 GNU GNUm: Directory nonexistent[/FONT]
[FONT=arial]+ ELF @ @@@@@\F8 \F8 8 8 @8 @ @@d: d: \F0= \F0=n\F0=n\9E{ \81 [/FONT]
[FONT=arial]/usr/sbin/grub-install: 1: /usr/sbin/grub-install: ELF : not found[/FONT]
[FONT=arial]/usr/sbin/grub-install: 2: /usr/sbin/grub-install: Syntax error: ")" unexpected[/FONT]
[FONT=arial]--------[/FONT]
[FONT=arial]/usr/sbin/grub-install : exit code of grub-install :2[/FONT]
[FONT=arial]---- End of grub-install verbose[/FONT]


[FONT=arial]chroot /mnt/boot-sav/sda5 efibootmgr -v[/FONT]
[FONT=arial]Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.[/FONT]
[FONT=arial]Try 'modprobe efivars' as root.[/FONT]

[FONT=arial]chroot /mnt/boot-sav/sda5 update-grub[/FONT]
[FONT=arial]Generating grub configuration file ...[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-27-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-27-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-24-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-24-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]Unhide GRUB boot menu in sda5/boot/grub/grub.cfg[/FONT]

[FONT=arial]An error occurred during the repair.[/FONT]

[FONT=arial]You can now reboot your computer.[/FONT]
[FONT=arial]Please do not forget to make your BIOS boot on sda (240GB) disk![/FONT]

[FONT=arial]You may want to retry after deactivating the [Backup and rename Windows EFI files] option.[/FONT]

[FONT=arial]The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.

```

I am a complete newbie to the linux world. Any help is appreciated.[/FONT]

---

### Post by ankur-1502 on 2014-05-31
Hi,

I am a complete newbie and am struggling with ubuntu UEFI installation on my Lenovo y500. I created a live USB using unebootin (for EFI support). Initially I was getting a blank screen after selecting "Try Ubuntu" or "Install Ubuntu". I made some changes to /boot/grub/grub.conf as suggested in [http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500). After this I can boot via USB and installer also seems to be running. Now the problem is that while installation, the installer will not detect windows 8.1 and hence I am unable to proceed.

Any help is appreciated.

---

### Post by LastDino on 2014-05-31
Please use code tags around boot info summery to make your post readable. 

Read this Wiki page to get a leg up on UEFI booting.

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by ajgreeny on 2014-05-31
As Win 8 is already installed in UEFI mode Ubuntu **MUST** also be in UEFI mode or you will need to mess around changing the UEFI setup each time you want to boot from one OS to the other.

See all the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for all the details of UEFI, dual boots, and hopefull it will tell you everything you may need to do.

EDIT:
Too slow, again!

---

### Post by LastDino on 2014-05-31
> **ajgreeny said:**
> As Win 8 is already installed in UEFI mode Ubuntu **MUST** also be in UEFI mode or you will need to mess around changing the UEFI setup each time you want to boot from one OS to the other.

See all the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for all the details of UEFI, dual boots, and hopefull it will tell you everything you may need to do.

EDIT:
Too slow, again!

Well, you did link to the latest page, so :P

---

### Post by squakie on 2014-05-31
I don't know why it would need to detect Windows 8 to install unless you are trying a wubi install - in which case wubi is no longer supported and doesn't work with the new partitioning scheme that Windows 8 requires.  You do need to do an actual install, so if you want to keep Windows 8 you need to create the space on your hard disk first.

Oldfred has quite extensive knowledge on all of this and has a link to a lot information you should read before trying this with Windows 8.  The following is from one of his posts dealing with Intel BIOS settings and installing with Windows 8.  There is also a link in his signature to a lot of information you need.

 		                                                                                                                                                    1 Day Ago                                                                                                                                                                                                     [#2]("http://ubuntuforums.org/showthread.php?t=2227071&p=13037311#post13037311")                                                                                                                                                                                      		
  		 			 				 				 					 						 	[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						Forums Moderator 					 					 						[IMG]http://ubuntuforums.org/images/rank_uf_moderator_2013-07.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateJun 2009LocationChicago SuburbsBeansHidden!                                                    
DistroUbuntu 12.04 Precise Pangolin 					 					 				
 			 		
 	
  	 		 		 		 		[h=2]Re: Installed Lubuntu, now my Windows 8.1 won't boot[/h] 		 				 				 		 			 				[INDENT] 					Instructions for installing include turning off Intel SRT before installing. :smile:

Also have to turn off Windows fast boot or always on hibernation or you  may have major issues. And often better to have secure boot off but not  absolutely required. Grub menu may not let you boot Windows with secure  boot on, but you can boot both Ubuntu & Windows from UEFI menu.

See if in UEFI/BIOS you can turn off Intel SRT.
Post link to BootInfo report from Boot-Repair.
What system & video do you have.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support...ts/chpsts/imsm]("http://www.intel.com/p/en_US/support/highlights/chpsts/imsm")
[http://software.intel.com/en-us/arti...art-technology]("http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology")
[http://download.intel.com/support/mo...user_guide.pdf]("http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf")

SRT is the same for all vendors.
      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

More info on UEFI install with screen shots in first links and Ultrabooks in the link in my signature. 				[/INDENT] 			
  			   		
 			 				 			 			 				[COLOR=Navy]For info on UEFI boot install & repair:
[/COLOR] [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
Please use Thread Tools above first post to close thread when/if answered completely.

---

### Post by squakie on 2014-05-31
I didn't want to add on right after the info from oldfred, so please forgive me adding another post:

Sometimes after installing Ubuntu in dual-boot with Windows 8 you need to use boot-repair in order for everything to show in the boot menu.

Also, can you clarify where you are at in the install process that you have this problem and what you expected to see?

---

### Post by newbie2244 on 2014-05-31
I don't know if this applies to your Grub listing,  but, on my system I have to find this file in the Grub listing -- UEFI bkpbootmgfw.efi -- and click on it in order for WIndows 8 to load.

---

### Post by oldfred on 2014-05-31
Lots of discussion in these threads.

 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

If you install in BIOS/Legacy/CSM mode you can only dual boot from UEFI/BIOS menu not grub. If you use Boot-Repair you can convert install to UEFI boot mode. It un-installs grub-pc(BIOS) and installs grub-efi(UEFI).

If you have bkpbootmgfw.efi then Boot-Repair has run its buggy UEFI fix. That is for those systems that only boot the Windows UEFI entry in Windows and renames the original Windows file to be grub. So you boot to grub with the Windows UEFI entry and can only boot Windows from the backed up bkpbootmgfw.efi file in grub menu.
There are several other work arounds for the UEFI only boot Windows issue.

---

### Post by oldfred on 2014-05-31
Merged your two threads. Please post only one thread per issue and both were boot issues.

---

### Post by ankur-1502 on 2014-06-01
Thank you all for the replies. I was finally able to install in UEFI. But I am stuck again with NVIDIA graphics. Here is what I have done so far.

1. Created a Live USB, edited the grub.conf from within windows to set the gfxmode value to 1920X1080 and updated the menuentry corresponding to Install Linux to replace quiet splash to nomodeset=1. This was suggested in following URL
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)

```
if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=1920X1080    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity nomodeset=1 --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

```

2. The Live USB would boot then and I was able to venture into Install Ubuntu. The installed still did not detect the existing Win 8.1 installation. I then followed the steps mentioned in [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html) and was able to install linux. On rebooting, I am able to see the grub menu :)

3. Choosing to boot into Ubuntu would still present a blank screen. I tried steps mentioned in [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) and realized the <ctrl>+<alt>+<F1> did not bring up any terminal :(. While trying different things, I stumbled upon an option in grub menu to edit the commands. I modified gfxmode $linux_gfx_mode to set gfxmode=1920X1080 and replace quiet splash to set nomodeset=1. I was able to boot into Ubuntu after that.

4. I had read a some things about NVIDIA creating problems and thought it would be a good idea to update nvidia drivers. I downloaded the nvidia drivers (.run file) and tried to execute it from within the terminal. It gave me the error as mentioned in
[http://askubuntu.com/questions/149206/how-to-install-nvidia-run](http://askubuntu.com/questions/149206/how-to-install-nvidia-run).

5. This is where I think I went wrong. I mixed two sets of instructions. I went to tty1 shell (ctrl+shift+F1) as described in (top voted answer in the above link) and ran following commands (as described in the blank screen sticky [post]("http://ubuntuforums.org/showthread.php?t=1743535"))
```

[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install nvidia-current  
sudo nvidia-xconfig 
sudo apt-get update
```

After this everything seems to be a mess :(. All I get is a blank screen with a blinking cursor. I cannot goto kernel shell and run any commands either.

What seems weird is that if I try to boot via live USB, my resolution goes berserk. I get triplicated displays on top 1/4 screen and everything below that is blank. Any suggestions as what to do next is highly appreciated. I want to avoid re-installing the Ubuntu OS.

---

### Post by ankur-1502 on 2014-06-01
I am new to this forum. I do not know if my latest issue qualifies as a separate thread or should I continue posting here. Any suggestions?

---

### Post by oldfred on 2014-06-01
You cannot mix nVidia versions. You have to totally purge one before attempting to install another.
Usually best to use the version from the repository. It usually is pretty current and only if a very new nVidia card or chip may the beta version directly from nVidia be better, but then using a ppa may be the easier way to install that. But each is different and must be purged before next install.
And nomodeset will be required if you boot without nVidia driver.

       Shows various install methods for nVidia. 13.04 but still the same
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

Some of the purge instructions:
[http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/](http://choorucode.com/2013/02/07/how-to-fix-nvidia-driver-failure-on-ubuntu/)

Shows any file with nvidia in name, lots of files.
 sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*

dkms status
 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


 # Install version you prefer, I have a desktop with 9600GT which uses the current versions. In some of my test installs I also have installed the experimental version and it worked for me.
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install  nvidia-current-updates 
sudo apt-get install nvidia-settings-updates
sudo dpkg-reconfigure nvidia-current-updates 
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.

---

### Post by ankur-1502 on 2014-06-01
Appreciate the quick response. I do have one question though (Pardon my ignorance). I am unable to access terminal. Do you think I should re-install the OS and then proceed with the drivers as you mentioned?

Thanks

---

### Post by oldfred on 2014-06-01
You should be able to access terminal.
If in Unity it it the top most left Icon and opens a search box. type terminal.
Keyboard Shortcut: Ctrl + Alt + T

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ankur-1502 on 2014-06-01
I am not in Unity UI. I cannot even access that. When I select Ubuntu in grub, it starts loading ubuntu. Then after a short while (<1sec) I see a screen with following message

```

No Caching mode page found
Assuming drive cache : write through
No Caching mode page found
Assuming drive cache : write through
No Caching mode page found
Assuming drive cache : write through

```

After seeing this message for about a second, the screen turns complete blank and that it where it seems to stay for ever. In one of my tries, I did wait for about 20 min for things to load but to no avail.

I have however made some progress, I was able to boot into the live USB. I will keep researching. Any pointers are appreciated.

Thanks

---

### Post by oldfred on 2014-06-01
Are you using nomodeset?

If nVidia driver not working then you need nomodeset. If you do not see grub menu hold shift key from BIOS, or if UEFI press escape key.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ankur-1502 on 2014-06-01
Indeed I am. Here is what my linux command looks like

```

/boot/vmlinuz-2.13.0-27 generic.efi.signed root=UUID=<some numbers> ro nomodeset=1 $vt_handoff

```

I have tried booting with both quiet splash and nomodeset and also without $vt_handoff. I think I am going to reinstall Ubuntu and not make the mistake that I did this time.

---

### Post by squakie on 2014-06-01
change nomodeset=1 to just nomodeset

---

### Post by ankur-1502 on 2014-06-01
Thank you every one and a huge shout out to oldfred for being incredibly patient. I have the graphics driver and dual boot also works like a charm.
It is time to mark this solved :D

---

