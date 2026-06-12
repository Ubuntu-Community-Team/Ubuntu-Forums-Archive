---
title: "I need to start over but keep my RAID stacks and VMs"
date: 2018-10-06
forum: New to Ubuntu
---

### Post by rocketshiptech on 2018-10-06
Nuking the site and starting over. After some experimentation with KDE (and not removing it cleanly), and some other issues with file sharing and printer services, before I get any deeper into configuring this machine, now would be a good time to start over. Most of configuration i *have* done involves setting up 2 RAID1 mirrors (using Mdadm, via Webmin)  and a few Virtual Box VMs, So I do need to keep all of that. But the rest of the entire boot drive can go.

Now if this was a Windows machine (like I've been doing for 30 years) I would move the VM files to one of the RAID drives, *unplug* the RAID drives* then reformat c:\ and reinstall the OS. 

*I do this because Windows will automatically spread out temp files, paging files, recovery partitions etc. on all available drives (if you let it). Given Windows software RAID, when I plug the RAID drives back in  Windows would find and re-establish them by itself, and I'd be good to go. I would probably have to rename the machine on the local net to avoid security issues later.

But this is linux :) so I assume it wouldn't put a bunch of stuff on other hardrives without asking first. Right? 

What about the RAID? will the new install just find it? (should I unplug them?)

And the machinename? Any issues creating a new install with exact same name as the old one?

---

### Post by rocketshiptech on 2018-10-09
I see. 
Three days. One view and zero replies.

Who says peer support doesn't work. Oh, that's right, I do.

Well, I've been poking along here myself. I boot up on an install USB drive, didn't install, just went into "Live CD" mode, and no. The RAID stacks are not there. 

Can't install Webmin on the Live CD. Did figure out how to install mdadm in term. from there "mdadm -- assemble -- scan" does show me the drives. 

They're locked.

Every folder and file has a lock icon overlay, and a big "X" icon overlay. I don't know what that means.

So: massive permissions problems.  I have no idea if creating a new user with the same name and password will get me around that. It would in Windows, but that's moot. And it does seem like one wrong step here and I could totally screw myself out of all of my data.

---

### Post by sp40140 on 2018-10-09
Not familiar with RAID. 
But for VBox vms: just back up the vdi files and "VirtualBox vm" directory from the users' home directory. Once you have new os installed and virtualbox installed. put the backup files/directories in their place and you are set.

Also, I suggest you provide more details such as what are the hardware specs? what is the usecase? More details are always better.

Also, please split each issue in it's own thread. As you will find different people with different set of expertise.
you mentioned "Webmin". No experience with it. You have better chance of making a thread with Webmin in title.

Everyone here is helping each other out. Sometimes it takes a bit longer. Hang in there.

---

### Post by wildmanne39 on 2018-10-09
> I see.
Three days. One view and zero replies.

Who says peer support doesn't work. Oh, that's right, I do.
That is not the case, people get there issues resolved by there peers everyday, the view counter is broken on the forum, there has been thirteen views of this thread, the issue is the right person with the answer has not seen your thread yet, you can and are encouraged to bump your thread once every twelve hours to keep it in view, if it goes out of sight then it will most likely not be seen by the person that can help.

---

### Post by rocketshiptech on 2018-10-09
You want hardware specs?
Ryzen 7, AMD Crosshair  MB, 16 GB RAM, 500GB SSD M2 drive as boot drive. 4 2TB drives organized as two RAID 1 mirrors. Nvidia graphics. (blazingly fast)

"what is the usecase?"
Better question: what does "usecase" mean?


Anyway I think I've got a strategy here:
I'll stick any old HD in the box a temporary boot drive. Try my new install there. (that way I'm not erasing the SSD) I can do a "dry run" of the reinstall on that drive. If anything goes wrong I still have the SSD to fall back on. Assuming I figure it all out (for myself) then I can repeat the process (a 3rd install!) on the SSD.

---

### Post by rocketshiptech on 2018-10-10
> **sp40140 said:**
> Not familiar with RAID. 
But for VBox vms: just back up the vdi files and "VirtualBox vm" directory from the users' home directory. Once you have new os installed and virtualbox installed. put the backup files/directories in their place and you are set.

Just taking the entire home folder will do, right?

---

### Post by sp40140 on 2018-10-11
Yes. home directory (~/) will include it.

---

