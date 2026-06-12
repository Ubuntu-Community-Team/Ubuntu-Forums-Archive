---
title: "Need help with sound on acer 6920"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by rab4567 on 2008-09-28
Hi all, I need a little help with no sound on my acer 6920 I'm using Cjay 554 fix for this problem [http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920](http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920) but I'm getting lots of errors, I need someone to show me where I went wrong see here


make[1]: Entering directory `/home/rodney/oss41build/kernel/OS/Linux' 
make[1]: Nothing to be done for `all'. 
make[1]: Leaving directory `/home/rodney/oss41build/kernel/OS/Linux' 
noregparm 
make[1]: Entering directory `/home/rodney/oss41build/noregparm' 
for n in kernel lib kernel/OS/Linux;do (echo $n && cd $n && make ARCH=x86_64) || eval 'exit 1'; done 
kernel 
make[2]: Entering directory `/home/rodney/oss41build/noregparm/kernel' 
for n in drv framework;do (echo $n && cd $n && make ARCH=x86_64) || eval 'exit 1'; done 
drv 
make[3]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv' 
for n in oss_ali5455 oss_atiaudio oss_audigyls oss_audioloop oss_audiopci oss_cmi878x oss_cmpci oss_cs4281 oss_cs461x oss_digi96 oss_emu10k1x oss_envy24 oss_envy24ht oss_fmedia oss_geode oss_hdaudio oss_ich oss_imux oss_midiloop oss_midimix oss_sblive oss_sbpci oss_sbxfi oss_solo oss_trident oss_usb oss_userdev oss_via823x oss_via97 oss_ymf7xx;do (echo $n && cd $n && make ARCH=x86_64) || eval 'exit 1'; done 
oss_ali5455 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_ali5455' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_ali5455' 
oss_atiaudio 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_atiaudio' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_atiaudio' 
oss_audigyls 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_audigyls' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_audigyls' 
oss_audioloop 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_audioloop' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_audioloop' 
oss_audiopci 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_audiopci' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_audiopci' 
oss_cmi878x 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cmi878x' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cmi878x' 
oss_cmpci 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cmpci' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cmpci' 
oss_cs4281 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cs4281' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cs4281' 
oss_cs461x 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cs461x' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_cs461x' 
oss_digi96 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_digi96' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_digi96' 
oss_emu10k1x 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_emu10k1x' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_emu10k1x' 
oss_envy24 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_envy24' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_envy24' 
oss_envy24ht 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_envy24ht' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_envy24ht' 
oss_fmedia 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_fmedia' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_fmedia' 
oss_geode 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_geode' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_geode' 
oss_hdaudio 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_hdaudio' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_hdaudio' 
oss_ich 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_ich' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_ich' 
oss_imux 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_imux' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_imux' 
oss_midiloop 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_midiloop' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_midiloop' 
oss_midimix 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_midimix' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_midimix' 
oss_sblive 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_sblive' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_sblive' 
oss_sbpci 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_sbpci' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_sbpci' 
oss_sbxfi 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_sbxfi' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_sbxfi' 
oss_solo 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_solo' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_solo' 
oss_trident 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_trident' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_trident' 
oss_usb 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_usb' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_usb' 
oss_userdev 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_userdev' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_userdev' 
oss_via823x 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_via823x' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_via823x' 
oss_via97 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_via97' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_via97' 
oss_ymf7xx 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_ymf7xx' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv/oss_ymf7xx' 
make[3]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/drv' 
framework 
make[3]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework' 
for n in ac97 audio midi_stubs mixer osscore remux sndstat uart401 vmix_core;do (echo $n && cd $n && make ARCH=x86_64) || eval 'exit 1'; done 
ac97 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/ac97' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/ac97' 
audio 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/audio' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/audio' 
midi_stubs 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/midi_stubs' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/midi_stubs' 
mixer 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/mixer' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/mixer' 
osscore 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/osscore' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/osscore' 
remux 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/remux' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/remux' 
sndstat 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/sndstat' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/sndstat' 
uart401 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/uart401' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/uart401' 
vmix_core 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/kernel/framework/vmix_core' 
make[4]: Nothing to be done for `all'. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework/vmix_core' 
make[3]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/framework' 
make[2]: Leaving directory `/home/rodney/oss41build/noregparm/kernel' 
lib 
make[2]: Entering directory `/home/rodney/oss41build/noregparm/lib' 
for n in libOSSlib;do (echo $n && cd $n && make ARCH=x86_64) || eval 'exit 1'; done 
libOSSlib 
make[3]: Entering directory `/home/rodney/oss41build/noregparm/lib/libOSSlib' 
sh ./compile.sh /lib "cc" "-O -fPIC" "make" 
make[4]: Entering directory `/home/rodney/oss41build/noregparm/lib/libOSSlib' 
make[4]: `libOSSlib.so' is up to date. 
make[4]: Leaving directory `/home/rodney/oss41build/noregparm/lib/libOSSlib' 
make[3]: Leaving directory `/home/rodney/oss41build/noregparm/lib/libOSSlib' 
make[2]: Leaving directory `/home/rodney/oss41build/noregparm/lib' 
kernel/OS/Linux 
make[2]: Entering directory `/home/rodney/oss41build/noregparm/kernel/OS/Linux' 
make[2]: Nothing to be done for `all'. 
make[2]: Leaving directory `/home/rodney/oss41build/noregparm/kernel/OS/Linux' 
make[1]: Leaving directory `/home/rodney/oss41build/noregparm' 
sh build.sh 
Check devices for oss_ali5455 
Check devices for oss_atiaudio 
Check devices for oss_audigyls 
Check devices for oss_audioloop 
Check devices for oss_audiopci 
Check devices for oss_cmi878x 
Check devices for oss_cmpci 
Check devices for oss_cs4281 
Check devices for oss_cs461x 
Check devices for oss_digi96 
Check devices for oss_emu10k1x 
Check devices for oss_envy24 
Check devices for oss_envy24ht 
Check devices for oss_fmedia 
Check devices for oss_geode 
Check devices for oss_hdaudio 
Check devices for oss_ich 
Check devices for oss_imux 
Check devices for oss_midiloop 
Check devices for oss_midimix 
Check devices for oss_sblive 
Check devices for oss_sbpci 
Check devices for oss_sbxfi 
Check devices for oss_solo 
Check devices for oss_trident 
Check devices for oss_usb 
Check devices for oss_userdev 
Check devices for oss_via823x 
Check devices for oss_via97 
Check devices for oss_ymf7xx 
cp: cannot stat `lib/libsalsa/.libs/libsalsa.so.2.0.0': No such file or directory 
Warning: No libsalsa library compiled 
done ossinfo 
done ossmix 
done ossplay 
done ossrecord 
done osstest 
done ossxmix 
done ossdevlinks 
done savemixer 
done vmixctl 
done ossdetect 
cp -R prototype/* / 
cd /usr/lib/oss/build && sh install.sh 

OSS build environment set up for REGPARM kernels 

Building module osscore 
Building module oss_ali5455 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_atiaudio 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_audigyls 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_audioloop 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_audiopci 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_cmi878x 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_cmpci 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_cs4281 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_cs461x 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_digi96 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_emu10k1x 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_envy24 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_envy24ht 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_fmedia 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_geode 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_hdaudio 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_ich 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_imux 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_midiloop 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_midimix 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_sblive 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_sbpci 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_sbxfi 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_solo 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_trident 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_usb 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_userdev 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_via823x 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_via97 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
Building module oss_ymf7xx 
make[1]: Entering directory `/usr/lib/oss/build' 
make[1]: Leaving directory `/usr/lib/oss/build' 
depmod -a 
----------------------------- 
Detected Intel High Definition Audio (ICH8) 
USB support available in the system, adding USB driver 
Detected Generic USB audio/MIDI device (BETA) 
----------------------------- 

sync 
soundoff && sync && soundon 
OSS not loaded. 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
ERROR: Module snd_hda_intel is in use 
ERROR: Module snd_pcm is in use by snd_hda_intel 
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm 
ERROR: Module snd_hwdep is in use by snd_hda_intel 
ERROR: Module snd_timer is in use by snd_pcm 
Failed to disable conflicting sound drivers 
Reboot and try running soundon again 

Also check that you have not compiled sound support statically 
into the kernel. 
make: *** [install] Error 50 
rodney@rodney-laptop:~/oss41build$ 
rodney@rodney-laptop:~/oss41build$ sudo apt-get remove libflashsupport 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package libflashsupport is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
rodney@rodney-laptop:~/oss41build$ cd ~/Desktop 
rodney@rodney-laptop:~/Desktop$ 
rodney@rodney-laptop:~/Desktop$ gunzip libflashsupport.so.gz 
gzip: libflashsupport.so.gz: No such file or directory 
rodney@rodney-laptop:~/Desktop$

thanks you for the help.

---

### Post by rab4567 on 2008-10-10
Can anyone help me?

---

### Post by kansasnoob on 2008-10-10
[http://ubuntuforums.org/showthread.php?p=5862362](http://ubuntuforums.org/showthread.php?p=5862362)

---

