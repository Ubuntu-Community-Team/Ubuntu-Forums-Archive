---
title: "sudo vs su and root user"
date: 2008-09-21
forum: Recurring Discussions
---

### Post by elijathegold on 2008-09-21
I like Ubuntu a lot, although I actually use a derivative version. However there is one thing I don't like about it. You should have picked up from the thread title that it is sudo. 

May I appologise if this is the wrong forum; this post is not about a security flaw but it does regard security.

There is something about using my user account to perform root actions that worries me and as a result I would like to go back to using the su (to root) method. Unless of course someone can give me a *cast iron* reason that sudo is better.  It seems to me that giving my root account a very strong password and using that as needed is better than having my day to day account with a weaker password able to gain root privileges.

I have seen arguments on the internet that seem to amount to "You might leave a root terminal open", well I wouldn't as I am not a *complete* moron*

Now I have enabled my root account using sudo passwd root and that works absolutely fine so the next step is to remove admin privileges from my account.

I am looking to remove root and admin groups from my user. Is this how I do it? Will automatic updates and things that currently ask for my password ask for the root password instead?

I suppose I could try it and see what happens but figured I'd ask first :?: 

* I'm still in training and thus only a partial moron

---

### Post by tarun.winlin on 2008-09-21
> **elijathegold said:**
> 
Now I have enabled my root account using sudo passwd root and that works absolutely fine so the next step is to remove admin privileges from my account.

I am looking to remove root and admin groups from my user. Is this how I do it? Will automatic updates and things that currently ask for my password ask for the root password instead?

I suppose I could try it and see what happens but figured I'd ask first :?: 

* I'm still in training and thus only a partial moron

Yes, removing your user from root/admin group should work for you. But a user without admin rights would not be able to perform a system update in my opinion, I am not sure though, would love if anyone can confirm on this.

---

### Post by aysiu on 2008-09-21
If you're really that concerned about security, you shouldn't have *any* account that has a weaker password. If someone is able to compromise a user account by cracking the password, it's only a matter of time before she is able to find a way to escalate to root privileges somehow.

Ubuntu isn't designed to be super-crazy-secure (otherwise there wouldn't be a 15-minute timeout on *sudo*). It's designed to create a good balance between security and usability.

You might be able to set up a way to have an admin user use a different password for *sudo* tasks. I think [this](http://ubuntuforums.org/showthread.php?p=1053358#post1053358) might help you with that.

If I were you, though, I would create a completely limited user account with a strong password and then create another admin (not root, though) user with a strong password.

---

### Post by cardinals_fan on 2008-09-21
To quote myself:
> **cardinals_fan said:**
> I personally consider "sudo" less safe than "su", especially with the default 15?-minute timeout in Ubuntu.  Since almost all malware relies on social engineering (in which the user makes the error) to run, the safest system provides said malware no way to run as administrator.  Allowing a program to request root privileges hands the user an opportunity to screw up.  The default timeout is incredibly dangerous - if malware runs "gksudo" less than 15? minutes after the last authorization, it can do whatever it likes with no password prompt.

On my nice, secure box with "su", the only way for an app to run as root is if I execute it from within the root shell, which I exit as soon as I'm done administering the system.

Just my 2¢

---

### Post by elijathegold on 2008-09-21
I wouldn't say I was that concerned, I just like separating the two functions user and admin; even in my Windows days I wouldn't give my every day user admin rights. 

As for passwords; my *weaker* passwords tend to be 9 Lowercase / Uppercase / numeric characters and my strong passwords tend to be 15 of those with punctuation thrown in. And yes I remember them without writing them down :D

If I can get an answer to my previous question (I'm 90% sure the answer is yes)

[quote=me]Will automatic updates and things that currently ask for my password ask for the root password instead?[/quote]

I'll go for it.

Thanks for your help so far

---

### Post by jerome1232 on 2008-09-22
I am in no way an expert but a couple of reasons I like sudo vs root account.

I can create custom rules in the sudoers file that allows certain users to run certain commands as other users, I can specify which users get to run which commands as what users I allow.

I can make sudo insult me when I fat finger my password lol

In line with the first reason I can create users that have root access to one or a handful of commands I want them to be able to run, all without giving my root password out.

My account that has god-like priviliges isn't a universally known account name known to have said priviliges.

IF you don't like your every day user having sudo priviliges then just treat any account in the admin group as you would a root user and don't login to it unless you need root privilges.

edit: Another bonus is an account in the admin group can run commands as ANY user on the system without needing their password, for example the following command would copy the contents of joe's ~/ to john's home directory as if you were the user john, so the files land in the correct location with correct permissions for john without involving the root user.
```
joe@cpu:~$ sudo -u john cp ~/ /home/john
[sudo] password for joe:
joe@cpu:~$
```

seems like it's not that different to use sudo to me.
```
unprivliged@cpu:~$ su myaccountwithadminprivs
password:
myaccountwithadminprivs@cpu:~$ sudo -i
[sudo] password for myaccountwithadminprivs:
root@cpu:~#
```

---

### Post by NoWayBill on 2008-09-22
With regards to an external attack (hack) sudo is safer.
As in an attacker must get both the username and password to aquire admin privileges.

With su one need only find the password since the username is always root.

---

### Post by Bachstelze on 2008-09-22
> **NoWayBill said:**
> 
With su one need only find the password since the username is always root.

You can disable root login while still allowing users to [FONT="Courier New"]su[/FONT]. In that case, [FONT="Courier New"]su[/FONT] and [FONT="Courier New"]sudo[/FONT] are pretty much equivalent if you're on a system with only one admin "level" (i.e. you only have normal users and admins that have full access to root privileges, by whichever means).

However, if you need more flexibility, [FONT="Curier New"]sudo[/FONT] is simply the only way. For example, you can specify on a per-user (or per-group) basis who can run what as root (o as any other user), which allows you to have "half admins" that can do some things, but not everything (like moderators here can edit posts but not edit users' avatars, which only admins can).

Oh, and by the way, the fact that you can't login as root in Ubuntu is not a consequence of the fact that [FONT="Courier New"]sudo[/FONT] is enabled by default. You can very well use [FONT="Courier New"]sudo[/FONT] while keeping your root account enabled.

---

### Post by elijathegold on 2008-09-22
Fantastic information guys.

sudo it is then. I'll just have to get used to it.:biggrin:

---

