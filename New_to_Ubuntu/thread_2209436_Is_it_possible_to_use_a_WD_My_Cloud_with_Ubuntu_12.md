---
title: "Is it possible to use a WD My Cloud with Ubuntu 12.04?"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by sillyboy on 2014-03-05
Would I be able to do automatic backups if I used a personal cloud device?  If so what device would work with 12.04, without jumping thru flaming hoops?  I'm using Gnome 2 desktop.

Thanks

---

### Post by Mark Phelps on 2014-03-05
If by "personal cloud device", you mean an external drive -- two things I would avoid are WD and USB 3.0.  

WD often sells external drives that come with Window front-end hard-wired into the system to support encryption.  IF you try to use one of those, you won't be able to access the drive other than through MS Windows.

USB 3.0 should not be causing problems, since Linux has had USB 3.0 support for some time, but we keep seeing lots of posts from folks with just those problems.  USB 2.0 has been around a lot longer, and while it is much slower, it does work.

---

### Post by nunecas123 on 2014-03-06
Unfortunately, WD inserts futile things to the HDD for some reason - and sometimes you can't even delete them. But normally, you can use external hard drives on Linux with no problem at all.

I have myself a WD and everything works fine. There are some nuances when using some features included on the disk because they are not compatible - basically, they think that Windows is the only OS out there.

Try using Wine on Linux if you have problems running Windows software.

---

### Post by Mark Phelps on 2014-03-06
> Try using Wine on Linux if you have problems running Windows software. 

Yeah ... but .. in my experience, using Wine was essentially a waste of time.

BEFORE you charge down that path, use the WineHQ website to look up compatibility ratings for the apps and versions you want to run.  Anything not listed, or rated less than Gold, is essentially going to be a waste of time installing.

---

### Post by Habitual on 2014-03-06
You may have to delete the partition that ships on the device, I had to on my WD MyBook 3Tb USB device.

gparted and nuke it to orbit, then create a linux compatible FS (ext4 for example).
You're device will be "good to go".

---

### Post by kurt18947 on 2014-03-06
> **Habitual said:**
> You may have to delete the partition that ships on the device, I had to on my WD MyBook 3Tb USB device.

gparted and nuke it to orbit, then create a linux compatible FS (ext4 for example).
You're device will be "good to go".

That sounds like a good solution.  My backup needs are probably pretty basic but using Lucky Backup to sync directories/folders seems to work just fine.  I don't worry about whole disk backups, just data folders.  I'm using Ubuntu-Gnome 14.04 and it has a "backups" app.  That might be another possibility though I've never used it.  If the backups app creates a compressed file, I'd be leary of it.  My personal preference at least for data files is to save them in a native uncompressed state.  That way I can use any app capable of reading that format without first having to process a compressed file and risking corruption along the way.  Of course I don't have much in the way of data and storage is cheap.

---

### Post by nunecas123 on 2014-03-07
> **Mark Phelps said:**
> Yeah ... but .. in my experience, using Wine was essentially a waste of time.

BEFORE you charge down that path, use the WineHQ website to look up compatibility ratings for the apps and versions you want to run.  Anything not listed, or rated less than Gold, is essentially going to be a waste of time installing.

That's why I said try. Wine has a lot to grow, still. At least it runs some programs well.

---

### Post by texaswriter on 2014-07-05
This may be relatively new information, but I found this on Google and it seems relevant: [http://www.huffingtonpost.com/dulio-denis/wd-my-cloud-nas-on-ubuntu_b_5121961.html](http://www.huffingtonpost.com/dulio-denis/wd-my-cloud-nas-on-ubuntu_b_5121961.html)

You may decide that formatting is the best thing for you, but the devices are designed to connect to PCs/MACs/smartphones/web. SOURCE: [http://www.wdc.com/en/products/products.aspx?id=1140](http://www.wdc.com/en/products/products.aspx?id=1140)

This was the pertinent information from the first linked site.

> But it was easy enough to connect my Lubuntu laptop as a Network File System (NFS) Client via three shell commands.First, I changed directory to my home directory and created a nfs directory in there:
$ cd $HOME
$ mkdir nfs
Then I applied the following three shell commands:
$ sudo apt-get install nfs-common
$ showmount -e 
$ sudo mount -o soft,intr,rsize=8192,wsize=8192 192.168.1.132:/nfs /home//nfs/
If  you cd into nfs you'll be accessing the WD My Cloud device. That's it. I  started to copy twenty mp4 files totalling 1.6GB into the device  through 802.11g and it took 8 minutes. I was then streaming these on my  iPad mini.
I hope this helps assure you you can connect to this  from Linux. I know once I finished the plug and play I panicked for a  bit thinking I wouldn't be able to connect my Linux machines to this  device but now I happily throw everything I have onto this. Also, it has  a USB 3 port on the back so I can simply plug another 4TB USB drive on  it and expand it in the future.



HTH

---

### Post by texaswriter on 2014-07-05
Sorry for the double post: 

Another link for reference: [http://community.wd.com/t5/WD-My-Cloud/Question-about-linux-and-My-Cloud/td-p/600627](http://community.wd.com/t5/WD-My-Cloud/Question-about-linux-and-My-Cloud/td-p/600627)

---

