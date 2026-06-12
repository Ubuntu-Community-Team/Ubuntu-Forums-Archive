---
title: "Save .odt file to CD"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by geomcd1949 on 2012-06-12
New Ubuntu user. I'd like to create a document in LibreOffice and save it to a CD in .odt format. Would appreciate instructions on how to do this. Thanks. ~George

---

### Post by mikewhatever on 2012-06-12
1. Create a document and save it to dosk first.

2. Use a CD burning program to burn the document (in fact, any file) to the CD. 

Ubuntu has **Brasero** pre-installed.

---

### Post by geomcd1949 on 2012-06-12
Thanks Mike. No joy. Brasero reports the following error(s). Any suggestions?

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_IH4SFW.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
    -input-charset
    utf8
    -r
    -J
    -graft-points
    -path-list
    /tmp/brasero_tmp_KN8RFW
    -exclude-list
    /tmp/brasero_tmp_KO8RFW
    -V
    Data disc (12 Jun 12)
    -A
    Brasero-3.4.1
    -sysid
    LINUX
    -quiet
    -print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 199
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage Finished track successfully
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage stopping
BraseroGenisoimage called brasero_job_get_done_tracks
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_input_type
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 0
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_output_size_for_current_track
BraseroLibburn called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroLibburn
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
    -input-charset
    utf8
    -r
    -J
    -graft-points
    -path-list
    /tmp/brasero_tmp_EFMQFW
    -exclude-list
    /tmp/brasero_tmp_PNMQFW
    -V
    Data disc (12 Jun 12)
    -A
    Brasero-3.4.1
    -sysid
    LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_fd_in
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: Total translation table size: 0
BraseroGenisoimage stderr: Total rockridge attributes bytes: 340
BraseroGenisoimage stderr: Total directory bytes: 0
BraseroGenisoimage stderr: Path table size(bytes): 10
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2295103 ,  r=22160 ,  w=22160
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 1Bh , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD+R pre-track 01 : get_nwa(0), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [4 3E 02] Timeout on logical unit
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(0,16): [4 3E 02] Timeout on logical unit
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
    error        = 1
    message    = "SCSI error on write(0,16): [4 3E 02] Timeout on logical unit"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroLibburn
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroLibburn stopping
BraseroLibburn closing connection for BraseroLibburn
Session error : SCSI error on write(0,16): [4 3E 02] Timeout on logical unit (brasero_burn_record brasero-burn.c:2856)

---

### Post by mikewhatever on 2012-06-12
The only thing I can suggest is an alternative to CD starage. I don't know why you'd like to have documents on a CD, but wouldn't it be more convenient to use something like Ubuntu One?

Ubuntu One is a cloud storage service that gives you 5GB of storage space for free.

---

### Post by Cheesehead on 2012-06-12
Are you able to do other activities with your CD drive? Listen to a CD? Read a file? Boot a LiveCD? Or is it broken for everything else?

If it usually works, are there any applications the it works with (or doesn't work with) reliably?

---

### Post by geomcd1949 on 2012-06-16
Thanks, guys! I would like to save book chapters in .odt format to disc. It's a task easily and simply done with Windows, and should be just as easy with Ubuntu. I read the Reviews of Brasero on the Ubuntu Software Center. Seems most folks don't like it for a variety of reasons, and some suggest K3b as an alternative to it. I tried K3b with the same results.

 I use Ubuntu One for other things. 

My CD drive works fine, other than not saving files to disc. Plays audio and video. It's what I installed Ubuntu 12.04 with. It just won't save files to disc.

---

### Post by afixane on 2012-06-16
> **geomcd1949 said:**
> Thanks, guys! I would like to save book chapters in .odt format to disc. It's a task easily and simply done with Windows, and should be just as easy with Ubuntu. I read the Reviews of Brasero on the Ubuntu Software Center. Seems most folks don't like it for a variety of reasons, and some suggest K3b as an alternative to it. I tried K3b with the same results.

 I use Ubuntu One for other things. 

My CD drive works fine, other than not saving files to disc. Plays audio and video. It's what I installed Ubuntu 12.04 with. It just won't save files to disc.

K3b is for KDE. If you install it, K3b will install some of KDE library. Why not Xfburn instead?

---

### Post by Financing Dragons on 2012-06-16
In k3b did you burn it as a data disk?

---

### Post by Peripheral Visionary on 2012-06-16
I use Xfburn, but I'm sure K3B offers the same choice between burning the disk as an **image**, or an **audio** CD, or a **Data** CD. Be absolutely certain you have chosen to save the file as data; that the disk in the drive is really a blank CD rather than a DVD or a disk with stuff already on it, and be sure your CD burner is in working order.

I've made all three of the above silly mistakes, from using a broken burner to trying to burn pictures as an "image." Check all three of those things first, and try a different burner (K3B or Xfburn). Brasero makes a lot of coasters for a lot of users, lol.

---

### Post by geomcd1949 on 2012-06-16
Tried Xfburn. It works perfectly. Thanks!

---

### Post by Peripheral Visionary on 2012-06-16
> **geomcd1949 said:**
> Tried Xfburn. It works perfectly. Thanks!

Yay! I like Xfburn for it's simplicity as well as it's reliability.  Great choice for a default burner on hard drives with limited space for all the KDE libraries and stuff that K3B pulls in when you install it on Ubu or Xubu.

---

