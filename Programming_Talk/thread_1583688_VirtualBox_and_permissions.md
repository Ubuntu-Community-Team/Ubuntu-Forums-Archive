---
title: "VirtualBox and permissions"
date: 2010-09-28
forum: Programming Talk
---

### Post by sevenearths on 2010-09-28
I have Ubuntu 9.10 and 10.04 installed on my system. 9.10 is my production, and 10.04 (or the partition) is what I will migrate to when things get to old.

I have a additional partition with all my development work, large data, and virtual boxes on. I created a XP virtualbox file on the additional partition from within 9.10, but I can't boot the XP virtualbox from 10.04.

I get a feeling that it is because virtualbox can't write to the .vid container because of permissions, but my login for both os's is the same and the file has been 'chmod 0777'. I wonder if it might be the way the drive is mounted. Any ideas?

---

### Post by quixote on 2010-10-01
When you say .vid, do you mean the vdi directory underneath .Virtualbox in your home directory on 9.10?  Which file is 777?  The vdi dir?  The specific virtual machine image inside vdi?  

When you're in 10.04, virtualbox will look in your home on 10.04.  I'm not sure there's any way that doesn't run the danger of crosslinking files, to use the same home on two different distros.

---

### Post by sevenearths on 2010-10-04
The .vdi file is on a seperate drive (called Data). The 9.04 and 10.04 install of ubuntu are actually my os's and don't exist as virtualboxs.

In addition I now mount my extra drive in just the same was as I used to mount it in 9.04 (/etc/fstab). So now I'm even more stumped!?!

EDIT: I also have a centOS virtualbox on the same partition and it boots up fine from with in 10.04

---

### Post by quixote on 2010-10-04
Sorry, I'm still having trouble grasping the question.  Is there some way you could do a diagram, or maybe a nested list of where everything is and what the problem is?

If I understand -- and I probably don't -- you'd like to access the XP virtual from either your 9.1 partition or from the 10.04 one.  The reason you can't is because vbox has its info about installed virtual OSes in its .Virtualbox directory under your home. 

But home under 9.10 is one dir, and home under 10.04 is a different one.  Furthermore, I think it has to be because the system would get hopelessly confused if you had two different versions writing to the same config files.

What you can do, I think, is edit ~/.VirtualBox/VirtualBox.xml so that it contains all the information it needs for a virtual machine (use one of the other installs in the list as a model), but have the location point to your home under 9.10.  Or something like that....  I don't think you could blow anything up just by trying.  At worst, it won't work.

Note that there needs to be a line under "MachineRegistry" and one under "HardDisks".  The MachineRegistry refers to an .xml file that has to go under the Machines subdirectory and should either also point to you 9.10 .xml file, or you should copy the 9.10 file to the folder under 10.04.  I'd try copying to 10.04 first because for some reason that feels like it might have a better chance of working.

Just guessing.  No guarantees.  :)

---

### Post by SeijiSensei on 2010-10-04
Virtualbox lets you create "shared folders" which you can see from both the host and guest operating systems.  That's by far the easiest method for transferring files between them. 

The other alternative is a network fileserver running Samba and, perhaps, NFS.  Mount the network share in both the guest and host.  This is a bit slower in terms of performance than shared folders, of course, since you're moving the files back and forth over the network.

---

### Post by quixote on 2010-10-04
True, if all you want is some of the data, then shared folders is the way to go.  You need to install VirtualBox Guest additions to do that, and then you need to manually share the specific folder you want.

---

### Post by sevenearths on 2010-10-05
> **quixote said:**
> Sorry, I'm still having trouble grasping the question.  Is there some way you could do a diagram, or maybe a nested list of where everything is and what the problem is?

If I understand -- and I probably don't -- you'd like to access the XP virtual from either your 9.1 partition or from the 10.04 one.  The reason you can't is because vbox has its info about installed virtual OSes in its .Virtualbox directory under your home. 

But home under 9.10 is one dir, and home under 10.04 is a different one.  Furthermore, I think it has to be because the system would get hopelessly confused if you had two different versions writing to the same config files.

What you can do, I think, is edit ~/.VirtualBox/VirtualBox.xml so that it contains all the information it needs for a virtual machine (use one of the other installs in the list as a model), but have the location point to your home under 9.10.  Or something like that....  I don't think you could blow anything up just by trying.  At worst, it won't work.

Note that there needs to be a line under "MachineRegistry" and one under "HardDisks".  The MachineRegistry refers to an .xml file that has to go under the Machines subdirectory and should either also point to you 9.10 .xml file, or you should copy the 9.10 file to the folder under 10.04.  I'd try copying to 10.04 first because for some reason that feels like it might have a better chance of working.

Just guessing.  No guarantees.  :)

Hummmm!... My bag. It looks like if I copy the '.vartualbox' folder from the 9.04 install to the 10.04 install all works fine. The directory must keep additional information on the xp vb.

Sorry guys. Should have been the first thing I did but I was under the impression that vb's were self contained and could be moved between machines. Guess that proved that wrong. Though this whole thing begs the question 'what would you do if you wanted your ubuntu created winxp vb to be used under another os?' I presume the '.virtualbox' directory would be useless.

---

### Post by quixote on 2010-10-05
Indeed.  If you copy the whole .VirtualBox directory you have a duplicate of your setup right down to the last bell and whistle.  If you already had virtual machines defined, though, they'd be gone.  I take it that wasn't an issue for you.  Another caveat: this vm WinXP is separate from the original one.  Changes you make or files you save under 10.04 vbox will not be reflected in your 9.10 vbox winxp vm.  As Seijisensei said, you need to share folders.  Or somehow point both vboxes to the same virtual winxp, which might not be a stable solution.

As to what you'd do with your vm under another OS, I'm not sure.  I think VMWare is famous for having a good export function, but I'm not too sure about vbox.  I think that's one of its shortcomings.  Possibly, with another linux OS you could use the same .VirtualBox dir in your home, but that seems too easy.  Maybe somebody else here knows.

---

