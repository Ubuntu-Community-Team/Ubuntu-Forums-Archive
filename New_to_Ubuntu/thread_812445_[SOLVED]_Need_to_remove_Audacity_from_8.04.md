---
title: "[SOLVED] Need to remove Audacity from 8.04"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by CyberDean on 2008-05-29
Just received the below Visionman DEP-VO100 Intel computer for audio recording at church.  Installed Ubuntu 8.04 64 bit desktop and Audacity.
When I record audio there is a tone under the audio I am trying to record and it is distorted.  When I installed Audacity, I compiled it like I did on my desktop that we currently use without any problems.  I would like to remove Audacity from the computer and install the precompiled version to see if there is a difference in recording quality, or maybe a bad audio circuit.  But I can't figure out how to remove the current Audacity. Synaptic Package Manager and Add/Remove do not see it as being installed.  I have searched through the directories and can not find a directory or file for audacity.  The program "Audacity Sound Editor" is listed under "Applications", "Sound & Audio".  The only other thing I can think of is to wipe the disk and start all over, that would not be a big lose, very little data on the computer at this time.

Any help out there?  Thanks in advance.:confused:

PCI Slots (Total):       	2
PCI Express X1 Slots (Total):  	1
PCI Express X16 Slots (Total):  1
PCI Express Slots (Total):  	2
Expansion Slots:  	        4
Processor Brand:  	        Intel®
Processor Class:  	        Pentium® Dual Core
Processor Number:  	        E2180
Processor Speed:  	        2.00GHz
Processor Interface:  	        Socket LGA775
Processors Supported:  	        1
Additional Technologies:  	Intel® Extended Memory 64 Technology
	  	Dual-Core Technology
Memory Type:  	                DDR2
Total Memory:  	                2.0GB
Memory Speed:  	                DDR2 667 (PC2-5300)
Maximum Memory Supported:  	4.0GB
Interface:  	                SATA II
Capacity:  	                500GB
Speed:  	                7,200RPM
Optical Drive Type:  	        DVD±RW/-RAM Dual Layer
Interface:  	                SATA
Type:  	                        Media Reader
Capacity:  	                7-in-1
Audio Description:  	        Integrated Audio
Audio Chipset:  	        High Definition
Channels:  	                5.1
Graphics Description:  	        Integrated Graphics
GPU/VPU:  	                Intel Graphics Media Accelerator 950
Video Interface:  	        VGA (15-Pin D-Sub)
Communications Description:  	Integrated LAN Support
Interface Type:  	        RJ-45 - Ethernet Connector
Data Transfer Rate:  	        1000Mbps
	  	                10Mbps
	  	                100Mbps
Power:  	                300 Watt
Mouse Type:  	                Optical
Buttons:  	                3
Scrolling Capability:  	        Vertical
Keyboard Type:  	        Premium
Front Speakers:  	        2

---

### Post by Inxsible on 2008-05-29
If you compiled it from source, you will need the source folder to uninstall it.  Or you may have to manually remove all the files in case you dont have the source folder.

---

### Post by Oldsoldier2003 on 2008-05-29
> **Inxsible said:**
> If you compiled it from source, you will need the source folder to uninstall it.  **Or you may have to manually remove all the files in case you dont have the source folder**.

You could just recompile then sudo make uninstall if you deleted the source folder.

---

### Post by drs305 on 2008-05-29
I compiled the latest version of audacity 1.3.4-1 to get a specific feature which is no longer included. Here is my synapatic list (I used checkinstall)  If you decide to delete things manually it will at least give you a start.

