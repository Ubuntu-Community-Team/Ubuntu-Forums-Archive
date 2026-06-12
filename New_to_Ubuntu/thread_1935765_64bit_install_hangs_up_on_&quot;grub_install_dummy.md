---
title: "64bit install hangs up on &quot;grub install dummy&quot;, Urgent Assistance Needed!"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Jake5 on 2012-03-05
Hi,
I have in the past successfully installed the 64 bit 11.10 on this system. It crashed, my fault.

When attempting to re-install I have checked three different disks and they all came back clean. 
All of them have hung up on the line on the live disk GUI install line:

Running "grub-install dummy"...

I have also attempted to not run the live version and just install 11.10. 

This would not normally be a matter of such urgency, however I have an appointment with a friend on Thursday who is interested in building a HIGH quality video editing studio. I don't want to scare him off because my box is down...Any help would be greatly appreciated.

---

### Post by yeats on 2012-03-05
> It crashed, my fault.

Can you provide some details about what happened?  They may shed some light on a problem you're not noticing that someone else would see.


> When attempting to re-install I have checked three different disks and they all came back clean. 
All of them have hung up on the line on the live disk GUI install line:

Running "grub-install dummy"...

There's a bug report on what appears to be the same issue - I don't see any workarounds in the bug comments, but you might do some web searching to see what others may have done:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/913321](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/913321)

I'll add that you might attempt installation using the alternate installer:

