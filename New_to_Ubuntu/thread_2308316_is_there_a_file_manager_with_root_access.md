---
title: "is there a file manager with root access?"
date: 2016-01-01
forum: New to Ubuntu
---

### Post by idee on 2016-01-01
I am new to Ubuntu.  Is there a file manager that I can get into root privileges?  The primary reason is to manage folder privileges on my system.

thanks

---

### Post by sandyd on 2016-01-01
Permissions are probably best managed via the CLI via chown/chmod/etc. Note that moving/creating files folders in your home folder using nautilus as root is highly discouraged as you cannot modify those folders with your normal user account. The same goes for other system folders of which certain system users may require access to.

But if you want to run nautilus as root, you can use
```

sudo -H nautilus
```

---

### Post by QIII on 2016-01-02
I would suggest that as a new user you don't mess with permissions. At all.  If you change permission on a critical system file (or directory) you could render your system inoperable.  

Why don't you take some time to learn a bit more before embarking on something like this?

Might I ask what makes you think you need to change file or directory permissions right now?

---

### Post by monkeybrain20122 on 2016-01-02
As said above you can do it with Nautilus but I suspect you can do it will all file managers. But I don't know why you would want that. I know for a fact that if a few people I have installed *buntu for know this trick they would have messed up their systems because accidentally deleting/modifying system files would be too easily. I see this as a big advantage over Windows especially for people who are new to Linux and haven't had the time to change their click happy habit yet.

---

### Post by idee on 2016-01-02
Thanks.  I agree running as root and messing with permissions is not a good thing.  I have installed VirtualBox.  The previous folder with the image file in it has read only privileges.  I need to make those RW.  Thanks for the tip,  Though I am new to Ubuntu, I have used Linux for a couple of years.

---

### Post by buzzingrobot on 2016-01-02
The owner of a file can change the read-write status of that file.  If that's root, not your user, preface the command with 'sudo'. Learn about chmod and chown.

Permissions on files and directories, and their ownership, throughout the file system are there for a reason. Altering them may result in incorrect behavior.

---

### Post by HermanAB on 2016-01-02
Some kezamples:
$ cd wherever
$ sudo chmod +w directory
$ sudo chmod 755 directory 

and what you actually want to do:
$ sudo nautilus

BUT, it may be a good idea to ensure that your data is backed up before you start to play with Nautilus running as root.

---

### Post by idee on 2016-01-02
Thanks for the help.  One old tool that I used to use was to via Tools "Open Current Folder in Terminal", and then to use sudo to provide access.  When I try that I get the following errors.  It is the same in a terminal window.  I don't know why, but it does not accept either the current users' password, or that of the "admin" or the original installation user. 

```
dad@office:~$ sudo -i
[sudo] password for dad: 
dad is not in the sudoers file.  This incident will be reported.
dad@office:~$ sudo -i
[sudo] password for dad: 
Sorry, try again.
[sudo] password for dad: 

```

So, what am I doing wrong?

---

### Post by steeldriver on 2016-01-02
You can't mix-'n'-match usernames and passwords - if you want to use the sudo credentials of 'admin' you will need to actually log in as 'admin' first, either from the GUI session manager or by switching user in the terminal

```

su - admin
<enter admin's password>

sudo -i
<enter admin's password again>

```

---

### Post by idee on 2016-01-02
Thanks.  I was not trying to mix the passwords, but just showing that I tried both, but neither worked.  So just focusing on this user, "dad".  It's still not working.  Thoughts?

```
dad@office:~$ sudo - dad
[sudo] password for dad: 
dad is not in the sudoers file.  This incident will be reported.
dad@office:~$ 
```

---

### Post by steeldriver on 2016-01-02
It's telling you

```

dad is not in the sudoers file

```

(neither explicitly, nor by virtue of being a member of the sudo group): in other words, you can't get there from where you are

I'm not seeing anything in the extract you posted that shows you tried logging in as 'admin' **before **trying to execute 'sudo': you seem to be logged in as 'dad' each time

---

