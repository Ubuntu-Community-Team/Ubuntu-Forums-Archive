---
title: "HOWTO: Solve VMWare sound (mixing?) problem once and for all"
date: 2007-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by xp_newbie on 2007-01-04
Concise practical summary / steps for the impatient (tested on VMware version 5.5.3 build-34685):
[COLOR="DimGray"]Note: to run step #2 successfully you will need apt's Universal (Community maintained) repository enabled.[/COLOR]

[LIST=1]
[*]sudo -i
[*]aptitude install alsa-oss
[*]chmod +s /usr/lib/libaoss.so.*
[*]mv /usr/bin/vmware /usr/bin/vmware.orig
[*]echo '#!/bin/bash' > /usr/bin/vmware
[*]echo 'LD_PRELOAD=libaoss.so exec /usr/bin/vmware.orig "$@"' >> /usr/bin/vmware
[*]chmod +x /usr/bin/vmware
[*]exit
[/LIST]

(now launch vmware as before)

**_Background_**:

The sound on your Ubuntu system works perfectly.

When you start a Windows 2000/XP VM on VMWare, the sound works there too - **most** of the time... Every once in a while, despite the sound device not being used at all by any Linux program (or so you think), you get the following error message when starting a Windows 2000/XP VM on VMWare:

> Failed to open sound device /dev/dsp: Device or resource busy Virtual device sound will start disconnected.

**_Explanation_**:

[LIST]
[*]Your Ubuntu system is using ALSA for sound mixing. ALSA is the [Advanced Linux Sound Architecture]("http://alsa.sourceforge.net"). 
[*]VMWare, on the other hand, is using OSS. OSS is the free version of the [Open Sound System]("http://www.4front-tech.com/oss.html").
[/LIST]

There are two ways of getting an application to work with ALSA if the application was written for OSS.
[LIST=1]
[*]The first way is to load the special ALSA drivers that emulate the OSS kernel interface; these allow the application to open /dev/dsp0 and other OSS device files.
[*]The second way is to wrap the application in the libaoss library provided in this package; the wrapper causes the application to access native ALSA device files such as /dev/snd/pcmC0D0c instead of OSS device files.
[/LIST]

Use of the alsa-oss library (i.e. method 1) is recommended over the use of OSS-emulation drivers if you want to use ALSA's PCM plugin layer.

Enjoy!

---

### Post by ssavelan on 2007-02-14
I've never heard of VMWare?

Is that Virtual Machine.  Sound interesting.   Surely you are not suggesting that linux is using a device when you are booted into XP, so you must be talking about running a virtual machine?  I recently manage to void my sound while trying to run wine on things that really shouldn't be run with wine yet.

---