[http://www.ubuntu.com/download/ubuntu/alternative-download#alternate](http://www.ubuntu.com/download/ubuntu/alternative-download#alternate)

---

### Post by Jake5 on 2012-03-05
> **yeats said:**
> Can you provide some details about what happened?  They may shed some light on a problem you're not noticing that someone else would see.

Would Love to, Thanks for responding, I was attempting to uninstall the gnome desktop and I ran the code to do so in Unity, It started deleting everything, Icons DIssapearing at an alarming rate, I stopped the process and attempted re-installation of 11.10.

this was the line of code that started this off,
```
 sudo apt-get remove libgtk-3-common
```

---

### Post by Jake5 on 2012-03-05
In the next hour or so I will be attempting an install of Kubuntu 64 bit so I can see if it will hang up too. Pretty sure it will as its still a ubu variant.

---

### Post by Jake5 on 2012-03-05
For some reason Kubuntu 64bit installed just fine, ran right past the Grub stuff, I have no idea why or what the problem with ubuntu was. Runs like a dream, at least for now, All I needed was a working 64 bit to show off some video capabilities, so for now, problem solved, However I am not going to mark the thread as solved for a while because I want my Unity Desktop back, so If any of the info I have provided gives anyone a clue as to why the ubu 64bit wont load, I would love to hear your thoughts.

---

### Post by Jake5 on 2012-03-08
Bump...
Showed off my video capabilities and would like to get ubuntu back, tried installing a few more times, the 32 bit works fine but can't access all of my RAM. I would like the 64 bit version back, if anyone has any ideas let me know please!

---

### Post by Jake5 on 2012-03-10
bump. 
Tried installing 64 bit kubuntu again and it stalled up again on installing grub-dummy

---

### Post by Jake5 on 2012-03-10
bump

---

### Post by oldfred on 2012-03-11
Please describe system a bit more. Are you using defaults or manual install to existing partitions? If manual install where are you choosing to install grub2's boot loader to, the MBR of the drive or a PBR?

Was drive ever in RAID or are you using RAID or LVM? RAID leaves meta-data that interferes with the standard desktop install. Alternate installer works with RAID or LVM.

If installed post link to boot info script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Jake5 on 2012-03-11
Thanks for your help!
Here is the boot info from boot repair
```
  1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35  36  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  71  72  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  88  89  90  91  92  93  94  95  96  97  98  99 100 101 102 103 104 105 106 107 108 109 110 111 112 113 114 115 116 117 118 119 120 121 122 123 124 125 126 127 128 129 130 131 132 133 134 135 136 137 138 139 140 141 142 143 144 145 146 147 148 149 150 151 152 153 154 155 156 157 158 159 160 161 162 163 164 165 166 167 168 169 170 171 172 173 174 175 176 177 178 179 180 181 182 183 184 185 186 187 188 189 190 191 192 193 194 195 196 197 198 199 200 201 202 203 204 205 206 207 208 209 210 211 212 213 214 215 216 217 218 219 220 221 222 223 224 225 226 227 228 229 230 231 232 233 234 235 236 237 238 239 240 241 242 243 244 245 246 247 248 249 250 251 252 253 254 255 256 257 258 259 260 261 262 263 264 265 266 267 268 269 270 271 272 273 274 275 276 277 278 279 280 281 282 283 284 285 286 287 288 289 290 291 292 293 294 295 296 297 298 299 300 301 302 303 304 305 306 307 308 309 310 311 312 313 314 315 316 317 318 319 320 321 322 323 324 325 326 327 328 329 330 331 332 333 334 335 336 337 338 339 340 341 342 343 344 345 346 347 348 349 350 351 352 353 354 355 356 357 358 359 360 361 362 363 364 365 366 367 368 369 370 371 372 373 374 375 376 377 378 379 380 381 382 383 384 385 386 387 388 389 390 391 392 393 394 395 396 397 398 399 400 401 402 403 404 405 406 407 408 409 410 411 412 413 414 415 416 417 418 419 420 421 422 423 424 425 426 427 428 429 430 431 432 433 434 435 436 437 438 439 440 441 442 443 444 445 446 447 448 449 450 451 452 453 454 455 456 457 458 459 460 461 462 463 464 465 466 467 468 469 470 471 472 473 474 475 476 477 478 479 480 481 482 483 484 485 486 487 488 489 490 491 492 493 494 495 496 497 498 499 500 501 502                 Boot Info Script 0.60-git      [23 Feb 2012]   ============================= Boot Info Summary: ===============================   => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for (,msdos1)/boot/grub on this drive.  => Windows is installed in the MBR of /dev/sdb.  sda1: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:  Ubuntu 11.10     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda2: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  Unknown     Boot sector info:   sda5: __________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:   sdb1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP: NTFS     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files:          ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *             63   967,129,064   967,129,002  83 Linux /dev/sda2         967,129,065   976,768,064     9,639,000   5 Extended /dev/sda5         967,129,128   976,768,064     9,638,937  82 Linux swap / Solaris   Drive: sdb _____________________________________________________________________  Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes 255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sdb1               2,048 3,907,024,895 3,907,022,848   7 NTFS / exFAT / HPFS   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/sda1        c0958442-086a-4ca4-a162-dd04cef85603   ext4        /dev/sda5        93dd3589-6606-48c0-aee9-00930ad6502d   swap        /dev/sdb1        922076B020769B45                       ntfs       Elements  ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)   =========================== sda1/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga   insmod video_bochs   insmod video_cirrus }  insmod part_msdos insmod ext2 set root='(hd0,msdos1)' search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=auto   load_video   insmod gfxterm   insmod part_msdos   insmod ext2   set root='(hd0,msdos1)'   search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603   set locale_dir=($root)/boot/grub/locale   set lang=en_US   insmod gettext fi terminal_output gfxterm if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### if [ ${recordfail} != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3; then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode if [ "$linux_gfx_mode" != "text" ]; then load_video; fi menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	set gfxpayload=$linux_gfx_mode 	insmod gzio 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	linux	/boot/vmlinuz-3.0.0-16-generic-pae root=UUID=c0958442-086a-4ca4-a162-dd04cef85603 ro   quiet splash vt.handoff=7 	initrd	/boot/initrd.img-3.0.0-16-generic-pae } menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod gzio 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	echo	'Loading Linux 3.0.0-16-generic-pae ...' 	linux	/boot/vmlinuz-3.0.0-16-generic-pae root=UUID=c0958442-086a-4ca4-a162-dd04cef85603 ro recovery nomodeset  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-3.0.0-16-generic-pae } submenu "Previous Linux versions" { menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	set gfxpayload=$linux_gfx_mode 	insmod gzio 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=c0958442-086a-4ca4-a162-dd04cef85603 ro   quiet splash vt.handoff=7 	initrd	/boot/initrd.img-3.0.0-16-generic } menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod gzio 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	echo	'Loading Linux 3.0.0-16-generic ...' 	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=c0958442-086a-4ca4-a162-dd04cef85603 ro recovery nomodeset  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-3.0.0-16-generic } menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	set gfxpayload=$linux_gfx_mode 	insmod gzio 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c0958442-086a-4ca4-a162-dd04cef85603 ro   quiet splash vt.handoff=7 	initrd	/boot/initrd.img-3.0.0-12-generic } menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod gzio 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	echo	'Loading Linux 3.0.0-12-generic ...' 	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c0958442-086a-4ca4-a162-dd04cef85603 ro recovery nomodeset  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-3.0.0-12-generic } } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	linux16	/boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set=root c0958442-086a-4ca4-a162-dd04cef85603 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### if [ "x${timeout}" != "x-1" ]; then   if keystatus; then     if keystatus --shift; then       set timeout=-1     else       set timeout=0     fi   else     if sleep --interruptible 3 ; then       set timeout=0     fi   fi fi ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ### --------------------------------------------------------------------------------  =============================== sda1/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda1 during installation UUID=c0958442-086a-4ca4-a162-dd04cef85603 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda5 during installation UUID=93dd3589-6606-48c0-aee9-00930ad6502d none            swap    sw              0       0 --------------------------------------------------------------------------------  =================== sda1: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)   346.145732403 = 371.671150080  boot/grub/core.img                             1   86.219253063 = 92.577218048   boot/grub/grub.cfg                             1    1.668971539 = 1.792044544    boot/initrd.img-3.0.0-12-generic               1    6.036296368 = 6.481423872    boot/initrd.img-3.0.0-16-generic               3    6.381865978 = 6.852476416    boot/initrd.img-3.0.0-16-generic-pae           3   50.132495403 = 53.829357056   boot/vmlinuz-3.0.0-12-generic                  1    5.824664593 = 6.254185984    boot/vmlinuz-3.0.0-16-generic                  1    0.902930737 = 0.969514496    boot/vmlinuz-3.0.0-16-generic-pae              2    6.036296368 = 6.481423872    initrd.img                                     3    1.668971539 = 1.792044544    initrd.img.old                                 1    5.824664593 = 6.254185984    vmlinuz                                        1   50.132495403 = 53.829357056   vmlinuz.old                                    1  ======================== Unknown MBRs/Boot Sectors/etc: ========================  Unknown BootLoader on sda2  00000000  6c 48 00 01 74 48 00 01  7c 48 00 01 84 48 00 01  |lH..tH..|H...H..| 00000010  8c 48 00 01 94 48 00 01  9c 48 00 01 a4 48 00 01  |.H...H...H...H..| 00000020  ac 48 00 01 b4 48 00 01  bc 48 00 01 c4 48 00 01  |.H...H...H...H..| 00000030  cc 48 00 01 d4 48 00 01  dc 48 00 01 e4 48 00 01  |.H...H...H...H..| 00000040  ec 48 00 01 f4 48 00 01  fc 48 00 01 04 49 00 01  |.H...H...H...I..| 00000050  0c 49 00 01 14 49 00 01  1c 49 00 01 24 49 00 01  |.I...I...I..$I..| 00000060  2c 49 00 01 34 49 00 01  3c 49 00 01 44 49 00 01  |,I..4I..<I..DI..| 00000070  4c 49 00 01 54 49 00 01  5c 49 00 01 64 49 00 01  |LI..TI..\I..dI..| 00000080  6c 49 00 01 74 49 00 01  7c 49 00 01 84 49 00 01  |lI..tI..|I...I..| 00000090  8c 49 00 01 94 49 00 01  9c 49 00 01 a4 49 00 01  |.I...I...I...I..| 000000a0  ac 49 00 01 b4 49 00 01  bc 49 00 01 c4 49 00 01  |.I...I...I...I..| 000000b0  cc 49 00 01 d4 49 00 01  dc 49 00 01 e4 49 00 01  |.I...I...I...I..| 000000c0  ec 49 00 01 f4 49 00 01  fc 49 00 01 04 4a 00 01  |.I...I...I...J..| 000000d0  0c 4a 00 01 14 4a 00 01  1d 4a 00 01 26 4a 00 01  |.J...J...J..&J..| 000000e0  2f 4a 00 01 38 4a 00 01  41 4a 00 01 4a 4a 00 01  |/J..8J..AJ..JJ..| 000000f0  53 4a 00 01 5c 4a 00 01  65 4a 00 01 6e 4a 00 01  |SJ..\J..eJ..nJ..| 00000100  76 4a 00 01 7e 4a 00 01  86 4a 00 01 8e 4a 00 01  |vJ..~J...J...J..| 00000110  96 4a 00 01 9e 4a 00 01  a6 4a 00 01 ae 4a 00 01  |.J...J...J...J..| 00000120  b6 4a 00 01 be 4a 00 01  c6 4a 00 01 ce 4a 00 01  |.J...J...J...J..| 00000130  d8 4a 00 01 e2 4a 00 01  ec 4a 00 01 f6 4a 00 01  |.J...J...J...J..| 00000140  00 4b 00 01 0a 4b 00 01  14 4b 00 01 1e 4b 00 01  |.K...K...K...K..| 00000150  28 4b 00 01 32 4b 00 01  3c 4b 00 01 46 4b 00 01  |(K..2K..<K..FK..| 00000160  50 4b 00 01 5a 4b 00 01  64 4b 00 01 6e 4b 00 01  |PK..ZK..dK..nK..| 00000170  78 4b 00 01 82 4b 00 01  96 4b 00 01 a0 4b 00 01  |xK...K...K...K..| 00000180  aa 4b 00 01 b2 4b 00 01  ba 4b 00 01 c2 4b 00 01  |.K...K...K...K..| 00000190  cc 4b 00 01 d4 4b 00 01  dc 4b 00 01 e4 4b 00 01  |.K...K...K...K..| 000001a0  ec 4b 00 01 f4 4b 00 01  fc 4b 00 01 04 4c 00 01  |.K...K...K...L..| 000001b0  0c 4c 00 01 1c 4c 00 01  25 4c 00 01 2e 4c 00 fe  |.L...L..%L...L..| 000001c0  ff ff 82 fe ff ff 3f 00  00 00 19 14 93 00 00 00  |......?.........| 000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| * 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200   =============================== StdErr Messages: ===============================  xz: (stdin): Compressed data is corrupt  ADDITIONAL INFORMATION : **************** log of boot-repair 2012-03-11__11h00 **************** boot-repair version : 3.16-0ppa10~oneiric boot-sav version : 3.17-0ppa20~oneiric glade2script version : 0.3.2.1-0ppa7~oneiric internet: connected python-software-properties version : 0.81.13.3  0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded. dpkg-preconfigure: unable to re-open stdin: LIVESESSION is : no (Ubuntu 11.10 , oneiric , Ubuntu , i686  ) BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes. BYTES_BEFORE_PART[2] (sdb) = 2048 sectors * 512 bytes = 1048576 bytes.  OSPROBER: /dev/sda1:The OS now in use - Ubuntu 11.10 CurrentSession:linux  BLKID: /dev/sdb1: LABEL="Elements" UUID="922076B020769B45" TYPE="ntfs" /dev/sda1: UUID="c0958442-086a-4ca4-a162-dd04cef85603" TYPE="ext4" /dev/sda5: UUID="93dd3589-6606-48c0-aee9-00930ad6502d" TYPE="swap"  1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS. Total of 1 OS detected on sda disk. sudo: cannot get working directory TABLE_TYPE of sda is MSDos TABLE_TYPE of sdb is MSDos sda1 : sda, not-sepboot, grub-install, grub2 , update-grub, apt-get, 32, with boot, , with-os, no-gpt, notEFItable, fstab-without-efi. sdb1 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb1, no-os, no-gpt, notEFItable, no-fstab.  PARTED:  Model: ATA Hitachi HDS72105 (scsi) Disk /dev/sda: 500GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End    Size    Type      File system     Flags 1      32.3kB  495GB  495GB   primary   ext4            boot 2      495GB   500GB  4935MB  extended 5      495GB   500GB  4935MB  logical   linux-swap(v1)   Model: WD Ext HDD 1021 (scsi) Disk /dev/sdb: 2000GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End     Size    Type     File system  Flags 1      1049kB  2000GB  2000GB  primary  ntfs   MOUNT: /dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) fusectl on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) gvfs-fuse-daemon on /home/jake5/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jake5) /dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)   /sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent /sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent /sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /dev:  ati autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 vga_arbiter zero /dev/mapper:  control  DF:  Filesystem    Type    Size  Used Avail Use% Mounted on /dev/sda1     ext4    454G   11G  421G   3% / udev      devtmpfs    2.3G   12K  2.3G   1% /dev tmpfs        tmpfs    927M  788K  926M   1% /run none         tmpfs    5.0M     0  5.0M   0% /run/lock none         tmpfs    2.3G  136K  2.3G   1% /run/shm /dev/sdb1  fuseblk    1.9T  793G  1.1T  43% /mnt/boot-sav/sdb1  FDISK:  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x0009f6e9  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          63   967129064   483564501   83  Linux /dev/sda2       967129065   976768064     4819500    5  Extended /dev/sda5       967129128   976768064     4819468+  82  Linux swap / Solaris  Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes 255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x0004b274  Device Boot      Start         End      Blocks   Id  System /dev/sdb1            2048  3907024895  1953511424    7  HPFS/NTFS/exFAT    ************************Before mainwindow FSCK_ACTION no PASTEBIN_ACTION yes recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes UNHIDEBOOT_ACTION yes (10s), noflag (sda1) PART_TO_REINSTALL_GRUB sda1, PART_TO_REINSTALL_GRUB_PURGE sda1, FORCE_GRUB all (sda) REMOVABLEDISK no USE_SEPARATEBOOTPART no (sdb1) grub2 (sda1) UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) ( ) internet: connected  ************************Actions FSCK_ACTION no PASTEBIN_ACTION yes bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes UNHIDEBOOT_ACTION no (10s), noflag (sda1) PART_TO_REINSTALL_GRUB sda1, PART_TO_REINSTALL_GRUB_PURGE sda1, FORCE_GRUB all (sda) REMOVABLEDISK no USE_SEPARATEBOOTPART no (sdb1) grub2 (sda1) UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda 1) internet: connected 

```

---

### Post by Jake5 on 2012-03-11
Deleted as illegible. see next post for link to boot script.

---

### Post by Jake5 on 2012-03-11
Okay, Neither of those look to be any helpful, try this:
[http://paste.ubuntu.com/879157/](http://paste.ubuntu.com/879157/)

Sorry

---

### Post by Jake5 on 2012-03-11
> **Jake5 said:**
> Okay, Neither of those look to be any helpful, try this:
[http://paste.ubuntu.com/879157/](http://paste.ubuntu.com/879157/)

Sorry
As you see in here there is a partition called Elements, This is my external HDD. I looked it over and couldn't really translate anything past that.

---

### Post by oldfred on 2012-03-11
It looks like grub is installed normally in sda's MBR and boots from sda1.

There was(is?) a bug in grub with large / (root) partitions where it would get lost. You have core.img at 371 and most of the rest of grub near the beginning of the partition.

I normally suggest a 10 to 25GB / (root) partition and then use the rest for /home. But you can test if my theory is correct just by using gparted to shrink your sda1 to 50GB or less. You may still have to reinstall grub but over half of those I have suggested this to have said it worked. (But not all:frown:). Or you can reinstall with a smaller / and large /home.

---

### Post by Jake5 on 2012-03-11
So This is the shot from gparted, Not really sure what to do from here, any further assistance would be greatly appreciated.

---

### Post by oldfred on 2012-03-11
You cannot edit partitions you are running the system from. You need to use the Ubuntu liveCD or download a gparted liveCD. Even then you often have to click on swap and swapoff as liveCDs will use a swap if found to speed things up.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

