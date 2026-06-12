---
title: "K3b cdrecord vs. cdrdao? conflict? (Brasero fails too)"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by simontaylor on 2008-06-14
I've trawled and tried bits and pieces of various solves that some have found OVER THE YEARS for this seemingly simple problem: K3b spits out the following when I try and burn an audio CD:

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-18-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1764 KB/s
pregap1: -1
Track 01: audio  314 MB (31:11.05) no preemp swab copy
Track 02: audio  189 MB (18:47.44) no preemp swab copy
Track 03: audio   73 MB (07:15.98) no preemp swab copy
Track 04: audio  168 MB (16:41.25) no preemp swab copy
Total size:      746 MB (73:55.73) = 332680 sectors
Lout start:      746 MB (73:57/55) = 332680 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 27166
Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  314 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   13.712s
Average write speed 882.3x.
Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 44 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x44 Qual 0x00 (internal target failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.210s timeout 200s
Trouble flushing the cache
Fixating time:   16.222s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=10 -dao driveropts=burnfree -eject -useinfo -audio /tmp/kde-simon/k3b_audio_0_01.inf /tmp/kde-simon/k3b_audio_0_02.inf /tmp/kde-simon/k3b_audio_0_03.inf /tmp/kde-simon/k3b_audio_0_04.inf 

Apologies for the length of it but here's what Brasero made of the SAME JOB:

> Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_MNZMCU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_4CYMCU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_PVENCU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_LPENCU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode deactivating
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_BNDNCU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 1871053333333 / bytes = 0 330053808
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/simon/Glenn Branca/Indeterminate Activity of Resultant Masses/01 - Indeterminate Activity of Resultant Masses.ogg to /tmp/brasero_tmp_BNDNCU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 330053808 bytes (= 330053808 ns)
=> padding 0 bytes
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_1H8YCU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 1127440000000 / bytes = 0 198880416
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/simon/Glenn Branca/Indeterminate Activity of Resultant Masses/02 - So That Each Person Is in Charge of Himself.ogg to /tmp/brasero_tmp_1H8YCU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 198880416 bytes (= 198880416 ns)
=> padding 0 bytes
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_83S0CU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 435986666666 / bytes = 0 76908048
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/simon/Glenn Branca/Indeterminate Activity of Resultant Masses/03 - Harmonic Series Chords.ogg to /tmp/brasero_tmp_83S0CU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 76908048 bytes (= 76908048 ns)
=> padding 0 bytes
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_WG26CU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 1001253333333 / bytes = 0 176621088
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_current_action
BraseroTranscode called brasero_job_start_progress
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode start decoding /home/simon/musix/Bang on a Can All-Stars/Renegade Heaven/04 - Movement Within.ogg to /tmp/brasero_tmp_WG26CU.cdr
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_set_written_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode wrote 176621088 bytes (= 176621088 ns)
=> padding 0 bytes
BraseroTranscode called brasero_job_get_audio_output
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_output_type
BraseroTranscode called brasero_job_add_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode finished track successfully
BraseroTranscode stopping
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
BraseroWodim called brasero_job_get_audio_title
BraseroWodim called brasero_job_get_tracks
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_BNDNCU.inf)
BraseroWodim got track length 1871053333333 140329
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_1H8YCU.inf)
BraseroWodim got track length 1127440000000 84558
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_83S0CU.inf)
BraseroWodim got track length 435986666666 32699
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_WG26CU.inf)
BraseroWodim got track length 1001253333333 75094
BraseroWodim called brasero_job_get_tracks
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/scd0
	gracetime=0
	speed=47
	driveropts=burnfree
	-dao
	fs=16m
	-audio
	-swab
	-pad
	-useinfo
	-text
	/tmp/brasero_tmp_BNDNCU.cdr
	/tmp/brasero_tmp_1H8YCU.cdr
	/tmp/brasero_tmp_83S0CU.cdr
	/tmp/brasero_tmp_WG26CU.cdr
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
BraseroWodim stdout: TOC Type: 0 = CD-DA
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'PIONEER '
BraseroWodim stdout: Identification : 'DVD-RW  DVR-111D'
BraseroWodim stdout: Revision       : '1.06'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1267712 = 1238 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 7056 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: pregap1: -1
BraseroWodim stdout: Track 01: audio  314 MB (31:11.05) no preemp copy
BraseroWodim stdout: Track 02: audio  189 MB (18:47.44) no preemp copy
BraseroWodim stdout: Track 03: audio   73 MB (07:15.98) no preemp copy
BraseroWodim stdout: Track 04: audio  168 MB (16:41.25) no preemp copy
BraseroWodim stdout: Total size:      746 MB (73:55.73) = 332680 sectors
BraseroWodim stdout: Lout start:      746 MB (73:57/55) = 332680 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
BraseroWodim stdout:   ATIP start of lead in:  -11634 (97:26/66)
BraseroWodim stdout:   ATIP start of lead out: 359846 (79:59/71)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 3
BraseroWodim stdout: Manufacturer: CMC Magnetics Corporation
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 27166
BraseroWodim stdout: Starting to write CD/DVD at speed  40.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in  0 seconds. Operation starts.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: SAO startsec: -11634
BraseroWodim stdout: Writing lead-in...
BraseroWodim stdout: Lead-in write time:   29.581s
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 00 00 00 00 1B 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x4 Hardware Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.006s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 1
	message	= "a write error occured which was likely due to overburning the disc"
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
Session error : a write error occured which was likely due to overburning the disc (brasero_burn_record burn.c:2270)

