---
title: "Blackmagic Resolve"
date: 2017-03-20
forum: New to Ubuntu
---

### Post by 8ontact on 2017-03-20
Hi, im trying to install Davinci Resolve. I have:
installed a new copy of Ubuntu on my SSD, created a root su password and dragged the .sh file into terminal.
i get the following error

```
jawa@FWM01:~$ su
Password: 
root@FWM01:/home/jawa# '/home/jawa/Desktop/DaVinci_Resolve_12.5.5_Linux.sh' 
Verifying archive integrity... All good.
Uncompressing DaVinci Resolve Installation Package...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Extracting files...
tar: /usr/lib64: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
./install.sh: line 43: Exit_With_Error: command not found
resolve: no process found
Copying Resolve files...
Copying scripts...
Copying docs...
Copying Onboarding package...
Copying UI resources...
Copying libraries...
Creating shortcuts...
cp: cannot create regular file '/root/Desktop/': Not a directory
/bin/chown: cannot access '/root/Desktop/DaVinci Resolve.desktop': No such file or directory
/bin/chmod: cannot access '/root/Desktop/DaVinci Resolve.desktop': No such file or directory
Resolve System Updated
root@FWM01:/home/jawa#
```

Any help for a complete newbie would be great, thank you.

---

### Post by #&amp;thj^% on 2017-03-20
Well see if this helps: [https://www.thefanclub.co.za/how-to/how-install-blackmagic-design-davinci-resolve-125-ubuntu-1604-lts](https://www.thefanclub.co.za/how-to/how-install-blackmagic-design-davinci-resolve-125-ubuntu-1604-lts)

EDIT I also agree with QIII on the Root Password. (For what it's worth)

---

### Post by QIII on 2017-03-20
Hello!

You did not need to create a "root password".  In fact, Ubuntu comes without such as a security feature.  I would remove the password immediately to disable the root account.

If you installed the OS, then you are already a member of the sudoers group and can use sudo (or one of its forms for graphical applications) and your own password.  

Then you will be creating files on your own desktop and the path should be found.

---

### Post by 8ontact on 2017-03-20
Hi, first time i installed it i got this message:

jawa@FWM01:~/Desktop$ '/home/jawa/Desktop/DaVinci_Resolve_12.5.5_Linux.sh' 
Verifying archive integrity... All good.
Uncompressing DaVinci Resolve Installation Package...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
This script is supposed to be run as the root user.
Please login as the root user and run this script again.

---

### Post by QIII on 2017-03-20
Quite understood.

Prepend your commands with "sudo" and enter your password.  That will temporarily raise your privileges to near-root.

---

### Post by 8ontact on 2017-03-21
Hi, thank you for your help so far. I tried running as sudo and it seemed to work, i now have a desktop icon at least... however it does not launch. here are the errors on install.

jawa@FWM01:~$ sudo '/home/jawa/Desktop/DaVinci_Resolve_12.5.5_Linux.sh' 
[sudo] password for jawa: 
Verifying archive integrity... All good.
Uncompressing DaVinci Resolve Installation Package...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Extracting files...
tar: /usr/lib64: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
./install.sh: line 43: Exit_With_Error: command not found
resolve: no process found
Copying Resolve files...
Copying scripts...
Copying docs...
Copying Onboarding package...
Copying UI resources...
Copying libraries...
Creating shortcuts...
Resolve System Updated
jawa@FWM01:~$

---

### Post by Perfect Storm on 2017-03-21
> tar: /usr/lib64: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Make a /usr/lib64 directory and see if it helps

```
sudo mkdir /usr/lib64
```

---

### Post by 8ontact on 2017-03-21
Hi, that seemed to work but it tried to load the app and then it closes

............................................................................................................................................................................................................................................................
Extracting files...
resolve: no process found
Copying Resolve files...
Copying scripts...
Copying docs...
Copying Onboarding package...
Copying UI resources...
Copying libraries...
Creating shortcuts...
Resolve System Updated
jawa@FWM01:~$

---

### Post by 8ontact on 2017-03-21
Doh, sorry for wasting your time guys, it can only run on CentOS 7 and RHEL Linux.

---

### Post by richard159 on 2017-12-08
> **8ontact said:**
> Doh, sorry for wasting your time guys, it can only run on CentOS 7 and RHEL Linux.
This might help someone show how to tun on ubuntu you could try the same with whatever flavor of linux you have

[https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=58668](https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=58668)

---

