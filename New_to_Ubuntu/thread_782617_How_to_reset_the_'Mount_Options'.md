---
title: "How to reset the 'Mount Options'?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by chingdaotze on 2008-05-05
Hello, I'm an absolute newbie at Linux, so use nice words please?

I was messing with the drives under the "Places" folder because I was trying to get my NTFS partition to mount on startup.  I entered 'auto' into the "Mount Options" text field when right-clicking on the drive, and now I get a "You are not privelaged to mount this volume." message.  I tried resetting the volume in fstab, but it seems like I get the same error, even when using an fstab configuration that worked before (which already took into account the NTFS volume).

I was wondering if there's any way to reset the text field of the drive?

Here's the fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25beb37a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14231   114310476    7  HPFS/NTFS
/dev/sda2           14232       18729    36130185   83  Linux
/dev/sda3           18730       19457     5847660   82  Linux swap / Solaris

and here's my current fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c1b7d2f9-2de2-4f52-82c8-8bf9374095c6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4e51a5bb-dfe2-4b30-ad6a-cd0803cae101 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda1
UUID=B078AF2C78AEEFF0 /media/hda1 ntfs defaults 0 0

I've tried the above configuration before with no problems, until I entered "auto" into the text field.

---

### Post by hermes0710 on 2008-05-05
I haven't tried entering mount options through nautilus the way you described but what to you get if you right-click again and select Mount Options? Is there an entry "auto"? If yes remove it.

---

### Post by Rocket2DMn on 2008-05-05
What happens when you run
```
sudo mount -a
```

---

### Post by chingdaotze on 2008-05-05
Thanks for your help guys!

I booted Hardy this morning, and it looked like it reset itself.  Solved!  Though this was kind of strange, because I tried rebooting to reset last night and it didn't work...

---

### Post by chingdaotze on 2008-05-05
On a related note, do you know how to configure my fstab so that it does load my ntfs partition on startup?  Thanks!

---

### Post by Rocket2DMn on 2008-05-05
Anything in fstab should load automatically at startup be default, though you can explicity append the "auto" option to the options column, so it looks like
```
UUID=B078AF2C78AEEFF0 /media/hda1 ntfs defaults,auto 0 0
```
Also, you may want to specify a locale for character encoding purposes
```
UUID=B078AF2C78AEEFF0 /media/hda1 ntfs defaults,locale=en_US.utf8,auto 0 0
```
If you wanted it to NOT mount, you would change auto to noauto.  auto is enabled by default though, but if that's what it takes...

---

### Post by chingdaotze on 2008-05-05
Thanks guys!  Everything is working now. :)

---

### Post by chingdaotze on 2008-05-05
Not sure how to mark as [SOLVED]... It's not showing up under 'Thread Tools'.

---

### Post by Rocket2DMn on 2008-05-05
You can change it manually by editing your original post, clicking Go Advanced, then changing the title from there.  The Mark as Solved function is currently disabled, they are still putting the pieces of the forums back together after some upgrades.

---

### Post by kuckunniwi on 2010-09-29
Just for the record...

I had a problem with one of my partitions not being mounted proberly on startup. As a complete newbie myself, I installed "Storage device manager", a nice GUI for us Ubuntu begginers, as I'm not too confident modifying fstab at the moment (although I WILL get round to it some day!) and reset the partition's value to default. Problem sovled!

For PsyDM:

```
sudo apt-get install psydm
```

or check out [HTML]http://pysdm.sourceforge.net/[/HTML]

Hope this is helpful to someone!

---

