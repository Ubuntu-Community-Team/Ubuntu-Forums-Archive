---
title: "Not Installing"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Cyan1 on 2008-04-29
I'm still trying to solve a problem that is now in the archive forum - as there doesn't seem to be much activity  in that forum, I hope folk don't mind me linking to it from here

[http://ubuntuforums.org/showthread.php?t=761906](http://ubuntuforums.org/showthread.php?t=761906)

I'm also in the process of Burning an 8.04 disc, am I likely to have the same problems?

---

### Post by Helios1276 on 2008-04-29
didn't read the link but the following works perfect for me everytime

1.download the iso

2.get Infra Recorder(sourceforge)

3.Burn it as an image, sloowly like around 8x / 4x.

4.Install

---

### Post by neurostu on 2008-04-29
I read most of that old post, but not all of it... but did you ever try an alternate install cd?

---

### Post by Cyan1 on 2008-04-29
This is a repeat of my final two messages - the result of trying to install using the Alternate CD

Thanks to Louieb and phidia for advice so far - not been able to carry it out until today - work and life getting in the way! - and this is still causing trouble.

I have 64Mb of RAM (or a base memory of 640k - which I presume is the same thing and an extended memory of 523264k - I presume that is the HDD)

I tried to carry out a memory test v1.70 - which failed at test 7 "random number sequence failed" and then a list of numbers which started
0000529f044 - 82.8mb
0000356e044 - 53.8mb
0000b03e044 - 176.8mb
0001b655044 - 438.3mb
and so on - too many to write them all down

I had one more go to install from the Live Cd (using OEM install) and it got as far as as 96% and the stopped saying
"Error installing oem-config subprocess post-installation script killed by signal (segmentation fault)

Error installing oem-config -gtk dependency problems - leaving unconfigured

An error occurred whilst installing package E:sub-process/user/bin dpkg returned an error code (1)

It then continued trying to install - and got to 103% (!) completely removed language-pack-bin - at which point it froze.

Trying today with the Alternate CD

The first attempt was going well until it got to 81% configuring yelp - at which point it froze (left it an hour but clearly nothing was happening)

Attempts 2 & 3 resulted in a "linux panic"

Attempt 4 - had a couple of errors but allowed me to go back a step and try again, until whilst installing the base system it froze at 66% python

Attempt 5 froze at 83% of installing base system

As my processor is an AMD I tried the Alternate AMD - the first attempt wanted a login and password - which I haven't got, the second took me to the first menu but then said "Your CPU does not support long mode. use a 32 bit distribution" - which I presume means that I'm right to stick with the i386

Another attempt stopped whilst partitioning - all blue screen and no text

Final attempt finished with the message "An error was returned whilst trying to install kernal into the target system kernal pack 'linux-generic' check lvar/log/syslog/ or see virtual console for the details

It took me back to install from menu but froze on 0%

So any ideas what is happening or what more I can do? - is the memory test showing there is a problem with RAM which is going to make installation impossible? My local computer shop says he will re-install the original Windows and clean everything up - if I can find it, but that was ME and I really don't want it

I can get a desktop with the Live CD - and looking at my files I can see that they look much the same as they did on 20 April - they are just dated 29 April - and the broken link vmlinuz 1.7MB link to unknown Modified 15 Oct 2007 is still at the bottom of the list

Re-reading phidia's last post I guess the next move might be the rescue a broken system option - but what am I looking for?

all advice gratefully received


Re: Not Installing - Kernel Panic
also wondering if there would be any benefit in reformating and starting on a clean HDD? - trouble is I've found the code for doing that on the warning about Malicious Commands to be Read but not Run!

but then I know have a Hard Drive with nothing much on it and no way of using it without an installed OS - so what would be the harm?

---

### Post by free2useemail on 2008-04-29
Well, go and order the free CD, it will work. If you burn an ISO too fast, it will not work. When burning an ISO, burn at the slowest speed possible. Also, use if you are using windows XP now, then use nero 8 to burn the ISO. Or just try Wubi, search Wubi and find out more. it will install Ubunti 8.04 without partition or burning an ISO!!!

---

### Post by Cyan1 on 2008-05-01
Bumping just in case there is anyone around with rather more constructive advice than "didn't read the link .. but it's easy" - if it was easy I wouldn't be asking for help.

I have also had a go with 8.04 but can't get it to LiveCD mode and install stops at a blank page with a pretty heron page - not tried the Alternate 8.04 CD yet because I suspect I need to sort out some more basic problems - perhaps memory, perhaps a  hard drive confused by too many attempts to install and the remnants of whatever Windows  has done to it - really want a Linux solution to be the answer for an oldish computer that is used for surfing, playing and occasional homework.

---

### Post by aberry5555 on 2008-05-01
If the memory test is failing then I suspect that this is your problem... Windows may have been mapping holes in  your memory and not using them, whereas ubuntu isn't, I'm not sure. You could search through your bios and see if there's anyway to use hardware memory hole mapping, if there is such a thing, I seem to remember seeing that in my bios somewhere... To be honest though you'd be better off getting new RAM as dodgy ram is never a good thing to work with.

If you're certain your ram is ok then I'll try to think of something but it seems very likely this is the problem to me.

<--EDIT--> Also you'll really struggle to run Ubuntu with 64 meg of ram... it may actually be running out of memory before it gets to install. In fact I'm not even sure it's possible to run the LiveCD with that little ram, are you sure you have that figure correct? PS the "640k" base memory is not the same as your installed DIMMS. If you can't see it in  your bios then maybe you should open up the case and have a look at the labels on the ram.

---

### Post by Cyan1 on 2008-05-01
This is going to sound really stupid to those of you that know what you are doing - but I'm getting very confused about all the different names I see for Memory

When I ran the Memory test it told me that memory was 512M

System Monitor says User Memory 171.8 MB of 503.8 MB
                    Used Swap 92.0kb of 855.0MB

and looking around I see that if I run
 cat /proc/cpuinfo - it tells me
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 6
model name      : AMD Athlon(tm) XP 2100+
stepping        : 2
cpu MHz         : 1742.375
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips        : 3487.65
clflush size    : 32

ubuntu@ubuntu:~$ cat /proc/meminfo
MemTotal:       515844 kB
MemFree:          5996 kB
Buffers:         63692 kB
Cached:         280476 kB
SwapCached:          0 kB
Active:         215188 kB
Inactive:       253780 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       515844 kB
LowFree:          5996 kB
SwapTotal:      875500 kB
SwapFree:       875396 kB
Dirty:               0 kB
Writeback:           0 kB
AnonPages:      124840 kB
Mapped:          51420 kB
Slab:            31876 kB
SReclaimable:    23668 kB
SUnreclaim:       8208 kB
PageTables:       1784 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1133420 kB
Committed_AS:   403716 kB
VmallocTotal:   507896 kB
VmallocUsed:      4396 kB
VmallocChunk:   503040 kB
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 252M   16M  237M   6% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 252M   16M  237M   6% /lib/modules/2.6.22-14-generic/volatile
varrun                252M   88K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   76K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
tmpfs                 252M   12K  252M   1% /tmp
ubuntu@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        515844     510132       5712          0      63748     280788
-/+ buffers/cache:     165596     350248
Swap:       875500        104     875396


Is any of that telling me how much RAM - or is it time to find a screw driver? 

Thanks
C

---

### Post by rubbermyroof on 2008-05-01
Hi, I've a problem which may or may not be related to the thread... and just to make it more interesting, it has several issues to it:
I had Gutsy Gibbon installed on its own partition, so that I could boot into that or Win2K pro, after the BIOS screen. I closed down Ubuntu many times when I wanted to go into Windows, before it had started up properly (I dodn't like the default boot being Ubuntu and had been meaning to get round to changing it, but never did). Now, Ubuntu refuses to run. It come up with various problems which it labels "fixed" one by one, then it loses interest and gives me the Black Screen of Death (I prefer the blue Windows one :))

I downloaded the Hopping Heron .iso (from Oxford Uni mirror)and burnt it to CD. It boots up OK but when I select the 'check the CD' type of option, it says that 1 file is not right. I've downloaded it from Italy (mirror) and again have the same problem.

Anyway, trying (using that slightly corrupted version) to install it, it gets as far as showing a progress bar but then loses interest and gives me a Black Screen of Death.

I need my Win 2K for business daily so can't do a Format over the whole lot, but would like to move over to the Adjectival Heron as soon as possible (there were a few issues with Gutsy that I couldn't get around, good as it was, and maybe they are resolved), so any help as to how to get it installed would be appreciated.

Note: It seemed to boot up from disk installed within Windows, so is there any way I can use that to fix the files/system of my properly installed Ubunu partition?

Cheers, Jules the rubber roofer

---

### Post by aberry5555 on 2008-05-06
Cyan1: It seems to me you've got 512mb of ram, of which 503 is available to the OS. This is probably due to an on-board graphics chip stealing some memory to run the desktop and isn't a problem.

---

### Post by Cyan1 on 2008-05-09
This problem is now solved - it was very simple - I didn't have enough memory - although one or two of you felt that 512MB RAM should be OK - I've installed the same again and it sailed through the installation in no time at all - so for future reference it might be that 512Mb is on the edge for some computers.

So now then - am I brave enough to update to 8.04 before you clever folk have sorted the bugs and reduce the need to save any files I save?

Thanks to those who helped
C

---

