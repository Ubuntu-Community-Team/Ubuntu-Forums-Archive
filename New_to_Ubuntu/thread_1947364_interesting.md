---
title: "interesting"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by rima on 2012-03-26
You know how everyone these days go like DO NOT EVER HARD REBOOT! BECAUSE IF YOU DO SO BAD STUFF HAPPENS doom doom dduuumm!!
And guess what?
I HARD REBOOTED** MILLIONS** OF TIMES by removing the battery from the back of my laptop and power when Ubuntu crashes or freezes. I especially did this on the first couple of my n00b days
And nothing, I tell you NOTHING ever happened. Ubuntu working perfectly fine
Sometimes, it's even quicker for me to do this than to do REISUB or similar.

Can you explain why this happens whilst others just innocently pull the power off or something and are unable to boot...

I've been wondering about this for a while

---

### Post by nothingspecial on 2012-03-26
Press Ctrl-Alt-F1 then do REISUB

You will see what happens. Or you can read this

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by winh8r on 2012-03-26
Go for it, it's your machine and it's your data.

how you shut it down is up to you.

---

### Post by BertN45 on 2012-03-26
Well I do the same. The power off button on one of my PCs is defect, so I activated power-fail auto-restart. If I want to power of the PC, I pull the plug. If your system is idling, there will be no application disk io. It might read or write to the swap area, but that is reset anyhow after the power-on. With windows using a paging file, it is slightly more vulnerable.

Bad sectors are impossible, because on the power off detection, the disk unit will finish writing the current sector and retract the heads afterwards. They have to, because in many countries like mine the electricity net is highly unreliable and we have between 2 and 20 power breaks per day. My file server is running for 6 years now without any increase in bad sectors.

If I would pull the plug on a fully loaded system, there is a relatively small chance that my disk administration will be corrupted. That is why Linux periodically checks your disks.

Even with all the power breaks here I do not remember that I had any serious problems. I think I had more motherboards dying on me then disk corruption problems. I do not remember any, that did not get fixed by the Linux periodical check or by chkdsk.

---

### Post by jerome1232 on 2012-03-26
Because we use journaling filesystems, filesystem damage should be kept to a minimum. If my understanding is correct, you **will** lose any data that's in cache waiting to be written, and it's possible you can irrevocably damage your file system if you are very unlucky, although you won't physically damaging the drive as others claim.

---

### Post by rima on 2012-03-27
I see.
But why is it that in some people this results in very damaged systems (it's not even limited to Linux I heard, some people even hard reboot Windows and get it in a horrible state) whilst in others it doesn't damage that much? Silly questions but I am just wondering

---

### Post by jerome1232 on 2012-03-27
That's kind of like asking "why do some people get struck by lightning 3 times but others never get struck"

---

### Post by BertN45 on 2012-03-27
> **jerome1232 said:**
> Because we use journaling filesystems, filesystem damage should be kept to a minimum. If my understanding is correct, you **will** lose any data that's in cache waiting to be written, and it's possible you can irrevocably damage your file system if you are very unlucky, although you won't physically damaging the drive as others claim.

If you close the file/program that data will be written to disk. To prove my point here a text from some kernel documentation about ext4:

commit=nrsec	
(*) Ext4 can be told to sync all its data and metadata every 'nrsec' seconds. The default value is 5 seconds. This means that if you lose your power, you will lose as much as the latest 5 seconds of work (your filesystem will not be damaged though, thanks to the journaling).  This default value (or any low value) will hurt performance, but it's good for data-safety. Setting it to 0 will have the same effect as leaving it at the default (5 seconds). Setting it to very large values will improve performance.

---

