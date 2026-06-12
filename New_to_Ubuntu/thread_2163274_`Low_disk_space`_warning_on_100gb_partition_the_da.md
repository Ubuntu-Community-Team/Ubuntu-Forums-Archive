---
title: "`Low disk space` warning on 100gb partition the day after I install Unbuntu"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by alphalvr on 2013-07-17
ok im running win 7 on a solid state 60gb drive with a 500gb hard drive for installs.
i decided to try ubuntu and shrank the hard drive partition from 500gb to 400gb to leave me 100gb of unallocated space.
i then booted from a usb stick with unbuntu 13 64bit on it and chose the win7 + ubuntu (alongside) option (it sort of took over from here never letting me choose what disk etc)
Anyway i boot up, i see grub, ubuntu boots up fine, i check win 7 and all seems fine so i start playing with my new toy.

i surfed net,watched youtube vids, played some music, played some video files, installed steam and everything seemed hunky dory. Then i was about to go to bed and web pages started taking forever to load and my mouse kept freezing for a few secs quite regulary and then it sorta froze while i was looking through steam client. my `number lock`  still functioned (slowly) so i figured it was busy, i had no idea how to shut it down safely so i just went to bed. (shortly after i could hear music from my headphones so i guess it unfroze)

i rebooted today and as i get into unbuntu i get a `low disk space` warning message. says i have 365mb of 100gb wtf

i looked into where unbuntu decided to install itself and it does seem to have created 2 partions in the 100gb of unallocted space, one about 90gb and the other about 10gb (swap file?)

my head is blown off, i have no idea what has happened.

ive read through posts, and i see commands to type into the alt/f2 thing but the only one that has seemed to work just did the same as me me viewing properties of the drive??

im finding the filesystem really confusing (to much win7) and this happening on my 1st day of unbuntu is really spoiling my fun :(

This space problem is making it hard to even post this, help please

---

### Post by grahammechanical on 2013-07-17
It is normal for the installer to create two partitions. One is for the OS the other is for swap. I do not know the default settings so I can not say if 10GB of swap is usual. How much RAM do you have?

You also have two Utilities that will give you some information, Disks and Disk Usage Analyser. You load them from the Dash. There is one thing that I think we need confirmation about. You say you chose Win7+Ubuntu option. Do you mean "Install alongside?" Or did you install Ubuntu from inside Windows using something called wubi.exe. Giving us clarity on how you installed will make a difference.

Regards.

---

### Post by Bashing-om on 2013-07-17
alphalvr; Hi ! Welcome to the forum .

Generally there exist three reasons for your situation ... 
a long time after install a build up of old kernels in the /boot partion;
/home directory filled up with many application installs;
run amuck logging due to a system problem requiring intervention.

I am going to assume the last scenerio ...so let us look at the folder containing your log files (/var).
Post the out put of Terminal commands (ctl+alt+t yields a terminal):
```

sudo du -h --max-depth=1 /var
sudo du -h --max-depth=1 /var/log/

```

[INDENT][INDENT]a tale in the telling
[/INDENT][/INDENT]

---

### Post by alphalvr on 2013-07-17
no i chose the `alongside` option and i have 8gb ram, i think the partition was 7.5gb iirc

---

### Post by alphalvr on 2013-07-17
omg ctrl/alt/t  damn i was using alt/f2  no wonder the commands did nothing, im such a nub :)

justin@Ubuntu-Phoenix:~$ sudo du -h --max-depth=1 /var
[sudo] password for justin: 
4.0K    /var/opt
200M    /var/lib
4.0K    /var/local
280M    /var/cache
4.0K    /var/metrics
4.0K    /var/tmp
60K    /var/spool
86G    /var/log
4.0K    /var/mail
2.1M    /var/backups
4.0K    /var/crash
86G    /var

justin@Ubuntu-Phoenix:~$ sudo du -h --max-depth=1 /var/log/
12K    /var/log/lightdm
104K    /var/log/apt
4.0K    /var/log/samba
4.0K    /var/log/dist-upgrade
4.0K    /var/log/unattended-upgrades
8.0K    /var/log/ConsoleKit
4.0K    /var/log/hp
12K    /var/log/fsck
116K    /var/log/upstart
4.0K    /var/log/speech-dispatcher
4.0K    /var/log/news
1.2M    /var/log/installer
16K    /var/log/cups
86G    /var/log/
justin@Ubuntu-Phoenix:~$

i guess `86G` next to `log` is a problem :)

---

### Post by Bashing-om on 2013-07-17
alphalvr;

Guess what... run amuck file... you get the fun now to determine what the system is screaming and hollering about.

And Hey,,, it is a new operating system, will take a bit to become comfortable with it !

Ok .. back to sloppyation at hand...with that great amount of a file... what I would do to get something we can handle, I would delete that file,,, run my system for a bit and look at the logs then.
For now let us see what file is so huge .. and prepare to delete it ... so the system can operate.

terminal code:
```
ls -la /var/log/
```
Will tell us a bunch.

[INDENT][INDENT]that is what I think, your opinion may vary[/INDENT][/INDENT]

---

### Post by alphalvr on 2013-07-17
i expected to have to play with it a bit....just not this soon ;p

```
justin@Ubuntu-Phoenix:~$ ls -la /var/log/
total 89305380
drwxr-xr-x 15 root              root        4096 Jul 17 23:29 .
drwxr-xr-x 13 root              root        4096 Jul 17 23:28 ..
-rw-r--r--  1 root              root       26144 Jul 17 01:18 alternatives.log
drwxr-xr-x  2 root              root        4096 Jul 16 23:47 apt
-rw-r-----  1 syslog            adm        22567 Jul 18 00:17 auth.log
-rw-r-----  1 root              adm           31 Apr 24 18:02 boot
-rw-r--r--  1 root              root        3024 Jul 17 23:29 boot.log
-rw-r--r--  1 root              root       51399 Apr 24 18:02 bootstrap.log
-rw-rw----  1 root              utmp           0 Apr 24 18:01 btmp
drwxr-xr-x  2 root              root        4096 Jul 16 23:52 ConsoleKit
drwxr-xr-x  2 root              root        4096 Jul 16 23:52 cups
drwxr-xr-x  2 root              root        4096 Apr 19 16:58 dist-upgrade
-rw-r-----  1 root              adm        64463 Jul 17 23:29 dmesg
-rw-r-----  1 root              adm        62983 Jul 17 15:02 dmesg.0
-rw-r-----  1 root              adm        16144 Jul 17 14:57 dmesg.1.gz
-rw-r-----  1 root              adm        17105 Jul 17 11:52 dmesg.2.gz
-rw-r-----  1 root              adm        16556 Jul 16 23:52 dmesg.3.gz
-rw-r-----  1 root              adm           59 Apr 24 18:02 dmesg.4.gz
-rw-r--r--  1 root              root     1105988 Jul 17 01:18 dpkg.log
-rw-r--r--  1 root              root       32032 Jul 16 23:47 faillog
-rw-r--r--  1 root              root        3248 Apr 24 18:04 fontconfig.log
drwxr-xr-x  2 root              root        4096 Apr 24 18:02 fsck
drwxr-xr-x  2 root              root        4096 Mar  9 07:46 hp
drwxr-xr-x  2 root              root        4096 Jul 16 23:51 installer
-rw-r-----  1 syslog            adm  45723151132 Jul 18 00:26 kern.log
-rw-rw-r--  1 root              utmp      292292 Jul 16 23:47 lastlog
drwxr-xr-x  2 root              root        4096 Jul 16 23:52 lightdm
-rw-r-----  1 syslog            adm            0 Jul 16 23:52 mail.err
-rw-r-----  1 syslog            adm            0 Jul 16 23:52 mail.log
drwxr-xr-x  2 root              root        4096 Jul 16 23:52 news
-rw-r--r--  1 root              root       22628 Jul 17 23:29 pm-powersave.log
drwxr-x---  2 root              adm         4096 Nov 26  2012 samba
drwx------  2 speech-dispatcher root        4096 Aug 21  2012 speech-dispatcher
-rw-r-----  1 syslog            adm  45723435994 Jul 18 00:26 syslog
-rw-r--r--  1 root              root      373662 Jul 17 23:29 udev
-rw-r-----  1 syslog            adm            0 Jul 16 23:52 ufw.log
drwxr-xr-x  2 root              root        4096 Jul 17 14:49 unattended-upgrades
drwxr-xr-x  2 root              root        4096 Jul 17 14:49 upstart
-rw-rw-r--  1 root              utmp       28032 Jul 17 23:54 wtmp
-rw-r--r--  1 root              root       59787 Jul 17 23:29 Xorg.0.log
-rw-r--r--  1 root              root       63459 Jul 17 23:28 Xorg.0.log.old
justin@Ubuntu-Phoenix:~$
```

