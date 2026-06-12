---
title: "VMPlayer and ALSA"
date: 2006-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Roner on 2006-05-25
I have had a nagging problem with VMPlayer: it uses OSS for sound.  That means that unless OSS is enabled and loaded, I get the annoying /dev/dsp not found message when the player starts; as I was moving to Dapper, many updates broke OSS and made the problem reappear.  Additionally, this means that while another application is using OSS and the player tries to access it, it will hang with an error message.

To enable OSS to begin with, follow the first section of this thread:
[http://www.ubuntuforums.org/showthread.php?t=101125&highlight=oss2jack](http://www.ubuntuforums.org/showthread.php?t=101125&highlight=oss2jack)

The best solution for me was adapted from [this thread]("http://www.vmware.com/community/thread.jspa?messageID=355054&#355054") on the vmware forums; it uses the alsa-oss package and enables VMPlayer to use ALSA for sound.

1. Install VMPlayer and create your image. I was greatly helped by [this guide]("http://www.ubuntuforums.org/showpost.php?p=490521&postcount=80"); browse the rest of the thread for instructions on using qemu without wine.

After you have a working image and preliminary installation of the guest OS:

2. Get the alsa-oss package:
```
sudo apt-get install alsa-oss
```

3. Ensure that the /usr/lib/libaoss.so.0.0.0 library is setuid:
```
sudo chmod +s /usr/lib/libaoss.so.*
```

4. Rename the VMPlayer bin file:
```
sudo mv /usr/bin/vmplayer /usr/bin/vmplayerorig
```

5. Create a new VMPlayer bin file:
```
sudo vi /usr/bin/vmplayer
```

Copy and paste the following into the file:
```

#!/bin/bash
LD_PRELOAD=libaoss.so exec /usr/bin/vmplayerorig "$@"

```

Make the new file executable:
```
sudo chmod +x /usr/bin/vmplayer
```

That's it. In the Multimedia Systems Selector choose either ALSA or Autodetect, and you will have sound in VMPlayer, and no hangs.

---

### Post by flibble on 2006-06-11
Fixed it for me. Thanks for your work!

---

### Post by Rizado on 2006-06-11
I tried this but now I can't open or edit my windows xp vm. ```
Unable to get information for disk (IDE 0:0)
Unable to open file "/home/username/.vmware/Windows XP Professional/Windows XP Professional.vmdk": Fil för stor.
```
Fil för stor = File too large. I didn't want to change the original message.

I can open it if I start vmwareorig.

---

### Post by Grundlebug on 2006-06-16
I know this is three weeks old, but thanks for posting it!  Got my VMPlayer sound going.

When's Ubuntu going to fully switch to ALSA?!? I've been cleaning up little sound problems all over the place.

---

### Post by Roner on 2006-06-16
Rizado, this fix is specifically for VMPlayer.  VMWare server has the option to choose the sound device.  I prefer the player simply because it seems to be the same speed of the server, and the interface is not as cluttered.  The server gives you, naturally, much more for the money you don't pay.

Grundlebug, I am glad I helped.  This problem is application-specific, and as I said, was already solved in the VMWare server.  Generally speaking, this workaround helps with many applications that default to OSS.

---

### Post by Rizado on 2006-06-17
Well I have sound through the kernel oss emulation but if I use that I can't use anything else. Will this guide make it mixable or is it just for people with sound problems?

EDIT: Ok I got mixing working now, don't know what the problem was but now it works. But the sound is horrible! [img]http://ubuntuforums.org/images/liteblue/icons/icon9.gif[/img] It's crackeling and too slow and just crap. Is it like this for you too?

BTW it's no problem getting vmware to work with this guide. The steps are the same.

---

### Post by andb on 2006-07-13
Is there a way to make VMware use ALSA without alsa-oss? I set the device name for the sound card to auto-detect and when anything else is using sound I still get the following error:

Failed to open sound device /dev/dsp: Device or resource busy
Failed to connect virtual device sound.

Is there a way to configure VMware server to use the sound card nicely? :)


edit: My goal is to use VMware sound and other sound apps (music, voip) simultaniously.

---

### Post by Sir_Brizz on 2006-07-18
> **Rizado said:**
> I tried this but now I can't open or edit my windows xp vm. ```
Unable to get information for disk (IDE 0:0)
Unable to open file "/home/username/.vmware/Windows XP Professional/Windows XP Professional.vmdk": Fil för stor.
```
Fil för stor = File too large. I didn't want to change the original message.

I can open it if I start vmwareorig.
How did you fix this? I'm having the same problem and have no clue what to look for next...

---

### Post by Rizado on 2006-07-23
> **Sir_Brizz said:**
> How did you fix this? I'm having the same problem and have no clue what to look for next...I couldn't fix it, had to reinstall windows, but it was a fresh install anyway. I've seen the same problem on vmware forums but noone knew how to fix it. The audio is crap using alsa anyway so I'm back to oss.

---

### Post by lobius on 2008-04-25
I found I had to give the full name of the library to get it working, i.e.

LD_PRELOAD=libaoss.so.0.0.0 exec /usr/bin/vmplayer "$@"

---

### Post by lviggiani on 2008-06-05
Hi, I'm trying to make it work on Hardy but it doesn't... :(

I followed your guide. The only difference is that instead of renaming wmplayer I did a new script called /usr/bin/vmplayer-alsa that contains:

```
#!/bin/bash
LD_PRELOAD=libaoss.so exec /usr/bin/vmplayer "$@"
```

the rest is as in your guide.

Then I run it:
```
vmplayer-alsa <path to my vmx file>
```

It starts but I get the message that the sound device is (actually) busy.

That was working with Gusty...

In the vmx file I have the following settings:

```
sound.present = "TRUE"
sound.virtualDev = "es1371"
sound.device = /dev/snd/pcmC0D0c
```

and that was working with Gusty.
Any idea?

---

### Post by raydude on 2008-06-05
sound.device = /dev/snd/pcmC0D0c

I think this needs to be /dev/dsp for alsa oss.

Raydude

---

### Post by lviggiani on 2008-06-06
Still not working... :(

---

### Post by ashdavely on 2008-06-20
I am having this problem in Hardy as well. Anyone able to resolve it?

---

### Post by lviggiani on 2008-06-23
Hi,
I could solve the problem... the tutorial was perfect.
The real problem with Hardy is that by default music players are not using ALSA.
So, first of all, go to System > Preferences > Sound.
In the Devices tab page (first one) make sure that all Sound Events, Music and Video, Conferences etc. are using ALSA (select it from the drop down list).

(after that, restarting X might be necessary)

That was my actual problem. Then just follow the tutorial and sound should work fine in vmware.

I hope that this will help.
Ciao!

---

### Post by shirsch on 2008-09-30
Unfortunately, none of this works to VMware using ALSA under Kubuntu (kde based) Hardy.  I am running out of ideas.

Regardless of what I use as a wrapper (artsdsp, vmwarearts, libaoss, etc), it complains that it cannot open /dev/dsp.  If nothing else on the system has used or is using sound, I can bring up VMware without a wrapper and it works fine - until the first time anything else makes noise.  Following that, I get an error in the guest telling me it cannot open /dev/dsp.

It's not a matter of suid anymore, since VMware 6.x does not have the binary as suid, BTW.

---

### Post by Crafty Kisses on 2008-09-30
Nice tutorial thanks, nicely laid out.

---

### Post by bbhavsar on 2009-10-06
New version of VMware Player 3.0 and VMware Workstation 7.0 supports ALSA for sound on Linux hosts.

[http://communities.vmware.com/community/beta/workstation](http://communities.vmware.com/community/beta/workstation)

--Bankim.

---

