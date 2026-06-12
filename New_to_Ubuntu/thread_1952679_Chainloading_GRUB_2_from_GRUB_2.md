---
title: "Chainloading GRUB 2 from GRUB 2"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by avnd on 2012-04-04
Hello!

I have a laptop with multiple OS's. My partition structure is as follows.

/dev/sda1 - GRUB
/dev/sda2 - Windows
/dev/sda3 - Extended
    /dev/sda5 - Data (NTFS)
    /dev/sda6 - Swap
    /dev/sda7 - Arch Linux
    /dev/sda8 - Arch Linux (minimal install)
    /dev/sda9 - Crunchbang Linux
    /dev/sda10- Data (Ext4)

My booting structure is as follows.
I have GRUB 2 installed on the hard drive's MBR. It looks for the grub.cfg on the GRUB partition. I installed the GRUB from a Live CD. So the regular scripts that create and update grub.cfg don't exist on my computer. I have to update grub.cfg manually and I don't mind that since it makes things easier in other ways.

My current grub.cfg is as follows

```
(hd0,1)/boot/grub/grub.cfg
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Config file for GRUB2 - The GNU GRand Unified Bootloader

# DEVICE NAME CONVERSIONS
#
# Linux		GRUB
#-------------------------------
# /dev/fd0	(fd0)
# /dev/sda	(hd0)
# /dev/sdb2	(hd1,2)
# /dev/sda3	(hd0,3)

# Timeout for menu (in seconds)
set timeout=60

# Default option to boot (number starts from 0)
set default=0

# Menu color options
set menu_color_normal=white/black
set menu_color_highlight=black/white
set gfxpayload=1366x768

# Menu Entry Number ---> 0
menuentry "Windows" 	{
	set root=(hd0,2)
	chainloader (hd0,2)+1
}

# Menu Entry Number ---> 1
menuentry "Arch" 	{
	set root=(hd0,7)
	chainloader (hd0,7)+1
}

# Menu Entry Number ---> 2
menuentry "Arch Test" 	{
	set root=(hd0,8)
	chainloader (hd0,8)+1
}

# Menu Entry Number ---> 3
menuentry "Crunchbang"	{
	set root=(hd0,9)
	chainloader (hd0,9)+1
}

```


My problem is the following:
I am able to boot into Windows and the 2 Arch Linux installations fine. But when I choose the Crunchbang option, I get the following error. 

```

Error: Invalid signature.
Press any key to continue....

```

I have installed the respective bootloaders for Arch Linux and Crunchbang on the specific partitions. The only difference I can see is that Arch has GRUB Legacy as the bootloader in the partition whereas Crunchbang has GRUB 2. 

Does GRUB 2 require a different syntax to be chainloaded? Or is it some other issue I'm overlooking?

I have actually tried re-installing Crunchbang once again. And the problem remains the same.

Kindly provide your opinions.

Thanks.

---

### Post by oldfred on 2012-04-04
I know this runs well in Ubuntu, and think it works in most other Linux.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Boot script will tell use what is installed where as it looks at MBR & PBR's to see what is installed.

---

### Post by avnd on 2012-04-05
> I know this runs well in Ubuntu, and think it works in most other Linux.

I still havn't set up the internet connection in Arch linux and I think it will take me 2 more days to read all that stuff and set it up. And I still can't boot into my Crunchbang.

So, will I be able to install bootinfoscript and the dependecies > Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

in a Live CD environment and run it from the Live CD?

Thanks.

---

### Post by avnd on 2012-04-05
In order to install bootinfo script on my laptop, I had to setup wireless internet access on my laptop. I'm running into some trouble. The arch wiki says the following 

> A small percentage of wireless chipsets also require firmware, in addition to a corresponding driver. If the wireless chipset requires firmware, you are likely to receive this error when bringing the interface up:
# ip link set wlan0 up
SIOCSIFFLAGS: No such file or directory
If unsure, invoke /usr/bin/dmesg to query the kernel log for a firmware request from the wireless chipset. Example output from an Intel chipset which requires and has requested firmware from the kernel at boot:
$ dmesg | grep firmware
firmware: requesting iwlwifi-5000-1.ucode
If there is no output, it may be concluded that the system's wireless chipset does not require firmware.
Note: Wireless chipset firmware packages (for cards which require them) are pre-installed under /lib/firmware in the live environment (on CD/USB stick) but must be explicitly installed to your actual system to provide wireless functionality after you reboot into it! Package selection and installation is covered later in this guide. Ensure installation of both your wireless module and firmware during the package selection step! See Wireless Setup if you are unsure about the requirement of corresponding firmware installation for your particular chipset. This is a very common error.

When I run 
```

$ dmesg | grep firmware
```

I get 

```
[ 5.697965] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.2 build 35905
```

The message says that firmware has been loaded, but according to the wiki, I should not be getting any messages if everything went alright.

---

### Post by oldfred on 2012-04-05
Can you just run the boot  script from a Ubuntu liveCD? And do you have a Ethernet connection as that avoids any wireless driver issues. Normally Ubuntu is best installed with an Ethernet connection so it can also download any extra drivers that may be required.

---

### Post by avnd on 2012-04-06
@oldfred: This is the output from bootinfoscript, mate.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub.cfg

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda7 and looks at sector 545747600 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #7 
                       for /boot/grub/menu.lst.
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda8 and looks at sector 629635728 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #8 
                       for /boot/grub/menu.lst.
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  CrunchBang Linux statler
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  83 Linux
/dev/sda2    *        206,848    84,092,927    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda3         105,066,494 1,250,263,039 1,145,196,546   5 Extended
/dev/sda5         105,066,496   524,496,895   419,430,400   7 NTFS / exFAT / HPFS
/dev/sda6         524,498,944   532,887,551     8,388,608  82 Linux swap / Solaris
/dev/sda7         532,889,600   616,775,679    83,886,080  83 Linux
/dev/sda8         616,777,728   658,720,767    41,943,040  83 Linux
/dev/sda9         658,722,816   700,665,855    41,943,040  83 Linux
/dev/sda10        700,667,904 1,250,263,039   549,595,136  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5336399f-f0d2-4223-893c-27baab0fbaf6   ext4       GRUB
/dev/sda10       60120d45-24d8-4a2f-aa7b-379f1c30fd43   ext4       DATAEXT4
/dev/sda2        6920EB5358960D76                       ntfs       SEVEN
/dev/sda5        7DC648F70CFAEE35                       ntfs       DATANTFS
/dev/sda6        b018b05a-e2bf-4e31-ae07-f12660a69dbe   swap       SWAP
/dev/sda7        931bd6c3-7259-49ee-b8c8-d2c16ef4339d   ext4       ARCH
/dev/sda8        6b15090a-720e-474a-bfca-b18bb1b46fd1   ext4       ARCHSPARE
/dev/sda9        d23d39bb-9100-4316-8a5a-ab7d663edfba   ext4       CRUNCHBANG

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
(hd0,1)/boot/grub/grub.cfg
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Config file for GRUB2 - The GNU GRand Unified Bootloader

