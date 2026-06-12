---
title: "how do i share files on my home network?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by snuffy on 2008-07-26
how do i share files and folders on my home network. I have several computers, some ubuntu, some xp. i can't find out how to do this anywhere!

cheers.
tim.

---

### Post by wishyjr on 2008-07-26
the key word here is 'Samba'. Its a open source networking stack that allow linux mahcines to read/write to Windows mahcines. There should be some packages installed by default in Ubuntu.

Try going to 'Places' then 'Network' or 'Connect to Server' (sorry im at work and away from my linux system). After that you should be presented with a dialog allowing you to enter details for a windows machine. This should allow you to browse file on windows machines (providing the windows machine in question has shared folders).


If you want to share a folder on an ubuntu machine to be browsable by other machines on the network i think you can just right-click on a given folder and select sharing, this will let you define the share name and other details.

---

### Post by snuffy on 2008-07-26
great, thanks.

do i need samba to share files between ubuntu computers?

---

### Post by wishyjr on 2008-07-26
> **snuffy said:**
> great, thanks.

do i need samba to share files between ubuntu computers?

y'know, i dont actually know :) I only have one ubuntu machine. But i don't think so - i think Samba was designed to connect linux and windows machines together.

---

### Post by bobbob94 on 2008-07-26
If you're only sharing between Linux machines you can use NFS, but in mixed network of Linux and Windows, Samba is the way to go (the LInux machines can also use samba to talk to each other).

---

### Post by eightmillion on 2008-07-26
Snuffy, you don't need samba to share files between ubuntu computers. You can also use NFS. Since you have windows computers on your network, I would set up samba. This [guide]("https://help.ubuntu.com/community/SettingUpSamba") should be able to help.

---

### Post by snuffy on 2008-07-26
thanks, ok, i'll look into samba for the ubuntu-windows thing.

for ubuntu-ubuntu, i've tried right clicking on a folder i want to share and selected 'sharing options' but when i try to set it up it says i don't have the correct permissions. this happens no matter what folder i try whether its in my home folder or other hard drives. ??

any ideas

---

### Post by eightmillion on 2008-07-26
You have to be root to share folders. I don't have gnome installed, but I think there's a sharing dialog under System>Preferences. If you can't find that, you can run an instance of nautilus as root by entering 'gksu nautilus' in a terminal. Then you should be able to right click on a folder in that nautilus window and share it. The usual disclaimers apply. Be careful what you do as root.

---

### Post by billgoldberg on 2008-07-26
I would avoid samba.

I use SSH, it's easy to set up and use, especially between ubuntu computers.

Installing and setting it up, shouldn't take more than a minute.

You just install

"openssh-client" and "openssh-server" on all your ubuntu computers.

```
sudo apt-get install openssh-server openssh-client
```

And it's installed.

To connect to your other pc, go to "places -> connect to server".

Pick "ssh" on the top, you'll need the ip adress of the other computer *(right-click the network manager applet, and look at the information)*.

Then as port you enter "22"

The folder you want to share is "/home/username" 

And you can fill in whatever you like in the "bookmark" part.

[IMG]http://linuxowns.files.wordpress.com/2008/06/ssh.png?w=335&h=299[/IMG]

And you'll have access to all the files on the other computer (after entering the password).

To use ssh on windows:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

---

### Post by snuffy on 2008-07-26
thanks, i'll try it.


[QUOTE=billgoldberg;5462468]I would avoid samba.

I use SSH, it's easy to set up and use, especially between ubuntu computers.

Installing and setting it up, shouldn't take more than a minute.

---

### Post by snuffy on 2008-07-26
thanks, i'll try that too.



> **eightmillion said:**
> You have to be root to share folders. I don't have gnome installed, but I think there's a sharing dialog under System>Preferences. If you can't find that, you can run an instance of nautilus as root by entering 'gksu nautilus' in a terminal. Then you should be able to right click on a folder in that nautilus window and share it. The usual disclaimers apply. Be careful what you do as root.

---

