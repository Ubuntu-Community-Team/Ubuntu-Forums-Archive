---
title: "hard drive partitions setup for clean install and virtualization"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by jemonic on 2008-09-19
I recently installed ubuntu for the first time after much googling with a dual boot setup with partitions for xp, ntfs files, ubuntu, and swap.

After reading more I would like try using virtualbox to access xp instead of rebooting. My primary needs will be quicken and office 2007, but mainly I'd like to have the option available.

I tried to figure out how to convert my existing xp partition for virtualbox use (perhaps even retaining the ability to boot natively into xp), but although there is a lot of material out there, this seems to be ahead of my learning curve at this point.

Since my data is backed up and I haven't put in that much work, I am thinking about starting over and trying to figure out the best setup. I would like to keep my files on a separate partition (I am working on a Dell Vostro 200 with 160GB Hard Drive, 3GB Ram).

Could/should I start over with a ubuntu partition, swap, file partition, and then install virtualbox and create the xp virtual disk image?
(Sorry if this is a long post it is my first, I have done a fair amount of research but haven't been able to synthesize it all)

---

### Post by Elfy on 2008-09-19
Sounds good to me - I don't bother with a seperate /home anymore and prefer to keep data completely away from the install partition.

You need to make sure that you put the virtual drive for the xp in your file partition when you get that far - which is easy.

---

### Post by jemonic on 2008-09-19
Any point or benefit to putting the virtual disk on it's own partition? Or would that just make my life more complicated at this early point in my career? I would like to be able to access the data on the file partition while in xp.

---

### Post by Elfy on 2008-09-19
I would say best not to have a seperate partition - it's more efficient to have less partitions imo

You can access the partitions from within the virtual xp - they get mounted as network drives iirc.

---

### Post by jemonic on 2008-09-21
ok, this is excellent! i am well on way and a very happy new arrival to linux/ubuntu so far.

i have three partitions /sda1 which is ext3 and has ubuntu; /sda2 linux swap; and /sda3 which is ntfs where i want to locate all my files. my virtualbox xp image is on /sda3 and running well.

i have to two questions:

1) how to do i change-move my /home directory to the /sda3 partition?
(or should i create symlinks for documents-videos-pictures-music instead, in which case how would i do that)

2) how can i get the xp image which is in a folder on /sda3 to be able to see/mount the rest of my files which are on /sda3?
(i'm presuming i'm correct in not wanting to save files locally on my xp image)

thanks a bunch!

---

### Post by jimmy the saint on 2008-09-21
With VirtualBox, you can set up a shared folder.  You need to install the guest addtions first, which is as simple as machine>install guest additions with an XP guest.  Once that is done, you can set up a shared folder.  the best way is to map a network drive because you are essentially networking the guest to the host.  If you set up a network place, the performance is terrible.  Do a google search about shared folders in virtualbox and you will find good info.  

I would advise against putting your /home folder on an ntfs partition simply because it is not a native filesystem in linux.  One solution for sharing documents would be to a folder on your ntfs partiton and use it to store any documents you may want to share and use that as your default storage spot for both OSs for those documents.  Just make sure to use this as the shared folder.

---

### Post by jemonic on 2008-09-21
Thanks for the Virtualbox part, I will get right on that.

For the storing of files, I was googling and someone said that they created symbolic links for music, videos, pictures, and document folders. Would this be a solution? Or I suppose I could reformat the partition as ext2, then install fs-driver on the xp image? Or do both. Thoughts?

---

### Post by jimmy the saint on 2008-09-21
None of that is neccessary.  Just make whatever folder you use to store your documents your shared folder.  Once you map this folder as a networked drvie it will show up in "My Computer" and you can use it just like any other.  From within Ubuntu, it is just like any other folder.  Piece of cake.  Essentially you will have one folder that you can access from both the Host and Guest OSs just like any other folder.  

To create the share:
In xp, right click in "my computer" and select "map network drive"  select the drive letter, then set the pat as \\vboxsvr\folder, where folder is the path to your share.  If the share folder is in your home directory, just type the folder name, if it isn't use the absolute path starting with \.

---

### Post by jemonic on 2008-09-21
... well I got the folder to show up in Devices > Machine Folders
the path is /media/disk/home-jo

when i clicked on install guest additions before that nothing visible happened so i'm not really sure if that worked correctly.

when i right click and try to map \\vboxsvr\media\disk\home-jo
it says the network path could not be found

i was able to share the folder home-jo over the network and allow guest connections with write permissions and then browse to it from map network drive. not sure if that is the intended solution as this seems to make the folder visible and accessible to everyone on the network. i might have to settle for this as i do not seem to be having much luck.

thanks again for the help.

---

### Post by talofo on 2008-12-11
> **jemonic said:**
> ... well I got the folder to show up in Devices > Machine Folders
the path is /media/disk/home-jo

when i clicked on install guest additions before that nothing visible happened so i'm not really sure if that worked correctly.

when i right click and try to map \\vboxsvr\media\disk\home-jo
it says the network path could not be found

i was able to share the folder home-jo over the network and allow guest connections with write permissions and then browse to it from map network drive. not sure if that is the intended solution as this seems to make the folder visible and accessible to everyone on the network. i might have to settle for this as i do not seem to be having much luck.

thanks again for the help.



I have absolutly no idea about how to partition a hardrive drive that will have Ubuntu 64 and Vista 64 (this one, on a VM).

Can I ask you one of two things or maybe both if you are in mood?

Any documents about this type of configuration?
I see a lot about "running windows as VM on Ubuntu" But, I'm unable to find:
"Partitions on a Ubuntu with Vista VM."

Have you reach your final configuration? How does it look? Do you have performance issues running M$ on VM?


Thanks, and Kind Regards,
MEM

---

### Post by talofo on 2008-12-14
my perfomance using virtualbox to virtualize xp pro. Is very very nice. This means, from now on, only linux distros. :D

The partitions are not a big deal. I mean, it can bee if we study a lot but, for commun mortals, its quite ok to install only the normal partitions, and know that virtualbox will create his stuff on /home. 

Regards to all.
MEM

---

