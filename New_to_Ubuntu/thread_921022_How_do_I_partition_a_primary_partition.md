---
title: "How do I partition a primary partition"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Brookeorama on 2008-09-15
Windows every time, stabs me right in the back. 
Hate that I'm doing it, but need help to do so. 
Thanks!

---

### Post by whizbaby on 2008-09-15
If you absolutely need it why not try virtualbox? Howtos on forum.
Basically you install windoze on a virtual drive in a virtual computer, so no need to repartition anything, and if you dont need to play the latest games or use 3D acceleration then it should be ok.

---

### Post by Morpheun on 2008-09-15
depends how you setup your partitions run
```
df -h
```
and paste the output.

After that the answer is probably just backing up your data and partitioning from a live cd. Also, before installing windows have you tried virtualbox, wine, etc?

---

### Post by Brookeorama on 2008-09-15
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  9.9G  206G   5% /
varrun                474M  108K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   60K  474M   1% /dev
devshm                474M   12K  474M   1% /dev/shm
lrm                   474M   39M  435M   9% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      227G  9.9G  206G   5% /home/brooke/.gvfs

---

### Post by whizbaby on 2008-09-15
Aaaah gotcha you wanna play games :p

---

### Post by Brookeorama on 2008-09-15
So with teh virtual box, which i am unfimilar with.. Do I need to buy Winblow$ or is it a 'shareware' verison... 
I am a n00b to virtual box. 
Also- Can I install programs?? And how much space does it give me to use?? 
I need like 100gb at the LEAST. 
Thanks agian you guys!!

---

### Post by Brookeorama on 2008-09-15
Nope, i actually dont. 
I have to use some programming softwear for school.. 
No games here.

---

### Post by compnut41 on 2008-09-15
If you have a live CD (which If you don't I seriously suggest you get one it will be your best friend) you can use the partition editor under the system menu. Just shrink the Ubuntu partition where there is free space, and be sure that the new free space is unallocated. You also may have to right click on one of the keyring icons and choose swap-off. Good Luck, and be sure to back everything up just in case.

---

### Post by Brookeorama on 2008-09-15
Huh. I don't get it. I dont have a live cd... 
And having one wont re write my exsisting OS?? 

____Scary!

---

### Post by whizbaby on 2008-09-15
> **Brookeorama said:**
> So with teh virtual box, which i am unfimilar with.. Do I need to buy Winblow$ or is it a 'shareware' verison... 
I thought you got a windows cd...you will need one anyways.
> 
I am a n00b to virtual box. 
Also- Can I install programs?? And how much space does it give me to use?? 
I need like 100gb at the LEAST. 
Thanks agian you guys!!
A virtual machine has a virtual harddrive of which you can specify the size when you create it. You can specify the amount of RAM and the CPU speed too (of course not higher than what you have as real hardware). Ok, when you boot that virtual machine (the real machine doesnt boot then) you can insert a cd in it (connect the virtual cd to the real one in vbox) and start that cd, e.g. a winXP installer. Then winXP would be installed on the virtual drive and you can use it as it were a real computer, turn on, turn off, reboot, go to the internet, install software, run software, whatever.
It has a nice graphical interface which is rather intuitive. If you want ill point you a howto.

---

### Post by Brookeorama on 2008-09-15
> **Brookeorama said:**
> Huh. I don't get it. I dont have a live cd... 
And having one wont re write my exsisting OS?? 

____Scary!

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_8Z5BHU toc = (null)
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum output set (IMAGE) image = /tmp/brasero_tmp_214BHU toc = (null)
BraseroMd5sum called brasero_job_get_session_output_size
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_set_current_action
BraseroMd5sum called brasero_job_start_progress
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum d41d8cd98f00b204e9800998ecf8427e ((null) before)
BraseroMd5sum finished track successfully
BraseroMd5sum stopping
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/scd0
	gracetime=0
	speed=20
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/brooke/Desktop/ubuntu-8.04.1-desktop-amd64.iso
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
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
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'TSSTcorp'
BraseroWodim stdout: Identification : 'CD/DVDW TS-H652L'
BraseroWodim stdout: Revision       : '0603'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1582592 = 1545 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 2823 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data     0 MB        
BraseroWodim stdout: Total size:        0 MB (00:04.00) = 300 sectors
BraseroWodim stdout: Lout start:        1 MB (00:06/00) = 300 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 4
BraseroWodim stdout:   Is unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
BraseroWodim stdout:   ATIP start of lead in:  -11634 (97:26/66)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 3
BraseroWodim stdout: Manufacturer: CMC Magnetics Corporation
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 359549
BraseroWodim stdout: Starting to write CD/DVD at speed  16.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in  0 seconds. Operation starts.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 MB written.
BraseroWodim stdout: Track 01: writing 600 KB of pad data.
BraseroWodim stdout: Track 01: Total bytes read/written: 0/614400 (300 sectors).
BraseroWodim stdout: Writing  time:    9.839s
BraseroWodim stdout: Average write speed   6.1x.
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:   29.130s
BraseroWodim stderr: wodim: fifo had 1 puts and 1 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 0
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_action
BraseroWodim finished successfully session
BraseroWodim stopping
BraseroWodim got killed
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum creating input
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum Starting checksuming (live) (size = 610304)
BraseroMd5sum called brasero_job_set_current_action
BraseroMd5sum called brasero_job_start_progress
BraseroMd5sum starting md5 generation live
BraseroMd5sum called brasero_job_set_nonblocking
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_action
BraseroReadom linked to BraseroMd5sum
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_fd_out
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom reading 1 from sector 0 to 298
BraseroReadom got varg:
	readom
	dev=/dev/scd0
	-nocorr
	-noerror
	-sectors=0-298
	-f=-
BraseroReadom launching command
BraseroReadom stderr: Read  speed:  4234 kB/s (CD  24x, DVD  3x).
BraseroReadom stderr: Write speed:  5645 kB/s (CD  32x, DVD  4x).
BraseroReadom stderr: Capacity: 300 Blocks = 600 kBytes = 0 MBytes = 0 prMB
BraseroReadom called brasero_job_set_current_action
BraseroReadom stderr: Sectorsize: 2048 Bytes
BraseroReadom stderr: Copy from SCSI (5,0,0) disk to file '-'
BraseroReadom stderr: end:       298
BraseroReadom stderr: addr:        0 cnt: 64

BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_written_track
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroReadom stderr: addr:       64 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_written_track
BraseroReadom called brasero_job_start_progress
BraseroReadom stderr: addr:      128 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_written_track
BraseroReadom called brasero_job_start_progress
BraseroReadom stderr: addr:      192 cnt: 64
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_written_track
BraseroReadom called brasero_job_start_progress
BraseroMd5sum called brasero_job_set_progress
BraseroReadom stderr: addr:      256 cnt: 42

BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_written_track
BraseroReadom called brasero_job_start_progress
BraseroReadom stderr: addr:      298
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_set_written_track
BraseroReadom called brasero_job_start_progress
BraseroReadom stderr: Time total: 1.381sec
BraseroReadom stderr: Read 596.00 kB at 431.6 kB/sec.
BraseroReadom stderr: HUP
BraseroMd5sum called brasero_job_set_progress
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom finished track successfully
BraseroReadom got killed
BraseroReadom disconnecting BraseroReadom from BraseroMd5sum
BraseroReadom deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum (type = 1) 151b265cc75738290f2c40d03a38ee0b (d41d8cd98f00b204e9800998ecf8427e before)
BraseroMd5sum called brasero_job_error
BraseroMd5sum finished with an error
BraseroMd5sum asked to stop because of an error
	error		= 22
	message	= "some files may be corrupted on the disc"
BraseroMd5sum stopping
BraseroMd5sum closing connection for BraseroMd5sum
Session error : some files may be corrupted on the disc (brasero_burn_record burn.c:2270)

[B]

Errors?? What do I do now?? [/B]

---

### Post by whizbaby on 2008-09-15
By the way - which programming language is it? Perhaps theres an equivalent software in linux?

---

### Post by pbotros1234 on 2008-09-15
Run an Ubuntu LiveCD, or you can get any LiveCD that has GParted, a really useful GUI that lets you partition easily. Partitioning can be done through the command line, but thats harder. Oh and it has to be done from a LiveCD, because the hard drive has to be unmounted in order to partition it.

There also is a GParted LiveCD, it's like 50 MB if you want to burn it and use that, pretty lightweight.

Anyway, when you're on the live cd, open up GParted from a menu, or just do "sudo gparted" in a terminal. Make sure your partition is unmounted, and then right click on it and choose the "Resize/Move" option. Move the slider so that you have however much space you want for Windows and your Ubuntu.
Once you resive it, you should have one partition and then the rest unallocated space. Click on it, and click "New" to make a new partition. Make all of your unallocated into another Primary Partition, and make sure to make it NTFS formatted. Click apply, and hopefully nothing messes up :) Then you can install windows on to the NTFS partition.

