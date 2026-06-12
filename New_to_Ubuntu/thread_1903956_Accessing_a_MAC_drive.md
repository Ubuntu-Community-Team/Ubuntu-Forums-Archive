---
title: "Accessing a MAC drive?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by roger465 on 2012-01-03
Hi folks – please be VERY gentle with me as I’m a beginner to Things Unix. I repair PC’s for a living, but up to now really only understand Windows (sorry…). Anyway, I have this customer’s dead Mini Mac, and have taken the 2½” SATA drive out of it and slaved it off the PC I’ve just installed Ubuntu 10.02 on.
   
  I can mount the drive in File Browser, but can't read any of the contents of its folders (I just want to copy the guy’s pictures to somewhere more accessible, then throw the Mini Mac away as it's knackered). The folders all appear empty, but I’m sure they’re not – the Disk Properties show 50GB used space.
   
  I’m assuming this is a security issue – but, if I try and change anything, it says I can't because I’m not the owner.
   
  Is there a simple, beginner-friendly way to take ownership of this drive, like I could in Windoze?
   
  Thanks in advance :-)

---

### Post by coffeecat on 2012-01-03
> **roger465 said:**
> 
  Is there a simple, beginner-friendly way to take ownership of this drive, like I could in Windoze?

Not quite!

There are two issues getting in your way. First - the drive will be formatted with the journalled version of Apple's HFS+ filesystem which Linux can mount read-only. Hence you can't change anything. (In fact you can mount it read-write with a force option, but I wouldn't recommend it. Also - as an aside - had the HFS+ filesystem been non-journalled, then it would have been mounted read-write. But's that's somewhat theoretical in your situation.)

The other issue is one of Unix permissions and ownerships, Linux and MacOS using the same system. The UID of the Mac personal files will probably be 501, and the UID of the account you are using will be 1000. That's why you get a "you are not the owner" message.

The workaround is fairly straightforward, and requires the use of a root-owned Nautilus file-browser. Plug the drive in and let it be automounted. Close the Nautilus window which opens - you won't need it. Now open a terminal and:

```
gksu nautilus /media
```

A root nautilus will open in the system /media folder and you will see one or more folders, one of which will be the mountpoint for the Mac drive. Open the one that seems most likely and you will see the MacOS filesystem. Browse to the folder where the personal files are and then copy them with a drag and drop in the usual way.

The one disadvantage is that the files may end up being owned by root once they are copied to your Ubuntu filesystem. I'm not 100% sure - it's been a little while since I've had to do this. If they are owned by root, post back and we'll take it from there.

**EDIT**: one way round the root-owned issue - if it occurs - is simply to copy the files to a NTFS filesystem which Linux can mount read-write. Plug your HFS+ drive in. Plug a second USB NTFS-formatted drive in (or use an internal partition). Then drag-copy from the root nautilus showing the Mac files to an ordinary nautilus open in the NTFS drive/partition. Since NTFS doesn't support Unix permissions/ownership, you lose them when you copy files to NTFS - which can be useful in a situation like this.

---

### Post by 741Baus on 2012-01-03
Hi roger465 to access that HHD you need to open the terminal Ctrl/Alt/T and run these commands 

```
sudo apt-get install hfsplus libhfsp0
```

```
gksu nautilus
```

the later command will open nautilus file manager with root privileges and you should be able to navigate to and back up those files .

---

### Post by coffeecat on 2012-01-03
@741Baus, I know it has been posted many times on this forum, and no doubt will continue to be, but you do not need to install the package hfsplus in order to read HFS+ filesystems. (Or write to non-journalled HFS+ filesystems.) Ubuntu uses the hfsplus kernel module and reading HFS+ works out of the box without the need to install anything. At least it does in this household.

---

### Post by 741Baus on 2012-01-03
Thanks for that Coffeecat thats some thing I didn't know.

---

### Post by coffeecat on 2012-01-03
Yes, it's strange. Both the packages you mention are official Ubuntu ones, and the package descriptions of both in Synaptic suggest that they are necessary for accessing HFS+ filesystems, yet neither are in a default install and a default install is capable of accessing HFS+ filesystems. So quite what advantages - if any - those packages confer, I do not know. :)

For the record I am running Oneiric, I have neither of those packages installed, and I have just retested two external drives, one formatted HFS+ journalled, the other HFS+ non-journalled, both formatted from Snow Leopard in my Mac Mini. They mount read-only and read-write respectively just fine.

---

### Post by roger465 on 2012-01-03
Thanks a lot guys - just shut the machines off to go to bed! Will try tomorrow and post here... I'm now beginning to suspect that the MAC drive may be a little faulty too, and I daren't run any kind of checkdisk utility on it, as I don't know which one you;d use for a Mac disk...

---

### Post by coffeecat on 2012-01-03
@roger465, I've just discovered something unexpected which may mean that even a gksu nautilus browser may not cope with some of your files. Long story short: I've been doing some experimenting with my HFS+ journalled USB drive, and I copied some files from my Mac desktop simply to double-check the point 741Baus and I were discussing. It seems my Mac has assigned such restrictive permissions to some (but not all) the files that I cannot copy them even with a root nautilus.

Try a root (gksu) nautilus browser anyway. If you still get problems with some of the files, post back.

Question: can you get access to another Mac? One answer might be to use another Mac to recursively change all permissions on all files on that drive in order to simplify things. I can tell you how if necessary.

I have to log off now - late here - but I'll check this thread in the morning.

---

### Post by roger465 on 2012-01-03
> **coffeecat said:**
> Question: can you get access to another Mac?

 My first thought! Yes, my daughter has a little MacBook – but I have no USB adapter for one of these drives. I keep an old dual-boot PC for this kind of thing, and it just has a SATA cable hanging out the side!

---

### Post by roger465 on 2012-01-04
Yes, that gksu command opened a window, and I was now able to right-click on MACINTOSH HD, do Properties, and everything was available for changing (I didn&#8217;t; change anything though), where it wasn't before, so thanks for that.
   
  Unfortunately&#8230; all the Mac disk&#8217;s folders still appear to be empty, even though the drive shows as over 50% full. This disk definitely has issues &#8211; sometimes it comes up, sometimes it doesn't, and occasionally makes that ominous clunking sound that they do when they&#8217;re knackered. Also sometimes the machine fails to boot, with some kind of Linux error concerning inability to find the boot device. This never happens when the Mac drive isn&#8217;t connected, and the actual boot drive is good, so I assume the Mac one is failing sporadically, soon to become permanent.
   
  I&#8217;m assuming that running any kind of non-Mac disk utility on it would be folly, so I think the only thing I can do is take the disk out of my daughter&#8217;s MacBook, put this in, boot off the MacOS DVD, and try a disk repair. If that doesn't work, I guess the customer&#8217;s stuffed :-(
   
  Getting out of the realms of Ubuntu here a bit too, sorry about that!
   
  Thanks so much for your help. I&#8217;ll still post if I get anywhere, in case anyone&#8217;s interested &#8230;

---

### Post by coffeecat on 2012-01-04
> **roger465 said:**
> Yes, that gksu command opened a window, and I was now able to right-click on MACINTOSH HD, do Properties, and everything was available for changing (I didn’t; change anything though), where it wasn't before, so thanks for that.

You'll find you get an error if you try to change anything, since the drive will be mounted read-only. 
   
> **roger465 said:**
>   Unfortunately… all the Mac disk’s folders still appear to be empty, even though the drive shows as over 50% full. This disk definitely has issues – sometimes it comes up, sometimes it doesn't, and occasionally makes that ominous clunking sound that they do when they’re knackered. Also sometimes the machine fails to boot, with some kind of Linux error concerning inability to find the boot device. This never happens when the Mac drive isn’t connected, and the actual boot drive is good, so I assume the Mac one is failing sporadically, soon to become permanent.

I agree - that does sound like a failing drive. There is something you can do in Ubuntu, not that it will help much. With the Mac drive attached, open the Disk Utility app. Highlight the Mac drive and look for the SMART data somewhere on the right. If SMART is supported in that drive, you can run some self-tests.
   
> **roger465 said:**
>   I’m assuming that running any kind of non-Mac disk utility on it would be folly, so I think the only thing I can do is take the disk out of my daughter’s MacBook, put this in, boot off the MacOS DVD, and try a disk repair. If that doesn't work, I guess the customer’s stuffed :-(

Good luck!

---

