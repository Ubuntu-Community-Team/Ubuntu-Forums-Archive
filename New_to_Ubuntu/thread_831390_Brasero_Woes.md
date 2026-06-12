---
title: "Brasero Woes"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Ahunt on 2008-06-16
I am running Ubuntu 8.04 and having problems using the Brasero CD burning utility for the first time. 

I have checked a couple of other forum threads that seem to describe similar problems with Brasero, but no one has posted any solutions.

This PC has a CD writer drive that was successfully used on Windows just two days ago, and has just worked fine with the Gnome CD/DVD Creator tool so I know that the problem is not hardware. The PC just had Ubuntu installed on it, replacing Windows XP. I have not been able to identify the type of CD burner, if that is important, as the hardware listing tool that was present in Ubuntu 7.4 and 7.10 seems to have been removed in 8.4.

Problem description: I tried doing a multi-session write to a new CD-RW. I wrote one folder with three files to the CD-RW successfully using Brasero and then attempted to write a second folder. It appeared to work correctly but when the CD was reinserted returned the error:

Cannot Mount Volume
Invalid mount option while attempting to mount the volume...

I presume this means it ruined the CD-RW.

I tried adding a folder with three files to an exiting CD-RW that was previously compiled on Windows XP. After importing the existing files into Brasero the new folder could be added to the list without a problem. When "burn" is selected it returned the following error:

Error While Burning
The image can't be created

and the file says:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile deactivating
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_set_current_action
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_add_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile finished track successfully
BraseroMd5sumFile stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum creating input
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage called brasero_job_start_progress
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_PSLLCU
	-exclude-list
	/tmp/brasero_tmp_UULLCU
	-quiet
	-print-size
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 1549
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/scd0
	gracetime=0
	speed=11
	driveropts=burnfree
	-multi
	fs=4m
	tsize=1549s
	-data
	-nopad
	-
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum linked to BraseroWodim
BraseroMd5sum creating input
BraseroMd5sum called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroMd5sum
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_last_session_address
BraseroGenisoimage called brasero_job_get_next_writable_address
BraseroGenisoimage called brasero_job_get_device
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_0JQWCU
	-exclude-list
	/tmp/brasero_tmp_REQWCU
	-V
	Photos working
	-A
	Brasero-0.7.1
	-sysid
	LINUX
	-C
	258928,283220
	-M
	/dev/scd0
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum starting md5 generation live
BraseroMd5sum called brasero_job_set_nonblocking
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Asuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.6
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroGenisoimage stderr: NO Rock Ridge present
BraseroGenisoimage stderr: Disabling Rock Ridge / XA / AA
BraseroGenisoimage stderr: Warning: Neither Rock Ridge (-R) nor TRANS.TBL (-T) 
BraseroGenisoimage stderr: name translations were found on previous session.
BraseroGenisoimage stderr: ISO-9660 file names have been used instead.
BraseroGenisoimage stderr: Using HENRY000.JPG;1 for  Ruth's Roses 15 June 2008/HenryKelsey03.JPG (HenryKelsey02.JPG)
BraseroGenisoimage stderr: Using HENRY001.JPG;1 for  Ruth's Roses 15 June 2008/HenryKelsey02.JPG (HenryKelsey01.JPG)
BraseroGenisoimage stderr: Using FARME000.JPG;1 for  /FARMER_S/FARMER~1.JPG (FARMER~1.JPG)
BraseroGenisoimage stderr: Using QUEBE000.JPG;1 for  /HIKETOQU/QUEBEC~2.JPG (QUEBEC~2.JPG)
BraseroGenisoimage stderr: Using QUEBE001.JPG;1 for  /HIKETOQU/QUEBEC~1.JPG (QUEBEC~1.JPG)
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/HIKETOQU/QUEBEC~1.JPG' and '/HIKETOQU/QUEBEC~1.JPG' have the same Rock Ridge name 'QUEBEC~1.JPG'.
BraseroGenisoimage stderr: Unable to sort directory /HIKETOQU
BraseroGenisoimage called brasero_job_error
BraseroGenisoimage finished with an error
BraseroGenisoimage asked to stop because of an error
	error		= 1
	message	= "the image can't be created"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroMd5sum