Oh, and the Windows install CD might have a guided partitioner itself, so maybe you can avoid all this :/


Oh and I wouldn't use Brasero to burn it. Make sure you're burning a .iso file, and on Ubuntu you can just right-click on the ISO and click "write to disc". Make sure you're writing at the lowest possible speed, to lower the chance of any errors.

---

### Post by Brookeorama on 2008-09-15
Ok THAT was helpful. 
Seriosuly. 
Im having problems burning the ISO image.. 
Is Brasero a bad program?? 
* I dont trust a windows partioner. at all. wont do it and refuse to try (for now ;/)

---

### Post by Brookeorama on 2008-09-15
alright so I i able to load the iso image on a  disk, brasero said the cd was a good copy, no errors. 
-I inserted the cd
-restarted
-got a blinking cursor that did nothing?? 
WEIRD!!
Apparently that isnt wanting to work either. 
what the heck?!!?

---

### Post by sudo_chop on 2008-09-15
> **whizbaby said:**
> By the way - which programming language is it? Perhaps theres an equivalent software in linux?
 
+1
 
We want to know why you are resorting to MS for something programming related. That seems a little backwards...

---

### Post by compnut41 on 2008-09-15
Then I am no help to you

---

### Post by Brookeorama on 2008-09-15
visual studio

---

### Post by sudo_chop on 2008-09-16
Sorry for the inactivity on this... whats the status?
 
If you are still having trouble with the live CD, maybe try checking the .iso against the md5 checksum
 
cd to the directory containing the .iso and run this command
 
```
md5sum ubuntu-8.04.1-desktop-amd64.iso
```
 
it should print a single line containing this number: b78ef719e3361e726b89bab78c526ad0
 
if it doesn't then you need to download the disk image again.
 
Good luck
 
-sudo chop

---

### Post by whizbaby on 2008-09-17
> **Brookeorama said:**
> visual studio
Is that a programming language? Or is it a platform for C#?
Ffs someone kill your teacher plz

---

