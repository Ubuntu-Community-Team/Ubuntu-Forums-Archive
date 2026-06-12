---
title: "Trouble with adding entries to grub2 menu."
date: 2013-11-17
forum: New to Ubuntu
---

### Post by jasiek96-parzydlo on 2013-11-17
Hello, I'm a new user. After updating from 12.04 to 13.10 my grub menu got edited and the link to Win7 is no longer there. I'm confused - where do I put the entry? Various sources give different solutions to this problem and I can't seem to get this to work. I've put it into /etc/grub.d/40_custom and I've used 'os-prober' which, I think added the entry to grub.cfg. Still not working. Help much appreciated.

---

### Post by deadflowr on 2013-11-17
If this doesn't help then post the output
```
sudo update-grub
```
As long as A)os-prober is not disabled, and B)The Windows Bootfiles are not corrupted, it should come back with an entry for Windows OS.
If it comes back without Windows listed, then there is a good chance that you need to run something like [EasyBCD]("http://neosmart.net/EasyBCD/")
which should fix the windows boot files.

---

### Post by jasiek96-parzydlo on 2013-11-17
```

 Generating grub.cfg ...Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found linux image: /boot/vmlinuz-3.5.0-43-generic
Found initrd image: /boot/initrd.img-3.5.0-43-generic
Found linux image: /boot/vmlinuz-3.5.0-42-generic
Found initrd image: /boot/initrd.img-3.5.0-42-generic
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

---

### Post by deadflowr on 2013-11-17
Windows 7 shows up in the menuentry listings.

When you reboot can you load Windows now?

---

### Post by jasiek96-parzydlo on 2013-11-17
No, the list ends at memtest entry.

---

### Post by oldfred on 2013-11-17
Scroll down.
Do you have a (very) tiny arrow in the lower right corner of the box around the grub entries? That says you have more entries.

You may want to house clean old kernels. I like to keep one older one just in case but delete the other older ones.
I prefer synaptic, but you can also use command line.

 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

If concern that you delete your current kernel you can make sure it still is installed.
# just to be sure latest kernel is installed
apt-get update
apt-get upgrade
apt-get dist-upgrade

---

### Post by jasiek96-parzydlo on 2013-11-18
I did try scrolling down ;) The entry is simply not there.

---

### Post by grahammechanical on 2013-11-18
Is that edited 40_custom (or renamed 40_custom) file executable? They normally are but it is worth a check. Does the File Manager>Properties>Permissions tab show a tick mark against Allow executing file as a program? 

Regards.

---

### Post by jasiek96-parzydlo on 2013-11-18
It is marked. Furthermore, I still have a ton of useless grub entries after cleaning old kernels with ubuntu-tweak. Oh and another thing: since I installed os-prober, shut down and restart on the top panel won't work :|

---

### Post by oldfred on 2013-11-18
I have never used ubuntu-tweak. If it removed kernels correctly you may need to run this to update menu.
sudo update-grub

You should not have to install os-prober, it is part of grub2?

and grub has nothing to do with gui after you have booted. Did you change something else or install/uninstall something else?

---

### Post by deadflowr on 2013-11-18
> **jasiek96-parzydlo said:**
> It is marked. Furthermore, I still have a ton of useless grub entries after cleaning old kernels with ubuntu-tweak. Oh and another thing: since I installed os-prober, shut down and restart on the top panel won't work :|

Are any of those useless entries the ones listed from the update-grub output?
Or are they totally different.

---

### Post by jasiek96-parzydlo on 2013-11-18
I did update grub manually after that. Also, I don't really know what broke the panel though. I installed tons of stuff, restarted, windows was not in the GRUB menu and I started to look around for a fix which resulted in installing os-prober which didn't work in the end.

---

### Post by oldfred on 2013-11-18
Your old kernels are 3.5 and new 3.11. So is this an upgrade?
Old kernels may not be registered in the install database of the new version and all you can do is manually remove them.
Then an update to grub will not find them.

---

### Post by jasiek96-parzydlo on 2013-11-18
Yes, this is an upgrade. I've upgraded from 12.04 to 12.10 but mouse and keyboard drivers did not install properly and I decided to install 13.10 from a live USB using the upgrade option. Now, how do I manually remove them? Shouldn't ubuntu-tweak have already done this for me? And the most important thing - how will it make an entry for WINDOWS 7 show up in grub??

---

### Post by oldfred on 2013-11-18
See post #6 on manually removing them using command line.

---

### Post by jasiek96-parzydlo on 2013-11-19
I'm having trouble with that too:
```

