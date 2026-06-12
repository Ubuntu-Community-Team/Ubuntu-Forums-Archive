---
title: "Samba and Remote Desktop support without internet connection"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by FlintZA on 2008-11-10
Hi,
I have an old PC which I want to use as a media server with Xubuntu and Twonkyserver. I have just done a fresh Xubuntu install from a live disk, and I'm having trouble with two vital elements:
- Remote desktop support: It seems Xubuntu doesn't have built in remote desktop server support, I need this to manage the server from my laptop on my home network. 
- SMB: I need to install samba support to be able to share the media folders to be able to copy media from other machines on the network.

Both of these problems are solved in other threads for cases where the machine has an internet connection, but in this case I do not have an internet connection available to me. How can I get the software I need saved to an external drive to install offline? I have tried using the install disk (and a standard Ubuntu install disk) as the source, but it doesn't have the necessary packages.

---

### Post by louieb on 2008-11-10
How is your home network setup then? 
If you get a router or hub (router would be easier to setup). Then  you can create your own **intranet. **Then the tutorials that refer to having a internet connection will work for you.

A far as getting samba and other packages installed you can use something like apt-on-cd.

---

### Post by FlintZA on 2008-11-10
Thanks for the reply louieb. I'm specifically referring to getting the packages I need without an internet connection, I fail to see how setting up an intranet would help this? AptonCD does look like it will do what I need, thanks a stack :)

---

### Post by FlintZA on 2008-11-10
Just another related question. I've installed AptonCD on an Ubuntu machine here, and run it to build an apt CD, and the list of packages includes X11vnc (that I will need for remote desktop use and installed with apt-get) but the samba packages (which are installed by default, and I'm already using to share on that machine) are missing. Which folder would I include to have the samba packages included? Alternatively can I safely install samba again with apt-get and then build the disk? Another option should be to add an 8.10 Ubuntu install CD as a repository source, right?

---

### Post by louieb on 2008-11-10
Don't know if it changed with v8.10. But in earlier versions  the alternate install CD could be used as a package source, the desktop CD could not. You'll just have to try it and see what happens. 

Guess I just got confused. Thought you had a couple of questions, not just the one about how to get packages without internet.

---

### Post by FlintZA on 2008-11-11
I've got an 8.4 alternate disk lying around, I'll try that. Thanks.

---

