---
title: "GRUB legacy + partition issues"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by Shmook on 2011-11-18
So I've got 4 OS's installed on one HD, and everything had been going fine. Until the other day I installed PCLOS and things got strange, 2 issues arose:

1: I installed it on what was previously /sda2 (primary partition, XP is on sda1) -- it renamed that partition sda4 for some reason, and raised the sda # on each of the following 4 partitions (SWAP (pri.), Sabayon, Xubuntu, ArchBang (ext.) respectively)

2: It installed GRUB legacy onto the MBR of this HD. I was actually a little excited about this, as I loved being able to edit menu.lst so easily and directly, as opposed to GRUB2's automated .cfg file.

But now, after editing menu.lst, none of the other OS's will work. I'm pretty sure this has to do with the re-numbering of partitions, but haven't gone through this sort of thing before, so I'm not positive.

So I'm wondering; is it possible to get these OS's able to boot while using GRUB legacy in its current form? I'm thinking if I need to I can just use Boot-Repair-Disk and re-write the MBR with GRUB2, but...I'm looking for more info on my current setup, as I'm sure someone out there has gone through something similar. Thanks in advance.

---

### Post by oldfred on 2011-11-19
Grub legacy has not been updated for a long time. Ubuntu added support for ext4 in its version, but others may not have.

Post this to see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

