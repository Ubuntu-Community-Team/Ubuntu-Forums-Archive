---
title: "The terms root and kernel confuse me..."
date: 2011-09-21
forum: New to Ubuntu
---

### Post by nksjolinder on 2011-09-21
Hey guys,

Just wondering what exactly a root user or root is? I have been able to collect that it is a user that has access to system files possibly? What exactly is it used for and so on? Same question about kernel? what exactly is it and what kind of practical things would you do with it or do most people just leave it alone? 

Nick

---

### Post by mikewhatever on 2011-09-21
Root user -> [https://secure.wikimedia.org/wikipedia/en/wiki/Superuser](https://secure.wikimedia.org/wikipedia/en/wiki/Superuser)

Linux kernel -> [https://secure.wikimedia.org/wikipedia/en/wiki/Linux_kernel](https://secure.wikimedia.org/wikipedia/en/wiki/Linux_kernel)

PS: Google is your friend.;)

---

### Post by nksjolinder on 2011-09-21
thank you thank you. i shall use my head next time :P

---

### Post by haqking on 2011-09-21
The **kernel** is just that it is the core from which everything is an addon which adorns it, it is the centre or core, or brain of the OS, then certain companies take that seed if you like and nurture it with there own add ons to make it there own, linux is the **kernel** and everything else is distro fluff.

**Root** is the **root** of the filesystem, the very start of it from which everything else branches off, it is the beginning or **root** of the system.

**Root** is also the omnipotent, omniscient, hopefully not omnipresent user with all power (hopefully not omnipresent cos it is locked by default in Ubuntu and you should use sudo ;-).
It is the superuser who can do anything to the system including to the kernel

---

### Post by nksjolinder on 2011-09-21
> **haqking said:**
> 
**Root** is the **root** of the filesystem, the very start of it from which everything else branches off, it is the beginning or **root** of the system.

What do you mean by the root of the file system? when i hear "the start  of the file system" i think home directory as that is where i branch  from to find other files

Also, what exactly is sudo? I know i use it in some commands that i type but am not sure what it is...

---

### Post by oldos2er on 2011-09-21
/home is a folder in root, root (folder) itself is /

There's also /root, which is the admin user's (AKA the "root" user) home folder.

'sudo' means *super user do*, it's a way for a normal user to temporarily elevate themselves to admin. More info at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and ```
man sudo
```

Because the term "root" can refer to two different things, the start of the file system and the administrator account, it does get confusing.

---

### Post by haqking on 2011-09-21
> **nksjolinder said:**
> What do you mean by the root of the file system? when i hear "the start  of the file system" i think home directory as that is where i branch  from to find other files

Also, what exactly is sudo? I know i use it in some commands that i type but am not sure what it is...

root as in root, like in a tree, it is the starting point from which anything else springs from in the filesystem.

Your /home is a branch from root, there may be other branches in the /home which would be other users.
/ is root /home /etc /usr /var /tmp are all branches which spring from the root /

as for sudo then read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

edit: ninja'd from above by oldos2er ;-)

---

### Post by kaldor on 2011-09-21
> **nksjolinder said:**
> What do you mean by the root of the file system? when i hear "the start  of the file system" i think home directory as that is where i branch  from to find other files

Also, what exactly is sudo? I know i use it in some commands that i type but am not sure what it is...

The root of the file system means the root directory. In Linux system, that would be */*. In Windows, it would be *C:\*. 

The "root directory" is not the same as "Root user". The root directory means the original directory where *everything* branches out from- think of the roots of a tree. 

The user "root" is the user that can do *anything* to the system without question or warning. Due to obvious security reasons with this, *sudo* is recommended for normal users such as your own. *sudo* stands for "superuser do" and will let anyone in the "sudoer's" file (run command *sudo visudo* to see) enter a password to perform a command as the root user.

Examples...

[LIST]
[*]You can access the / directory. Inside /, you can find /home, /usr, /var, etc.

[*]You can log in as the *root* user.

[*]You can run the command *sudo apt-get update* to allow yourself to run *apt-get update* without needing to log in as *root*; you are elevating your permissions to allow it to happen.
[/LIST]

Hope this clears it up :)

Edit: Ninja'd by two people. I shouldn't have grabbed a drink while posting this.

---

### Post by nksjolinder on 2011-09-21
Thank you for all the informative posts! Responding to all your definitions of sudo, are there set commands that require using sudo? for example, to install some tar files i ran sudo make. If i did not run that as sudo would it have been denied? if not, are there any commands that do require sudo in order to be allowed by the user?

---

### Post by nothingspecial on 2011-09-21
> **nksjolinder said:**
> Thank you for all the informative posts! Responding to all your definitions of sudo, are there set commands that require using sudo? for example, to install some tar files i ran sudo make. If i did not run that as sudo would it have been denied? if not, are there any commands that do require sudo in order to be allowed by the user?

There are many commands that require sudo.

You don't usually need to run make with sudo, not if the source code is in your $HOME directory anyway.

---

### Post by haqking on 2011-09-21
> **nksjolinder said:**
> Thank you for all the informative posts! Responding to all your definitions of sudo, are there set commands that require using sudo? for example, to install some tar files i ran sudo make. If i did not run that as sudo would it have been denied? if not, are there any commands that do require sudo in order to be allowed by the user?

anything that requires elevated privelege requires sudo...how do you know ? well if you try to do something and it says permission denied or this should be run as sudo...then you run it again using sudo ;-)....as long as you think you should be doing so and not just doing it blindly.

There are lots of things that require elevated privelege, usually system based.  Anything else is on a per situation basis, try to limit running anything that requires root privelege, especially anything you download from a untrusted source.

---

### Post by nksjolinder on 2011-09-21
> **nothingspecial said:**
> There are many commands that require sudo.

You don't usually need to run make with sudo, not if the source code is in your $HOME directory anyway.

Thank you, I am beginning to put the pieces together...And thank you haqking once again! I am loving the infinite knoledge i am finding on these forums :)

---

### Post by decoherence on 2011-09-21
Good question. Here's the long answer.

In general, sudo is used to modify files (or run commands that modify files) that are owned by root or some other system-level user.

Using the terminal, if you type 'ls -l' from your home directory you'll get a list of files, one per line. On each line you should see your username twice. The second occurrence is actually a group name that ubuntu automatically creates for you. The first occurrence of your username indicates that you are the owner of the file (also known as the file's user) and the second occurrence indicates the file belongs to your group. They don't have to be the same but they often are in ubuntu.

If you go to most system levels directories ('cd /usr' for instance) and run the same command, you'll find the files are owned by the root user and the root group, or perhaps another system-level user like 'daemon' which is an account made strictly for the purpose of running certain background services. You would need to use sudo to modify any of these files. In general, you can read them but not change them. Look but no touch, so to speak.

Looking again at the output from 'ls -l' (doesn't matter for what directory) you can see on the far left some combination of dashes, "r's"  "w's" and "x's", for example -rwxrw-r--

I'll try to explain the format then give an example... otherwise this reply will go on even longer!

r -- permission to read the file
w -- permission to write the file
x -- permission to execute the file (if it's a program)
'-' -- no permission

U -- user
G -- group
O -- other

The way to read the line is

-UUUGGGOOO (that first dash indicates the type of file or special flags. A directory would have 'd' instead of a dash)

An example

```
-rw-rw-r--  1 decoherence decoherence 167329792 2011-09-15 11:45 testfile
```

so here I have a file i named 'testfile' and you can see that the user and group are 'decoherence'. The first 'rw-' says that I can read or write to the file but not execute it (i could make it executable but it isn't a program or directory so it'd be pointless.) The second 'rw-' says that anyone belonging to the group 'decoherence' can also read and write the file. This is a bit meaningless since I'm the only user in the group but it's more useful in other parts of the system. The third 'r--' means that everybody else can read it, but not write or execute it.

Here is an example of a directory

```
drwxr-xr-x  3 decoherence decoherence      4096 2011-07-25 13:25 Pictures
```

You can see that the first dash changed to a 'd' indicating that this is a directory. You can also see that the user, group and all other users can read or execute this directory (all directories must be executable) but can't write anything in it -- that is to say, anyone can view the contents this directory but only the owning user can save anything in it... unless they used 'sudo' to make themselves the superuser, then they can do anything.

Sorry for the long reply but it's necessary to have a basic understanding of file permissions in order to understand when and why you have to use sudo. I suppose I could've given you the short version which would be "if you're doing anything which writes files outside of your home directory, you probably need sudo" but that's a cop out ;)

---

### Post by nksjolinder on 2011-09-21
Thank you for the detailed reply, It is a very useful bit of info!

---