# DEVICE NAME CONVERSIONS
#
# Linux        GRUB
#-------------------------------
# /dev/fd0    (fd0)
# /dev/sda    (hd0)
# /dev/sdb2    (hd1,2)
# /dev/sda3    (hd0,3)

# Timeout for menu (in seconds)
set timeout=60

# Default option to boot (number starts from 0)
set default=0

# Menu color options
set menu_color_normal=white/black
set menu_color_highlight=black/white
set gfxpayload=1366x768

# Menu Entry Number ---> 0
menuentry "Windows"     {
    set root=(hd0,2)
    chainloader (hd0,2)+1
}

# Menu Entry Number ---> 1
menuentry "Arch"     {
    set root=(hd0,7)
    chainloader (hd0,7)+1
}

# Menu Entry Number ---> 2
menuentry "Arch Test"     {
    set root=(hd0,8)
    chainloader (hd0,8)+1
}

# Menu Entry Number ---> 3
menuentry "Crunchbang"    {
    set root=(hd0,9)
    chainloader (hd0,9)+1
}
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.011020660 = 0.011833344    boot/grub/core.img                             1
   0.011024475 = 0.011837440    boot/grub/grub.cfg                             1

================================ sda5/grub.cfg: ================================

--------------------------------------------------------------------------------
(hd0,1)/boot/grub/grub.cfg
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Config file for GRUB2 - The GNU GRand Unified Bootloader

# DEVICE NAME CONVERSIONS
#
# Linux        GRUB
#-------------------------------
# /dev/fd0    (fd0)
# /dev/sda    (hd0)
# /dev/sdb2    (hd1,2)
# /dev/sda3    (hd0,3)

# Timeout for menu (in seconds)
set timeout=60

# Default option to boot (number starts from 0)
set default=0

# Menu color options
set menu_color_normal=white/black
set menu_color_highlight=black/white
set gfxpayload=1366x768

# Menu Entry Number ---> 0
menuentry "Windows"     {
    set root=(hd0,2)
    chainloader (hd0,2)+1
}

# Menu Entry Number ---> 1
menuentry "Arch"     {
    set root=(hd0,7)
    chainloader (hd0,7)+1
}

# Menu Entry Number ---> 2
menuentry "Arch Test"     {
    set root=(hd0,8)
    chainloader (hd0,8)+1
}

# Menu Entry Number ---> 3
menuentry "Crunchbang"    {
    set root=(hd0,9)
    chainloader (hd0,9)+1
}
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub.cfg                                       1

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   0
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,6)
kernel /boot/vmlinuz-linux root=/dev/sda7 ro
initrd /boot/initramfs-linux.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,6)
kernel /boot/vmlinuz-linux root=/dev/sda7 ro
initrd /boot/initramfs-linux-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
/dev/sda6 swap swap defaults 0 0
/dev/sda7 / ext4 defaults 0 1
--------------------------------------------------------------------------------

======================= sda7/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Change to 1 if you do not want to use a menu
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
    MENU LABEL Arch Linux
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux.img

LABEL archfallback
    MENU LABEL Arch Linux Fallback
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 260.233066559 = 279.423127552  boot/grub/menu.lst                             1
 260.232887268 = 279.422935040  boot/grub/stage2                               2
 254.306041718 = 273.059033088  boot/initramfs-linux-fallback.img              2
 254.302814484 = 273.055567872  boot/initramfs-linux.img                       1
 260.232654572 = 279.422685184  boot/vmlinuz-linux                             1

================= sda7: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 260.230476379 = 279.420346368  boot/syslinux/syslinux.cfg                     1

=========================== sda8/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   0
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,7)
kernel /boot/vmlinuz-linux root=/dev/sda8 ro
initrd /boot/initramfs-linux.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,7)
kernel /boot/vmlinuz-linux root=/dev/sda8 ro
initrd /boot/initramfs-linux-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
/dev/sda6 swap swap defaults 0 0
/dev/sda8 / ext4 defaults 0 1
--------------------------------------------------------------------------------

======================= sda8/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Change to 1 if you do not want to use a menu
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
    MENU LABEL Arch Linux
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux.img

LABEL archfallback
    MENU LABEL Arch Linux Fallback
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 300.234043121 = 322.373849088  boot/grub/menu.lst                             1
 300.233863831 = 322.373656576  boot/grub/stage2                               2
 294.314826965 = 316.018139136  boot/initramfs-linux-fallback.img              2
 294.307701111 = 316.010487808  boot/initramfs-linux.img                       1
 300.233631134 = 322.373406720  boot/vmlinuz-linux                             1

================= sda8: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 300.231452942 = 322.371067904  boot/syslinux/syslinux.cfg                     1

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set d23d39bb-9100-4316-8a5a-ab7d663edfba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set d23d39bb-9100-4316-8a5a-ab7d663edfba
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set d23d39bb-9100-4316-8a5a-ab7d663edfba
insmod png
if background_image /usr/share/images/desktop-base/grub-splash-crunchbang.png ; then
  set color_normal=light-gray/black
  set color_highlight=black/white
