---
title: "forgotten login name??"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by jockyburns on 2011-09-26
Since downloading Ubuntu 11.04 several weeks ago, it has crossed my mind  that I set it to automatically log me in on startup. I know my password that I set when I installed Ubuntu, but for the life of me I can't remember the full login name I put. IS there an easy way to find the username off the system (I know the login password is encrypted, ) but was wondering if the username is as well. Sorry about what must seem a very silly question (probably with an easy answer) ((The amnesia doesn't help either;);)))
Cheers JB

Only need this just in case I ever have the need to log out of my computer in future.

---

### Post by SlugSlug on 2011-09-26
> **jockyburns said:**
> Since downloading Ubuntu 11.04 several weeks ago, it has crossed my mind  that I set it to automatically log me in on startup. I know my password that I set when I installed Ubuntu, but for the life of me I can't remember the full login name I put. IS there an easy way to find the username off the system (I know the login password is encrypted, ) but was wondering if the username is as well. Sorry about what must seem a very silly question (probably with an easy answer) ((The amnesia doesn't help either;);)))
Cheers JB

Only need this just in case I ever have the need to log out of my computer in future.


open terminal

```
whoami
```

---

### Post by matt_symes on 2011-09-26
Hi

> **SlugSlug said:**
> open terminal

```
whoami
```

Quite! 

Or for a standard Ubuntu install (where you have not messed about with the $PS1 variable) just open a terminal and look at the prompt .

```
[COLOR=Red]matthew[/COLOR]@[COLOR=Navy]matthew-laptop[/COLOR]:[COLOR=Green]/sys/bus/usb$[/COLOR] 
```

The user name is red and the computer name is blue. The current working directory is in green (pwd).

Kind regards

---

### Post by jockyburns on 2011-09-26
Cheers all Good job I can remember my name then. Simples :D:D:D:D

Have a brain full of passwords and usernames though, for different sites. What will I do once alzheimers sets in ??

---

### Post by Lisiano on 2011-09-26
Once Alzeimers sets in, try using something along the lines of [KeePass]("http://keepass.info/"). To install it, run ```
sudo apt-get install keepass2
```Or use the Gnome-Keyring.

---

### Post by jockyburns on 2011-09-26
Thanks Lisiano, looks like a great program for the terminally aged :D:D:D
Nah seriously though, I also have to remember my G/F's passwords for various sites. 
I did log off just to see what happens though (once I had the info from the replies. When it came to logging on again, my username was already there in the box so all I had to do was type in my password. 
Gracious thanks to all who replied. ;);)

---

