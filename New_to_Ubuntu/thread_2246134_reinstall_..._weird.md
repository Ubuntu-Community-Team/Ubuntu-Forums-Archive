---
title: "reinstall ... weird"
date: 2014-09-28
forum: New to Ubuntu
---

### Post by czgirb on 2014-09-28
Finally, I reinstalled my Ubuntu 14.04, but after all finished, I found that my previous **/home**'s label had become **207GB** and I have new and clean:
** Documents, Downloads, Music, Pictures,** and **Video** folders.

  So I supposed to delete some folder in my **previous /home** ..., which now called now **207GB**.

  I pressed **Delete** key, but no response.
 So I deleted it by **Right-Click** > **Move to Trash** ... and the folder **JUST** disappeared, without showing up in the **Trash**.

  Why does this happen? How can I solved this problem?
Please guide me ...
**Thanks**
**PS:**
Just delete **3-Sub-Folder**, it showing up in the **Trash** ... but said that each folder contains **0 (Zero)-KB**
How can it be? Each folder contains **more than 100MB** previously ... before it was to **Moved to Trash**.

---

### Post by Quarkrad on 2014-09-28
I think I have a similar problem.  I installed a clean 14.04 with separate / and /home - I was expecting to find my Documents folder in /home but it appears in / and /home.  I have done some testing and what ever happens in home in /home also appears in home in /.  Everything is duplicated.  Perhaps this is how it works - I was expecting to find all the folders and files normally associated in home under /home and not in / (only system folders/files).

---

### Post by Quarkrad on 2014-09-28
Something odd seems to be happening - my (what I call system file partition) partition sda1 that has mount point / is 30GB and is showing as full.  As I have a partition for / and another for /home surely / cannot be full with just the 14.04 system folders/files.  This is the first time on this machine I have install separate / and /home partitions.

---

### Post by Quarkrad on 2014-09-28
Attached warning and picture of gparted for my machine.

---

### Post by yancek on 2014-09-28
> I found that my previous **/home**'s label had become **207GB** 

I'm not sure I understand that.  Are you saying if your run the command:  ls /   that you do not see /home as one of the directories?
If you reinstalled Ubuntu 14.04, did you previously have a separate /home partition?  and did you select not to change it during the reinstall?

Do you have a separate entry for /home in your /etc/fstab file?

---

### Post by mcduck on 2014-09-29
If you didn't tell the installer to mount the home partition at /home, it's not going to happen automatically and you just end with a new home in your / partition, and a separate data partition (probably mounted inside /media, either through fstab or your desktop's automount system). In that case you'll want to start the system with a live-CD or USB key, and then delete the /home that exists on the root partition and edit /etc/fstab to mount the home partition as /home. (In theory you could just mount the separate oartition over the existing /home, but as any files there would still stay on the root partition, even though inaccessible, you'd waste some disk space doing that)

I'm not sure what you are talking after you mention pressing Delete key. In file manager? To delete what?

---

### Post by czgirb on 2014-09-29
Yes ... Yes ... Yes ...!!! How can I forgot for the **/home**!!! Yup! I'm not define any **/home**!!!
 OK, OK, OK! If I **JUST** let this happen, is it OK? If it's OK, just let it be ...

**Now the last question:**
When I open **/media/czgirb**, I found the **real name** of **207GB** is **8580d3f9-05cf-4b89-b766-12c0e6f43e91** ... how can I rename it?

---

### Post by Vladlenin5000 on 2014-09-29
You need to read again the post just above yours, post #6...

---

### Post by nerdtron on 2014-09-29
> **czgirb said:**
> Yes ... Yes ... Yes ...!!! How can I forgot for the **/home**!!! Yup! I'm not define any **/home**!!!
 OK, OK, OK! If I **JUST** let this happen, is it OK? If it's OK, just let it be ...

**Now the last question:**
When I open **/media/czgirb**, I found the **real name** of **207GB** is **8580d3f9-05cf-4b89-b766-12c0e6f43e91** ... how can I rename it?

You can edit drive labels using GParted (right Click on the drive> Label). Just make sure the drive you want to rename is not mounted.

---

### Post by czgirb on 2014-09-30
> **nerdtron said:**
> You can edit drive labels using GParted (right Click on the drive> Label). Just make sure the drive you want to rename is not mounted.

SORRY ... I'm a newbie to Ubuntu
[B]1. Choose the Partition unmount
2. Choose the Label => typed the label
3. Mounted the Partition
4. and Applied[/B]
That's it?
Plaese confirm

Maybe my questions is a **SILLY** question to you.
But please be considerate that I'm a newbie
Please ...

---

### Post by nerdtron on 2014-09-30
3. Apply your changes.
4. Mount the partition.

---

