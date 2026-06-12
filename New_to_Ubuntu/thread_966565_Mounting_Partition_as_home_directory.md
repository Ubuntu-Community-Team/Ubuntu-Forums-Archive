---
title: "Mounting Partition as home directory"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by sanjit on 2008-11-01
I moved my home directory to its own partition before reinstalling Intrepid (got frustrated trying to get Compiz to play nice, tho it worked fine on Hardy). I've been trying to establish that /dev/sda3 is /home, but Ubuntu isn't playing dice. Luckily, I've had the presence of mind to move its original home folder so that I can move it back through a live CD when Ubuntu ultimately fails to recognize the new /home and says that I have no '/home'. AT this point, it may be the case that I have to just replace my old /home/[username] through copying and pasting, which is not something I want to do.

Summation:
*/dev/sda3 has my old home files.
*/dev/sda1 is where I installed Ubuntu
*Ubuntu must be made to recognize /dev/sda3 as '/home' at all times.

Also:
My old 'lost+found' is on my /dev/sda3. I don't know how it got there. Do I need it there?

Thanks.

---

### Post by taurus on 2008-11-01
If you want to mount /dev/sda3 as a separate /home, you need to edit /etc/fstab and add an entry in there.

```
/dev/sda3   /home   ext3   defaults   0   1
```

---

### Post by Diabolis on 2008-11-01
Also during the installation of a new system you are able to pick from where the Home folder should be mounted.

> The lost+found is the place where corrupted files are placed when they are found during a filesystem check. [https://answers.launchpad.net/ubuntu/+question/8373](https://answers.launchpad.net/ubuntu/+question/8373)

---

### Post by mapes12 on 2008-11-01
I had the same problem a while ago and found this Howto:

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

It worked for me.

Mark

---

### Post by sanjit on 2008-11-01
Thanks, all. I'll try the fstab edit before resorting to reinstall. I considered setting the /home mount point at installation, but I was worried it'd cause problems during the install process. I'll check out that link as well.

NOTE: I get one version of fstab through clicking in sudo nautilus and another using sudo gedit. What's that about, and which one do I edit?

---

### Post by taurus on 2008-11-01
```
gksudo gedit /etc/fstab
```

---

### Post by philinux on 2008-11-01
> **sanjit said:**
> Thanks, all. I'll try the fstab edit before resorting to reinstall. I considered setting the /home mount point at installation, but I was worried it'd cause problems during the install process. I'll check out that link as well.

NOTE: I get one version of fstab through clicking in sudo nautilus and another using sudo gedit. What's that about, and which one do I edit?

Setting sda3 as mount point /home is exactly what you needed to do and choose ext3 and of course not format. 

Use 
```
gksudo gedit /etc/fstab
```

---

### Post by sanjit on 2008-11-01
Hmm...It fails at 'Creating User' during install. Might that be because there is already a user folder on my /home partition with the same name?

Tried the install after getting some message about User's HOME/.drmc or something being ignored, as if it was having problems finding my /home directory as well as its own. I think I'll have to rough it after install, tho. I at least need to install. My PC doesn't always boot from the DVD drive, and I currently have no functional OS on the HDD.It gets annoying having to turn the computer on and off repeatedly just to get the Ubuntu CD to boot.

UPDATE: Adding '/dev/sda3   /home   ext3   defaults   0   1' to fstab using 'gksudo gedit /etc/fstab' results in a message about ignoring USER's HOME/.drmc or something when logging in. It says crap about the home directory having 644 permissions, and having to be accessible only to USER. Nothing really works at login, even under Gnome failsafe, because Gnome appears to rely on /home, and the other programs rely on it.(SOLUTION: Load up a live session from an Ubuntu CD, enter access /etc/fstab using 'sudo nautilus' or some similar method, remove the added line, and try logging in again.)

Is it possible that there are permission errors with the /home partition? That would be strange, because I can access that partition and its files from nautilus.

Could it be because the old home still exists at its original location, and having two '/home's confuses it? I didn't want to bother around with that. I assumed that adding that line to fstab would tell Ubuntu to ignore its original /home in favor of the /home partition. Later, I'll move home somewhere else, and see whether not having the original directory and the partition identified as /home works.

Observation: For an individual to go through this kind of trouble, the OS must kick some serious ***. The rewards outweigh the risks seriously. I'd never go through all of this for Windows.

---

### Post by philinux on 2008-11-03
To fix the dmrc error is real easy. I caused this more than once by playing with permissions in my home folder.

In this order. And no sudo.
```
chmod 700 /home/yourusername
chmod 644 /home/yourusername/.dmrc
```

There are no messages given back when you enter the code.

---

