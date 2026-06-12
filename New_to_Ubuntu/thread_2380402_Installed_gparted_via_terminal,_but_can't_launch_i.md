---
title: "Installed gparted via terminal, but can't launch it"
date: 2017-12-16
forum: New to Ubuntu
---

### Post by sterator on 2017-12-16
I used the terminal sudo apt install gparted  which seemed to be successful

When I hit the super key, and type g-p-a....I see gparted's icon, I hit return, I enter my credentials but gparted isn't launched.

Am I missing something?

Thank you!

---

### Post by oldfred on 2017-12-16
If you run this, does it work?
sudo -H gparted

---

### Post by deadflowr on 2017-12-17
17.10 by chance?
If so, please read post #1 of this thread:
[https://ubuntuforums.org/showthread.php?t=2375077]("https://ubuntuforums.org/showthread.php?t=2375077")

---

### Post by sterator on 2017-12-17
> **oldfred said:**
> If you run this, does it work?
sudo -H gparted

I can't tell because when I run the command when logged as standard user, terminal asks for my password, but then says that my username is not in the sudoer's file - which it isn't.

How can I instruct terminal that I am the admin also? Is there a way to tell it that?

Thank you

I have a standard user and an administrator for security (an article I read years ago advised against one's everyday user having Admin priveleges)

---

### Post by QIII on 2017-12-17
Hello!

Are you using Ubuntu or a derivative?  Your username, if it was the one used to create the installation, should be a sudoer.

If you are using a second account that is not a sudoer, you can access the admin user by **s**witch **u**ser:

```
su admin_user_name
```

at the password prompt, enter admin_user_name's password.

Remember to return to your non-admin user when you are done.

---

### Post by sterator on 2017-12-17
> **QIII said:**
> Hello!

Are you using Ubuntu or a derivative?  Your username, if it was the one used to create the installation, should be a sudoer.


17.10 Ubuntu

Yes, you are quite right. my "standard" user was the name I used to set up the installation. but afterward, I created another user to be the Admin, and demoted the first user to Standard.

---

### Post by sterator on 2017-12-17
> **QIII said:**
> Hello!

Are you using Ubuntu or a derivative?  Your username, if it was the one used to create the installation, should be a sudoer.

If you are using a second account that is not a sudoer, you can access the admin user by **s**witch **u**ser:

```
su admin_user_name
```

at the password prompt, enter admin_user_name's password.

Remember to return to your non-admin user when you are done.

tells me:  "No passwd entry for user 'admin_user_name'

that doesn't seem right...

---

### Post by QIII on 2017-12-17
Did you use "admin_user_name" verbatim?  

If you did then use the actual name of the admin.  :)

---

### Post by sterator on 2017-12-17
> **QIII said:**
> Did you use "admin_user_name" verbatim?  

If you did then use the actual name of the admin.  :)

this is what I typed

su artboxeR



where, 'artboxeR'  is the admin user on the computer in question

the terminal responds with this:

No passwd entry for user 'artboxeR'

I am wide open to that perhaps I did something wrong

---

### Post by deadflowr on 2017-12-17
You can find the username in the /etc/passwd file.
You can limit the output to only the users you created thus far by grepping like so
```
getent passwd | grep 100[0-9]
```
UID 1000 is the first user you created, so the second would be 1001.
The proper name is the first in whatever the output shows like
```
**bob**:x:1000:1000::Bob Denver,,,:/home/bob:/bin/bash
```

Use that to check that you spelled the name correctly.

