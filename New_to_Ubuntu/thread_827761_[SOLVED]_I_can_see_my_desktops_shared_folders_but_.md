---
title: "[SOLVED] I can see my desktops shared folders but can't open them"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by tysonh on 2008-06-13
When I click on system,places, network.  I can see my desktop pc and the folders I have shared on it.  However, when I click on one to open it a window pops up asking for a user name domain name and password.  I've made sure I'm using the right domain name.  I'm not sure what user name it wants my user name for my laptop or the user name for my desktop and which pass word do I use my desktop or my laptop password.

I've tried every possible combination I could think of.  Is there a way to assign all this information?

---

### Post by billgoldberg on 2008-06-13
You would fill in the password and username from the other computer.

Could it be firewall related?

I you are sharing between 2 Ubuntu computers (works with windows and osx, bit a bit harder) it is incredibly easy to use openssh.

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

---

### Post by iaculallad on 2008-06-13
> **tysonh said:**
> When I click on system,places, network.  I can see my desktop pc and the folders I have shared on it.  However, when I click on one to open it a window pops up asking for a user name domain name and password.  I've made sure I'm using the right domain name.  I'm not sure what user name it wants my user name for my laptop or the user name for my desktop and which pass word do I use my desktop or my laptop password.

I've tried every possible combination I could think of.  Is there a way to assign all this information?

Use the username and password (when loggin on) for the Desktop computer you're accessing the shared folder. When you have the correct credentials inputted on your "Authentication Required" window, select "Remember forever" option if you don't want inputting the same data when accessing that shared folder.

---

### Post by ukripper on 2008-06-13
> **tysonh said:**
> When I click on system,places, network.  I can see my desktop pc and the folders I have shared on it.  However, when I click on one to open it a window pops up asking for a user name domain name and password.  I've made sure I'm using the right domain name.  I'm not sure what user name it wants my user name for my laptop or the user name for my desktop and which pass word do I use my desktop or my laptop password.

I've tried every possible combination I could think of.  Is there a way to assign all this information?

Username you have assigned for samba shares.

On your machine which is sharing  folders, go to terminal and use the following commands and assign the username:
```
sudo smbpasswd -L -a your_username
```
```
sudo smbpasswd -L -e your_username
```
replace your_username to the username you currently using on this machine.

One more thing you might need to restart samba deamon:
```
sudo /etc/init.d/samba restart
```


And now acces using this username from another machine.:)

---

### Post by tysonh on 2008-06-13
when you say "replace your_username to the username you currently using on this machine.:

do you mean input my username that I use on my host desktop or my user name I use from my laptop?

---

### Post by lisati on 2008-06-13
> **tysonh said:**
> when you say "replace your_username to the username you currently using on this machine.:

do you mean input my username that I use on my host desktop or my user name I use from my laptop?

Use the name & password from the machine you are using at the time.

---

### Post by tysonh on 2008-06-13
Thanks a bunch its working perfect now :)

---

