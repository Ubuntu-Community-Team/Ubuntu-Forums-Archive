---
title: "Can not cut, delete, paste on a windows share."
date: 2012-11-11
forum: New to Ubuntu
---

### Post by Prostakat on 2012-11-11
Here is the line in which I specify how the windows share is to be mounted.

From /etc/fstab:

//192.168.0.1/HD_ST9500420AS /mnt/dir685 cifs guest,uid=1000,iocharset=utf8 0 0

When I use programs like cp, rm and thunar as root, everything works as it is supposed to, but when I am not root _I can only copy_ from the windows share. 

On my other OS (Windows XP) everything works fine with no additional configurations, but I assume that this information is irrelevant.

Assistance required.

---

### Post by cariboo on 2012-11-11
NTFS doesn't understand Linux permissions, so about all you can do is give the mount point a permission of 777 to be able to do what you want as a normal user.

```
sudo chmod -R 777 /mnt/dir685
```

---

### Post by Prostakat on 2012-11-12
NTFS? The file system on my windows share is ext3.

chmod 777 -R did not change the permissions to the following directories:

chmod: changing permissions of `/mnt/dir685/': Permission denied
chmod: changing permissions of `/mnt/dir685/lost+found': Permission denied

Thus meaning that I can now cut and delete the directories but I can not paste anything there.

---

### Post by Impavidus on 2012-11-12
> **Prostakat said:**
> NTFS? The file system on my windows share is ext3.
Are you sure? By default Win XP cannot read or write ext3, although I've read there're third-party extensions available to add that functionality.

---

### Post by El Tito on 2012-11-12
I agree with Impavidus; Windows will be NTFS more likely. Have you tried to change the owner of the partition:

#sudo chown your_user:your_group /the_path_to_the_mounted_point

---

### Post by Prostakat on 2012-11-12
Please read my first post again. I said that I can access and do all operations on my windows share from Windows XP. I never said that my windows share is in any way related to my Windows XP installation or any other Microsoft operating system.

Perhaps I am wrong to call it a windows share in the first place. At least that is how they call it here:

[http://askubuntu.com/questions/72471/correct-way-of-mounting-a-windows-share](http://askubuntu.com/questions/72471/correct-way-of-mounting-a-windows-share)

It is the Hard Drive in my router.

As for chown, it does not work.
chown: changing ownership of `/mnt/dir685/': Permission denied

---

### Post by El Tito on 2012-11-12
Ok, now I think I understand.
You used samba to share, and you are trying to access the hard drive of your router.
So you added to fstab the line in your first post. Try to add to the fourth column ***rw*** , to read and write in the partition, and tell us if it works.

---

### Post by varunendra on 2012-11-12
Hi Prostakat, and Welcome to the forums :)

You are using the correct term 'windows share' for what it is, perhaps it is the usage of a network address that confused us (you didn't mentioned in you original post that it was located in your router). So please confirm if I am understanding it correctly now -

- The router hdd is a remote location on network

- your xubuntu pc is the local machine where you are setting up the share, and is the same machine where you are having problem.

- the xp machine is the third machine in this setup where everything is fine.

Please correct me if I'm wrong, and here is a must-read for you : [How To FSTAB]("http://ubuntuforums.org/showthread.php?t=283131") by bodhi.zazen
Community wiki : [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Prostakat on 2012-11-13
Adding rw to the mount options in /etc/fstab works. I can now do everything (cut, paste, delete, rename). I read many posts and many suggestions in many other forums, so far only this works. Thank you El Tito. 

> **varunendra said:**
> 
- The router hdd is a remote location on network

Yes.

> **varunendra said:**
> 
- your xubuntu pc is the local machine where you are setting up the share, and is the same machine where you are having problem.

Yes.

> **varunendra said:**
> 
- the xp machine is the third machine in this setup where everything is fine.

Yes, that is why I assumed it is irrelevant information.

I am sorry if I mislead anyone. Everything works now, obviously i did not mount it correctly. 

It still puzzles me why I could do all these operations when I was root (sudo thunar, sudo cp, sudo rm) and could not while I was not root. Does not mount read /etc/fstab and mount the devices the same way for all users? So why without the rw mount option root still has read, write and execute privileges?

---

### Post by varunendra on 2012-11-13
> **Prostakat said:**
> It still puzzles me why I could do all these operations when I was root (sudo thunar, sudo cp, sudo rm) and could not while I was not root. Does not mount read /etc/fstab and mount the devices the same way for all users? So why without the rw mount option root still has read, write and execute privileges?I 'believe' it works like this -
root can do everything (everywhere) unless explicitly restricted.
All others can do nothing (except in their ~/home) unless explicitly permitted.

The mount point did not have 'rw' (read-write) permission earlier, so adding it gave explicit write permission to everyone.
But then it wasn't mounted with 'ro' (read-only) option either -
> **Prostakat said:**
> //192.168.0.1/HD_ST9500420AS /mnt/dir685 cifs guest,uid=1000,iocharset=utf8 0 0..so root wasn't explicitly restricted. Hence was able to write even then.

But this is just my guess based on the results, and can be a false assumption. Especially the uid=1000 suggests to me that my assumption is not entirely correct and there is more to it. With uid=1000, at least the first user (which was you in normal mode) should have same permission on it as in his ~/home, if I'm understanding it correctly. I hope someone else can give a clear and confident explanation.

---

### Post by Prostakat on 2012-11-14
What your are saying makes sense.

Thank you varunendra for enlightening me.

---

### Post by varunendra on 2012-11-14
Glad I could contribute ! :)

You can contribute back by marking the thread as [Solved] now to let others having similar problem know that this one has a possible solution.

---