micro@buntu:/boot$ ls vmlinuz*
vmlinuz-3.11.0-13-generic             vmlinuz-3.5.0-40-generic
vmlinuz-3.11.0-13-generic.efi.signed  vmlinuz-3.5.0-42-generic
vmlinuz-3.5.0-23-generic              vmlinuz-3.5.0-43-generic
vmlinuz-3.5.0-39-generic
micro@buntu:/boot$ ls vmlinuz*
vmlinuz-3.11.0-13-generic             vmlinuz-3.5.0-40-generic
vmlinuz-3.11.0-13-generic.efi.signed  vmlinuz-3.5.0-42-generic
vmlinuz-3.5.0-23-generic              vmlinuz-3.5.0-43-generic
vmlinuz-3.5.0-39-generic
micro@buntu:/boot$ sudo apt-get purge vmlinuz-3.5.0-43-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vmlinuz-3.5.0-43-generic
E: Couldn't find any package by regex 'vmlinuz-3.5.0-43-generic'
micro@buntu:/boot$ 

```
What am I doing wrong?

---

### Post by oldfred on 2013-11-19
I think that just proves that it is not in the package index so apt cannot remove it.
But then you have to manually delete each file, but will also have to manually delete the support files also or everything that is -3.5.0-43-generic.

cd /boot
ls *-3.5.0-43*
sudo rm *-3.5.0-43*

Just be sure not to delete all kernels or the 3.11 versions. I like to keep 2 just to have an older one. 
Anything with an * can be dangerous as a space afterwards would then be everything and the rest of the line  ignored.

You can also run this.
gksudo nautilus
But again close as soon as you are done and be careful using it as working at root you can do anything or even accidentally delete the entire system.

---

### Post by jasiek96-parzydlo on 2013-11-20
**olfred**, I did this and removed files for all versions except the currently used one, updated grub after that. The boot menu still looks the same for some reason :| Just to make it clear, I don't really care about all that stuff being there as long as Windows is here as well.
This is what files are left in /boot directory:
```

micro@buntu:/boot$ sudo ls
[sudo] password for micro: 
abi-3.11.0-13-generic	      memtest86+_multiboot.bin
config-3.11.0-13-generic      System.map-3.11.0-13-generic
grub			      vmlinuz-3.11.0-13-generic
initrd.img-3.11.0-13-generic  vmlinuz-3.11.0-13-generic.efi.signed
memtest86+.bin

```

---

### Post by oldfred on 2013-11-20
If you ran sudo update-grub and they still show it may mean some sort of error on the update of grub so menu does not get updated? 
Or you are actually booting a different version of Ubuntu. But then you would have to have two installs.

rerun sudo update-grub and post both terminal output and copy of /boot/grub/grub.cfg. Use code tags from advanced editor as grub.cfg is longer.

---

### Post by jasiek96-parzydlo on 2013-11-20
update-grub:
```

micro@buntu:~$ sudo update-grub
[sudo] password for micro: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

