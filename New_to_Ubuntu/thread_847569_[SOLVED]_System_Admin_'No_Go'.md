---
title: "[SOLVED] System Admin 'No Go'"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by WilhelmGGW on 2008-07-02
When I click on System and Administration, then on almost all the items in the drop-down list -- like Synaptic Package Manager -- a turning circle appears at my cursor point on the desktop.  It turns and turns with nothing happening for a few moments, then it reverts to the arrow and the "starting administra.." box at the bottom of my window disappears.  That is, like the system tries to initiate the program, then gives up.

Please help.  How can I fix this?

---

### Post by ibutho on 2008-07-02
To debug the problem, try running the applications from a terminal e.g. Applications -> Accessories -> Terminal
```
sudo synaptic
```
If there are any problems, error messages will be shown in the terminal. Post these messages back.

---

### Post by drs305 on 2008-07-02
Also check your /etc/hosts file for a corrupted hostname.

```
cat /etc/hosts

```
 
Your hostname (computername) should not have any additional tags preceeded by a period. Example: correct = mycomputer     incorrect = mycomputer.zdckdkll

---

### Post by WilhelmGGW on 2008-07-02
gary@dell-desktop:~$ sudo synaptic
sudo: unable to resolve host dell-desktop
gary@dell-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 dell-desktop.example.com dell-desktop.LinuxUbuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by ibutho on 2008-07-02
Change
```
127.0.1.1 dell-desktop.example.com dell-desktop.LinuxUbuntu
```
to
```
127.0.1.1 dell-desktop.example.com dell-desktop
```
You may need to restart your networking services or reboot.

---

### Post by WilhelmGGW on 2008-07-02
I'm sorry for being yet so unschooled in these things. But how do I change code like you suggest?

---

### Post by sisco311 on 2008-07-02
use:
```
gksu gedit /etc/hosts
```to edit the file

---

### Post by WilhelmGGW on 2008-07-02
> **sisco311 said:**
> use:
```
gksu gedit /etc/hosts
```to edit the file

OK. I still need help.
I go to terminal mode and it give me this:
     gary@dell-desktop:~$ 

Exactly what do I enter on successive lines,
and how to I close the dialog to save the edit?

I'm sorry I'm so ignorant of what some of you know so much about.

---

### Post by drs305 on 2008-07-02
> **WilhelmGGW said:**
> OK. I still need help.
I go to terminal mode and it give me this:
     gary@dell-desktop:~$ 

Exactly what do I enter on successive lines,
and how to I close the dialog to save the edit?

I'm sorry I'm so ignorant of what some of you know so much about.

In a terminal type this. It will open a file called *hosts* with a text editor called *gedit*.

**gksudo gedit /etc/hosts**

You will see this:
```

127.0.0.1 localhost
**127.0.1.1 dell-desktop.example.com dell-desktop.LinuxUbuntu**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Change it to look like below. You are removing the last part of the second line:
```
127.0.0.1 localhost
**127.0.1.1 dell-desktop.example.com dell-desktop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Then at the top of gedit, File, Save. Close the gedit program. 
Reboot your system and see if your problem is solved.

---

### Post by WilhelmGGW on 2008-07-02
Thanks so much. I did just as you clearly said, but when I went to save it, I got the following message:

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

How do I get permission to save this?

---

### Post by drs305 on 2008-07-02
I hadn't read the first posts since this afternoon and forgot you couldn't use sudo. Sorry.

You will have to boot to the recovery mode via the grub menu and then do the steps in the previous post. If you still can't save the file from there, we will have to use the livecd.

ADDED: 
From the root terminal, you will have to use a text editor called *nano*. So the command to edit the file will now be:
**nano /etc/hosts**

Make the changes above. To save it is different. In nano, to save the file you will type "CTRL-O",  to write the changes, then ENTER, and finally "CTRL-X" to exit. If it saves the file, reboot.

If it still doesn't allow you to save the file we will have to do it from the liveCD. That will require more instructions so let me know if this works first.

---

### Post by rburkartjo on 2008-07-03
wil, try this open terminal type sudo (space)-i
will prompt for your password, enter it,note it will not show your password when you enter. then follow the steps as other have mentioned.should work/cheesemaker

---

### Post by WilhelmGGW on 2008-07-03
Thanks for all the help, folks.
A special thanks to drs305 -- for all the help here and offline.

This was my first really major issue with my new computer that came from Dell with Ubuntu already loaded.  You have made me very pleased with the helpfulness of this community.

---

