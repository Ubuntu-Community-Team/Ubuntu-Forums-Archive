---
title: "Remove one of three Ubuntu installations"
date: 2017-09-02
forum: New to Ubuntu
---

### Post by Zetetes on 2017-09-02
On my 1 TB HDD, I have three Ubuntu installations: Kylin, Studio, and KX.  I want to remove the KXStudio installation and keep the other two without causing instability, data loss, or boot-up issues.  How is this best done?

---

### Post by Bashing-om on 2017-09-02
Zetetes; Hello -

Which is now the primary system that you boot into ?

No big deal to copy off what ever data you want from the KXStudio installation;
In a live environment, fire up GParted and delete the KXStudio partition(s) .

Then boot back into the primary and run:
```

sudo update-grub

```
to make grub aware of the changes . ( nothing in the primary's /etc/fstab file that reflects back to the KXStudio installation !)

If KXStudio is presently primary, then will have to do some prior prudent planning ,

[INDENT][INDENT]all in what you want in the end
[/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-07
> **Bashing-om said:**
> Zetetes; Hello -

Which is now the primary system that you boot into ?

No big deal to copy off what ever data you want from the KXStudio installation;
In a live environment, fire up GParted and delete the KXStudio partition(s) .

Then boot back into the primary and run:
```

sudo update-grub

```
to make grub aware of the changes . ( nothing in the primary's /etc/fstab file that reflects back to the KXStudio installation !)

If KXStudio is presently primary, then will have to do some prior prudent planning ,[INDENT][INDENT]all in what you want in the end
[/INDENT]
[/INDENT]


The KXStudio was installed last on sda7. In GParted, I deleted it.  I now have that logical partition sitting there. How can I 'attach' it to sda6?  This is my most-used Ubuntu Studio area.  [sda1 is Chinese Kylin]  Thanks for the help!

---

### Post by Bashing-om on 2017-09-07
Zetetes; Hey ....

> 
The KXStudio was installed last of the three. Let me go take a look in GParted and see what I can see...


then KXStudio is presently the "primary" /will save some head ache to boot up an alternate linux and make it primary boot ( sudo update-grub) at this time prior to removing KXStudio .

[INDENT][INDENT]prior prudent planning[/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-08
> **Bashing-om said:**
> Zetetes; Hey ....



then KXStudio is presently the "primary" /will save some head ache to boot up an alternate linux and make it primary boot ( sudo update-grub) at this time prior to removing KXStudio .[INDENT][INDENT]prior prudent planning[/INDENT]
[/INDENT]


I screwed up. I assumed that since KXStudio was installed last, then the primary would be the one installed firstly, the sda1. Before seeing your answer, I deleted the sda7 with KXStudio. From my place in sda6/Ubuntu Studio, I ran sudo update-grub. Imagine my surprise when I started up to find the grub rescue prompt.  Yes, an imprudent lack of planning.  One unsafe assumption.  

Now, at the grub rescue prompt, things aren't going well, either. The command 'ls' is working, but the command 'cat' is 'unknown'. I tried > linux /boot/vmlinuz-4.4.0-91-generic root=/dev/sda1 but grub rescue replied that 'linux' is an unknown command.  I do not know and can't find out which version of grub I am facing which lacks the 'cat' command. Searches on the various forums seem to turn up a lot of unanswered questions like mine.

I can't abandon the installations.  All of my data is in there. Perhaps I could install some 'intelligent' distro in the unallocated space where sda7 was, and then, hopefully, recover my sda1 Kylin, and sda6 Studio from there?  I'd like to work it out from the grub rescue prompt, though, but it seems I am facing a 'crippled' or limited version of grub.

Anyway, here I am in the exact place I was hoping to avoid.

---

### Post by Bashing-om on 2017-09-08
Zetetes; Hey !

Not a catastrophic issue in the least ! .. One can ALWAYS boot from grub if the target config files are consistent .

You in for the learning experience ? We need to find out where these config files that grub needs are installed to .
As I am not at your terminal. will be a slow process to find these files ; and tell grub what to do .
In a conventional Install, all it takes is 3 commands to boot a operating system !

At the grub > prompt . tell us what returns ;
```

ls

```
From the ls output we descend into the file system and locate the files grub wants.
Just be prepared - this process of discovery can be a long one , A lot depends on 
a) the file system on the partitions
b) the partitioning scheme imposed
c) file system layers
d) encryption -- here then ALL bets are off as I do not know encryption !

Else . well one can also boot up a liveDVD(USB), discover what is and install grub where it needs to be.

[INDENT][INDENT]ain't nothing but a thing ( or 2 )[/INDENT][/INDENT]

---

