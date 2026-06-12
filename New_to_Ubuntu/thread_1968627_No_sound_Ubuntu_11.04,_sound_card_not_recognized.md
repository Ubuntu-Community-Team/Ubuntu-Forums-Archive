---
title: "No sound Ubuntu 11.04, sound card not recognized"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by anthie88 on 2012-04-29
[SIZE=2]Hello all!

I have a frustrating problem which I try to resolve all day long.
I have installed Ubuntu 11.04 but my sound card is not recognized by the system.
I tried several approaches by doing a lot of googling but as I am a n00bie in ubuntu, I think I lack knowledge to do the right steps.

My audio device is:
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

and the sound card is not recognized by the system (although the modules are installed).
~$ aplay -l
aplay: device_list:240: &#916;&#949;&#957; &#946;&#961;&#941;&#952;&#951;&#954;&#945;&#957; &#954;&#940;&#961;&#964;&#949;&#962; &#942;&#967;&#959;&#965; ... (translation from greek language: no sound card detected).

I have installed alsamixer but when I try to run it I got:
anthoulini@anthoulini-desktop:~$ alsamixer
cannot open mixer: &#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#964;&#941;&#964;&#959;&#953;&#959; &#945;&#961;&#967;&#949;&#943;&#959; &#942; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962; (translation: no such file or folder)


anthoulini@anthoulini-desktop:~$ lspci -v | grep -A7 -i "audio"00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
Subsystem: Intel Corporation Device d608
Flags: fast devsel, IRQ 16
Memory at ff900000 (64-bit, non-prefetchable) [size=16K]
Capabilities: access denied
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])

Please, could anbody give me some help regarding this? I would really appreciate it! Thank you very much in advance.







[/SIZE]

---

