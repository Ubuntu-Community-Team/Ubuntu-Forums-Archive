---
title: "Few questions concerning fresh install with lxde and drive permissions."
date: 2014-07-26
forum: New to Ubuntu
---

### Post by myhatisgreen on 2014-07-26
Im new to these forums but have been getting into Linux  lately after years of windows which I only use for gaming now and I see  Linux as a superior alternative for everyday use.  
  Im running the LXDE desktop since I really don't like the other alternatives.
I've managed to allow other login through GUI at bootup so I can login as root.
  I'm dual booting Win 8.1 with Ubuntu, and I would like to totally  lock down the Windows partition for security reasons. From what I gather  no matter what flavor of Linux you need to be root to change drive  permissions.
I would not only like to lock the Windows drive due to the fact that I  know there are viruses that even if your running Linux will look for a  Windows partition to infect.
So I want to lock the windows drive and set all permissions to list files only for root and nothing for other users.
I tried doing this through GUI and root. Thing is when I right click on  the drive I see no option for permissions and if I go into the drive  itself and right click folder properties upon changing permissions there  is no effect.
  Can someone please help me with this so I can have peace of mind when  I'm using Linux and I will know for sure my windows drive is safe?

I was told as ask ubuntu to perform these steps:



      

>              Set the uid,gid and umask mount options:

  mount -o rw,exec,uid=0,gid=0,umask=077 -t ntfs-3g /dev/something /mount/point 
  Or, equivalently, make an fstab entry with these options:
  cat <<EOF | sudo tee -a /etc/fstab 
/dev/something /mount/point ntfs-3g rw,exec,uid=0,gid=0,umask=077 0 0
EOF
  Remember to replace /dev/something and /mount/point with appropriate values.





      


Thing is I dont know what a mount point is, the user that responded said they are folders, but im talking about partitions here, mainly sda1 and sda2.

Can someone clarify this for me in n00bs terms please?

---

### Post by Rob Sayer on 2014-07-26
> **myhatisgreen said:**
> ... I would [...] like to lock the Windows drive due to the fact that I  know there are viruses that even if your running Linux will look for a  Windows partition to infect ...

I doubt this.  Please provide specific examples.

---

