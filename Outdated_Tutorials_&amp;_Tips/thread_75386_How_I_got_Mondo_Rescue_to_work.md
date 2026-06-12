---
title: "How I got Mondo Rescue to work"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by GrayMagiker on 2005-10-13
**Disclaimer**
This is what worked for me, i make no promises that it will work for you.  As with all backup solutions this should be tested under all possible conditions multiple times before being put into use as a primary solution. I am not an expert on Ubuntu, Linux, Mondo, or anything else computer related.  I will not be held liable for any damage to anything in any way because you have read this and/or tried this procedure, I disavow all claims of warranty or responsibility for your failure to take proper precautions. 
** (/Disclaimer) **

I did this on a test system that it didn't really matter if it came back up, I suggest you do the same.

1. Install Mondo from synaptic.  Do not try and install from source and/or RPM's unless you are sure you know what you are doing and/or you are looking for a challenge.

1b.  Of course installing from apt-get would do the same thing
```

sudo apt-get install mondo

```

2.  Update your Ubuntu, make sure everything is up to date.  I don't know if this helps but it sure couldn't hurt.  

3.  Enter the following at the command prompt to make two new directories under the root directory.  They can be called anything you want, if you use different names be sure to change the rest of the commands in order to match.
```

$ sudo cd /
$ sudo mkdir iso
$ cd iso
$ sudo mkdir isotmp
$ cd ..

```

4.  Now for the fun part, actually making a back up CD.  I made an ISO because I intend to use this solution on systems with large hard drives and it will take multiple CD's, and I want it to run without having to change CD's a bunch.  Enter the following command to make a backup.  

```

$ sudo mondoarchive -Oi -9 -k FAILSAFE -s700m -S /iso/tmpiso -E /iso -d /iso

```

4b.  Explanation of switches used
-Oi tells mondo to make an ISO archive not burn to any removable media.

-9 specifies the compression level, 9 is the highest 0 is none.  This is optional, the default is 3.

-k FAILSAFE tells mindi to use the FAILSAFE kernel, mindi is not real compatible with debian (and therefore ubuntu) so we use this to be on the safe side

-s700m tells the size of the media, if we are using standard CD-R's to burn the iso's to latter than this is good.  "m" means megabytes other multipliers can be used here

-S /iso/tmpiso tells mondo to use /iso/tmpiso as temp storage to build the iso images

-E /iso tells mondo not to back up the directory it is working from.  This is very important and seemed to be what I was doing wrong before.

-d /iso tells mondo where to put the iso images when it is done.  

5.  Use your favorite method to burn the iso's to a CD.  The first one is bootable, stick it in and follow the directions.  
--Type "compare" to check files against the originals still on the disk
--Type "nuke" to wipe the disk and restore everything
--Type "interactive" to restore some files

**Notes**
This was done on a fresh install of Ubuntu Horary with no other packages installed.  

This is what I learned from days at trying to get it to work, it may take you as long or longer to get it to work for you.

During the "compare" and "restore"  phases it seemed to generate a lot of error messages, but it still worked ok.  I don't know the problem, but if it ain't broke don't fix it in my opinion.  