I'm onto a dozen useless and expensive shiny discs so far: ear-rings anyone? Lee Scratch need a suit?

PLEASE HELP!

Yours, 

Simon Taylor

---

### Post by cariboo on 2008-06-14
Have you tried burning at a slower speed something like 8X? A lot of times the media won't burn a good copy unless it is done at a slower speed than it is supposedly rated at.

Jim

---

### Post by simontaylor on 2008-06-15
Hi cariboo907,
K3b and my burning machine aren't talking. It's not a question of a good copy. Yes, I can slow the process of rejection down; it remains a painful and wasteful one.

thanks Jim,
best,

Simon

---

### Post by alienexplorers on 2008-06-16
List a copy of your /etc/fstab file here.

Brassero is a piece of junk.  Never got it to burn anything yet.  I use just gnomebaker.

---

### Post by simontaylor on 2008-06-16
We meet again. Sleep was not as successful as it might have been. Waste of precious time, even. Back on it!

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=5d2cb925-f4e0-4630-b3a2-d818e5ef7fbf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

A friend who does use Brasero suggested system>admin>software sources - check multiverse and universe boxes. This I did and received this interesting account when the repositories were contacted automatically:

Could not download all repository indexes

> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

Again, I don't know what to make of it. 

best,
simon

---

### Post by alienexplorers on 2008-06-16
Try changing in your /etc/fstab /dev/hdc to:

