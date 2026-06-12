---
title: "Want to Change Admin Username"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by Jeffrey Kang on 2011-11-26
I need to change my username because I'm giving this computer to a friend.

I tried to access this page: [http://ubuntuforums.org/showthread.php?p=4968235](http://ubuntuforums.org/showthread.php?p=4968235)

but apparently, I am not allowed.

Can anyone help me?

---

### Post by sudodus on 2011-11-26
It is better to ***create a new account*** with the proper privileges (the new owner should have administration privileges). Your can either keep 'your' account if you need to help your friend in the future or delete it. I suggest you keep it at least for some time. Change the password or let your friend change it if he wants to.

---

### Post by Jeffrey Kang on 2011-11-26
Wow. How did I mess that one up?

What I meant to say was that I want to change my username and I'm going to keep the computer. I'm not giving it away. So I need to keep all the files.

---

### Post by Corporation on 2011-11-26
Do in terminal: 

sudo usermod -l oldname newname

But it won't change the user's home directory, for that you need to do:

sudo cp -r /home/oldname /home/newname
sudo nano /etc/passwd

Find a line like:

corporation:x:1000:1000:corporation,,,:/home/corporation:/bin/ksh

Change the bit /home/oldname to /home/newname.

This should work after a restart, but it's not an elegant method, so make sure you're comfortable in terminal before doing it.

Probably worth noting that if any files in your home directory are referenced by anything directly (using '/home/oldname/file' instead of '~/file') the link will break if you delete the old folder.

---

### Post by sudodus on 2011-11-26
> **Jeffrey Kang said:**
> Wow. How did I mess that one up?

What I meant to say was that I want to change my username and I'm going to keep the computer. I'm not giving it away. So I need to keep all the files.
Do you mean the name of your user account in Ubuntu in your computer. Why? I guess you ***can*** change your username, but it might create problems because your environment is also using it, so unless you do a lot of tweaking you will have different names of username and home folder etc. So it is usually recommended to create a new user instead of changing the username.

---