Online man page for mondoarchive can be found at [http://ccp14.minerals.csiro.au/ccp/web-mirrors/mondorescue/download/mondoarchive.1.html](http://ccp14.minerals.csiro.au/ccp/web-mirrors/mondorescue/download/mondoarchive.1.html)
there are a lot of options which I did not cover, check them out here.  

The mondo website is at
[http://mondorescue.org](http://mondorescue.org)
They have a nice forum there which you might check out and search for your issue if it is not resolved by this.

A helpful more in depth guide on all the features can be found by going to the Mondo website and going to support and clicking on the PDF link.  

That is all for now.

---

### Post by chanders on 2005-10-13
Hey! Great HOWTO. I myself have used mondo in the past and it has helped me out of countless hairy situations...

You can also use the graphical user interface by running 

```
mondoarchive
```

Another good tool is partimage, but you need to make sure the partition that you are backing up is not mounted.

---

### Post by TristanMike on 2006-01-17
Hi, I'm trying to burn a back up DVD using this program, but I keep getting a "Manual CD tray + DVD not supported yet." error just before it starts to burn then crashes out. Here is the out put from the log file. ```
running: dmesg -n1 > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
Mondo Archive v2.04 --- http://www.mondorescue.org
running on i386 architecture
-----------------------------------------------------------
NB: Mondo logs almost everything, so don't panic if you see
some error messages.  Please read them carefully before you
decide to break out in a cold sweat.    Despite (or perhaps
because of) the wealth of messages. some users are inclined
to stop reading this log. If Mondo stopped for some reason,
chances are it's detailed here.  More than likely there's a
message at the very end of this log that will tell you what
is wrong. Please read it!                          -Devteam
-----------------------------------------------------------
Zero...
[Main] main.c->welcome_to_mondoarchive#173: One...
	[Main] main.c->welcome_to_mondoarchive#174: Two...
		[Main] main.c->welcome_to_mondoarchive#175: Three...
			[Main] main.c->welcome_to_mondoarchive#176: Four...
	[Main] main.c->distro_specific_kludges_at_start_of_mondoarchive#193: Unmounting old ramdisks if necessary
running: umount `mount | grep shm | grep mondo | cut -d' ' -f3` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
Usage: umount [-hV]
umount -a [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
umount [-f] [-r] [-n] [-v] special | node...
--------------------------------end of output------------------------------
...ran with res=512
running: mount | grep cdrom | grep super > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=256
running: mount | grep floppy | grep super > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=256
		[Main] libmondo-tools.c->stop_autofs_if_necessary#1361: No autofs detected.
[Main] libmondo-tools.c->mount_boot_if_necessary#1398: Started sub
			[Main] libmondo-tools.c->mount_boot_if_necessary#1399: About to set g_boot_mountpt[0] to '\0'
			[Main] libmondo-tools.c->mount_boot_if_necessary#1401: Done. Great. Seeting command to something
			[Main] libmondo-tools.c->mount_boot_if_necessary#1403: Cool. Command = 'cat /etc/fstab | grep -v ":" | grep -vx "#.*" | grep -w "/boot" | tr -s ' ' '	' | cut -f1 | head -n1'
			[Main] libmondo-tools.c->mount_boot_if_necessary#1405: tmp = ''
[Main] libmondo-tools.c->mount_boot_if_necessary#1448: Ended sub
[Main] libmondo-tools.c->get_kernel_version#409: g_kernel_version = 2.610000
[Main] libmondo-tools.c->reset_bkpinfo#974: Hi
root is mounted at /dev/hda

No, Schlomo, that doesn't mean /dev/hda is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[Main] libmondo-devices.c->am_I_in_disaster_recovery_mode#351: Is this a ramdisk? result = 0
running: rm -Rf /tmp/changed.files* > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
Checking sanity of your Linux distribution
	[Main] libmondo-tools.c->some_basic_system_sanity_checks#1100: Free space on given partition = 9431 MB
running: cat /proc/devices | grep ramdisk > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
1 ramdisk
--------------------------------end of output------------------------------
...ran just fine. :-)
running: mount | grep -w vfat | grep -v /dev/fd | grep -v nexdisk > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
/dev/hda5 on /windows type vfat (rw,umask=000)
--------------------------------end of output------------------------------
...ran just fine. :-)
I think you have a Windows 9x partition.
			[Main] libmondo-files.c->find_home_of_exe#423: find_home_of_exe () --- Found ms-sys at /usr/bin/ms-sys
			[Main] libmondo-files.c->find_home_of_exe#423: find_home_of_exe () --- Found cmp at /usr/bin/cmp
	[Main] libmondo-tools.c->some_basic_system_sanity_checks#1193: Directory /etc/modprobe.d found. mindi will use its contents.
running: mindi -V > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
mindi v1.04
--------------------------------end of output------------------------------
...ran just fine. :-)
running: fdisk -l | grep -i raid > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=256
Done.
		[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#1798: media type = default
	[Main] libmondo-devices.c->sensibly_set_tmpdir_and_scratchdir#2288: bkpinfo->tmpdir is being set to /.dev/tmp.mondo.19213
	[Main] libmondo-devices.c->sensibly_set_tmpdir_and_scratchdir#2291: bkpinfo->scratchdir is being set to /.dev/mondo.scratch.6212
 
	[Main] libmondo-devices.c->find_dvd_device#1096: I cannot find DVD
[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#1840: Setting to DVD defaults
[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#1873: bkpinfo->media_device = /dev/cdrom
[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#1876: bkpinfo->media_device = /dev/cdrom
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#1881: DVD device found at /dev/cdrom
	[Main] libmondo-devices.c->which_boot_loader#2504: list_drives_cmd = fdisk -l 2>/dev/null | grep "/dev/.*:" | tr -s ':' ' ' | tr -s ' ' '
' | grep /dev/; echo /dev/hda
	[Main] libmondo-devices.c->which_boot_loader#2517: looking at drive /dev/hda's MBR
	[Main] libmondo-devices.c->which_boot_loader#2532: 1 grubs and 0 lilos

	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2144: isodir = /root/images/mondo
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2145: nfs_mount = ''
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2148: media device = /dev/cdrom
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2149: media size = 4380
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2150: media type = default
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2151: compression = 4
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2152: include_paths = '/'
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2153: exclude_paths = '/windows'
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2154: scratchdir = '/.dev/mondo.scratch.6212'
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2155: tmpdir = '/.dev/tmp.mondo.19213'
	[Main] libmondo-devices.c->interactively_obtain_media_parameters_from_user#2156: boot_device = '/dev/hda' (loader=G)
[Main] libmondo-tools.c->post_param_configuration#627: Foo
	[Main] libmondo-tools.c->post_param_configuration#671: Tmpfs mounted OK - 250 MB
			[Main] libmondo-files.c->find_home_of_exe#423: find_home_of_exe () --- Found growisofs at /usr/bin/growisofs
[Main] newt-specific.c->fatal_error#373: Fatal error received - 'Manual CD tray + DVD not supported yet.'
		[Main] newt-specific.c->fatal_error#394: OK, I think I'm the main PID.
	[Main] newt-specific.c->fatal_error#403: I'm going to do some cleaning up now.
			[Main] newt-specific.c->fatal_error#404: killall mindi 2> /dev/null
running: kill `ps wax | grep "/mondo/do-not" | awk '{print $1;}' | grep -vx "\?"` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=15
running: kill `ps wax | grep "tmp.mondo" | awk '{print $1;}' | grep -vx "\?"` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=15
running: kill `ps wax | grep "partimagehack" | awk '{print $1;}' | grep -vx "\?"` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=15
-------FATAL ERROR---------
Manual CD tray + DVD not supported yet.
Please DON'T contact the mailing list. Try the SNAPSHOTS.
	[Main] libmondo-files.c->register_pid#815: Unregistering PID
	[Main] libmondo-files.c->register_pid#815: Unregistering PID
	[Main] libmondo-files.c->register_pid#816: Error unregistering PID
running: umount /mnt/cdrom > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not mounted
--------------------------------end of output------------------------------
...ran with res=256
running: rm -Rf /mondo.scratch.* /tmp.mondo.* > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
running: rm -Rf /.dev/tmp.mondo.19213 /.dev/mondo.scratch.6212 > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
[Main] newt-specific.c->finish#496: Calling newtSuspend()
	[Main] libmondo-tools.c->do_libmondo_global_strings_thing#1598: libmondo-tools.c, do_libmondo_global_strings_thing, 1598: Freeing globals
```I can't figure out what this dilly-o is, can someone please help me?

Thanx in advance,
TM

---

### Post by piglet_74 on 2006-03-01
I had a similar problem.  I found the question in graphical mode to be missleading.  I think it asked if the system is a laptop or has burnproofing or some such.  I said yes, because I have burnproof.  Well actually it seem it wants to know if it's a laptop because it doesn't like manual trays.  So now I just say no and it continues on.  The problem I have now is the DVD boot to a command line and want's a floppy disk but it never made one, heck the machine doesn't even have one.  Why it would boot the dvd rom that has the images but not restore is beyond me.  Any takers?

BTW I'm running 5.10 with mondo and mindi from the desknow website I think.

---

### Post by bullpost on 2006-09-14
Just wanted to say this worked fine for ubuntu 6.06 Dapper drake.
Thanks for the info.

:)

---

