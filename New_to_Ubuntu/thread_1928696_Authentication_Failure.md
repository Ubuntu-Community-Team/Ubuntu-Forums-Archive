---
title: "Authentication Failure"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by benjie1 on 2012-02-20
In terminal window, I typed su - and then hit enter. It asks for password and I have typed it correctly, and I get authentication failure. I know the password is right because it allows me to get software for example How can I fix this problem? Thanks                        Bob

---

### Post by wildmanne39 on 2012-02-20
Hi, try sudo instead and see if that works.
Thanks

---

### Post by Cheesemill on 2012-02-20
The su command tries to log on as the root user. As the root user account is disabled in Ubuntu and doesn't have a password then it cannot succeed.

The preferred method with Ubuntu is to prefix any commands that need to be run as root with the sudo command (or gksudo for graphical applications).

---

### Post by e79 on 2012-02-20
The Ubuntu variant of 'su' (to gain full root shell) would be :

```
sudo -i
```But beware what you are doing in root mode and try not to mess up your system :D

In fact, you should always use 'sudo' in front of your commands as **Cheesemill** recommended :

For command line applications:
```
sudo *command*
```

For GUI applications:
```
gksu *program*
```

Regards

---

### Post by thirnick on 2012-02-21
try    sudo su

---

### Post by benjie1 on 2012-02-21
> **thirnick said:**
> try    sudo su

thanks. all those commands worked. Now I need to use one of them to install adobe flashplayer  (rpm). How can I do this from terminal window?  Can I still use yum after the sudo commands? Thanks.

---

### Post by roelforg on 2012-02-21
> **benjie1 said:**
> thanks. all those commands worked. Now I need to use one of them to install adobe flashplayer (rpm). How can I do this from terminal window? Can I still use yum after the sudo commands? Thanks.
 
Let me clarify.
 
Assuming you come from a Winslow background.
You know that in Winslow you have an Administrator account that is allowed to install stuff and modify configs/sys dirs, you also know that the normal useraccount can't do the afformentioned things.
Now, in linux you don't have an Administrator account, you have root (basicly the same thing, but even more powerfull as winslow prohibits anyone from making certain changes, linux doesn't when you're root).
Again, i'm trying to make a link between known and unknown.
In winslow you can right click on a file (as normal user) and select "Execute as Administrator", right?
In Linux sudo/su/gksudo do the same thing; (sudo/su for terminal progs, gksudo for graphical stuff).
But if you want a terminal that runs as if it's started by root, use sudo bash or sudo -i
Type exit to get back to your normal terminal.

---

### Post by Ms. Daisy on 2012-02-21
> **benjie1 said:**
> thanks. all those commands worked. Now I need to use one of them to install adobe flashplayer  (rpm). How can I do this from terminal window?  Can I still use yum after the sudo commands? Thanks.
What operation system are you running? :/  Fedora distros use yum. Debian distros (including Ubuntu) use [apt-get.]("https://help.ubuntu.com/community/AptGet/Howto") 

If you have installed Ubuntu 11.10 then I encourage you to read these:

[https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html](https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html)
[https://help.ubuntu.com/11.10/ubuntu-help/addremove.html](https://help.ubuntu.com/11.10/ubuntu-help/addremove.html)

---

### Post by roelforg on 2012-02-21
> **Ms. Daisy said:**
> What operation system are you running? :/  Fedora distros use yum. Debian distros (including Ubuntu) use [apt-get.]("https://help.ubuntu.com/community/AptGet/Howto") 

If you have installed Ubuntu 11.10 then I encourage you to read these:

[https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html](https://help.ubuntu.com/11.10/ubuntu-help/unity-introduction.html)
[https://help.ubuntu.com/11.10/ubuntu-help/addremove.html](https://help.ubuntu.com/11.10/ubuntu-help/addremove.html)

Whilst on the topic of where, i'd install gnash; but it's your choice.
Adobe Flash Player:
```

sudo apt-get install flashplugin-installer
sudo flashplugin-installer

```

---

