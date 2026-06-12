---
title: "Application Autostart to Mount Remote Share"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by AlistairH on 2013-04-04
I can run the following command in a terminal to mount a remote ssh share with no problems

```
sshfs alistair@myserver:/media/external/ ~/pictures
```

But when I use that as the command in an entry in the Application Autostart window with the aim of having the remote share mounted automatically upon login,  it doesn't work.

What am I missing?

---

### Post by r.stiltskin on 2013-04-04
I'm not sure why that doesn't work; maybe because it depends on you already being logged in and the system is trying to run it before it's finished logging you in.  Have you tried ```
sshfs alistair@myserver:/media/external/ /home/alistair/pictures
```

Better yet, why not try adding it to your fstab as explained in this [tutorial]("http://ubuntuforums.org/showthread.php?t=430312").

---

### Post by AlistairH on 2013-04-04
> **r.stiltskin said:**
> Better yet, why not try adding it to your fstab as explained in this [tutorial]("http://ubuntuforums.org/showthread.php?t=430312").

I have a problem using fstab as the machines in question get used by multiple users, each with their own login credentials. As I understand it, putting the sshfs statement in fstab means that the mount will only be accessible by the user specified in the statement, i.e. me in this case. (Is that true as well when connecting to a samba share through a mount configured in fstab when a username and password has to be defined).

It was for this reason that I thought that running the corresponding command for each user when they log on to the PC would be the way to go.

I tried to set up an fstab entry earlier following that tutorial, but it didn't work. I was in a rush so probably missed a step and I haven't had time to backtrack to troubleshoot.

What determines the access permissions if the mount was specified in fstab? Is there a generic statement that can be placed there by an administrator so that the mount point is created on boot and is available to any user who happens to log on to the machine. Their access to files on the remote share would be determined by the file permissions on the remote share.

---

### Post by AlistairH on 2013-04-25
After much consideration and investigation into the various options I've decided that the best solution here, where any number of users may use the same machine with their own accounts, is to use Gigolo and configure it to start up automatically allowing each user to create their own connections and bookmarks accordingly.

---