### Post by ssavelan on 2007-02-14
[http://en.wikipedia.org/wiki/VMware]("http://en.wikipedia.org/wiki/VMware")

I see, that is what I thought.  Must you purchase such software?

---------------
ps.... we need to make everything JACK-able.

---

### Post by dro0g on 2007-02-22
awesome walkthrough, thanks!

---

### Post by xp_newbie on 2007-02-25
> **ssavelan said:**
> [http://en.wikipedia.org/wiki/VMware]("http://en.wikipedia.org/wiki/VMware")

I see, that is what I thought.  Must you purchase such software?

Some versions are free, some are not. Check the VMWare web site. Also, there is the open source equivalent of VMWare, called Xen. Its only limitation is that currently if you want to emulate a Microsoft OS using Xen, you must have one of the latest CPUs that support virtualization in HARDWARE. Otherwise, you can run as many Linux VMs as you want under Xen (which itself runs under Linux).

HTH,
Alex

---

### Post by xp_newbie on 2007-02-25
> **dro0g said:**
> awesome walkthrough, thanks!

Glad you liked it. After getting so much from this virtual community, it was time for me to give something back. :)

Alex

---

### Post by jasonxh on 2007-03-11
Nice HOWTO. However it doesn't apply to my vmware server directly, but with a little bit twist which I found from vmware forum. I point it out here in case anyone like me stumble upon this thread with a vmware server.

Instead of /usr/bin/vmware, I have to modify /usr/lib/vmware/bin/vmware-vmx (default installation path) to get it working, i.e.,
```
cd /usr/lib/vmware/bin
sudo mv vmware-vmx vmware-vmx.real
sudo echo '#!/bin/bash' > vmware-vmx
sudo echo 'LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"' >> vmware-vmx
sudo chmod +x vmware-vmx
```

Everything else is the same.

---

### Post by mfarley on 2007-03-18
> **jasonxh said:**
> Nice HOWTO. However it doesn't apply to my vmware server directly, but with a little bit twist which I found from vmware forum. I point it out here in case anyone like me stumble upon this thread with a vmware server.

Instead of /usr/bin/vmware, I have to modify /usr/lib/vmware/bin/vmware-vmx (default installation path) to get it working, i.e.,
```
cd /usr/lib/vmware/bin
sudo mv vmware-vmx vmware-vmx.real
sudo echo "#!/bin/bash" > vmware-vmx
sudo echo "LD_PRELOAD=libaoss.so.0.0.0 exec /usr/lib/vmware/bin/vmware-vmx.real "$@"" >> vmware-vmx
sudo chmod +x vmware-vmx
```

Everything else is the same.

I tried everything in the original post and what you said -- no dice.

I can play audio in both the XP VM and the native Linux, just not simultaneously.

Any tips?

---

### Post by jasonxh on 2007-03-19
mfarley, have you installed and suid'd libaoss correctly? Which version of vmware are you using?

BTW, I noticed that in my last post, I used wrong quotation marks (corrected). Check and make sure your vmware-vmx file looks like this
```

#!/bin/sh
LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"

```

---

### Post by eliesen on 2007-03-26
Hi everyone!

I've been a noob with Ubuntu for almost two years now, on and off, on and off.. mostly I've solved my issues by googleing the problem, find a  site with a solution (usually this forum) and just done exactly what it says (i consider myself a master of "cut and paste";)

But this time that did'nt work. I too got the "device busy" message when trying to load a soundriver when running WinXP through vmware on a Ubuntu (edgy) system. First I tried what XP_newbie suggested in the origninal post, and when that didnt work, i tried jasonxh's solution. Now, on the other hand, I can't get my winXP in vmware to boot! When I start it, I get this message:

> Unable to change virtual machine power state: The process exited with an error:

VMware Server Error:
VMware Server must be set-UID root, "/usr/lib/vmware/bin/vmware-vmx" is not.  Are you running /usr/lib/vmware/bin/vmware-vmx from its distribution directory?  That copy of the program is not set-UID root.

Press "Enter" to continue...
End of error message.

Can anyone help me with this? I had everything set up on that winXP other than the sound, I'd really hate to lose it.. I can post any systeminfo you need if you first tell me how to find it :p 

Great community btw, thanks for all the help I've gotten in the past and present :)

---

### Post by jasonxh on 2007-03-26
Did you somehow change the permission of vmware-vmx(or vmware-vmx.real if you followed my post)? You should make sure that it is suid. Also check if you have followed the original post to set suid to libaoss.so.*. The commands are
```

sudo chmod u+s /usr/lib/vmware/bin/vmware-vmx.real
sudo chmod u+s /usr/lib/libaoss.so.*

```
Also, please do calm down. Your XP on vmware would be fine as long as you don't touch the .vmdk files. DON'T touch those files.


> **eliesen said:**
> Hi everyone!

I've been a noob with Ubuntu for almost two years now, on and off, on and off.. mostly I've solved my issues by googleing the problem, find a  site with a solution (usually this forum) and just done exactly what it says (i consider myself a master of "cut and paste";)

But this time that did'nt work. I too got the "device busy" message when trying to load a soundriver when running WinXP through vmware on a Ubuntu (edgy) system. First I tried what XP_newbie suggested in the origninal post, and when that didnt work, i tried jasonxh's solution. Now, on the other hand, I can't get my winXP in vmware to boot! When I start it, I get this message:



Can anyone help me with this? I had everything set up on that winXP other than the sound, I'd really hate to lose it.. I can post any systeminfo you need if you first tell me how to find it :p 

Great community btw, thanks for all the help I've gotten in the past and present :)

---

### Post by Strelock on 2007-04-09
I have a strange iisue - if I use the new file (vmware) then I get error mmessage  on my main Vmware virtual ddisk  Cannot open "" or one the snapshots it depends on. Reason: File to large.

If I just run vmware.orig everything works fine... Any ideas?

If I remove LD_PRELOAD=libaoss.so from vmware then everything works fine again...

Now If I remove problematic virtual disk I get "Cannot connect virtual device sound" message from VMWare anyway...

---

### Post by Waya on 2007-04-18
Okay, I did everything xp_noobie explained that didnt work the way it should... output on the console is when I try to run the /usr/bin/vmware is:

```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
kde-config: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
kde-config: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
```

VM starts up tho. so I thought "cool, lets not bother with that, lets just start windows" (I need that to dj using Sam2)

Anyhow... what I get when I try to start windows is:

```
Cannot connect virtual device sound. No corresponding device is available on the host. Wouls ou like an attemt to be made to connect thic virtual device every time you power on the virtual machine?
```

Sound in linux works perfectly.. I dont have any other programs running that could occupy it. I am out with my knowledge, no idea what it could be.

I would really appreciate it if you had any hints for me into what direction to look.

I am running Drapper with 
```
Linux hellonearth 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
```
and
```
VM Workstation
5.5.3 build-34685
```

Greetings Waya

P.S. I am not sure what informations you might need, I will of course provide it if its nessesary.

---

### Post by justin99 on 2007-04-18
Thanks for the post, and thanks for the note about modifying the vmware-vmx script in the case of vmware server (free!). Works like a charm for me.
This community is the best. Now I have my voip solution and my WoW both working together. No more vmware/oss taking over the sound system. Very happy.

---

### Post by itsdaveperdue on 2007-05-07
Thanks jasonxh!  Worked perfectly for me!

---

### Post by starkadder on 2007-05-07
you need to make the new file executable.  Run:

sudo chmod a+x /usr/lib/vmware/bin/vmware-vmx

---

### Post by starkadder on 2007-05-07
you need to make the new file executable. Run:

sudo chmod a+x /usr/lib/vmware/bin/vmware-vmx

---

### Post by twa on 2007-05-10
I've executed the commands in the first post of this thread and I'm no longer getting the error about /dev/dsp being busy but I still can not get Vmware Workstation 6 to attach the sound card to the vm guest.  My VM guest is WinXP and I'm running an up to date Ubuntu 7.04.

I'm now getting the following error:

Cannot connect virtual device sound. No corresponding device is available on the host.

Just after receiving the error I've been able to generate sound from ubuntu so I know the card is alive and active.  I saw a similar error to mine a couple of posts above mine but there is no solution posted in reply yet.

---

### Post by twa on 2007-05-12
My machines is good to go.  I've reinstalled workstation 6 right over the previous install and I'm working now.  I've tried so many things now that it's hard to pinpoint what fixed it.

---

### Post by hasimir44 on 2007-05-28
> The first way is to load the special ALSA drivers that emulate the OSS kernel interface; these allow the application to open /dev/dsp0 and other OSS device files.

I don't have any new /dev/dsp* devices, any idea how to create those? maybe I'm missing a package or two?

my environment: 

```
**arymcdo@gloryrider:/opt> sudo apt-get install alsa-oss**
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-oss is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
[B]
arymcdo@gloryrider:/opt> cat /usr/bin/vmware[/B]
#!/bin/bash
LD_PRELOAD=libaoss.so exec /usr/bin/vmware.orig "$@"

**arymcdo@gloryrider:/opt> ll /usr/lib/libaoss.so***
lrwxrwxrwx 1 root root    16 2007-05-28 10:07 /usr/lib/libaoss.so -> libaoss.so.0.0.0
lrwxrwxrwx 1 root root    16 2007-05-28 10:07 /usr/lib/libaoss.so.0 -> libaoss.so.0.0.0
-rwSr-Sr-- 1 root root 19200 2006-11-22 17:58 /usr/lib/libaoss.so.0.0.0


**arymcdo@gloryrider:/opt> ll /usr/bin/vmware /usr/bin/vmware.orig**
-rwxr-xr-x 1 root root   65 2007-05-28 09:49 /usr/bin/vmware
-r-xr-xr-x 1 root root 4570 2007-05-27 08:25 /usr/bin/vmware.orig

**arymcdo@gloryrider:/opt> ll /dev |grep audio**
crw-rw---- 1 root audio    14,  12 2007-05-27 10:45 adsp
crw-rw---- 1 root audio    14,   4 2007-05-27 10:45 audio
crw-rw---- 1 root audio    14,   3 2007-05-27 10:45 dsp
crw-rw---- 1 root audio    14,   0 2007-05-27 10:45 mixer
crw-rw---- 1 root audio    10, 135 2007-05-27 03:45 rtc
crw-rw---- 1 root audio    14,   1 2007-05-27 10:45 sequencer
crw-rw---- 1 root audio    14,   8 2007-05-27 10:45 sequencer2
```

Using /dev/dsp and /dev/adsp gives me the device busy error, while
using /dev/dsp0 gives me the file not found, no device error.. 

any suggestions are appreciated. thanks!

---

### Post by Snam on 2007-06-01
> **xp_newbie said:**
> There are two ways of getting an application to work with ALSA if the application was written for OSS.
[LIST=1]
[*]The first way is to load the special ALSA drivers that emulate the OSS kernel interface; these allow the application to open /dev/dsp0 and other OSS device files.
[*]The second way is to wrap the application in the libaoss library provided in this package; the wrapper causes the application to access native ALSA device files such as /dev/snd/pcmC0D0c instead of OSS device files.
[/LIST]

Use of the alsa-oss library (i.e. method 1) is recommended over the use of OSS-emulation drivers if you want to use ALSA's PCM plugin layer.


I'm confused :confused:.

In the first bullet you say: > "The **first** (i.e. method 1) way is to load the special ALSA drivers that **emulate** the OSS kernel interface; these allow the application to open /dev/dsp0 and other OSS device files."
So the **first** method mentions **emulation**.

In the second bullet you say: > "The **second** way is to wrap the application in the **libaoss library** provided in this package; the wrapper causes the application to access native ALSA device files such as /dev/snd/pcmC0D0c instead of OSS device files."
So the **second** method mentions the use of a **library**.

Then you say: > "Use of the **alsa-oss library** (i.e. **method 1**) is recommended over the use of OSS-emulation drivers if you want to use ALSA's PCM plugin layer."
Shouldn't that be method **2** instead of method **1**?!? Because method 2 mentions the use of a library and method 1 the use of emulation.

---

### Post by Snam on 2007-06-01
> **xp_newbie said:**
> 
[LIST=1]
[*]sudo -i
[*]aptitude install alsa-oss
[*]chmod +s /usr/lib/libaoss.so.*
[*]mv /usr/bin/vmware /usr/bin/vmware.orig
[*]echo '#!/bin/bash' > /usr/bin/vmware
[*]echo 'LD_PRELOAD=libaoss.so exec /usr/bin/vmware.orig "$@"' >> /usr/bin/vmware
[*]chmod +x /usr/bin/vmware
[*]exit
[/LIST]


I still got the error message:
```

Failed to open sound device /dev/dsp: Device or resource busy.
Failed to connect virtual device sound.

```

This is what I've done:
[LIST]
[*] I skipped step 1 to 3, because the alsa-oss package was already installed on my system.
[*] I've got VMware Player, so instead of step 4 to 6 I've written the following script which I placed in my home directory:
```

#!/bin/bash
# Script to startup vmplayer without the following error message in the Virtual Machine: 
# 	Failed to open sound device /dev/dsp: Device or resource busy
# 	Failed to connect virtual device sound.
LD_PRELOAD=/usr/lib/libaoss.so exec /usr/bin/vmplayer "$@"
[*] I made my script executable (chmod 774 vmplayer.sh).

```
[/LIST]

When I ran my script I still got the "Failed to open sound device /dev/dsp" error message.

You wrote:
> **xp_newbie said:**
> 
the wrapper causes the application to access native ALSA device files such as **/dev/snd/pcmC0D0c** instead of OSS device files. 


So VMware should use a native ALSA device files such as "**/dev/snd/pcmC0D0c**", but the VMware Player error message said it is still trying to use "**/dev/dsp**".

So I changed my .vmx file as folows:

```

sound.present = "TRUE"
sound.virtualDev = "es1371"
sound.device = /dev/snd/pcmC0D0c

```

But that didn't do the trick, I still got the error message:
```

Failed to open sound device /dev/dsp: Device or resource busy.
Failed to connect virtual device sound.

```

Can you tell me how to fix this problem?

---

### Post by susta on 2007-06-02
Hello,

I follow the instructions from this tutorial but I want to add a little info.

Open your VMWare server and then your virtual machine.
Edit the settings of the virtual machine.
In the sound section instead of use **/dev/dsp**  you can use **/dev/adsp**

Save your settings and Power On you machine.

/dev/adsp is used by the Alsa System Sound.

With this configuration I can play sounds in the Host (Ubuntu) and in the Guest (Windows XP).

I hope this help.

Ivan Sustaita (susta).

Sorry for my bad english.

---

### Post by hasimir44 on 2007-06-03
I was able to get sound in my guest OS and ubuntu to work (using /dev/dsp in vmware) by creating a .asoundrc file in my home directory. This is all that it contains: 

```

pcm.!default {
        type plug
        slave.pcm "dmix"
}

```

more info on this file: 

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php)

