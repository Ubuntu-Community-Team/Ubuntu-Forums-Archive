---
title: "unable to perform tasks though I have super user privileges"
date: 2015-04-05
forum: Programming Talk
---

### Post by IAMTubby on 2015-04-05
Hello,
 I have two questions relating to permissions.

**First**, I am a super user on my system. I have confirmed this, see below commands. This confirms that IAMTubby is a superuser on this system.

```
root@IAMTubby-Inspiron-1545:/var/www# sudo usermod -a -G sudo IAMTubby
root@IAMTubby-Inspiron-1545:/var/www# sudo adduser IAMTubby sudo
The user `IAMTubby' is already a member of `sudo'.
root@IAMTubby-Inspiron-1545:/var/www# exit
exit

```

However, I'm not able to copy files and keep getting bumped out saying I don't have permissions to copy files within the /var/www folder

```

IAMTubby@IAMTubby-Inspiron-1545:/var/www$ whoami
IAMTubby
IAMTubby@IAMTubby-Inspiron-1545:/var/www$ touch helloworld.txt
touch: cannot touch `helloworld.txt': Permission denied

```

**Second**,
Keeping the context of file permissions, how does a client from a browser have permission to upload files on to a php server's file system running ubuntu, since he does not have super user privieges?
Because from what I can see, I'm not able to cp somefile /var/www/html/uploadsfolder  if I'm logged in as any user other than super user on my server. So how is any  client in the world able to cp files to /var/www/html/uploadsfolder since they are not superusers.

Please advise.
Thanks.

---

### Post by ian-weisser on 2015-04-05
> **IAMTubby said:**
> However, I'm not able to copy files and keep getting bumped out saying I don't have permissions to copy files within the /var/www folder

Correct.
/var/www is usually owned by root, not IAMTubby.
/var/www is usually  by the 'root' group, which IAMTubby is not a member of (and should not be a member of).

The user IAMTubby should use the 'sudo' command to do root-level tasks.
```
/var/www$ **sudo** touch helloworld.txt
```


> **IAMTubby said:**
> Keeping the context of file permissions, how does a client from a browser have permission to upload files on to a php server's file system running ubuntu, since he does not have super user privieges?
[...]So how is any  client in the world able to cp files to /var/www/html/uploadsfolder since they are not superusers.

The client has no permission to do anything. The serving application's setup is the important part.

The client (web browser) sends the upload request and file to the serving application (like Wordpress).
The serving application (on the server) receives the file.
The serving application usually has permission to save to /var/www/html/uploadsfolder

---

### Post by IAMTubby on 2015-04-05
Thanks ian-weisser

> **ian-weisser said:**
> 
/var/www is usually  by the 'root' group, which IAMTubby is not a member of (and should not be a member of).

But I thought that doing sudo adduser IAMTubby sudo would add me to the super user group, and from then onwards I can just execute any command that root can.
If that's not the case, then what does  sudo adduser IAMTubby sudo do?
Even before the command, I was able to execute any command by appending sudo before it, like sudo touch helloworld.txt


> 
The client has no permission to do anything. The serving application's setup is the important part.
The serving application usually has permission to save to /var/www/html/uploadsfolder
I have a couple of questions here.

1. Let's say we have a website of two files - index.html provides a file upload button, and this is form redirected to upload.php which basically copies the uploaded file to location on the file system of the remote server.
Now say, **upload.php has permission 777**. Why does it still need to do **sudo** cp uploadedfile /var/www/somelocationonserver. Why can't it just do cp uploadedfile /var/www/somelocationonserver ?

2. What does upload.php having permission 777 signify? Does it mean that it can create any file anywhere on the file system(something that only root was supposed to be able to do)?

3. Usually are the html and php files of permission 777? Because html and php files basically call each other and execute other other. So that can be possible only if they are of permission 777?