### Post by oldfred on 2017-09-08
perhaps jumping ahead.
Just to add to Bashing-om's post and use of ls to find boot files.

If it is a working install in another partition, you just need to know which partition (from ls commands).
I have used this to boot my other install in sda5. 

configfile (hd0,5)/boot/grub/grub.cfg

If you have an Ubuntu live installer, you also can use Boot-Repair to reinstall grub to MBR of a full reinstall of grub using advanced options where you choose which install to make the one in the MBR (if BIOS).

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Zetetes on 2017-09-08
> **Bashing-om said:**
> Zetetes; Hey !

Not a catastrophic issue in the least ! .. One can ALWAYS boot from grub if the target config files are consistent .

You in for the learning experience ? We need to find out where these config files that grub needs are installed to .
As I am not at your terminal. will be a slow process to find these files ; and tell grub what to do .
In a conventional Install, all it takes is 3 commands to boot a operating system !

At the grub > prompt . tell us what returns ;
```

ls

```
From the ls output we descend into the file system and locate the files grub wants.
Just be prepared - this process of discovery can be a long one , A lot depends on 
a) the file system on the partitions
b) the partitioning scheme imposed
c) file system layers
d) encryption -- here then ALL bets are off as I do not know encryption !

Else . well one can also boot up a liveDVD(USB), discover what is and install grub where it needs to be.
[INDENT][INDENT]ain't nothing but a thing ( or 2 )
[/INDENT]
[/INDENT]


OK.  Thanks!  Always up for learning!

> ls produces: (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1)

I think hd0,msdos5 is where the now-deleted KXStudio was located (just guessing). I never elected to encrypt anything, so I think I'm 'safe' on that score.

---

### Post by Zetetes on 2017-09-08
> **oldfred said:**
> perhaps jumping ahead.
Just to add to Bashing-om's post and use of ls to find boot files.

If it is a working install in another partition, you just need to know which partition (from ls commands).
I have used this to boot my other install in sda5. 

configfile (hd0,5)/boot/grub/grub.cfg

If you have an Ubuntu live installer, you also can use Boot-Repair to reinstall grub to MBR of a full reinstall of grub using advanced options where you choose which install to make the one in the MBR (if BIOS).

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Thank you, OldFred. I had working installs of Ubuntu Kylin in sda1, and the newest Ubuntu Studio in sda6.  I just made a disc from ubcd537.iso, but haven't tried it, yet. [OK. I can't boot to the disc I made from ubcd537.iso in spite of having the cd/dvd set first in the BIOS boot order.  Also, I tried > configfile (hd0,msdos6)/boot/grub/grub.cfg and received the reply: "Unknown command 'configfile'."  I keep getting an inordinate number of returns of 'Unknown command'.  For example, 'cat' returned unknown command.]

---

### Post by Bashing-om on 2017-09-08
Zetetes; Ho Kay;

So, MBR partitioning, and all we have to do is find grub's config files for the system we want to boot .
so next layer(s) down:
```

ls -al (hd0,msdos1)/
ls -al (hd0,msdos5)/
ls -al (hd0,msdos6)/

```

