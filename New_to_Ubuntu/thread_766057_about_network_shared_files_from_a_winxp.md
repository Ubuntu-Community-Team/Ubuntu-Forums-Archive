---
title: "? about network shared files from a winxp"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by stevek123 on 2008-04-25
I am very new to ubuntu, HSp internet, and setting up a network. I almost have this (my Ubuntu 7.10 setup :) ) where I dont go upstairs to use the POS winxp machine. I have enabled the std shared files from winxp and what I want available to network from my ubuntu machine. I've been able to get the winxp printer to work over my network too. The thing is I'd like to make my whole data HD on the winxp (OS & BS on one HD - all data on a second) one of the 'shared files'. I dont know how. Any help?

---

### Post by bodhi.zazen on 2008-04-25
It is all point and click.

Go to Places -> Networks and navigate to your windows server.

Or go to Places -> connect to a server -> enter you windows IP / hostname and share name ...

If you have problems :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by stevek123 on 2008-04-25
No I got this ubuntu part right... shared files work like a champ. I can grab network files and folders, and my shared folders open right up up there. My problem is in the winxp POS. Ubuntu only accesses network enabled folders from the winxp POS. I dont know an easy way to move the entire HD to shared status within winxp without making a mess of the file system???? Should be easy (but probably not...)

 BUT,  Once I do, I'll be able to get all my stuff down to ubuntu. I guess it's more a winxp issue than ubuntu - but the goal is to make my family less dependent on MS distros and regain control over the software that I use-and THAT is linux. Bet I cant get much of an answer from the MS people on how to....

---

### Post by bodhi.zazen on 2008-04-25
In Windows XP, to share the entire drive, you need to go to "My Computer"

Tools -> folder options

Go to the "View' tab. All the way at the bottom, uncheck 
"Use simple file sharing"

Now share your C drive ...

---

