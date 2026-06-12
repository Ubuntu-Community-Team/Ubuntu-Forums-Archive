---
title: "Root access"
date: 2015-05-17
forum: New to Ubuntu
---

### Post by RobGoss on 2015-05-17
Hello everyone I was wondering if you could help me with this question. I was trying to access a root folder on my machine it's called - root ans as a X aside of it but when I try to access it I'm greeted with this message.

You do not have the permissions necessary to view the contents of “root”.

Can you tell me why I'm getting this message. Thanks so much

---

### Post by dino99 on 2015-05-17
Yes, this is normal to Ubuntu and every Linux distributions. You can't access to the root folder because that folder is owned by root and it's user folder.

[http://askubuntu.com/questions/187997/i-cant-access-the-root-folder](http://askubuntu.com/questions/187997/i-cant-access-the-root-folder)

---

### Post by RobGoss on 2015-05-17
So what you're saying there's no way to access to this folder?

---

### Post by lisati on 2015-05-17
> **robert159 said:**
> So what you're saying there's no way to access to this folder?

Not exactly. 

In Ubuntu, and other Linux and Unix-like distributions, there is a system of [file permissions]("https://help.ubuntu.com/community/FilePermissions"). In a multi-user environment this not only helps prevent people being nosy and looking at stuff that they shouldn't, it also helps protect against accidental damage to important files, such as those held in "root" (e.g. system files). 

If you tell us what you were trying to do, we can guide you through the appropriate steps for temporarily elevating privileges.

---

### Post by RobGoss on 2015-05-17
I was just backing some Linux command notes I made using Tomyboy note, after syncing my note it seems like they were saved in this root - folder. I'm sure it's to my best interest not to mess with this folder or change anything.

---

### Post by sandyd on 2015-05-17
Tomboy shouldn't be able to save stuff inside the /root folder unless tomboy is running as root.

Whats the output of
```

sudo ls -la /root
```

---

### Post by RobGoss on 2015-05-17
Here you go thanks

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ls -la /root[/FONT][/COLOR] 
```


Here's the out put

```
 total 32drwx------  6 root root 4096 May  9 12:19 .
drwxr-xr-x 23 root root 4096 May 11 16:47 ..
-rw-r--r--  1 root root 3106 Feb 19  2014 .bashrc
drwx------  4 root root 4096 May  9 09:20 .cache
drwx------  3 root root 4096 May  9 09:20 .dbus
drwxr-----  2 root root 4096 May 17 07:08 .hplip
-rw-r--r--  1 root root  140 Feb 19  2014 .profile
drwx------  3 root root 4096 May 11 16:49 .synaptic



```

---

### Post by sandyd on 2015-05-17
It uses temporarily elevated permissions to list files in the root folder

---

### Post by ajgreeny on 2015-05-17
It allows you as user to temporarily raise your ability to see what is in that folder.

In Ubuntu we use **sudo** as a prefix to commands in order to raise the command status to that of the root account, which is by default disabled in Ubuntu, meaning that we can not log in as the root user.
The rest of the command then simply lists, line by line, including all hidden folders and files, everything in the /root folder.  Just try it and you will see.
You can use the same command without the sudo prefix to view all that is in your home, ie **ls -la** in terminal will list your home files and folders
See Root-Sudo in my signature for all the details.

---

### Post by sandyd on 2015-05-17
Yep, tomboy has never stored files in /root, it stores notes in ~/.local/share/tomboy

---

### Post by RobGoss on 2015-05-17
Thank you guys so much for your time and help. Much appreciated.

---

### Post by RobGoss on 2015-05-17
Thank you guys so much for the help.

---