---

### Post by deadflowr on 2013-07-17
You have two larger than normal logfile there.
The first is the kern.log logfile.
The second is the syslog logfile.

Normally, I'd suggest posting them, but alas, they are pretty big. 
So try posting the end with
```
tail -n 10 /var/log/kern.log
```
and 
```
tail -n 10 /var/log/syslog
```
Tail is the end of the file
the number 10, is the last ten lines in the file.
You can change the number from 10 to 1, or something else if you want.

When posting, please put the otuput in code tags.
(Code tags are the symbol # in the reply box toolbar)

---

### Post by alphalvr on 2013-07-17
lack of space is really a problem atm, keep having to reboot

justin@Ubuntu-Phoenix:~$ tail -n 10 /var/log/kern.log
Jul 18 00:49:28 Ubuntu-Phoenix kernel: [  126.067516] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 18 00:49:28 Ubuntu-Phoenix kernel: [  126.067518] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 18 00:49:28 Ubuntu-Phoenix kernel: [  126.067519] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 18 00:49:28 Ubuntu-Phoenix kernel: [  126.067521] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 18 00:49:29 Ubuntu-Phoenix kernel: [  127.338749] wlan0: authenticate with 10:c6:1f:47:f5:d8
Jul 18 00:49:29 Ubuntu-Phoenix kernel: [  127.358590] wlan0: send auth to 10:c6:1f:47:f5:d8 (try 1/3)
Jul 18 00:49:29 Ubuntu-Phoenix kernel: [  127.362033] wlan0: authenticated
Jul 18 00:49:29 Ubuntu-Phoenix kernel: [  127.362313] wlan0: associate with 10:c6:1f:47:f5:d8 (try 1/3)
Jul 18 00:49:29 Ubuntu-Phoenix kernel: [  127.365350] wlan0: RX AssocResp from 10:c6:1f:47:f5:d8 (capab=0x411 status=0 aid=3)
Jul 18 00:49:29 Ubuntu-Phoenix kernel: [  127.365476] wlan0: associated

justin@Ubuntu-Phoenix:~$ tail -n 10 /var/log/syslog
Jul 18 00:51:18 Ubuntu-Phoenix kernel: [  235.996573] wlan0: associate with 10:c6:1f:47:f5:d8 (try 1/3)
Jul 18 00:51:18 Ubuntu-Phoenix NetworkManager[1024]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 18 00:51:18 Ubuntu-Phoenix wpa_supplicant[1265]: wlan0: Associated with 10:c6:1f:47:f5:d8
Jul 18 00:51:18 Ubuntu-Phoenix kernel: [  236.005006] wlan0: RX AssocResp from 10:c6:1f:47:f5:d8 (capab=0x411 status=0 aid=3)
Jul 18 00:51:18 Ubuntu-Phoenix kernel: [  236.005130] wlan0: associated
Jul 18 00:51:18 Ubuntu-Phoenix NetworkManager[1024]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 18 00:51:18 Ubuntu-Phoenix NetworkManager[1024]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jul 18 00:51:18 Ubuntu-Phoenix wpa_supplicant[1265]: wlan0: WPA: Key negotiation completed with 10:c6:1f:47:f5:d8 [PTK=CCMP GTK=TKIP]
Jul 18 00:51:18 Ubuntu-Phoenix wpa_supplicant[1265]: wlan0: CTRL-EVENT-CONNECTED - Connection to 10:c6:1f:47:f5:d8 completed (reauth) [id=0 id_str=]
Jul 18 00:51:18 Ubuntu-Phoenix NetworkManager[1024]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed

ASUS PCE-N15 PCI-E adaptor is the wifi card im using

---

### Post by Bashing-om on 2013-07-17
alphalvr; Well well...
appears you installed something on the 17th... not happy at all..
Kern.log and dmesg are running away !
Let's get some operating room:
```

sudo rm /var/log/dmesg.2.gz
sudo rm /var/log/dmesg.3.gz
sudo rm /var/log/dmesg.4.gz

``` Those are old files and not needed at this time.
And as it appears a recent happening, let's do away with 1/2 of kern.log file:
```

gksudo gedit /var/log/kern.log

```
Now it may be that that file is way to big for the editor to handle...but if it does load up... delete the first half of that file, save and exit.
now in 12.04 is a log file viewer... makes life a lot simpler:
in dash's search box, type log viewer (best I recall .. not on 12.04 at this time so can not test) and the log viewer icon pops up... 
in the viewer take a look at the kern.log file.... what pops out at you as an error repeated over and over ?
That file is much to big to upload here to the forum... but the suspect portion, ya may upload for us to take a look at.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by alphalvr on 2013-07-17
on the 17th eh, well i only installed ubuntu 8 minutes before the 17th, so it took me less than 10 mins to bugger it :)

got to this bit - 

gksudo gedit /var/log/kern.log

it says its loading......been loading a while now and progress bar is maybe at 3/4%  it may be stuck, oh no i just saw movement, ill be patient.

---

### Post by steeldriver on 2013-07-17
Here's a one-liner I've used a few times - it tries to count any recurring messages (after stripping timestamps) in the given log file(s) and lists the 10 most frequent ones

```
tail -n 10000 /var/log/kern.log | sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' | sort | uniq -c | sort -hr | head -10
```

---

### Post by alphalvr on 2013-07-17
this thing is not very intresting, so far most of it says 

Kernel: [ 8159.644031] nouveau E[  PGRAPH][0000:01:00.0] TRAP CH 4 [0x000027fb87] 0x01000000

a line like that was mostly all i could see

oh and i think gedit just crashed, well it did.

---

### Post by alphalvr on 2013-07-17
im a bit stuck now, so i tried this line.....

