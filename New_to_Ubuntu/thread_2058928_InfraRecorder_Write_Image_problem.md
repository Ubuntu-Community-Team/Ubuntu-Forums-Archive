---
title: "InfraRecorder Write Image problem"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by JXR on 2012-09-16
I downloaded and checksummed **ubuntustudio-12.04-dvd-i386.iso.**
 
I want to install Ubuntu Studio.
 
I've used InfraRecorder before with good results but this time I'm having a problem.
 
After following instructions on 
[COLOR=black][FONT=DejaVu Sans][[COLOR=#800080]https://help.ubuntu.com/community/BurningIsoHowto[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto") [/FONT][/COLOR]
 
[COLOR=black][FONT=DejaVu Sans]and using Windows XP to burn the DVD with InfraRecorder [/FONT][/COLOR]
> 
[FONT=DejaVu Sans][COLOR=black][COLOR=black][FONT=DejaVu Sans]at minimum speed ~ 3.5x [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Write method: Session-At-Once (SAO)[/FONT][/COLOR]
[/COLOR][/FONT] 
[COLOR=black][FONT=DejaVu Sans]I (repeatedly) get an "Operation Failed" box with the following message [/FONT][/COLOR]
 
> 
[FONT=DejaVu Sans][COLOR=black][FONT=DejaVu Sans][COLOR=black][FONT=DejaVu Sans][COLOR=black][COLOR=black][FONT=DejaVu Sans]Warning: The DMA speed test has been skipped[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Started to write disc in real write mode.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Started to write track 1.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Input/Output error[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]A write error occurred. Please see program log...[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Please properly read the error message above.[/FONT][/COLOR]
[/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT]
 
[FONT=DejaVu Sans][COLOR=black][FONT=DejaVu Sans][COLOR=black]The program log says:[/COLOR][/FONT]
 
[FONT=DejaVu Sans][COLOR=black][COLOR=black][FONT=DejaVu Sans]>  > BURN-Free is ON.[/FONT][/COLOR][/COLOR][/FONT]> 
[FONT=DejaVu Sans][COLOR=black][COLOR=black][FONT=DejaVu Sans]> Starting new track at sector: 0[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> 0x[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Track 01: writing 30 KB of pad data[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Track 01: Total bytes read/written: 1996795904/1996826624 (975013 sectors)[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Writing time: 171[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> 844s[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Average write speed 8[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> 4x[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Min drive buffer fill was 80[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Fixating[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Fixating time: 28[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> 078s[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> /cygdrive/c/Program Files/InfraRecorder/cdrtools/cdrecord: fifo had 60938 puts and 60938 gets[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> /cygdrive/c/Program Files/InfraRecorder/cdrtools/cdrecord: fifo was 2 times empty and 4432 times full, min fill was 0[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]CCore ProcessEnded[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Process exited with code: 0.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]CCore::BurnImage[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans][0,1,0] PHILIPS DVD+-RW DVD8801 4D28[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]File = H:\Linux OS\Ubuntu 12.04 and Studio\ubuntustudio-12.04-dvd-i386.iso.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Eject = 1, Simulate = 0, BUP = 1, Pad tracks = 1, Close = 1, Overburn = 1, Swab = 0, Ignore size = 0, Immed = 0, Audio master = 1, Forcespeed = 0, VariRec (enabled) = 0, VariRec (value) = 0, Clone = 0.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Command line to run: "C:\Program Files\InfraRecorder\cdrtools\cdrecord.exe" -v dev=0,1,0 gracetime=5 -eject -sao driveropts=burnfree -pad -overburn speed=31 "/cygdrive/H/Linux OS/Ubuntu 12.04 and Studio/ubuntustudio-12.04-dvd-i386.iso"[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> scsidev: '0,1,0'[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> scsibus: 0 target: 1 lun: 0[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> SCSI buffer size: 64512[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> /cygdrive/c/Program Files/InfraRecorder/cdrtools/cdrecord: Warning: The DMA speed test has been skipped[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Cdrecord-ProDVD-ProBD-Clone 2[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> 01[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> 01a61 (i686-pc-cygwin) Copyright (C) 1995-2009 Jörg Schilling[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> TOC Type: 1 = CD-ROM[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Using libscg version 'schily-0[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> 9'[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Driveropts: 'burnfree'[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> atapi: -1[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Device type : Removable CD-ROM[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Version : 0[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Response Format: 1[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Vendor_info : 'PHILIPS '[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Identifikation : 'DVD+-RW DVD8801 '[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Revision : '4D28'[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Current: DVD-R sequential recording[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: DVD+R/DL [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: DVD+R [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: DVD+RW [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: DVD-RW sequential recording [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: DVD-RW restricted overwrite [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: DVD-R sequential recording (current)[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: DVD-ROM [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: CD-RW [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: CD-R [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Profile: CD-ROM [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Using generic SCSI-3/mmc-2 DVD-R/DVD-RW/DVD-RAM driver (mmc_dvd)[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Driver flags : NO-CD DVD MMC-3 SWABAUDIO BURNFREE [/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Supported modes: PACKET SAO[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Drive buf size : 655360 = 640 KB[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> FIFO size : 4194304 = 4096 KB[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Track 01: data 1904 MB padsize: 30 KB[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Total size: 1904 MB = 975013 sectors[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Current Secsize: 2048[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Blocks total: 2297888 Blocks current: 2297888 Blocks remaining: 1322875[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Reducing transfer size from 64512 to 32768 bytes[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Starting to write CD/DVD/BD at speed 16 in real SAO mode for single session[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Last chance to quit, starting real write in 5 seconds[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Operation starts.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Waiting for reader process to fill input buffer ... input buffer ready.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> BURN-Free is ON.[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]> Starting new track at sector: 0[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]CCoreProcessEnded[/FONT][/COLOR]
[COLOR=black][FONT=DejaVu Sans]Process exited with code: 254.[/FONT][/COLOR][/COLOR][/FONT]
 
[FONT=DejaVu Sans][COLOR=black]- I tried the same thing with "Simulation" checked and that ran fine but, of course, it didn't write anything to the disc.[/COLOR][/FONT]
[FONT=DejaVu Sans][COLOR=black]- Interestingly, it seems that in both cases nothing was written to the DVD. This is because, even after getting the "Operation Failed" message, I can still run InfraRecorder on the DVD and it does not say the disc can't be written on.[/COLOR][/FONT]
 
[FONT=DejaVu Sans][COLOR=black]Am I doing something wrong?[/COLOR][/FONT][/COLOR][/FONT]

---

