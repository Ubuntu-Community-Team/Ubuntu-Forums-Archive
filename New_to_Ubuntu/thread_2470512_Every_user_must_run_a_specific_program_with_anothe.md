---
title: "Every user must run a specific program with another user, by default"
date: 2022-01-02
forum: New to Ubuntu
---

### Post by 90v45mfsdhbgsd on 2022-01-02
We are "userA", "userB" and "userC" and we want DOSBox run with user "DOS" for anyone of us.

So, I do this:

```
useradd DOS
passwd DOS
mkdir /home/DOS
chown DOS:DOS /home/DOS
chmod u+s /home/DOS
chmod g+s /home/DOS
chmod a+s /home/DOS

chown DOS:DOS /usr/bin/dosbox
chmod u+s /usr/bin/dosbox
chmod g+s /usr/bin/dosbox
chmod a+s /usr/bin/dosbox
```

and then I run dosbox.
I get
```
DOSBox version 0.74-3
Copyright 2002-2019 DOSBox Team, published under GNU GPL.
---
No protocol specified
No protocol specified
No protocol specified
&#931;&#966;&#940;&#955;&#956;&#945; &#954;&#945;&#964;&#940;&#964;&#956;&#951;&#963;&#951;&#962; (segmentation fault) (core dumped)
```

Am I following the correct procedure?
With other words, the problem is in dosbox or before keyboard?

---

### Post by yancek on 2022-01-02
> We are "userA", "userB" and "userC" and we want DOSBox run with user "DOS" for anyone of us.
 

I'm not sure why you would want to do that but if the user DOS can run the program, did you try using chgrp to add your 3 users to the DOS group with execute permissions?  THe error you report doesn't seem as if it would be resolved by this.  How do you run dosbox, terminal command?  As user DOS:  Have you tried as other users?

---

### Post by Impavidus on 2022-01-02
To make program dosbox run as user DOS, what matters is that the executable is owned by user DOS and its setUID bit has been set. Note that the setUID bit is ignored on shell scripts, as that poses a security risk.

There's no need to set the setGID bit or the sticky bit. I don't think it does any harm. Also, to run a program as user DOS, there's no need for DOS to have a home directory and a password, but you may have other reasons why you may want one. Also, no need for special permissions on DOS's home directory (and setUID on a directory is ignored anyway). This tells me you don't fully grasp the meaning of setUID, setGID and sticky bit. If you tell us more about your intentions, we may be able to help.

Also keep in mind that when running a setUID program, it runs as a different user, but still has the home directory and the rest of the environment set to that of the original user.

The error message only tells us that the program ran and encountered some error. Without knowing dosbox, I can't tell what error it is. Segmentation faults usually result from bugs in the program or loading an incompatible version of some shared library.

---

### Post by 90v45mfsdhbgsd on 2022-01-02
> **yancek said:**
> I'm not sure why you would want to do that but if the user DOS can run the program, did you try using chgrp to add your 3 users to the DOS group with execute permissions?  THe error you report doesn't seem as if it would be resolved by this.  How do you run dosbox, terminal command?  As user DOS:  Have you tried as other users?

What I want for DOSBox, ScummVM and Wine, is run with a specific user and save their data in a specific user's home folder.

So, any user runs DOSBox with games and configuration in /home/DOS.
So, any user runs Wine with programs and configuration in /home/DOS. 
So, any user runs ScummVM with games and configuration in /home/DOS.

Changing the ownership to DOS : DOS for /usr/bin/dosbox, dosbox is not running anymore for everyone.

PS: another solution is hardlink directories with programs, games and configurations, to any other account home directory.

---

### Post by 90v45mfsdhbgsd on 2022-01-02
> **Impavidus said:**
> Also keep in mind that when running a setUID program, it runs as a different user, but still has the home directory and the rest of the environment set to that of the original user.

Wow. Thats exactly my reason of run the dosbox with another user. It seems I am wrong.

Basically I want the same configuration files and same games and savegames for EVERY user in computer.
The same for Wine and for ScummVM.

Hardlinking all of these to each user's home directory is a solution but this is not apply to newly created users automatically.

---

### Post by grahammechanical on 2022-01-02
I am confused. Do you want help getting DOSbox to run? Or, do you want advice on setting up a special user account that several people can login into an run DOS/Windows games through emulators? These are two different problems.

I am a single user. I have no experience with DOSbox or ScummVM. I have installed Wine and I do run a Windows application through Wine. I can tell you this:

In Ubuntu we install Wine the same way we install any other application. And Wine's application files are placed in directories/folders under the root directory. My user is then able to run Wine and use Wine to install Windows applications. The application files for that Windows application are then put in a directory/folder under home/username/. My user can then run that Windows application. If I give other people my login password they will also be able to run that Windows application. 

But other users who login to their own account will not be able to run that Windows application unless they install it through Wine. 

My login in password is also the administrator password. I do not want other people to have access to my user password. But I can do what you want to do. I can set up a special user account that does not have administrator access. I log in to that special user account and use the emulator I have installed (as administrator under my own username and password) to install and run DOS/Windows games. Anyone who has the password to the special user account will be able to run those DOS/Windows applications I have installed. All the configuration files for those games will be in the same directories/folders under that home/special username/.

Your problem with DOSBox is a separate problem.

[https://www.dosbox.com/DOSBoxManual.html]("https://www.scummvm.org/")

[https://www.scummvm.org/](https://www.scummvm.org/)

[https://appdb.winehq.org/](https://appdb.winehq.org/)

Regards

---

### Post by 90v45mfsdhbgsd on 2022-01-02
> **grahammechanical said:**
> I am confused. Do you want help getting DOSbox to run?

My concept is to use a shared user for DOSBox, Wine and ScummVM only.
Everyone login with its own account and only when run these 3 programs, these 3 programs executed from the shared user automatically.
So, all data of that 3 programs lie on the same /home/shared_user directory and are common for everyone.
I though that setuid/setgid flag can do this, but finally it seems cannot do this.

Another solution is to forget about shared user. Instead hardlink settings from my account to all others (including accounts not yet created)

---

### Post by Impavidus on 2022-01-02
Hardlinks only work for ordinary files, not for directories. The filesystem actually supports hardlinked directories, but the OS doesn't like it. Most applications will be happy with symlinks too. But then, the files or directories you link to (hardlinks or symlinks) still have an owner and set of permissions and some applications actually check to make sure others than the user running the application cannot modify the settings, or they simply reset permissions so that another user can no longer change the settings.

Maybe it's possible to abuse sudo for this. Write a wrapper (shell script) for the applications you want, which will in turn run the applications with sudo and the right options to change user to DOS and set the environment correctly. Then configure sudo such that the different users can run the sudo commands specified in the wrapper without providing a password. Configuring sudo is considered a pretty advanced skill.

The thing is, Linux is designed as a system for multiple users, where all users are kept separate from each other. You try to go straight against the basic design of Linux.

---

