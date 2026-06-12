---
title: "Shell Scripting"
date: 2007-09-17
forum: Programming Talk
---

### Post by aztlan72 on 2007-09-17
It's kind of late where I am at so please excuse me if I post this in the wrong category.

My question is this. I installed the Cisco VPN client and it works fine and all, I can go to my shell and run my command 

vpnclient connect work

and it connects and all, after it connects thou, the process basically stays running in the shell. I know if I press Ctrl-z and then bg I can send this process to the background and exit the shell and have the VPN connection stay active. So my question is this. I made a script, which executes all the commands

$ VPN Connection Script
# VPN Connection Script
clear
echo password | sudo -S vpnclient connect work
# Username 
echo username
# Password 
echo password
<---------  at this point, I want the script to be able to send the Ctrl-z command to stop the process, then bg to send the process to the background, then the end and exit commands to close the shell window.

I want to run the shell script from an Icon on the desktop by creating a new launcher, but it half works until I can get throu this hump.


Thanks in advanced for any replies.

---

### Post by ghostdog74 on 2007-09-17
when using third party applications like vpnclient or others, always check the manual that comes with it. It may have an option that you can use to put vpnclient in "daemon" mode.

---

### Post by aztlan72 on 2007-09-17
I checked the Cisco website to see if there was anything in terms of a Daemon, I couldnt find anything, so I guess this would be my only chance of getting this thing to work the way I would like it to.

---

### Post by nanotube on 2007-09-17
look into "expect"
```
sudo apt-get install expect
```
and find a tutorial for expect scripting, or just use the man page. :)

---