(Also I don't know if grepping is a proper word, but I liked writing it, so there)

---

### Post by sterator on 2017-12-19
> **deadflowr said:**
> You can find the username in the /etc/passwd file.

so..bear with me, please...that looks to me like a path, beginning at root. Is this correct?

The highest (rootiest?) I can get in the file manager is Home

Lacking that file, when I open the Users panel, I see my admin named, clearly spelled, just as I typed it in terminal and was told no password.

Is it possible that something is broken? When I say, 'broken,' I mean something like a disconnect..

Thank you!

---

### Post by deadflowr on 2017-12-19
> Is it possible that something is broken?
Yes

I would forget about the odd user you created and either try resetting the original user as the admin
 (since there wasn't any real benefit to removing that user from the admin group)
or try creating a new user again.
You can do all this (either reset the original or make a new user) in recovery mode.
After reseting or creating the new/or old user, simply delete the bad user that isn't working right.

---

### Post by sterator on 2017-12-19
Can't I simply make my standard user an Admin using the Users panel? Why is recovery needed?

Thank you

---

### Post by yancek on 2017-12-19
> Can't I simply make my standard user an Admin using the Users panel? Why is recovery needed?

I don't see how as you apparently don't have admin/root privileges based on your posts.  The original user you created during the install had root/admin privileges.  That's the default.  You removed those privileges by making that user a standard user.  You then created an admin user but you apparently don't have a password or the correct password for this second user.  Therefore, you will not be able to make system changes.  When you created the 'admin' user you referenced, did you create a password for that user?

---

### Post by sterator on 2017-12-19
The place of difficulty is in switching the user in the terminal using su

When the os asks for administrator credentials, it shows the name of the administrator, and accepts when I supply the administrator password.

---

### Post by sisco311 on 2017-12-19
> **sterator said:**
> 
When the os asks for administrator credentials, it shows the name of the administrator, and accepts when I supply the administrator password.

So, can you confirm that you can run applications as root?
What's the output of:
```
pkexec id
```

And what happens when you try to run gparted:
```
pkexec  gparted
```

---

### Post by sterator on 2017-12-19
pkexec id does ask for my admin credentials AND shows the correct admin name (the same spelling as I've typed)
The output is:  

```

uid=0(root) gid=0(root) groups=0(root)
```

the output of 
pkexec  gparted is:

```
Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/boot-efi.mount &#8594; /dev/null.
Created symlink /run/systemd/system/media-artmaker-Bento_Backup.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-1000.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-124.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
Invalid MIT-MAGIC-COOKIE-1 key
(gpartedbin:3963): Gtk-WARNING **: cannot open display: :0
Removed /run/systemd/system/-.mount.
Removed /run/systemd/system/boot-efi.mount.
Removed /run/systemd/system/media-artmaker-Bento_Backup.mount.
Removed /run/systemd/system/run-user-1000.mount.
Removed /run/systemd/system/run-user-124.mount.
Removed /run/systemd/system/tmp.mount.
```

---

### Post by sterator on 2017-12-19
> **deadflowr said:**
> 
 (since there wasn't any real benefit to removing that user from the admin group)



No benefit from making my everyday user be standard and not admin?  Isn't that good security practice?

---

### Post by yancek on 2017-12-19
> No benefit from making my everyday user be standard and not admin?  Isn't that good security practice? 		

It would have been simpler to create another 'standard' user rather than an admin user as the default user created when you install is the admin.  With a default install, the default user created has admin privileges but you also need to use sudo and have the password to make any system changes outside your user /home/user directory.

---

### Post by sisco311 on 2017-12-19
> **sterator said:**
> pkexec id does ask for my admin credentials AND shows the correct admin name (the same spelling as I've typed)
The output is:  

```

uid=0(root) gid=0(root) groups=0(root)
```

the output of 
pkexec  gparted is:

```
Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/boot-efi.mount &#8594; /dev/null.
Created symlink /run/systemd/system/media-artmaker-Bento_Backup.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-1000.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-124.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
Invalid MIT-MAGIC-COOKIE-1 key
(gpartedbin:3963): Gtk-WARNING **: **cannot open display: :0**
Removed /run/systemd/system/-.mount.
Removed /run/systemd/system/boot-efi.mount.
Removed /run/systemd/system/media-artmaker-Bento_Backup.mount.
Removed /run/systemd/system/run-user-1000.mount.
Removed /run/systemd/system/run-user-124.mount.
Removed /run/systemd/system/tmp.mount.
```

The `cannot open display: :0' warning indicates that your issue is related to the one linked by deadflowr: [https://ubuntuforums.org/showthread.php?t=2375077](https://ubuntuforums.org/showthread.php?t=2375077)


> **sterator said:**
> No benefit from making my everyday user be standard and not admin?  Isn't that good security practice?

You have to understand how your system works. I would suggest you to start with the basics like users/groups, sudo/su and polkit...

**Security is an ongoing process and, like an onion, it has layers and stinks. The best defense you have is to read and learn how to secure your OS** [COLOR="#A52A2A"]~bodhi.zazen[/COLOR]

---

### Post by sterator on 2017-12-19
I'm using the same 2-user method I've used for awhile on OSX, in that I had an everyday user which was standard, and an Admin user for times when I needed to modify the system in anyway.

When I installed Ubuntu, yes, my first user was an Administrator..I later created another user as an Admin, and changed the first user to Standard because my Documents were under that User.

If I had to do it again, I would have left the first user as Admin. Maybe I took the long way 'round the barn to feed the chickens, but I haven't harmed anything, have I?

It's not like one would create and delete Users willy-nilly, but if they need to be changed or deleted, one can do that, right?

Thank you..I am going to be roping off some time to learn the basics, as you say..I appreciate throwing out some topics I should cover.

---

### Post by oldfred on 2017-12-19
With Ubuntu you do not need two users, you just use sudo when you need to do system things.

 Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
sudo is not to be used for GUI applications. current recomedend method is
sudo -H # which keeps /home as location of files.

---

### Post by sterator on 2017-12-20
> **oldfred said:**
> With Ubuntu you do not need two users, you just use sudo when you need to do system things.

thank you, oldfred

that's a huge rock off my toe. based on the advice for OS X users, I felt like I was flying without a net.

Thank you for the links; I've got some reading to do. I appreciate your pointing me the way.

---