else
  set menu_color_normal=light-gray/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-amd64' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set d23d39bb-9100-4316-8a5a-ab7d663edfba
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=d23d39bb-9100-4316-8a5a-ab7d663edfba ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set d23d39bb-9100-4316-8a5a-ab7d663edfba
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=d23d39bb-9100-4316-8a5a-ab7d663edfba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6920eb5358960d76
    chainloader +1
}
menuentry "Arch Linux (on /dev/sda7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set d91efe75-dffc-47fe-b93c-d251274df3f2
    linux /boot/vmlinuz-linux root=/dev/sda7 ro
    initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux Fallback (on /dev/sda7)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set d91efe75-dffc-47fe-b93c-d251274df3f2
    linux /boot/vmlinuz-linux root=/dev/sda7 ro
    initrd /boot/initramfs-linux-fallback.img
}
menuentry "Arch Linux (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 336b8d53-b689-48f3-ada6-5c347e99065a
    linux /boot/vmlinuz-linux root=/dev/sda8 ro
    initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux Fallback (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 336b8d53-b689-48f3-ada6-5c347e99065a
    linux /boot/vmlinuz-linux root=/dev/sda8 ro
    initrd /boot/initramfs-linux-fallback.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=d23d39bb-9100-4316-8a5a-ab7d663edfba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=25eaca72-a695-4c30-a3f9-57c954798853 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/usb0     auto    rw,user,noauto  0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 318.242992401 = 341.710811136  boot/grub/core.img                             1
 318.232627869 = 341.699682304  boot/grub/grub.cfg                             1
 322.729454041 = 346.528112640  boot/initrd.img-2.6.32-5-amd64                 2
 318.232425690 = 341.699465216  boot/vmlinuz-2.6.32-5-amd64                    1
 322.729454041 = 346.528112640  initrd.img                                     2
 318.232425690 = 341.699465216  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  9e db 94 f1 a4 cf cb 01  00 80 03 00 00 00 00 00  |................|
00000010  ff 75 03 00 00 00 00 00  20 00 00 00 00 00 00 00  |.u...... .......|
00000020  5a 01 61 00 6d 00 64 00  36 00 34 00 5f 00 6e 00  |Z.a.m.d.6.4._.n.|
00000030  65 00 74 00 77 00 6f 00  72 00 6b 00 69 00 6e 00  |e.t.w.o.r.k.i.n.|
00000040  67 00 2d 00 6d 00 70 00  73 00 73 00 76 00 63 00  |g.-.m.p.s.s.v.c.|
00000050  2d 00 73 00 76 00 63 00  5f 00 33 00 31 00 62 00  |-.s.v.c._.3.1.b.|
00000060  66 00 33 00 38 00 35 00  36 00 61 00 64 00 33 00  |f.3.8.5.6.a.d.3.|
00000070  36 00 34 00 65 00 33 00  35 00 5f 00 36 00 2e 00  |6.4.e.3.5._.6...|
00000080  31 00 2e 00 37 00 36 00  30 00 31 00 2e 00 31 00  |1...7.6.0.1...1.|
00000090  37 00 35 00 31 00 34 00  5f 00 6e 00 6f 00 6e 00  |7.5.1.4._.n.o.n.|
000000a0  65 00 5f 00 66 00 38 00  33 00 61 00 34 00 30 00  |e._.f.8.3.a.4.0.|
000000b0  65 00 37 00 64 00 65 00  37 00 63 00 34 00 37 00  |e.7.d.e.7.c.4.7.|
000000c0  64 00 61 00 2e 00 6d 00  61 00 6e 00 69 00 66 00  |d.a...m.a.n.i.f.|
000000d0  65 00 73 00 74 00 00 00  08 f8 00 00 00 00 01 00  |e.s.t...........|
000000e0  10 01 fc 00 00 00 00 00  cc 36 00 00 00 00 01 00  |.........6......|
000000f0  1f 21 92 c3 9c f8 cb 01  1f 21 92 c3 9c f8 cb 01  |.!.......!......|
00000100  22 e2 fb 32 0d 4b cc 01  1f 21 92 c3 9c f8 cb 01  |"..2.K...!......|
00000110  00 20 00 00 00 00 00 00  47 1d 00 00 00 00 00 00  |. ......G.......|
00000120  20 00 00 00 00 00 00 00  5d 00 61 00 6d 00 64 00  | .......].a.m.d.|
00000130  36 00 34 00 5f 00 70 00  6f 00 6c 00 69 00 63 00  |6.4._.p.o.l.i.c.|
00000140  79 00 2e 00 38 00 2e 00  30 00 2e 00 6d 00 69 00  |y...8...0...m.i.|
00000150  63 00 72 00 6f 00 73 00  6f 00 66 00 74 00 2e 00  |c.r.o.s.o.f.t...|
00000160  76 00 63 00 38 00 30 00  2e 00 61 00 74 00 6c 00  |v.c.8.0...a.t.l.|
00000170  5f 00 31 00 66 00 63 00  38 00 62 00 33 00 62 00  |_.1.f.c.8.b.3.b.|
00000180  39 00 61 00 31 00 65 00  31 00 38 00 65 00 33 00  |9.a.1.e.1.8.e.3.|
00000190  62 00 5f 00 38 00 2e 00  30 00 2e 00 35 00 30 00  |b._.8...0...5.0.|
000001a0  37 00 32 00 37 00 2e 00  34 00 30 00 35 00 33 00  |7.2.7...4.0.5.3.|
000001b0  5f 00 6e 00 6f 00 6e 00  65 00 5f 00 30 00 00 fe  |_.n.o.n.e._.0...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 00 00 19 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 00  00 19 00 08 80 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

P.S. Bootinfoscript says there is no bootloader on the Crunchbang partition. I was certain that I had installed GRUB 2 to "/dev/sda9" on both the occasions that I had installed that distro. And apparently, the boot files are present in the /boot folders. I guess they are created at the time of bootloader installations. By the way, I used Crunchbang's graphic installer. I don't understand what has happened. 

I'll try installing GRUB to the partition's boot sector pointing it to the boot files in the /boot folder of Crunchbang. I'll get back in a couple of hours to post if I was successful.

---