---

### Post by djgrant on 2007-06-03
None of the proposed solutions seem to work for me with VMWare workstation 6 and Feisty.

---

### Post by xp_newbie on 2007-06-04
> **djgrant said:**
> None of the proposed solutions seem to work for me with VMWare workstation 6 and Feisty.

Did it work for you with VMWare workstation 5 and Dapper?

I haven't tried yet VMWare 6. The most I tried is VMWare 5.5.4 build-44386 on Dapper (kernel 2.6.15-28-686). I will report back when I get to trying VMWare 6.

---

### Post by ryu kun on 2007-06-04
None of above solutions worked on Feisty, VMWare Server Console 1.0.3 build-44356.

---

### Post by djgrant on 2007-06-05
> **xp_newbie said:**
> Did it work for you with VMWare workstation 5 and Dapper?

I haven't tried yet VMWare 6. The most I tried is VMWare 5.5.4 build-44386 on Dapper (kernel 2.6.15-28-686). I will report back when I get to trying VMWare 6.

Haven't tried anything except Feisty. I'm a long time Gentoo user trying Ubuntu for the first time. I have heard that Vmware 5.5 is fine and that something changed between 5.5 and 6 that makes sound difficult to impossible to get working.

Dave

---

### Post by Snam on 2007-06-09
> **susta said:**
> 
Edit the settings of the virtual machine.
In the sound section instead of use **/dev/dsp**  you can use **/dev/adsp**


Thnx. When I use ```
sound.device = /dev/adsp
``` in my .vmx configuration, then my sound works in my Guest OS (WinXP) :-).

Unfortunately I don't have sound in both my host OS (Ubuntu) and my Guest OS at the same time :-(. I only get sound in the OS that uses my sound device first.

Therefore I tried 

> **hasimir44 said:**
> creating a .asoundrc file in my home directory.

```

pcm.!default {
        type plug
        slave.pcm "dmix"
}

```


But that didn't do the trick.

Does anybody know how I can get sound from my Host OS and my Guest OS simultaneously?

---

### Post by Snam on 2007-06-10
> **Snam said:**
> 
I tried creating a .asoundrc file in my home directory.
```

pcm.!default {
        type plug
        slave.pcm "dmix"
}

```


**Warning:** When I created the above .asoundrc file in my home directory, my headset output didn't work anymore. When I pluged in my headset in my headsetoutput, I didn't heared sound through my headset and the sound of my laptop speakers wasn't muted. (I double checked if my headsetplug was completely in the headsetoutput of my laptop, so that wasn't the cause of the problem.)
When I removed the .asoundrc file and restarted my computer, my headset worked fine again :-).

---

### Post by NeutrinoX on 2007-06-14
Well guys, I don't know if this is useful at all, but I got VMWare Workstation (6.0.0 build-45731) sound working, mixing well and without problems so far on Feisty Fawn, by using newbie_xp's method and /dev/adsp as my sound adapter. 

I don't know if this might be relevant, but I noticed that on my .asoundrc I have *slave.pcm "duplex"* instead of *slave.pcm "dmix"*

---

### Post by mooscape on 2007-06-19
I have struggled through all the above advice, to no avail.  There is no sound device shown in VM (host or guest).   

Feisty Fawn (2.6.20-16-generic) on IBM R40 laptop.  Vmware Server 1.0.2 build-39867.

](*,)

(Is there anything I can post that could be of use in resolving this?)

---

### Post by whistle on 2007-06-19
How would I reverse this?  I just got Ubuntu last week and can't quite follow what happened... did I make a copy of my vmware program, then modify that?  If so, could I just delete vmware and rename vmware.orig to vmware and have it back to where it was before?

<-- didn't work on Feisty and Workstation 6.

---

### Post by whistle on 2007-06-20
Never mind.  I figured it out... at least, I think i did.

---

### Post by SirOracle on 2007-06-29
> **jasonxh said:**
> Nice HOWTO. However it doesn't apply to my vmware server directly, but with a little bit twist which I found from vmware forum. I point it out here in case anyone like me stumble upon this thread with a vmware server.

Instead of /usr/bin/vmware, I have to modify /usr/lib/vmware/bin/vmware-vmx (default installation path) to get it working, i.e.,
```
cd /usr/lib/vmware/bin
sudo mv vmware-vmx vmware-vmx.real
sudo echo "#!/bin/bash" > vmware-vmx
sudo echo 'LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"' >> vmware-vmx
sudo chmod +x vmware-vmx
```

Everything else is the same.

I don't get this to work, I use Feisty and VMware Server 1.0.3.
On the first echo-command I get this (I have double checked, the file has been renamed to vmware-vmx.real, and there is no wmare-vmx file):
```

sudo echo "#!/bin/bash" > vmware-vmx
bash: !/bin/bash": event not found

```
If I replace the double " with single ' I get this:
```

sudo echo '#!/bin/bash' > vmware-vmx
bash: vmware-vmx: Permission denied

```
I am however able to get the text in this way:
```

sudo gedit vmware-vmx

```
And paste in this code:
```

#!/bin/bash
LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"

```

