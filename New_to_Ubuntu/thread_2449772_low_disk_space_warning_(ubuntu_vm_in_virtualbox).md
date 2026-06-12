---
title: "low disk space warning (ubuntu vm in virtualbox)"
date: 2020-09-02
forum: New to Ubuntu
---

### Post by bartalor on 2020-09-02
I got this warning of low disk space for ubuntu vm because I allocated to it 10 gb and 9.4 were full already, legit (although I also chose to dynamically allocate memory but it seems that it doesn't work, but that's another topic).
so I changed the settings on virtualbox and allocated 15 gb instead, but I still get the warnings despite that still only 9.4 gb are full (I checked to verify it) and now I have 15 gb allocated overall.
I hope it's just some bug and it just not aware that I allocated more memory, but if I use this added memory it will work fine.

anyone know's what that all means and what should I do?

thanks :)

---

### Post by guiverc on 2020-09-02
In my experience when you increase the space on the HOST/virtualbox, you need to still boot a *live* system (in the VM) and expand your Ubuntu *filesystem* so it'll use the additional space (space will be there but be unallocated as your Ubuntu  formatted the disk space available when it was installed; ie. the original size).

ie. treat the system as if it was on hardware (cloning a *fs* (filesystem) perfectly from a 10gb disk to a 15gb disk will still have 10gb allocated to it, but have 5gb space free* unless your cloning software alters the fs which vbox won't do*)

10gb isn't much space, esp. if it's a desktop (25gb is the recommended space for a desktop; [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)) though many blogs will suggest smaller as the space needed entirely depends on what you do with it, what software you'll add etc.

---

### Post by ajgreeny on 2020-09-02
Run command **df -h** in terminal as although you have enlarged the virtual disk  I suspect the filesystem is still only 10G.

You will probably need to add a virtual CD disk to your VM, with a live session of Ubuntu and enlarge the filesystem using gparted.
There are more details of how to do this on the VBox website which I will have to let you search formas I'm  using an Android tablet at present and find it impossible to copy/paste quickly. However, it's  easy to do; I had to do it myself in similar circumstances several years ago.

---

### Post by bartalor on 2020-09-02
> **guiverc said:**
> In my experience when you increase the space on the HOST/virtualbox, you need to still boot a *live* system (in the VM) and expand your Ubuntu *filesystem* so it'll use the additional space (space will be there but be unallocated as your Ubuntu  formatted the disk space available when it was installed; ie. the original size).

ie. treat the system as if it was on hardware (cloning a *fs* (filesystem) perfectly from a 10gb disk to a 15gb disk will still have 10gb allocated to it, but have 5gb space free* unless your cloning software alters the fs which vbox won't do*)

10gb isn't much space, esp. if it's a desktop (25gb is the recommended space for a desktop; [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)) though many blogs will suggest smaller as the space needed entirely depends on what you do with it, what software you'll add etc.

thanks, I see it now, went to the disks and saw that there is 10 gb free (I decided to allocate 20 gb in second thought),
but the problem is that there are 4 partitions there, not including the free space, and I don't know what I should resize,
the partitions are: Filesystem partition 1, Filesystem partition 2, Extended Partition Partition 3, Filesystem Partition 5.
I really have no idea what that all means.

---

### Post by ajgreeny on 2020-09-02
I think you may be looking at the partitions in yur host system which is not what we were meaning; you need to increase the size of your VM's filesystem, which unless you installed the VM in an unusual manner will be a single partition.

---

### Post by mastablasta on 2020-09-02
please boot up the virtual machine and within it run: 

```
df -h 

```
and post output here.

then go to host OS and do the same there (assuming your host is linux). if host is windows i think you can use:
```

dir *.*
```

i am not sure with users and all, if this still works well. if it doesn't, there are a couple GUI applications that will show this data.

edit: eh file manager shows it or you can right click on disk in file manager and then properties.

---

### Post by bartalor on 2020-09-02
Really got annoyed with it, just deleted my vm, didn't have anything too important there anyway, hope to create a new one and things will be better.

---

### Post by ActionParsnip on 2020-09-02
Please mark as solved. Be sure to keep old kernels down if you have a small VM

---

