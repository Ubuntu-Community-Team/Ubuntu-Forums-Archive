---
title: "HOWTO: Change auto fsck after &quot;X&quot; reboots"
date: 2006-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-03-04
The default fsck (File system check) of your Ubuntu root partition is 30 reboots (or six months after the last reboot, whichever comes first). These settings are part of the ext2 filesystem that Ubuntu defaults to and can be easily changed, but to do so **you must be very careful with the command used as it could potentially do a lot of damage is used incorrectly!**

If you want to change the count of when the auto fsck is done (to 20 instead of the default 30, for example), do (and replace the "your-filesystem-partition" with the appropriate hda or sda designation of your partition):
```
sudo tune2fs -c20 /dev/your-filesystem-partition
```
To also set a fsck check after a certain period of time since the previous reboot (this example will set it to 1 week, "-i1d" would set the interval to 1 day, "-i1m" one month etc.), do:
```
sudo tune2fs -i1w /dev/your-filesystem-partition
```
You can individually alter all of your ext2/ext3 filesystems in this way, and the tune2fs man page has many more options (like setting a partition label) which may be of use.

To see the settings for a particular ext2/ext3 filesystem:
```
sudo dumpe2fs -h /dev/your-filesystem-partition
```

---

### Post by tienhn on 2007-11-01
This is a good tip. However, my wish would be to have the boot up process to prompt the user with a Yes or No if the user want to delay the fsck for this booting.

I have a laptop and I travel a lot. So as Murphy's law states: this 30 reboot  fsck will always come up when I am at the airport with 10 minutes to board the flight. Now the booting process become a 20 minute deal!!!

Why can Ubuntu prompt the use: "Check now Yes or No?"

Cheers,

---