### Post by mikewhatever on 2014-07-26
Honestly, I think you are being a bit paranoid, there is no need to mess with it for the reasons you state. It's also completely unnessesary to login as root - that's one of the reasons Windows is insecure. Be advised, linux is no more secure then Windows if you login as root!
That said, ...a mount point is indeed a folder. Many good expanations have been written, so I won't pollute the web with another, have a read:
[http://www.linuxnix.com/2013/09/what-is-a-mount-point-in-linuxunix.html](http://www.linuxnix.com/2013/09/what-is-a-mount-point-in-linuxunix.html)
[http://www.comptechdoc.org/os/linux/manual1/mountpoints.html](http://www.comptechdoc.org/os/linux/manual1/mountpoints.html)

Now, regarding the permissions, you need to check them on the mount point, and not the partition, in other words <ls -l /media/mountpoint>.

---

### Post by Toz on 2014-07-26
Hello @myhatisgreen and welcome to the forums.

> **myhatisgreen said:**
> I've managed to allow other login through GUI at bootup so I can login as root......From what I gather  no matter what flavor of Linux you need to be root to change drive  permissions.
Logging in as root is not a good idea and also not necessary. You will still have root access to the system using the sudo/gksudo commands when logging in using your user account. Please have a read of the [RootSudo wiki entry]("https://help.ubuntu.com/community/RootSudo") for more information.

---

### Post by yancek on 2014-07-26
> Thing is I dont know what a mount point is, the user that responded said  they are folders, but im talking about partitions here, mainly sda1 and  sda2.

A mount point is a directory.  It gives you a place to access a partition.  You can probably do that under the /media directory where partitions are usually listed by UUID.

In your situation, you can create mount points for sda1 with:  sudo mkdir /mnt/sda1
You would then need to manually mount or mount on boot with an entry similar to the one in your example in the /etc.fstab file.  You need sudo for root/admin privileges working outside your /home directory.  The standard is to put mount points in the /mnt directory but is not necessary.  Creating a mount point 'sda1' for the sda1 partition is for simplicities sake, you can call it anything you want but need to use it in your fstab entry also.  Repeat the process for sda2.  There are quite a lot of tutorials on using the mount command and sites with examples for that as well as fstab entries.  You should also do an online search for 'Linux umask options'.  I don't use windows very often but someone will probably be able to give you more specific advice.  In the sample entry above, you should probably change the 'rw' to 'ro', read/write, read-only.

---

### Post by coffeecat on 2014-07-26
> **myhatisgreen said:**
> I've managed to allow other login through GUI at bootup so I can login as root.

I suggest for your own peace of mind and the security of your Ubuntu installation, that you reverse whatever it is you did to enable login to a GUI as root. Tutorials which explain how to do this are the height of irresponsibility, which is why forum policy does not allow them to be posted here. 

Anyway, you are going about "locking" the Windows C: partition in the wrong way. Windows permissions and Linux permissions work somewhat differently. If you want to prevent your Windows C: partition from being accessed, you do so by means of a custom line in /etc/fstab with special mount options as described here:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Scroll down to "**Option 2 - to ensure that Ubuntu does not mount the partition and also disables graphical mounting from the file manager.**" You'll need to read the whole page if you are not familiar with editing /etc/fstab.

Others have stated why your reasons for wanting to "lock" the Windows partition are not necessarily good ones, but preventing writes to the Windows C: partition is good practice, if only to prevent accidental damage to the Windows filesystem from Ubuntu.

---

### Post by myhatisgreen on 2014-07-26
> **Rob Sayer said:**
> I doubt this.  Please provide specific examples.

Sorry I can not provide any examples, I just found this out after extensive research.

> **mikewhatever said:**
> Honestly, I think you are being a bit paranoid, there is no need to mess with it for the reasons you state. It's also completely unnessesary to login as root - that's one of the reasons Windows is insecure. Be advised, linux is no more secure then Windows if you login as root!
That said, ...a mount point is indeed a folder. Many good expanations have been written, so I won't pollute the web with another, have a read:
[http://www.linuxnix.com/2013/09/what-is-a-mount-point-in-linuxunix.html](http://www.linuxnix.com/2013/09/what-is-a-mount-point-in-linuxunix.html)
[http://www.comptechdoc.org/os/linux/manual1/mountpoints.html](http://www.comptechdoc.org/os/linux/manual1/mountpoints.html)

Now, regarding the permissions, you need to check them on the mount point, and not the partition, in other words <ls -l /media/mountpoint>.

No, Im not being paranoid, I just had to go through a complete rehaul of all systems on my network due to being infected with a hardware based BIOS rootkit. In any case I think your misunderstanding me, I only created the root login to make the changes I see necesary, I do not use it reguraly. I use my regular user account to login to Ubuntu.

> **Toz said:**
> Hello @myhatisgreen and welcome to the forums.


Logging in as root is not a good idea and also not necessary. You will still have root access to the system using the sudo/gksudo commands when logging in using your user account. Please have a read of the [RootSudo wiki entry]("https://help.ubuntu.com/community/RootSudo") for more information.

I am familiar with sudo and gksudo but they dont always perform the things you want to do which is why I like to have option for logging in as root, like I told the poster above dont worry I dont login as root reguraly and most of the time when I do I disconnect internet.

> **coffeecat said:**
> I suggest for your own peace of mind and the security of your Ubuntu installation, that you reverse whatever it is you did to enable login to a GUI as root. Tutorials which explain how to do this are the height of irresponsibility, which is why forum policy does not allow them to be posted here. 

Anyway, you are going about "locking" the Windows C: partition in the wrong way. Windows permissions and Linux permissions work somewhat differently. If you want to prevent your Windows C: partition from being accessed, you do so by means of a custom line in /etc/fstab with special mount options as described here:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Scroll down to "**Option 2 - to ensure that Ubuntu does not mount the partition and also disables graphical mounting from the file manager.**" You'll need to read the whole page if you are not familiar with editing /etc/fstab.

Others have stated why your reasons for wanting to "lock" the Windows partition are not necessarily good ones, but preventing writes to the Windows C: partition is good practice, if only to prevent accidental damage to the Windows filesystem from Ubuntu.

I dont see how logging in as root is irresponsible as long as you are offline. My goal is not about mounting the windows partition, I think you misunderstood what I said, Ubuntu sees the windows partition and I dont want that. I want it locked down, ubuntu doesnt care what it is, all it sees is an NTFS drive. What Im trying to do is for ubuntu to 1) not mount it at login and 2) change permissions from ubuntu enviroment to NOT allow any writing to this drive.

Also in any case once Im done with locking down the windows drive, I plan on totally disabling the root account. So no problems there.


EDIT: Ok I managed to get the windows drive not to automount at startup. I dont think it will be necesary to change drive permissions for the windows drive since in order to mount them you need password and to mount the system reserved partition only root can do that.

Now all i have to do is disable root account and its login.

---

### Post by myhatisgreen on 2014-07-27
Alright I disabled the root account, now I dont remember how I got alternate login option to appear at splash at boot. Any tips on how to remove this now?

---

