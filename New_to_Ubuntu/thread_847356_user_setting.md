---
title: "user setting"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by UbuntoRookie on 2008-07-02
First time with Ubuntu and the forum. I accidently uncheck the administrator option on users and group setting and now I can't get into Synaptic Package/Add and Remove, Network Configuration or anything require administrater.  I can't login into the root either.  When type in sudo in terminal it's require a password and i typed in the user password, and it kept saying that's not the right password.  When I type in su then it'll take the user password.  What's the different between su and sudo?

How do I go about fixing this problem and what's the root password?  I don't remember getting a root password during installation.  Any help would be appreciate.  I used Ubuntu 8.4 on a HP Pavilion dv1000.

Thanks

---

### Post by nintendorulz55 on 2008-07-02
someone please answer. i am having the same problem while trying to install java. i need permissions, but my sudo password doesnt work with su.

---

### Post by Nxion on 2008-07-02
> **UbuntoRookie said:**
> First time with Ubuntu and the forum. I accidently uncheck the administrator option on users and group setting and now I can't get into Synaptic Package/Add and Remove, Network Configuration or anything require administrater.  I can't login into the root either.  When type in sudo in terminal it's require a password and i typed in the user password, and it kept saying that's not the right password.  When I type in su then it'll take the user password.  What's the different between su and sudo?

How do I go about fixing this problem and what's the root password?  I don't remember getting a root password during installation.  Any help would be appreciate.  I used Ubuntu 8.4 on a HP Pavilion dv1000.

Thanks

By default, Ubuntu have root login via the gui disabled. 

So when you unchecked the admin option, Now when you try to open synaptic does it prompt you for a password? or does it just error out?

In regards to the su vs sudo option I found this post.
[http://forums.macosxhints.com/showthread.php?t=4534](http://forums.macosxhints.com/showthread.php?t=4534)

I know it was from macosxhints but su and sudo are generally the same across the board.

Also when you were first installing it should have asked you for the root password and for a password when you first created user. Did it not ask you?

THanks,
Nx

---

### Post by bumanie on 2008-07-02
I know this is not quite the same thing as you have done, but I suspect if you follow [this]("http://www.psychocats.net/ubuntu/resetpassword")  and reset your password/user account, you may be able to get things back to normal. Hope it works.

---

### Post by Nxion on 2008-07-02
> **nintendorulz55 said:**
> someone please answer. i am having the same problem while trying to install java. i need permissions, but my sudo password doesnt work with su.

Are you trying to install Java via terminal?

Also...

When you type "su" and put in your password what happend's?

---

### Post by Sydius on 2008-07-02
> **Nxion said:**
> 
Also when you were first installing it should have asked you for the root password and for a password when you first created user. Did it not ask you?

With 8.04, I'm pretty sure (unless I'm blind) that it doesn't ask for a root password anywhere during a normal install--just the first normal user, which has sudo privileges.

---

### Post by stchman on 2008-07-02
> **UbuntoRookie said:**
> First time with Ubuntu and the forum. I accidently uncheck the administrator option on users and group setting and now I can't get into Synaptic Package/Add and Remove, Network Configuration or anything require administrater.  I can't login into the root either.  When type in sudo in terminal it's require a password and i typed in the user password, and it kept saying that's not the right password.  When I type in su then it'll take the user password.  What's the different between su and sudo?

How do I go about fixing this problem and what's the root password?  I don't remember getting a root password during installation.  Any help would be appreciate.  I used Ubuntu 8.4 on a HP Pavilion dv1000.

Thanks

Reboot and select recovery mode from the kernel list and type:

```
adduser <username>
```

substitute <username> with like joe or something.

This will give you a new account with administration privileges.

You can now logon with the new user and go to System--->Administration--->Users and select your non admin username and check the box to Administer the system.

Hope this helps.

---

### Post by Nxion on 2008-07-02
> **Sydius said:**
> With 8.04, I'm pretty sure (unless I'm blind) that it doesn't ask for a root password anywhere during a normal install--just the first normal user, which has sudo privileges.

Actually you might me correct on that. But for me I actually had to edit the /etc/sudors file and give myself access to be a sudoer.

---

### Post by UbuntoRookie on 2008-07-02
> **Nxion said:**
> By default, Ubuntu have root login via the gui disabled. 

So when you unchecked the admin option, Now when you try to open synaptic does it prompt you for a password? or does it just error out?

In regards to the su vs sudo option I found this post.
[http://forums.macosxhints.com/showthread.php?t=4534](http://forums.macosxhints.com/showthread.php?t=4534)

I know it was from macosxhints but su and sudo are generally the same across the board.

Also when you were first installing it should have asked you for the root password and for a password when you first created user. Did it not ask you?

THanks,
Nx
Thanks to all with the questions.  I'll try it later, but as far as asking for the root password during installation I don't remember it at all.  The User acct is the only account I remember creating during installation.

---

