---
title: "How Do I Determine What Operating System I Have?"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by TomBrooklyn on 2013-08-21
How can I determine which version of Ubuntu I have on a computer?

---

### Post by howefield on 2013-08-21
Try the terminal command..

```
cat /etc/lsb-release
```

---

### Post by Frogs Hair on 2013-08-21
See the link. [https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by vasa1 on 2013-08-21
Just today, I came across `cat /etc/issue` which gives me "Ubuntu 13.04 \n \l" even though I'm on Lubuntu 13.04.

Then there's `env | grep XDG_CURRENT_DESKTOP` and `XDG_CURRENT_DESKTOP` and `echo $DESKTOP_SESSION`.

---

### Post by ajgreeny on 2013-08-21
I use an alias in my ~/.bash_aliases file ```
alias version='lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -a'
```then the command I type is **version** to get output like
```
Description:    Ubuntu 12.04.3 LTS
Codename:    precise
Desktop:    xubuntu
Linux Xubuntu 3.5.0-37-generic #58~precise1-Ubuntu SMP Wed Jul 10 17:48:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
Tells me all I need to know!

---

### Post by texaswriter on 2013-08-22
I use Kubuntu and this is what I get:

```
user@computer:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
user@computer:~$ 
```

---

### Post by 3rdalbum on 2013-08-23
Kubuntu and Lubuntu are the same as Ubuntu, but with a different package set. So what you're all reporting is perfectly normal.

/etc/lsb-release is used by several programs to check what distribution is running, so they can do things the correct way for that distribution. Changing that to something different would confuse programs into doing things the wrong way, or would prompt the user to select their distribution whenever the program starts.

---