justin@Ubuntu-Phoenix:~$ tail -n 10000 /var/log/kern.log | sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' | sort | uniq -c | sort -hr | head -10
      2 Jul 18 00:47:37 Ubuntu-Phoenix kernel: [    0.000000] No AGP bridge found
      2 Jul 18 00:47:37 Ubuntu-Phoenix kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
      2 Jul 17 23:28:59 Ubuntu-Phoenix kernel: [    0.000000] No AGP bridge found
      2 Jul 17 23:28:59 Ubuntu-Phoenix kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
      2 Jul 17 15:02:00 Ubuntu-Phoenix kernel: [    0.000000] No AGP bridge found
      2 Jul 17 15:02:00 Ubuntu-Phoenix kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
      2 Jul 17 14:57:08 Ubuntu-Phoenix kernel: [    0.000000] No AGP bridge found
      2 Jul 17 14:57:08 Ubuntu-Phoenix kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
      2 Jul 17 11:52:08 Ubuntu-Phoenix kernel: [    0.000000] No AGP bridge found
      2 Jul 17 11:52:08 Ubuntu-Phoenix kernel: [    0.000000] ACPI: Local APIC address 0xfee00000

---

### Post by alphalvr on 2013-07-17
im in the log viewer, i cant see how to look at the  kernel log, i see Xorg.0.log   syslog   mail.log   auth.log and dpkg.log, maybe its not right viewer, was only thing that came up.

---

### Post by steeldriver on 2013-07-17
Oops my apologies that was the wrong one-liner - try this one:

```
for log in /var/log/{dmesg,syslog,kern.log}; do echo "${log} :"; sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' ${log} | sort | uniq -c | sort -hr | head -10; done
```

---

### Post by Bashing-om on 2013-07-17
steeldriver; Hey old friend !

Recon we can just delete that huge kern.log file ? Will the file be regenerated if it were deleted... and look at the new file in a bit ??

edit: dmesg will in all likely hood tell us the same thing... and that file is a lot smaller (rolled over several times !)

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by alphalvr on 2013-07-17
justin@Ubuntu-Phoenix:~$ for log in /var/log/{dmesg,syslog,kern.log}; do echo "${log} :"; sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' ${log} | sort | uniq -c | sort -hr | head -10; done
/var/log/dmesg :
      6  ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20121018/psargs-359)
      4 .0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
      3  sd 6:0:0:0: [sdc] No Caching mode page present
      3  sd 6:0:0:0: [sdc] Assuming drive cache: write through
      3  ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
      3  ACPI: Dynamic OEM Table Load:
      3 .0: setting latency timer to 64
      3 .0
      2  xHCI xhci_check_bandwidth called for root hub
      2  xHCI xhci_add_endpoint called for root hub
/var/log/syslog :
      4  Ubuntu-Phoenix wpa_supplicant: wlan0: WPA: Key negotiation completed with 10:c6:1f:47:f5:d8 [PTK=CCMP GTK=TKIP]
      4  Ubuntu-Phoenix wpa_supplicant: wlan0: Trying to associate with 10:c6:1f:47:f5:d8 (SSID='BTHub3-2WNM' freq=2437 MHz)
      4  Ubuntu-Phoenix wpa_supplicant: wlan0: SME: Trying to authenticate with 10:c6:1f:47:f5:d8 (SSID='BTHub3-2WNM' freq=2437 MHz)
      4  Ubuntu-Phoenix wpa_supplicant: wlan0: CTRL-EVENT-DISCONNECTED bssid=10:c6:1f:47:f5:d8 reason=7
      4  Ubuntu-Phoenix wpa_supplicant: wlan0: CTRL-EVENT-CONNECTED - Connection to 10:c6:1f:47:f5:d8 completed (reauth) [id=0 id_str=]
      4  Ubuntu-Phoenix wpa_supplicant: wlan0: Associated with 10:c6:1f:47:f5:d8
      4  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: scanning -> authenticating
      4  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: disconnected -> scanning
      4  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: completed -> disconnected
      4  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: authenticating -> associating
/var/log/kern.log :
sort: write failed: /tmp/sortBQsKQa: No space left on device

i got a no disk space message so i rebooted and ran it again

justin@Ubuntu-Phoenix:~$ for log in /var/log/{dmesg,syslog,kern.log}; do echo "${log} :"; sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' ${log} | sort | uniq -c | sort -hr | head -10; done
/var/log/dmesg :
      6  ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20121018/psargs-359)
      4 .0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
      3  ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
      3  ACPI: Dynamic OEM Table Load:
      3 .0: setting latency timer to 64
      3 .0
      2  xHCI xhci_check_bandwidth called for root hub
      2  xHCI xhci_add_endpoint called for root hub
      2  system 00:04: [io  0xffff] has been reserved
      2  pci 0000:00:1c.6: PCI bridge to [bus 06]
/var/log/syslog :
      9  Ubuntu-Phoenix kernel:  cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
      8  Ubuntu-Phoenix wpa_supplicant: wlan0: WPA: Key negotiation completed with 10:c6:1f:47:f5:d8 [PTK=CCMP GTK=TKIP]
      8  Ubuntu-Phoenix wpa_supplicant: wlan0: Trying to associate with 10:c6:1f:47:f5:d8 (SSID='BTHub3-2WNM' freq=2437 MHz)
      8  Ubuntu-Phoenix wpa_supplicant: wlan0: SME: Trying to authenticate with 10:c6:1f:47:f5:d8 (SSID='BTHub3-2WNM' freq=2437 MHz)
      8  Ubuntu-Phoenix wpa_supplicant: wlan0: Associated with 10:c6:1f:47:f5:d8
      8  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: scanning -> authenticating
      8  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: authenticating -> associating
      8  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: associating -> associated
      8  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
      8  Ubuntu-Phoenix NetworkManager: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
/var/log/kern.log :
sort: write failed: /tmp/sortuUOALk: No space left on device

No space message again :(

thanks a million for the help btw

---

### Post by steeldriver on 2013-07-17
Well we don't seem to be doing very well here - it looks like the kern.log is the problem, however you don't have enough space to run the command

You could try just performing the command on a chunk of the file e.g.

```
[COLOR=#0000cd]tail -n 100000 /var/log/kern.log[/COLOR] | sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' | sort | uniq -c | sort -hr | head -10
```

If you still get the 'sort: write failed' message then reduce the number after the -n some more e.g. 'tail -n 10000'

---

### Post by Bashing-om on 2013-07-17
alphalvr;

I do not see enough there to pin point any particular....

Log file viewer: there is a procedure in the utility to add files to the viewer, But, been a while since I was there, and I do not recall how, off the top of my head. I added it and as I recall the directions to do so are rather cryptic and sparse. But can be done !
Might do this:
```
less /var/log/dmesg
```

Yet another great file utility... "q" to quit the utility.
terminal command:
```
man less
``` will tell ya all ya want to know about it.

[INDENT][INDENT]meanwhile, back at the ranch
[/INDENT][/INDENT]

---

### Post by alphalvr on 2013-07-17
justin@Ubuntu-Phoenix:~$ tail -n 100000 /var/log/kern.log | sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' | sort | uniq -c | sort -hr | head -10
  93563 .0] TRAP ch 4 [0x000027fb87] 0x01000000
     54  Ubuntu-Phoenix kernel:  cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
     48  Ubuntu-Phoenix kernel:  wlan0: send auth to 10:c6:1f:47:f5:d8 (try 1/3)
     48  Ubuntu-Phoenix kernel:  wlan0: RX AssocResp from 10:c6:1f:47:f5:d8 (capab=0x411 status=0 aid=3)
     48  Ubuntu-Phoenix kernel:  wlan0: authenticate with 10:c6:1f:47:f5:d8
     48  Ubuntu-Phoenix kernel:  wlan0: authenticated
     48  Ubuntu-Phoenix kernel:  wlan0: associate with 10:c6:1f:47:f5:d8 (try 1/3)
     48  Ubuntu-Phoenix kernel:  wlan0: associated
     48  Ubuntu-Phoenix kernel:  cfg80211: World regulatory domain updated:
     48  Ubuntu-Phoenix kernel:  cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