Here we be looking for 'vmlinuz' , /boot/grub . 
( yeah, we could cheat a tad and 'search" to find - but what fun is that ?)

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-08
Hey, Bashing-om:  my system balks at 'ls -al'.  It returns: 'invalid file name -al'. It also balks at 'search'.  Same reason: 'unknown command'.

No fun, so far...

Using 'ls' with no '-al' [>ls (hd0,msdos1)/] returns a long list, as follows: ./ ../ lost+found/ etc/ media/ bin/ boot/ dev/ home/ lib/ lib64/ mnt/ opt/ proc/ root/ run/ sbin/ snap/ srv/ sys/ tmp/ usr/ var/ initrd.img vmlinuz cdrom/ lib32/ initrd.img.old vmlinuz.old

entering >ls (hd0,msdos5)/ returns: 'error: unknown file system'.

entering >ls (hd0,msdos6)/ returns: ./ ../ lost+found/ swapfile etc/ media/ bin/ boot/ dev/ home/ lib/ lib64? mnt/ opt/ proc/ root/ run/ sbin/ snap/ srv/ sys/ tmp/ usr/ var/ vmlinuz initrd.img cdrom/ initrd.img.old vmlinuz.old lib32/

This last one includes 'swapfile' and the order is different, otherwise, the first and third are the same.

I don't know how to move/look around from the grub rescue> prompt.  It returns 'Unknown command' to everything I try ...

---

### Post by Bashing-om on 2017-09-08
Zetetesl Ouch !

I know my memory is not that hazy. but, give me a bit and when I reboot I will verify .
I am referring to the use of grub2 .

[INDENT][INDENT]when in doubt
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-09-08
Zetetes; ...

rebooting .. back soonest .

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-08
I was noticing that various tutorials on the Net were suggesting commands that my system was balking at.  I don't know the version of grub that I am facing, or even how to determine it. I started with a blank HDD and installed the newest Chinese Ubuntu Kylin from late July on sda1. I moved on to install the newest Ubuntu Studio on sda6.  Finally, I added the newest KXStudio on sda7, then decided I didn't need it. I deleted sda7. 

Which of them provided the grub that I am using here? Because of the constant returns of 'Unknown command' I suspect that grub came from the Chinese Kylin distro.

---

### Post by Zetetes on 2017-09-08
By the way, I revised the previous post to include the results of 'ls' for the three partitions

---

### Post by oldfred on 2017-09-08
Grub is a boot loader not an operating system, so it has very few commands that work.
But you seem to have found full / folder structures in both sda1(hd0,1) and sda6 (hd0,6). 

If neither of these work.
 configfile (hd0,1)/boot/grub/grub.cfg 

 configfile (hd0,1)/boot/grub/grub.cfg 

then you can try these with both hd0,1 or hd0,6. (all 1 or all 6)

 set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
linux (hd0,6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,6)/initrd.img
boot 


But I still prefer you run Boot-Repair from an Ubuntu live installer, using ppa to add Boot-Repair to live installer.

---

### Post by Zetetes on 2017-09-08
My grub rescue> prompt rejects 'configfile' and 'linux' as 'unknown commands'.  That's why I am drifting up the creek without a paddle at the moment.  

I could load the Ubuntu Studio live install disc and select 'Try Ubuntu', but then I wouldn't know what to do from that platform.  When you say, 'using ppa to add Boot-Repair to live installer', my eyes glaze over because the live installer is running from memory. How do I add things to it?

---

### Post by Bashing-om on 2017-09-08
Zetetes; Well.

verified my memory is not at fault :)

search -f /vmlinuz
search -f /sbin/init

results in the locations of these files on my system !

We working from a grub > prompt or from a  "grub rescue>" prompt ??
But, lets work with what we have to work with .

We now know that there are linux installs on partitions 1 and 6 and most likely that partition 5 is swap .

So, now which do you want to boot ? 1 or 6 /

Get the knowledge of what is installed to the respective partitions by looking in the respective /home directories for known files.
from grub one can do a number like :
```

ls -l (hd0,msdos1)/home/<your_user_name>/

```

I can accept that the new install is on the partition 6 ( hd0,msdos6) .

Ya want to boot into 6 ? then from the grub > prompt :
```

linux (hd0,msdos6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,msdos6)/initrd.img
boot

```

Now if you are in fact at a grub rescue> we will have to provide grub with some additional facts in order to boot.

