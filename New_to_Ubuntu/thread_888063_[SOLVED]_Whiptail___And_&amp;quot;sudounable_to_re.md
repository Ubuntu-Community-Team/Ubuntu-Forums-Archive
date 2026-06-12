---
title: "[SOLVED] Whiptail?   And &amp;quot;sudo:unable to resolve host&amp;quot;"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by GrnFrag on 2008-08-12
2 q's.     First, i have a process called whiptail that i'm not sure where came from.   it's part of a package in Synaptec, but it appears to be running very hard.   between 50 and 90% of cpu, all the time.   doesn't lag the system really, but the monitors display the use.    
What the heck is it?  How did i break it?   Or Can i delete the package?


Second.   every time i sudo or gksu, i get a message
"sudo: unable to resolve host MYCOMPUTERNAME"

I know i did this one, used samba to create whatever i've done, but i have no clue what or how to fix it. I made no changes to samba, used it only through the gui.  i'm not so worried about security, i'm on a private lan, locked up tight.   i uninstalled/reinstalled samba with apt-get autoclean and autoremove in between, but i still got the error, even without samba installed.

Edit-   Issue 1 is resolved.  whiptail is a logging ap, high cpu was from a broken program whining into some weird terminal void that whiptail caught.  whiptail will diplay some of the output when hovered over in sysmon, but you have to be displaying "all process" under view menu

---

### Post by Java Geek on 2008-08-12
I have had a similar problem (I think) The problem was that the groups were changed and root did not own the right file. If root owns /root, I think you are in good shape

---

### Post by cariboo on 2008-08-12
A little seaarching in Google and I came up with this:

> Whiptail is a "dialog" replacement using newt instead of ncurses. It provides a method of displaying several different types of dialog boxes from shell scripts. This allows a developer of a script to interact with the user in a much friendlier manner. 

As far as:

"sudo: unable to resolve host MYCOMPUTERNAME"

Check /etc/hosts, it should look like this:

```
127.0.0.1	localhost
127.0.1.1	intrepid
192.168.1.201	willy
192.168.1.1	router
192.168.1.202	minibuntu
```

Note 127.0.1.1 your hostname should be here. If you don't know what your hostname is, in a terminal type:

```
hostname -a
```

Jim

---

### Post by GrnFrag on 2008-08-12
that worked.   somehow i appeared to have added sort of a domain name to the end of my computer name.  

Tho now that i think about it, i did add a workgroup name to samba.   
Thanks for your help

---

### Post by MatthewPlanchard on 2008-08-13
Thanks. I was having the sudo: unable to resolve host for the same reason...

Samba had added a domain name to the end of my host.

---

### Post by vasiauvi on 2008-08-30
I have the same problem, but I can't save the file "hosts" after I modify from "127.0.1.1 name_of_PC.domain_name" to "127.0.1.1 name_of_PC". It say that I don't have permision to save the file!!It's an other way to save the file??

---

### Post by Too Late on 2008-08-30
> **vasiauvi said:**
> I have the same problem, but I can't save the file "hosts" after I modify from "127.0.1.1 name_of_PC.domain_name" to "127.0.1.1 name_of_PC". It say that I don't have permision to save the file!!It's an other way to save the file??
You have to edit it with root/sudo permissions. Go to terminal and type:
```
gksudo gedit /etc/hosts
```
Replace gedit with the corresponding text editor, if you use another one.

edit: sudo -> gksudo

---

### Post by caljohnsmith on 2008-08-30
> **vasiauvi said:**
> I have the same problem, but I can't save the file "hosts" after I modify from "127.0.1.1 name_of_PC.domain_name" to "127.0.1.1 name_of_PC". It say that I don't have permision to save the file!!It's an other way to save the file??
If you can boot into recovery mode, which will make you the "root" user, you can modify that file with:
```
nano /etc/hosts
```
Or if you can't do that, you can boot your Live CD, open a terminal, and do:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition as /dev/sdX, and then:
```
sudo mount /dev/sdX /mnt
gksudo gedit /mnt/etc/hosts &
```
Save changes, quit, reboot, and you should be all set. Let me know if you need any more details or info.

---

### Post by Anilda on 2011-10-28
> **cariboo907 said:**
> A little seaarching in Google and I came up with this:



As far as:

"sudo: unable to resolve host MYCOMPUTERNAME"

Check /etc/hosts, it should look like this:

```
127.0.0.1	localhost
127.0.1.1	intrepid
192.168.1.201	willy
192.168.1.1	router
192.168.1.202	minibuntu
```

Note 127.0.1.1 your hostname should be here. If you don't know what your hostname is, in a terminal type:

```
hostname -a
```

Jim


Hello i am new to form and i loved it!
 i tried this and found
127.0.0.1	localhost
127.0.1.1	anil-google

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

but for hostname -a 
i found
anil@google:~$ hostname -a
hostname: Name or service not known

---

### Post by oldos2er on 2011-10-28
Closed for necromancy. Please start a new thread for your question or problem.

---

