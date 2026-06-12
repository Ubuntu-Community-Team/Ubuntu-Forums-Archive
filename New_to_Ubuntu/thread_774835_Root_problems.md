---
title: "Root problems"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-04-29
I am having some trouble becoming the root user.  When I enter "su" in the command line, and enter the correct password, I get this:

```

xxx@xxx-laptop:~$ su
Password: 
su: Authentication failure
xxx@xxx-laptop:~$ 

```

If I try to install something with "sudo apt-get install ______", though, it installs without me entering my password.  I also don't get a prompt for the admin password when opening Synaptic, it just opens right up.

One other thing though is that I am trying to follow these instructions to mount a USB drive [http://www.novell.com/coolsolutions/feature/11637.html](http://www.novell.com/coolsolutions/feature/11637.html) , and when I get to the third or fourth step (I was trying to do this without doing the 'su' part at the beginning) I get this:

```

xxx@xxx-laptop:~/Desktop$ cp /etc/fstab /etc/fstab.bak
cp: cannot create regular file `/etc/fstab.bak': Permission denied

```

So I can't tell if it is an incorrect command or if it is because I am not logged in as root.  All the other things make me think that I am permanently logged in as root, though.  Which is it?  If I did log in as root permanently, how do I log out (I'd like to be prompted when doing sudo things and using synaptic)?

---

### Post by Zill on 2008-04-29
> **ConMan318 said:**
> I am having some trouble becoming the root user.  When I enter "su" in the command line...
Unlike some other Linux distros, Ubuntu does not have a separate root "user".  Instead, the primary user(s) can obtain admin rights **when required** by prefixing a command with "sudo".  If using Gnome then a graphical app will use the prefix gksudo.  This link should help clarify:
[URL="https://help.ubuntu.com/community/RootSudo"]
https://help.ubuntu.com/community/RootSudo[/URL]

---

### Post by scorp123 on 2008-04-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bilal.17 on 2008-04-29
> **Zill said:**
> Unlike some other Linux distros, Ubuntu does not have a separate root "user".  Instead, the primary user(s) can obtain admin rights **when required** by prefixing a command with "sudo".  If using Gnome then a graphical app will use the prefix gksudo.  This link should help clarify:
[URL="https://help.ubuntu.com/community/RootSudo"]
https://help.ubuntu.com/community/RootSudo[/URL]
also try su root, that works for me, so i dont have to keep putting sudo in front of everything

---

### Post by scorp123 on 2008-04-29
> **bilal.17 said:**
> su root, that works for me This only works if you enabled the "root" account which you are not supposed to do.

---

### Post by Barrucadu on 2008-04-29
If you want, you can enable the root account (and thus "su", "su - root", etc) by running "sudo passwd".
Despite all the warnings, enabling the root account was one of the first things I did and it is very useful.

---

### Post by ConMan318 on 2008-04-29
Thanks everyone, I didn't know it worked that differently in Ubuntu.

---

### Post by Tatty on 2008-04-29
> **bilal.17 said:**
> also try su root, that works for me, so i dont have to keep putting sudo in front of everything

There is a much better method of achieving persistant superuser powers which is mentioned in the RootSudo wiki entry above.

---

### Post by bilal.17 on 2008-04-29
> **Tatty said:**
> There is a much better method of achieving persistant superuser powers which is mentioned in the RootSudo wiki entry above.

ok thanks for the advice i'll try it out

---

