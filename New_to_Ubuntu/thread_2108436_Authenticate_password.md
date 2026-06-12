---
title: "Authenticate password?"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by moparfreak426 on 2013-01-24
I keep putting in my username password and i guess that isnt it. What is the password?

---

### Post by The Cog on 2013-01-24
What is asking for a password?

Generally, in Ubuntu, if you are asked for a password then it will be your user login password. There are no other passwords.

If you are trying to become root, don't use **su** because the root account doesn't have a password - use the command ```
sudo -i
``` instead. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by moparfreak426 on 2013-01-24
Its not working...  My password doesnt do it...  But im trying to install updates, install programs from ubuntu software center....  All have to authenticate.  I type my user password and then...  Nothing...  And root i just learned about....  Its like android? Jk...  Idk. Ill need to look what i can do with root in ubuntu before i start trying that and ive tried typing passwd in terminal and it doesnt enter anything except enter key....  Then says....  Oh cant post screenshots from home. There needs an ubuntu android app or ability to use Tapatalk

---

### Post by Warren Hill on 2013-01-24
What is asking for a password?



The first user created is an administrator and in the "sudo" group.  All other users are not by default and need to made members of this group to be made able to administer the system.


To check if you are an administrator enter this command in a terminal
```
id
```on my system I see this
```
$ id
uid=1000(warren) gid=1000(warren) groups=1000(warren),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare),125(wireshark)

```If you see sudo you are a member of administrators group and your password should work.  If not it wont let us know what you see and we can advise how to become an administrator.

Assuming you are already you could try resetting your password using any of the following methods

 [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
 
[https://help.ubuntu.com/12.04/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/12.04/ubuntu-help/user-forgottenpassword.html)
 
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)
 [URL="http://naveenubuntu.blogspot.co.uk/2012/05/recover-login-password-of-ubuntu-1204.html"]
[/URL]

---

### Post by moparfreak426 on 2013-01-24
[ATTACH][/ATTACH]here is screenshot of that

---

### Post by matt_symes on 2013-01-24
Hi

Assuming it's the (gksudo/gksu) graphical prompt that is not accepting your password and you are sure it's correct then this may be off the mark but worth checking.

Run ```
gksu-properties
``` and check the authentication method is set to sudo.

Kind regards

---

### Post by moparfreak426 on 2013-01-24
> **matt_symes said:**
> Hi

Assuming it's the (gksudo/gksu) graphical prompt that is not accepting your password and you are sure it's correct then this may be off the mark but worth checking.

Run ```
gksu-properties
``` and check the authentication method is set to sudo.

Kind regards
is set to sudo

---

### Post by matt_symes on 2013-01-24
Hi

You edited your post after i posted :) So the problem is not gksudo then.

Is your root partition mounted read only ?

Open a terminal and type

```
cat /proc/mounts 
```

Post the output back here by copying and pasting from the terminal (select text -> right click->copy) into your next post. 

Please post between code tags.

Can you also post the out of (from the terminal)

```
ls -l /etc/shadow
```

That is a small L after ls.

Kind regards

---

### Post by Warren Hill on 2013-01-25
Take a look here
[http://www.linuxquestions.org/questions/linux-newbie-8/passwd-authentication-token-manipulation-error-236955/](http://www.linuxquestions.org/questions/linux-newbie-8/passwd-authentication-token-manipulation-error-236955/)

similar problem solved -- may apply to you

---

### Post by fdrake on 2013-02-27
to reset a users' password follow this tutorial:
[http://theguyonthe3rdfloor.wordpress.com/2013/02/27/ubuntu-lost-password/](http://theguyonthe3rdfloor.wordpress.com/2013/02/27/ubuntu-lost-password/)

---

### Post by Impavidus on 2013-02-27
> **moparfreak426 said:**
> ... and ive tried typing passwd in terminal and it doesnt enter anything except enter key.... 
Aren't we making this much too complicated? Did you realise that when you're typing the password in a terminal it doesn't show up on screen, although it is accepted? This makes it look like it doesn't accept any keyboard input, which is often confusing to new users.

---

### Post by matt_symes on 2013-02-27
Hi

> **Impavidus said:**
> Aren't we making this much too complicated? Did you realise that when you're typing the password in a terminal it doesn't show up on screen, although it is accepted? This makes it look like it doesn't accept any keyboard input, which is often confusing to new users.

You may well be right here. when you've used linux for a while you tend to forget these things.

BTW:

It is possible to change sudo's behaviour to get feedback when you type passwords in.

Some consider it a security risk as you can see the number of characters entered if not the characters themselves.

For most home users though, IHMO, i don't consider this a security risk.

For those interested read:

```
man  visudo
``` 

and 

```
man sudoers
```

The answers are contained within there.

Kind regards

---