But when I start a virtual machine I get this error:
Cannot open the disk '/var/lib/vmware/Virtual Machines/Windows/Windows.vmdk' or one of the snapshot disks it depends on.
Reason: File too large.

If I revert the changes, the virtual machines starts fine, except for the sound. Could someone please help me with this?

---

### Post by jasonxh on 2007-06-29
Oops, another quotation mistake... Since I actually used vim to edit the file, so the code was NOT tested...

Now I suggest you check permissions of libaoss.so, vmware-vmx.real and the newly created vmware-vmx. If you still can not figure it out, please attach the results here.

---

### Post by SirOracle on 2007-07-02
/usr/lib:
lrwxrwxrwx 1 root root    16 2007-06-29 08:16 libaoss.so -> libaoss.so.0.0.0
-rwSr-Sr-- 1 root root 14580 2006-11-23 02:07 libaoss.so.0.0.0

/usr/lib/vmware/bin:
-r-xr-xr-x 1 root root 3651784 2007-05-30 12:26 libvmcontrol-helper
-r-xr-xr-x 1 root root 1130988 2007-05-30 12:26 openssl
-r-xr-xr-x 1 root root 2407344 2007-05-30 12:26 vmrun
-r-xr-xr-x 1 root root 7615260 2007-05-30 12:26 vmware
-r-xr-xr-x 1 root root 1589452 2007-05-30 12:26 vmware-remotemks
-rwxr-xr-x 1 root root      80 2007-07-02 07:30 vmware-vmx
-r-sr-xr-x 1 root root 4385824 2007-05-30 12:26 vmware-vmx.real

I can't see what's wrong.
I usually start vmware as my normal user, but I tried now to start it with sudo, but I got the same error message.

---

### Post by jasonxh on 2007-07-03
What's the size of your virtual disk? Have you tried creating a new disk?

---

