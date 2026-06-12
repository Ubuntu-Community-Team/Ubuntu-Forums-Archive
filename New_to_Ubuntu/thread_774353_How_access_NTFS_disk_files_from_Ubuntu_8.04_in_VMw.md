---
title: "How access NTFS disk files from Ubuntu 8.04 in VMware Player?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by FuturePerfect on 2008-04-29
I am running Ubuntu 8.04 in VMware Player 1.03 under Windows XP Pro SP2 with latest patches using an 80GB NTFS disk.

But I can't find and access my NTFS hard disk files.

I CAN access NTFS files on a CD by double-clicking Computer from the 8.04 desktop.

But I can't find my NTFS hard disk files in Computer.  The only devices I see in Computer are:

CD-RW/DVD-RW Drive
Floppy Drive
Ubuntu 6.10 i386 (VMware player--been using since Ubuntu 6.10)
Filesystem

Thanks for any help on opening my NTFS hard disk files.

---

### Post by forrestcupp on 2008-04-29
You really can't do what you are wanting.  In a virtual machine, everything is contained within that machine.  The only way to do it is to create a virtual network between the guest and host systems and set up a shared folder to share files with.

[Here](http://www.vmware.com/support/ws3/doc/ws32_running9.html) is what vmware has to say about doing that.

---

### Post by PeterJS on 2008-04-29
I would assume you're trying to access the ntfs partition on your physical disk. The thing about virtual machines is that they are virtual, and by design have no understanding of the encapsulating physical host system. You'll have to share the disk over the VM network using samba.

---

### Post by bdailey on 2008-04-29
NTFS is how your hard drive is partitioned. When you have files on a CD they are not stored in NTFS.  8.04 can handle NTFS formated hard drives. I can see my Vista partitions fine. It sounds like you don't have file sharing turned on in VMware. I don't believe that it is turned on by default. I don't have too much experience with VMware Player but I believe this is where the problem is. Hope this helps narrow down your search.

---

### Post by FuturePerfect on 2008-04-29
Wow!  You guys respond FAST!  

As you can see, I am new to the Ubuntu Forum.  So I hope I am responding correctly.

I see you all have a Thanks count.  I'm don't know how to get that incremented automatically, but let me thank each of you that responded:

forrestcupp:  thanks for pointing me to the VMware page--I couldn't find it with my many Google searches

PeterJS:  thanks for pointing me to samba

bdailey:  thanks for letting me know that my CD is not really NTFS and mentioning looking for VMware sharing

After looking at references above, I see that, for my level of expertise, NTFS disk access will be more of a science project than the cookbook I was hoping for.  The VMware article is great, but finding how to address my same hard disk where my VMWare virtual machine lies will require more research.

You guys have pointed me in the right direction.  Thanks again.

---

### Post by mijanous on 2008-05-19
I was trying it in vmware server by adding another "virtual" hard drive by physical ntfs partition however the vmware shown an error that i don't have permissions....but i run the vmware also as sudo and normal user but no success....can somebody respond on this ?

---

### Post by gm.matias on 2010-02-12
I am using VMPlayer and in the configuration I enabled the Share Files options but it did not work for me. I read some more articles and found a good solution that works for me. I put in here: [http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12](http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12)

Hope it helps.

---

