---
title: "Creating a server?"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by tal32123 on 2013-04-30
I would like to set up an Ubuntu computer that would be able to torrent things using a VPN for a network of about 35-40 computers, afterwards I would like to have a shared folder that people can go into and copy files remotely into their own computers. I would also like to have the torrents scheduled to not download at a certain time period. I have never used Ubuntu Server before, but I have used the Ubuntu OS before. How would I go about doing this? Should I even use a server for this? What are the benefits of making a server for this instead of just an Ubuntu PC? Would I be able to still use the server for other, everyday uses such as printing, using google chrome to surf the internet, writing documents, etc.?

---

### Post by Slim Odds on 2013-04-30
Besides the difference in the default packages installed, the primary difference between the server install and the desktop install is the kernel.

The desktop kernel is optimized for user responsiveness, whereas the server kernel is optimized for services. For example, the server kernel has a much longer time-slice so that it does not spend so much of its time switching between processes. This approach would make for a poor user experience with a GUI.

---

### Post by lykwydchykyn on 2013-05-01
> **Slim Odds said:**
> Besides the difference in the default packages installed, the primary difference between the server install and the desktop install is the kernel.

The desktop kernel is optimized for user responsiveness, whereas the server kernel is optimized for services. For example, the server kernel has a much longer time-slice so that it does not spend so much of its time switching between processes. This approach would make for a poor user experience with a GUI.

That used to be the case, but now Ubuntu server and Ubuntu desktop use the same kernel.  Effectively the only difference between the two is lack of a GUI on the server.

---

### Post by Slim Odds on 2013-05-01
> **lykwydchykyn said:**
> That used to be the case, but now Ubuntu server and Ubuntu desktop use the same kernel.  Effectively the only difference between the two is lack of a GUI on the server.
That seems like a very poor choice on Ubuntu's part.
Servers and Desktops have many more differences then just whether there is a GUI or not. Server performance will suffer if the kernel is more like the old desktop version and the Desktop will not be as responsive if the kernel is more like the old server version.

---

### Post by lykwydchykyn on 2013-05-01
> **Slim Odds said:**
> That seems like a very poor choice on Ubuntu's part.
Servers and Desktops have many more differences then just whether there is a GUI or not. Server performance will suffer if the kernel is more like the old desktop version and the Desktop will not be as responsive if the kernel is more like the old server version.

I am sure that somewhere on some mailing list there is a discussion justifying the decision.  Obviously the people working on both projects felt the one kernel met their needs, I wouldn't second guess their decisions without data.

---

### Post by |{urse on 2013-05-01
> **lykwydchykyn said:**
> That used to be the case, but now Ubuntu server and Ubuntu desktop use the same kernel.
I.. did not know this! Helped me out! Thanks.

---

### Post by ajbader on 2013-05-01
Now I am unfamiliar with Ubuntu Server OS, but if you want to start a server, definitely learn how to use the terminal. Basic commands are simple (ls = show directory, cp = copy, mv = move/rename, cd = change directory, nano = text editor, [tab] = autocompletion). Then you'll want to learn how to ssh ([https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH))  into the server remotely so that you can make changes and install packages etc. As far as I know BitTorrent is a client to client system, so installing a text based torrent client like rtorrent or transmission-cli and just running those on the server would be fine I think. I don't know how to make torrent files, so good luck with that. Also you could use BitTorrent Sync which is probably more of what you are looking for. I don't know how you would do do it in a terminal. 

Other than that, the shared folder that you are looking for is done through samba. Some old documentation is here: [URL="https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html"]https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html
[/URL]
NOW, there is no reason why you can't run a server on the desktop version of the OS. If you want to make it simpler, download the desktop version because then you wont have to deal with the terminal or ssh as much.

---

### Post by papibe on 2013-05-01
Hi tal32123.

If you are thinking on using a VPN just so downloads can be done on the server side, it may not be needed.

There are several torrent clients that either have a webgui interface, or watch folders, so that torrents can be submitted remotely. Also, some of them supports scripts to trigger actions after a torrent is completed. For instance, moving the data to another directory.

transmission-daemon can do all that, for example.

Note that all major services can be set either on a Desktop or a Server edition. It just a matter of how comfortable are you using the command line, and how much hardware resources do you have. 

Let us know how it goes.
Regards.

---

### Post by tal32123 on 2013-05-01
> **papibe said:**
> Hi tal32123.

If you are thinking on using a VPN just so downloads can be done on the server side, it may not be needed.

There are several torrent clients that either have a webgui interface, or watch folders, so that torrents can be submitted remotely. Also, some of them supports scripts to trigger actions after a torrent is completed. For instance, moving the data to another directory.

transmission-daemon can do all that, for example.

Note that all major services can be set either on a Desktop or a Server edition. It just a matter of how comfortable are you using the command line, and how much hardware resources do you have. 

Let us know how it goes.
Regards.
I am planning on using a VPN so I won't get caught for torrenting (they catch you if you do it in my country)

---

