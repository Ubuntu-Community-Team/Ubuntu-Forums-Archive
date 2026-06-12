---
title: "Remote Desktop/Access"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by skozzy on 2008-06-10
I'm still getting the hang of ubuntu, so far I think i'm doing well, I havn't bailed out and gone back to windows yet.

I have 2 PCs running Ubuntu and Windows dual booting well, 1 laptop also running well, and a very old HP Omnibook laptop running a mini version of 8.04 with a cutdown gfx interface (not sure what it's called).

On that old laptop I would like to know what program(s) I have to install to be able to remote access it from anyone of the other computer (running ubuntu or windows). The normal ubuntu installs I can use VNC from windows and it works well, but I assume the cutdown 8.04 on the old laptop needs a VNC installed or something.

I prefer to have the same remote desktop access as what is on the main releases of ubuntu. I must admit I have only been able to access ubuntu via winvnc from WindowsXP, I still don't know how to access one computer to the other using ubuntu.

I looked at TightVNC and attempted to use it on the old laptop but I had no luck.

---

### Post by hyper_ch on 2008-06-10
For remote desktop I use krfb / krdc... one is the server that lets others access this machine and one is the client.

But why do you need a remote desktop? Wouldn't be accessing shared folders be enough?

---

### Post by skozzy on 2008-06-10
The old laptop is just being used on a IRC channel using xChat to keep the channel user count up to keep a few bots in there (the bots part when the user count is low). There isn't anything else worth doing on it cause of it's age. And the remote access is to save my lazy butt from getting up to remove it from the top of a cupboard to make it log in if it didn't auto reconnect to the channel if the connection went down.

Later when I learn ubuntu more and get a grasp on how to setup a www server and ftp server I might use it on one of the access points I have to run a open wifi in my street. Once again, being lazy the remote access will be nice to have.

---

### Post by Xiong Chiamiov on 2008-06-10
If you're just running an irc client, you might take a look at [bitchx]("http://www.bitchx.com/"), which is a cli irc client.  Running without an X session will save quite a bit of resources.

---

### Post by hyper_ch on 2008-06-10
or irssi :)

---

### Post by skozzy on 2008-06-10
Being limited on free time I prefer to keep running what I am using (cause it is working) and just be able to remote access the desktop. So I only need to know what program(s) to install to have a normal VNC access to it since I have WinVNC (at home and work) where I can access the other computers if needed.

I can't seem to find the name of the remote desktop that ubuntu uses, I guess if I know that I can use the package manager to install it

---

### Post by ayenack on 2008-06-10
I would use VNC over an SSH connection. There's loads of HowTo's on this on the net or you can take a look at the Ubuntu docs [here]("https://help.ubuntu.com/community/VNCOverSSH").

Basically you'll need to install OpenSSH Server and VNC on the old lappy.

Hope this is of some help.

---

### Post by ayenack on 2008-06-10
Bump.

EDIT: Sorry bumped the wrong thread.

---