BraseroMd5sum stopping
BraseroMd5sum disconnecting BraseroMd5sum from BraseroWodim
BraseroMd5sum closing connection for BraseroMd5sum
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : the image can't be created (brasero_burn_record burn.c:2270)

I have tried duplicating the burn by using the Gnome CD/DVD Creator tool. It won't do multi-sessions, so I tried replacing the existing files on the CD-RW with a duplicate set, plus an extra folder as a test. I erased the disc and burned a new set. It worked fine and resulted in the files all being there on the CD-RW. This proves that the hardware is not the problem, but that Brasero is.

Can anyone provide some information on what is not working with Brasero?

---

### Post by rainwalker on 2008-06-17
Did you make sure you enabled the option to leave the disc open to write more data in the future?

---

### Post by simontaylor on 2008-06-17
hi Ahunt,

here's your problem > Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'

I'm onto my first dozen useless shiny plastic discs and am thinking of introducing them as an alternative coin of the realm (replacing the coffee references?). I've experienced the same problem with Gnomebaker & Brasero & K3b & Serpentine & Gnome & every other burner I've tried. 

Thought it was a permission issue, or something to do with cdrecord being replaced by cdrdao in Hardy, but the literature on Launchpad, where it's listed as bug 149076, points to a kernel problem with wodim. Bug seems to occur where there's been a recent update. (I updated to 8.04 ... suddenly no K3b!)Anyway, I have another thread up at the moment:  K3b cdrecord vs. cdrdao? conflict? (Brasero fails too) ...

I will subscribe to this thread and let you know what gives, if anything, when it does. But I suggest you check out the Launchpad material on said bug. Not much help I'm afraid. Then, same boat.

best,
simon

---

### Post by Ahunt on 2008-06-17
Thanks you both for your replies!

Rainwalker: yes!

Simon: Your explanation makes sense. My next strategy after posting here was to file a bug report, but since it is already done, I suppose the best option is to wait for action from the developers.

In my case this problem is not serious - the Gnone CD/DVD Creator works fine, it just cannot do multi-session writing, meaning adding new files to existing CD-RWs or CD-Rs. With the RWs I can work around this by just reloading all the files onto the CD. With the Rs I just cache the files until I have enough to totally fill a CD and then write it once. It is more work but doable.

I look forward to your post back here when you hear of a fix. In the meantime I only wrecked one CD-RW and I won't waste anymore!

---

### Post by simontaylor on 2008-06-17
Cool man

check out what alienexplorers is doing over here with > combined_mode=ide 

messing with the kernel ... he's gonna be jealous of his 100 secret herbs and spices!

> post #15 K3b cdrecord vs. cdrdao? conflict? (Brasero fails too)

Like poor old K. sang, I should be so lucky ...

simon

---

### Post by Ahunt on 2008-06-17
Simon:

Thanks for the reference to that thread. I wasn't clear from your post on that thread, did that work for you or not?

I am not especially concerned about this snag as the Gnome CD burning application still works fine on both my Ubuntu PCs, it just doesn't multisession.

There was a new kernel download today - wonder if that helped or not?

---

### Post by simontaylor on 2008-06-17
no joy so far with line added to grub file. 

will keep looking.

best,
simon

---

### Post by cariboo on 2008-06-17
To identify what type of CD-ROm drive you have in a terminal type:

```
wodim -scanbus
```

I don't know what you can do with the info but at least you'll know what make of drive it is.

Jim

---

### Post by Ahunt on 2008-06-18
> **cariboo907 said:**
> To identify what type of CD-ROm drive you have in a terminal type:

```
wodim -scanbus
```

I don't know what you can do with the info but at least you'll know what make of drive it is.

Jim

Jim: That was helpful!! It tells me:

```
'MITSUMI ' 'CR-48X9TE '1.0C' Removable CD-ROM
```

---

