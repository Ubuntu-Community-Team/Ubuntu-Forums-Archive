---
title: "recovering files after executing sudo rm -Rfv command"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by Mark_Brian_Abad on 2015-03-18
Hi,

I accidentally deleted the files from an nfs mount point, before I execute the rm -Rfv, I unmount the mount point by running sudo umount -av. My mistake was only verifying if the 2 mount points are already unmounted. We have 2 mount point usadata0 and USA_DB. what I need to recover is the USA_DB which is being mounted from the server. By the way we are using xfs filesystem for that mount point. Is there anyway we can recover it? I already tried  testdisk and Raise Data Recovery, but no luck :(.

thank you very much.

---

### Post by DuckHook on 2015-03-18
Sorry to tell you this, but you shouldn't expect a happy ending to this story. Have not worked with XFS, but a quick Google search provides little cause for optimism. Is it a RAID array? If so, then you have an orders-of-magnitude harder problem since the data is striped across multiple disks. I am not remotely qualified to help you with this&#8213;hoping *oldfred* or some other guru will step in here&#8213;but until they do, at least unplug the NAS (or whatever machine is serving the data) so that as little as possible is written to its HDD. If it's just a single disk, then your chances improve from "all but impossible" to "highly improbable". Have a look at [this]("http://www.linuxquestions.org/questions/linux-software-2/how-do-i-undelete-files-on-an-xfs-filesystem-718787/") old thread (it's five years old, but still relevant) and also consider trying *PhotoRec* which I understand will work with XFS. You might also consider imaging the HDD as per post #15 of aforementioned thread.

Aside from above, I'm not qualified to help you any further.

P.S. I know that it is closing the barn door after the horses have bolted, but any form of```
sudo rm -rf
``` is juggling a live hand grenade. I don't see the point in the -v flag when you invoke such a nuclear option except you get to actually see the train wreck as it unfolds before your eyes. At least the -i or -I flag will give you the chance to limit the damage.

---

### Post by King of Heart 4711 on 2015-03-19
I'm going to have to agree with DuckHook. Those files are probably gone. 

Pro Tip: alias rm='rm -i'

---