justin@Ubuntu-Phoenix:~$ 


no space message yet but it is usually delayed a bit.

seems ok so i added another 0

justin@Ubuntu-Phoenix:~$ tail -n 1000000 /var/log/kern.log | sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' | sort | uniq -c | sort -hr | head -10
 993541 .0] TRAP ch 4 [0x000027fb87] 0x01000000
     55  Ubuntu-Phoenix kernel:  cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
     49  Ubuntu-Phoenix kernel:  wlan0: send auth to 10:c6:1f:47:f5:d8 (try 1/3)
     49  Ubuntu-Phoenix kernel:  wlan0: RX AssocResp from 10:c6:1f:47:f5:d8 (capab=0x411 status=0 aid=3)
     49  Ubuntu-Phoenix kernel:  wlan0: authenticate with 10:c6:1f:47:f5:d8
     49  Ubuntu-Phoenix kernel:  wlan0: authenticated
     49  Ubuntu-Phoenix kernel:  wlan0: associate with 10:c6:1f:47:f5:d8 (try 1/3)
     49  Ubuntu-Phoenix kernel:  wlan0: associated
     49  Ubuntu-Phoenix kernel:  cfg80211: World regulatory domain updated:
     49  Ubuntu-Phoenix kernel:  cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

then i tried it again with 2 extra 0`s but space message came up

---

### Post by steeldriver on 2013-07-17
so it looks like the 'TRAP ch4' message is what's filling up the log - google says it may be some kind of nouveau (graphics driver) bug - possibly related to suspend/resume?

[http://www.mail-archive.com/nouveau@lists.freedesktop.org/msg10851.html](http://www.mail-archive.com/nouveau@lists.freedesktop.org/msg10851.html)

---

### Post by alphalvr on 2013-07-18
does that mean im buggered??

i tried to be smart as id seen some choices for graphics drivers in the options somewhere and changed driver to nvidia/tested driver, i rebooted and now i cant get into linux.
 
i get a box saying that my screens etc could not be be recognised and need configuring.
 
i choose the run low graphics option and i just get black screen with cursor flashing (top left)

my graphics card is a EVGA GTX 660 2GB superclocked

i started trying to boot into a safe mode (grub advanced section???) to try and change driver, but not knowing what im doing is what got me here and im losing heart rapidly, i quit and booted windows for a bit.

any ideas? how i get unbuntu back?

thks

---

### Post by dannyboy79 on 2013-07-18
im guessing your ~/.xsession-errors is the log file that is taking all your space with a stupid warning. as far as getting back into ubuntu, can you hit ctrl-alt-f1 and login textually? then you could uninstall any nvidia drivers with 
sudo apt-get remove --purge nvidia-current

---

### Post by alphalvr on 2013-07-18
i didnt know when you wanted me to press ctrl-alt-f1 so i just tapped it continually through the entire boot process.

nothing changed, i still got the graphics could not be setup warning box, i have tried all the options it gives, i always end up on black screen with flashing cursor (top left)

---

### Post by steeldriver on 2013-07-18
You can try pressing Ctrl-Alt-F1 now - it *may* get you to a command line 'virtual terminal' - if not you will need to reboot and then when you get to the grub menu screen choose 'recovery' mode (that's a step below 'low graphics' - basically it's a true command line interface, but we should be able to repair from there)

---

### Post by alphalvr on 2013-07-18
it didnt, i tried it :(

where do u see this recovery mode? advanced ubuntu setting in grub, where there are 4 options, 2 say recovery?

---

### Post by steeldriver on 2013-07-18
That sounds like the newer grub menu (with the 'advanced' option) - I'm not familiar with the details of that, sorry

If the 'advanced' menu is just offering you different kernel versions, then select the newest one (this will be the one you just broke)

Alternatively you may be able to simply boot into a previous (unbroken) kernel from the regular menu, not the advanced menu

---

### Post by alphalvr on 2013-07-18
ok your losing me, my grub has 5 options

ubuntu
2 x memtest
advanced
win7

ubuntu doesnt work so i go to advanced

in there are 4 options, kernels i think, 2 sets with a a recovery option for each

looks something like this

kernel 757758
kernel 757758 (recovery)
kernel 757754
kernel 757754 (recovery)

all from memory so .....

think i tried booting with those, so if your going to say `try booting with kernel 757758` ill say i think it does same as ubuntu on main screen, but ill check.

ok, i tried latest (not recovery version) exactly the same as booting with ubuntu from main grub screen

then i tried recovery version, (newest) it gives some options, i picked the option that said something about graphics, same result.

---

### Post by dannyboy79 on 2013-07-18
edit your boot line by hitting "e" when on top of the ubuntu line, then change "quiet splash" WITH "noapic". let's see what that does

---

### Post by alphalvr on 2013-07-18
ok i think i did it right, deleted the two words, replaced with `noapic`then pressed f10

same boot up as always apart from i could see stuff (writing) scrolling up the screen when first activated, eventually i see a blink of a nvidia logo followed by the the warning window....all options i select lead to black screen with flashing cursor (top left)

could it be be my lack of space on the drive is the problem causing the nvidia driver to fail?? i mean it was hard to even post on this forum before i switched the driver and killed it dead.

---

### Post by steeldriver on 2013-07-18
Yes that could be part of the problem - if you boot into recovery mode you should be able to delete the kern.log

---

### Post by alphalvr on 2013-07-18
ok i went to advanced in grub then selected - ubuntu with linux 3.8.0-26 generic (recovery)

i come to a menu, the choices are-

resume / clean / dpkg / failsafex / fsck / grub / network / root / sys summary

i tried clean as i was there, it resulted in 
0 upgraded
0 newly installed
0 to remove
134 not upgraded

help :)

---

### Post by Boab1993 on 2013-07-18
Just from my own personal experience i think you need to re-install linux if you just want a quick fix, 10gb is far to large for a swap, so i think there has been an error while installing.
If you go back onto your live install CD you can edit existing partitions on your computer, reformat the offending partitions.
You can also merge existing partitions, but requires re-formating so you would lose the data on the partition. 
You can also edit the linux partition while on windows, i use a program called 'Gparted' you can download it from sourceforge. 

Hope that helps

---

### Post by dannyboy79 on 2013-07-18
boot into failsafex

---

### Post by alphalvr on 2013-07-18
well i think it was 7.5gb not 10, id have to check, and as i had 8gb of ram i figured that was why it was that size?

---

### Post by Boab1993 on 2013-07-18
You actually need less space on your swap, the larger your RAM, it is only required when you run out of physical memory, or certain blocks of contiguous memory need to be allocated to a program. Which is less likely to happen when you have more RAM. It is usually around about 1 or 2 GB as far as i know.

---

### Post by dannyboy79 on 2013-07-18
swap can be turned off, made smaller and then re-enabled at any time. that's not really the issue at hand. boot into failsafex so you can delete your huge log file and fix your GFX driver issue.

---

### Post by Boab1993 on 2013-07-18
I know i was just replying to him.
My original point was considering the original post about his 100GB partition coming up with low disk space warning.
I agree with you about booting into failsafex, i was just giving my suggestion of simple reformatting the 100GB so that he can have it as unallocated, as he originally wished.

Apologies if i got the wrong end of the stick in this one.

---

### Post by alphalvr on 2013-07-18
failsafex doesnt work, ivealready tried it a couple of times but ill just nip and do it once more to be sure.
iirc it just does the same as loading ubuntu

ok i ran the newest recovery option, chose failsafex, results in a message box saying graphics could not be configured correctly

several options to choose but its same menu as i always see and i tried them all, like `configure now` doesnt do anything 

i have to start with default settings and it results in black screen with cursor flashing (top left)

---

### Post by alphalvr on 2013-07-18
> **Boab1993 said:**
> I know i was just replying to him.
My original point was considering the original post about his 100GB partition coming up with low disk space warning.
I agree with you about booting into failsafex, i was just giving my suggestion of simple reformatting the 100GB so that he can have it as unallocated, as he originally wished.

Apologies if i got the wrong end of the stick in this one.

no i just created the 100gb unallocated space to put ubuntu in, not really bothered how it does it. my original plan was a 100gb drive ill see easy in options so easy to select, also pretty much all id need i figured while getting to grips with it.

it turned out i didnt get to choose where.....but ubuntu seems to have chosen that space for itself anyway so imo that bit went just fine (at the moment anything positive is a good thing)

anyway as i say failsafex just boots the same as booting ubuntu

thanks, ill try anything atm, had ubuntu for two and a half days, its only worked (sorta) for about 2 hours :(

---

### Post by Boab1993 on 2013-07-18
Ahhh okay, well you can choose where it goes on the install but you have to go for custom/advanced install, but you have to create your own ext2, ext4, swap etc, so make sure you know what your doing.

Good Luck Sir, you'll learn alot

---

### Post by dannyboy79 on 2013-07-18
try to change your boot line and add "nomodeset noapic" and see if that boots

---

### Post by alphalvr on 2013-07-18
im afraid i get same resultwall of text, followed by nvidia splash for a microsecond and then a warning about graphics not configured right, selecting the use basic settings results in the black screen with flashing cursor.i did want to say i see something as it boots saying `kvm disabled in bios` vm? video memory?  anyway just thought id better mention it although it has said that ever since i originally installed ubuntu.

---

### Post by dannyboy79 on 2013-07-18
can you try to go to recovery and choose root this time. that should get you to the command line, then you can remove nvidia-current

---

### Post by alphalvr on 2013-07-18
ok im at  the command line, 

feels like im moving forward, so what do i do with it?  :)

i found this line on one of your previous posts 

[COLOR=#000000]sudo apt-get remove --purge nvidia-current

i tried that and.....

W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to /var/cache/apt
E: the package lists or status file could not be parsed or opened[/COLOR]

---

### Post by alphalvr on 2013-07-20
anyone know why this command failed, id like to give this 1 more shot now i have a little time over weekend.

thanks for the help so far.

---

### Post by steeldriver on 2013-07-20
Hi again

When you drop to the 'Root Shell' option in recovery mode, the filesystem gets mounted read-only - so before you can make any actual changes you will need to remount it:

```
# mount -o remount,rw /
```

Note there is space between the rw option and the / (root mount point), but NOT between the two options remount,rw

It's possible that the huge kern.log file got rotated out or deleted already, but before even trying to fix the graphics driver, I'd suggest making sure you have some free space

```
# df -h
```

If it's still 100% used (or close to) then 

```
# ls -l /var/log
```

and if necessary delete the kern.log

```
# rm /var/log/kern.log
```

(or if the HUGE kern.log has got rotated out, you may have a HUGE kern.log.1 or SEMI HUGE kern.log.2.gz etc files, if so delete those instead)

Good luck and post back to let us know how it goes

---

### Post by alphalvr on 2013-07-20
Ladies and gentlemen, `kern.log` has left the building \o/

ok that freed up 48gb which is plently for  the moment but it said sys.log was the same size

ok im ready, hit me :)

shall i try the remove driver command again?

WAIT - it seems the lack of space was causing the driver problem, im straight into ubuntu without the kern.log

ok what shall i do now??  thanks a lot guys

---

### Post by steeldriver on 2013-07-20
OK that's good - for now 

It's possible that the graphics driver update you did has fixed the original TRAP error - but in case it hasn't, keep and eye on the log(s) size(s) and if they start to grow again we will have to investigate further

---

### Post by Damien_Cross on 2013-08-02
I'm having the same issue. The computer tells me that I have 800MBs left but when I allowed the System Allocation (sorry I'm not completely new to Ubuntu I'm just having a hell of a spot with this version *12.04.1*) to run it completely freezes or it takes forever to load and it looks like it's all on the Windows 7 side. Thing is, Lucid Lynx ran smoothly without a single issue alongside Windows but I did go into the terminal and this is what pulled up...nothing over a gig at all. 

```
umbrellacorp@ubuntu:~$ sudo du -h --max-depth=1 /var
[sudo] password for umbrellacorp: 
14M    /var/log
8.0K    /var/www
4.0K    /var/local
412K    /var/tmp
4.0K    /var/games
68K    /var/spool
4.0K    /var/opt
4.0K    /var/crash
4.0K    /var/mail
435M    /var/lib
6.0M    /var/backups
338M    /var/cache
792M    /var