[INDENT][INDENT]hey we can do that
[/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-08
prompt is 'grub rescue>'

It rejects 'configfile', and 'linux', and 'search' as 'unknown commands'. Also rejects '-l' after 'ls'

---

### Post by Bashing-om on 2017-09-09
Zetetes; Ho Kay !

grub rescue> is a hoss of another color - explains lots !

run:
```

set prefix=(hd0,msdos6)/boot/grub
set root=(hd0,msdos6)
insmod linux
linux (hd0,msdos6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,msdos6)/initrd.img
boot

```

once booted into the install, we can set grub to boot from the boot menu - but if you are going to install another system . we wait and see then the results after that install completes . The last linux install becomes that primary booting system .

all depends
[INDENT][INDENT]on what you want
[/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-09
```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type 'swsuspend'

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 17.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 17.04 
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   538,875,903   538,873,856  83 Linux
/dev/sda2         538,877,950 1,953,523,711 1,414,645,762   5 Extended
/dev/sda5       1,936,887,808 1,953,523,711    16,635,904  82 Linux swap / Solaris
/dev/sda6       1,060,780,032 1,936,887,807   876,107,776  83 Linux
/dev/sda7         538,877,952 1,060,777,983   521,900,032  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        94dd2b04-b030-486b-b162-d67bbfbce7dd   ext4       
/dev/sda5        602df15a-2ca3-4068-b9c3-4f00a5f078e5   swsuspend  
/dev/sda6        171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa   ext4       
/dev/sda7        dc70516c-a6b1-44e4-b9c7-14952bacd560   ext4       
/dev/sr0         2017-04-12-04-07-51-00                 iso9660    Ubuntu-Studio 17.04 amd64

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Sep  9 04:28 ata-CLOVER_CN-M101MBB_F200M8B10TG23838_4 -> ../../sda
lrwxrwxrwx 1 root root 10 Sep  9 04:28 ata-CLOVER_CN-M101MBB_F200M8B10TG23838_4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep  9 04:28 ata-CLOVER_CN-M101MBB_F200M8B10TG23838_4-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Sep  9 04:28 ata-CLOVER_CN-M101MBB_F200M8B10TG23838_4-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Sep  9 04:28 ata-CLOVER_CN-M101MBB_F200M8B10TG23838_4-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Sep  9 04:28 ata-CLOVER_CN-M101MBB_F200M8B10TG23838_4-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Sep  9 04:11 ata-HL-DT-STDVDRAM_GT30N_M2WAA1D2014 -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
else
  search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=zh_CN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
else
  search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
fi
insmod tga
if background_image /boot/grub/ubuntu_kylin_grub_bg.tga; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu Kylin GNU/Linux' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
    else
      search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
    fi
        linux    /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-91-generic
}
submenu 'Ubuntu Kylin GNU/Linux &#39640;&#32423;&#36873;&#39033;' $menuentry_id_option 'gnulinux-advanced-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
    menuentry 'Ubuntu Kylin GNU/Linux&#65292;Linux 4.4.0-91-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-91-generic-advanced-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        echo    '&#36733;&#20837; Linux 4.4.0-91-generic ...'
            linux    /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff
        echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
        initrd    /boot/initrd.img-4.4.0-91-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-91-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-91-generic-init-upstart-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        echo    '&#36733;&#20837; Linux 4.4.0-91-generic ...'
            linux    /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff init=/sbin/upstart
        echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
        initrd    /boot/initrd.img-4.4.0-91-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-91-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-91-generic-recovery-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        echo    '&#36733;&#20837; Linux 4.4.0-91-generic ...'
            linux    /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro recovery nomodeset locale=zh_CN
        echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
        initrd    /boot/initrd.img-4.4.0-91-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux&#65292;Linux 4.4.0-89-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-89-generic-advanced-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        echo    '&#36733;&#20837; Linux 4.4.0-89-generic ...'
            linux    /boot/vmlinuz-4.4.0-89-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff
        echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
        initrd    /boot/initrd.img-4.4.0-89-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-89-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-89-generic-init-upstart-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        echo    '&#36733;&#20837; Linux 4.4.0-89-generic ...'
            linux    /boot/vmlinuz-4.4.0-89-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff init=/sbin/upstart
        echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
        initrd    /boot/initrd.img-4.4.0-89-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-89-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-89-generic-recovery-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        echo    '&#36733;&#20837; Linux 4.4.0-89-generic ...'
            linux    /boot/vmlinuz-4.4.0-89-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro recovery nomodeset locale=zh_CN
        echo    '&#36733;&#20837;&#21021;&#22987;&#21270;&#20869;&#23384;&#30424;...'
        initrd    /boot/initrd.img-4.4.0-89-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
    else
      search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
    else
      search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=602df15a-2ca3-4068-b9c3-4f00a5f078e5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.779720306 = 7.279669248    boot/grub/grub.cfg                             1
  74.427036285 = 79.915421696   boot/grub/i386-pc/core.img                     1
  48.507583618 = 52.084621312   boot/vmlinuz-4.4.0-89-generic                  1
  49.639911652 = 53.300449280   boot/vmlinuz-4.4.0-91-generic                  1
  49.639911652 = 53.300449280   vmlinuz                                        1
  48.507583618 = 52.084621312   vmlinuz.old                                    1
 208.128364563 = 223.476129792  boot/initrd.img-4.4.0-89-generic               2
  50.294990540 = 54.003834880   boot/initrd.img-4.4.0-91-generic               2
  50.294990540 = 54.003834880   initrd.img                                     2
 208.128364563 = 223.476129792  initrd.img.old                                 2

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
else
  search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/09_lowlatency ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu (lowlatency)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    else
      search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    fi
    linux    /boot/vmlinuz-4.10.0-33-lowlatency root=UUID=171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.10.0-33-lowlatency
}

### END /etc/grub.d/09_lowlatency ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    else
      search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    fi
        linux    /boot/vmlinuz-4.10.0-33-lowlatency root=UUID=171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.10.0-33-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa' {
    menuentry 'Ubuntu, with Linux 4.10.0-33-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-33-lowlatency-advanced-171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        else
          search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        fi
        echo    'Loading Linux 4.10.0-33-lowlatency ...'
            linux    /boot/vmlinuz-4.10.0-33-lowlatency root=UUID=171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-33-lowlatency
    }
    menuentry 'Ubuntu, with Linux 4.10.0-33-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-33-lowlatency-recovery-171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        else
          search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        fi
        echo    'Loading Linux 4.10.0-33-lowlatency ...'
            linux    /boot/vmlinuz-4.10.0-33-lowlatency root=UUID=171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-33-lowlatency
    }
    menuentry 'Ubuntu, with Linux 4.10.0-32-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-32-lowlatency-advanced-171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        else
          search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        fi
        echo    'Loading Linux 4.10.0-32-lowlatency ...'
            linux    /boot/vmlinuz-4.10.0-32-lowlatency root=UUID=171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-32-lowlatency
    }
    menuentry 'Ubuntu, with Linux 4.10.0-32-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-32-lowlatency-recovery-171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        else
          search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
        fi
        echo    'Loading Linux 4.10.0-32-lowlatency ...'
            linux    /boot/vmlinuz-4.10.0-32-lowlatency root=UUID=171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-32-lowlatency
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    else
      search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    else
      search --no-floppy --fs-uuid --set=root 171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 16.04.3 LTS (16.04) (on /dev/sda1)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
    else
      search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
    fi
    linux /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff
    initrd /boot/initrd.img-4.4.0-91-generic
}
submenu 'Advanced options for Ubuntu 16.04.3 LTS (16.04) (on /dev/sda1)' $menuentry_id_option 'osprober-gnulinux-advanced-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
    menuentry 'Ubuntu Kylin GNU/Linux (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-91-generic--94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        linux /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff
        initrd /boot/initrd.img-4.4.0-91-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux&#65292;Linux 4.4.0-91-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-91-generic--94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        linux /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff
        initrd /boot/initrd.img-4.4.0-91-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-91-generic (upstart) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-91-generic--94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        linux /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff init=/sbin/upstart
        initrd /boot/initrd.img-4.4.0-91-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-91-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-91-generic-root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro recovery nomodeset locale=zh_CN-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        linux /boot/vmlinuz-4.4.0-91-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro recovery nomodeset locale=zh_CN
        initrd /boot/initrd.img-4.4.0-91-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux&#65292;Linux 4.4.0-89-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-89-generic--94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        linux /boot/vmlinuz-4.4.0-89-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff
        initrd /boot/initrd.img-4.4.0-89-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-89-generic (upstart) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-89-generic--94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        linux /boot/vmlinuz-4.4.0-89-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro locale=zh_CN quiet splash $vt_handoff init=/sbin/upstart
        initrd /boot/initrd.img-4.4.0-89-generic
    }
    menuentry 'Ubuntu Kylin GNU/Linux, with Linux 4.4.0-89-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-89-generic-root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro recovery nomodeset locale=zh_CN-94dd2b04-b030-486b-b162-d67bbfbce7dd' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  94dd2b04-b030-486b-b162-d67bbfbce7dd
        else
          search --no-floppy --fs-uuid --set=root 94dd2b04-b030-486b-b162-d67bbfbce7dd
        fi
        linux /boot/vmlinuz-4.4.0-89-generic root=UUID=94dd2b04-b030-486b-b162-d67bbfbce7dd ro recovery nomodeset locale=zh_CN
        initrd /boot/initrd.img-4.4.0-89-generic
    }
}

set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 561.422477722 = 602.822795264  boot/grub/grub.cfg                             3
 561.994567871 = 603.437072384  boot/grub/i386-pc/core.img                     1
 511.763923645 = 549.502328832  boot/vmlinuz-4.10.0-32-lowlatency              1
 525.095165253 = 563.816640512  boot/vmlinuz-4.10.0-33-lowlatency              1
 525.095165253 = 563.816640512  vmlinuz                                        1
 511.763923645 = 549.502328832  vmlinuz.old                                    1
 561.420886993 = 602.821087232  boot/initrd.img-4.10.0-32-lowlatency           3
 677.958343506 = 727.952228352  boot/initrd.img-4.10.0-33-lowlatency           3
 677.958343506 = 727.952228352  initrd.img                                     3
 561.420886993 = 602.821087232  initrd.img.old                                 3

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=dc70516c-a6b1-44e4-b9c7-14952bacd560 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/12859/mountinfo) leaked on lvs invocation. Parent PID 20347: bash
File descriptor 63 (pipe:[72993]) leaked on lvs invocation. Parent PID 20347: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-09-09__04h28 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
boot-info is executed in live-session (Ubuntu 17.04, zesty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntustudio.seed boot=casper initrd=/casper/initrd.lz quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
mount: unknown filesystem type 'swsuspend'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'swsuspend'
mount -r /dev/sda5 : Error code 32
Partition 2 does not start on physical sector boundary.

=================== os-prober:
/dev/sda1:Ubuntu 16.04.3 LTS (16.04):Ubuntu:linux
/dev/sda6:Ubuntu 17.04 (17.04):Ubuntu1:linux
/dev/sda7:Ubuntu 17.04 (17.04):Ubuntu2:linux

=================== blkid:
/dev/sda1: UUID="94dd2b04-b030-486b-b162-d67bbfbce7dd" TYPE="ext4" PARTUUID="1728df09-01"
/dev/sda6: UUID="171a57d4-d4da-4cd1-8ff0-2d45a7ccc9aa" TYPE="ext4" PARTUUID="1728df09-06"
/dev/sda7: UUID="dc70516c-a6b1-44e4-b9c7-14952bacd560" TYPE="ext4" PARTUUID="1728df09-07"
/dev/sr0: UUID="2017-04-12-04-07-51-00" LABEL="Ubuntu-Studio 17.04 amd64" TYPE="iso9660" PTUUID="1283d997" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="602df15a-2ca3-4068-b9c3-4f00a5f078e5" TYPE="swsuspend" PARTUUID="1728df09-05"


1 disks with OS, 3 OS : 3 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mount: unknown filesystem type 'swsuspend'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'swsuspend'
mount -r /dev/sda5 : Error code 32
Partition 2 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.

=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Aug  2 04:14 grub.d
total 80
-rwxr-xr-x 1 root root  9791 Apr 15  2016 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 May 20 20:27 10_linux
-rwxr-xr-x 1 root root 11082 Apr 15  2016 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 15  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Apr 15  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 15  2016 40_custom
-rwxr-xr-x 1 root root   216 Apr 15  2016 41_custom
-rw-r--r-- 1 root root   483 Apr 15  2016 README




=================== sda1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=Ubuntu Kylin
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="locale=zh_CN"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Aug 16 04:07 grub.d
total 92
-rwxr-xr-x 1 root root  9783 Mar 30 21:45 00_header
-rwxr-xr-x 1 root root  6258 Nov  1  2016 05_debian_theme
-rwxr-xr-x 1 root root  9921 Sep  2  2016 09_lowlatency
-rwxr-xr-x 1 root root 12676 Mar 30 21:45 10_linux
-rwxr-xr-x 1 root root 11281 Mar 30 21:45 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Mar 30 21:45 30_os-prober
-rwxr-xr-x 1 root root  1418 Mar 30 21:45 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mar 30 21:45 40_custom
-rwxr-xr-x 1 root root   216 Mar 30 21:45 41_custom
-rw-r--r-- 1 root root   483 Mar 30 21:45 README




=================== sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Sep  9 02:29 grub.d
total 92
-rwxr-xr-x 1 root root  9783 Mar 30 21:45 00_header
-rwxr-xr-x 1 root root  6258 Nov  1  2016 05_debian_theme
-rwxr-xr-x 1 root root  9921 Sep  2  2016 09_lowlatency
-rwxr-xr-x 1 root root 12676 Mar 30 21:45 10_linux
-rwxr-xr-x 1 root root 11281 Mar 30 21:45 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Mar 30 21:45 30_os-prober
-rwxr-xr-x 1 root root  1418 Mar 30 21:45 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mar 30 21:45 40_custom
-rwxr-xr-x 1 root root   216 Mar 30 21:45 41_custom
-rw-r--r-- 1 root root   483 Mar 30 21:45 README




=================== sda7/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== No kernel in /mnt/boot-sav/sda7/boot:
abi-4.10.0-19-lowlatency
config-4.10.0-19-lowlatency
grub
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-4.10.0-19-lowlatency



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sda7    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    emptyusr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA CLOVER CN-M101M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system  Flags
1      1049kB  276GB   276GB   primary   ext4         boot
2      276GB   1000GB  724GB   extended
7      276GB   543GB   267GB   logical   ext4
6      543GB   992GB   449GB   logical   ext4
5      992GB   1000GB  8518MB  logical   swsusp


Model: HL-DT-ST DVDRAM GT30N (scsi)
Disk /dev/sr0: 3131MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags:

Number  Start   End     Size    File system  Name   Flags
1      2048B   6143B   4096B                Apple
2      36.4MB  38.8MB  2359kB               EFI

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA CLOVER CN-M101M:;
1:1049kB:276GB:276GB:ext4::boot;
2:276GB:1000GB:724GB:::;
7:276GB:543GB:267GB:ext4::;
6:543GB:992GB:449GB:ext4::;
5:992GB:1000GB:8518MB:swsusp::;

BYT;
/dev/sr0:3131MB:scsi:2048:2048:mac:HL-DT-ST DVDRAM GT30N:;
1:2048B:6143B:4096B::Apple:;
2:36.4MB:38.8MB:2359kB::EFI:;

=================== lsblk:
KNAME TYPE FSTYPE      SIZE LABEL
loop0 loop squashfs    2.9G
sda   disk           931.5G
sda1  part ext4        257G
sda2  part               1K
sda5  part swsuspend     8G
sda6  part ext4      417.8G
sda7  part ext4      248.9G
sr0   rom  iso9660     2.9G Ubuntu-Studio 17.04 amd64

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0
sda5     1  0  0
sda6     1  0  0         /mnt/boot-sav/sda6
sda7     1  0  0         /mnt/boot-sav/sda7
sr0      1  0  1 running /cdrom


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4034620k,nr_inodes=1008655,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=810288k,mode=755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=946ce6a8e4c41b41)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=35,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=18507)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=810284k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw,relatime,data=ordered)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw,relatime,data=ordered)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  adsp autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 dsp dvd dvdrw ecryptfs fb0 fd full fuse fw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg lightnvm log mapper mcelog mei0 mem memory_bandwidth mixer mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sda7 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout tpm0 uhid uinput urandom userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control
Partition 2 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     792M  9.6M  782M   2% /run
/dev/sr0       iso9660   3.0G  3.0G     0 100% /cdrom
/dev/loop0     squashfs  2.9G  2.9G     0 100% /rofs
aufs           aufs      3.9G  222M  3.7G   6% /
tmpfs          tmpfs     3.9G     0  3.9G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  224K  3.9G   1% /tmp
tmpfs          tmpfs     792M   20K  792M   1% /run/user/999
/dev/sda1      ext4      253G   81G  160G  34% /mnt/boot-sav/sda1
/dev/sda6      ext4      411G   60G  331G  16% /mnt/boot-sav/sda6
/dev/sda7      ext4      244G  2.3G  230G   1% /mnt/boot-sav/sda7

=================== fdisk -l:
Disk /dev/loop0: 2.9 GiB, 3081154560 bytes, 6017880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1728df09

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048  538875903  538873856   257G 83 Linux
/dev/sda2        538877950 1953523711 1414645762 674.6G  5 Extended
/dev/sda5       1936887808 1953523711   16635904     8G 82 Linux swap / Solaris
/dev/sda6       1060780032 1936887807  876107776 417.8G 83 Linux
/dev/sda7        538877952 1060777983  521900032 248.9G 83 Linux

Partition table entries are not in disk order.




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by Zetetes on 2017-09-09
> **oldfred said:**
> perhaps jumping ahead.
Just to add to Bashing-om's post and use of ls to find boot files.

If it is a working install in another partition, you just need to know which partition (from ls commands).
I have used this to boot my other install in sda5. 

configfile (hd0,5)/boot/grub/grub.cfg

If you have an Ubuntu live installer, you also can use Boot-Repair to reinstall grub to MBR of a full reinstall of grub using advanced options where you choose which install to make the one in the MBR (if BIOS).

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

OldFred: This is 'sinking in' now. I've gone to the first link re: Boot-Info and copy~pasted the result into a 'quick reply' post ... Now on to the second link ... OK ... installed and used boot-repair according to the instructions in your link. In spite of me botching it (I panicked when it threw up a window asking me to delete the grub loader saying the computer would become unbootable causing me to reflexively select 'no' when I should have selected 'yes'), and the last window asking me which device to install to always responding with, 'you have not selected any device. Do you want to continue?' I finally selected 'yes' to continue without installing.  I thought I could go through it again if it was a total failure. However, restarting the machine did bring up a boot menu from which I successfully chose 'Ubuntu' for sda1 and Kylin, and then sda6 with Studio.  All is well.  That Boot-Repair process is awesome. I've saved the links for posterity.  I am much obliged for your help!

---

### Post by Zetetes on 2017-09-09
> **Bashing-om said:**
> Zetetes; Ho Kay !

grub rescue> is a hoss of another color - explains lots !

run:
```

set prefix=(hd0,msdos6)/boot/grub
set root=(hd0,msdos6)
insmod linux
linux (hd0,msdos6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,msdos6)/initrd.img
boot

```

once booted into the install, we can set grub to boot from the boot menu - but if you are going to install another system . we wait and see then the results after that install completes . The last linux install becomes that primary booting system .

all depends[INDENT][INDENT]on what you want
[/INDENT]
[/INDENT]


Bashing-om: I am currently in a live install disc of Ubuntu Studio doing as oldfred previously suggested: (1) I've just run Boot-Info from there and copy-pasted the (lengthy) result into a post here; and (2) I'm going to look into Boot-Repair for a few moments.  I can tell you, though, that my 'grub rescue>' prompt has rejected the command, 'linux', already.

---

### Post by Bashing-om on 2017-09-09
Zetetes; Hey;

I have been on this keyboard for an excess of 14 hours, My brain is miss-firing and my eyes are crossing.

I will pick this back up in my AM - for a short time as Duty calls for Saturday after noon.

we boot something - some where .

---

### Post by Zetetes on 2017-09-09
> **Bashing-om said:**
> Zetetes; Hey;

I have been on this keyboard for an excess of 14 hours, My brain is miss-firing and my eyes are crossing.

I will pick this back up in my AM - for a short time as Duty calls for Saturday after noon.

we boot something - some where .

I am dazed and confused myself at this point ... I greatly appreciate the assistance and wish you sweet dreams!

---

### Post by oldfred on 2017-09-09
Please do not post long terminal or text directly. With Boot-Repair just post the link it gives to pastebin site. If that does not work then manually post to pastebin.
For longer text use code tags. Easy to add with Forum's advanced editor and # icon.
 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) 


Did you leave Ubuntu in a suspended state as swap is not shown as swap but as suspend?

---

### Post by Zetetes on 2017-09-09
> **oldfred said:**
> Please do not post long terminal or text directly. With Boot-Repair just post the link it gives to pastebin site. If that does not work then manually post to pastebin.
For longer text use code tags. Easy to add with Forum's advanced editor and # icon.
 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) 


Did you leave Ubuntu in a suspended state as swap is not shown as swap but as suspend?

Sorry about that! (I can't say that without thinking of Don Adams). I really had no idea that the output of Boot-Info would be that voluminous.  It did not succeed in getting the info into the pastebin site so all I could think of was to paste it into the discussion.  It appears that I can't go back and delete it. I'll know better next time (hopefully never). 

As to leaving the system in a 'suspended' state, I don't know anything about that.  Both sda1 and sda6 are working well and 'normally' at this time, and I have a nice functional boot menu, since running boot-repair.  

I now have the problem to face that got me into this mess: The previous KXStudio install on sda7 is empty territory that I would like to merge or attach to sda6 which holds Ubuntu Studio. I noticed that, from Ubuntu Studio on sda6, I can see sda7 and click on it to mount it, just as I can do with Kylin on sda1.  Can I automount sda7 as a 'data partition' under sda6/Studio?  I have a lot to learn!

---

### Post by Bashing-om on 2017-09-09
Zetetes; Top-o-the-Morn'n

As you have marked the thread as solved;
did:
> 
Did you leave Ubuntu in a suspended state as swap is not shown as swap but as suspend?


lead to the solution ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-09
Hi, Bashing-om.  I confess: I do not know what that means (about Ubuntu being in a suspended state).  After running boot-info and boot-repair from the live install disc of Ubuntu Studio, I removed the install DVD, restarted the machine, found a nice-looking boot menu with my two Ubuntu installations (sda1 and sda6), and both started from the menu normally.  That satisfied me!  As to the meaning of 'suspension', I'm lost.  I see a swapfile in gparted so I'm not worried about that.

Now I want to have sda7 (the old deleted KXStudio) attached/merged/accessible to Ubuntu Studio on sda6, and I'm pondering how to do this...

Like many, I developed an antipathy for Microsoft in the late 80s and in the 90s, and I've wanted to go with Linux for a long time, but I would rather be able to get work done on it with upper level software than learn its anatomy and physiology.  Over the years of struggling with Linux, I have learned a few things to get me by, but I am still the rankest of outsiders when it comes to knowing the internal machinations of the Linux system.  I didn't give up on it, and won't, but I come to these forums occasionally like most people go to the doctor's office -- ill but ignorant of internal medicine.  When I learn to do something in the terminal, I feel good about it, but then see what the experts are talking about and realize I know nothing.

---

### Post by Bashing-om on 2017-09-09
Zetetes; Welp'

All's well that ends well .
linux is always a in-progress learning experience. No one knows it all about everything :)

As to deleting sda7 and merging it to another install, open a new thread and we address that there .

threads are like dead men -
[INDENT][INDENT][INDENT]one to the box
[/INDENT][/INDENT][/INDENT]

---

### Post by Zetetes on 2017-09-10
> **Bashing-om said:**
> Zetetes; Welp'

All's well that ends well .
linux is always a in-progress learning experience. No one knows it all about everything :)

As to deleting sda7 and merging it to another install, open a new thread and we address that there .

threads are like dead men -[INDENT][INDENT][INDENT]one to the box
[/INDENT]
[/INDENT]
[/INDENT]


Thanks, again!

---

