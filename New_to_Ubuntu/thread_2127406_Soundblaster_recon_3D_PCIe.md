---
title: "Soundblaster recon 3D PCIe"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by woomdawg on 2013-03-19
I have and evga x58 classified 3 with and I7-920 12GB or gskill ram and i recentley purchased a creative soundblaster recon 3D and it wount play any sound just static. In pulse it shows it as a stereo and also in alsa but just static. Can anyone help me with this? Oh yea I am running ubuntu 12.10 64bit.

---

### Post by woomdawg on 2013-03-21
Bump

---

### Post by ManamiVixen on 2013-03-22
The PCIe Recons are not really supported well by Linux. Drivers for it were introduced in Kernel 3.5 for the Sound Core tech but at the moment it's biggest feature is being recognized by ALSA and it's missing all it's sound features. It is in fact a pretty useless card in Linux at the moment. Problems with the card arise in the fact most of it's sound processing is actually done by the CPU with the chips on the card being glorified HDA Codecs with some intelligence. As well as the companion chip that bridges the Sound Core to the PCIe bus requiring a separate driver. So it isn't a matter of writing a driver for a single sound chip as much as trying to figure out how to have the CPU encode the audio stream and have a driver ready for the companion chip so the incoming stream could be sent to the Quad DSP's through that chip on the Recon to be decoded and read and be played over the speakers. There might be better support in Raring 13.04 though. Kernel 3.8 got new ALSA drivers and was updated to work with more cards. You should of bought a used X-Fi PCI Card.

---

### Post by woomdawg on 2013-03-23
ughhhh

---

### Post by mmstick on 2013-04-22
X-Fi PCI cards are inferior to the new sound blasters. I can tell you that 13.04 also does not yet support Recon3D, so I'm forced to use the onboard chip in my Sabertooth 990FX. I've heard there will be support for Recon3D-based cards in kernel 3.9 which is about to release (and Ubuntu 13.04 will not be shipping with it).

---

### Post by ThEMarD85 on 2013-06-06
Heyyo,

Actually? For some reason my SoundBlaster Recon 3D Fatal1ty Professional Edition (lots of fancy words) works flawlessly without any modification in Kubuntu 13.04.. even on the live cd. I'm trying to figure out how that is cause I must say I'm not a fan of KDE cause of how annoying the menus are. I've had marginal luck in Ubuntu 13.04 using Kernel 3.9.4 but it was static and I had to modify the rc.local file and for some reason it doesn't always work for me. Hope my testing of stuff helps.

---

### Post by tatsujb on 2013-11-09
Where's this at? my gameblaster's not working (it's a Sound Core3D chip card), I'm on Ubuntu 13.10. apparently 3.5 kernel is enough to have support for this chip. I don't know what kernel I have.

---

### Post by tatsujb on 2013-11-09
Ubuntu software center returns 7 entries for "sound blaster" could any of those work?

---

### Post by ThEMarD85 on 2013-11-13
Heyyo,

Actually? I bet the problem you guys are all having is you're running a 64bit kernel... try 32bit kernel.

I have a Sound Blaster Recon 3D FATAL1TY Professional.... she works perfect in Ubuntu, Kubuntu, Fedora and Linux Mint... ONLY in 32bit. I believe Kernel 3.7 or 3.9 was the one that gave me full functionality... but like I said, for some odd reason only in 32bit.

---

### Post by sandyd on 2013-11-13
> **ThEMarD85 said:**
> Heyyo,

Actually? I bet the problem you guys are all having is you're running a 64bit kernel... try 32bit kernel.

I have a Sound Blaster Recon 3D FATAL1TY Professional.... she works perfect in Ubuntu, Kubuntu, Fedora and Linux Mint... ONLY in 32bit. I believe Kernel 3.7 or 3.9 was the one that gave me full functionality... but like I said, for some odd reason only in 32bit.

If it actually really only works in 32-bit, please consider reporting this as a bug - then perhaps we can get this to work in 64bit as well :)

---

### Post by ThEMarD85 on 2014-01-01
> **sandyd said:**
> If it actually really only works in 32-bit, please consider reporting this as a bug - then perhaps we can get this to work in 64bit as well :)
Heyyo,

There's bug reports already  and I posted my findings.. but sadly still nothing has changed... maybe the Linux Kernel Organization doesn't own a Sound Blaster Recon 3D...  now there's the Sound Blaster Z series as well... and by the looks of it? Same boat.

And apparently I don't have full functionality... front audio ports on my PC case doesn't work... microphone doesn't work either... I can disconnect and it disappears from the Sound Settings, and plugging it back in makes it pop up... but nothing, wether I try S-PDIF or Analog Input... so she needs lots of work. Testing right now even on Ubuntu 14.04 32bit with Kernel 3.12.0-7-generic I'm still getting the same stuff as back with kernel 3.9.

---

