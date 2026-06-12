---
title: "Removal of old versions of Ubuntu"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by davidhogg on 2011-11-09
Is there any way to remove previous versions of Ubuntu? I have a memory problem and I think this would solve it. The previous versions (and even 11-10 which i do not want to remove) are all contained in a folder called /dev/sda1/, but I am denied access to the folder.

---

### Post by Rex Bouwense on 2011-11-09
Are you talking about older kernels that remain on your hard drive when your system gets updated?  They really don't have any effect on RAM usage that I am aware of.

---

### Post by Silent Warrior on 2011-11-09
Memory problems? Ease off on the booze, then! :P

/Serious mode turn on
*A-hem* Well, about removing old versions of Ubuntu... If they're in separate partitions (i.e. / for Maverick in partition x, / for Natty in y, / for Oneiric in z), you just wipe the partition, but if you're concerned with old kernels, it's nowhere near as dramatic (though several more clicks of the mouse). Which description fits your situation?

---

### Post by Mark Phelps on 2011-11-09
If my "memory" you really mean "disk space" -- the for the tiny amount of space that will be freed up purging older kernel versions, it's really not worth the risk of purging the wrone one and rendering your PC unbootable.

---

### Post by davidhogg on 2011-11-11
OK I get the point.

---

### Post by davidhogg on 2011-11-11
I am not sure whether I am talking about kernels. The point is that when I boot the computer apart fro the latest version I see a whole let of [revious versions. But if they do not have any effect on the RAM then there is no point in removing them.

---

### Post by davidhogg on 2011-11-11
I'm not sure which description fits.

---

### Post by Gone fishing on 2011-11-11
You can purge the old kernels quite easily using synaptic or the software center just search for linux-image and remove the older images. Leave the latest image and the one before and you should be OK. 

However, you will simply free up a few 100 Meg of disk space - that is all, it wont make the box faster use less RAM etc.

---

### Post by bryncoles on 2011-11-11
perhaps to help people understand what you're asking, you could open a terminal and type ```
sudo fdisk -l
``` and post the section which looks something like 

> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2000   480000000   240000000   63  Linux
/dev/sda2       480000000   480000000     3100000    3  Extended
/dev/sda3       480000000   480000000     3100000   62  Linux swap / Solaris


---

### Post by Silent Warrior on 2011-11-11
He already stated that he wants to get rid of kernels, we don't really need to see his partition layout at this point.

davidhogg: As you said, you don't HAVE to remove them - but they are still some of the biggest components on your system in terms of Mb (90-200 apiece). If you haven't done anything interesting with your installation, you'll be running the 3.0-kernel. If you ever run low on space on your / partition, make it your first priority to remove the older kernels (2.6-series - don't forget the headers, modules, backports, image, etc.).

---

### Post by davidhogg on 2011-11-12
My question is HOW specifically I go about removing kernels, I don't find them anywhere.:P

---

### Post by Gone fishing on 2011-11-12
> My question is HOW specifically I go about removing kernels, I don't find them anywhere

Use synaptic or the Ubuntu Software Center and 

> search for linux-image and remove the older images. Leave the latest image and the one before

---

### Post by 3rdalbum on 2011-11-12
Removing them frees up disk space, but not RAM. Just thought I'd clarify that in case you were operating under a misconception.

---

### Post by thane1 on 2011-11-12
If I understand this correctly, you are wanting to remove the old ubuntu version choices from one of the first start up screens such as:

ubuntu ver xxx
ubuntu ver xxxx
ubuntu ver xxx recovery mode
(and maybe windows or another os if dual booting)

If this is the case, you can start up a Terminal session and enter the following code, using the version of ubuntu (linux image) , that you don't want to see any more on start up.

[HTML]sudo apt-get remove linux-image-2.6.35-30-generic[/HTML]

Just substitute the version designation, that you don't want to be displayed any longer for the 2.6.35-30-generic in the example above.  Enter your password, when prompted and all should be fine.  Cheers

---

### Post by Paqman on 2011-11-12
> **Gone fishing said:**
> Leave the latest image and the one before and you should be OK. 


I wouldn't bother leaving the one before. If you're trying to free up space on your hard drive I'd get rid of all the old ones, as they're pretty big. 

Keeping a spare kernel on the stable release is excessively conservative IMO. If the latest kernel is working fine (which it almost certainly will be) then just keep that one. If you're in any doubt that you've picked the right kernel to keep make sure you check linux-generic for reinstallation before hitting the "apply" button in Synaptic.

---

### Post by kalehrl on 2011-11-12
> My question is HOW specifically I go about removing kernels, I don't find them anywhere.:razz:

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---

### Post by bryncoles on 2011-11-12
> **Silent Warrior said:**
> He already stated that he wants to get rid of kernels, we don't really need to see his partition layout at this point.

davidhogg: As you said, you don't HAVE to remove them - but they are still some of the biggest components on your system in terms of Mb (90-200 apiece). If you haven't done anything interesting with your installation, you'll be running the 3.0-kernel. If you ever run low on space on your / partition, make it your first priority to remove the older kernels (2.6-series - don't forget the headers, modules, backports, image, etc.).

Whoops!  I think I'll go and clean my glasses... I must have missed that ;-)

---

### Post by davidhogg on 2011-11-12
An additional problem in following your excellent advice is the Dash Home is not working, so I don't know how to find the terminal.

---

### Post by davidhogg on 2011-11-12
An additional problem in following your excellent advice is that Dash  Home is not working, so I don't know how to find the terminal.

---

### Post by Chronon on 2011-11-12
If you are using Unity you should be able to type in the first few letters of the name into the search field, or simply enter Alt+F2 and enter "terminal".

---

### Post by Miljet on 2011-11-12
Or ctrl+Alt+t

---

### Post by bioterror on 2011-11-13
> **davidhogg said:**
> An additional problem in following your excellent advice is the Dash Home is not working, so I don't know how to find the terminal.

As this is marked under Lubuntu I will answer:
Press "alt+f2" and you will get launcher where you can type ```
lxterminal
```

Now you should get that terminal.
If that doesnt help, you can always fallback to the TTY1 for example by pressing ctrl+alt+f1 and you can always return to X by pressing (ctrl+)alt+f7 (or f8, if something has failed on F7 and X is moved to tty9)

---

### Post by davidhogg on 2011-11-13
Alt-F2 works fine, but the message says "Run a command". Unfortunately, I don't know what 'command' to run to get the Terminal.

---

### Post by bioterror on 2011-11-13
> **davidhogg said:**
> Alt-F2 works fine, but the message says "Run a command". Unfortunately, I don't know what 'command' to run to get the Terminal.

lxterminal

---

### Post by davidhogg on 2011-11-13
I can't open the software center.

---

### Post by davidhogg on 2011-11-13
Is 'lxterminal' a command? It doesn't look like a command. Also, it doesn't work.

---

### Post by Paqman on 2011-11-13
> **davidhogg said:**
> Is 'lxterminal' a command? It doesn't look like a command. Also, it doesn't work.

Lxterminal is the name of the default terminal in Lubuntu. The command to launch an application is just the application's name, for example, hitting Alt-F2 and typing firefox will launch it.

I can't imagine why you can't launch lxterminal, check you're spelling it right. You can switch to a command line by hitting Ctrl-Alt-F1. To switch back to the graphical desktop hit Ctrl-Alt-F7.

---

### Post by davidhogg on 2011-11-13
Im not using Lubuntu, Im using Ubuntu. Perhaps the reason why it doesn't work. but 'firefox' doesn't work either.

---

### Post by bkratz on 2011-11-13
The command in post 21 will put you in terminal mode.

---

### Post by davidhogg on 2011-11-13
I don't quite understand what you mean,

---

### Post by davidhogg on 2011-11-13
What is post 21?

---

### Post by bkratz on 2011-11-13
> **davidhogg said:**
> What is post 21?



The 21st post in this thread. It says

 ctrl+Alt+t

If you do this you are in the terminal mode shown by something like

---

### Post by bkratz on 2011-11-13
Since what you seem to be interested in is removing old kernels that show up at boot time, here is the guide.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by Paqman on 2011-11-13
> **bkratz said:**
> Since what you seem to be interested in is removing old kernels that show up at boot time, here is the guide.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

Note that if you want to use Synaptic as suggested in that article, it is no longer installed by default in Ubuntu. It's a good way to clean out old kernels, but you would need to install it first.

---

### Post by bkratz on 2011-11-13
> **Paqman said:**
> Note that if you want to use Synaptic as suggested in that article, it is no longer installed by default in Ubuntu. It's a good way to clean out old kernels, but you would need to install it first.



Thanks, I always forget that (stuck back in the 10.04 era!)

---

### Post by davidhogg on 2011-11-13
> **Paqman said:**
> I wouldn't bother leaving the one before. If you're trying to free up space on your hard drive I'd get rid of all the old ones, as they're pretty big. 

Keeping a spare kernel on the stable release is excessively conservative IMO. If the latest kernel is working fine (which it almost certainly will be) then just keep that one. If you're in any doubt that you've picked the right kernel to keep make sure you check linux-generic for reinstallation before hitting the "apply" button in Synaptic.
The message I get when I type this command with 2.6.35.28 is "couldn't find linux-image-2.6.35.28-generic. I wonder why since this appears among the previous versions.

---

### Post by Elfy on 2011-11-13
> **davidhogg said:**
> Im not using Lubuntu, Im using Ubuntu. Perhaps the reason why it doesn't work. but 'firefox' doesn't work either.I changed the thread prefix to ubuntu - it was showing as lubuntu - hence people assuming that.

> **davidhogg said:**
> The message I get when I type this command with 2.6.35.28 is "couldn't find linux-image-2.6.35.28-generic. I wonder why since this appears among the previous versions.If they are not showing in any of the package managers like synaptic - they _might_ be sitting in /boot and being picked up by grub update, I've had similar in the recent(ish) past.

---

### Post by Paqman on 2011-11-13
It's also possible that they're not installed and that you simply need Grub to update its list. Grub should update the list whenever you remove or install a new kernel, but you can prompt it to update with the command:
```
sudo update-grub
```

---

### Post by philinux on 2011-11-13
Remove old kernels with a gui.

 [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by davidhogg on 2011-11-13
> **bkratz said:**
> The 21st post in this thread. It says

 ctrl+Alt+t

If you do this you are in the terminal mode shown by something like
Thanks. I don't understand the numbering system, but it's true that Ctl-Alt-t opens the Terminal.

---

### Post by davidhogg on 2011-11-13
> **Paqman said:**
> It's also possible that they're not installed and that you simply need Grub to update its list. Grub should update the list whenever you remove or install a new kernel, but you can prompt it to update with the command:
```
sudo update-grub
```
The command 'update-grub' produces a list of linus images which says if found, such as 3.0.0.13, which are not present in the list I am referring to. And, although 2.6.35.8 was successfully removed, it still appears on the list.

---

### Post by Elfy on 2011-11-13
david - can you open a terminal - run this command and then copy the whole lot here for us please.

```
dpkg -l linux-image* && sudo update-grub && ls /boot
```

---

### Post by Paqman on 2011-11-13
> **davidhogg said:**
> The command 'update-grub' produces a list of linus images which says if found, such as 3.0.0.13, which are not present in the list I am referring to. And, although 2.6.35.8 was successfully removed, it still appears on the list.

Do you have more than one Linux system installed on your machine? If so, boot up into the other one and run the same command, and it will clean up the list. It sounds like the Grub entry on your Master Boot Record is pointing to a different Linux installation for its config files.

---

### Post by Elfy on 2011-11-13
> **Paqman said:**
> Do you have more than one Linux system installed on your machine? If so, boot up into the other one and run the same command, and it will clean up the list. It sounds like the Grub entry on your Master Boot Record is pointing to a different Linux installation for its config files.

If that is the case it might be a good thing to reinstall grub for the right install once you've got it all sorted out.

Good catch Paqman.

---

### Post by davidhogg on 2011-11-13
> **forestpiskie said:**
> david - can you open a terminal - run this command and then copy the whole lot here for us please.

```
dpkg -l linux-image* && sudo update-grub && ls /boot
```
I've run the command with interesting results. Is there any way of copying this into a quick reply?

---

### Post by davidhogg on 2011-11-13
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda1
done
abi-3.0.0-12-generic         memtest86+_multiboot.bin
abi-3.0.0-13-generic         System.map-3.0.0-12-generic
config-3.0.0-12-generic      System.map-3.0.0-13-generic
config-3.0.0-13-generic      vmcoreinfo-3.0.0-12-generic
grub                         vmcoreinfo-3.0.0-13-generic
initrd.img-3.0.0-12-generic  vmlinuz-3.0.0-12-generic
initrd.img-3.0.0-13-generic  vmlinuz-3.0.0-13-generic
memtest86+.bin

---

### Post by davidhogg on 2011-11-13
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda1
done
abi-3.0.0-12-generic         memtest86+_multiboot.bin
abi-3.0.0-13-generic         System.map-3.0.0-12-generic
config-3.0.0-12-generic      System.map-3.0.0-13-generic
config-3.0.0-13-generic      vmcoreinfo-3.0.0-12-generic
grub                         vmcoreinfo-3.0.0-13-generic
initrd.img-3.0.0-12-generic  vmlinuz-3.0.0-12-generic
initrd.img-3.0.0-13-generic  vmlinuz-3.0.0-13-generic
memtest86+.bin

---

### Post by davidhogg on 2011-11-13
> **davidhogg said:**
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda1
done
abi-3.0.0-12-generic         memtest86+_multiboot.bin
abi-3.0.0-13-generic         System.map-3.0.0-12-generic
config-3.0.0-12-generic      System.map-3.0.0-13-generic
config-3.0.0-13-generic      vmcoreinfo-3.0.0-12-generic
grub                         vmcoreinfo-3.0.0-13-generic
initrd.img-3.0.0-12-generic  vmlinuz-3.0.0-12-generic
initrd.img-3.0.0-13-generic  vmlinuz-3.0.0-13-generic
memtest86+.bin
Copy of relevant parts of Terminal window after running the command 'dpkg linux-image* && sudo update-grub && ls /boot'

---

### Post by davidhogg on 2011-11-13
> **davidhogg said:**
> Copy of relevant parts of Terminal window after running the command 'dpkg linux-image* && sudo update-grub && ls /boot'
Sorry, the complete command should have '-l' before 'linux-image*;

---

### Post by davidhogg on 2011-11-17
All is fine, except that I still see the previous versions on the screen, even though they appear to have been removed.

---

### Post by davidhogg on 2011-11-17
> **davidhogg said:**
> All is fine, except that I still see the previous versions on the screen, even though they appear to have been removed.
What does this line mean?

grub-mkconfig: you must run this as root

---

### Post by davidhogg on 2011-11-17
Yes, here it is.
/dev/sda1   *        2048   207365674   103681813+  83  Linux
/dev/sda2       207366142   234440703    13537281    5  Extended
/dev/sda5       225232896   234440703     4603904   82  Linux swap / Solaris
/dev/sda6       207366144   222615551     7624704   83  Linux
/dev/sda7       222617600   225230847     1306624   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Elfy on 2011-11-17
Please go here - follow the instructions.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by davidhogg on 2011-11-17
david@david-Aspire-3100:~$ sudo bash -/Downloads/boot-info-script060
[sudo] password for david: 
bash: -/: invalid option
Usage:    bash [GNU long option] [option] ...
    bash [GNU long option] [option] script-file ...
GNU long options:
    --debug
    --debugger
    --dump-po-strings
    --dump-strings
    --help
    --init-file
    --login
    --noediting
    --noprofile
    --norc
    --posix
    --protected
    --rcfile
    --restricted
    --verbose
    --version
Shell options:
    -irsD or -c command or -O shopt_option        (invocation only)
    -abefhkmnptuvxBCHP or -o option
david@david-Aspire-3100:~$ sudo bash -/Downloads/boot_info_script060.sh
bash: -/: invalid option
Usage:    bash [GNU long option] [option] ...
    bash [GNU long option] [option] script-file ...
GNU long options:
    --debug
    --debugger
    --dump-po-strings
    --dump-strings
    --help
    --init-file
    --login
    --noediting
    --noprofile
    --norc
    --posix
    --protected
    --rcfile
    --restricted
    --verbose
    --version
Shell options:
    -irsD or -c command or -O shopt_option        (invocation only)
    -abefhkmnptuvxBCHP or -o option

---

### Post by davidhogg on 2011-11-17
I obviously made a mistake somewhere.

---

### Post by oldos2er on 2011-11-17
```
david@david-Aspire-3100:~$ sudo bash [COLOR="Red"]-[/COLOR]/Downloads/boot-info-script060
```

The character in red should be a tilde ~ not a dash -

---

### Post by davidhogg on 2011-11-17
> **oldos2er said:**
> ```
david@david-Aspire-3100:~$ sudo bash [COLOR="Red"]-[/COLOR]/Downloads/boot-info-script060
```

The character in red should be a tilde ~ not a dash -
david@david-Aspire-3100:~$ sudo bash ~/Downloads/boot_info_script060
[sudo] password for david: 
/home/david/Downloads/boot_info_script060: /home/david/Downloads/boot_info_script060: is a directory
david@david-Aspire-3100:~$

---

### Post by davidhogg on 2011-11-17
> **davidhogg said:**
> david@david-Aspire-3100:~$ sudo bash ~/Downloads/boot_info_script060
[sudo] password for david: 
/home/david/Downloads/boot_info_script060: /home/david/Downloads/boot_info_script060: is a directory
david@david-Aspire-3100:~$
The program seems to have automatically replaced the tilde with a complete path - but not the correct one. The correct path is /Home/Downlads/. I don't know how to put this right.

---

### Post by Silent Warrior on 2011-11-17
Yes, that path is entirely correct. ~ points to the current user's home directory - it's as correct as it's possible to get. However, it seems boot_info_script060 isn't a file, but a directory - verify this by going into your favoured file manager and check. You might also want to right-click the file, wherever it is, enter Properties, and make sure it can be executed (Permissions tab).
If you're still attempting to clear up your kernels, did you try this:
```
sudo apt-get remove linux-image-generic-3.0.0-12
```

---

### Post by davidhogg on 2011-11-18
> **Silent Warrior said:**
> Yes, that path is entirely correct. ~ points to the current user's home directory - it's as correct as it's possible to get. However, it seems boot_info_script060 isn't a file, but a directory - verify this by going into your favoured file manager and check. You might also want to right-click the file, wherever it is, enter Properties, and make sure it can be executed (Permissions tab).
If you're still attempting to clear up your kernels, did you try this:
```
sudo apt-get remove linux-image-generic-3.0.0-12
```
Boot Info Script 0.60    from 17 May 2011

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   207,365,674   207,363,627  83 Linux
/dev/sda2         207,366,142   234,440,703    27,074,562   5 Extended
/dev/sda5         225,232,896   234,440,703     9,207,808  82 Linux swap / Solaris
/dev/sda6         207,366,144   222,615,551    15,249,408  83 Linux
/dev/sda7         222,617,600   225,230,847     2,613,248  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        d9d58899-8c8f-4ef2-ad2a-879bb1406159   ext4       
/dev/sda5        f4c5971e-38d0-4ec4-9904-23c457aef95b   swap       
/dev/sda6        f75776f4-e766-4ca5-b136-b64262b6f711   ext4       
/dev/sda7        63ae6d97-4d6a-4874-895f-664f099e10b7   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f4c5971e-38d0-4ec4-9904-23c457aef95b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1

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

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=f75776f4-e766-4ca5-b136-b64262b6f711 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f75776f4-e766-4ca5-b136-b64262b6f711
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro single
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro single
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d9d58899-8c8f-4ef2-ad2a-879bb1406159
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=d9d58899-8c8f-4ef2-ad2a-879bb1406159 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f75776f4-e766-4ca5-b136-b64262b6f711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=63ae6d97-4d6a-4874-895f-664f099e10b7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                initrd.img                                     3
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff f6 49 b1 f3 ff fb 52  c0 b3 80 0b 79 2d 61 e4  |..I....R....y-a.|
00000010  85 6b c9 6c a4 ec 3c 71  a1 79 ac 47 7d ab 5b 46  |.k.l..<q.y.G}.[F|
00000020  96 96 55 41 a8 88 0e b6  9b 8d c4 00 01 c1 a0 4e  |..UA...........N|
00000030  1d 0b 6f 14 ba d5 7f c1  60 52 66 6c d8 cc 9b c4  |..o.....`Rfl....|
00000040  ed b5 27 67 e2 30 85 07  3f 95 e7 a4 3f 6b 55 71  |..'g.0..?...?kUq|
00000050  11 34 6e 2b 10 86 4f 54  4b 49 d7 09 2a 50 34 89  |.4n+..OTKI..*P4.|
00000060  12 2d 8a 07 b2 b2 57 b2  4b cb 63 b5 2d dd ad f7  |.-....W.K.c.-...|
00000070  da ff c2 b6 5b 9b 75 2d  cf 29 5d e7 a6 a4 f8 ac  |....[.u-.)].....|
00000080  89 f1 60 53 b4 14 72 cb  20 00 15 0f 10 35 ae 25  |..`S..r. ....5.%|
00000090  59 6c b7 5b ef 35 b3 20  90 cc 26 80 06 4d 98 22  |Yl.[.5. ..&..M."|
000000a0  66 51 3f 19 a5 6a e2 ff  71 cf 1b 13 76 87 f2 1f  |fQ?..j..q...v...|
000000b0  98 90 26 d4 71 c5 8d 0e  04 00 b9 26 05 c5 0c 0e  |..&.q......&....|
000000c0  1d 5c 7a 16 c2 15 9c 5b  94 59 e9 cd b6 90 8d 16  |.\z....[.Y......|
000000d0  3a 97 ab ef f4 ef ff fb  52 c0 b6 00 0c 09 09 5b  |:.......R......[|
000000e0  a4 85 6b 89 6e 25 2b 3c  90 a1 78 bf ee df fa 42  |..k.n%+<..x....B|
000000f0  d7 b6 1a 05 75 80 19 45  25 30 00 0e 06 e6 63 34  |....u..E%0....c4|
00000100  4e 2c c7 23 56 b9 ad fe  5a 45 d7 f7 5e 98 e5 a6  |N,.#V...ZE..^...|
00000110  79 29 ab 53 86 40 8f b9  fe f3 f9 db f5 79 66 b4  |y).S.@.......yf.|
00000120  b3 5f 41 12 82 c0 4a 90  2d 03 07 8b 33 c9 c2 60  |._A...J.-...3..`|
00000130  f8 54 39 38 56 59 dd 86  59 c3 da ca 69 88 e2 3f  |.T98VY..Y...i..?|
00000140  bb 1f 6d 7f 15 6c eb 6e  93 ea 8b 37 cd 0d 90 03  |..m..l.n...7....|
00000150  64 5f f6 60 85 00 70 70  66 88 ae 05 77 13 8a 58  |d_.`..ppf...w..X|
00000160  98 fb 9c cd 50 9e 98 a2  4f 26 aa 74 cd 88 a9 1d  |....P...O&.t....|
00000170  57 4c 89 d9 23 f1 e9 5c  94 3c b7 f8 e6 6f b2 16  |WL..#..\.<...o..|
00000180  1c ba 3b d1 10 68 4c a9  6c 6a cc 82 24 28 41 2c  |..;..hL.lj..$(A,|
00000190  bd 4d 49 1b c1 bc fd 66  a2 fa 8a 1f ed d5 ef 2f  |.MI....f......./|
000001a0  7f f5 b9 99 1c f1 b9 ff  fb 52 c0 b6 00 0b dd 2f  |.........R...../|
000001b0  49 a7 85 2b c9 6d a6 27  a9 80 a1 79 fc f9 00 fe  |I..+.m.'...y....|
000001c0  ff ff 82 fe ff ff 02 a0  10 01 00 80 8c 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 b0 e8 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by davidhogg on 2011-11-18
The script generated a s-called "Results.txt" file. I've copied the whole file. Rather long, I'm afraid. And I don't know how to interpret it!

---

### Post by Elfy on 2011-11-18
I'm sure someone else will be along - I'm shortly off out. 

But assuming that you wish to keep 11.10 and remove 11.04 it should be as simple as booting the 11.10 livecd.

Delete the 11.04 partition and it's swap.
Reinstall grub for 11.10 in case grub is booting from 11.04
Reboot into 11.10 and run update-grub.

---

### Post by davidhogg on 2011-11-18
Yes, I have, but it generates an error message, basically saying it can't find the file (if it is a file).

---

### Post by davidhogg on 2011-11-18
> **davidhogg said:**
> Yes, I have, but it generates an error message, basically saying it can't find the file (if it is a file).
Yes, I have, but it generates an error message, basically saying it can't find the file (if it is a file).

---

### Post by davidhogg on 2011-11-18
> **davidhogg said:**
> Yes, I have, but it generates an error message, basically saying it can't find the file (if it is a file).
Actually the error message concerned 2.6.38.11-generic, not 3.0.0.12-generic which as I understand it is 11.4.

---

### Post by davidhogg on 2011-11-18
> **davidhogg said:**
> Actually the error message concerned 2.6.38.11-generic, not 3.0.0.12-generic which as I understand it is 11.4.
11.4 (linux-image-3.0.0.12-generic) was successfully renoved.

---

### Post by davidhogg on 2011-11-18
If you're going out, thanks for your help!

---

### Post by davidhogg on 2011-11-18
I have succeeded. I'm not quite sure how. I still need some help though. Mu Ubuntu Software Center doesn''t work. Nor dies the thing called Dash Home.

---

### Post by davidhogg on 2011-11-18
> **davidhogg said:**
> I have succeeded. I'm not quite sure how. I still need some help though. Mu Ubuntu Software Center doesn''t work. Nor dies the thing called Dash Home.
Dash Home is useful, but there must be other ways of launching programmes - through the Terminal, fir example. But O dpm't know the basic syntax.

---

### Post by davidhogg on 2011-11-18
> **davidhogg said:**
> Dash Home is useful, but there must be other ways of launching programmes - through the Terminal, fir example. But O dpm't know the basic syntax.
I don't know the basic syntax.

---

### Post by Elfy on 2011-11-18
> **davidhogg said:**
> Actually the error message concerned 2.6.38.11-generic, not 3.0.0.12-generic which as I understand it is 11.4.

> **davidhogg said:**
> 11.4 (linux-image-3.0.0.12-generic) was successfully renoved.

> **davidhogg said:**
> If you're going out, thanks for your help!

> **davidhogg said:**
> I have succeeded. I'm not quite sure how. I still need some help though. Mu Ubuntu Software Center doesn''t work. Nor dies the thing called Dash Home.

As the thread is marked solved then I am glad you got there - but am slightly confused - if you removed one of the kernels for 11.10 I'd assume the other 2.6.* ones still show as they are in a completely different partition and will be found by the os-prober part of grub update.

---

### Post by Elfy on 2011-11-18
> **davidhogg said:**
> Dash Home is useful, but there must be other ways of launching programmes - through the Terminal, fir example. But O dpm't know the basic syntax.

> **davidhogg said:**
> I don't know the basic syntax.

Might be best to start a new thread for new issues.

---

