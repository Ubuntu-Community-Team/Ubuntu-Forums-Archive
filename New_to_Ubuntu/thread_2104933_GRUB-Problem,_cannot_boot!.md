---
title: "GRUB-Problem, cannot boot!"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by surati on 2013-01-14
Hi
I&#7743; using a dualboot system and wanted to make windows to boot first...so I used "grub customizer". I changed windows to be the first in the list, and changed also font size and added a foto. So now when I start my computer I only see the foto (absolut un-correct displayed) but no menu apears and nothing happens! So now I can use the computer only with a live cd and I have no idea how to correct the grub files. ( I tryed to download a "boot repair" but the download does&#324;t function, maybe because my livecd has an older ubuntu on it 10.10??).
I will be happy for an advice!
Thanks
surati

---

### Post by oldfred on 2013-01-14
10.10 is not supported anymore, so you cannot get any updates.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You might be able to hit down arrow or up arrow to get to an Ubuntu entry. Grub remembers key strokes as soon as BIOS finishes and I have hit down arrow to get to Windows before menu even appears. If you remember where it was on menu it would be best to know number to key strokes.

You should download a newer copy of Ubuntu to have as a liveCD, DVD or flash install to use for repairs.

---

### Post by surati on 2013-01-14
Thanks for your fast answer.
Hitting the arrow/enter didn´t bring any reaction so now I&#7743; downloading a boot-repair-disk and see if it would help...

---

### Post by sigmarhophi on 2013-01-14
If you get to a foto in grub, then you should be able to do some limited command line grub editing. When you are at the foto, press 'c' and you should be dropped to a grub command line. From there, you can boot which ever OS you want.

Else

I would recommend using any live CD (including your 10.10) to boot from and reinstall grub. Like the poster above, I would recommend upgrading to the lates LTS version.

Here is a nice walk through:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

