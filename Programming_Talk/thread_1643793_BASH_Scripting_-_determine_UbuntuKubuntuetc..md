---
title: "BASH Scripting - determine Ubuntu|Kubuntu|etc."
date: 2010-12-12
forum: Programming Talk
---

### Post by HotShotDJ on 2010-12-12
I do hope this is the appropriate sub-forum for this question. Does there exist a bash command (or a file that I can grep) that will return a value that will allow me to determine if the user has Ubuntu, Kubuntu, Xubuntu, etc. running?  I want to use this for various case statements within a bash script. Right now, I'm using the following:
```
read -p "Version (Ubuntu/Kubuntu/Xubuntu/Lubuntu): "
case $REPLY in
```Since I'm going to be using my script for people who may not have a clue what the answer is (you know the type, they call you for help to reboot the Internet), I really want to limit the number of questions the script has to ask. Google and Forum searches have not yielded an answer.  Any help with this is greatly appreciated!

---

### Post by File_ on 2010-12-12
See 'uname -a' output.
Mine is: ```
Linux **** 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux
```

---

### Post by oldfred on 2010-12-12
And this:

fred@fred-DTgpt:~$ uname -a
Linux fred-DTgpt 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
fred@fred-DTgpt:~$ lsb_release -d
Description:    Ubuntu 10.04 LTS

---

### Post by luvshines on 2010-12-12
```

# Also may want to try this

cat /etc/issue
```

---

### Post by oldfred on 2010-12-12
Found one more in my notes:

fred@fred-LucidDT:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
fred@fred-LucidDT:~$

---

### Post by HotShotDJ on 2010-12-12
Thank you all for your responses!  Unfortunately, all the above commands return strings that contain "Ubuntu" on both my Ubuntu and Kubuntu box.  I need to be able to differentiate between the different *buntu's -- that is, if the script is running on an Ubuntu box, it will return "Ubuntu"; on a Kubuntu box, it will return "Kubuntu"; etc.

---

### Post by Vaphell on 2010-12-12
if you want to run it from GUI, you can look for DE specific processes in ps output (ie gnome-session). Also you can test for ubuntu/kubuntu-desktop packages with dpkg if they are installed. Not bulletproof but can be good enough.

---