### Post by vxd240 on 2007-07-10
Hi SirOracle,
- check your permissions in ~/.vmware (you might want to give full access "sudo chmod 777 ~/.vmware" just to rule out any issues with your binaries, then reduce access for security)
- check that ~/.vmware/* is owned by you

---

### Post by SirOracle on 2007-07-10
jasonxh:
I have one Windows Vista with a 40 GB harddisk and one Windows XP with a 60 GB harddisk. They are both dynamic and in 1 file. The Vista-disk-file is now 17 GB and the XP-disk-file is now 2.1 GB.

If I create a new Virtual machine, it boots fine. And if I remove the harddisk from the Vista Virtual machine and add a new empty harddisk the Vista machine also boots fine.

vxd240:
The ~/.vmware directory and both files in it (favorites.vmls and preferences) are owned by me. And chmod ~/.vmware to 777 did not help.

---

### Post by vxd240 on 2007-07-10
Hi SirOracle,

Firstly, I had the exact same problem as you.  

I find that the files may change permission depending on whether you run/snapshot in root or not.  So sorry if I ask you to check your permissions and ownership again; in particular, the files where your vm image is stored (*.vmdk, *vmsn, *.vmx, *.vmem, etc) 

And finally...as a last desperate try (I'm sure it doesn't have anything to do with anything, but I turned on debugging and....ummm...it just worked :/ )  That is Edit Virtual Machine Settings -->Options tab-->Advanced-->Run with debugging information

---

### Post by t_tovenaar on 2007-07-10
Pretty good howto! It worked for me, thanks.

---

### Post by SirOracle on 2007-07-11
Hi vxd240
All files in both my virtual machines directories are owned by me and I have rw.
Turning on debugging actually did make the virtual machine start. But it's still without sound :(
Did you get sound on both host and guest OS (at the same time) when you turned on debugging?

I will try to install a new fresh virtual machine, to see if I get sound then.

---

### Post by SirOracle on 2007-07-13
I installed a new fresh Windows XP virtual machine now. And I got sound on both the host and guest OS. I have no idea why it don't work on my existing virtual machines, but I'm happy with this new installation.

So thanks for the help folks!!

---

### Post by SirOracle on 2007-07-16
No, no no...
I shut down my new XP virtual machine last week, and when I now turned it back on, I got the samme error message...
(Cannot open the disk '/var/lib/vmware/Virtual Machines/WinXP/WinXP.vmdk' or one of the snapshot disks it depends on. Reason: File too large.)

I read about something similar on this post on the VMware forums:
[http://www.vmware.com/community/message.jspa?messageID=677861](http://www.vmware.com/community/message.jspa?messageID=677861)

"WS 6 & Player 2.0 is more strict on not allowing the user to run a virtual disk that can grow larger than what the filesystem can support."

On Wikipedia ([http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)) I see that ext3 has a max filesize from 16GB to 2TB, it depends on the blocksize. I don't know how to find out what blocksize my filesystem use, but if it uses 1KB, the max filesize will be 16GB. That could explain the error message. But that doesn't explain why the error message only comes if I apply the "hack" explained in this post.

I converted the virtual disk to be split into 2GB files, then it started up fine, with sound again. I even tried to shutdown and turn it back on again now ;) I find this very strange, but I hope this can help others that get in my situation.

---

### Post by cbudden on 2007-07-16
> **SirOracle said:**
> No, no no...
I shut down my new XP virtual machine last week, and when I now turned it back on, I got the samme error message...
(Cannot open the disk '/var/lib/vmware/Virtual Machines/WinXP/WinXP.vmdk' or one of the snapshot disks it depends on. Reason: File too large.)

I read about something similar on this post on the VMware forums:
[http://www.vmware.com/community/message.jspa?messageID=677861](http://www.vmware.com/community/message.jspa?messageID=677861)

"WS 6 & Player 2.0 is more strict on not allowing the user to run a virtual disk that can grow larger than what the filesystem can support."

On Wikipedia ([http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)) I see that ext3 has a max filesize from 16GB to 2TB, it depends on the blocksize. I don't know how to find out what blocksize my filesystem use, but if it uses 1KB, the max filesize will be 16GB. That could explain the error message. But that doesn't explain why the error message only comes if I apply the "hack" explained in this post.

I converted the virtual disk to be split into 2GB files, then it started up fine, with sound again. I even tried to shutdown and turn it back on again now ;) I find this very strange, but I hope this can help others that get in my situation.


How did you convert back to split files?  I just started over.  

Also, when I use alsa for vmware sound, it is slight laggy and stuttery when playing video.  If i use oss, the stutter is not present.

Chris

---

### Post by jasonxh on 2007-07-16
You can check the block size by:
```
sudo tune2fs -l /dev/xxx
```

---

### Post by SirOracle on 2007-07-17
cbudden:
Use vmware-vdiskmanager to modify virtual disks. Just type vmware-vdiskmanager in a terminal window to see how to use it. But to convert a single growable disk to a growable disk split into 2GB files use this command:
```
vmware-vdiskmanager -r diskname.vmdk -t 1 newdiskname.vmdk
```
Then you need to rename the disk back to the original name, or change in the .vmx file so it points to the correct name for the vmdk-file.

jasonxh:
Then I have 4KB blocks, and I should have a 2TB max filesize. So that can't be the reason why it helps to split into 2GB files. But thanks for the tip with tune2fs :)

---

### Post by jfrankman on 2007-08-10
Do the proposed solutions fix the soud when it is not present, or do they help improve sound quality? 

I tried the solution posted for vmware server, in order to try to improve sound quality on my windows xp guests  because my sound is so choppy in windows xp. However, after making all the necessary changes the sound is as choppy as ever.  The funny thing is when I first installed vmware added windows xp as my first guest os the sound was nearly perfect. Then after a month or so the sound became very choppy. The only thing I could think that is happening is that an update to ubuntu affected the sound, or degraded performance on my computer. I doubt this however, since I have 2GB of RAM and the sound was working at one time. If anyone has any other ideas, I would appreciate it.

---

### Post by mooscape on 2007-09-27
This HOWTO worked really well.

Two outstanding issues though: 

1. I can only play CD's in XP on the virtual machine from one of my DVD drives. The other drive does not register at all.
2. In linux, sound juicer starts the music from the first CD. I then close and switch to the other CD player. This plays OK, but then I cann't change back to the first. Both will now only show the second CD !!! :confused:

Any ideas on what is happening here?

---

### Post by ccd on 2007-10-16
Did anyone get vmplayer 2 to work with alsa-oss? I tried to modify both /usr/bin/vmplayer and /usr/lib/vmware/bin/vmware-vmx. Neither works for me.

---

### Post by netj on 2007-11-05
> **ccd said:**
> Did anyone get vmplayer 2 to work with alsa-oss? I tried to modify both /usr/bin/vmplayer and /usr/lib/vmware/bin/vmware-vmx. Neither works for me.

Check if your alsa-oss package has any Large File Support problem.
Debian etch's alsa-oss of the moment (1.0.12) is suffering from it.
See also: [http://lists.alioth.debian.org/pipermail/pkg-alsa-devel/2007-April/004301.html](http://lists.alioth.debian.org/pipermail/pkg-alsa-devel/2007-April/004301.html)

My aoss vmplayer works fine now after I've compiled the fixed source package (1.0.14) from lenny.  I'm not sure what version of alsa-oss is available in Ubuntu, but if you get some problem opening .vmdk, it must be the Large File Support bug in alsa-oss.

-J

---

### Post by Meister_Eder on 2007-11-11
Hi, I tried the HowTo but it didn't work for me. I am using Feisty and vmware-server from the repos. 
If I modify my vmware-vmx I get 
```

VMware Server Error:
The command line specifies more than one configuration file.

```
On the other hand when I modify vmware, I get 
```

Unable to open: Virtual machine "“”" is not in the inventory.

``` 
Any help is greatly appreciated.

---

### Post by Floppyjoe on 2007-11-17
When i had firefox running or sometimes even if I had nothing that I thought used sound in Linux running then I would get that error mentioned on the first post.

I skimmed through the posts here and did not find a reference to the package oss-compat. I installed this package and now I think it works to load the vmware xp machine while my browser is open in Linux as long as it is not using the sound.

The package says:
> OSS compatibility package
This package ensures that OSS support is provided in some way.  On Linux, it
enables the ALSA compatibility modules.  On other kernels where OSS is the
default interface, no action is taken.

The purpose of this package is for applications that only support OSS to depend
on it, hence preventing common "/dev/dsp not found" errors that would confuse
unexperienced users.

It seems to be working for me although i have not done extensive testing.

---

### Post by jasonxh on 2007-11-18
> **Floppyjoe said:**
> I installed this package and now I think it works to load the vmware xp machine while my browser is open in Linux as long as it is not using the sound.

Does this workaround solve the problem of using sound in both host and guest at the same time? 'Cause this was the original task of this thread. If it does, then this sounds like a much simpler solution.

---

### Post by Floppyjoe on 2007-11-18
> **jasonxh said:**
> Does this workaround solve the problem of using sound in both host and guest at the same time? 'Cause this was the original task of this thread. If it does, then this sounds like a much simpler solution.

No this does not solve that problem. It just makes it so the vm has sound when the host is not using the sound.

---

### Post by Mazehero55 on 2008-02-15
I did this but now I get a different error.

> Cannot connect virtual device sound. No corresponding device is available on the host.

Would you like an attempt to be made to connect this virtual device every time you power on the virtual machine?

by the way I'm using version 5
and I'm using PulseAudio
any ideas?

---

### Post by survient on 2008-03-15
I know it's been awhile, but it'd be nice to get this working. 

I've done this:

   1. sudo -i
   2. aptitude install alsa-oss
   3. chmod +s /usr/lib/libaoss.so.*
   4. mv /usr/bin/vmware /usr/bin/vmware.orig
   5. echo '#!/bin/bash' > /usr/bin/vmware
   6. echo 'LD_PRELOAD=libaoss.so exec /usr/bin/vmware.orig "$@"' >> /usr/bin/vmware
   7. chmod +x /usr/bin/vmware
   8. exit

and this:

cd /usr/lib/vmware/bin
sudo mv vmware-vmx vmware-vmx.real
sudo echo '#!/bin/bash' > vmware-vmx
sudo echo 'LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"' >> vmware-vmx
sudo chmod +x vmware-vmx

and this:

editing

/usr/lib/vmware/lib/wrapper-gtk24.sh
by inserting at the end (before the call to vm_run) the following export statement

export LD_PRELOAD=libaoss.so:$LD_PRELOAD
vm_run "$@"

and all I keep getting is:

ERROR: ld.so: object 'libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)

any ideas?

---

### Post by deccico on 2008-03-22
Hi, 

I've VMware server 1.04 in Gutsy and also got the "Failed to open sound device /dev/dsp: Permission denied
Virtual device sound will start disconnected." 

After some time and research with no results, I tried with [VirtualBox]("http://www.virtualbox.org/") (acquired by Sun) and after some minutes I was hearing my music in Amarok plus the Windows guest sound. 

VirtualBox support several sound systems, so it's painless to use.

I hope I've helped someone.

---

### Post by felixtherat on 2008-03-27
For those having problems getting VMWare going with OSS:

I had this problem "Cannot connect to virtual device sound" when starting vmware w/ winxp guest (or any guest).  The solution was to stick the device name in the .vmx config file manually: 

sound.fileName = "/dev/dsp"

... and sound began to work, but was choppy, distorted and clipping, and I couldn't find any reference to this anywhere  (hence my google-helping keywords above... and here's some more... garble, popping, bubbling, underwater).

So anyway, solution:

$osstest

 gave me the *actual *name of the devices oss was pumping sound out of (with that nice Seal piano piece as a test file, nice touch OSS guys), so I stuck in /dev/oss/hdaudio0/pcm0 instead, but the sound was still distorted.  However, if you're running a crappy via / HD Audio soundcard on your mobo like I am then try the spdif out (or any other outputs that you hear sound from when running osstest) instead, cos for me sticking

sound.fileName = "/dev/oss/hdaudio0/spdout0"

made everything sound beautiful in VMWare :)

System: Debian etch 2.6.18-6-686 / pentium d / asrock mobo / via chipset / hd audio / VMWare 6

---

### Post by BIGtrouble77 on 2008-03-29
This worked perfectly for me for VMWare Workstation 6 in Hardy.   No negative side effects that I've found.  Thanks Hasimir! 

-bt

> **hasimir44 said:**
> I was able to get sound in my guest OS and ubuntu to work (using /dev/dsp in vmware) by creating a .asoundrc file in my home directory. This is all that it contains: 

```

pcm.!default {
        type plug
        slave.pcm "dmix"
}

```

more info on this file: 

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php)

---

### Post by azredwing on 2008-04-11
I was also able to get my sound working properly with the .asoundrc:

```

pcm.!default {
        type plug
        slave.pcm "dmix"
}

```

I am running Hardy.

I also created the bash script as outlined in the first post. The first post did not work initially, so I assume that the .asoundrc addition did it. However, even that did not work until I restarted X (I tried to restart VMWare Workstation 6 several times). I do not know why.

Good luck to all.

---

### Post by survient on 2008-04-11
I'll try that, but I don't believe that will fix my issue of that module not loading properly, sounds like my vmware's sound has been totaled.

---

### Post by mgysgthath on 2008-04-14
Creating the .asoundrc fixed my issue, without following the rest of the guide.  

In my particular case I set up a 98 SE machine under Fedora 8 and everything was peachy.  I copied the machine to my ubuntu box and low and behold, no sound.  

The trick as was mentioned is I had to restart X (ctrl alt backspace) for the fix to work, restarting vmware workstation did nothing to help.

Hopefully this helps someone.

---

### Post by sheen on 2008-04-25
> **survient said:**
> I'll try that, but I don't believe that will fix my issue of that module not loading properly, sounds like my vmware's sound has been totaled.

The trick does not work for me too on Hardy.
I don't know why : /

---

### Post by Jim_in_Germany on 2008-05-12
Hi guys,

I have pulseaudio installed and have simultaneous
sounds coming from vlc, firefox etc with no problems. 
However /dev/dsp is always busy when I start vmware server 1.0.5. 
I tried the wrapper solution of loading the OSS lib prior to vmware, as well as the other fixes mentioned here but still no joy.

Can anyone help me out?

---

### Post by kmand on 2008-05-21
I tried the dmix .asoundrc suggestion and it did help. Previously I couldn't get any sound from vmware if pulseaudio was running.

Howerver, its still awkward. If vmware is running and I start mythtv, then even if myth is paused, vmware can't play audio. Even if I quit myth, once vmware notices it can't play audio it takes a restart to get it back.

Is there some way to get better sharing?

---

### Post by RandyJ5150 on 2008-05-25
> **hasimir44 said:**
> I was able to get sound in my guest OS and ubuntu to work (using /dev/dsp in vmware) by creating a .asoundrc file in my home directory. This is all that it contains: 

```

pcm.!default {
        type plug
        slave.pcm "dmix"
}

```

more info on this file: 

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php)
Thank you so much.  How do I send a thank you in this forum?

---

### Post by Beach on 2008-06-01
I was having the same issue of not being able to use the sound card (in my guest os) if my host was using the device.  Simply adding:
```
sound.filename = "/dev/adsp"
```
to my .vmx config fixed it for me.  Here is my setup:

Host OS:     Hardy 
Guest OS: WindowsXP, Virtual device: es1371
VMware:   VMware Player, 2.0.3

-Beach

---

### Post by pravinbravi on 2008-06-25
> **susta said:**
> Hello,

I follow the instructions from this tutorial but I want to add a little info.

Open your VMWare server and then your virtual machine.
Edit the settings of the virtual machine.
In the sound section instead of use **/dev/dsp**  you can use **/dev/adsp**