grub.cfg:
```

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  fc5b9175-ea23-4f1d-b77e-d8cf6212566b
else
  search --no-floppy --fs-uuid --set=root fc5b9175-ea23-4f1d-b77e-d8cf6212566b
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-fc5b9175-ea23-4f1d-b77e-d8cf6212566b' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  fc5b9175-ea23-4f1d-b77e-d8cf6212566b
	else
	  search --no-floppy --fs-uuid --set=root fc5b9175-ea23-4f1d-b77e-d8cf6212566b
	fi
	linux	/boot/vmlinuz-3.11.0-13-generic root=UUID=fc5b9175-ea23-4f1d-b77e-d8cf6212566b ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.11.0-13-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-fc5b9175-ea23-4f1d-b77e-d8cf6212566b' {
	menuentry 'Ubuntu, with Linux 3.11.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-13-generic-advanced-fc5b9175-ea23-4f1d-b77e-d8cf6212566b' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  fc5b9175-ea23-4f1d-b77e-d8cf6212566b
		else
		  search --no-floppy --fs-uuid --set=root fc5b9175-ea23-4f1d-b77e-d8cf6212566b
		fi
		echo	'Loading Linux 3.11.0-13-generic ...'
		linux	/boot/vmlinuz-3.11.0-13-generic root=UUID=fc5b9175-ea23-4f1d-b77e-d8cf6212566b ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-13-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-13-generic-recovery-fc5b9175-ea23-4f1d-b77e-d8cf6212566b' {
	recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  fc5b9175-ea23-4f1d-b77e-d8cf6212566b
		else
		  search --no-floppy --fs-uuid --set=root fc5b9175-ea23-4f1d-b77e-d8cf6212566b
		fi
		echo	'Loading Linux 3.11.0-13-generic ...'
		linux	/boot/vmlinuz-3.11.0-13-generic root=UUID=fc5b9175-ea23-4f1d-b77e-d8cf6212566b ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-13-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  fc5b9175-ea23-4f1d-b77e-d8cf6212566b
	else
	  search --no-floppy --fs-uuid --set=root fc5b9175-ea23-4f1d-b77e-d8cf6212566b
	fi
	linux16	/boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd0,msdos5'  fc5b9175-ea23-4f1d-b77e-d8cf6212566b
	else
	  search --no-floppy --fs-uuid --set=root fc5b9175-ea23-4f1d-b77e-d8cf6212566b
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-AC2226F92226C7E2' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  AC2226F92226C7E2
	else
	  search --no-floppy --fs-uuid --set=root AC2226F92226C7E2
	fi
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
chainloader +1
}
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by oldfred on 2013-11-20
You only have Ubuntu with the one kernel & Windows in grub.cfg.
That is all you should see when booting.
If you are seeing something else, use camera, shrink to small size and attach with paperclip icon in advanced editor.

---

### Post by squakie on 2013-11-22
Also, hopefully you are not manually changing the grub.cfg file - you don't do that with grub2.  update_grub will just overwrite it.

---

### Post by jasiek96-parzydlo on 2013-11-22
[[img]http://s23.postimg.org/pxdy11h07/zdj_cie_1.jpg[/img]](http://postimg.org/image/pxdy11h07/)

[[img]http://s23.postimg.org/mp9gnzuqf/zdj_cie.jpg[/img]](http://postimg.org/image/mp9gnzuqf/)

---

### Post by oldfred on 2013-11-22
Did you run this?
sudo update-grub

If so download and run this, so we can see entire system configuration. 
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jasiek96-parzydlo on 2013-11-22
Of course I did, the last time I mentioned it was in post #20. I also pasted the output from the command line. I'm gonna try boot-repair now, thanks

---

### Post by squakie on 2013-11-22
We all get frustrated - try to remember that Oldfred is very knowledgable in ubuntu and is trying to help.

I also don't understand why, if the os prober finds windows and you run update-grub that it's not updateing the boot menu.  That is very strange. 

Oldfred:  I don't know, but it is possible that something got messed up in the file paths such that update-grub and/or os-prober is not actually putting the new file in /boot/grub?

OP:

via command line:

cd /
find -name grub.cfg

post the output baclk here.

---

### Post by oldfred on 2013-11-22
I had a typo in my 40_custom and it never updated grub.cfg, but created another file with a slightly different name. 
Also seen the same thing where there was a typo or extra lines in /etc/default/grub. But I thought grub gave an error referring to line number to help resolve it?

---

### Post by squakie on 2013-11-22
You're beyond me there - I've gotten lazy since grub2 started being used and just take the defaults ;)  I know sooner or later I'm going to need to go in and make some special changes - just not in a big hurry for that.  

Does update-grub create some sort of log file you can look in to see if it noted errors?

---

### Post by squakie on 2013-11-22
Perhaps we can come up with a way for the OP to search to be sure it's not creating a different file - some kind of find or something with a modifcation date or some such thing to isolate newly created files?  That way we could have the OP run sudo update-grub again then the find and see if there is a new file.

EDIT:  suggestion removed here - please see my post #31

---

### Post by oldfred on 2013-11-22
I do not see an error log, but in grub-mkconfig, it posts a warning and copies file to grub.cfg.new

>     echo "Syntax errors are detected in generated GRUB config file." >&2
    echo "Ensure that there are no errors in /etc/default/grub" >&2
    echo "and /etc/grub.d/* files or please file a bug report with" >&2
    echo "${grub_cfg}.new file attached." >&2


---

### Post by squakie on 2013-11-22
OP:  do the following - it will be a better option:

sudo update-grub
cd /
sudo find / -mmin 2  (EDIT: added the sudo to front of find - you need it)

This will shows us any files modifed (I don't know about newly created - may need to add another test) in the last 2 minutes.  Running this immediately after update-grub should hopefully show grub.cfg as having been modifed or show a different file if the were errors as per Oldfred above.

Please post back the terminal screen showing the update-grub all the way through everything until the prompt is returned after the find.


dave@davepc / $ cd /
dave@davepc / $ sudo find   /  -mmin 3
find: `/run/user/dave/gvfs': Permission denied
find: `/proc/5968/task/5968/fd/5': No such file or directory
find: `/proc/5968/task/5968/fdinfo/5': No such file or directory
find: `/proc/5968/fd/5': No such file or directory
find: `/proc/5968/fdinfo/5': No such file or directory
/home/dave/.local/share/cinnamon
/home/dave/.local/share/cinnamon/application_state
dave@davepc / $

