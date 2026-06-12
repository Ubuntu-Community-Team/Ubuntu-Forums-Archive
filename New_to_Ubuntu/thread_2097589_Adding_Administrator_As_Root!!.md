---
title: "Adding Administrator As Root!!"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by freesparks on 2012-12-23
Hello Everyone,

     Please tell me i'm not going crazy.  It used to be that after a fresh ubuntu install, in order to create a root user, or better yet add the current administrator as a root user, I simply typed:

sudo passwd root

     After typing the above in the terminal, I am prompted to enter a new password, I enter the password and all done.

     In 12.04.1, I do the following as described above and and i get:

 <myusername> is not in the sudoers file.  This incident will be reported.  Please excuse my ignorance, but I've never encountered this error upon a fresh ubuntu install.  Any help would be greatly appreciated.

---

### Post by epicoder on 2012-12-23
Giving the root user a password is generally frowned upon on systems with sudo (Ubuntu included) and it is not really necessary. Instead, obtain a root prompt (see below if you aren't sure how to do this) and execute this to add yourself to the sudo group:
```
adduser yourusername sudo
```From there, you can run any command as root with ```
sudo command...
```Unless you really need to have it, you should disable the root password to prevent direct logins as root, using this command (you will need root permissions for this):
```
passwd root -l
```It will still be possible to obtain a root shell using ```
sudo -s
``` (see below).

To get a root shell:
```
su
```You must have a root password for this to work. Answer the "Password:" prompt with the root password. You really shouldn't be using this method if you have sudo installed. 

```
sudo -s
```The user you run this as needs to be in the sudo group. Just run it at the normal terminal prompt and type in the password you use to log in. This is the preferred method.

Recovery mode:
This is a bit harder and usually you will want to use the above methods. However, this is the only way to get a root prompt without a password, unless your system is really broken. Use this if your root account doesn't have a password and none of your normal accounts are in the sudo group.
Reboot your system. Hold shift until the boot menu appears. Below the normal "Ubuntu [version] [kernel]" option, there should be an option that has "(recovery mode)" appended to the normal Ubuntu version details. Choose that one, and once it boots up, use the arrow keys and enter to select the option that gives you a root shell.

Strictly speaking, you really shouldn't be using a root shell at all unless it's absolutely necessary. It's much safer to remain a normal user and use sudo when needed.

---

### Post by freesparks on 2012-12-23
I really appreciate the quick response sh228, and I understand completely and have no wish to do it because I was using sudo with no problems when doing simple installs and now I'm being asked for it.

     I ran the command:

adduser <myusername> sudo

and i get:

adduser: only root may add a user or group to the system.

What in the world could be causing this.  I've never encountered this before as I said.  Thanks for the quick response.

---

### Post by epicoder on 2012-12-23
You need to have root permissions before you can manipulate users or groups. In short, you need a root shell. See the section from my other post on how to do this (replicated here for convenience):


To get a root shell:
```
su
```You must have a root password for this to work. Answer  the "Password:" prompt with the root password. You really shouldn't be  using this method if you have sudo installed. 

```
sudo -s
```The user you run this as needs to be in the sudo  group. Just run it at the normal terminal prompt and type in the  password you use to log in. This is the preferred method.

Recovery mode:
This is a bit harder and usually you will want to use the above methods.  However, this is the only way to get a root prompt without a password,  unless your system is really broken. Use this if your root account  doesn't have a password and none of your normal accounts are in the sudo  group.
Reboot your system. Hold shift until the boot menu appears. Below the  normal "Ubuntu [version] [kernel]" option, there should be an option  that has "(recovery mode)" appended to the normal Ubuntu version  details. Choose that one, and once it boots up, use the arrow keys and enter to select the  option that gives you a root shell.

---

### Post by haqking on 2012-12-23
> **freesparks said:**
> I really appreciate the quick response sh228, and I understand completely and have no wish to do it because I was using sudo with no problems when doing simple installs and now I'm being asked for it.

     I ran the command:

adduser <myusername> sudo

and i get:

adduser: only root may add a user or group to the system.

What in the world could be causing this.  I've never encountered this before as I said.  Thanks for the quick response.

you are already a sudo user if you were carrying out sudo commands.

And that message means you need to adduser with sudo privelege such as:

sudo adduser <username>

I dont get what you are asking as you are already as sudo user demonstrated byt the command entered in your original post.

Your title is misleading as you dont add anyone to root, root is root.  If you mean give admin sudo privelege then you already have it and admin typically implies sudo permission.

Your OP didnt have any problems in it, you gave root a password (though not needed in systems with sudo) and that was it, the message you got at the end is typical.

---

### Post by freesparks on 2012-12-23
Yes, i did that sh228, thanks for the reply, but it's still nt working.  I then proceeded to hold down shift in order to add my username as a root user, still no luck.

I see the login as:

root@<mycomputername>

but I am getting the error:

gpasswd: cannot locak /etc/group; try again later
adduser: /usr/bin/gpasswd -a <myusername> sudo returned error code 1.  Exiting.

    Again, I've never encountered this problem before and I've been using Ubuntu since version 9.04.  Usually, as you pointed out, i only use root when I'm prompted for it.  Thanks so much for your help.

---

### Post by haqking on 2012-12-23
> **freesparks said:**
> Yes, i did that sh228, thanks for the reply, but it's still nt working.  I then proceeded to hold down shift in order to add my username as a root user, still no luck.

I see the login as:

root@<mycomputername>

but I am getting the error:

gpasswd: cannot locak /etc/group; try again later
adduser: /usr/bin/gpasswd -a <myusername> sudo returned error code 1.  Exiting.

    Again, I've never encountered this problem before and I've been using Ubuntu since version 9.04.  Usually, as you pointed out, i only use root when I'm prompted for it.  Thanks so much for your help.

YOU ARE ALREADY A SUDO USER.

If you want to use root then su and enter the password you entered when you created one in the first post.

But no need to use ROOT as you have sudo privelege so to carry out an admin action then type sudo and enter your own user password when prompted

EDIT: I think i might be misreading you, let me read it again.

ok so show us output of

```
groups
```

---

### Post by freesparks on 2012-12-23
Again, yes haqking, you're absolutely right.  For example, I just tried installing Synaptic Package Manager in the Ubuntu Software Center, and I am being prompted for:

Password for root:

     I retraced my steps and I never even created a root password.  I only created a user as Administrator during the installation.  I'm so puzzled by all of this because I've never encountered this problem.  Again, thank you for all the help.

---

### Post by freesparks on 2012-12-23
the output for groups is:

<myusername> dialout

  No idea what this means as I've never encountered this problem.  Thank you so much!!

---

### Post by haqking on 2012-12-23
> **freesparks said:**
> Again, yes haqking, you're absolutely right.  For example, I just tried installing Synaptic Package Manager in the Ubuntu Software Center, and I am being prompted for:

Password for root:

     I retraced my steps and I never even created a root password.  I only created a user as Administrator during the installation.  I'm so puzzled by all of this because I've never encountered this problem.  Again, thank you for all the help.

yes that means enter your sudo password which is YOUR password.

the command you entered in the first post was giving ROOT a password which by default it doesnt have.

When asked for a ROOT password enter your own.

However please show us output of

```
groups
```

---

### Post by epicoder on 2012-12-23
> **freesparks said:**
> 
gpasswd: cannot locak /etc/group; try again later
adduser: /usr/bin/gpasswd -a <myusername> sudo returned error code 1.  Exiting.

A quick google suggests that your root partition is mounted as readonly while in recovery mode. Try booting into recovery mode again, then running this at the root prompt before trying to add yourself to sudo again:
```
mount -o remount,rw /
```
This should remount the root partition as read-write instead of readonly.

---

### Post by freesparks on 2012-12-23
the output for groups is:

<myusername> dialout

---

### Post by freesparks on 2012-12-23
Wow, talk about growing pains.  Thank you so much, the last post fixed the issue perfectly.  

I rebooted in recovery mode and ran the command:

mount -o remount,rw /

    and added user using the post aforementioned.  Thanks again guys.

---

### Post by freesparks on 2012-12-23
Now output groups gives me:

<mysusername> dialout sudo

    which really isn't what I wanted but at leas i can install software again.  As you guys mentioned root should be its own entity as a fail safe.  This is why in previous version of ubuntu, all I had to do is do:

sudo passwd

    this would create a root account with a specific password that I designated and would only show itself when doing/running an elevated system command.  thanks again guys!!

---

### Post by DuckHook on 2012-12-24
I'm afraid that you still don't understand the point that previous posters have been trying to make:

1. There is never any need in Ubuntu for the typical user to activate the root account. By doing so, you have actually hobbled an important security feature of Ubuntu.
2. Any time you need to install software or run "an elevated system command" you don't need root. You only need the sudo command prefixed to whatever "elevated system command" that you want to run.
3. In Ubuntu, root is not a "fail safe". In fact, it is a security hole and should not be activated.

I am particularly in tune with your way of thinking because I too insisted on activating root when I first started using Ubuntu. Bad idea. My stubbornness led to my deleting my entire hard drive. Every file. Total calamity. Did I mention that it's a bad idea?

Anyhows, Linux is about choice, so if you insist on activating root, no one will or should stop you. I just hope that you never bork your whole install or delete your entire HDD.

---

### Post by Zill on 2012-12-24
> **DuckHook said:**
> ...1. There is never any need in Ubuntu for the typical user to activate the root account. By doing so, you have actually hobbled an important security feature of Ubuntu.
2. Any time you need to install software or run "an elevated system command" you don't need root. You only need the sudo command prefixed to whatever "elevated system command" that you want to run.
3. In Ubuntu, root is not a "fail safe". In fact, it is a security hole and should not be activated...
+1

Excellent advice!

I recommend the OP should read the [RootSudo Ubuntu documentation]("https://help.ubuntu.com/community/RootSudo").
> Enabling the Root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo.

---

