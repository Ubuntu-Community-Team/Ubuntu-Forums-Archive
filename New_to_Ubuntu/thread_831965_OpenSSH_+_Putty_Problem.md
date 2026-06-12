---
title: "OpenSSH + Putty Problem"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by BlackRabbit89 on 2008-06-17
Aye guys

Fairly new to Linux... Came across a problem.

I've installed Ubuntu 8.04 to 10GB HDD that I'll later insert into another machine 'cause most of the I/O ports are dead. (Dont ask)

So here's my dilemma... I've installed OpenSSH...

And using my brothers computer(WinXP) + Putty... I successfully connected via open ssh...

But it asks me for a password...

I'm logging in as root... and i don't have a password set for root.

I'm pretty sure that i have allowed root login.

But i have also used my other account that was created during setup... black rabbit... However, it could be me, but im almost certain i have the correct password.

It just doesn't let me log in... it just says...

'Access Denied'

Any help or ideas would be greatly appreciated.

Keep in mind that I'm still really newbie when it comes to cli.

Thanks guys... Looked everywhere and couldn't find what i was looking for.

Ciao!
Black Rabbit

---

### Post by dlehman on 2008-06-17
It has been a while since I set up SSH on my system but I think you have to run a command to generate your ssh key for the users you want to have access.  Glancing through the SSH howto it doesn't look like that is necessary any more 

here is the link to that howto

[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

As for root Ubuntu disables root logins by default and really there is no need to enable them 

the sudo command works just fine for a few commands and if you need to do many commands a 

```
sudo -i
```

will get you to a root command line 

Hope this helps

dlehman

---

### Post by neurostu on 2008-06-17
The easiest way would be to ssh using your username, then you can gain root access by using the following command:
```

sudo -s

```

Its the ubuntu way of doing 
```

su

```

and you don't need the root password, just your password (if your account has been allowed to administer the system)

ps.

I'm no expert on sudo, but a bunch of ubuntu guys chewed me out in IRC for not using:
```

sudo -s

```
for going root, apparently most of the other ways of going root, sudo bash, sudo su, sudo -i, don't handle things as well...

---

### Post by bodhi.zazen on 2008-06-17
/me chews neurostu out

```
sudo -i
```

:lolflag:

@BlackRabbit89 :

The basic syntax is :

```
ssh user@server
```Enter the user's password, then if needed sudo -i

If you want to log in as root you will need to set a root password.

If you forgot your user name/password :

boot the broken machine to recovery mode.

List user names :

```
ls /home
```Set a password

```
passwd user
``` where "user" is a user in /home

---

### Post by BlackRabbit89 on 2008-06-18
Hmm... Well I looked at the HowTo again... And as im on medication that impairs my ability to absorb information... Its difficult. [Yeah, I'm pretty much at a 2 yo's level atm]

This key gen encryption... is there anyway i could just bugger that off? 

Hell i dont even care if it has a password or anything... Its just a playground linux server. And i just need to remote connect to it.

If not, how do i go about creating a user and giving it a key... ive read that you need to give the key to the remote pc... but im using a winXP putty... where would i put the key?

Sorry for the hassle guys.

EDIT: Ah k thanks for that... Ill try that when i get the next chance. Ill post back with the results.

---

### Post by bodhi.zazen on 2008-06-18
You do not need a key, making a key will only make things one step more complex.

---

### Post by hyper_ch on 2008-06-18
a key can be used to create auto-logins so that no passwords are needed. I have this setup to rsync backups between multiple machines.

---

### Post by neurostu on 2008-06-18
> **bodhi.zazen said:**
> /me chews neurostu out

```
sudo -i
```

:lolflag:

So what is the difference between -i and -s for sudo?

---

### Post by dlehman on 2008-06-18
I apologize for all the confusion with the key, I just remember having to do that at one time, but reading through everything now you don't need a key.  

As said before 
1.  fire up putty and connect to your box
2.  login with the regular user account and password 
3. ```
sudo -i
``` will get you root access and use your user account password 

This assumes that the regular user as rights to administer, which you should because it is the  account created during install correct? 

Again sorry about the confusion with the key.

---

### Post by bodhi.zazen on 2008-06-18
> **neurostu said:**
> So what is the difference between -i and -s for sudo?

Both give root access. sudo -s uses your user environmental variables -i uses root's.

Try it yourself :

```
sudo -s

echo $HOME

exit
```

And then

```
sudo -i

echo $HOME
```

The problem with sudo -s is root will user your $HOME (and alises and other environmental variables) rather then /root (as home or root's environmental variables.). This can be problematic as any files written in $HOME will then be owned by root and will result in conflicts (try starting a shell (bash) in $HOME/.bashrc is owned by root).

There *may* be times when you would want to sudo -s (ie use your user's alilses and $HOME), but in general you should put any alises for root in /root/.bashrc and use /root as home when running as root.

See man sudo

---

