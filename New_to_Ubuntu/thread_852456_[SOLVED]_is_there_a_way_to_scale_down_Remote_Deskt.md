---
title: "[SOLVED] is there a way to scale down Remote Desktop Viewer?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-07
i have four computers in my house running ubuntu
(one for my parents and one for each of my sisters and me)  

so basically im the admin for all of them because my parents are clueless with computers

i have setup the Remote Desktop  (System-Preferences-Remote Desktop)

i connect to the remote desktops  with (Applications-Internet-Remote Desktop Viewer)

everyhting works great but the problem is that my laptop has 1280x800 LCD screen while the other desktops in my house have 1280x1024 CRT


so when i connect to them my remote desktop viewer is much bigger then my screen 

is there a way to scale down the remote desktop viewer a bit so it can all fit on my screen?

---

### Post by bodhi.zazen on 2008-07-07
Yes, but it it usually a property of the client.

Better, ssh

If you want to forward X applications

ssh -X

[uwiki]SSHHowto[/uwiki]

---

### Post by tjwoosta on 2008-07-07
> Yes, but it it usually a property of the client.

what client should i use?
> 
Better, ssh

If you want to forward X applications

ssh -X

i dont understand what  you mean? (open a terminal and type ssh -X?)


what i have been doing is setting the remote desktop up individually on each computer (system-preferences-remote desktop)

i checked the box beside "require ssh" and i installed openssh-server on every computer just incase i needed it

also i checked the box beside require a password and i chose a strong password (although it only allowed for 8 digits)


then i connected from my computer with whatever client comes installed on ubuntu (it asked for my password then it connected first try)

so with all the computers ive been using whatever client comes pre-installed, what client should i use?

---

### Post by bodhi.zazen on 2008-07-07
Take a look at the link I gave you on how to ssh

ssh gives you remote access via a CLI interface.

ssh user@server

If you use the -X flag you can then forward X apps.

Once you have connected, for example, you can sudo synaptic ...

---