4.Right now, this is what I observe.
I'm logged in as me, which is IAMTubby. I have a script of 777 permission which does sudo ls > lsoutput. When I execute the script, it just says that it cannot create the lsoutput file. The only work around I found was to create a blank file called lsoutput of 777 permission and then run this script. But is this expected?
```

IAMTubby@IAMTubby-Inspiron-3542:/var/www/fileupload$ whoami
IAMTubby


IAMTubby@IAMTubby-Inspiron-3542:/var/www/fileupload$ ls -l myscript.php 
-rwxrwxrwx 1 root root 41 Apr  5 19:04 myscript.php

IAMTubby@IAMTubby-Inspiron-3542:/var/www/fileupload$ cat myscript.php 
<?php
exec("sudo ls > lsoutput")
?>

IAMTubby@IAMTubby-Inspiron-3542:/var/www/fileupload$ php myscript.php 
sh: 1: cannot create lsoutput: Permission denied


```

---

### Post by ethan26 on 2015-04-05
> But I thought that doing sudo adduser IAMTubby sudo would add me to the  super user group, and from then onwards I can just execute any command  that root can.
If that's not the case, then what does  sudo adduser IAMTubby sudo do?
Even before the command, I was able to execute any command by appending sudo before it, like sudo touch helloworld.txt
It adds you to the group in witch you type the password in for when you execute the sudo command for example:
```
IAMTubby@*:~$ sudo touch helloworld.txt
[sudo] password for IAMTubby:
```
so you have to type in the password for a user in the group sudo to use the sudo command
but I am no ubuntu/bash profesional so i could very well be mistaken so dont quote me. Just what I would assume if I were you.

---

### Post by ian-weisser on 2015-04-05
> **IAMTubby said:**
> But I thought that doing sudo adduser IAMTubby sudo would add me to the super user group, and from then onwards I can just execute any command that root can.
Yes and no.
Yes, IAMTubby can execute root-level commands (other users cannot)
No, IAMTubby must still use the 'sudo' command every time.

One purpose of 'sudo' is to prevent root-level user-caused accidents, like deleting your entire system instead of one folder due to a typo.
Another purpose of 'sudo' is top make clear to users which commands are user-level, and which are root-level.
Ubuntu uses sudo precisely because it offers those kinds of protections. 

> **IAMTubby said:**
> 1. Let's say we have a website of two files - index.html provides a file upload button, and this is form redirected to upload.php which basically copies the uploaded file to location on the file system of the remote server.
Now say, **upload.php has permission 777**. Why does it still need to do **sudo** cp uploadedfile /var/www/somelocationonserver. Why can't it just do cp uploadedfile /var/www/somelocationonserver ?
upload.php only needs permission the be run by the server user (like the 'wordpress' user). Permission 777 on an executable file is merely a security hazard - any user on that system can use it...or edit it...or replace it with an entirely different file of the same name.

The directory /var/www/somelocationonserver may be owned by root or by a different user entirely. Permission 777 means any user on that system can read/write/edit files in that directory...perhaps even users you don't want writing and editing files there.

In your specific example, you must still use sudo because /var/www/somelocationonserver is *either* not owned by the correct user *or* the user lacks write permission.

Let's say your server runs under the user 'myserver' instead of root (so that when the server is compromised, the hacker does not immediately gain root access!)
upload.php should be *owned* by 'myserver' (the only user that runs it). Appropriate permissions might be 774 or 754 (or others), so others can read or execute if needed.
/var/www/somelocationonserver should be owned by 'myserver' (the only user that writes to it). Appropriate permissions should be tighter, like 640, to limit the ability of other processes to read and execute arbitrary uploaded data.

I strongly advise against any internet-facing system to run network-connected services as root.
I strongly advise against ANY 777 files or directories on an internet-facing system outside of /tmp.

> **IAMTubby said:**
> <?php
exec("sudo ls > lsoutput")
?>

The php code should be executed by the webserver user ('myserver'), not you ('IAMTubby'), nor any browser client user ('IAMTubby', 'guest', etc.)
When php executes the code, it can't enter your sudo password. So that *should* fail.
Users who need to use sudo should generally use their ssh login instead.

---

