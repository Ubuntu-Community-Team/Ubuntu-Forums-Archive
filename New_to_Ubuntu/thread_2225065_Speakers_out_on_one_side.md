---
title: "Speakers out on one side"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by rook3 on 2014-05-19
Speakers, earbuds, etc... out on one side only. On multiple jacks. Pavumeter(with a test sound) and pavucontrol show signal, it's just not making it to one side of the output devices. 

Newer(Obviously, this is the "Absolute Beginners Section"), so I'm unsure what other data would be useful. Here's a copy paste from lshw.

[ATTACH]253296[/ATTACH]

---

### Post by Vladlenin5000 on 2014-05-19
*Warning - dumb question ahead*: Have you checked the balance? (not possible to check that in your comprehensive - thanks, btw - list of hardware).

Check again anyway and while there slide it all the way to either sides. Does it confirm you have one channel only?

Your Gigabyte GA-78LMT-S2P uses an ubiquitous Realtek ALC889 HD audio codec; problems with this chipset in Linux, other than OS/external settings or hardware failure, are seldom reported.

---

### Post by rook3 on 2014-05-19
@Vladlenin- No such things as dumb questions, I'm a self admitted absolute beginner :P  

I assume that's what I checked in pavucontrol? Left and right are both at 100%, and pavumeter shows signals on both sides. I could be wrong though, this may just be "volume"; I'm not sure how to delineate "volume on both sides" vs. "balance".

---

### Post by rook3 on 2014-05-22
New info: 
Pulseaudio, pulseaudio-utils, pavumeter, pavucontrol are all installed. 

Result of relevant alsa commands: 
[http://www.alsa-project.org/db/?f=2bfa44d035e5865d6a29d342b528da2febb3a1d4](http://www.alsa-project.org/db/?f=2bfa44d035e5865d6a29d342b528da2febb3a1d4)

Alsamixer shows 2 channels. 

Updating/reinstalling alsa via [COLOR=#000000][FONT=Times New Roman][ ! -f './purgeconfig.sh' ] && wget [http://purgeconfig.sf.net/purgeconfig.sh](http://purgeconfig.sf.net/purgeconfig.sh) && sudo bash ./purgeconfig.sh alsa-base alsa-utils linux-sound-base libasound2

[/FONT][/COLOR]Next steps are to update/reinstall kernel, reset local settings via "[COLOR=#000000][FONT=Times New Roman]rm -rf ~/.pulse* ~/.asound* ~/.pulse-cookie"[/FONT][/COLOR]? Is there anything else I can look for or try?  Recommendations from folks in realtime is "try in a different  computer/distro", which I'm unable to do easily.

---

### Post by rook3 on 2014-05-22
Results of [FONT=times new roman]speaker-test[/FONT] version 1.0.27.2

[ATTACH]253377[/ATTACH]

I notice that it only lists one channel... Does this help me narrow things down?

---

### Post by rook3 on 2014-05-24
REMOVED pulseaudio. speaker-test and audio still out on one side when tested through alsa. 

*The problem is not pulseaudio*. It's either alsa or something simpler. I'm at the point as a beginner where it seems more likely I'll screw up  my system than fix the problem, but I've tried a lot of different stuff  found in google.

Not really sure I can test without alsa active ;-) Next step: Removal of alsa and testing on an OSS install? Is my logic sound?

---

### Post by rook3 on 2014-05-27
Marking this as solved, even if it isn't completely. The most likely culprit is sound card, now, and I'm sick of trying to google this stuff. 

Learned a bit about how alsa/pulseaudio/kernel works, and how to boot isos directly from HDD, so I guess it wasn't a complete loss. 

For those that come later with similar issues: 
I tried booting a livecd from different OSes, putting iso images of the distros in the /boot/grml folder. Hold shift at startup to enter grub, and boot the iso. If the sound is STILL bad, it's likely not ubuntu :P You can't INSTALL those distros to hard drive without being unable to unmount the hard drive, but you can test with them live.

For competent folks: Feel free to correct me if my logic is bad, or verify if this is likely.

---