```
/.
/usr
/usr/local
/usr/local/bin
/usr/local/bin/audacity
/usr/local/share
/usr/local/share/man
/usr/local/share/man/man1
/usr/local/share/man/man1/audacity.1.gz
/usr/local/share/doc
/usr/local/share/doc/audacity
/usr/local/share/doc/audacity/LICENSE.txt
/usr/local/share/doc/audacity/README.txt
/usr/local/share/audacity
/usr/local/share/audacity/audacity.xpm
/usr/local/share/audacity/nyquist
/usr/local/share/audacity/nyquist/seq.lsp
/usr/local/share/audacity/nyquist/sndfnint.lsp
/usr/local/share/audacity/nyquist/nyqmisc.lsp
/usr/local/share/audacity/nyquist/misc.lsp
/usr/local/share/audacity/nyquist/system.lsp
/usr/local/share/audacity/nyquist/bug.lsp
/usr/local/share/audacity/nyquist/xlinit.lsp
/usr/local/share/audacity/nyquist/dspprims.lsp
/usr/local/share/audacity/nyquist/init.lsp
/usr/local/share/audacity/nyquist/test.lsp
/usr/local/share/audacity/nyquist/evalenv.lsp
/usr/local/share/audacity/nyquist/seqfnint.lsp
/usr/local/share/audacity/nyquist/printrec.lsp
/usr/local/share/audacity/nyquist/seqmidi.lsp
/usr/local/share/audacity/nyquist/nyinit.lsp
/usr/local/share/audacity/nyquist/follow.lsp
/usr/local/share/audacity/nyquist/profile.lsp
/usr/local/share/audacity/nyquist/nyquist.lsp
/usr/local/share/audacity/plug-ins
/usr/local/share/audacity/plug-ins/highpass.ny
/usr/local/share/audacity/plug-ins/vocoder.ny
/usr/local/share/audacity/plug-ins/beat.ny
/usr/local/share/audacity/plug-ins/crossfadein.ny
/usr/local/share/audacity/plug-ins/delay.ny
/usr/local/share/audacity/plug-ins/tremolo.ny
/usr/local/share/audacity/plug-ins/lowpass.ny
/usr/local/share/audacity/plug-ins/SilenceMarker.ny
/usr/local/share/audacity/plug-ins/pluck.ny
/usr/local/share/audacity/plug-ins/crossfadeout.ny
/usr/local/share/audacity/plug-ins/equalabel.ny
/usr/local/share/audacity/plug-ins/clicktrack.ny
/usr/local/share/audacity/plug-ins/rissetdrum.ny
/usr/local/share/mime
/usr/local/share/mime/packages
/usr/local/share/mime/packages/audacity.xml
/usr/local/share/applications
/usr/local/share/applications/audacity.desktop
/usr/share
/usr/share/doc
/usr/share/doc/audacity-src
/usr/share/doc/audacity-src/README.txt


```

---

### Post by CyberDean on 2008-05-29
> **Inxsible said:**
> If you compiled it from source, you will need the source folder to uninstall it.  Or you may have to manually remove all the files in case you dont have the source folder.

The source folder, ok you got me, I am still fairly new to Linux and I'm not sure what the source folder is. I followed "HOWTO: Compile Audacity on Linux - 1.3 Beta Series on Ubuntu Gutsy" by ArtInvent Feb 1, 2008, and it worked. To be honest with you I am suspecting a bad audio circuit, but I need to be able to prove it before I contact the manufacture.  I just played an audio CD and the left channel is distorted also.  I know when I tell them I'm using Linux they will tell me that's the problem, and I want to be able to prove it one way or another.  Sorry I can't help you any more, Thanks.

---

### Post by CyberDean on 2008-05-29
Thanks drs305, that will get me started.

---

### Post by drs305 on 2008-05-29
> **CyberDean said:**
> The source folder, ok you got me, I am still fairly new to Linux and I'm not sure what the source folder is. 

When you compile something, one of the first things that is usually done is to extract a folder. During compilation of the program, certain files are generated within the folder. Normally you don't need that folder once the program is installed to RUN the program. 

However, there are usually scripts generated to uninstall the app should you choose to do so. Since the app doesn't show up in synaptic nor is registered by apt-get/aptitude, the system has no knowledge of how to uninstall it. The scripts are the only things containing this information. If the folder is deleted, that information is lost. That is why it is a good practice to save the folder somewhere so that you can access the removal scripts when that day comes.

An even easier method is to install and use 'checkinstall' instead of make install. Checkinstall can create a deb file and also register the files in synaptic for easy removal.

---

### Post by CyberDean on 2008-05-29
> **drs305 said:**
> When you compile something, one of the first things that is usually done is to extract a folder. During compilation of the program, certain files are generated within the folder. Normally you don't need that folder once the program is installed to RUN the program. 

However, there are usually scripts generated to uninstall the app should you choose to do so. Since the app doesn't show up in synaptic nor is registered by apt-get/aptitude, the system has no knowledge of how to uninstall it. The scripts are the only things containing this information. If the folder is deleted, that information is lost. That is why it is a good practice to save the folder somewhere so that you can access the removal scripts when that day comes.

An even easier method is to install and use 'checkinstall' instead of make install. Checkinstall can create a deb file and also register the files in synaptic for easy removal.

Thanks again, I have removed Audacity, my compiled version and reinstalled Audacity through the Synaptic Package Manager.  You have helped solve my immediate problem, now to take the computer back and test it.  But I don't believe it will fix the real problem, but I'm hoping.

---

### Post by rvkbob on 2008-06-09
I too have noticed the crinkly metallic noise in Audacity recordings. It was there in Audacity 1.3.2 and I have noticed that it is still there but considerably reduced in 1.3.4. This gives me hope that maybe they'll solve the problem in the next release. In the meantime I have to use Windows to do my recording.

By the way, Audacity 1.3.4 does NOT have file compatibility with the FLAC output from the sound recorder, else that would solved the problem.

If there are any other workable solutions I'd like to hear about them.

[email]rvkbob@juno.com[/email]

---

