---
title: "Permanently Mounting Drives"
date: 2015-11-10
forum: New to Ubuntu
---

### Post by Iflana on 2015-11-10
I am attempting to follow the tutorial [here]("http://sourcedigit.com/8194-customize-ubuntu-14-04-mount-hard-disk-partitionsdrives-automatically-system-startup/") on permanently mounting some drives in Ubuntu 14.04.  All appears to go well until I go to save the fstab file.  It tells me **Could not find the file "/ect/fstab".  Please check that you typed in the location correctly and try again.**  When I look I seem to have an **fstab.d** directory instead.  Is there a difference?

---

### Post by coffeecat on 2015-11-10
The file is /etc/fstab, not /ect/fstab. Look at the spelling of the higher level directory.

A word of caution. Perhaps I have misread you, but from your wording it sounds as though you have created a new fstab file. If you save it correctly at /etc/fstab, you will overwrite your original /etc/fstab and be in all sorts of trouble, including being unable to boot up (probably). If this is what you are doing, have another look at the tutorial. You need to open the pre-exisiting /etc/fstab with "gksudo gedit /etc/fstab" and append your new lines at the end, and then save.

I'm not overimpressed with that tutorial. Mounting a ntfs partition with just the defaults option works, but there are better ways of doing it, and it's far better to use UUIDs to define your devices instead of /dev/sda1 and the like. What types of partitions (**not** drives) are you wanting to mount?

---

### Post by Iflana on 2015-11-10
The period was part of the punctuation, not the file path or name.  Just to clarify, here's what I typed into the terminal to bring up the file to edit.

```
jen@jen-System-Product-Name:~$ gksudo gedit /ect/fstab
```

As far as I can determine I should be editing the fstab file, not creating a brand new one.  When I did the command above there was no text of any kind loaded.  It appeared to be an empty file.  Of course if my information is contained in **fstab.d** instead of **fstab** then that changes things I suppose.  Can you answer my initial question about whether or not these two are the same?

Part of what I liked about this tutorial was the simplicity.  I'm new, so I really need that.  If you feel that UUID is better, can you please explain why?  Also, how you'd suggest going about it instead.  I am open to ideas, but I need something simple and basic.  Starting with defaults seems like a decent way to go, and then change things from there if needed.  I am wanting to permanently mount the bold ones below, as they contain all my files.

```
   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *        2048   314574847   157286400    7  HPFS/NTFS/exFAT**
/dev/sdb2       314576894   524290047   104856577    5  Extended
[B]/dev/sdb3       524290048  1048578047   262144000    7  HPFS/NTFS/exFAT
/dev/sdb4      1048578048  1953519615   452470784    7  HPFS/NTFS/exFAT[/B]
/dev/sdb5       314576896   346574847    15998976   82  Linux swap / Solaris
/dev/sdb6       346576896   524290047    88856576   83  Linux
```

---

### Post by Morbius1 on 2015-11-10
> jen@jen-System-Product-Name:~$ gksudo gedit /[COLOR=#0000cd]**ect**[/COLOR]/fstab
There is no "ect" directory in Linux. There is however an /etc directory and as it happens fstab is in it. So what you should have done is:
> jen@jen-System-Product-Name:~$ gksudo gedit /[COLOR=#0000cd]**etc**[/COLOR]/fstab

---

### Post by coffeecat on 2015-11-10
> **Iflana said:**
> The period was part of the punctuation, not the file path or name. 

Morbius1 has explained but please look at my first sentence again. I was not directing you to any punctuation but the spelling of the /etc directory.

---

### Post by Geoffrey_Arndt on 2015-11-11
Always a good idea to peruse the file and directory you want or need to edit via the standard files manager.    By navigating to the file, you get to learn the Linux file tree, and the "correct" spelling of subdirectories.

(one way to remmember /etc . . . . . it's often pronounced as "et see")

Finally, "cut & paste" is your friend.

---

### Post by leunam12 on 2015-11-11
It is better to use UUID because if the /dev/sdx designation changes for whatever reason you will not have problems to boot. type sudo blkid on the terminal to see the UUID's. Also check the link below for a better tutorial:

[https://help.ubuntu.com/community/MountingWindowsPartitions#NTFS](https://help.ubuntu.com/community/MountingWindowsPartitions#NTFS)

---

