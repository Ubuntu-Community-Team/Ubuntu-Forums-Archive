---
title: "New PC -- migration of software ... need ideas"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by cwmoser on 2008-11-21
I currently have an Intel P4 2.8Ghz PC - Ubuntu 8.04.  I just obtained a new AMD Athlon 64 dual core based PC.

I would like to go with Ubuntu 8.10 on the new PC ... and keep everything I've installed on my old PC.  

The only way I can think to set up this new PC is to just reload everything I've installed.  Is this the best way?  Is there a way to transport what I have installed on my old PC to my new PC?  I have /home in a partition all by itself and can copy it to the new PC.

Need ideas.

Thanks

Carl

---

### Post by MunkyJunky on 2008-11-21
I've never done this before myself, but unless you have a slow internet connection it shouldn't be too much of a problem to just reinstall all your applications through synaptic, should it? For personalised settings, everything is stored in /home in hidden folders (hit ctrl+h to see them), so you could probably just move those over and get your settings back.

But like I said, I've never done this before, so I'm not 100% on it.

---

### Post by Farmer of Bricks on 2008-11-21
> **MunkyJunky said:**
>  For personalised settings, everything is stored in /home in hidden folders (hit ctrl+h to see them), so you could probably just move those over and get your settings back.

This might not be advisable. Certainly, copy over all of your files, but you want to be careful with the hidden files (the ones starting with "." as in ".kde"). Some of the Hardy settings may not carry over to Intrepid, or could cause big bad bugs. 

My suggestion: use whatever export feature the programs provide to backup your data, and save the backups to a removable disk so you can move them to your new computer. 

Another suggestion is to go into Adept and uncheck the show "not installed" box, and then copy down whatever packages you know and reckognize that you use, like Openoffice, Amarok, Atanks, Blender, conky, Dragonplayer, Firefox, firefox-3.0, gimp, k3b, klickety, knotes, etc., and then install them on your new computer.

---

### Post by cwmoser on 2008-11-28
Alright, how about this strategy to move my Ubuntu configuration to a new PC:


- Fresh load my new PC with Ubuntu 8.10


- Copy my old /home/carl folder to my new PC overwriting the new /home/carl


- On old PC, get a list of all the packages I had installed:
  $  dpkg  --get-selections  |  grep  -v  deinstall   >  installed-software


- On new PC, reinstall all the packages I installed on the old PC:
  $  sudo  dpkg  --set-selections  <  installed-software


- Remove orphaned packages:
  $  sudo apt-get  autoremove


Anyone tried this?  Think it will work?

Carl

---

### Post by Dedoimedo on 2008-11-28
You could mount the home from the old machine as a network share under a directory like /external or /data.
Dedoimedo

---

### Post by philinux on 2008-11-28
> **cwmoser said:**
> Alright, how about this strategy to move my Ubuntu configuration to a new PC:


- Fresh load my new PC with Ubuntu 8.10


- Copy my old /home/carl folder to my new PC overwriting the new /home/carl


- On old PC, get a list of all the packages I had installed:
  $  dpkg  --get-selections  |  grep  -v  deinstall   >  installed-software


- On new PC, reinstall all the packages I installed on the old PC:
  $  sudo  dpkg  --set-selections  <  installed-software


- Remove orphaned packages:
  $  sudo apt-get  autoremove


Anyone tried this?  Think it will work?

Carl
That should work as long as username and password are the same. I'm referring of course to the home folder permissions.

---

### Post by mkvnmtr on 2008-11-28
There is an app in the system manager named APTonCD that will make a bootable disk of your current system. I have installed it but not used it yet. As I understand it is to make a disk to install a clone of the first system on another machine.

---

