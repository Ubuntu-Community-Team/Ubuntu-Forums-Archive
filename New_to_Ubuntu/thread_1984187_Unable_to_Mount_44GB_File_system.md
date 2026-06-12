---
title: "Unable to Mount 44GB File system"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by mlplatt on 2012-05-21
Each time I start Ubuntu I am faced with a window that informs me -


*"Unable to Mount 44GB File system*
  
 *DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found"*


I don't know what it means being an unhappy state of complete ignorance about computers generally.n The message has always been there since I first installed Ubuntu so I don't know if it is serious or not, or indeed what I am deprived of. I only installed Ubuntu a couple of weeks back and have had a couple of more pressing problems to solve . 



i would be most grateful for any advice.

---

### Post by raja.genupula on 2012-05-21
post the output of ```
cat /etc/fstab
``````
blkid
```

---

### Post by jtarin on 2012-05-21
Do you have a 44GB File system?

---

### Post by jtarin on 2012-05-21
> **raja.genupula said:**
> post the output of ```
cat /etc/fstab
``````
blkid
```Just about to correct your "/stab".:p

---

### Post by mlplatt on 2012-05-21
Thanks. I should have mentioned it before. The 44GB File system relates to my Ubuntu files. 



[I]The mlplatt@mlplatt-Inspiron-530s:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=56da761e-53ce-4e0b-bd77-e64d87468170 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=59485a5d-4618-434c-8944-e53695001613 none            swap    sw              0       0
mlplatt@mlplatt-Inspiron-530s:~$ blkid
mlplatt@mlplatt-Inspiron-530s:~$ ^C
mlplatt@mlplatt-Inspiron-530s:~$ 

[/I]

---

### Post by raja.genupula on 2012-05-21
> **mlplatt said:**
> Thanks. I should have mentioned it before. The 44GB File system relates to my Ubuntu files. 



[I]The mlplatt@mlplatt-Inspiron-530s:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=56da761e-53ce-4e0b-bd77-e64d87468170 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=59485a5d-4618-434c-8944-e53695001613 none            swap    sw              0       0
mlplatt@mlplatt-Inspiron-530s:~$ blkid
mlplatt@mlplatt-Inspiron-530s:~$ ^C
mlplatt@mlplatt-Inspiron-530s:~$ 

[/I]
blkid have to give like this 
```
raja@badfox:~$ blkid
/dev/sda1: UUID="77f2fbc4-93fb-4b58-9dac-6ef7ce57b921" TYPE="ext4" 
/dev/sda2: UUID="DCEAB5EDEAB5C454" TYPE="ntfs" 
/dev/sda3: UUID="fdb67f35-c296-4cca-b95c-8f0fc331cc90" TYPE="swap" 
/dev/sda5: LABEL="New" UUID="3B39256A713495C1" TYPE="ntfs" 
/dev/sda6: UUID="630715dc-6e18-4295-9a38-cc1ba4e50ac0" TYPE="ext4" 
raja@badfox:~$ 

```

---

### Post by raja.genupula on 2012-05-21
> **jtarin said:**
> Just about to correct your "/stab".:p
thanks man :)

---

### Post by Cheesemill on 2012-05-21
The command above is incorrect. Can we have the output of:
```
sudo blkid
```

---

### Post by mlplatt on 2012-05-21
Hi Cheesemill

mlplatt@mlplatt-Inspiron-530s:~$ sudo blkid
[sudo] password for mlplatt: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0308" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="32FE2052FE2010A1" TYPE="ntfs" 
/dev/sda3: UUID="5A8EB5ED8EB5C235" TYPE="ntfs" 
/dev/sda5: UUID="56da761e-53ce-4e0b-bd77-e64d87468170" TYPE="ext4" 
/dev/sda6: UUID="59485a5d-4618-434c-8944-e53695001613" TYPE="swap" 
/dev/sdb1: LABEL="My Book" UUID="7B05-602B" TYPE="vfat" 
/dev/sdb5: UUID="d804b7c1-96ea-47ca-b16a-1e5fbc834fa7" TYPE="ext4" 
/dev/sdb6: UUID="be457892-1357-4ed5-99b7-10a7ff940f0d" TYPE="swap" 
mlplatt@mlplatt-Inspiron-530s:~$

---

### Post by sandyd on 2012-05-21
> **mlplatt said:**
> Hi Cheesemill

mlplatt@mlplatt-Inspiron-530s:~$ sudo blkid
[sudo] password for mlplatt: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0308" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="32FE2052FE2010A1" TYPE="ntfs" 
/dev/sda3: UUID="5A8EB5ED8EB5C235" TYPE="ntfs" 
[B]/dev/sda5: UUID="56da761e-53ce-4e0b-bd77-e64d87468170" TYPE="ext4" 
/dev/sda6: UUID="59485a5d-4618-434c-8944-e53695001613" TYPE="swap" [/B]
/dev/sdb1: LABEL="My Book" UUID="7B05-602B" TYPE="vfat" 
[COLOR=Red]/dev/sdb5: UUID="d804b7c1-96ea-47ca-b16a-1e5fbc834fa7" TYPE="ext4" 
/dev/sdb6: UUID="be457892-1357-4ed5-99b7-10a7ff940f0d" TYPE="swap" [/COLOR]
mlplatt@mlplatt-Inspiron-530s:~$
You have two ubuntu installations. One is on your WD MyBook, and the other is on your hard drive.

I've bolded the one you are currently using. and turned the one that you aren't using red.
From the info above, I would guess that you accidentally installed Ubuntu on your WD MyBook. Or is that intentional?

---

### Post by mlplatt on 2012-05-21
Hi Sandyd,

Practically everything I do on computers is accidental! This certainly wasn't intentional.

How do I get rid off it? Or should I just ignore it? 

MyBook is a backup hard drive. God knows how it got there but it doesn't surprise me. 

I shall be off line till tomorrow now.

Thanks

---

### Post by mlplatt on 2012-05-25
Thanks all,

I managed to uninstall the spare Ubuntu and the errant window has disappeared.

Thanks for all your help

---

