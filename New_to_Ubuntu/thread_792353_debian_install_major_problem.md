---
title: "debian install major problem"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by david0075 on 2008-05-12
i have recently installed ubuntu 8.06 on a laptop. i am using a different computer at the moment. 

when i try to open synaptic package manager or software sources the program shows at the bottom as "starting administrati..." and then closes with no noticeable effects.

i have tried installing a deb package, synergy v2.0, using "sudo dpkg /home/programs/synergy_1.3.1-2ubuntu1_i386.deb" i have checked that the filename is correct. i have tried using -i at the front, as suggested by a help page i viewed. i have tried with or without sudo at the front, and with --force all, or --force depends, and all the time it comes back with "unable to resolve host computername" where computername is the name i chose for my computer to be

---

### Post by Monicker on 2008-05-12
The "unable to resolve host" message is probably due to a known bug.

Look here for info on how to fix that:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by bjschuma on 2008-05-12
I think you can install a .deb by double clicking it.

If you use "sudo apt-get install synergy" you should be able to download/install it from the repositories.

---

### Post by inportb on 2008-05-12
> **david0075 said:**
> i have tried installing a deb package, synergy v2.0, using "sudo dpkg /home/programs/synergy_1.3.1-2ubuntu1_i386.deb" i have checked that the filename is correct. i have tried using -i at the front, as suggested by a help page i viewed. i have tried with or without sudo at the front, and with --force all, or --force depends, and all the time it comes back with "unable to resolve host computername" where computername is the name i chose for my computer to be

Um, the -i does not belong at the front; it should be after the dpkg.

---

### Post by david0075 on 2008-05-13
> **inportb said:**
> Um, the -i does not belong at the front; it should be after the dpkg.

thanks, i tried it like that, but i wrote it wrong, 




> **Monicker said:**
> The "unable to resolve host" message is probably due to a known bug.

Look here for info on how to fix that:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

darn,
i went to the page, and went to the workaround thread. it said to type gksudo gedit /ect/hosts into terminal. i did that and there was a window showing in the bottom taskbar titled 'Starting administrative program", which closed in the same way as i said the package manager closed, in my original post.

i opened it through file browser, and the only thing i noticed different, was the second line was recommended to be '127.0.1.1 icarus-laptop' while mine is '127.0.1.1 sony.ubuntu'

im guessing i have a problem with being recognised as administrator. i doubt this bug is the problem, as others have reported that the bug fix worked for them, but i cant even try it.

---

### Post by Monicker on 2008-05-13
> **david0075 said:**
> 
im guessing i have a problem with being recognised as administrator. i doubt this bug is the problem, as others have reported that the bug fix worked for them, but i cant even try it.

Actually, that thread mentions several different ways to fix the problem.

Run these commands:

```
hostname
cat /etc/hosts
```

If the output of the first command does not match the entry for 127.0.1.1 in /etc/hosts, then you are definitely affected by that bug.

---

### Post by david0075 on 2008-05-13
> **Monicker said:**
> Actually, that thread mentions several different ways to fix the problem.

Run these commands:

```
hostname
cat /etc/hosts
```

If the output of the first command does not match the entry for 127.0.1.1 in /etc/hosts, then you are definitely affected by that bug.


ok, so hostname is sony, and second line of /etc/hosts is 127.0.1.1 sony.ubuntu

so i guess i have to remove the '.ubuntu' bit

but the file is protected, and gksudo gedit /etc/hosts doesnt work. so what do i do to change the file

i looked at changing the permissions of the file, but it says im not the owner so **** off. can i log in as owner, and perhaps will this fix my problem of not being able to open package manager and other admin stuffs?

---

### Post by david0075 on 2008-05-13
ok, i have answered my question about loging in as owner (root) and found out how to do it (i cant because 'login window' is an administrative program, and those arent running for me at the moment)

i still need to get access to change my /etc/hosts file
cant do it by running nautilus as gksudo
cant do it by running text editor as sudo
cant do it by copying a file called 'hosts' from another file to /ect/

any help would be really helpful

---

### Post by Monicker on 2008-05-13
Boot into Recovery Mode from the boot menu, as also mentioned in thread for fixing this issue.  After selecting Recovery Mode, you will have an option to go to a root shell.  Once you are in the root shell you will be able to edit /etc/hosts.
```

nano /etc/hosts
```

---

### Post by BDNiner on 2008-05-13
Are you able to go to System>Administration>Network? you can change your hostname there also. I ran into a similar issue where i could not run any commands as sudo because my hostname was wrong.

---