Save your settings and Power On you machine.

/dev/adsp is used by the Alsa System Sound.

With this configuration I can play sounds in the Host (Ubuntu) and in the Guest (Windows XP).

I hope this help.

Ivan Sustaita (susta).

Sorry for my bad english.



This did the trick for me.
/dev/adsp.

I tried all /dev/dsp /dev/audio and the other tinkering with the code and all. Atleast it now doesn't give no errors, but still no sound. I will work on it from here. Thanks Susta anyways.

---

### Post by lionstone on 2008-07-18
So I tried a number of these solutions to no avail...but the fix ended up being quite easy (running Ubuntu Studio 8.04 64bit with VMWare Server )

1) Edit virtual machine settings
2) Click "Add", then choose "sound adapter"
3) Enable autodetect for audio (using /dev/dsp/ was fine)
4) In Ubuntu: Go to System / Preferences / PulseAudio Preferences. THis launches "Change PulseAudio preferences". Now, check all the boxes ( in the Network Access and Simultaneous Output tabs)
5) Launch the Virtual Machine ( XP Pro, in this case)
6) Enjoy XP audio in a virtual machine!

---

### Post by sheen on 2008-07-18
Thanks for the tips lionstone.

Just a litte thing, to get System / Preferences / Pulseausio Preferences, install package named "paprefs" with synaptic or "sudo apt-get install paprefs".

---

### Post by Mirzabah on 2008-07-22
Frankly I don't buy it. The subject line for this thread should be changed to "VMware sound mixing: more time-wasting, cruft-inducing voodoo that fails"

I've tried all of the above and more besides. Nothing works - same old "device already in use" message every freaking time. Thing is, so long as no other process is connected to audio, everything seems fine and that's why most people think their little incantation has done the trick. Fact is, we won't see resolution on this until VMware gets with the program.

---

### Post by Pullkick on 2008-07-31
> **lionstone said:**
> So I tried a number of these solutions to no avail...but the fix ended up being quite easy (running Ubuntu Studio 8.04 64bit with VMWare Server )

1) Edit virtual machine settings
2) Click "Add", then choose "sound adapter"
3) Enable autodetect for audio (using /dev/dsp/ was fine)
4) In Ubuntu: Go to System / Preferences / PulseAudio Preferences. THis launches "Change PulseAudio preferences". Now, check all the boxes ( in the Network Access and Simultaneous Output tabs)
5) Launch the Virtual Machine ( XP Pro, in this case)
6) Enjoy XP audio in a virtual machine!

Hi!

**ONLY WORKS FOR A WHILE! Sadly, after a few minutes of having sound  a message box comes up, telling me that the device is busy again. LEFT FOR REFERENCE!**
[INDENT]
On my machine only "Add virtual output device for simultaneous output on all local sound cards" (the only option on tab "Simultaneous output") had to be checked. All other options on all other tabs could be left unchecked.

And it works now after logging out of gnome desktop, relogging in, and selecting from menubar of vmware server console VM|Removable Devices|Sound Adapter|Connect.
[/INDENT]

---

### Post by slackey on 2008-08-23
In case anyone is still having problems, this is what I did:

Sound worked on my base ubuntu install, but not in any of my VM's. I could not get any of the steps listed in this thread to work, so I switched my system from ALSA to OSS as per this thread: [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2]("http://ubuntuforums.org/showpost.php?p=4874981&postcount=2"). Then I just had to set the audio device on my virtual machine to /dev/oss/ich0/pcm0 and it worked! (If you aren't sure what the OSS audio device is, ossinfo will tell you.)

---

### Post by Phkillah on 2008-09-14
Ok, so let me get it straight:

There is no possible fix to get sound on Windows XP running under VMware Workstation v6, installed in Ubuntu 8.04 x64 that uses OSS instead of alsa. Right?

I switched my sound card drivers in ubuntu 8.04 64b from alsa to oss (i have an x-Fi and i really appreciate the 5.1. Thanks OSSv4).
My virtual XP lost its sound card.....


:popcorn:

---

### Post by shirsch on 2008-09-20
> **Phkillah said:**
> Ok, so let me get it straight:

There is no possible fix to get sound on Windows XP running under VMware Workstation v6, installed in Ubuntu 8.04 x64 that uses OSS instead of alsa. Right?

I switched my sound card drivers in ubuntu 8.04 64b from alsa to oss (i have an x-Fi and i really appreciate the 5.1. Thanks OSSv4).
My virtual XP lost its sound card.....


:popcorn:

I'm forced to agree with you.  Just spent two days flailing around in an attempt at getting VMware WS6 to play nice with a 64-bit Kubuntu Hardy install.  Absolutely nothing will convince Flash player in Kubuntu to share audio with a VMware session (or anything else for that matter).  I tried everything:

