---
title: "[SOLVED] Sudo-gksudo-visudo-gsudo simple guide?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-07-12
Many of you have undoubtedly noticed that I often refer to myself as a "gui-guy". I love how far along Ubuntu has come with gui, I believe that's what truly is bringing Linux into more and more homes.

Anyway I'm still trying to learn more about cli and as I google around reading this and that about different programs, etc. I notice different prefixes are used for different commands based on the level of "password protection" ............... obviously limiting privileges based on "user", "administrator", "root":confused:

So could someone tell me very simply what the different levels are and when it's appropriate to use each? What really peaked my interest was noting some Debian commands prefixed with "gsudo" which is foreign to me.

Sorry for the dumb nOObish question, but hey gotta' learn someday:)

---

### Post by mcduck on 2008-07-12
It's actually very simple. "sudo" is for command-line programs, and "gksudo" is for graphical programs.

If no user is specified, they execute the following command as root (asuming the user running the command is a member of the admin group.) Gksudo will provide a popup window for entering the password, and also loads root user's desktop settings properly ("sudo doesn't, so don't use it with graphical applications!)

If "sudo" or "gksudo" is followed by username and then a command, the command is run as the user specified. For example "gksudo mcduck firefox" would start Firefox as user mcduck.

"gksu" is same as "gksudo", at least on ubuntu.

"visudo" is a special tool used when manually editing sudo's settings. You shouldn't need it.

---

### Post by Polygon on 2008-07-12
im not sure what gksudo actually does, but i have read that if you plan on running any program that uses a GUI through the terminal (and it requires you to use sudo) you should use gksudo, to prevent weird permission problems which are hard to fix

but for command line programs that dont use a GUI, such as apt-get, you should use sudo

thats all there is too it really.

---

### Post by dracayr on 2008-07-12
every UNIX system (ubuntu is based on linux, which is based on UNIX) has the root user. root has User ID 0. root is the "God" of your System. He has all rights. he can read, write and execute every single file on your computer. the word "administrator" means the same as "root" in UNIX. A "user" obviously is every user other than root. In debian/ubuntu users can use the command "sudo" instead of logging in as root to gain root rights, because logging in as root is considered dangerous. gksudo is used always when u want to execute a gui program with root rights. If one would use sudo for gui programs, errors can occur, up to not being able to log in. for more information on that, see:[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo).
visudo is a seperate command for editing the sudoers file which determines which users are allowed to use sudo

dracayr

---

### Post by maybeway36 on 2008-07-12
On a KDE system, you can use kdesu in place of gksu/sksudo.

---

### Post by kansasnoob on 2008-07-12
OK, I think I'm kind of getting the idea. I also read the Psychocats guide.

Now, just for instance lets say I want to read the man sudoers and/or man sudo. 

Would I:

```
gksudo man sudoers 
gksudo man sudo
```

or:

```
sudo man sudoers
sudo man sudo
```

or could I even:

```
gksudo man sudoers && man sudo
```

or:

```
sudo man sudoers && man sudo
```

Sorry to be a pain, and many thanks in advance!!!!!!!!!!!!!1

---

### Post by brian_p on 2008-07-12
> **kansasnoob said:**
> 
Sorry to be a pain, and many thanks in advance!!!!!!!!!!!!!1

```
man sudo
``` and ```
man sudoers

```
are sufficient. Manuals are accessible to everyone

---

### Post by kansasnoob on 2008-07-12
> **brian_p said:**
> ```
man sudo
``` and ```
man sudoers

```
are sufficient. Manuals are accessible to everyone

The reason I chose manuals is because there's nothing there I can really break:confused:

---

### Post by kansasnoob on 2008-07-12
I'm marking this solved, although I'm still confused, but I'll be following it up in the Security Discussions section soon.

BACKSTORY:

While I'm perfectly satisfied with installing Firestarter and setting it up once just to be sure iptables is doing what it should be doing (that's not even necessary) I've brought about 20 seniors out of the Win 98/ME hole where they can no longer even buy a cheap HP printer that'll work to print a simple letter, and I get them hooked up with AT&T's $10.00 a month DSL and they're happy campers!

Especially when I introduce them to the simplicity of Abiword! And I can build them one lower panel and a desktop that's "friendly" for folks that are used to Windows. And I always keep them set up with their favorite email program whether it's Hotmail or Yahoo.

Where the problem starts is when their kids come around and start bitching that they have no Firewall!!!!!!!!!! So what I want, stupid or not, is to have Firestarter NOT start but "try to start" and "ask" for a password to start when the computer starts.

Yeah, I know it's redundant after the initial login but I'm tired of the whining! Then once they enter a password they'll have a cute icon in the lower panel that says, "I'm working"!

---

### Post by nothingspecial on 2008-07-12
I asked a similar question a few days ago

[http://ubuntuforums.org/showthread.php?t=851911](http://ubuntuforums.org/showthread.php?t=851911)

---

