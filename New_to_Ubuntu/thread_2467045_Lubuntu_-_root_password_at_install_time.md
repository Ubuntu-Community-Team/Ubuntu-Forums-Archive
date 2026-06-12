---
title: "Lubuntu - root password at install time?"
date: 2021-09-14
forum: New to Ubuntu
---

### Post by fausto99 on 2021-09-14
like the title says.

 I've just installed Lubuntu and am trying to set up Samba and Apache. I'm fed up of typing "sudo" befor every command, so would like to switch to being root. I assumed no password at install time but this does not work. I tried my username password and "password" - those don't work either. Can anyone enlighten me, please?

---

### Post by Tadaen_Sylvermane on 2021-09-14
I'm not sure if there is a policy on this for the forum but you just set one.

```
sudo -i
```

Then once under root...

```
passwd
```

Add your password. Doesn't follow the recommended way of things for *buntu but such is life. Be careful once this is done. It's all to easy to trash your system.

*EDIT*

I think you can one shot it like this. Haven't tried. ```
sudo passwd root
```

---

### Post by coley9225 on 2021-09-14
This is really not a good idea. Using sudo for commands makes you give extra thought to what you are doing, to reduce any catastrophic mistakes. However, if you insist as running as root, use extreme caution, and when you launch your terminal, use code sudo -i, enter your password, and you will not need sudo from then until you exit the terminal. REMEMBER...USE WITH EXTREME CAUTION;; YOUR ENTIRE SYSTEM CAN BE KILLED WITH A SIMPLE TYPO!! If I were you, I would reconsider doing this.

---

### Post by ActionParsnip on 2021-09-14
```

sudo su -

```
And you will become root. For security I suggest you leave the root account locked and unused, especially for a system with services like Samba and Apache.
There is a grace period for sudo which means you don't type your password for every command. The grace does expire and you need to reenter your password again but you will be able to use sudo uninterrupted during the grace.

---

### Post by fausto99 on 2021-09-14
I found a way of resetting the password entering recovery mode via GRUB. All sorted now. I come from a distant UNIX background and am reasonably aware of the dangers of doing everything as root. 

My main gripe with sudo was that, having use it to create a root owned directory, I couldn't then use "sudo cd" to go into the new directory! What sort of madness is that?

Finally, no one answered the question; what is the root password set to by the installation process (at install time)?

---

### Post by Impavidus on 2021-09-14
> **fausto99 said:**
> 
My main gripe with sudo was that, having use it to create a root owned directory, I couldn't then use "sudo cd" to go into the new directory! What sort of madness is that?That's because cd is a shell built-in. sudo doesn't work with those. Instead, use a root shell, for example with sudo -i.

> Finally , no one answered the question; what is the root password set to by the installation process (at install time)?
No password is set, so you can't login as root.

---

### Post by fausto99 on 2021-09-14
Let's just check I've understood this...

a) "sudo -i" gets me a different shell/cmd window where I am root?
b) no password is set at install time, but you can't log in as root with a blank password?!

---

### Post by ActionParsnip on 2021-09-14
The root password is not set at any time. The account is disabled by default and no password is set.

---

### Post by ActionParsnip on 2021-09-14
> **fausto99 said:**
> Let's just check I've understood this...

a) "sudo -i" gets me a different shell/cmd window where I am root?
b) no password is set at install time, but you can't log in as root with a blank password?!

a) If you read the man page for sudo by running
```

man sudo

```
You will see what it does. You sound very new to the OS and I suggest you use it as is and stick to using sudo until you understand the OS a little more.

b) If an account has no password set then how can you get the password right? Any input you give, even a blank one, will be incorrect as there is no password to compare to. This is by design and is a great security measure as the root account is common on ALL Linux systems so is targeted by attacks. If the account has no password and is locked (Which it is by default) then 100% of attempts to log in as root will fail.

---

### Post by Impavidus on 2021-09-14
I rarely use a root shell, but there's one case where you really need it. You can't cd into a directory where you have no execute permission.

Further, if you have no read permission in the directory, autocompletion of filenames doesn't work, and sometimes it's nice to have shell I/O redirection.

---

### Post by grahammechanical on 2021-09-14
I think it is more inconvenient to log out of one account and then log in to an administrator account in order to run certain commands than it is to use "sudo" to temporarily become administrator.

Other distributions of Linux, such as Debian, require an administrator or root account to be set at install time as well as a user account. Administration tasks can only be done from the administrator account. The temptation is to login as root and continue working as root rather then logging out and logging back in as a standard user.

I mention these things because this discussion is taking place in the New Users section of the forum. As others have mentioned this subject holds dangers for new users. Even long time users can easily mess up.

Regards

---

### Post by GhX6GZMB on 2021-09-14
The Username and Password entered during Lubuntu installation is for the "main" user who has sudo permissions.
A normal $HOME directory tree will be set up for this user with "root" permissions.

The /root directory is normally "dead" and is basically needless.

I've worked with Lubuntu for over two years now, and have no problems prefacing terminal commands with "sudo" when needed. The first command entered will need a password, then you can just continue working (the sudo permission will time out after 10...15 min.).

In the file manager (PCManFM-Qt), just go under "Tools" and select "Open as root", then you can work with sudo permissions until you close the window.

I have NEVER had any need for su access. In fact, I'm haappy that it's not there. Far too tempting and dangerous.

---

### Post by coffeecat on 2021-09-14
> **grahammechanical said:**
> 
I mention these things because this discussion is taking place in the New Users section of the forum. As others have mentioned this subject holds dangers for new users. Even long time users can easily mess up.



+1. Thank you @grahammechanical.

This is the New to Ubuntu sub-forum. Giving advice on how to enable the root account and thus set a huge bear trap for oneself in a section provided especially for newbies is... questionable. 

To those who so blithely give such instruction, please read and take to heart our forum root policy:

[https://ubuntuforums.org/showthread.php?t=1486138](https://ubuntuforums.org/showthread.php?t=1486138)

> If you wish to instruct people to set a root password please include, at a minimum, the nature of the problem at hand (permissions) and information on how to [lock the root account again]("https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account").


---

### Post by fausto99 on 2021-09-15
Thanks for the responses. So similar to Unix yet very different.

---

