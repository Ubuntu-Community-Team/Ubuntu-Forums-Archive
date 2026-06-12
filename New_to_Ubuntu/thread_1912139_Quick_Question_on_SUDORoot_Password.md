---
title: "Quick Question on SUDO/Root Password"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by indiana913 on 2012-01-20
I'm having a bit of a problem on shutting down my Ubuntu ( which is a totally different issue that I won't get into here).  On looking through the forums I found the "sudo shutdown -h now" command and I typed it into terminal and I found out it only works if I actually log out of my normal users account and log back in as root. Here is what my terminal screen says if I am on my normal users account.

crashbang@kenton-Aspire-5253:~$ sudo shutdown -h now
[sudo] password for crashbang: 
Sorry, try again.
[sudo] password for crashbang: 
crashbang is not in the sudoers file.  This incident will be reported.
crashbang@kenton-Aspire-5253:~$

I used my root password on the second line and my normal users password on the fourth line.  I tried more than once to check spelling.  While on my normal users account, my root password works just fine to use the Ubuntu Software Center and the Update Manager.  Why won't it work in the terminal?

---

### Post by sanderd17 on 2012-01-20
> **indiana913 said:**
> 
I used my root password on the second line and my normal users password on the fourth line.  I tried more than once to check spelling.  While on my normal users account, my root password works just fine to use the Ubuntu Software Center and the Update Manager.  Why won't it work in the terminal?

How did you get a root password? The root account is normally disabled so it doesn't have a password.

Can you try
```

su
shutdown -hP now

```

If this works, you'll need to do some reconfigurations in your sudoers file: [https://wiki.archlinux.org/index.php/Sudo#Configuration](https://wiki.archlinux.org/index.php/Sudo#Configuration)

---

### Post by Grenage on 2012-01-20
As above, the clue is in:

```
crashbang is not in the sudoers file. This incident will be reported.
```

The root password wouldn't work for for *sudo*, as it expects the current user's password; the user's password didn't work, because they are not in the sudoers file.

Have you changed anything?

---

### Post by lisati on 2012-01-20
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by indiana913 on 2012-01-20
Hey, thank you folks for your help.  I clearly have some study time ahead of me.

---

