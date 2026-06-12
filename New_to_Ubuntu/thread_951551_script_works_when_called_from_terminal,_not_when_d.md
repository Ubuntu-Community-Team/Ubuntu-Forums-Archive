---
title: "script works when called from terminal, not when double clicked"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by henryrhenryr on 2008-10-18
I have a simple script for mounting a remote folder by SSHFS.  This is the script
```

#!/bin/sh
sshfs henry@192.168.2.109:/home/share /mnt/share -o uid=1000,umask=0
```

It is executable and when I double click on the script to execute it, the terminal opens and requests the password.  I enter the correct password, the terminal closes but the directory is not mounted!

When I open a terminal and then run
```

/home/henry/mount.sh
```

The script works as expected.

Surely it's possible!?

Any ideas?

Thanks

---

### Post by tdrusk on 2008-10-18
I remember trying to make one of these. It would mount as long as the program was running. Try something like
```
sleep 30
``` at the end of it. This will make it wait 30 seconds before closing. If that keeps the folder mounted than that is your problem.

Sorry if I am not helpful but...
I use Ubuntu's "connect to server" under places. I connected with the ssh server. Then I made it mount to a folder called "Server" under places so it's always right there(It's an option in the connect to server dialog). Best of all I can drag my music folder into Rhythmbox and listen to my music.

Other brainstormed ideas...
I know you said it's executable, but did you try right clicking it and making it executable?
Are you sure it doesn't need a sudo since you are mounting to /mnt?

---

### Post by henryrhenryr on 2008-10-18
Hi

Thanks.  That has at least identified the problem!  During the 'sleep 30' bit, the directory is mounted.  After the 30 seconds are up, the directory is unmounted.

I think "connect to server" must be a gnome tool.   I am stuck with XFCE because of RAM limitations.  

How do I stop it umounting once the password check is done?

---

### Post by Kareeser on 2008-10-18
Random thought. Perhaps it needs to run in the background?

---

### Post by tdrusk on 2008-10-18
Okay awesome. Try executing Thunar afterwords.

```
#!/bin/sh
sshfs henry@192.168.2.109:/home/share /mnt/share -o uid=1000,umask=0
thunar 

```

---

