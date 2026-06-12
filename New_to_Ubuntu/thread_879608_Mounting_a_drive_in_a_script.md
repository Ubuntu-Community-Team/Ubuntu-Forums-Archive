---
title: "Mounting a drive in a script"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by CrookedKarma on 2008-08-04
Hey everyone.
Sorry, if this has been asked before, but I've been searching about for answers for about a week, and haven't found anything (which also suggests it might not be absolute beginners, but there were slightly similar things in here)
Anyway, I'm currently trying to write a script (in python, though a lot of it is calling shell commands) to start up a program on a remote computer. It has to mount a network drive, and as it's not run as root, it's not got permission, but it needs to run completely automatically (i.e. not prompt for a password) so I can't use sudo/su.
Also, it would be preferable to not use the fstab for this, so the script can remove/mount the drive every time it is run.
Any help on how to do this would be greatly appreciated.
Thanks in advance,
Dave

---

### Post by ibuclaw on 2008-08-04
I can think of two ways you can do this.

[LIST]
[*]1) It's called sudo, you put it before the appname and the script is ran with root privileges, with only one password of authentication from the user. Afterall, one password before the app is executed is better than half a dozen password queries while the app is running.
```
sudo ./appname.py
```
[*]2) Depending on how automatic you want the script to be, you could add a line in one of the startup/login scripts so the app is run by root everytime you/the user boots up/logs in. No sudo privileges required (except to edit the file to add the line).
[/LIST]
Regards
Iain

---

### Post by AdamWood on 2008-08-04
As far as I know it's not possible to _both_ ensure a drive is **not** listed in /etc/fstab and mount it without root permissions.

If you're worried about the /etc/fstab file mounting a drive when the computer starts you can use the **noauto** option on the fstab line.

Another option might the SUID permission flag. Have a look at [this link]("http://www.codecoffee.com/tipsforlinux/articles/028.html"). It does present a security risk however and should be used with care!

---

### Post by ibuclaw on 2008-08-04
Ah, yes. fstab might work too.

have the options **defaults,user,noauto** in the line.

defaults sets all the default mount settings.
user allows normal/unprivileged users to mount the drive.
noauto means that the drive won't be mounted automatically.

Regards
Iain

---

### Post by CrookedKarma on 2008-08-04
Yeah, I did just mean not mounted automatically, rather than not in the fstab.
I tried putting those options in the fstab but I still get the message "mount: only root can do that" (which suggests to me that user does absolutely nothing :confused:)

Setting the user ID looks like the kind of thing I want, but I can't figure out how to do it.

---

### Post by hyper_ch on 2008-08-04
isn't there a "mount" group to which you can add your user?

---

### Post by AdamWood on 2008-08-04
> I tried putting those options in the fstab but I still get the message "mount: only root can do that" (which suggests to me that user does absolutely nothing )
Are you trying to mount a Windows share using SAMBA by any chance?

> 
Setting the user ID looks like the kind of thing I want, but I can't figure out how to do it.
```

sudo chown root:root FILENAME
sudo chmod u+s FILENAME
sudo chmod g+s FILENAME
sudo chmod a+x FILENAME

```
Will make the file owned by root, and run as root when executed, and finally can be executed by anyone. That final step is where the security risk lies. It is possible, and advisible, to use a different group for the owner of the file and to set the executable bit on the group only, but that's another question. ;)

---

### Post by CrookedKarma on 2008-08-04
> **AdamWood said:**
> Are you trying to mount a Windows share using SAMBA by any chance?

I am, does that only allow root to do it then?

I followed all of those steps, but it still gives me the same messages :(

---

### Post by AdamWood on 2008-08-04
I think you need to set the SUID bit for the /usr/bin/smbmount file. When calling the mount command it calls the /usr/bin/smbmount command internally and it is that step which requires root privileges. I might be wrong here but I recall having the same problem a while ago and chmod u+s /usr/bin/smbmount fixed it for me. I had assumed that setting SUID on /bin/mount would be enough but it wasn't. You might also need to need to set SUID on /usr/bin/smbclient but we're getting well out of "Absolute Beginner" territory now so I suggest you try and read up on the SAMBA executables before going down this route as I wouldn't recommend it unless there is no other option.

---

### Post by CrookedKarma on 2008-08-04
k, I'll have a look into that, though might have to rethink how the script works.
Thanks very much for the help guys.

---

### Post by limasierra on 2008-08-04
If you want to mount and unmount disks without the need of being root you can run "sudo polkit-gnome-authorization" on terminal without the quotes and grant an authorization to your user in "Mount file systems from internal drives."
Then you can run your script without having to use "sudo" command.

---

### Post by bodhi.zazen on 2008-08-04
You can mount and unmount partitions not listed in fstab with pmount.

pmount is designed for removable devices but can be adapted for partitions on internal hard drives as well.

[http://ubuntuforums.org/showpost.php?p=1487054&postcount=3](http://ubuntuforums.org/showpost.php?p=1487054&postcount=3)

You can of course edit with nano or gedit if you like ...

```
gksu gedit /etc/pmount.allow
```

---