### Post by idee on 2016-01-02
As a little more information, my intent was to have two users for safety.  I have the installation user set up as admin.  Then I have a second user profile I set as a desktop user only (there are others in the family that also use this computer and I didn't want to chance an accident with admin privileges).  That one is "dad", in the "dad" group.  I am now trying to clean up some folders with privilege issues.  These are some data folders that I need to change ownership.  The easiest way I have done this in the past was via the file mgr.  Don't know what is mixed up.

> **steeldriver said:**
> It's telling you

```

dad is not in the sudoers file

```

(neither explicitly, nor by virtue of being a member of the sudo group): in other words, you can't get there from where you are

I'm not seeing anything in the extract you posted that shows you tried logging in as 'admin' **before **trying to execute 'sudo': you seem to be logged in as 'dad' each time

Correct, I am trying to get there using a su login from the desktop user.  Is that not possible in ubuntu?  I can use the admin password to adjust users and groups, and to install software.  I apologize, I am not trying to be difficult, just trying to get a grasp on a new system.  If what I am trying to do isn't possible, please let me know.  Is it possible or wise to place "dad" in sudoers list?

thanks

---

### Post by steeldriver on 2016-01-02
It should be possible - like I posted before:

> **steeldriver said:**
> 
```

**[COLOR=#0000ff]su -[/COLOR]** **admin**
<enter **admin**'s password>

sudo -i
<enter **admin**'s password again>

```

However that's not the same as either of these two things:

> **idee said:**
> 
```
[COLOR=#ff0000]**dad**[/COLOR]@office:~$ sudo -i
[sudo] password for [COLOR=#ff0000]**dad**[/COLOR]: 
dad is not in the sudoers file.  This incident will be reported.
[COLOR=#ff0000]**dad**[/COLOR]@office:~$ sudo -i
[sudo] password for [COLOR=#ff0000]**dad**[/COLOR]: 
Sorry, try again.
[sudo] password for [COLOR=#ff0000]**dad**[/COLOR]: 

```


and

> **idee said:**
> 
```
dad@office:~$ [COLOR=#ff0000][B]sudo - dad
[/B][/COLOR] [sudo] password for [COLOR=#ff0000]**dad**[/COLOR]: 
dad is not in the sudoers file.  This incident will be reported.
dad@office:~$ 
```

---

### Post by idee on 2016-01-03
strange twist from what I have been used to.  Thanks, finally got it.

Hope you have a great new year.

OK, another twist.  I have a partition that was set up as a hand-off area from the old data to the new OS.  It came across with ownership of root:plugdev.  It will not allow the chown command to bring these files back to the user dad:dad.  "Operation not permitted"

Q - Can I still access these files?  Is there any need to change them?
Q - Is there a reason for these locked down to root only?
Q- If there is no danger changing these old data files, what is the correct process to do so?

---

### Post by Herdo on 2016-01-03
[https://wiki.ubuntu.com/Security/Privileges#Access_external_storage_devices](https://wiki.ubuntu.com/Security/Privileges#Access_external_storage_devices)

Add the user to the group "plugdev".

```
[COLOR=#111111][FONT=Consolas]sudo adduser user group[/FONT][/COLOR]
```

So, ```
sudo adduser dad plugdev
```


The user will need to log out and log back in.

---

### Post by HermanAB on 2016-01-03
I think much confusion originated from the fact that 'su' and 'sudo' are different commands that operate quite differently.  The user 'dad' is not in the 'sudoers' file and therefore cannot use 'sudo' at all, but he can use 'su' to accomplish the same, if and only if user 'dad' happens to know the super user password.

---

### Post by Herdo on 2016-01-03
> **HermanAB said:**
> I think much confusion originated from the fact that 'su' and 'sudo' are different commands that operate quite differently.  The user 'dad' is not in the 'sudoers' file and therefore cannot use 'sudo' at all, but he can use 'su' to accomplish the same, if and only if user 'dad' happens to know the super user password.

+1

Good point.  idee, if you so wish you can add your father to the sudoers group as well the same way.

```
sudo adduser dad sudo
```

You would need to do that from the original administrator account or by executing the command as the root user.

```
su

adduser dad sudo
```

You have to enable the root account because it is disabled by default in Ubuntu.  You can enable it, but it's probably a better idea to just run the command while under the administrator user (the first user account created) using sudo.

---

### Post by DuckHook on 2016-01-03
> **siloam said:**
> Any filemanager can have a root access if it's opened with ' sudo'.Careful though. Technically true, but practically problematic and possibly a ticking time bomb. *sudo* was designed to be used for CLI tools. Graphical tools will yield wonky results if invoked with *sudo* alone. *gksudo* used to be the go-to method for invoking nautilus or gedit, but has since been deprecated in deference to *pkexec*. Unfortunately, *pkexec* does not come with policykit profiles for either *nautilus* or *gedit*. For better or worse, the Canonical powers-that-be have decided that root-level file administration s/b done in the CLI, or through special invocations like *sudo -H*. So, you can either invoke graphical apps using sudo -H (the -H flag is critically important), or use CLI apps as alternatives (which is actually cooler and geekier&#8213;for example, try out *mc* and *nano*), or perhaps the most "elegant" solution of all, create the missing *pkexec* policykit profiles for *nautilus* and *gedit*, instructions [here]("http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html").

---

### Post by Kari_Leppanen on 2016-01-03
You need to add user dad to sudoers file: ```
sudo visudo
```

Add a line with: dad    ALL=(ALL:ALL) ALL

Now you can use your own password (dad's) to have root access by using command sudo.

Kari

---

### Post by sandyd on 2016-01-03
> **Kari_Leppanen said:**
> You need to add user dad to sudoers file: ```
sudo visudo
```

Add a line with: dad    ALL=(ALL:ALL) ALL

Now you can use your own password (dad's) to have root access by using command sudo.

Kari

Please don't do this, the proper way is to add the user to the 'sudo' group for much easier management. I don't recommend touching the sudoers file unless necessary as any error or minor typo in the sudoers file will **stop** sudo from working, and thus require you to repair the sudoers file from recovery session or live media.

---

