---
title: "Removing Ubuntu from dual boot desktop"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Autodave on 2012-06-06
I have a machine that is being recommissioned.  It currently has Ubuntu 10.04 and Win XP on it.  It's new use will require Windows, so I need to either remove Ubuntu and then need to know how to give the disk space all to XP.

If that is not possible, then can I at least shrink the Ubuntu partition and allocate the space to XP?

Lastly, it not possible or easy to delete Ubuntu, how can I at least change the order in the boot menu so that XP would be the only choice or at least the *first *choice?

Thanks in advance!

---

### Post by Curtis6767 on 2012-06-06
Do you have the required XP or other Windows install disk? Will the new use of this computer require a fresh install of Windows? 

If you or someone else is going to do a fresh Windows install on the machine, that fresh install will wipe out Ubuntu.

---

### Post by malangaman on 2012-06-06
I use a nice GUI utility called "Start Up Manager" to change the order and time the grub screen paints the screen, among other settings:
[(https://launchpad.net/startup-manager)"][https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)]("[https://launchpad.net/startup-manager)

It may be available through synaptic?

What version of Ubuntu are you using?
Is it a dual boot on one drive?

---

### Post by Autodave on 2012-06-06
The OE XP disk is long lost, so I do not want to erase XP.  I would either like to remove Ubuntu and resize the partition for XP to use all of the disk.  If easier, shrinking the size of the partition that Ubuntu uses and giving that extra space to XP would be great.

Lastly, I will check out that link about modifying GRUB.

---

### Post by NikTh on 2012-06-06
> **malangaman said:**
> I use a nice GUI utility called "Start Up Manager" to change the order and time the grub screen paints the screen, among other settings:
[(https://launchpad.net/startup-manager)"]]("http://[https://launchpad.net/startup-manager)[https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)

It may be available through synaptic?

What version of Ubuntu are you using?
Is it a dual boot on one drive?
Hi @malangaman
Startup manager is a dead project right now , you can see it in the link you quoted. 

To manage boot options i recommend [Grub Customizer](http://ubuntuforums.org/showthread.php?t=1664134) 
 Hi , 
@Autodave : If you want to remove Ubuntu you can . You can inside of windows. You must go to disk manager (from control panel if i remember correctly) and delete Ubuntu entry (it will shown up as unknown filesystem) ,** but you must have a windows disk** , because system will not boot (witout grub , grub will also deleted with Ubuntu) and you must boot from windows cd to repair you installation. 

Second option is also possible . You can boot from a Ubuntu live cd and try to shrink the Ubuntu partition. (always from the end to the begin) This is more dangerous because you can end up with a non bootable Ubuntu system . So use it with caution . 
Then you can reformat the new partition to NTFS so windows will see it. 
Thanks

---

### Post by Autodave on 2012-06-06
Thanks, all!

---