---

### Post by squakie on 2013-11-22
> **oldfred said:**
> I do not see an error log, but in grub-mkconfig, it posts a warning and copies file to grub.cfg.new

I don't know if the find I just posted will show new files or just modifeid ones (I'm hoping it is just checking modified time, since on a new file that would still be there).  Maybe that will show something to help us trace what the heck is going on.

---

### Post by jasiek96-parzydlo on 2013-11-23
I've just run into another weird problem, the output list of 'find' is so long that terminal won't let me see the whole thing. When I scroll all the way to the top 'update-grub' output is no longer there. Any ideas?

---

### Post by oldfred on 2013-11-23
Post link to Bootinfo report from boot repair. 

And post this.
ls -l /boot/grub/grub*

---

### Post by squakie on 2013-11-23
> **oldfred said:**
> Post link to Bootinfo report from boot repair. 

And post this.
ls -l /boot/grub/grub*

If the file you mentioned was also grub.cfg - just with the .new, perhaps the find with grug.cfg.* might help to - it should compact the output to 1 or 2 files.  Only if you need it - I'm leaving this in your more than capable hand Oldfred - I just thought I'd throw that out there if it could help any.  Even a ls -al /boot/grub/grub.cfg would tell if it was updated after the update-grub.

I'm just going to stand by on the sidelines now - I don't want to disrupt Oldfred's help to you (sorry for butting in there Oldfred!). :0 ;)

EDIT:  ooppss!   that should be:

    cd /
 
   sudo  find . -name grub.* -mmin 2