### Post by avnd on 2012-04-06
I tried installing GRUB 2 to the Crunchbang partition (/dev/sda9) with the following command from a Ubuntu Live CD.

```

ubuntu@ubuntu:~$ sudo mount /dev/sda9 -t ext4 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda9

```I adapted from the instructions found at the following thread and the GNU GRUB manual.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

But with the above commands, I get the following error.

```

/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition. This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists
```Any suggestions?

Thanks!

I found the following instructions on Arch Linux's GRUB 2 wiki page.

> 
To setup [COLOR=#222][FONT=monospace]grub2-bios[/FONT][/COLOR] to a partition boot sector, to a partitionless disk (also called superfloppy) or to a floppy disk, run (using for example [COLOR=#222][FONT=monospace]/dev/sda1[/FONT][/COLOR] as the [COLOR=#222][FONT=monospace]/boot[/FONT][/COLOR] partition): 
```
# chattr -i /boot/grub/i386-pc/core.img # grub-install --directory=/usr/lib/grub/i386-pc --target=i386-pc --boot-directory=/boot --recheck --force --debug /dev/sda1 # chattr +i /boot/grub/i386-pc/core.img
```
You need to use the [COLOR=#222][FONT=monospace]--force[/FONT][/COLOR] option to allow usage of blocklists and should not use [COLOR=#222][FONT=monospace]--grub-setup=/bin/true[/FONT][/COLOR] (which is similar to simply generating [COLOR=#222][FONT=monospace]core.img[/FONT][/COLOR]). 
[COLOR=#222][FONT=monospace]grub-install[/FONT][/COLOR] will give out warnings like which should give you the idea of what might go wrong with this approach: 

```

/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition. This is a BAD idea. /sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists.                          However, blocklists are UNRELIABLE and their use is discouraged.
```
Without [COLOR=#222][FONT=monospace]--force[/FONT][/COLOR] you may get the below error and [COLOR=#222][FONT=monospace]grub-setup[/FONT][/COLOR] will not setup its boot code in the partition boot sector: 

```

/sbin/grub-setup: error: will not proceed with blocklists 
```
With [COLOR=#222][FONT=monospace]--force[/FONT][/COLOR] you should get: 

```

Installation finished. No error reported.
```



Is it safe to add the --force command to my version as following?

```

 sudo grub-install --force --root-directory=/mnt /dev/sda9
```

---

### Post by oldfred on 2012-04-06
The --force should work, but that does use blocklists. That is hard coded addresses to find the rest of the grub code in the partition. If on an update to grub any files get moved it will break install and you will have to reinstall grub to the PBR.

But you can add an entry like this that will boot your partition with the newest kernel. Ubuntu & I see Crunchbang add a link in root to the newest kernel.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. 

```
menuentry "CrunchBang Linux on sda9" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}

```

---

### Post by avnd on 2012-04-06
Is
```
$ sudo mount /dev/sda9 -t ext4 /mnt
$ sudo grub-install --root-directory=/mnt /dev/sda9
```
the same as
```
$ sudo mount /dev/sda9 -t ext4 /mnt
$ sudo grub-setup -d /mnt/boot/grub /dev/sda9
```
??

Is there any difference between the above two?
I adapted the above from Herman's guide at 
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html") which says
> Run the grub-setup command, inserting the -d option and specifying the path to the /boot/grub directory of the operating system you're trying to fix,
```
sudo grub-setup -d /media/disk/boot/grub /dev/sda
```
The -d option tells GRUB to use files from the specified directory.
Please substitute the word 'disk' with the name of your own mount point as found in step 3)
The '/dev/sda' part tells grub-setup to install GRUB to MBR in the first hard disk, which is called '/dev/sda'.
You may use the same command to install GRUB in any other disks in your computer by replacing the /dev/sda part of the command with /dev/sdb or /dev/sdc and so on.

Also, kindly point out if I have not adapted it correctly.
I already have the operating system installed in /sda9 and it already has a boot directory but I don't mind if the install creates a new directory or uses the existing one.

@oldfred: Thanks for the suggestion, oldfred. I prefer it that all my operating systems boot similarly for sake of simplicity. I will use that if I can't figure out any way to chainload GRUB2 from GRUB2 elegantly.

Thanks.

P.S. Does it make any difference if I chroot into the Crunchbang installation and try
```
sudo grub-install --root-directory=/mnt /dev/sda9
``` and can I chroot into the installation with a Crunchbang Live USB?

---

### Post by oldfred on 2012-04-06
I have not seen the grub setup recently.

from man grub-setup

> You should not normally  run  grub-setup  directly.   Use  grub-install
       instead.


And with grub2 version 1.99 they now prefer boot not root. And I have not installed to a PBR since Ubuntu 9.10 as I prefer the partition boot.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by avnd on 2012-04-06
@oldfred: I'm extremely sorry for being so pig-headed and not going for the easier options available. And many thanks for all your time and patience.

I kind of have the feeling that I'm closer to what I want. But I need some help adapting things to my situation since I don't have much experience with Linux and I don't want to experiment too much with something as important as the bootloader.

I found the following guidelines at Arch Linux's GRUB 2 wiki page. 
[https://wiki.archlinux.org/index.php/GRUB2#Install_to_Partition_or_Partitionless_Disk]("https://wiki.archlinux.org/index.php/GRUB2#Install_to_Partition_or_Partitionless_Disk")
> Note: grub2-bios (any version - including upstream Bazaar repo) does not encourage installation to a partition boot sector or a partitionless disk like GRUB Legacy or syslinux does. Neither do the Arch devs.
To setup grub2-bios to a partition boot sector, to a partitionless disk (also called superfloppy) or to a floppy disk, run (using for example /dev/sda1 as the /boot partition):
```
# chattr -i /boot/grub/i386-pc/core.img
# grub-install --directory=/usr/lib/grub/i386-pc --target=i386-pc --boot-directory=/boot --recheck --force --debug /dev/sda1
# chattr +i /boot/grub/i386-pc/core.img
```
You need to use the --force option to allow usage of blocklists and should not use --grub-setup=/bin/true (which is similar to simply generating core.img).
grub-install will give out warnings like which should give you the idea of what might go wrong with this approach:
```
/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition. This is a BAD idea.
/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. 
                        However, blocklists are UNRELIABLE and their use is discouraged.
```
Without --force you may get the below error and grub-setup will not setup its boot code in the partition boot sector:
```
/sbin/grub-setup: error: will not proceed with blocklists
```
With --force you should get:
```
Installation finished. No error reported.
```

What followed is what I think is my solution.
> The reason why grub-setup does not by default allow this is because in case of partition or a partitionless disk is that grub2-bios relies on embedded blocklists in the partition bootsector to locate the /boot/grub/i386-pc/core.img file and the prefix dir /boot/grub. The sector locations of core.img may change whenever the filesystem in the partition is being altered (files copied, deleted etc.). For more info see [https://bugzilla.redhat.com/show_bug.cgi?id=728742]("https://bugzilla.redhat.com/show_bug.cgi?id=728742") and [https://bugzilla.redhat.com/show_bug.cgi?id=730915]("https://bugzilla.redhat.com/show_bug.cgi?id=730915").
The workaround for this is to set the immutable flag on /boot/grub/i386-pc/core.img (using chattr command as mentioned above) so that the sector locations of the core.img file in the disk is not altered. The immutable flag on /boot/grub/i386-pc/core.img needs to be set only if grub2-bios is installed to a partition boot sector or a partitionless disk, not in case of installtion to MBR or simple generation of core.img without embedding any bootsector (mentioned above).

If the above method is good enough, I need some help setting the immutable flag on the core.img file in my system. The file exists at /boot/grub/core.img.

Any help is greatly appreciated.

Thanks.

---

### Post by oldfred on 2012-04-06
I now nothing about it.

Google found this:
[http://www.aboutlinux.info/2005/11/make-your-files-immutable-which-even.html](http://www.aboutlinux.info/2005/11/make-your-files-immutable-which-even.html)

My concern then it that you will get some sort of error on a grub update and grub updates will fail. That could lead to system issues if system is partially updated.

Herman also has the configfile type of chainload, I have not used it:

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#configfile_boot_entry](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#configfile_boot_entry)

---

### Post by avnd on 2012-04-07
> Herman also has the configfile type of chainload, I have not used it:

[http://members.iinet.net/~herman546/...ile_boot_entry](http://members.iinet.net/~herman546/...ile_boot_entry)

With the above method, I don't know what happens when I get kernel updated, oldfred.

Everything is getting too complicated for my liking. I guess the simplest and most elegant method would be to purge GRUB2 off my Crunchbang install and then install GRUB-Legacy to the partition.

I guess I have to chroot into the Crunchbang install to do that. (Please correct me if I'm wrong. I don't know how else I could install a package in a Linux install when I can't boot into it). Since I have never chroot'ed before, I think it'll take me a day or two to read about it and do it. I'll get back with what happened after I do that.

Thanks for your replies, oldfred.

---

### Post by avnd on 2012-04-07
I'm running into more trouble.

I decided to uninstall GRUB 2 and install GRUB-Legacy. Following the guides at [https://wiki.archlinux.org/index.php/Change_Root]("https://wiki.archlinux.org/index.php/Change_Root") and [http://ubuntuforums.org/showthread.php?t=1298932]("http://ubuntuforums.org/showthread.php?t=1298932")
I booted into a live Arch linux USB (because my Crunchbang is 64-bit and I only 64-bit live USB/CD I had was Arch). Then I entered the following at the terminal.
(I connected to the wireless internet initially)
```

mkdir /mnt/crunch
mount /dev/sda9 /mnt/crunch
cd /mnt/crunch
mount -t proc proc proc/
mount -t sysfs sys sys/
mount -o bind /dev dev/
cp -L /etc/resolv.conf etc/resolv.conf
chroot . /bin/bash

```
(I have now chroot-ed)
(Now following the guidelines at the above-mentioned Ubuntu forums thread, I uninstalled GRUB 2 and installed GRUB Legacy as follows. I actually did this twice because, I ended up reinstalling GRUB2 on the first attempt. I purged it again. Essentially, I did the following).
I didnot use sudo as mentioned in the thread because I was already superuser.

```
apt-get update
apt-get upgrade
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get --purge remove startupmanager
apt-get --purge remove grub-pc grub-common
apt-get install grub-legacy (when I followed the command in the post, I ended up re-installing GRUB2)
grub
```

Now, I was at the GRUB shell and I tried the following command to install GRUB.

```

root (hd0,8)
setup(hd0,8)

```
After the setup command, I got an error message saying stage1 was not found. (I guess most instructions on the web to restore a broken grub assume an intact /boot folder).

I thought I would have to install from outside the GRUB shell using the grub-install command. So I quit the GRUB shell and did the following at the root prompt.

```

grub-install /dev/sda9
```
Since I chroot-ed, I did not think setting the root-directory was necessary for my situation. But I got an error saying
```

The file /boot/grub/stage1 not read correctly
```
I checked /boot/grub and the folder had stage1 among other files which grub-install had created.

Can someone tell me how I can install GRUB Legacy from a chroot-ed installation that doesnot have the /boot/grub folder and its files?

Many thanks.

---

### Post by oldfred on 2012-04-07
I thought grub legacy was just grub and grub2 is grub-pc, and you get grub-common with both from command line.

sudo apt-get install grub

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

I am not sure old grub legacy works with ext4 unless you use the newest grub from Ubuntu as they modified it to work with ext4. Others may not have. I just prefer grub2 now.

---

### Post by avnd on 2012-04-08
I finally removed GRUB2 and reinstalled GRUB-Legacy in Crunchbang as follows.

I installed Crunchbang in /dev/sda9 with GRUB2 in the partition. Apparently, there is some issue with installing GRUB2 in the partition and it is not installed. 

Now, I booted into the Live USB image of Arch Linux (amd64 - the same as my Crunchbang installation). 

I connected to the wireless internet (This has a few steps that are not relevant to this topic).

I chroot-ed into the Crunchbang installation as follows.

```
mkdir /mnt/crunch
mount /dev/sda9 /mnt/crunch
cd /mnt/crunch
mount -t proc proc proc/
mount -t sysfs sys sys/
mount -o bind /dev dev/
cp -L /etc/resolv.conf etc/resolv.conf
chroot . /bin/bash
```

I removed the GRUB2 that was installed with Crunchbang as follows.

```
apt-get update
apt-get upgrade
mv /boot/grub /boot/grub_backup
apt-get --purge remove startupmanager
apt-get --purge remove grub-pc grub-common
```

I had trouble in the following unmounting step after exiting chroot. I got an error message saying the device was busy. Even the -f option did no good. I had to reboot as such. I don't know if I did any damage there. I exited chroot as follows.

```
exit
umount {proc,sys,dev,boot...}

```

I re-booted again into the Arch Live-USB. I installed grub as follows.

```
mount /dev/sda9 /mnt
grub-install --root-directory=/mnt /dev/sda9

```

This did not create the menu folder. I created the menu-lst file as follows.

```
nano /mnt/boot/grub/menu.lst
```

I entered the following lines in the menu-lst file.

```
timeout     5
default     0

title     Crunchbang
root     (hd0,8)
kernel    /boot/vmlinuz-3.2.0-0.bpo.1-amd64 root=/dev/sda9 ro
initrd    /boot/initrd.img-3.2.0-0.bpo.1-amd64
```

I had previously created the entry in the GRUB partition's grub-cfg file for the Crunchbang chainloader.

When I rebooted and chose the 'Crunchbang' entry in the menu, I successfully booted into the Crunchbang installation.

Somehow, it seems so simple after the solution has been figured out. :)

@oldfred: Many thanks for all your time and help, mate.

P.S. I've marked this thread as solved, even though technically it is not since I havn't chainloaded GRUB2 from GRUB2.

---

### Post by oldfred on 2012-04-08
Glad you got it resolved.

You are not chainloading. The advantage of chainloading is a kernel update to Crunchbang will update the grub menu & a chain load will present the new menu. You are directly booting a specific kernel. On an update you will have to change to new kernel.

But in old grub legacy you can also boot a partition.

```
title 1 Most Current Ubuntu on sda9
root (hd0,8)
kernel /vmlinuz root=/dev/sda9 ro quiet splash
initrd /initrd.img

```That boots thru the link in / (root) to the most current kernel. I am not 100% sure but I think you do not even need grub in the install when you directly boot from another grub whether grub or grub2.

---

### Post by avnd on 2012-04-08
Oh Jeez!

This thread is definitely not solved if I'm not chain-loading. But I thought I was chain-loading. Ever since I created the grub-cfg in my GRUB partition, I have not changed it. It reads as follows.

```
(hd0,1)/boot/grub/grub.cfg
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Config file for GRUB2 - The GNU GRand Unified Bootloader

# DEVICE NAME CONVERSIONS
#
# Linux        GRUB
#-------------------------------
# /dev/fd0    (fd0)
# /dev/sda    (hd0)
# /dev/sdb2    (hd1,2)
# /dev/sda3    (hd0,3)

# Timeout for menu (in seconds)
set timeout=60

# Default option to boot (number starts from 0)
set default=0

# Menu color options
set menu_color_normal=white/black
set menu_color_highlight=black/white
set gfxpayload=1366x768

# Menu Entry Number ---> 0
menuentry "Windows"     {
    set root=(hd0,2)
    chainloader (hd0,2)+1
}

# Menu Entry Number ---> 1
menuentry "Arch"     {
    set root=(hd0,7)
    chainloader (hd0,7)+1
}

# Menu Entry Number ---> 2
menuentry "Arch Test"     {
    set root=(hd0,8)
    chainloader (hd0,8)+1
}

# Menu Entry Number ---> 3
menuentry "Crunchbang"    {
    set root=(hd0,9)
    chainloader (hd0,9)+1
}
```And I have installed Grub-Legacy on my Crunchbang partition with the following command from the Live Arch-Linux CD. 

```
grub-install --root-directory=/mnt /dev/sda9
```After that I created the entry for the kernel which has to be booted and the initrd image only in the menu-lst file. I never made any mention of the kernel or the initrd image in the grub-cfg file in the GRUB partition. 

The menu-lst file in the /boot folder of my Crunchbang partition reads as follow.

```
timeout     5
default     0

title     Crunchbang
root     (hd0,8)
kernel    /boot/vmlinuz-3.2.0-0.bpo.1-amd64 root=/dev/sda9 ro
initrd    /boot/initrd.img-3.2.0-0.bpo.1-amd64
```@ oldfred: With the above setup, are you sure I'm not chain-loading?

The following is the output of bootinfoscript on my computer

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub.cfg

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda7 and looks at sector 545747600 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #7 
                       for /boot/grub/menu.lst.
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda8 and looks at sector 629635728 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #8 
                       for /boot/grub/menu.lst.
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda9 and looks at sector 684154368 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #9 
                       for /boot/grub/menu.lst.
    Operating System:  CrunchBang Linux statler
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  83 Linux
/dev/sda2    *        206,848    84,092,927    83,886,080   7 NTFS / exFAT / HPFS
/dev/sda3         105,066,494 1,250,263,039 1,145,196,546   5 Extended
/dev/sda5         105,066,496   524,496,895   419,430,400   7 NTFS / exFAT / HPFS
/dev/sda6         524,498,944   532,887,551     8,388,608  82 Linux swap / Solaris
/dev/sda7         532,889,600   616,775,679    83,886,080  83 Linux
/dev/sda8         616,777,728   658,720,767    41,943,040  83 Linux
/dev/sda9         658,722,816   700,665,855    41,943,040  83 Linux
/dev/sda10        700,667,904 1,250,263,039   549,595,136  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5336399f-f0d2-4223-893c-27baab0fbaf6   ext4       GRUB
/dev/sda10       60120d45-24d8-4a2f-aa7b-379f1c30fd43   ext4       DATAEXT4
/dev/sda2        6920EB5358960D76                       ntfs       SEVEN
/dev/sda5        7DC648F70CFAEE35                       ntfs       DATANTFS
/dev/sda6        3f89db71-3e34-4ddf-ab98-8d5958dd85f1   swap       
/dev/sda7        931bd6c3-7259-49ee-b8c8-d2c16ef4339d   ext4       ARCH
/dev/sda8        6b15090a-720e-474a-bfca-b18bb1b46fd1   ext4       ARCHSPARE
/dev/sda9        13a729be-c6ae-4165-897c-c8e4ca2ac8dd   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
(hd0,1)/boot/grub/grub.cfg
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Config file for GRUB2 - The GNU GRand Unified Bootloader

# DEVICE NAME CONVERSIONS
#
# Linux        GRUB
#-------------------------------
# /dev/fd0    (fd0)
# /dev/sda    (hd0)
# /dev/sdb2    (hd1,2)
# /dev/sda3    (hd0,3)

# Timeout for menu (in seconds)
set timeout=60

# Default option to boot (number starts from 0)
set default=0

# Menu color options
set menu_color_normal=white/black
set menu_color_highlight=black/white
set gfxpayload=1366x768

# Menu Entry Number ---> 0
menuentry "Windows"     {
    set root=(hd0,2)
    chainloader (hd0,2)+1
}

# Menu Entry Number ---> 1
menuentry "Arch"     {
    set root=(hd0,7)
    chainloader (hd0,7)+1
}

# Menu Entry Number ---> 2
menuentry "Arch Test"     {
    set root=(hd0,8)
    chainloader (hd0,8)+1
}

# Menu Entry Number ---> 3
menuentry "Crunchbang"    {
    set root=(hd0,9)
    chainloader (hd0,9)+1
}
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.011020660 = 0.011833344    boot/grub/core.img                             1
   0.011024475 = 0.011837440    boot/grub/grub.cfg                             1

================================ sda5/grub.cfg: ================================

--------------------------------------------------------------------------------
(hd0,1)/boot/grub/grub.cfg
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Config file for GRUB2 - The GNU GRand Unified Bootloader

# DEVICE NAME CONVERSIONS
#
# Linux        GRUB
#-------------------------------
# /dev/fd0    (fd0)
# /dev/sda    (hd0)
# /dev/sdb2    (hd1,2)
# /dev/sda3    (hd0,3)

# Timeout for menu (in seconds)
set timeout=60

# Default option to boot (number starts from 0)
set default=0

# Menu color options
set menu_color_normal=white/black
set menu_color_highlight=black/white
set gfxpayload=1366x768

# Menu Entry Number ---> 0
menuentry "Windows"     {
    set root=(hd0,2)
    chainloader (hd0,2)+1
}

# Menu Entry Number ---> 1
menuentry "Arch"     {
    set root=(hd0,7)
    chainloader (hd0,7)+1
}

# Menu Entry Number ---> 2
menuentry "Arch Test"     {
    set root=(hd0,8)
    chainloader (hd0,8)+1
}

# Menu Entry Number ---> 3
menuentry "Crunchbang"    {
    set root=(hd0,9)
    chainloader (hd0,9)+1
}
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub.cfg                                       1

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   0
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,6)
kernel /boot/vmlinuz-linux root=/dev/sda7 ro
initrd /boot/initramfs-linux.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,6)
kernel /boot/vmlinuz-linux root=/dev/sda7 ro
initrd /boot/initramfs-linux-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
/dev/sda6 swap swap defaults 0 0
/dev/sda7 / ext4 defaults 0 1
--------------------------------------------------------------------------------

======================= sda7/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Change to 1 if you do not want to use a menu
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
    MENU LABEL Arch Linux
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux.img

LABEL archfallback
    MENU LABEL Arch Linux Fallback
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 260.233066559 = 279.423127552  boot/grub/menu.lst                             1
 260.232887268 = 279.422935040  boot/grub/stage2                               2
 254.306041718 = 273.059033088  boot/initramfs-linux-fallback.img              2
 254.302814484 = 273.055567872  boot/initramfs-linux.img                       1
 260.232654572 = 279.422685184  boot/vmlinuz-linux                             1

================= sda7: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 260.230476379 = 279.420346368  boot/syslinux/syslinux.cfg                     1

=========================== sda8/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution

# general configuration:
timeout   0
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,7)
kernel /boot/vmlinuz-linux root=/dev/sda8 ro
initrd /boot/initramfs-linux.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,7)
kernel /boot/vmlinuz-linux root=/dev/sda8 ro
initrd /boot/initramfs-linux-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
/dev/sda6 swap swap defaults 0 0
/dev/sda8 / ext4 defaults 0 1
--------------------------------------------------------------------------------

======================= sda8/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Change to 1 if you do not want to use a menu
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
    MENU LABEL Arch Linux
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux.img

LABEL archfallback
    MENU LABEL Arch Linux Fallback
    LINUX ../vmlinuz-linux
    APPEND root=/dev/sda3 ro
    INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 300.234043121 = 322.373849088  boot/grub/menu.lst                             1
 300.233863831 = 322.373656576  boot/grub/stage2                               2
 294.314826965 = 316.018139136  boot/initramfs-linux-fallback.img              2
 294.307701111 = 316.010487808  boot/initramfs-linux.img                       1
 300.233631134 = 322.373406720  boot/vmlinuz-linux                             1

================= sda8: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 300.231452942 = 322.371067904  boot/syslinux/syslinux.cfg                     1

=========================== sda9/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout    0
default    0

title    Crunchbang
root    (hd0,8)
kernel    /boot/vmlinuz-3.2.0-0.bpo.1-amd64 root=/dev/sda9 ro quiet
initrd    /boot/initrd.img-3.2.0-0.bpo.1-amd64    
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=13a729be-c6ae-4165-897c-c8e4ca2ac8dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3f89db71-3e34-4ddf-ab98-8d5958dd85f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/usb0     auto    rw,user,noauto  0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 316.228584290 = 339.547856896  boot/grub/menu.lst                             1
 326.230361938 = 350.287183872  boot/grub/stage2                               1
 314.984394073 = 338.211917824  boot/initrd.img-3.2.0-0.bpo.1-amd64            2
 314.779964447 = 337.992413184  boot/vmlinuz-3.2.0-0.bpo.1-amd64               1
 314.779964447 = 337.992413184  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  9e db 94 f1 a4 cf cb 01  00 80 03 00 00 00 00 00  |................|
00000010  ff 75 03 00 00 00 00 00  20 00 00 00 00 00 00 00  |.u...... .......|
00000020  5a 01 61 00 6d 00 64 00  36 00 34 00 5f 00 6e 00  |Z.a.m.d.6.4._.n.|
00000030  65 00 74 00 77 00 6f 00  72 00 6b 00 69 00 6e 00  |e.t.w.o.r.k.i.n.|
00000040  67 00 2d 00 6d 00 70 00  73 00 73 00 76 00 63 00  |g.-.m.p.s.s.v.c.|
00000050  2d 00 73 00 76 00 63 00  5f 00 33 00 31 00 62 00  |-.s.v.c._.3.1.b.|
00000060  66 00 33 00 38 00 35 00  36 00 61 00 64 00 33 00  |f.3.8.5.6.a.d.3.|
00000070  36 00 34 00 65 00 33 00  35 00 5f 00 36 00 2e 00  |6.4.e.3.5._.6...|
00000080  31 00 2e 00 37 00 36 00  30 00 31 00 2e 00 31 00  |1...7.6.0.1...1.|
00000090  37 00 35 00 31 00 34 00  5f 00 6e 00 6f 00 6e 00  |7.5.1.4._.n.o.n.|
000000a0  65 00 5f 00 66 00 38 00  33 00 61 00 34 00 30 00  |e._.f.8.3.a.4.0.|
000000b0  65 00 37 00 64 00 65 00  37 00 63 00 34 00 37 00  |e.7.d.e.7.c.4.7.|
000000c0  64 00 61 00 2e 00 6d 00  61 00 6e 00 69 00 66 00  |d.a...m.a.n.i.f.|
000000d0  65 00 73 00 74 00 00 00  08 f8 00 00 00 00 01 00  |e.s.t...........|
000000e0  10 01 fc 00 00 00 00 00  cc 36 00 00 00 00 01 00  |.........6......|
000000f0  1f 21 92 c3 9c f8 cb 01  1f 21 92 c3 9c f8 cb 01  |.!.......!......|
00000100  22 e2 fb 32 0d 4b cc 01  1f 21 92 c3 9c f8 cb 01  |"..2.K...!......|
00000110  00 20 00 00 00 00 00 00  47 1d 00 00 00 00 00 00  |. ......G.......|
00000120  20 00 00 00 00 00 00 00  5d 00 61 00 6d 00 64 00  | .......].a.m.d.|
00000130  36 00 34 00 5f 00 70 00  6f 00 6c 00 69 00 63 00  |6.4._.p.o.l.i.c.|
00000140  79 00 2e 00 38 00 2e 00  30 00 2e 00 6d 00 69 00  |y...8...0...m.i.|
00000150  63 00 72 00 6f 00 73 00  6f 00 66 00 74 00 2e 00  |c.r.o.s.o.f.t...|
00000160  76 00 63 00 38 00 30 00  2e 00 61 00 74 00 6c 00  |v.c.8.0...a.t.l.|
00000170  5f 00 31 00 66 00 63 00  38 00 62 00 33 00 62 00  |_.1.f.c.8.b.3.b.|
00000180  39 00 61 00 31 00 65 00  31 00 38 00 65 00 33 00  |9.a.1.e.1.8.e.3.|
00000190  62 00 5f 00 38 00 2e 00  30 00 2e 00 35 00 30 00  |b._.8...0...5.0.|
000001a0  37 00 32 00 37 00 2e 00  34 00 30 00 35 00 33 00  |7.2.7...4.0.5.3.|
000001b0  5f 00 6e 00 6f 00 6e 00  65 00 5f 00 30 00 00 fe  |_.n.o.n.e._.0...|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 00 00 19 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 00  00 19 00 08 80 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
```

@oldfred: Can you please also tell me if I can update the kernel in my Crunchbang installation without bothering to mess around with the menu-lst file? I have set the default choice as the first menu option in the menu-lst file ( of course, this only applies if I'm right in thinking that I'm chain-loading).

Thanks.

---

### Post by oldfred on 2012-04-08
It looks like you have a chain load entry. 

You had posted this, which was not chainloading and is grub legacy:

title     Crunchbang
root     (hd0,8)
kernel    /boot/vmlinuz-3.2.0-0.bpo.1-amd64 root=/dev/sda9 ro
initrd    /boot/initrd.img-3.2.0-0.bpo.1-amd64

Now you have this which is a chainload but also is grub2.

menuentry "Crunchbang"    {
    set root=(hd0,9)
    chainloader (hd0,9)+1
}

But if you have a major update to grub where it reinstalls files, it may break the blocklist location of the files and you will have to reinstall to the partition. But the chainload will give full grub menu.

Even if blocklist breaks booting this type of entry will still boot the most current kernel using the links. The previous one I posted was grub legacy. Sometimes you can manually type this type of entry at a grub> or grub rescue> prompt to boot. Otherwise you have to use a liveCD, Boot-Repair or Supergrub to boot if you have breakage.

menuentry "Crunchbang on sda9" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}

---

### Post by avnd on 2012-04-09
Thanks for your reply, oldfred.

You said before that this kind of entry works only with distributions based on Ubuntu. I have none of those.

Does 'grub-install' command in GRUB-Legacy also use blocklists? I got no warning when I installed GRUB-Legacy to the partition (unlike GRUB2 where I got a 'This is a BAD idea...' warning).

---

### Post by oldfred on 2012-04-09
I do not know. 

But grub legacy was smaller code and we used it for chainloading for quite a while. 

Distributions are converting to grub2 as grub legacy was not maintained for years and each distribution made tweaks to grub 0.97 which meant each grub was different. Ubuntu added support for ext4 in grub legacy with 9.04 for example.

If it works for you and you understand it then grub legacy is ok. It just is that new partition formats (ext4 & others), new partition layouts (gpt), new boot methods (UEFI) and many other system changes will not be in grub legacy unless a distribution decides to do that update instead of changing to grub2.

---