- libflashplugin:  Nope, seems to require pulseaudio which is not available in Kubuntu. 

- libaoss:  Nope, "can't open device /dev/dsp". Switch VMware to /dev/adsp?  No error, but no sound either.

- vmwareesd and vmwarearts?  Nope.  Rebuilt both and same results.

- Change KDE to use esd backend?  Nope, nope and nope.

Not sure if it's a flash issue or VMware issue and I'm not interested in fingerpointing.  Sound in Linux is a mess and getting worse with every generation.

---

### Post by Phkillah on 2008-09-20
> **shirsch said:**
> I'm forced to agree with you.  Just spent two days flailing around in an attempt at getting VMware WS6 to play nice with a 64-bit Kubuntu Hardy install.  Absolutely nothing will convince Flash player in Kubuntu to share audio with a VMware session (or anything else for that matter).  I tried everything:

- libflashplugin:  Nope, seems to require pulseaudio which is not available in Kubuntu. 

- libaoss:  Nope, "can't open device /dev/dsp". Switch VMware to /dev/adsp?  No error, but no sound either.

- vmwareesd and vmwarearts?  Nope.  Rebuilt both and same results.

- Change KDE to use esd backend?  Nope, nope and nope.

Not sure if it's a flash issue or VMware issue and I'm not interested in fingerpointing.  Sound in Linux is a mess and getting worse with every generation.

No I am forced to agree with you.

Sound management is way too much complicated than it should. 
However don't forget the fact that this is a Creative X-Fi X-Stupid card from a X-Stupid Company.


Anyway, please tell me if you have Ubuntu 8.04 + X-FI + OSSv4 + VMware WS6 + Virtual Windows XP with sound (any sound at all, not just flash)
I mean, apart from flash, the rest works with you?

Cheers

---

### Post by shirsch on 2008-09-21
> **Phkillah said:**
> No I am forced to agree with you.

Sound management is way too much complicated than it should. 
However don't forget the fact that this is a Creative X-Fi X-Stupid card from a X-Stupid Company.


Anyway, please tell me if you have Ubuntu 8.04 + X-FI + OSSv4 + VMware WS6 + Virtual Windows XP with sound (any sound at all, not just flash)
I mean, apart from flash, the rest works with you?

Cheers

After spending a week getting IP Telephony working with Hardy + ALSA, I'm too nervous to try OSSv4 (need this for working from home).   I don't know what X-FI is - sorry.

After upgrading my 32-bit Swiftweasel browser to use the Flash 10 plugin, I can finally get system sounds + flash to work at the same time.  However, still no luck getting VMware WS6 to share with anything.  

There's probably some poorly documented trick to getting ALSA to listen on an alternate /dev/dsp* or adsp*, but all the recipes I've seen are different - some of them contradict each other.

If anyone ever writes a comprehensive guide to Linux sound that treats it as a complete system (kernel --> user space apps), I will be the first customer.  Everything out there assumes that you've already read and understood everything else.  As an audio systems person, I would benefit from a block diagram that explained all the relationships and data data flow.  Unfortunately, there does not seem to be any such thing.

---

### Post by djbon2112 on 2008-10-13
Hello everyone. I'm trying to get sound working in VMWare Workstation 6.5 but it doesn't want to work. I followed the guide, but when I connect the sound device with "Auto Detect" I get an error about no sound device being detected. ("Cannot connect virtual device sound. No corresponding device is available on the host.")

But the problem furthers when I try to set it to use /dev/dsp or /dev/adsp since these files don't even exist on my system! ('ls /dev | grep dsp' returns nothing). alsa-oss is the latest version, and everything else seems to work fine sound-wise on my system.

I do have an option in VMWare to connect my USB sound device directly (it's a USB sound card), however doing so means (a) I can't have sound in both the VM and the host at the same time, and (b) MIDI playback refuses to work in the guest (XP Pro x64).

---

### Post by djgrant on 2008-10-14
Just switch to VirtualBox. Sound works perfectly.

---

### Post by djbon2112 on 2008-10-15
> **djgrant said:**
> Just switch to VirtualBox. Sound works perfectly.

Have they fully opened it all up so all features are in the OSS version?

---

### Post by wwonkers on 2008-11-02
Everything was fine in Ubuntu 8.04 with vmware workstation 6.05, using the "/dev/adsp" device in vmware.

Now I'm in 8.10 with vmware workstartion 6.5 and sound is broke :(

---

### Post by Erumer on 2008-11-06
Here Ubuntu 8.10 x64, 
Vm-Ware Workstation 6.5

I've tried many things but what did the trick was

- installing the packet paprefs
- preferences - Pulse audio prefs - check all the squares
- loggin' off and on again

and now my guest OS, Win XP 64 is quite happy with its /dev/dsp sound card.

I also point out that the Unity function is just amazing.

Cheers

Update... it worked for several hours, then /dev/dsp got back to "busy". Much ado about nothing...

---

### Post by bosp7 on 2008-11-13
> **Erumer said:**
> Here Ubuntu 8.10 x64, 
Vm-Ware Workstation 6.5

I've tried many things but what did the trick was

- installing the packet paprefs
- preferences - Pulse audio prefs - check all the squares
- loggin' off and on again

and now my guest OS, Win XP 64 is quite happy with its /dev/dsp sound card.

I also point out that the Unity function is just amazing.

Cheers

Update... it worked for several hours, then /dev/dsp got back to "busy". Much ado about nothing...

Erumer,
Have you had any problems with Unity in 8.10 64bit?  It worked perfectly for me on 7.10 32 bit and when I first installed workstation on 8.10 64bit, it was working fine until the first time I restarted Workstation.  Now Workstation just freezes up when I click on the Unity button.

---

### Post by anandchakru on 2008-11-16
Bravo...... :) Good How-to . Thank you very very much. but my mic is not working .... any idea what to do ??

---

### Post by Dropknee on 2008-11-16
I have this problem too, but I reboot my Ubuntu box and now VMWare have sound, I really don't know why this happen, but rebboting the host OS help me out. Try that first before doing this tutorial maybe you are another lucky one :). By the Way my VMWare Workstation is 6.5.0 build-118166

---

### Post by Magneto on 2008-12-06
> **Dropknee said:**
> I have this problem too, but I reboot my Ubuntu box and now VMWare have sound, I really don't know why this happen, but rebboting the host OS help me out. Try that first before doing this tutorial maybe you are another lucky one :). By the Way my VMWare Workstation is 6.5.0 build-118166
what sound card do you have?

---

### Post by septone on 2008-12-23
Well, I should start with the fact I am not using Ubuntu. I'm a longtime Fedora user, although I get around pretty well in other distros too. Ubuntu happens to have a very active user community, and a lot of times when I can't find the answer in the Fedora related places, I look here, and often I can just install the equivalent packages for my distro, and slightly tweak the directions as appropriate. 


That being said, I just tried just about everything in this thread to no avail. I am using FC10 and VMware Server 2. Again, I don't expect what I read here to map directly to my distro (for me libasound.0 is in /usr/lib64, and part of the rpm alsa-oss-libs). I have pulseaudio installed as well, and installing the pulseaudio preferences, and configuring as suggested, then logout/login also did not do it for me. I also manually killed and restarted pulseaudio, after logout/login, still nogo. 

I still have sound one at a time, host OS, or guest OS. If I fire up sound on my host, my guest loses connection to the sound device (I assume because host OS is breaking a lock on the sound device). 

One thing that did with another issue I had: 