umbrellacorp@ubuntu:~$ sudo du -h --max-depth=1 /var/log/
24K    /var/log/apache2
692K    /var/log/apt
8.0K    /var/log/dbconfig-common
4.0K    /var/log/mythtv
1.3M    /var/log/installer
4.0K    /var/log/samba
36K    /var/log/lightdm
2.1M    /var/log/dist-upgrade
4.0K    /var/log/unattended-upgrades
4.0K    /var/log/speech-dispatcher
84K    /var/log/ConsoleKit
48K    /var/log/mysql
488K    /var/log/upstart
112K    /var/log/gdm
4.0K    /var/log/apparmor
72K    /var/log/cups
12K    /var/log/fsck
4.0K    /var/log/hp
4.0K    /var/log/news
14M    /var/log/
umbrellacorp@ubuntu:~$ 
```

So where is the problem and how can I fix it? Some info on the system. It's a quad core AMD Phenom 9750 processor with 8GB of RAM and a 750 GB Hard drive of which over 500 GB is free. Perhaps it got partitioned wrong?

---

### Post by Bashing-om on 2013-08-02
Damien_Cross; Hi ! Again ...

I see nothing amiss in /var ... if indeed you are again low on disk space... lets look at another situational issue... possible that the /boot partition is full ..
fresh(er) install not to likely;
```

sudo du -h --max-depth=1 /boot
ls -la /boot

```

Quite an impressive little system ... if you are concerned with the partitioning the best tool for a looksee is "GParted" ...
Fire up the liveDVD and Gparted is available,,, from the dash search box type "gparted" -> icon; Look but do not touch 'till you KNOW what you are doing.
Quick looksee from the command line:
```

df -h

```

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by Damien_Cross on 2013-08-02
Okay checking the boot partition this is what comes up. Appreciate the advice so far. 
```
umbrellacorp@ubuntu:~$ sudo du -h --max-depth=1 /boot
[sudo] password for umbrellacorp: 
4.3M    /boot/grub
33M    /boot
umbrellacorp@ubuntu:~$ ls -la /boot
total 28672
drwxr-xr-x  3 root root     4096 Jul 14 16:23 .
drwxr-xr-x 26 root root     4096 Jul 14 16:23 ..
-rw-r--r--  1 root root   795365 Jun 18 14:20 abi-3.2.0-49-generic
-rw-r--r--  1 root root   140622 Jun 18 14:20 config-3.2.0-49-generic
drwxr-xr-x  3 root root    12288 Jul 14 16:23 grub
-rw-r--r--  1 root root 20159247 Jul 14 10:43 initrd.img-3.2.0-49-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2893287 Jun 18 14:20 System.map-3.2.0-49-generic
-rw-------  1 root root  4978416 Jun 18 14:20 vmlinuz-3.2.0-49-generic
umbrellacorp@ubuntu:~$ ^C
umbrellacorp@ubuntu:~$
```

---

### Post by steeldriver on 2013-08-02
You could also do something like

```

