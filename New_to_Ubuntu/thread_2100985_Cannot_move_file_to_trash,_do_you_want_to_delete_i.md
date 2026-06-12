---
title: "Cannot move file to trash, do you want to delete immediately?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by foxdib on 2013-01-03
hey I have Ubuntu 12.10 on dual boot with windows 7.
When I access the local disk D of windows from Ubuntu. I'm able to write and copy files. But when I try deleting something I get this "Cannot move file to trash, do you want to delete immediately?"
Is there a way so when I delete a file from the local disk disk D in Ubuntu it goes to the trash? 
I've read that I can create a trash folder for this but didn't really get how to do it.
PS: Sorry for my bad English.

---

### Post by cariboo on 2013-01-03
Moved to the Absolute Beginner Section, as it has nothing to do Forum Feedback & help.

---

### Post by NikTh on 2013-01-03
Hi , 

[quote="bcbc"]The files in /host are outside of the virtual disk Wubi installs Ubuntu  on. So it doesn't make sense for these to be 'deleted' and moved into  the virtual disk's trash. If you want to delete them and keep them in  the recycle bin, do it from Windows or move them onto the virtual disk  first.

Personally I'd recommend keeping your data on the /host and not on the  virtual disk as the host ntfs file system is more reliable than the  virtual disk.[/quote]

source : [http://ubuntuforums.org/showthread.php?t=1810591](http://ubuntuforums.org/showthread.php?t=1810591)

Thanks

---

### Post by foxdib on 2013-01-03
Nikth I understand. But I'm asking because I'm using the same folders for musics videos and photos on both Ubuntu and Windows. So I'd like to add a Trash folder. I think I should be able to do it. I saw it here " [http://ubuntuforums.org/showthread.php?t=1499345&highlight=windows+partition+trash](http://ubuntuforums.org/showthread.php?t=1499345&highlight=windows+partition+trash) " but didn't really know how to do it. I'm still a beginner and not too familiar with Ubuntu.

---

### Post by NikTh on 2013-01-03
> **foxdib said:**
>  I think I should be able to do it. I saw it here " [http://ubuntuforums.org/showthread.php?t=1499345&highlight=windows+partition+trash](http://ubuntuforums.org/showthread.php?t=1499345&highlight=windows+partition+trash) " but didn't really know how to do it. I'm still a beginner and not too familiar with Ubuntu.

Well , I'm not a wubi expert , but I think you misunderstood. The thread you've looked is not the same. There the situation is different. 

I don't know if you can mount permanently the /host in fstab as is a folder and not a partition. 

Also the problem in the thread you've looked is quite different because it has to do with permissions (read-write) but you have full permissions in /host folder and no permissions problem apply here. 

Hopefully someone with more knowledge on wubi installations will clarify things. 

Thanks

---

