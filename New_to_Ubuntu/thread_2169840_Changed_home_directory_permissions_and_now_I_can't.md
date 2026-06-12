---
title: "Changed home directory permissions and now I can't login."
date: 2013-08-23
forum: New to Ubuntu
---

### Post by devongarber1 on 2013-08-23
Hello,
I was trying to keep one user from viewing my home directory so I changed the advanced permissions in Dolphin so that the user couldn't read or write. Then later when I logged in the screen just went black and went back to the login screen. I have Kubuntu 13.04. I have tried all kinds of chmod commands.

---

### Post by coffeecat on 2013-08-23
You may find this tutorial helpful for rescuing the situation:

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

Since you can't log in to a GUI, you would need to press ctrl-alt-F1 at the login screen to get to a virtual terminal from where you can run all the commands.

---

### Post by devongarber1 on 2013-08-23
Unfortunately, that didn't work. But when I tried to access .dmrc in nano I noticed it said ```
[ Error reading /home/devon/.dmrc: Permission denied ]
``` then I ran the first two commands again and it let me look at it, so I rebooted and it says "Permission denied" again! :confused:

---

### Post by coffeecat on 2013-08-23
If you ran the commands for correcting ownership and permissions on .dmrc from that tutorial correctly you would not get a permission denied error. 

From the virtual console, run:

```
ls -l /home/devon/.dmrc
```

And look at section 5 of that tutorial again. You may have missed something.

---

### Post by devongarber1 on 2013-08-23
This is the output of ls -l: ```
----rw----+ 1 devon devon 29 Aug 23 16:18 /home/devon/.dmrc
``` I ran those commands a few more times, but I noticed in my other user when I go to /home/devon and look at .dmrc's properties it says ```
Owner: Forbidden
Group: Can Read & Write
Others: Forbidden
``` but when I run those commands it says ```
Owner: Can Read & Write
Group: Can Read
Others: Can Read
```, then when I try to log in all the permissions go back. This is the output of ls -l after I run the commands.```
-rw-r--r--+ 1 devon devon 29 Aug 23 16:27 /home/devon/.dmrc
```

---

### Post by coffeecat on 2013-08-24
> **devongarber1 said:**
> This is the output of ls -l: ```
----rw----+ 1 devon devon 29 Aug 23 16:18 /home/devon/.dmrc
``` 

That is 060 permissions which is unusable. The only way I know to get that would have been to run:

```
chmod 060 /home/devon/.dmrc
```

Which is not in that tutorial at all. I wonder if 060 was a typo for 600. Check and double-check any terminal command before you run it.

> **devongarber1 said:**
> I ran those commands a few more times, but I noticed in my other user when I go to /home/devon and look at .dmrc's properties it says ```
Owner: Forbidden
Group: Can Read & Write
Others: Forbidden
``` but when I run those commands it says ```
Owner: Can Read & Write
Group: Can Read
Others: Can Read
```,

Why are you running commands from your "other" user? This only complicates things, and shouldn't work anyway. That is why I suggested to run commands from a virtual terminal. Again: press Ctrl-Alt-F1 from the login screen to open a virtual terminal, log in as devon and then run the commands. Do not run any of these commands from your other user.

> **devongarber1 said:**
>  then when I try to log in all the permissions go back. This is the output of ls -l after I run the commands.```
-rw-r--r--+ 1 devon devon 29 Aug 23 16:27 /home/devon/.dmrc
```

What with the above, I can't follow what is going on. That last set of permissions is 644, which is exactly what .dmrc should be. 

Boot up, at the GUI log in screen go to tty1 with Ctrl-Alt-F1, log in as devon and follow the tutorial again, section 5. **Do not log in as your other user.** Now press Ctrl-Alt-F7 to get you to tty7. Log in as devon. Check that everything is working as it should be. Reboot and see if you can log in as devon again. Only then consider what you need to be doing to prevent another account from seeing your devon files, but I think that might need a separate thread.

---

### Post by Morbius1 on 2013-08-24
@coffeecat,

Don't mean to interrupt but we still don't know what the permissions are on /home/devon/.dmrc
> **devongarber1 said:**
> This is the output of ls -l:  ```
----rw----+ 1 devon devon 29 Aug 23 16:18 /home/devon/.dmrc
```
That little "+" at the end of the permissions indicates that when he went into advanced permissions in Dolphin he activated an Access Control List for that object. An "ls -l" won't tell you the real permissions. You need to run something like this:
```
getfacl -t /home/devon/.dmrc
```
I try to stay away from ACL's because they are too complicated for my little brain but I remember the "+" indicating that it is in control of permissions.

---

### Post by coffeecat on 2013-08-24
> **Morbius1 said:**
> Don't mean to interrupt but we still don't know what the permissions are on /home/devon/.dmrc

That little "+" at the end of the permissions indicates that when he went into advanced permissions in Dolphin he activated an Access Control List for that object. An "ls -l" won't tell you the real permissions. You need to run something like this:
```
getfacl -t /home/devon/.dmrc
```
I try to stay away from ACL's because they are too complicated for my little brain but I remember the "+" indicating that it is in control of permissions.

@Morbius1, interrupt away! :) I'm sure I missed something, because I'm not particularly familiar with Dolphin's features. Thanks for the input!

---

### Post by devongarber1 on 2013-08-24
Sorry, I should have been more clear. I can't really run those commands in my other user as it is not a sudoer. I was just reading this thread from it and viewing the permissions of .dmrc in Dolphin. I tried running the commands again but still with the same outcome. This is the output of getfacl: ```
getfacl: Removing leading '/' from absolute path names
# file: home/devon/.dmrc
USER     devon    ---
user      apache   ---
GROUP   devon    ---
mask                 rw-
other                 ---
``` apache is my other user.

---

### Post by sandyd on 2013-08-24
> **devongarber1 said:**
> Sorry, I should have been more clear. I can't really run those commands in my other user as it is not a sudoer. I was just reading this thread from it and viewing the permissions of .dmrc in Dolphin. I tried running the commands again but still with the same outcome. This is the output of getfacl: ```
getfacl: Removing leading '/' from absolute path names
# file: home/devon/.dmrc
USER     devon    ---
user      apache   ---
GROUP   devon    ---
mask                 rw-
other                 ---
``` apache is my other user.

try
```

sudo setfacl -x u:devon /home/devon/.dmrc
sudo setfacl -x u:apache /home/devon/.dmrc
sudo setfacl -x g:devon /home/devon/.dmrc

```

if you cant login to a user with sudo privileges, choose "recovery mode" during computer startup (may have to press a key to make the grub menu show), and run it there

---

### Post by devongarber1 on 2013-08-24
Ok, I ran: ```
sudo setfacl -x u:devon /home/devon/.dmrc
sudo setfacl -x u:apache /home/devon/.dmrc
sudo setfacl -x g:devon /home/devon/.dmrc
sudo chown -R devon /home/devon
chmod 755 /home/devon
chmod 644 /home/devon/.dmrc
``` I checked the permissions with ls -l which were: ```
-rw-r--r--+
``` so I tried to log in and the permissions went back to: ```
----rw----+
``` :confused:

---

### Post by sandyd on 2013-08-24
sorry - typo there, should be
```
sudo setfacl -b /home/devon/.dmrc
```

---

### Post by devongarber1 on 2013-08-26
Ok I just fixed it. It turns out either .dmrc wasn't completely the problem or I was the running the commands in the wrong order. First I ran all of the commands in #5 of the tutorial. Then I ran ```
sudo setfacl -b /home/devon
``` instead of ```
sudo setfacl -b /home/devon/.dmrc
``` Thanks for the help!:)

---

