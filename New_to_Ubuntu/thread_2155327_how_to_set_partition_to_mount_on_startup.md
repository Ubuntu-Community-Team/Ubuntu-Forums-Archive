---
title: "how to set partition to mount on startup"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by BigZ1981 on 2013-06-17
Hi guys, seeing as I'm really new to Linux, period, I'm still learning the ins & outs & without much time during the day to do so, which puts me on a slow learning curve.  Here's thing:  I set up a separate ext4 partition to make FFR easier if I need to (hope that with the switch to Linux, I no longer have to worry about doing it much).  It's of course set up under media & shows up in Dolphin as another drive.  However, if I want to access it, I always have to go into Dolphin first & mount it (easily done just by clicking on it to open it up, but a bit of an inconvenience to do it every time I start up), and I don't remember to do it right after I start up.  So if I want to set Amarok to access my music on that partition, it doesn't exist until it's mounted.  I'm thinking there is a way to do this since Linux was created for the user to customize to his/her own desires granted s/he knows how to manipulate the system well enough.  Thanks in advance for the help.

---

### Post by papibe on 2013-06-17
Hi BigZ1981.

Take a look at this [tutorial]("https://help.ubuntu.com/community/AutomaticallyMountPartitions").

Let us know if you need any help with that.
Regards.

---

### Post by BigZ1981 on 2013-06-18
VERY informative.  Thank you.  I couldn't do the system-wide mount, but then I saw a line that directed me into system settings, so I looked in there, and found the option for mounting it under removable devices.  This brings up another question, though. How do I changed the system-assigned UUID for it?  It's difficult to use if I want to link directly to it when using terminal...or can I link directly as "/dev/sda6"?

---

### Post by dave2001 on 2013-06-18
Ubuntu handles mounting drives with a file called "fstab", which is short for file system table i'd imagine. 

In order to open it with appropriate root editing privledges, type the following into terminal: 
```
gksudo gedit /etc/fstab
```
input password and you should see the file. Save a backup copy as fstab.bak before altering it.

your going to add a new line at the bottom of fstab telling your comp to mount the seperate ext4 partition. It will look something like this:
```
/dev/sda2    /YourMountPoint        ext4    defaults  0       0
```

The only thing you'll need to change is /dev/sda2, to match the identifier of your parition. You can also change the YourMountPoint to where ever you want the parition mounted. Next time you reboot, it should auto-mount.

Let us know if you have questions!

---

### Post by BigZ1981 on 2013-06-18
Thanks Dave.  I did try that, but got a mounting error when I restarted to test it.  The line I put in was:
```

/dev/sda6     /media/storage     ext4     user,fmask=0111,dmask=0000     0     0

```

So I simply just set it to "Automount on login" in System Settings > Removable Drives.
Guess I should have looked there before asking the question, but hindsight is 20/20.

So, like my previous question, if I want to navigate to the partition using terminal or anything else that requires me to type a path, can I get there using /dev/sda6 or do I need to use the UUID, and if I need to use the UUID, is there a way to change it from the system-assigned default?

---

### Post by CatKiller on 2013-06-18
I believe that if you give the partition a label it will be automatically mounted using that rather than UUID.

Using the UUID in fstab is recommended, however.

Although I would personally persevere with the fstab approach, having it mounted to a location based on it's UUID isn't functionally that problematic. If you're clicking on it, it doesn't really matter what it's called, and Tab-completion means that you never need to actually type it. It just doesn't look pretty.

You wouldn't use the /dev/sda6 path; that refers to the device rather than the filesystem on it.

---

### Post by Impavidus on 2013-06-18
> **BigZ1981 said:**
> Thanks Dave.  I did try that, but got a mounting error when I restarted to test it.  The line I put in was:
```

/dev/sda6     /media/storage     ext4     user,fmask=0111,dmask=0000     0     0

```
(...)
In principle that line should work. You have to make sure the mount point exists before mounting the partition, in other words, create the directory /media/storage. The option "user" is not necessary if you're automounting it at boot. I'm not sure about the fmask and dmask options. To make sure you can access the partition, give yourself permission to read/write/execute the mount point, or make a directory inside with those permissions. You'll be able to access it through /media/storage. You don't have to reboot to test it, giving the command```
sudo mount -a
```is enough.

If it doesn't work, can you post the error message?

