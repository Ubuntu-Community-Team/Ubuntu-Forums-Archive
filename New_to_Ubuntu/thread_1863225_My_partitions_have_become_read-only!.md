---
title: "My partitions have become read-only!"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Milind on 2011-10-17
I changed from Ubuntu 11.04 to 11.10 and now all my logical partitions have become read-only. I can't change the permissions. "Create New Document" and "Create New Folder" are grayed out. I keep getting the following message :

"Sorry, could not change the permissions of "1860A7A760A78A58": Error setting permissions: Read-only file system."

I want to set permission for all partitions, folders, and files as read and write. Please advise.

---

### Post by mcduck on 2011-10-17
That sounds like it's not actually a permission issue, but instead the Linux kernel has found some problems with the filesystems on those partitions, and has changed them to read-only mode to protect your files from any further damage.

If the partitions in question are using Linux filesystems, then unmounting them and running fsck on them should fix the issue and allow them to be mounted in read/write mode again. You can also do that from a live-CD if the partitions are used for some purpose that dosn't allow you to unmount them while running your Ubuntu install.

And if they are Windows filesystems, you should boot to Windows and run chkdisk to repair the filesystems.

---

### Post by audeojude on 2011-10-17
arggg. i just had the same thing happen. I have like 4 ntfs drives as storage drives and it did the same thing this morning. Was working fine since I upgraded to 11.10 64bit two days ago and just changed.

this is pissing me off. I don't have windows on this system at all.

---

### Post by audeojude on 2011-10-17
Ok I just ran chkdsk /f off a windows recovery disk on all 4 ntfs storage drives and then rebooted the system back into 11.10 and it is still doing the same thing. most of the drives had no errors and the one that did it fixed.

Two of these drives are on an internal sata controller and two of them are external USB

So what is the deal?

---

### Post by Milind on 2011-10-17
> **audeojude said:**
> Ok I just ran chkdsk /f off a windows recovery disk on all 4 ntfs storage drives and then rebooted the system back into 11.10 and it is still doing the same thing. most of the drives had no errors and the one that did it fixed.

I'm facing the same situation. Ran chkdsk /f on all drives, then booted back into Ubuntu.No change. Anyway, it's getting very late and I can't keep my eyes open any more. I'll resume trying to fix this problem in the morning.

---

### Post by audeojude on 2011-10-17
This is becoming a endemic issue. I think there has been a security update or something that has caused this behaviour. I am having read only problems with sata drives, usb drives etc... As I look around the forums I am finding more and more people reporting this exact same problem.

Lots of experts are telling people if its ntfs or fat drives to scan them with chkdsk /f to repair issues that would cause the Linux kernel to only mount  read only. However of the four drives I have checked only one had errors and even when fixed, my 11.10 installation will not mount the drives read write.

My guess is someone blew it big time and pushed out a security fix or kernel with major issues.

---

### Post by audeojude on 2011-10-17
If someone knows whats going on I would appreciate it if you take the time to let us know :)

---

### Post by Milind on 2011-10-18
An OS which doesn't let me use my files and folders, nor create new ones isn't of any use. I've formatted the Ubuntu partition and installed Ubuntu 11.04 again as I could find no solution that worked. Better an older OS that works than a newer one that screws up.

---

### Post by ninjaaron on 2011-10-18
I don't have a fix, unfortunately, but I will say that stuff like this sometimes happens in the new releases if nobody was testing with certain hardware during the development cycle.  Most issues of this kind get fixed within the first month after release.  The best way to make sure problems of this sort don't affect your machine is to become a beta-tester and make bug reports.

---

### Post by mikechant on 2011-10-18
I found this link in another thread about this issue:
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-ntfs-config-in-ubuntu.html)

The post doesn't explain why this is relevant, but I assume they are implying that 11.10 comes up with NTFS writes disabled by default, and installing and using the ntfs-config package will allow you to switch NTFS write support on.

Worth a try as it should only take about 20s!

I'd try it myself on my 11.10 test install but I'm not at my Ubuntu PC at present...

---

### Post by Goncezilla on 2011-10-18
I had this problem myself on my HP DM1Z-3000 after upgrading to 11.10. It seems that the new fstab automatically locks out the root drive if an error is found. Just adjust fstab to get around this.

1. ```
sudo nano /etc/fstab
```
2. Find the line that deals with your / partition (usually sda1)
3. Delete the part that says something like ```
error=remount ro
```
4. Replace the deleted part with ```
defaults
```
5. Save using CTRL-O or CTRL-X
6. Reboot

Now to fix my graphics again and figure out why there are errors on my drive in the first place!

---

### Post by Rocky1937 on 2011-10-18
I have also had this problem appear.  Mine are all USB external drives.  Three connected to my desk top machine and the other on my laptop.

I upgraded to 11.10 early last week but the read only error popped up yesterday on the desk top and today on the laptop.  The internal drives on both computers are fine though -- go figure!  One of the USB drive was brand new and was almost instantly read only!

I agree that the problem is update related.  More than likely happened over the weekend or yesterday morning.

---

### Post by audeojude on 2011-10-20
This just started to happen to my laptop a few seconds ago. and I have run no updates. I have been writing many gigs of data to external sd cards and usb drives yesterday and today. I just finished moving a 1 gig file to a usb drive and went to copy a second file out to it. I re-opened the drive and it was now read only. so in a matter of a maybe 60 seconds it went from read write to read only.

so now two of my computers are doing this ****. However the laptop is 11.04 not 11.10

seriously scratching my head.

---

### Post by audeojude on 2011-10-20
Laptop results might be anomalous. After rebooting the laptop I could read right again. still weird. Laptop is 11.04

desktop is 11.10 and is still read only for every drive but /

---

### Post by audeojude on 2011-10-22
Ok I have fixed mine.. 

It seems to be a problem in ntfsprogs and the kernel. I have tried a couple kernels and no luck. Then I installed ntfs-3g which automatically un-installed and replaced ntfsprogs and my read write ability on my usb drives and even my ntfs sata drives came back.

so the solution was to go 

sudo apt-get install ntfs-3g 

allow it to uninstall ntfsprogs

it takes a while to un-install and install as it has to recompile a bunch of kernel drivers. I had upgraded to the latest stock 3.0.13 kernel in updates just before trying this.


what a pita though. in changing permissions and playing with settings I killed my ability to log into my user directory. I had to delete that and create a totally fresh user directory and then copy back into the new one all my data and application configurations. 

Mostly Ubuntu just works which is what I like. Years ago I loved digging under the hood and customising and tweaking. Nowadays I just want my applications and Internet to work.

---

