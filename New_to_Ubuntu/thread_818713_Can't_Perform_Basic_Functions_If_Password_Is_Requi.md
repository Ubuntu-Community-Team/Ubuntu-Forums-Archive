---
title: "Can't Perform Basic Functions If Password Is Required"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-06-04
HELP! 

For some unknown reason, suddenly my computer will not let me perform any basic functions if a password is required. After I enter the password I get a message that says that I am not allowed to run this program or perform this function. I can log on to my computer normally, when it boots up and I enter my password, but after that if I have to enter my password to carry out an internal function, nothing works. However, if I use the terminal, and the SU command I can then log in as root. I know it is not a password error, because I can log in as root using that password.

Here are three examples of what I am talking about.

(1) AFTER CLICKING ON THE ICON FOR UPDATE MANAGER
    and entering my password...I get:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '60817411' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpILhCDp' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.


(2) AFTER CLICKING ON THE ICON FOR LOGIN WINDOW
    and entering my password...I get:

Failed to run /usr/sbin/gdmsetup as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

(3)AFTER CLICKING ON THE ICON FOR SYNAPTIC PACKAGE MANAGER
   and entering my password...I get:

Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
_________________________________________________________________________________________________________________________

In addition to all of the above, if I try to mount another drive that is attached to my computer, I get this error: 

CANNOT MOUNT VOLUME    You are not privileged to mount the volume 'NTFS Local Disk'.


In spite of all this I can still logon as root at a terminal prompt, if I type as below:

jim@jim:~$ SU
Password: **********
root@jim:/home/jim# 

(now I am logged in as root)


At the prompt above, if I type in the command  /usr/sbin/gdmsetup, it works, the login window opens.
At the prompt above, if I type in the command  /usr/sbin/synaptic, it works, the synaptic package manager program opens.


None of these problems were happening yesterday.

Does anybody have any idea how to fix these problems?


JBA2337

---

### Post by Oldsoldier2003 on 2008-06-04
run the command ```
id <your user name>
``` and if you are not part of the group "admin" run ```
usermod -aG admin <your_user_name>
``` as root

---

### Post by sdennie on 2008-06-04
It sounds like the user you are logged in as isn't in the admin group.  If you are able to get to root in some manner, this should fix it:

```

adduser your_username admin

```

---

### Post by JBA2337 on 2008-06-04
To: OldSoldier2003  and  vor

Thank you very much for your help! After I added my name into the admin group, most of the problems that I mentioned in my previous message went away. I can now use the Synaptic Package Manager, the Login Windows and other similar functions, as it should be. THANKS!!!

I wonder how my name got deleted from the admin group in the first place. Everything was working OK yesterday.

I still have one problem though. In my system I have a 120 GB NTFS drive, with Windows XP sp3, and on this same drive I have a 50 GB ext3 partition where I have Ubuntu installed. While in Ubuntu I installed the NTFS-config program, so that I can mount and have access to the data on the NTFS drive. However, if I try to mount this drive, I always get a message,
"Cannot mount volume. You are not privileged to mount the volume 'NTFS Local Disk'.

I was using this drive yesterday, from within Ubuntu, so something changed since then.

How do I get "privileges" so that I can mount the NTFS Drive while in Ubuntu?

JBA2337

---

### Post by Oldsoldier2003 on 2008-06-05
try looking over this post: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) it covers in detail how to mount drives and what settings are needed

---