do that right after a sudo update-grub  -  it should find only a bare minimum of files, not the long list

---

### Post by deadflowr on 2013-11-23
> **jasiek96-parzydlo said:**
> I've just run into another weird problem, the output list of 'find' is so long that terminal won't let me see the whole thing. When I scroll all the way to the top 'update-grub' output is no longer there. Any ideas?

That's because the terminal is set at 512 lines for the scroll back.
To change it go to edit > profile preferences > scrolling.
You can set the line to whatever you want, or better yet set it to unlimited.

---

### Post by jasiek96-parzydlo on 2013-11-29
I'm back and I have boot-repair info for you guys to look into :)
[URL="http://paste.ubuntu.com/6496143/"]http://paste.ubuntu.com/6496143/

[/URL]

---

### Post by oldfred on 2013-11-29
How did you get grub legacy? That has not been the standard grub since 9.04, but can be installed.
But all your updates looked like updates to grub2, but I do not see a grub.cfg from grub2, just the old menu.lst with grub legacy. And that old version of grub never found Windows 7 and we always had to manually add the boot entry.
I would just let Boot-Repair run its auto repairs. Make sure you have Internet connection and it will totally uninstall all of grub and  then download & reinstall grub2.

---

### Post by jasiek96-parzydlo on 2013-11-29
Ok, I'm gonna do this. So just in case something goes wrong and I lose access to either of the OS'es - thanks for all the effort guys. Jan.

---

