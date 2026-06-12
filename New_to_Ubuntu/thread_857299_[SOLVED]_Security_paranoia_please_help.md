---
title: "[SOLVED] Security paranoia please help"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Neo_The_User on 2008-07-12
OK If you go to System>Administration>Authorizations how do you use it? I want to take some of the security paranoia away because its constantly asking me to type in my password, unlock stuff, then if I want to edit files in my HDD that are critical or somewhat important like modify my menu.lst file or sources.list file and all this stuff unless I go all the way to the terminal, type in sudo nautilus, and edit my files that way. Any suggestions?

---

### Post by hyper_ch on 2008-07-12
you only have to enter the password if you want to accomplish system-wide changes... all changes that affect only your current logged in user is not required with a password entry.

---

### Post by Sef on 2008-07-12
> Foe those who use nVIDIA cards and when you update the kernel then you boot up in low graphics mode

That's why I just use the drivers in the repositories.

---

### Post by brian_p on 2008-07-12
> **Neo_The_User said:**
>  . . . I just can't take it anymore. 

Relief is a few keystrokes away:

```
man sudo
```

```
man sudoers
```

---

### Post by Neo_The_User on 2008-07-12
Thank you all so much! I will do those commands. That was a lot of stuff came up! Might take me awhile to read. :lolflag:

---

### Post by aysiu on 2008-07-12
It should be ```
gksudo nautilus
``` not *sudo nautilus*

Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Neo_The_User on 2008-07-12
> **aysiu said:**
> It should be ```
gksudo nautilus
``` not *sudo nautilus*

Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I got an error. Everything works fine though.

neo@neo-desktop:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:18599): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by Hendrixski on 2008-07-12
> **Neo_The_User said:**
> OK If you go to System>Administration>Authorizations how do you use it? I want to take some of the security paranoia away because its constantly asking me to type in my password, unlock stuff, then if I want to edit files in my HDD that are critical or somewhat important like modify my menu.lst file or sources.list file and all this stuff unless I go all the way to the terminal, type in sudo nautilus, TYPE IN MY PASSWORD, I just can't take it anymore. Is Authorizations what I am looking for and I just need help using it or is there some other thing I have to do? I want it not asking for my password 2 minutes when I want to do something. Any suggestions?

P.S. Foe those who use nVIDIA cards and when you update the kernel then you boot up in low graphics mode, takes 1 hour to get ubuntu to remember all your settings, install envy, restart, go to nvidia xserver screen settings or whatever and says you aren't root then you do su root in the terminal and still says you aren't root that bothers me. It only says you aren't root if your screen resolution is a bit higher than low. If any of you who have nVIDIA cards you know exactly what I am talking about. WHICH IS WHY I NOW USE ATI!!!!!

That's an easy one
just stop doing things that require administrative priviledges.  Don't edit system files, there's usually a GUI-based way to do things (even though it's usually not the first thing we think of when we tell people an answer here on the forums).

---

### Post by matthewbpt on 2008-07-12
there is a good reason why you can't log in as a root user, it vastly enhances the security of the system, and I recomend you DONT try and log in as root, the sudo way of doing things i think is a very good way of doing things. read more here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by brian_p on 2008-07-12
> **matthewbpt said:**
> there is a good reason why you can't log in as a root user, it vastly enhances the security of the system, and I recomend you DONT try and log in as root, the sudo way of doing things i think is a very good way of doing things. read more here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I do not think Neo_The_User wants to log in as root though he might want to read the last part of of the page you gave a link for.

---

### Post by Neo_The_User on 2008-10-30
Logging in as root from the login screen solved all my problems.

System > Administration > Login window > Security > Allow local system administrator login. That really helped me. Now I never have to type my md5 hashed password all the time.

---

