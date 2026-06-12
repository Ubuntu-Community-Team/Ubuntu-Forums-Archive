---
title: "How to change to . in the root folder"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by Nedrin on 2012-12-18
Hey, I've been learning to work with the shell slowly but steadily, I'm trying to view the shell history which should be in the /root/.bash_history file. 

Now I have no idea how to access this file. Ive tried listing it with l -a but I can't seem to find it. 

Any help would be appreciated.

---

### Post by dannyboy79 on 2012-12-18
root won't have a bash history because Ubuntu disabled logging in as root on all it's systems. also, the command to list files is ls, not just l. so it would be this to even show hidden files.

```
ls -la /home/yourusernamehere/
```

If you want to view YOUR bash history, it would be in your users home directory

---

### Post by JKyleOKC on 2012-12-18
The history is maintained on a per-user basis. The only things shown in /root/.bash_history will be commands executed as the super user. Commands that you execute without using "sudo" will be in ~/.bash_history.

The "ls" command only lists items in the current working directory, which by default is your home directory (execute "echo $HOME" to see the full path of your home directory, or "pwd" to see your current working directory's path). The "-a" option will display hidden files, but if you want to list content of some other directory you have to add the name of that directory to the command, such as "ls -a /root" to get a listing of the /root directory.

Hope this helps a bit!

---

### Post by JKyleOKC on 2012-12-18
> **dannyboy79 said:**
> root won't have a bash history because Ubuntu disabled logging in as root on all it's systems.Not always true. I've never enabled the root user on this box, but here's what I see:```
jk@mehitabel:~$ sudo ls /root -a
[sudo] password for jk: 
.	       .cache	  .gconfd	   .lightscribe  .pulse-cookie
..	       .config	  .gnome2	   .local	 .recently-used.xbel
.AbiSuite      .dbus	  .gnome2_private  .mozilla	 .synaptic
[COLOR="Red"].bash_history[/COLOR]  .esd_auth  .gtk-bookmarks   .profile	 .thumbnails
.bashrc        .gconf	  .gvfs		   .pulse	 .wireshark

```Unless I use "sudo" on the command, though, I just get an error message; the /root directory permissions are 0700.

---

### Post by sudodus on 2012-12-18
Welcome to the Ubuntu Forums :-)

While in the home directory

Run ```
sudo -i cat .bash_history
```
to view root's command history

while ```
sudo cat .bash_history
``` and ```
cat .bash_history
```
both let you view your user id's command history, basically the same as the command ```
history
```

---

### Post by oldos2er on 2012-12-18
> **Nedrin said:**
> Hey, I've been learning to work with the shell slowly but steadily, I'm trying to view the shell history which should be in the /root/.bash_history file. 

Now I have no idea how to access this file. Ive tried listing it with l -a but I can't seem to find it. 


If you run **cd /root** as your normal user, you'll see "bash: cd: /root/: Permission denied" therefore you'd need to run ```
sudo -i

cd /root

nano .bash_history
``` Type **exit** when you want to leave the root shell.

---

### Post by ajgreeny on 2012-12-18
The simple command ```
sudo cat /root/.bash_history
``` also works.  You need sudo as the file is not readable as your normal user, only by root.

EDIT:
Whoops! I missed sudodus's reply at post 5.

---

### Post by Nedrin on 2012-12-19
Thanks for the quick and efficient replies.  Very active forum by the looks of things :D

---

