---
title: "Dual Booting Ubuntu and Vista"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by ikick on 2008-07-08
Hi there everyone.

Today i bought my brand new 160gig SATA hard drive.
I would like to be able to use the latest version of ubuntu on the new hard drive without having to format **OR** modify (within reason) windows vista on the current hard drive (also a 160gig SATA).


If there is another way, i would be so very greatful if somebody could please provide assistance.

I DON'T want to make another partition on my C:\ drive as i already have one and i did not just buy this new hard drive for nothing.

Regards,
D Jones

---

### Post by westentertainer on 2008-07-08
i have vista and ubuntu dual booting no problem i had vista instaled first on a 160 gig hd and then booted from ubuntu disk and then in the partitioning menu during install .chose guided then allocated ubuntu to the sata drive  all with no problems

---

### Post by Cypher on 2008-07-08
Insert the new drive, put in the Ubuntu Live CD and ensure that everything works OK on your machine. Then install Ubuntu and make sure that it uses the unformatted new drive as opposed to the existing Windows drive. Allow it to install GRUB on the primary HD and it will now give you the option of booting into Windows or Linux each time you boot up.

---

### Post by Bigtime_Scrub on 2008-07-08
If it is an external drive I would unplug my internal HD first and then boot into the Ubuntu Live CD. 

Then plug in the external HD and install as normal to it. Be sure to use the entire disk with it and you should be all set.

---

### Post by ikick on 2008-07-08
Thanks very much for all your posts.

I will attempt to what Cypher has suggested and i will get back to you.

Regards,

ikick

---

### Post by Bucky Ball on 2008-07-08
I have 3 comps, all booting a different version of Ubuntu with a different version of Windows! lol

Go with Cypher, baby Tux is his right hand penguin. :p

---

### Post by ikick on 2008-07-08
Will do..

[offtopic] Australia ftw? 

heheh :p
thanks for all support...... Im going in ;)

---

### Post by fidamehran on 2008-07-08
I think the main point is "ikick" wants not to partition or repartition his harddisk to install Ubuntu. While it is not possible for many (or any) other OSs, you can do it in Ubuntu.

The latest version of Ubuntu comes with "Wubi". Wubi is a virtualization program which will install Ubuntu within your Windows partition and not repartition your harddisk or anything.

You also don't need to have enough technical knowledge to partition a harddisk. By using Wubi, Ubuntu will install itself in the existing Windows partition just like any other Windows program. When you want to uninstall Ubuntu, all you need to do is uninstall it from Add/Remove.

Wubi is so easy, you will have a laugh yourself with it.

Enjoy it. Enjoy Ubuntu.

---

