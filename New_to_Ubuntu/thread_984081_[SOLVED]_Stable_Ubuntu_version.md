---
title: "[SOLVED] Stable Ubuntu version"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by sven_wien on 2008-11-16
Hi all,

when is the new stable ubuntu 8,10 coming out as this 8,10 right now is very unstable and also sound doesnt work and internet disconects all time firefox crashes regulary etc.
where do i find out when its sop- getting released?

thanks
or is there another linux with mobile internet support u guys running as well? i dont realy want to quit ubuntu so i want to run it as second os

---

### Post by taurus on 2008-11-16
Did you upgrade from Hardy to Intrepid or did you do a clean install of Intrepid?  I don't have any problem at all since the first day it came out.

---

### Post by bodhi.zazen on 2008-11-16
Here is a kubuntu wiki page that reviews releases :

[https://wiki.kubuntu.org/Releases](https://wiki.kubuntu.org/Releases)

"Stability" is somewhat subjective and hardware dependent, and there are differences between kubuntu with KDE4 and say Ubuntu or XFCE. There are known issues with 8.10 and some nvidia cards fore example.

Others feel 8.10 is more stable then 8.04, so opinions vary.

With that said, an ubuntu release does not necessarily imply "stability".

There is always a trade off between stability and newest-latest-greatest.

If you want stable, stay with 8.04 as it has been out longer and more bugs have and will continue to be fixed (and it is a LTS so it will be with us for a while).

If you want to consider other "stable" distors take a look at Debian stable, Centos, Slackware, DSL runs on just about anything.

See also :

[http://distrowatch.com/](http://distrowatch.com/)

These forums or the ubuntu wiki can also help if you are having specific problems.

---

### Post by sven_wien on 2008-11-16
well i got an acer aspire 6920g and the os dont seem to give any sound i read lots of complains.
i reg. watch dstrowatch but i realy want sound now or a distro that supports that .? hmm thanks so far but i need more infos

---

### Post by taurus on 2008-11-16
You already tried Intrepid on your machine and couldn't get a few things to work?  Have you tried Hardy, 8.04, yet?

---

### Post by binbash on 2008-11-16
> **sven_wien said:**
> well i got an acer aspire 6920g and the os dont seem to give any sound i read lots of complains.
i reg. watch dstrowatch but i realy want sound now or a distro that supports that .? hmm thanks so far but i need more infos

This is not a stability issue.You need to configure your sound card.

This page was worked me at HARDY : 

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by sven_wien on 2008-11-16
unforunatly i tried all of that but as i am new to 8.10 and linux as such i may like someone logging into my pc somehow and fix it is that possible?

---

### Post by binbash on 2008-11-16
this will be your sound problem fix : 

[http://forum.mandriva.com/viewtopic.php?t=88199](http://forum.mandriva.com/viewtopic.php?t=88199)

---

### Post by sven_wien on 2008-11-16
looking interisting but a) where do i get the verb programm and B) is there a way to explain step by step to me?

---

### Post by binbash on 2008-11-16
> **sven_wien said:**
> looking interisting but a) where do i get the verb programm and B) is there a way to explain step by step to me?

[http://mailman.alsa-project.org/pipermail/alsa-devel/2008-May/007653.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-May/007653.html)

---

### Post by sven_wien on 2008-11-16
error 550 cwd command failed

---

### Post by binbash on 2008-11-16
you will execute the command with sudo

sudo command

---

### Post by sven_wien on 2008-11-16
as i said im new to this here the error:

```
xxl@xxl-laptop:~$ CONFIG_SND_HDA_HWDEP=y
xxl@xxl-laptop:~$ sudo ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2
[sudo] password for xxl: 
sudo: ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2: command not found
xxl@xxl-laptop:~$ 
xxl@xxl-laptop:~$ 



```


pls give me easy to use steps

---

### Post by binbash on 2008-11-16
> **sven_wien said:**
> as i said im new to this here the error:

```
xxl@xxl-laptop:~$ CONFIG_SND_HDA_HWDEP=y
xxl@xxl-laptop:~$ sudo ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2
[sudo] password for xxl: 
sudo: ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2: command not found
xxl@xxl-laptop:~$ 
xxl@xxl-laptop:~$ 



```


pls give me easy to use steps

No no.Download that : 

wget -c [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2)

then extract that and then you will run

sudo ./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

ALso before that you will do this part :

''
Thanks for the hints and the applet... after some meddling around I 
found the magic incantations to fire up the amp / speakers on this 
laptop are to force model=acer-aspire in /etc/modprobe.conf, then using 
the applet from the URL quoted above:
''

---

### Post by taurus on 2008-11-16
```
wget -c ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz
tar xvzf hda-verb-0.3.tar.gz
cd hda-verb-0.3
sudo apt-get update
sudo apt-get install build-essential
make
sudo ./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

```

---

### Post by binbash on 2008-11-16
> **taurus said:**
> ```
wget -c ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz
tar xvzf hda-verb-0.3.tar.gz
cd hda-verb-0.3
sudo apt-get update
sudo apt-get install build-essential
make
sudo ./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

```


Yes exactly : ) Thanks for saving me Taurus : )

