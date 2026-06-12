---
title: "Keep programs running  after I log off"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by V-600 on 2008-04-30
I have just installed ubuntu 8.04 on an old computer running as a basic file server. I would like to be able to do more than just this though but the computer is headless (and soon to be stuffed somewhere out of the way).

It starts and auto logs into a gnome desktop. I can ssh to it either from my laptop with ubuntu 8.04 or from a win XP machine using putty. I have set up (via ssh) the computer to run the folding@home client as a service when the computer starts but programs I run myself stop after I log off.

An ugly way round this is to set up any programs before hand, create an init script, let it run, then remove the script when done and reboot/restart init.

What I think I need to do is run a program as another user but I am not sure how to go about it. Hopefully the following will make it clear. 

The computer has a user called "storage". When it boots, gdm logs storage in on tty7. I can then ssh to the computer and log in again by going "storage@whatever.the.IP.is". Using this ssh session I want to be able to run programs as the user logged in on tty7.

Would this leave the programs running after I end the ssh session and if so how do I go about this?

Many thanks

---

### Post by markharding557 on 2008-04-30
adminisration>users and groups>add user
this will create a new user you can run certain programs as this user instead of yourself.
this is useful if you want to increase security by giving your extra user lower privileges

---

### Post by Bothered on 2008-04-30
Maybe "screen" would be helpful? See "man screen" or the wikipedia page: [http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)

---

### Post by V-600 on 2008-05-01
Thanks. I've had a quick play about with screen but was under the impression that when I logged off screen would stop, taking all the programs that were started with it as well.

Perhaps I was mistaken. Further research is warranted I think.

---

### Post by Bothered on 2008-05-01
screen will be left running after you log off.

An example of typical usage:

1. "screen -S [session name]" - the session name is useful if you use screen multiple times
2. Execute long running command
3. Press Cntl+a then Cntl+d to detach
4. Return some time later (perhaps after logging out), and execute "screen -ls". Your previous session should be listed.
5. "screen -r [session name]" will resume the session

---

### Post by V-600 on 2008-05-01
Thanks. That worked perfectly.

---

