---
title: "Permission denied error!!"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by taekr on 2008-11-04
Hi

I found this link.. 

[http://forums.debian.net/viewtopic.php?t=31275&postdays=0&postorder=asc&start=0](http://forums.debian.net/viewtopic.php?t=31275&postdays=0&postorder=asc&start=0)

and.. followed the instruction. 

But when I do this, 


mark@mark-laptop:~$ echo 'CONCURRENCY=shell' >> /etc/default/rcS
bash: /etc/default/rcS: Permission denied
mark@mark-laptop:~$ sudo echo 'CONCURRENCY=shell' >> /etc/default/rcS
bash: /etc/default/rcS: Permission denied
mark@mark-laptop:~$ gksudo echo 'CONCURRENCY=shell' >> /etc/default/rcS
bash: /etc/default/rcS: Permission denied
mark@mark-laptop:~$ echo 'vm.swappiness=20' >> /etc/sysctl.conf
bash: /etc/sysctl.conf: Permission denied
mark@mark-laptop:~$ gksudo gedit /etc/default/rcs
mark@mark-laptop:~$ sudo echo 'vm.swappiness=20' >> /etc/sysctl.conf
bash: /etc/sysctl.conf: Permission denied



I got permission denied. Why is that? 

I used 'sudo' but still get denied. What is wrong?

---

### Post by thelinuxer on 2008-11-04
> **taekr said:**
> Hi

I found this link.. 

[t/rcS
bash: /etc/default/rcS: Permission denied
mark@mark-laptop:~$ sudo echo 'CONCURRENCY=shell' >> /etc/default/rcS
bash: /etc/default/rcS: Permission denied
mark@mark-laptop:~$ gksudo echo 'CONCURRENCY=shell' >> /etc/default/rcS
bash: /etc/default/rcS: Permission denied
mark@mark-laptop:~$ echo 'vm.swappiness=20' >> /etc/sysctl.conf
bash: /etc/sysctl.conf: Permission denied
mark@mark-laptop:~$ gksudo gedit /etc/default/rcs
mark@mark-laptop:~$ sudo echo 'vm.swappiness=20' >> /etc/sysctl.conf
bash: /etc/sysctl.conf: Permission deniedurl]http://forums.debian.net/viewtopic.php?t=31275&postdays=0&postorder=asc&start=0[/url]

and.. followed the instruction. 

But when I do this, 


mark@mark-laptop:~$ echo 'CONCURRENCY=shell' >> /etc/defaul



I got permission denied. Why is that? 

I used 'sudo' but still get denied. What is wrong?

My best guess is that you're not in the soduers file. Try changing to root first. The following command will change you to root ```
 su 
``` Then try the commands you were trying before. If this didn't work (and that will be really weird). Do ```
 ls -l /etc/default/rcS /etc/sysctl.conf
``` and give us the output.

---

### Post by taekr on 2008-11-04
> **thelinuxer said:**
> My best guess is that you're not in the soduers file. Try changing to root first. The following command will change you to root ```
 su 
``` Then try the commands you were trying before. If this didn't work (and that will be really weird). Do ```
 ls -l /etc/default/rcS /etc/sysctl.conf
``` and give us the output.

Wow... something weird is happening. 
I absolutely type the correct password but I'm getting the following error message... 


mark@mark-laptop:~$ su
Password: 
su: Authentication failure
mark@mark-laptop:~$ su
Password: 
su: Authentication failure
mark@mark-laptop:~$ su
Password: 
su: Authentication failure
mark@mark-laptop:~$ 
mark@mark-laptop:~$ 
mark@mark-laptop:~$ su
Password: 
su: Authentication failure
mark@mark-laptop:~$ 


Then, I tried 

sudo fdisk -l 

and put the password and..   it's working.. 

What's going on???

---

### Post by wizard10000 on 2008-11-04
> **taekr said:**
> ...What's going on???

What's going on is that root doesn't have permission to log on at the console - you can fix this by granting root permission to log on locally in System --> Administration --> Login Window

*at least that's where I think it is - I'm at the office on a Windows machine right now*

Good luck -

---

### Post by taurus on 2008-11-04
```
sudo echo 'CONCURRENCY=shell' >> **sudo** /etc/default/rcS
sudo echo 'vm.swappiness=20' >> **sudo** /etc/sysctl.conf
```

---

### Post by taekr on 2008-11-04
> **taurus said:**
> ```
sudo echo 'CONCURRENCY=shell' >> **sudo** /etc/default/rcS
sudo echo 'vm.swappiness=20' >> **sudo** /etc/sysctl.conf
```

it's working now. Thanks!!!

---

### Post by taekr on 2008-11-04
> **wizard10000 said:**
> What's going on is that root doesn't have permission to log on at the console - you can fix this by granting root permission to log on locally in System --> Administration --> Login Window

*at least that's where I think it is - I'm at the office on a Windows machine right now*

Good luck -

Thank you for the tip. I'm gonna try it.

---

