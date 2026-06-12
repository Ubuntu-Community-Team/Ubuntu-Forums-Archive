---
title: "Trying[sudo -] password for user"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by zania on 2013-02-26
In the terminal I tried: 
  user@user-Inspiron-1525:~$ sudo -
[sudo] password for user:
  It does not allow me to write anything in the opened window.
  So I was stack!
  I have admin privileges.
  Any suggestions welcome.

---

### Post by deadflowr on 2013-02-26
What command are you trying to run?
sudo is used to lift a user from his/her restricted rights to an elevated level. However, it needs a command to activate it.

---

### Post by JiuJitsu500 on 2013-02-26
Yeah man sudo on it's own doesn't do anything.

something like "sudo deluge" or "sudo gedit /etc/default/grub" or "sudo reboot" will do something - like dead said, you need a command. In these cases "deluge-gtk" is a graphical torrent client, gedit is a text editor default with GNOME-based environments, and reboot is just that...

the command "su" grants the rest of anything else you have to type superuser priveleges until you close the terminal or exit... "gksu" is meant for graphics-based tools like nautilus....

sudo means "super user do" followed by your command for a one-time run. Also, *nix won't show your password after any su ordeal, just type in your password and hit enter - it'll run what you tell it to but won't show that you typed your password.


EDIT*** Admin means you are su, btw.... the "administrator" on linux or any *nix is not when you are the admin account - even then it won't let you destroy the system without su. What that means is that you are in more ocntrol than other users (say, your kids or something you don't want to edit settings and such). In *nix, the "administrator" like windows is the superuser - but you have to tell it to BE su first, usually with sudo <command> <flags, parameters, filepaths, etc> in order to actually change the system, rather than just tell other users they can't run certain apps or change settings or such.

---

### Post by theDaveTheRave on 2013-02-26
The other thing to remember is that when the 
```

[sudo] password for user:

```
is shown it will not display anything that you type in (not even # or * characters), this is another security feature, to ensure that no-one looking over your shoulder could get your password.

Dave

---

### Post by deadflowr on 2013-02-26
> **theDaveTheRave said:**
> The other thing to remember is that when the 
```

[sudo] password for user:

```
is shown it will not display anything that you type in (not even # or * characters), this is another security feature, to ensure that no-one looking over your shoulder could get your password.

Dave

Duh, I'm so use to the fill in the blank password field I forgot some users get baffled by that.

+1 to the above advice.

---

### Post by zania on 2013-02-27
Thank youall  for your quick responce!
I was expecting * or somthing.
All the best

---

### Post by mastablasta on 2013-02-27
> **JiuJitsu500 said:**
> something like "sudo deluge" or "sudo gedit /etc/default/grub" or "sudo reboot" will do something - like dead said, you need a command. In these cases "deluge-gtk" is a graphical torrent client, gedit is a text editor default with GNOME-based environments, and reboot is just that...

 
this is wrong usage of sudo. it can lead to complicaitons. sudo is used for command line commands. for graphical aplicaiton the command is gksudo. see more here on the difference and the problem it causes.: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
 
and here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
>  
 
You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo). 


---

### Post by Paqman on 2013-02-27
You sort of can use sudo on it's own. For example, adding the -i switch gives:
```

sudo -i

```
Which drops you into a root-like shell where you can work without having to add sudo to every command. Just type:
```

exit

```
...to get back to the regular command line.

---

### Post by CharlesA on 2013-02-27
+1 to Paqman.

Also:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

;)

---

