---
title: "Install Flash player"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-08-28
I downloaded flash player and can not install it.

I tried the instructions from this site

[http://kubuntu101.blogspot.com/2005/11/installing-macromedia-flash-player.html](http://kubuntu101.blogspot.com/2005/11/installing-macromedia-flash-player.html)


 but get the following errors.

allan@allanlaptop:~$ $ tar xzvf install_flash_player_7_linux.tar.gz
bash: $: command not found
allan@allanlaptop:~$ allan@allanlaptop:~$ $ tar xzvf install_flash_player_7_linux.tar.gz
bash: allan@allanlaptop:~$: command not found
allan@allanlaptop:~$ bash: $: command not found
bash: bash:: command not found
allan@allanlaptop:~$ allan@allanlaptop:~$
bash: allan@allanlaptop:~$: command not found
allan@allanlaptop:~$ tar xzvf install_flash_player_7_linux.tar.gz
tar: install_flash_player_7_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
allan@allanlaptop:~$ cd Documents
allan@allanlaptop:~/Documents$ tar xzvf install_flash_player_7_linux.tar.gz
tar: install_flash_player_7_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
allan@allanlaptop:~/Documents$ $ tar xzvf install_flash_player_7_linux.tar.gz
bash: $: command not found
allan@allanlaptop:~/Documents$
allan@allanlaptop:~/Documents$

---

### Post by tommcd on 2008-08-28
Just get the flashplugin-nonfree from synaptic package manager. It should work just fine. Then restart firefox.

EDIT: I'm not sure why you are getting "command not found" with the tar program. Can you run "man tar" in terminal to get the man page. Also, make sure you are in the directory that contains install_flash_player_7_linux.tar.gz when you try to untar it. 
But try flash from syaptic first.

---

### Post by Crafty Kisses on 2008-08-28
Why don't you just install the "flashplugin-nonfree" package from the repos?

---

### Post by swoll1980 on 2008-08-28
untar the file put the libflashplayer.so file on you desktop use this command
```
sudo mv ~/Desktop/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```make sure you use capital D in Desktop or just copy and paste

---

### Post by aysiu on 2008-08-28
That tutorials kind of old.

Try this one instead:
[http://www.psychocats.net/ubuntucat/installing-flash-on-kubuntu-804/](http://www.psychocats.net/ubuntucat/installing-flash-on-kubuntu-804/)

---

### Post by jpkotta on 2008-08-28
Too much blind copy and paste.  The '$' in their instructions indicates that it is a command to type in.  You aren't supposed to put a '$' in the command.  It's called a prompt, because it is prompting you for input (as opposed to grinding away and being too busy to accept input).  

Firefox usually saves in ~/Desktop (it really should default to ~/Documents).  

Use the flashplayer from the repos like others suggested.

---

### Post by sonofusion82 on 2008-08-28
> **saskatchewan said:**
> 
allan@allanlaptop:~$ $ tar xzvf install_flash_player_7_linux.tar.gz
bash: $: command not found
you have an additional $ in front of "tar xzvf". the dollar sign is just the shell prompt, you should exclude it when typing commands in the terminal

> **saskatchewan said:**
> 
allan@allanlaptop:~$ tar xzvf install_flash_player_7_linux.tar.gz
tar: install_flash_player_7_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


now you got the command right but you are probably in the wrong directory, you will need to change to the directory containing the install_flash_player_7_linux.tar.gz file.


anyway, like other replies, i suppose it is easier to just installed the flashplugin-nonfree using apt-get, synaptic or adept

---