> /dev/hdc       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by simontaylor on 2008-06-17
Hi there, back onto the problem. Report follows from K3b, tested after changing /dev/hdc as you suggested, alienexplorers, clearly without success:

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1764 KB/s
pregap1: -1
Track 01: audio  314 MB (31:11.05) no preemp swab copy
Track 02: audio  189 MB (18:47.44) no preemp swab copy
Track 03: audio   73 MB (07:15.98) no preemp swab copy
Track 04: audio  168 MB (16:41.25) no preemp swab copy
Total size:      746 MB (73:55.73) = 332680 sectors
Lout start:      746 MB (73:57/55) = 332680 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 27166
Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
Track 01:    0 of  314 MB written.
write track data: error after 0 bytes
Writing  time:   13.794s
Average write speed 883.7x.
Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 44 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x44 Qual 0x00 (internal target failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.195s timeout 200s
Trouble flushing the cache
Fixating time:   16.207s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=10 -dao driveropts=burnfree -eject -useinfo -audio /tmp/kde-simon/k3b_audio_0_01.inf /tmp/kde-simon/k3b_audio_0_02.inf /tmp/kde-simon/k3b_audio_0_03.inf /tmp/kde-simon/k3b_audio_0_04.inf 

cdrecord, when in synaptic, appears to have been replaced by cdrdao. K3b doesn't recognise this? Or is it a wodim deal? (well, obviously, no deal.)

Is it worth busting another shiny disc on a gnomebaker trial?

simon

---

### Post by simontaylor on 2008-06-17
hi again,
well, against my better judgement I threw more plastic at the problem. Gnomebaker fails too: readout follows:
> wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 7056 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.079s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:   19.974s
Average write speed 839.1x.
Fixating...
Fixating time:    0.021s
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.014s timeout 480s
cmd finished after 0.014s timeout 480s
wodim: Cannot fixate disk.
wodim: fifo had 192 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.


So. Nil to the Gnomes. Which makes it NIL by CDROM!

But here it looks more clearly as if it is WODIM not dealing. And, how do you raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'?????????????????????????????!

Under Gnomebaker>Edit>Preferences>Advanced I find: > Additional *cdrecord* options, a tickable box with "Force" written on it and a drop menu with a single entry: WODIM

Wodim and cdrecord ... sounds like a partnership that went seriously wrong.

thoughts?

---

### Post by simontaylor on 2008-06-17
OK, so this is a confirmed bug: #149076 Launchpad, first reported on 2007-10-04  by  hendrikwout.

here's the link: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076")

And some observations thereon:

> Copying my post from bug #178808, which is probably a duplicate:

> OK, I tried the fixes mentioned at:
[http://linux-ata.org/faq,html#combined](http://linux-ata.org/faq,html#combined)

...

> Adding kernel parameters is not for the newbie,the problem exists elsewhere and should be fixed elsewhere. Adding the kernel paramenter should be viewed as a workaround, so the bug should probably not be closed, just re-pointed to wodim or wherever the bug actually lives.



> Same problem in 8.04. combined_mode=ide did the trick.

> I hope to see some progress on this issue soon as it seems to be a fairly common issue. There a lot of duplicate bugs out there describing basically the same thing "/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'" perhaps the description should be changed to something reflecting this? "I can't write a cd" is pretty generic and not particularly helpful for identifying this bug accurately.

Separate cases of the same bug relate to Kubuntu and Ubuntu, Feisty, Gutsy and Hardy.

Now, I don't understand the fixes mentioned, possibly because I am a newbie and ought not to be messing with the kernel?

The solution mentioned above is to go to libATA FAQ where we read:
     
> * Recommended (where BIOS permits): Change BIOS IDE mode from "legacy" or "combined" mode to "AHCI" (recommended), "RAID" or "native".

* Boot with the kernel commandline parameter "combined_mode=libata" or "combined_mode=ide" to allow the specified driver to claim all IDE ports.

* Disable libata (CONFIG_ATA) entirely, and enable CONFIG_BLK_DEV_IDE_SATA.

* (newer choice, with less field testing) Disable CONFIG_IDE, and permit libata to run all your IDE and SATA ports.


So can somebody please help me out?

simon

---

### Post by simontaylor on 2008-06-17
I had did a quick general forum search for:

> RLIMIT_MEMLOCK limits.scsidev: '/dev/hdc' 

Found 22 threads citing similar problems and none that I could see - which was of course the point of searching - listed solutions. 

I'd like to know if the COMBINED / libATA thing flies. But I don't know where to start. 

Curious, given how widespread the same bug appears to be, that there has been no generic fix offered. If I, as a complete tyro, can see a point of similarity across this group, someone else, with sufficient experience to do something about the problem, surely has. (Also amazing that so many problems date from uploading 8.04.) 

Please step forward if you can help!

best, expecting great things,

simon

---

### Post by alienexplorers on 2008-06-17
I added the following line to the end of my kernel line in /boot/grub/menu.lst:
> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
[COLOR="Red"]kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2eed7dda-3209-456c-8867-a36d3716088c ro acpi=force combined_mode=ide[/COLOR]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

---

### Post by alienexplorers on 2008-06-17
When ubuntu set up my fstab file it looked like this and I kept it that way and everything is working fine:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2eed7dda-3209-456c-8867-a36d3716088c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=e13115d5-3546-4367-a80f-8b87ac63ff10 /data           ext3    relatime        0       2
# /dev/sda2
UUID=64af1f59-71ab-4fc5-b463-092ab5fa4dea /home           ext3    relatime        0       2
# /dev/sda4
UUID=3664cc8d-e2ee-4a98-8249-c0d906c995a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Not that all of the devices start with "S" even though my entire system is ide.

---

### Post by simontaylor on 2008-06-17
that's really cool. Now, I need a bit of reassurance as to where this sits. So,if you'll forgive me, I've done it the nana way. Can you show me exactly where here:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bb50905b-4ffd-4a3e-8b41-71acdbef96e6 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bb50905b-4ffd-4a3e-8b41-71acdbef96e6 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bb50905b-4ffd-4a3e-8b41-71acdbef96e6 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bb50905b-4ffd-4a3e-8b41-71acdbef96e6 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

yep, I fear The Gloom of no GUI.

if it goes, fantastic work, alienexplorers,

simon

---

### Post by simontaylor on 2008-06-17
> **alienexplorers said:**
> When ubuntu set up my fstab file it looked like this and I kept it that way and everything is working fine:

Not that all of the devices start with "S" even though my entire system is ide.

I don't understand this. Over head. Explain? or will that ruin it?

simon

---

### Post by alienexplorers on 2008-06-17
Go into /boot/grub/menu list and enter the section in red after the quiet splash section of you version 19 kernel:

> title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro quiet splash [COLOR="Red"]combined_mode=ide[/COLOR]
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa ro single
initrd /boot/initrd.img-2.6.24-19-generic


---

### Post by alienexplorers on 2008-06-17
The "S" is normally used for SATA devices, but ubuntu set my system up using this format and well every thing is working fine even though my whole system is IDE.

---

### Post by simontaylor on 2008-06-17
Got it.

simon

---

### Post by simontaylor on 2008-06-17
hi alienexplorers,
sorry, that took a while, checking, double-checking. Added 
> 
combined_mode=ide

as per your direction.

fstab as follows:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=5d2cb925-f4e0-4630-b3a2-d818e5ef7fbf none            swap    sw              0       0

/dev/hdc 	/media/cdrom0 	udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

What was I doing? Looking at your fstab and wondering where the rest of mine was. We call it fstab envy.

Well, now. What do you think? Wouldn't want to go off half-fstabbed.

simon

PS checked again. Yep. That's all there is.

---

### Post by alienexplorers on 2008-06-17
Sorry for not being around for a while.  Was out grocery shopping.  Fstab looks good and adding that line to your grub file should help.  I tried burning a CD and it worked fine at 24x.  I use to be able to only burn at 2x or 4x.
Donald Saunders

P.S. - thanks for finding that information on LibATA FAQ.  Without that I would still be burning at 2x or 4x.

---

### Post by simontaylor on 2008-06-17
I don't believe it. K3b created my 13th useless shiny piece of plastic!

this is after adding line to grub file. 

debugging output follows:

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio  314 MB (31:11.05) no preemp swab copy
Track 02: audio  189 MB (18:47.44) no preemp swab copy
Track 03: audio   73 MB (07:15.98) no preemp swab copy
Track 04: audio  168 MB (16:41.25) no preemp swab copy
Total size:      746 MB (73:55.73) = 332680 sectors
Lout start:      746 MB (73:57/55) = 332680 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 27166
Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
Speed set to 1764 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  314 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   13.705s
Average write speed 883.2x.
Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 44 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x44 Qual 0x00 (internal target failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.180s timeout 200s
Trouble flushing the cache
Fixating time:   16.192s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=10 -dao driveropts=burnfree -eject -useinfo -audio /tmp/kde-simon/k3b_audio_0_01.inf /tmp/kde-simon/k3b_audio_0_02.inf /tmp/kde-simon/k3b_audio_0_03.inf /tmp/kde-simon/k3b_audio_0_04.inf 

same wodim bug / error: > /usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'

Question: if, once the process aborts, as it did a second ago, and the CD-R won't remount as audio, what's on them? 

I've tried to Gnomebaker re-blank a disc and same in K3b --- no go.

Hoping that a new day would bring a new deal. No luck.

simon

---

### Post by simontaylor on 2008-06-17
here's the link to the lit around cdrecord, for interest's sake: [http://cdrecord.berlios.de/old/private/linux-dist.html]("http://cdrecord.berlios.de/old/private/linux-dist.html")

Have found further dependencies for K3b at [http://freshmeat.net/projects/k3b/]("http://freshmeat.net/projects/k3b/")

List includes cdrtools - ... unavailable through synaptic. Have found latest (via cited link) version of cdrtools (itself, if you have a look at the lit, a version of cdrecord/or replacement thereof);

have extracted cdrtools in desktop to check it out. 

How do I install it? 

and if I need to name directory, how do I do that?

I'm figuring my problem with K3b is: 1) the bug -- combined ide should do something about in kernel;
2) dependencies relating to cdrecord;
3) checking I'm in the usr group and/or chowning (not sure how to do this... the research side is fine... it's the practical code stuff which confuses me.)

More help please,

yours

simon


simon

---

### Post by simontaylor on 2008-06-18
if it were a problem soley with dependencies, then I wouldn't be getting this output with Gnomebaker (which I tried out of desperation):

> wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 7056 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.089s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:   20.014s
Average write speed 840.7x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.011s timeout 480s
cmd finished after 0.011s timeout 480s
Fixating time:    0.017s
wodim: Cannot fixate disk.
wodim: fifo had 192 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

---

### Post by alienexplorers on 2008-06-18
Well I tried something new.  Instead of using combined_mode=ide, I have switched over to:
> combined_mode=libata
I found out that libata is part of the kernel and since so many new kernels have come out I am hoping that it has been fixed in the latest kernel version 19.
Donald

---

### Post by alienexplorers on 2008-06-18
Try reading over this page it has to do with wodim:
[http://ubuntuforums.org/showthread.php?t=448453&highlight=wodim.conf]("http://ubuntuforums.org/showthread.php?t=448453&highlight=wodim.conf")

---

### Post by simontaylor on 2008-06-18
hi donald,

back on with usual frustration at not finding a satisfying fix for the bug: switched to libata at your prompt. Have also extracted the suite cdrtools-2.01.01 ... but I don't know how to install it. It's an 8.5 MB folder, sitting on my desktop at present. cdrtools would be what the wodim-based (?) cdrkit and cdrdao have sought to supercede ... without any success, as far as I'm concerned, since on Feisty cdrecord worked fine. The bug came with the 8.04 update. Stupid, I know, but can you guide me through the cdrtools install? have tried > sudo cp cdrtools-2.01.01 /usr/bin/ 

with this reponse in terminal

> cp: omitting directory `cdrtools-2.01.01'

best,
simon

---

### Post by simontaylor on 2008-06-18
well, here's a problem:

>  cdrdao scanbus
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Error trying to open /dev/sg1 exclusively (Permission denied)... retrying in 1 second.

---

### Post by alienexplorers on 2008-06-18
Try cdrecord scanbus

---

### Post by simontaylor on 2008-06-18
had looked before ... makes a little more sense now ... synaptic man has entry for cdrecord

> cdrecord scanbus
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
wodim: No such file or directory. Cannot open 'scanbus'.

went into > /etc/wodim.conf which, for interest, looks like this:

> # wodim.dfl Copyright 2006 E. Bloch
# Based on cdrecord.dfl (Copyright 1998 J. Schilling)
#
# This file is /etc/wodim.conf
# It contains defaults that are used if no command line option
# or environment is present.
# 
# The default device, if not specified elsewhere.
#
#CDR_DEVICE=yamaha
CDR_DEVICE=cdrom

# 
# The default speed, if not specified elswhere.
#
# For MMC compliant drives, the default is to write at maximum speed, so it in
# general does not make sense to set up a default speed in /etc/wodim.conf.
#
#CDR_SPEED=40

# 
# The default FIFO size if, not specified elswhere.
#
CDR_FIFOSIZE=12m

#
# CDR_MAXFIFOSIZE can limit the maximum allowed FIFO size. This is useful to
# not let mallicious users allocate too much system memory if no ulimit is set
# or wodim runs with suid-root permissions.
#
# CDR_MAXFIFOSIZE=256m

#
# The following definitions allow abstract device names.  They are used if the
# device name does not contain the the characters ',', ':', '/' and '@'
#
# Unless you have a good reason, use speed == -1 and let wodim use its internal
# drive specific defaults.
#
# drive name	device	speed	fifosize driveropts
#
#default=	USCSI:0,0,0	-1	-1	burnfree
#sanyo=		1,4,0	-1	-1	burnfree
#cdrom=		0,6,0	2	1m	""
#remote=		REMOTE:rscsi@somehost:1,0,0	16	32m	burnfree
#
cdrom=          -1      -1      -1      burnfree

where PhilJ in the > burning and blanking in xfburn is this a cure for you? thread has added

> default= ATAPI:0,0,0 -1 -1 burnfree

I have 

> default=	USCSI:0,0,0	-1	-1	burnfree

now I know there's some issue about the SCSI but ATAPI makes no sense. I changed the device to 0 (from 1) to see if this is the root cause of my lack of permission to open > /dev/sg1 

or is this the point of making sure I'm in the usr group? or is this the driver issue that cdrdao scanbus points to?

best

---

### Post by simontaylor on 2008-06-18
then again, looking at FIFOSIZE, would the limit here cause the reported > cannot raise RLIMIT_MEMLOCK 

message?

mmmmmmmmmmmmmmmmmmmmmm

---

### Post by alienexplorers on 2008-06-18
First is your system scsi or ide or sata.  Please print your fstab file.  Yes the fifo may have something to do with that error, but I have no ideaa how to set it up.  Try removing the # in front of the CDR_MAXFIFOSIZE=256m.

---

### Post by simontaylor on 2008-06-18
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=5d2cb925-f4e0-4630-b3a2-d818e5ef7fbf none            swap    sw              0       0

/dev/hdc 	/media/cdrom0 	udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

here's what I've read about FIFO [http://forums.gentoo.org/viewtopic-t-579662-highlight-.html?sid=093d338d3cc563b0d0583708d1252678]("http://forums.gentoo.org/viewtopic-t-579662-highlight-.html?sid=093d338d3cc563b0d0583708d1252678")

see, it has a link to ATAPI --- the instructions are pretty complex 

You don't think I should install cdrtools-2.01.01?

---

### Post by simontaylor on 2008-06-18
> The fifo buffer runs low - that makes the drive run slower. cdrecord/growisofs/cdrdao can raise their process priority and decrease the risk of fifo buffer drops - if they're run under root or setuidroot. 

> cd /usr/bin
chown root:cdrom cdrecord cdrdao growisofs
chmod 4710 cdrecord cdrdao growisofs

> Given that you're using UTF8 I'd upgrade to cdrtools-2.01.01_alpha34 before doing that. The new included mkisofs has better support for UTF8. For better fifo performance you can increase the fifo size a little bit, for instance to 32MB, which is useful for DVD writing. You can tell k3b to do so in it's setup.

excerpts from [http://forums.gentoo.org/viewtopic-t-579662-highlight-.html?sid=093d338d3cc563b0d0583708d1252678]("http://forums.gentoo.org/viewtopic-t-579662-highlight-.html?sid=093d338d3cc563b0d0583708d1252678")

---

### Post by alienexplorers on 2008-06-18
Save your fstab by doing a:
> sudo cp fstab fstab.bak
Now make the following changes to your fstab file.  Note 1) the changes are in red:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# [COLOR="Red"]/dev/sda6[/COLOR]
UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa / ext3 defaults,errors=remount-ro 0 1
# [COLOR="Red"]/dev/sda7[/COLOR]
UUID=5d2cb925-f4e0-4630-b3a2-d818e5ef7fbf none swap sw 0 0

[COLOR="Red"]/dev/scd0[/COLOR] /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 

Save the file and reboot.  If the system does not load boot in recovery mode and sudo rm fstab and run sudo fstab.bak fstab.

If everything loads OK then rerun cdrdao scanbus.

I thinks it would be fine to load that cdrtools file.  What could it hurt.

---

### Post by simontaylor on 2008-06-18
yep. That went down fine --- that's the SATA change, yeah? But this didn't go down at all:

> cdrdao scanbus
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Error trying to open /dev/sg1 exclusively (Permission denied)... retrying in 1 second.
etc.
etc.

I don't know how to load the cdrtools file. Although it hurts my pride to say so!

best

---

### Post by alienexplorers on 2008-06-19
CD to the directory cdrtools is in.
Double click on cdrtools-2.01.01 and extract file to /home/yourname/cdrtools-2.01.01......
cd /home/yourname/cdrtools-2.01.01
sudo make
wait for prompt
sudo make install
wait for prompt
sudo make clean

cd /opt/schily
this is where the new files are stored.

---

### Post by alienexplorers on 2008-06-19
Some Info about your CDROM:

Vendor-------Model--------Firmware-----Driver----Recording----CD-TEXT--Reading 

PIONEER-----DVD-ROM DVD-114---2.06---generic-mmc----o----------o--------o

---

### Post by cariboo on 2008-06-19
In earlier kernel versions to find the cd-rom you would issue:

```
cdrecord -scanbus dev=ATA
```

to find the dirve id. Now wodim seems to be the one to use

```
wodim -scanbus
scsibus1:
	1,0,0	100) 'HL-DT-ST' 'DVDRAM GSA-4167B' 'DL10' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
```

To  record a mixed-mode CD with an ISO 9660 filesystem from cdimage.raw on the first track, the other tracks being audio tracks from the  files track01.cdaudio, track02.cdaudio, etc:

```
wodim -v dev=1,0 cdimage.raw -audio track*.cdaudio
```

I got most of this info from man wodim

Jim

---

### Post by simontaylor on 2008-06-19
that was brilliant! first time I've installed through terminal. 

cdrecord scanbus returns no data.

I get this

> WARNING: the ATA: method is considered deprecated on modern kernels!

be very interesting to see if it's wodim causing the problem.

thanks for coming up with such invaluable assistance.

will check through K3b with dependencies and paths and perhaps run a test.

---

### Post by simontaylor on 2008-06-19
hi donald,
writing immediately before thoroughly going through data: check out this debug off K3b --- yes it failed but:

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.06 (/dev/scd0, /dev/sg2) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 2.1.1a41

cdrecord
-----------------------
/opt/schily/bin/cdrecord: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits./opt/schily/bin/cdrecord: Cannot allocate memory. WARNING: Cannot do mlockall(2).
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
/opt/schily/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/opt/schily/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
Cdrecord-ProDVD-ProBD-Clone 2.01.01a41 (i686-pc-linux-gnu) Copyright (C) 1995-2008 Jörg Schilling
TOC Type: 0 = CD-DA
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-R
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
/opt/schily/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/opt/schily/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
pregap1: -1
Track 01: audio  314 MB (31:11.05) no preemp swab copy
Track 02: audio  189 MB (18:47.44) no preemp swab copy
Track 03: audio   73 MB (07:15.98) no preemp swab copy
Track 04: audio  168 MB (16:41.25) no preemp swab copy
Total size:      746 MB (73:55.73) = 332680 sectors
Lout start:      746 MB (73:57/55) = 332680 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
Disk Is not unrestricted
Disk Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
    Capacity  Blklen/Sparesz.  Format-type  Type
           0             2048         0x00  Unformated or Blank Media
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 27166
Starting to write CD/DVD/BD at speed 10 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  314 MB written.
/opt/schily/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
/opt/schily/bin/cdrecord: A write error occured.
/opt/schily/bin/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   13.299s
Average write speed 879.6x.
Fixating...
/opt/schily/bin/cdrecord: Input/output error. flush cache: scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 44 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x44 Qual 0x00 (internal target failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 16.185s timeout 200s
Trouble flushing the cache
Fixating time:   16.211s
/opt/schily/bin/cdrecord: fifo had 64 puts and 1 gets.
/opt/schily/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/opt/schily/bin/cdrecord -v gracetime=2 dev=/dev/scd0 speed=10 -dao driveropts=burnfree -eject -useinfo -audio /tmp/kde-simon/k3b_audio_0_01.inf /tmp/kde-simon/k3b_audio_0_02.inf /tmp/kde-simon/k3b_audio_0_03.inf /tmp/kde-simon/k3b_audio_0_04.inf 

---

### Post by alienexplorers on 2008-06-19
Did you try reading that disk.  I come up with roughly the same error and the disks are still readable.  Also, did you try what cariboo907 said which was to enter in terminal:
> wodim -scanbus
I tried running with the cdrtools-2.0.0 and found that I could not record anything in gnomebaker or k3b.  When I removed it I was again able to burn cd's with gnomebaker and k3b.  I had a problem with gnomebaker locking up so I unloaded it and am sticking with k3b which is working perfectly.

---

### Post by simontaylor on 2008-06-19
> wodim -scanbus
scsibus1:
	1,0,0	100) 'PIONEER ' 'DVD-RW  DVR-111D' '1.06' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

and from attempt to mount disc:

> Unable to mount Audio Disc
Drive /dev/scd0 does not contain audio files

---

### Post by alienexplorers on 2008-06-19
When you tried to mount it di you do:
> sudo mount /dev/scd0 /media/cdrom

---

### Post by simontaylor on 2008-06-19
No. Just put it in drawer.

when I do try sudo mount/dev/scd0 /media/cdrom

I get > mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type

---

### Post by alienexplorers on 2008-06-19
I am having a lot of senior moments ever since I had my brain operated on to remove a non cancerous tumor. I use to be able to fix problems with no problem, but now it's like learning everything all over again.  I do remember that you can't mount a cd drive.  It gets mounted when it is being run in a program such as k3b.


terminator@terminator-desktop:~$ wodim -scanbus
scsibus1:
	1,0,0	100) 'HL-DT-ST' 'DVD-ROM GDR8164B' '0L06' Removable CD-ROM
	1,1,0	101) 'BTC     ' 'BCE2410IM       ' 'A.23' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

Next week I am ordering a new cd/dvd combo drive and a new hard drive.  Probably will have problems setting that up.  So anything I learn here will really help me in setting that stuff up.

---

### Post by simontaylor on 2008-06-19
donald,
for me the problem is human-readable vs. terminal/and-people-used-to-terminal-readable-and-computer-logic language: for example, volumes 'mount' in Unix and Linux; so I say to you, I 'mount' the drive or disc by inserting it into the drawer of my cdr/drdr, and my desktop tells me whether it has 'mounted' or not. Which means I take your point: no, you don't 'mount' a cd drive. 

For me language is a much more movable feast than an efficient means of communicating what task you need a collection of complex algorhythms to perform. 

Any brain has its 'new normal' - yours is post-op, mine is post dealing with computer logic! (Although, that said, I know that dealing with surgical intervention in your personal bio-kernel is a big thing: had a scare last year and the subsequent MRIs showed nothing --- but I haven't been able to play my dvd of the MRI - and see the space where my brain should be - because Ubuntu doesn't like the codec!!!)

That gentoo forum I linked to had some good stuff --- pushing the parameters of the memlock out --- and I'm heartened by the CHANGE in the problem I'm experiencing with this bug: a qualitative change, now an input/output error. I strongly suspect a clash somewhere between wodim and cdrecord (even if it's cdrecord in its new encodement as cdrtools). 

And, having said that, I'm amazed such a simple problem as not being able to burn an audio cd from files already on my drive is so difficult to solve!!!!!!!!!!!!!!

best,
simon

---

### Post by simontaylor on 2008-06-19
found this at [http://k3b.plainblack.com/message-board/unable-to-writelba7f690h-input/output-error]("http://k3b.plainblack.com/message-board/unable-to-writelba7f690h-input/output-error")

> a very similar error can be due to a filesystem corrpution. If /var/log/user.log contains something like:

k3b: resmgr: communication failure : No such file or directory

 

Try fsck the filesystem.

had a look at my user log:> 
Jun 20 08:37:32 simon-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu

which was repeated innumerable times for all the dates I tried burning cds.

then

> fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa'

which in my fstab is under /dev/sda6 (ext 3)

---

### Post by tipiglen on 2008-07-04
Try here:

[http://ubuntuforums.org/showthread.php?p=5318658#post5318658](http://ubuntuforums.org/showthread.php?p=5318658#post5318658)

best of luck
ed

---

### Post by ales on 2008-07-05
Hi all,

maybe this is stupid to write, but I noticed, that when I attach an usb device to my computer a leave it in system, the burning fails with the error saying, that write error occured which was likely due to overburning the disc.
I just removed  my usb drive from port and restarted ubuntu again and it worked. I dont'know if it influences the system so, that the burning fails.
Maybe.

Maybe someone has similar experience.

Bye.



Ales

---

### Post by simontaylor on 2008-07-07
I left the problem alone, completely frustrated and none the wiser. Tried to put a bunch of jpgs onto disc tonight and couldn't write them to disc. Attempted to use K3b and this is the output:

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

K3bIsoImager
-----------------------
mkisofs print size result: 33284 (68165632 bytes)
Pipe throughput: 4180736 bytes read, 4176384 bytes written.

Used versions
-----------------------
mkisofs: 2.1.1a41
cdrecord: 2.1.1a41

cdrecord
-----------------------
/opt/schily/bin/cdrecord: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits./opt/schily/bin/cdrecord: Cannot allocate memory. WARNING: Cannot do mlockall(2).
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
/opt/schily/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/opt/schily/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
Cdrecord-ProDVD-ProBD-Clone 2.01.01a41 (i686-pc-linux-gnu) Copyright (C) 1995-2008 Jörg Schilling
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identifikation : 'DVD-RW  DVR-111D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: CD-R
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-R/DL layer jump recording 
Profile: DVD-R/DL sequential recording 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-R sequential recording 
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R (current)
Profile: CD-ROM 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R LAYER_JUMP
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
/opt/schily/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/opt/schily/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/opt/schily/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data    65 MB        
Total size:       74 MB (07:23.81) = 33286 sectors
Lout start:       74 MB (07:25/61) = 33286 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
Disk Is not unrestricted
Disk Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
    Capacity  Blklen/Sparesz.  Format-type  Type
           0             2048         0x00  Unformated or Blank Media
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 326560
Starting to write CD/DVD/BD at speed 4 in real TAO mode for multi session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of   65 MB written.
/opt/schily/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 1F 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 40s
/opt/schily/bin/cdrecord: A write error occured.
/opt/schily/bin/cdrecord: Please properly read the error message above.
write track data: error after 63488 bytes
Writing  time:   18.776s
Average write speed  51.7x.
Fixating...
Fixating time:   64.468s
/opt/schily/bin/cdrecord: fifo had 65 puts and 2 gets.
/opt/schily/bin/cdrecord: fifo was 0 times empty and 1 times full, min fill was 98%.

cdrecord command:
-----------------------
/opt/schily/bin/cdrecord -v gracetime=2 dev=/dev/scd0 speed=4 -tao driveropts=burnfree -eject -multi -xa -tsize=33284s - 

mkisofs
-----------------------
33284
/opt/schily/bin/mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
/opt/schily/bin/mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
/opt/schily/bin/mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
Setting input-charset to 'UTF-8' from locale.
  1.55% done, estimate finish Mon Jul  7 19:48:55 2008
  3.02% done, estimate finish Mon Jul  7 19:48:24 2008
  4.51% done, estimate finish Mon Jul  7 19:48:13 2008
  6.04% done, estimate finish Mon Jul  7 19:48:07 2008

mkisofs calculate size command:
-----------------------
/opt/schily/bin/mkisofs -gui -graft-points -print-size -quiet -volid p1050728 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-simon/k3bfHKyEa.tmp -rational-rock -hide-list /tmp/kde-simon/k3bd9M77b.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-simon/k3bIjMFta.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-simon/k3b0dg8Mb.tmp 

mkisofs command:
-----------------------
/opt/schily/bin/mkisofs -gui -graft-points -volid p1050728 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-simon/k3bS9Lvlc.tmp -rational-rock -hide-list /tmp/kde-simon/k3bDogXPa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-simon/k3bjuXXoc.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-simon/k3byyqe3a.tmp 

That's right. I've learnt nothing. None of it makes sense. And clearly the fault is mine in trying to work with a system I know nothing about. Or my little knowledge has realised the inevitable danger. 

Educate yourself, you say to me. I've read and researched this particular problem and still it makes no sense to me. I need a dummy's fix for this. Otherwise I may as well forget I have a cd/dvd writer. Why? Because it doesn't work.

As to the simple fixes of changing the cdrom0 to cdrom1 in fstab - no, I did that, even though I've got no idea what it means. It made no difference whatsoever.

As for reducing the writing speed to the lowest possible, I've done that too, with no result. You'll see from the above that it's trying to burn at x4. 

I might have downloaded so much extraneous shite to support K3b - in the ways of dependencies - that I've exacerbated the problem. Maybe. I don't understand.

Yours, incorrigibly frustrated, don't talk to me unless you can be bothered dealing with an UBUNTU IDIOT,

Simon

---

### Post by simontaylor on 2008-07-07
Error.

---

### Post by alienexplorers on 2008-07-07
Why don't you just bite the bullet and reformat everything.  Start from scratch using the new 8.04.1 CD.  With all the changes you made there is probably more wrong with the system other than just the burning problem.  I have had to reload my system twice before everything started working hyst fine.  Now I am adding a Lightscribe drive and no doubt I will be having problems with that.  I am ready to reload if needed.

---

### Post by ka0spm on 2008-07-07
I am with SimonTaylor, i have tried numerous changes and i am on my 10 fails Cut of the a cd. I am right now reduced to using a Laptop with Vista to cut a cd, Apparently the ubuntu group does not see this as a problem because there are few if any bugs open on this and the open ones are of low priority. So I guess the Ubuntu thinks the ability to write CD DVD's is low priority. 

I have made too many configuration changes to count. I have failures of numerous types with k3b, gnomebaker and Brasero. Before you make suggestions I have tried all the things Simon has and gotten no joy. I cut the .iso on this machine to do an upgrade to heron, now no CD's. I guess the idea that vista is kicking Hardys butt would make a few developers sort of uneasy. I will leaving Ubuntu as soon as I can get a Debian netinstaller cut. Just tired of the stuff that don't work anymore.

---