### Post by jasiek96-parzydlo on 2013-11-29
Nope, didn't work. At least the menu looks better now and all that rubbish is gone. Still, Windows entry is not there. During the process it asked me which device should grub be installed on and it showed me the hard drive and sda5 as the second option. The third one was the USB drive I was using for the repair so I didn't mark it. It's almost like it didn't see the NTFS partition. But it is there, so I don't get what the problem is.
Here is the report it generated afterwards:
[http://paste.ubuntu.com/6496314/](http://paste.ubuntu.com/6496314/)

EDIT:
I tried it once more and here is what it looks like:
[[img]http://s10.postimg.org/w4pkar5np/wat.jpg[/img]](http://postimg.org/image/w4pkar5np/)

---

### Post by oldfred on 2013-11-29
Boot-Repair says you booted in UEFI mode? You need to consisently boot in BIOS/CSM/Legacy mode as both of your installs are BIOS based, not UEFI.

You are showing /grldr in both sda1 & sda2
 /grldr /bootmgr /Boot/BCD /grldr

Those are grub for dos files which are often used by EasyBCD. Did you try EasyBCD somewhere?
I would remove those files as they sometimes interfere.
Also was Windows hibernated?
Do not install grub to partitions, just MBR with BIOS booting.

Does not your 40_custom menu entry get added to grub menu on reboot? It looks correct?

You show nVidia, have you used nomodeset? Or is it booting ok?

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jasiek96-parzydlo on 2013-11-29
Thanks for the quick response. Sadly, I could not understand most of what you said there.
1. How do I boot into mode other than UEFI?
2.[COLOR=#000000]You are showing /grldr in both sda1 & sda2[/COLOR]
[COLOR=#000000]/grldr /bootmgr /Boot/BCD /grldr[/COLOR] - what does that mean?
[COLOR=#000000][/COLOR]3. I've never used EasyBCD.
4. Windows wasn't hibernated, I barely ever do it.
5. [COLOR=#000000]Do not install grub to partitions, just MBR with BIOS booting[/COLOR] - how do I do this? I'm one big newbie.
6. I don't think 40_custom gets added. Now in Grub2, I only have "Ubuntu" and "Advanced Ubuntu Options", which is normal or recovery mode. Nothing more.
7. I think it is booting just ok, except for showing a black screen for a few seconds after logging in.

---

### Post by oldfred on 2013-11-29
When you go into UEFI/BIOS you should get two entries for booting the Ubuntu live installer.
This shows the resulting screens, purple one is BIOS, grub menu is UEFI.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

/grldr is grub4dos files or folders. Just delete them in sda1 & sda2, do not delete any other files or folders. If concerned back them up first. If you did not use EasyBCD I am not sure where they came from.

You also show grub2 installed to the partition in your BootInfo report. Your screenshot in #40 shows the options to install to a MBR like sda or a partition like sda5. Only install to drives like sda, sdb etc, never partitions with one very few exceptions. As long as the copy in the MBR is the most current one that is all that is important now.

Script does show it did not find Windows on its own, but script seemed to mount sda1 & sda2 ok. And both sda1 & sda2 seem to have the standard first two Windows boot files that os-prober looks for. You should actually be able to boot from either directly.

Do you have a Windows repairCD or flash drive. You may need to run chkdsk on both sda1 & sda2.

---

### Post by jasiek96-parzydlo on 2013-11-29
I don't know if that's what you meant, but in the boot devices section in UEFI there is no entry for booting the USB in BIOS mode, only UEFI. I also deleted the grldr file. Next, I went trough boot-repair once again and there are a few things I noticed:
1. In the first menu where I choose all the options I want, I can also choose the default os that GRUB will boot. It lets me pick either Ubuntu or Win7, so I guess it kind of recognizes all Windows files necessary to boot it.
2. During the process it asks me to paste this command, is it all right?
```
sudo chroot "/mnt/boot-sav/sda5" apt-get install -y --force-yes grub-pc linux
```
(Next, I select to install GRUB to sda as you suggested)
3. After running the command mentioned above, when it's done it outputs the standard GRUB formula, but there is no Windows found to put it into grub.cfg. Didn't it just show Windows as an available os 30 seconds ago? Why is that happening?
```
Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
done


```

---

### Post by oldfred on 2013-11-29
Boot-Repair is seeing the NTFS partition, but for some reason os-prober as part of the update-grub is not seeing it. I still do not understand why 40_custom is not adding the manual entry? Is that still in 40_custom?

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some UEFI/BIOS have settings you have to turn on or off to get to CSM/BIOS boot mode. Some even require you to add a password. You should review Vendor manual on your system. It may be somewhere on your system or you have to download a pdf file by model number from your vendor's web site.

Post this:
cat /etc/grub.d/40_custom
And post this.
ls -l /boot/grub/grub*                 

Did you run chkdsk from your Windows repairCD on both sda1 & sda2?

---

### Post by jasiek96-parzydlo on 2013-11-30
```

micro@buntu:~$ cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```
```

micro@buntu:~$ ls -l /boot/grub/grub*
-r--r--r-- 1 root root 6162 lis 30 02:59 /boot/grub/grub.cfg
-rw-r--r-- 1 root root 1024 lis 30 19:45 /boot/grub/grubenv

```

I don't think I have the repairCD.
I'm going to look into the CMS/BIOS thingy but I'm posting this since 40_custom doesn't look alright to me.

---

### Post by oldfred on 2013-11-30
There must have been a total reinstall of grub as now your 40_custom does not have a Windows entry.

Copy both of the entries from post #20 into 40_custom and see it one or the other works.

---

### Post by jasiek96-parzydlo on 2013-12-01
It works! Now the only remaining problem is that I have 3 Windows7 entries. One for sda2 and two for sda1. How do I clean those up?

---

### Post by oldfred on 2013-12-01
Now it sounds like os-prober found an entry and you have the two from 40_custom? Or two from os-prober?

Boot-Repair often copies the two boot files from the (hidden in Windows) 100MB boot partition into the main install. Too many users do not know the boot partition exists or is essential and delete it without backups or repairCD. But then os-prober sees boot files in sda1 & sda2, so both get added to menu.

If your 40_custom entry works, you can turn off os-prober. If you ever add another system and do not know boot stanza to add to 40_custom, you can turn it back on.

Add grub disable line:
       gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