sudo find / -type f -size +1G -exec du -h {} \; 2>/dev/null | sort -hr | head -n 10

```

which will search the whole filesystem for files bigger than 1G and then sort them and print the 10 largest ones (you can adjust the '1G' and the '-n 10' if that's not granular enough) - you can exclude mounted filesystems with '-xdev' or a suitable '-prune' if you have a more complicated multi-partition filesystem

It would also be useful if you posted the outputs of

```
df -h
```

and

```
df -hi
```

---

### Post by Bashing-om on 2013-08-02
+1+1
as nothing seen amiss in /boot.

edit: Teach me not to read the thread... Damien_Cross, I apologize. I had you confused with the originator of this thread.
So allow me this opportunity to welcome you to the forum ... in  a formal type introduction ! We will work to find the cause and offer a solution...

Comply with the aboves ... and what will be will be

---

### Post by Damien_Cross on 2013-08-02
sorry this thing took awhile so while it was thinking about it I decided to play a round of Tetris on my DS. Still can't beat that High Score of mine but here ya go. 

```
umbrellacorp@ubuntu:~$ sudo find / -type f -size +1G -exec du -h {} \; 2>/dev/null | sort -hr | head -n 10
[sudo] password for umbrellacorp: 
17G    /host/ubuntu/disks/root.disk
7.8G    /host/pagefile.sys
5.9G    /host/hiberfil.sys
4.4G    /host/System Volume Information/{b243842b-f913-11e2-808a-002618339c08}{3808876b-c176-4e48-b7ae-04046e6cc752}
2.4G    /host/Users/Umbrella Corp/Desktop/Photos/107___11/MVI_0641.MOV
2.2G    /home/umbrellacorp/Desktop/State_Of_Mind_Film_HD.mp4
2.0G    /host/Users/Umbrella Corp/Desktop/Photos/107___11/MVI_0642.MOV
2.0G    /host/System Volume Information/{c01dcb0c-f792-11e2-a1b2-002618339c08}{3808876b-c176-4e48-b7ae-04046e6cc752}
1.9G    /host/System Volume Information/{b5deb065-f58d-11e2-bace-002618339c08}{3808876b-c176-4e48-b7ae-04046e6cc752}
1.7G    /host/System Volume Information/{928c077f-f4a4-11e2-ad57-002618339c08}{3808876b-c176-4e48-b7ae-04046e6cc752}
umbrellacorp@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   15G 1018M  94% /
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           1.6G  904K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  152K  3.8G   1% /run/shm
/dev/sda1       685G  183G  502G  27% /host
umbrellacorp@ubuntu:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/loop0       1.1M  328K  721K   32% /
udev             956K   557  956K    1% /dev
tmpfs            967K   476  967K    1% /run
none             967K     2  967K    1% /run/lock
none             967K     6  967K    1% /run/shm
/dev/sda1        503M  596K  502M    1% /host
umbrellacorp@ubuntu:~$
```

---

### Post by Bashing-om on 2013-08-02
Damien_Cross; Hey ..

see my last post for my apology..
Well the problem sticks out like a sore thumb... but sure throwing me for a loop presently ...

How is "/host/XXXXX" and  "/dev/loop0 17G 15G 1018M 94% /" related ... where in the world did they come from ?
Let's see:
```

sudo fdisk -lu
blkid
cat /etc/fstab
mount

``` shows disk(s) layout, UUID assignments and what is mounted to the file system where.
Once this is known, we can look at what is generating all those text files ... and why !

[INDENT][INDENT]it's a process, but why and how
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-08-02
Bashing, I think that just indicates that it's a wubi install, no? All the /host stuff is the parent Windows filesystem (except for the root.disk obviously, which corresponds to the /dev/loop Ubuntu virtual disk)

---

### Post by Petro Dawg on 2013-08-02
Never mind, I see where OP freed up some space a while ago now.

---

### Post by Bashing-om on 2013-08-02
@ steeldriver... yeah .. that do make sense.. So we are looking at:
A file (ubuntu virtual file system) within Windows system no longer large enough to accommodate ubuntu ?
OR Windows' Partition is out of space - as ubuntu's virtuallity is of dedicated size within Windows ??
Is Windows screaming and hollering ?

Once more Windows -> WUBI ... and I am out of my depth...I would have to struggle to get through this.

[INDENT][INDENT]this too we will get through[/INDENT][/INDENT]

---

### Post by Damien_Cross on 2013-08-03
Alright everyone here you go...Bashing, no apology needed I'm just really appreciative for all the help you guys put in here. Thanks again. Happy to go through the process just to understand what went wrong here. 10.01 worked really well and smooth and then this one just sorta went nuts on me and I have been unable to figure out why though I love Ubuntu more than Windows for it's privacy protections. Sorry...digressing. Here you go!

```
umbrellacorp@ubuntu:~$ sudo fdisk -lu
[sudo] password for umbrellacorp: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1436082479   718041208+   7  HPFS/NTFS/exFAT
/dev/sda2      1436082480  1465144064    14530792+   7  HPFS/NTFS/exFAT
umbrellacorp@ubuntu:~$ blkid
umbrellacorp@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
umbrellacorp@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/umbrellacorp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=umbrellacorp)
umbrellacorp@ubuntu:~$
```

---

### Post by steeldriver on 2013-08-03
I don't really see any red flags - you appear to have a fairly normal wubi install with a 17G virtual disk, of which 15G is currently used - but only one single file in the 'top ten' (although the host filesystem confused the results), i.e.

```
2.2G    /home/umbrellacorp/Desktop/State_Of_Mind_Film_HD.mp4
```

So it's possible you just have a bunch of small 'stuff' that's filling up the space - I'd start by doing a bit of house cleaning of the package management system e.g.

```

sudo apt-get autoremove

sudo apt-get clean

```

and then run df -h again to see how it looks - if there are still space issues, run the 'find' command again with a smaller size threshold (and let's ignore the /host dir this time, now that we know we're dealing with wubi) e.g.

```

sudo find / **-path '/host' -prune** -o -type f **-size +100M** -exec du -h {} \; 2>/dev/null | sort -hr | head **-n 25**

```

---

### Post by Damien_Cross on 2013-08-03
> **steeldriver said:**
> I don't really see any red flags - you appear to have a fairly normal wubi install with a 17G virtual disk, of which 15G is currently used - but only one single file in the 'top ten' (although the host filesystem confused the results), i.e.

```
2.2G    /home/umbrellacorp/Desktop/State_Of_Mind_Film_HD.mp4
```

So it's possible you just have a bunch of small 'stuff' that's filling up the space - I'd start by doing a bit of house cleaning of the package management system e.g.

```

sudo apt-get autoremove

sudo apt-get clean

```

and then run df -h again to see how it looks - if there are still space issues, run the 'find' command again with a smaller size threshold (and let's ignore the /host dir this time, now that we know we're dealing with wubi) e.g.

```

