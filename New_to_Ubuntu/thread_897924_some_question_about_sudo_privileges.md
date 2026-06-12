---
title: "some question about sudo privileges"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by xusword on 2008-08-22
Hi

I just installed my xubuntu on my school computer yesterday. I have some question about my setup.

When I first install the system, I entered an admin account name, and then I created another account for myself. The account I am using right now does not have privileges to sudo anything except shutdown.

Since I actually dont know much about security, I am just curious, in theory, is this 2-tier users system I have more secure (against malware and hackers) at all than granting everyone privileges to sudo everything?

P.S. Also, I am wondering, is there any (desirable) task that you cant achieve by using a series of sudo but you would if you su as root user?

thanks

---

### Post by iansane on 2008-08-22
Yes it is safer.

Even if someone wrote a script or virus that used the sudo command, they would have to be a sudo user and know the root password to gain root access.

I haven't found anything yet that couldn't be done with sudo and a password but I don't really know much about su since I never use it so maybe there is a time and place to use it instead.

lol now i feel silly. I think I just answered my own question about why linux is safer.

---

### Post by bubba_169 on 2008-08-22
Ubuntu doesnt use a root user - a root user would be able to do anything to any file without entering any passwords. Instead the accounts are set up in Ubuntu where usually, any programs run have lesser privileges and permissions unless the user tells Ubuntu they want to run with all privileges (sudo/gksu) and provide their password.

In terms of security the account without sudo access will be slightly more secure than the one with sudo access because you wont be able to change any system files at all. However the difference in security vs the convenience of sudo makes it seem pointless to not let yourself use sudo. 

Thats my view anyhows... :)

---

### Post by oldos2er on 2008-08-22
> **bubba_169 said:**
> Ubuntu doesnt use a root user - a root user would be able to do anything to any file without entering any passwords.:)

 This is not true. Root must login the same as any other user.

---

### Post by bubba_169 on 2008-08-22
Sorry what I meant was after login, you wouldnt need to use sudo and enter the password ... root can edit/delete/move/manipulate any system file without question

---

### Post by xusword on 2008-08-22
> **bubba_169 said:**
> The difference in security vs the convenience of sudo makes it seem pointless to not let yourself use sudo. 

Thats my view anyhows... :)

Yeah, that's where I am struggling
I think I will give myself admin privileges until I am more familiar with the OS... but again, it is more unsafe in the sense that I don't know what I am doing... :confused:

---

### Post by cardinals_fan on 2008-08-22
> **xusword said:**
> Yeah, that's where I am struggling
I think I will give myself admin privileges until I am more familiar with the OS... but again, it is more unsafe in the sense that I don't know what I am doing... :confused:
I'm not a fan of the sudo method.  I prefer to use the old-fashioned "su" to gain root access, and sign out when I'm done with the system.

However, you should never run as administrator.  You give anything you run the power to do anything it wants - a bad idea.

---

### Post by xeth_delta on 2008-08-22
There is a lot of information on root/sudo here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

A good resource for beginners: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I agree with previous posters, I would seriously not recommend giving administrative privileges to yourself permanently. Not only because it would be a security risk, but also because while you familiarize with the system, mistakes you make can affect the entire system, and will not be restricted to your account alone.

Use sudo or a root account only for administrative privileges and no for any regular program.

Good luck!

---

### Post by jerome1232 on 2008-08-22
[offtopic]
The main thing I like about sudo, you don't have to give the root password out to everyone you want to have admin rights, and it offers control if you say want a particular user or group to be able to run one or a few programs as root.

But that stuff is more beneficial in a server/multi user environment.
[/offtop]

It's fine if your user is in the admin group, just don't run as root all the time. It would make your system vulnerable.

---

### Post by Cheesehead on 2008-08-22
As a new user of a desktop (non-server) system, your biggest use of sudo will be for periodic updates (System-->Administration-->Update Manager).

Really, I suggest wandering around the installed system and using the existing applications before installing anyting new - most of what you need is already there, though you may not know the name yet.

As you get experienced you may want to install new applications (use the Add/Remove or Synaptic *package managers* to install new stuff - downloading stuff off the net is inviting a big headache for you.

You may want to customize your system - search these help pages and forums for help with that. *Tip:* A well-crafted change shouldn't require sudo, either.

---

### Post by xusword on 2008-08-23
Yup, when I said I gave myself administrative access I didn't mean make myself root (I didn't even know if that is possible)

I meant putting myself in admin group; therefore I am able to sudo anything. I guess it is safe enough because every time I would like to start a sudo task they always ask for password.

---

### Post by xeth_delta on 2008-08-23
> **xusword said:**
> Yup, when I said I gave myself administrative access I didn't mean make myself root (I didn't even know if that is possible)

I meant putting myself in admin group; therefore I am able to sudo anything. I guess it is safe enough because every time I would like to start a sudo task they always ask for password.

Ok, that is different, and isn't it the standard practice with the first added user to the system in Ubuntu? Was that account not the first one?

---

### Post by xusword on 2008-08-24
> **xeth_delta said:**
> Ok, that is different, and isn't it the standard practice with the first added user to the system in Ubuntu? Was that account not the first one?

Yes, because this computer is public property in my school. So, I name the first account XXXXadmin

---

