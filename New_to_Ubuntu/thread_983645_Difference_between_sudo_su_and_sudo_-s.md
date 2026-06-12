---
title: "Difference between sudo su and sudo -s"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by ItecKid on 2008-11-15
Hello,

I am curious as to what the difference between sudo su and sudo -s are.  As far as I can tell, they both make you root.

Thanks.

---

### Post by overdrank on 2008-11-15
> **ItecKid said:**
> Hello,

I am curious as to what the difference between sudo su and sudo -s are.  As far as I can tell, they both make you root.

Thanks.

Hi and according to the link
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
They are equivalent.

---

### Post by lovinglinux on 2008-11-15
According to "man sudo"

```
-s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).
```

---

### Post by unutbu on 2008-11-15
I did the following experiment:
```

applic@ion:~% sudo su
[sudo] password for applic:
root@ion:/home/applic# env > /tmp/sudo_su_env
root@ion:/home/applic# exit
exit
applic@ion:~% sudo -s
applic .bashrc read...
root@ion:~% env >/tmp/sudo_s
```

Here are the differences I found:
[list]
[*]"sudo -s" 
HOME=/home/applic
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
reads $USER's ~/.bashrc

[*]"sudo su"
HOME=/root
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
reads /etc/environment
reads /root/.bashrc
[/list]

Notice the difference in $HOME. Being root and having $HOME set to the normal user's home can cause problems. For example, if you run a graphical app, the normal user's ~/.Xauthority can get overwritten by root. This causes the normal user problems later on such as not being able to run certain graphical apps through cron.

Here is a summary:
```

				                     corrupted by user's 
		HOME=/root	uses root's PATH     env vars
sudo -i		Y		Y[2]                 N
sudo -s		N		Y[2]                 Y
sudo bash	N		Y[2]                 Y
sudo su		Y		N[1]                 Y


[1] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
    probably set by /etc/environment
[2] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

```

The bottom line, is "sudo -i" is the proper command to run when you want a root shell that is untainted by the user's environment.

---

### Post by bodhi.zazen on 2008-11-15
+1 for sudo -i 

While all these variations give you root access the differences are in the environmental variables as demonstrated by unutbu

If you really really want to know the technical details, you will need to read the man pages for su and sudo (because most of us would need to do just that to give you a better answer).

---

### Post by infoseeker on 2009-06-03
I noticed a problem the other day when using 'sudo -s' in that, as an example, when using 'mc' at the prompt, the resulting change in the mc's configuration file (in 'home/user/.mc') is owned by root, and not the user, and needs to be changed back to that of the user if further configuration changes are required when 'mc' is used as 'user'.

Using 'sudo -i' and then 'mc' uses the configuration file in '/root/.mc'.

---

### Post by theDaveTheRave on 2009-12-23
I just had a question related to this from my boss.

The quick easy answer was

Don't do < sudo su > or < sudo -i > to get a "true" root login. It open up your system to potential harm, and may cause viruses, trojan's etc to infect all the windows systems in the network. If you insist on using it, sit in front of the terminal, and pull the network cable out of the wall!

OK, this may not be particularly true, but it got the desired response of

> 
Ah OK

Thanks


so our server should be safe for a few months... when hopefully my boss will remember there was a reason he doesn't use this option.

Personally I've never used the option... and I can quite happily break my system without it :lolflag: 

David

---

### Post by jimingkui on 2009-12-23
Great! unutbu tells what exactly I want to know!

---

### Post by ashlynne on 2010-12-27
> **unutbu said:**
> 
Here is a summary:
```

				                     corrupted by user's 
		HOME=/root	uses root's PATH     env vars
sudo -i		Y		Y[2]                 N
sudo -s		N		Y[2]                 Y
sudo bash	N		Y[2]                 Y
sudo su		Y		N[1]                 Y


[1] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
    probably set by /etc/environment
[2] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

```

The bottom line, is "sudo -i" is the proper command to run when you want a root shell that is untainted by the user's environment.

Hello there, this is my first post!

On my machine, doing [FONT="Courier New"]sudo -i[/FONT] does not result in PATH being set to that of root's.

```
ceyi@ceyi:~$ sudo -i
root@ceyi:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Can anyone tell me why? What can I do to have it use root's PATH when I [FONT="Courier New"]sudo -i[/FONT]?

---

### Post by @nne on 2011-03-08
Hello there!

I hope people are around and willing to help me understand. This is what I get when I use "sudo -i", "sudo -s" and "sudo su" :

[HTML]
anne@anne-MaverickMeerkat:~$ sudo -i
[sudo] password for anne: 
root@anne-MaverickMeerkat:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
root@anne-MaverickMeerkat:~# exit
logout
anne@anne-MaverickMeerkat:~$ sudo -s
root@anne-MaverickMeerkat:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@anne-MaverickMeerkat:~# exit
exit
anne@anne-MaverickMeerkat:~$ sudo su
root@anne-MaverickMeerkat:/home/anne# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
root@anne-MaverickMeerkat:/home/anne# exit
exit
anne@anne-MaverickMeerkat:~$
[/HTML]According to these results, I guess I should use "sudo -s" if I want to do a full backup of my system, for example, as described here : [https://help.ubuntu.com/community/BackupYourSystem/TAR#Backing%20Up]("https://help.ubuntu.com/community/BackupYourSystem/TAR#Backing%20Up"). 

Has anyone any idea why there is a difference between my results and that of unutbu's? Or is it merely because I'm under 10.10?

---