sudo find / **-path '/host' -prune** -o -type f **-size +100M** -exec du -h {} \; 2>/dev/null | sort -hr | head **-n 25**

```

I do have two file folders marked Songs of Anarchy (Sons of Anarchy Soundtrack...highly recommended music) and of course my newest addition State of Mind for my Conspiracy Theory File (because hey, these things are just interesting as hell to me) but you think it might be that that's causing it? Hell if that's the case I'll slap those things onto a flash drive kick them off my hard drive and call it a day but I didn't know that so little would cause a space issue. So the partition itself is only 17 GB with 15GB used? If that's the case it wouldn't surprise me but I'll do this a little later. Right now I'm modding my phone on my windows side.

I'll post my results coming up. Wonder if there's any way to kick out some more space on that partition...

---

### Post by Werne on 2013-08-04
> **Damien_Cross said:**
> Wonder if there's any way to kick out some more space on that partition...
Maybe, 17G isn't much when when putting everything on it, especially home (it's why I always separate /home from the rest) but I believe you might be able to squeeze something out of it. Post the output of the following first, then we can see what takes up space:
```
cd / && sudo du -h --max-depth=1 ./ 2>/dev/null | sort -rh
```

---

### Post by Damien_Cross on 2013-08-04
Okay so here's what we got. 


```
umbrellacorp@ubuntu:~$ sudo apt-get autoremove
[sudo] password for umbrellacorp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.
umbrellacorp@ubuntu:~$ sudo apt-get clean
```

Right after I did Sudo Apt-Get Clean it didn't do anything at all. Moved on to part two...

```
umbrellacorp@ubuntu:~$ sudo find / -path '/host' -prune -o -type f -size +100M -exec du -h {} \; 2>/dev/null | sort -hr | head -n 25
2.2G    /media/A245-CAF9/State_Of_Mind_Film_HD.mp4
2.2G    /home/umbrellacorp/.local/share/Trash/files/State_Of_Mind_Film_HD.mp4
617M    /home/umbrellacorp/Downloads/root66_ATT_I747UCDLK3.7z
499M    /usr/share/games/nexuiz/data/textures.pk3
265M    /usr/share/games/nexuiz/data/data.pk3
211M    /media/A245-CAF9/audrey_bitoni_pics.zip
176M    /home/umbrellacorp/Dropbox/Jane's Stuff/CIU5/ciu052.wmv
156M    /media/A245-CAF9/dylan_ryder_pics.zip
114M    /home/umbrellacorp/Downloads/FiveYearsofStories.mobi
103M    /home/umbrellacorp/.secondlife/cache_sg1/data.db2.x.1
0    /sys/devices/pci0000:00/0000:00:0b.0/0000:02:00.0/resource1_wc
0    /sys/devices/pci0000:00/0000:00:0b.0/0000:02:00.0/resource1
0    /proc/kcore
```

There's where that movie popped up. Okay a little odd because I'd just trashed it but there I see it in the trash so I emptied it out and tried it again

```
umbrellacorp@ubuntu:~$ sudo find / -path '/host' -prune -o -type f -size +100M -exec du -h {} \; 2>/dev/null | sort -hr | head -n 25
2.2G    /media/A245-CAF9/State_Of_Mind_Film_HD.mp4
617M    /home/umbrellacorp/Downloads/root66_ATT_I747UCDLK3.7z
499M    /usr/share/games/nexuiz/data/textures.pk3
265M    /usr/share/games/nexuiz/data/data.pk3
211M    /media/A245-CAF9/audrey_bitoni_pics.zip
176M    /home/umbrellacorp/Dropbox/Jane's Stuff/CIU5/ciu052.wmv
156M    /media/A245-CAF9/dylan_ryder_pics.zip
114M    /home/umbrellacorp/Downloads/FiveYearsofStories.mobi
103M    /home/umbrellacorp/.secondlife/cache_sg1/data.db2.x.1
0    /sys/devices/pci0000:00/0000:00:0b.0/0000:02:00.0/resource1_wc
0    /sys/devices/pci0000:00/0000:00:0b.0/0000:02:00.0/resource1
0    /proc/kcore
```

Now that it's gone from the computer but the oddball thing is it was still popping up. I pulled the flash drive out of my computer and ran it again...

```
umbrellacorp@ubuntu:~$ sudo find / -path '/host' -prune -o -type f -size +100M -exec du -h {} \; 2>/dev/null | sort -hr | head -n 25
617M    /home/umbrellacorp/Downloads/root66_ATT_I747UCDLK3.7z
499M    /usr/share/games/nexuiz/data/textures.pk3
265M    /usr/share/games/nexuiz/data/data.pk3
176M    /home/umbrellacorp/Dropbox/Jane's Stuff/CIU5/ciu052.wmv
114M    /home/umbrellacorp/Downloads/FiveYearsofStories.mobi
103M    /home/umbrellacorp/.secondlife/cache_sg1/data.db2.x.1
0    /sys/devices/pci0000:00/0000:00:0b.0/0000:02:00.0/resource1_wc
0    /sys/devices/pci0000:00/0000:00:0b.0/0000:02:00.0/resource1
0    /proc/kcore
```

That seems to have done it. Ignore the top file. That was what I was going to use to root my phone but the computer kept lagging hardcore so I popped over to the Windows side and did it there.

---

### Post by steeldriver on 2013-08-04
Well, files in mounted external devices like your USB device mounted in /media shouldn't count towards the usage of the parent filesystem - so regardless of whether it's plugged in or not you have only found a total of about 2GB of 'real' usage there

What does df -h say now?

---

### Post by Damien_Cross on 2013-08-04
> **steeldriver said:**
> Well, files in mounted external devices like your USB device mounted in /media shouldn't count towards the usage of the parent filesystem - so regardless of whether it's plugged in or not you have only found a total of about 2GB of 'real' usage there

What does df -h say now?

Here we are. I used to get the disk error message just after booting up now I'm not but from what I'm gathering from you gnarly people the computer decided to allocate as little space to Ubuntu as possible and just shoehorned it in

```
umbrellacorp@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   13G  2.4G  85% /
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           1.6G  900K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  152K  3.8G   1% /run/shm
/dev/sda1       685G  185G  501G  27% /host
umbrellacorp@ubuntu:~$
```

---

### Post by Bashing-om on 2013-08-04
Damien_Cross & steeldriver;

I can appreciate all the effort that steeldriver has invested in getting you to this point as well making us understand the situation. 
Presently you are at 85% capacity ... and there is of course some more trimming you may do ... but is it not time to consider migrating the wubi to a true dual boot ? I have been looking about IRT expanding the wubi ... and the consentient is to migrate rather than expand.
See these for your consideration:
Original post from oldfred;
[http://ubuntuforums.org/archive/index.php/t-2141703.html](http://ubuntuforums.org/archive/index.php/t-2141703.html)
HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)


Resize wubi - bcbc
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)


The intent is to offer options, it is your system and only you know what is in your best interest.

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by Damien_Cross on 2013-08-04
> **Bashing-om said:**
> Damien_Cross & steeldriver;

I can appreciate all the effort that steeldriver has invested in getting you to this point as well making us understand the situation. 
Presently you are at 85% capacity ... and there is of course some more trimming you may do ... but is it not time to consider migrating the wubi to a true dual boot ? I have been looking about IRT expanding the wubi ... and the consentient is to migrate rather than expand.
See these for your consideration:
Original post from oldfred;
[http://ubuntuforums.org/archive/index.php/t-2141703.html](http://ubuntuforums.org/archive/index.php/t-2141703.html)
HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)


Resize wubi - bcbc
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)


The intent is to offer options, it is your system and only you know what is in your best interest.[INDENT][INDENT]just a thought
[/INDENT]
[/INDENT]


Bash you're absolutely right and what I had done, I had initially thought, was install a full on 64 bit dual boot. That's initially what I was aiming to do. I'd rather keep Windows around for a few things but as for Ubuntu, I'd like to make it my primary which I can do and have done. I just need to shake this low storage problem so I can fire it up and use it with total confidence. Too bad the WUBI didn't get that done for me. As I'd like to install it as a separate but equal OS that I can run as my primary which option would you recommend?

---

### Post by Bashing-om on 2013-08-04
Damien_Cross'

Mind you I have no experience at all with "wubi" ... but that said ... I highly suggest migrating the wubi install onto a hard disk partitition,
the second reference looks to be comprehensive. -> always back up your data prior to doing any major changes to the system ... hey power outages can happen at the worst of times ...fat fingering has left me with a bad day a time or two.
If it were me in your situation ... I would proceed as:
In Windows, defrag 2 times;
in Windows run chkdisk afterward 2 times;
in Windows (disk utility) resize windows to permit 50 GB unallocated space to move ubuntu as an "extended" partition onto; Within that "extended" partition, setting up -logical partitions-; 30 GB for ubuntu's "/" and say 2GB swap partitions (swap depends on how much ram you have and whether you "hibernate" the system)...and say 10 GB as a shared data partition... leave the remainder as "unallocated" for future expansion --- ie to again move /home at a later time as a separate partition if and when that should become needed ... 

Now at this point, I would boot up a liveDVD, and fire up GParted (partition editor) and look at what the hard disk looked like, making sure I know what partition was what and how these partitions were assigned ... as for example, the extended partition may be set to sda5 ... and in this "extended" partition are the logical partitions ... / (say sda6) and swap (say maybe like sda8) and "data" (say sda9). But do note the assignments so you can direct the install script what to install/where.

Then again in Windows run chkdisk.
At this time I would expect that I am prepared to proceed with the migration ... and I would avail myself of the ease of the script provided to install a basic fully functional ubuntu installation to do so.

May I say again ... we do not know what boot restrictions that may be  in place ... as in UEFI, ISRT, Rapid response, which none apply to a pre Windows7 system. But be prepared to fix the boot loader in any event. 

Did you back your data up ....keep in mind ... with the data backed up ... no matter what happens ... we can always resort to doing a clean install in the event there is a major problem . 

[INDENT][INDENT]care is no accident [/INDENT][/INDENT]

---

### Post by Damien_Cross on 2013-08-04
> **Bashing-om said:**
> Damien_Cross'

Mind you I have no experience at all with "wubi" ... but that said ... I highly suggest migrating the wubi install onto a hard disk partitition,
the second reference looks to be comprehensive. -> always back up your data prior to doing any major changes to the system ... hey power outages can happen at the worst of times ...fat fingering has left me with a bad day a time or two.
If it were me in your situation ... I would proceed as:
In Windows, defrag 2 times;
in Windows run chkdisk afterward 2 times;
in Windows (disk utility) resize windows to permit 50 GB unallocated space to move ubuntu as an "extended" partition onto; Within that "extended" partition, setting up -logical partitions-; 30 GB for ubuntu's "/" and say 2GB swap partitions (swap depends on how much ram you have and whether you "hibernate" the system)...and say 10 GB as a shared data partition... leave the remainder as "unallocated" for future expansion --- ie to again move /home at a later time as a separate partition if and when that should become needed ... 

Now at this point, I would boot up a liveDVD, and fire up GParted (partition editor) and look at what the hard disk looked like, making sure I know what partition was what and how these partitions were assigned ... as for example, the extended partition may be set to sda5 ... and in this "extended" partition are the logical partitions ... / (say sda6) and swap (say maybe like sda8) and "data" (say sda9). But do note the assignments so you can direct the install script what to install/where.

Then again in Windows run chkdisk.
At this time I would expect that I am prepared to proceed with the migration ... and I would avail myself of the ease of the script provided to install a basic fully functional ubuntu installation to do so.

May I say again ... we do not know what boot restrictions that may be  in place ... as in UEFI, ISRT, Rapid response, which none apply to a pre Windows7 system. But be prepared to fix the boot loader in any event. 

Did you back your data up ....keep in mind ... with the data backed up ... no matter what happens ... we can always resort to doing a clean install in the event there is a major problem . 
[INDENT][INDENT]care is no accident [/INDENT]
[/INDENT]


Well in that case let me ask you this. All the data that really makes any difference to me whatsoever is already on external drives and whatnot. I don't have anything on the Linux side stored in the way of photos, music, etc. Everything on my Ubuntu side is completely replaceable. Would it be easier/better to just wipe this part out and do a clean install?

---

### Post by Bashing-om on 2013-08-04
Damien_Cross; Hey ;
A clean install will be much faster and a whole lot easier ! 
(un-)install wubi from within Windows ->
boot the liveDVD -> install ubuntu -> choose the "install along side of" option -> 20 minutes later you are dual booting... the install wizard will take care of everything with but a very minimum of input from you (pay attention where the installer is going to install grub to ->sda).
Now this is "assuming" no boot code restrictions exist (UEFI, ISRT ect ect) ... then it is a walk in the park ... That install wizard is not only smart .. it is wonderful.
Later on will set up for a shared partition.

LiveDVD:
 download the desired .iso file (links at the top of the forum);
Verify the .iso file:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn the .iso to a DVD as an image -lowest burn speed - !
Boot the liveDVD, at the purple splash screen press the shift key -> language screen; escape to accept default -> boot options screen -> "check disk for defects"
install ubuntu.

Takes about 30 minutes all told - with a decent 'net  connection; preferable, wired - ... over and done with -> ubuntu'n alla the way

---

### Post by Damien_Cross on 2013-08-04
> **Bashing-om said:**
> Damien_Cross; Hey ;
A clean install will be much faster and a whole lot easier ! 
(un-)install wubi from within Windows ->
boot the liveDVD -> install ubuntu -> choose the "install along side of" option -> 20 minutes later you are dual booting... the install wizard will take care of everything with but a very minimum of input from you (pay attention where the installer is going to install grub to ->sda).
Now this is "assuming" no boot code restrictions exist (UEFI, ISRT ect ect) ... then it is a walk in the park ... That install wizard is not only smart .. it is wonderful.
Later on will set up for a shared partition.

LiveDVD:
 download the desired .iso file (links at the top of the forum);
Verify the .iso file:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn the .iso to a DVD as an image -lowest burn speed - !
Boot the liveDVD, at the purple splash screen press the shift key -> language screen; escape to accept default -> boot options screen -> "check disk for defects"
install ubuntu.

Takes about 30 minutes all told - with a decent 'net  connection; preferable, wired - ... over and done with -> ubuntu'n alla the way


Sickness. Thanks Bash! Thanks again everyone for helping me spot this problem. I kept looking at the Disk Usage Analyzer scratching my head wondering how the bluest of blue hells I had so much disk space but it kept saying something different. Now...time to do this....

---

### Post by Bashing-om on 2013-08-04
Damien_Cross;
See ya in 45 minutes ( but hey, ya got any idea how many times, over the years I have done this) piece of cake !

[INDENT][INDENT]practice makes perfect
[/INDENT][/INDENT]

---