I had really choppy sound from time to time in the guest OS. I poked around a bit in the pulseaudio docs, and I found that by increasing my user's rtprio and nice in limits.conf (ulimit), I could allow pulseaudio to run in realtime priority. I logged out, back in, checked ulimit -a to make sure my changes were there, and restarted pulseaudio and it fixed the chopping. 

So maybe that helps somebody else here, maybe not. A lot of the older posts are for older versions of vmware and such, so I thought I'd post my results with something more current, for what it's worth.

Even though this thread didn't pan out for me, I have fixed a lot fo stuff with things I've found here, so thanks for those. :)

---

### Post by rotero on 2008-12-30
> **survient said:**
> 
export LD_PRELOAD=libaoss.so:$LD_PRELOAD
vm_run "$@"

and all I keep getting is:

ERROR: ld.so: object 'libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)

any ideas?

I believe you're getting these errors because you need quotes as I have them in the line below.

export LD_PRELOAD="libaoss.so:$LD_PRELOAD"

---

### Post by ljerabek on 2009-01-02
The easiest way I have found to resolve the WMWare 6.5.X audio issue in Ubuntu 8.04 and Ubuntu 8.10 is to change the device. Instead of using /dev/dsp or /dev/dsp1 just simply use /dev/audio by typing it in manually in VMware (6.5 or 6.5.1). Hope this helps I have had no issues. My systems are using Alsa Mixer which I think is default. 

Regards,

Lu

---

### Post by Tenorio on 2009-03-20
It worked for me, thanks, I've been looking for this for so long!

---

### Post by tulpie on 2009-03-25
I think this is also a cool way to get it to work.
Vmware Player now use alsa .... MY UBUNTU VERSION IS GUTSY 7.10 :guitar:

**[COLOR="Red"]Try this -->[/COLOR]**  [https://bugs.launchpad.net/ubuntu/+bug/81742](https://bugs.launchpad.net/ubuntu/+bug/81742) **[COLOR="Red"]<-- Try this [/COLOR]**
:popcorn:

---

### Post by NimoTh on 2009-04-12
> **xp_newbie said:**
> 
There are two ways of getting an application to work with ALSA if the application was written for OSS.
[LIST=1]
[*]The first way is to load the special ALSA drivers that emulate the OSS kernel interface; these allow the application to open /dev/dsp0 and other OSS device files.
[*]The second way is to wrap the application in the libaoss library provided in this package; the wrapper causes the application to access native ALSA device files such as /dev/snd/pcmC0D0c instead of OSS device files.
[/LIST]

Use of the alsa-oss library (i.e. method 1) is recommended over the use of OSS-emulation drivers if you want to use ALSA's PCM plugin layer.

Enjoy!

To get back to the original post: You talk about two solutions, the first one being the superior one. However, the solution you provide seems to be the second one, right? If so, then what about the first one? Does anyone know how to do that? I have no idea.

Thanks and Cheers
Martin

---

### Post by donor on 2009-06-08
Hi, all
Have a quastion. In guest system sound work perfectly but don't work microfon. Vmware server 2.0

.vmx
```

sound.present = "TRUE"
sound.fileName = "/dev/dsp"
sound.autodetect = "FALSE"

```

How can i solve this?

---

### Post by maudin88 on 2009-07-08
Works for me! Thanks xp_newbie!!  :guitar:

---

### Post by Alfiegerner on 2009-07-26
> **ljerabek said:**
> The easiest way I have found to resolve the WMWare 6.5.X audio issue in Ubuntu 8.04 and Ubuntu 8.10 is to change the device. Instead of using /dev/dsp or /dev/dsp1 just simply use /dev/audio by typing it in manually in VMware (6.5 or 6.5.1). Hope this helps I have had no issues. My systems are using Alsa Mixer which I think is default. 

Regards,

Lu


Just wanted to say thanks, this worked for me, nice easy solution :)

---

### Post by babygenius55 on 2009-08-01
OK, I just finished reading/re-reading all of this post, and after about 8 different methods I'm surprised anything still works.
     My situation is thus: I have a sound-blaster audigy 2 ZS with a Live Drive. Sound works fine. I don't know what you folks define as mixing, but I can't get my VMware workstation 6.5 to recognise my card for what it is. It just reads sound-blaster pci in the device manager. I don't care about being able to play 5 streams at once from the host and the guest. I just want to use my Microphone from the front panel. I have Alsa/pretty much everything else installed, from a very nice utorial that allowed me to finally use my mic with Ubuntu "9.04".  No matter what I type into the sound card selection in vmware, I get the same SB PCI in windows device man. I'm really at a loss how this thread could go all over the place. There was good help to be had, but what REALLY going on?
     I can't load the proper drivers in the virtual machine. FWIW, I didn't change any setup files to reorder the priority of my sound cards, or pgysically take the card out...oh yeah, I have an onboard realtek(no problems in either host/guest) as well. Maybe that would help, but I would really rather leave that as a last resort, as this is the 5th PC my card has been in.  As I haven't heard anyone mention anything about the live drive, I must guess that this problem hasn't been tackled.
     Yet and, still: Why can I get VMware to forward the SBA2ZS identifier to windows?  Is ther some little know driver that you can manually install in the VM sirectories to have it pick it up? I'm so lost.   I just want to use my magic jack. I'm a relative noob, but this is the hardest problem to date.  I got Maya up and running on linux, VMware, and some few others. How could such a basic peice of hardware be so difficult?

I suppose I may have to pony up some loot for a new external setup and use one of my old pc's jsut for this card. :((

Please feel free to PM me. I mean really, please feel free.

---

### Post by mac-duff on 2009-09-08
well,

I still dont understand why it is so difficult to get sound to work but now it seems to work, also when the sound stucks?!

This helped me
[https://bugs.launchpad.net/ubuntu/+bug/81742](https://bugs.launchpad.net/ubuntu/+bug/81742)

---

### Post by nacho_dh on 2009-09-16
> **jasonxh said:**
> mfarley, have you installed and suid'd libaoss correctly? Which version of vmware are you using?

BTW, I noticed that in my last post, I used wrong quotation marks (corrected). Check and make sure your vmware-vmx file looks like this
```

#!/bin/sh
LD_PRELOAD=libaoss.so exec /usr/lib/vmware/bin/vmware-vmx.real "$@"

```

this modification of the solution you came up with worked for me. I'm using VMWare Workstation 6.5.2 in a Ubuntu 9.04.

---

### Post by yurenjimi on 2009-11-10
You guys can download the new VMware-Player-3.0
[http://downloads.vmware.com/d/details/player_3_0/ZGp0YmQlJSpiZGVkZA==]("http://downloads.vmware.com/d/details/player_3_0/ZGp0YmQlJSpiZGVkZA=="),
In the vmplayer3.0, cat choose the ALSA card..:D
Very nice!!!!

---

### Post by Ex-Opesa on 2009-11-20
Thanks! It solved my problems. :)

---

### Post by jejohnsen on 2010-05-29
Posting what worked for me for others who have the same problem on a similar setup:

```

aptitude install alsa-oss oss-compat
chmod +s /usr/lib/libaoss.so.*

```
This makes the /dev/dsp device available for software that requires it, like VMware.

Then make sure that your VM has the following properties in its .vmx-file:
```

sound.present = "TRUE"
sound.filename = "/dev/dsp"
sound.autodetect = "FALSE"

```And finally restart VMware Server:
```
/etc/init.d/vmware restart
```My setup:

- Debian Lenny (probably works on Ubuntu as well?)
- VMware Server 2.0.2
- Intel 82801H/ICH8 sound card
- Working setup with Alsa on host

---