---

### Post by sven_wien on 2008-11-16
step one works but step 2 doesnt```
xxl@xxl-laptop:~$ 
xxl@xxl-laptop:~$ sudo ./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
sudo: ./hda-verb: command not found
xxl@xxl-laptop:~$ 

```

---

### Post by binbash on 2008-11-16
> **sven_wien said:**
> step one works but step 2 doesnt```
xxl@xxl-laptop:~$ 
xxl@xxl-laptop:~$ sudo ./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
sudo: ./hda-verb: command not found
xxl@xxl-laptop:~$ 

```

navigate to the directory : 

cd hda-verb-0.3

---

### Post by sven_wien on 2008-11-16
fantastic ```
wget -c ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz
tar xvzf hda-verb-0.3.tar.gz
cd hda-verb-0.3
sudo apt-get update
sudo apt-get install build-essential
make
sudo ./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
```

works fantastic hope its working when i restarted now!
THANKS SO FAR

---

### Post by binbash on 2008-11-16
if you didnt edit /etc/modprobe.conf (i mentioned it ABOVE) it wont work probably.

---

### Post by sven_wien on 2008-11-16
pff, ok no sound after restart,

```
xxl@xxl-laptop:~$ edit /etc/modprobe.conf
Warning: unknown mime-type for "/etc/modprobe.conf" -- using "application/octet-stream"
Error: no write permission for file "/etc/modprobe.conf"
xxl@xxl-laptop:~$ 


```

what do i have to do now with this edit thing ?

---

### Post by binbash on 2008-11-16
[QUOTE=sven_wien;6191890]pff, ok no sound after restart,

```
xxl@xxl-laptop:~$ edit /etc/modprobe.conf
Warning: unknown mime-type for "/etc/modprobe.conf" -- using "application/octet-stream"
Error: no write permission for file "/etc/modprobe.conf"
xxl@xxl-laptop:~$ 


```

sudo gedit /etc/modprobe.d/alsa-base 
go to the at the end of file and add : 
options snd-hda-intel model=acer-aspire

(If something has similar to model is there , change it to acer-aspire.)

TRY the sound with reboot.

PS : go to volume center try to volume up sound etc first

---

### Post by sven_wien on 2008-11-16
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

should i change the last line then?

---

### Post by binbash on 2008-11-16
add the line i posted at the end

---

### Post by sven_wien on 2008-11-16
did that, restarted but now no sound!
i had sound earlier but just until i restarted first time what happend?

---

### Post by binbash on 2008-11-16
> **sven_wien said:**
> did that, restarted but now no sound!
i had sound earlier but just until i restarted first time what happend?

Oh aslkdjalk&#305;sjdh&#305;lashdjashdaasdasd

you have to write the script to rc.local.


give me 1 minute i will make you one

---

### Post by binbash on 2008-11-16
We will write a script to /etc/rc.local

After that it will work, if i cant manage to write one you have to give 

./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

this command everytime you boot : )

First try this if it doesnt work report here so i will write another : 

lets copy hda-verb to /usr/bin
cd hda-verb-0.3
sudo cp hda-verb /usr/bin
chmod 755 /usr/bin/hda-verb


sudo gedit /etc/rc.local

add this :

hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2


save and reboot.

---

### Post by sven_wien on 2008-11-16
seem to have a root problem ```
xxl@xxl-laptop:~$ cd hda-verb-0.3
xxl@xxl-laptop:~/hda-verb-0.3$ sudo cp hda-verb /usr/bin
xxl@xxl-laptop:~/hda-verb-0.3$ chmod 755 /usr/bin/hda-verb
chmod: Beim Setzen der Zugriffsrechte für „/usr/bin/hda-verb“: Operation not permitted
xxl@xxl-laptop:~/hda-verb-0.3$ 

```

---

### Post by binbash on 2008-11-16
sudo chmod 755 , add sudo.

---

### Post by sven_wien on 2008-11-16
ok... ```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 
```


adding at the end or where?

---

### Post by binbash on 2008-11-16
before exit.

asdhajsdhjashdjashdjasdhk
exit

---

### Post by sven_wien on 2008-11-16
bin bash thank you for all that i restart now and hope it works

---

### Post by binbash on 2008-11-16
> **sven_wien said:**
> bin bash thank you for all that i restart now and hope it works

if it doesnt work change rc.local script to : 



/usr/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

then reboot and try sound.

---

### Post by sven_wien on 2008-11-16
Its works perfectly!! many thanks binbash!

---

### Post by binbash on 2008-11-16
Mark the thread as solved please.

---

### Post by CJay554 on 2008-12-12
Another fix for the Acer 6920 sound problem is here:
[http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920+sound&page=3#26](http://ubuntuforums.org/showthread.php?t=921637&highlight=acer+6920+sound&page=3#26)

pretty much updating the ALSA driver to the newest one.

---