Edit: I checked the manual. fmask and umask are for mounting fat partitions, not ext4 (as Morbius1 said below).

---

### Post by Morbius1 on 2013-06-18
> **BigZ1981 said:**
> Thanks Dave.  I did try that, but got a mounting error when I restarted to test it.  The line I put in was:
```

/dev/sda6     /media/storage     ext4     user,fmask=0111,dmask=0000     0     0

```

So I simply just set it to "Automount on login" in System Settings > Removable Drives.
Guess I should have looked there before asking the question, but hindsight is 20/20.

So, like my previous question, if I want to navigate to the partition using terminal or anything else that requires me to type a path, can I get there using /dev/sda6 or do I need to use the UUID, and if I need to use the UUID, is there a way to change it from the system-assigned default?
** You can't set a file or directory mask on an ext4 partition in fstab.
** If you are going to do this use UUID's instead.
** I don't use KDE but it sounds like "AUtomount on login" is using udisks so the way to change the automatically generated mount point is to change the label of the partition - or in your case add one. 

There's a way to do that from the terminal which I can never remember without my notes so I would suggest you use gparted to do it. Once you change the label it should mount to /media/LABEL or /media/$USER/LABEL depending on which version of Kubuntu you are using.

---

### Post by dave2001 on 2013-06-18
> **BigZ1981 said:**
>  if I want to navigate to the partition using terminal or anything else that requires me to type a path, can I get there using /dev/sda6 or do I need to use the UUID, and if I need to use the UUID, is there a way to change it from the system-assigned default?

Once you have a partition mounted, you should access it through the mount-point. (eg. /media/storage). 

For manipulation of the actual partition you can use the device designation (dev/sda6), but UUID is more robust. I'm not sure about changing  system assigned UUID's, I've never looked into it.

---

### Post by BigZ1981 on 2013-06-18
Awesome!  Thanks for the help!  I got everything up & running with my desired UUID & fstab edited properly.  So kubuntu uses the partition's label as the UUID when mounting, and generates a random one if there isn't one.  That's good to know.  Thanks for the tip on the options...I wasn't sure what to put in there so I went by the example in the tutorial...defaults is all I need unless I want something special.

---

### Post by CatKiller on 2013-06-18
No, the partition still has a UUID. Kubuntu uses the UUID for the mount point if it doesn't have a label. UUIDs are generated at partition creation, IIRC.

---

### Post by Morbius1 on 2013-06-18
> **BigZ1981 said:**
> Awesome!  Thanks for the help!  I got everything up & running with my desired UUID & fstab edited properly.  So kubuntu uses the partition's label as the UUID when mounting, and generates a random one if there isn't one.  That's good to know.  Thanks for the tip on the options...I wasn't sure what to put in there so I went by the example in the tutorial...defaults is all I need unless I want something special.
There is no randomness. udisks will mount to /media/LABEL if the partition has a label. It will mount to /media/UUID if there is no partition label. 

You can circumvent this by creating a entry in fstab enabling you to mount it wherever you please.

---

### Post by dave2001 on 2013-06-18
> **BigZ1981 said:**
> Awesome!  Thanks for the help!  I got everything up & running 

Glad you got all the info you needed! The forums are a great community, and one of the things I find most impressive and appealing about Ubuntu and it's derivatives.

Oh, and remember to mark your threads "solved" once the initial problem is answered to your satisfaction!

---

### Post by Paqman on 2013-06-18
Just one nitpick:

> **dave2001 said:**
>  
```
gksudo gedit /etc/fstab
```


On a KDE system that should be:
```
kdesu kate /etc/fstab
```

---

### Post by BigZ1981 on 2013-06-18
> **CatKiller said:**
> No, the partition still has a UUID. Kubuntu uses the UUID for the mount point if it doesn't have a label. UUIDs are generated at partition creation, IIRC.

> **Morbius1 said:**
> There is no randomness. udisks will mount to /media/LABEL if the partition has a label. It will mount to /media/UUID if there is no partition label. 

You can circumvent this by creating a entry in fstab enabling you to mount it wherever you please.


Right.  The randomness I'm referring to is the system-generated UUID, itself.  I know it stays the same once it's initially generated, but it generates a random UUID at that point.  Gparted had an option to change to a new system-generated UUID.  Considering that my partition is now labeled, I don't have to worry about that.  Marking solved now.

---

