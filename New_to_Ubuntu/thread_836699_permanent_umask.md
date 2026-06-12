---
title: "permanent umask"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by _TED_ on 2008-06-21
Hello there!

How can I add a permanent umask to a user?

---

### Post by HalPomeranz on 2008-06-22
Edit that user's $HOME/.bashrc and add the umask command to that file.  That will set the umask value every time the user fires up a shell.  If you want to set a default umask for all users, put the umask setting in /etc/profile.

Or were you asking how to enforce a minimum umask value and prevent users from changing it?  You can't do that unfortunately-- users always have the final say on what their umask is.

---

### Post by _TED_ on 2008-06-22
ty! it worked! (the second one, I didn't find any file named .bashrc ...)

---

### Post by _TED_ on 2008-06-22
exm... problem again:

I connect to an ftp server on that pc, with a user who sould create files with permissions: 777. 
It works when he create a foldger, but not when he copy/pastes files, they have permissions 000... (In case it helps, when he copy/pastes foldgers with files inside, foldgers have permissions 777 and files inside them 000 ! !)

---

### Post by HalPomeranz on 2008-06-22
When a user logs in via FTP, they don't start a normal command shell, so your setting in /etc/profile won't help these users.  Normally the FTP server will have a way for you to set a default umask in the server configuration file.  What FTP server are you using?  vsftpd?  WU-FTPD?

---

### Post by _TED_ on 2008-06-22
I use vsftpd.

I have put the following lines in the config file:

local_enable=YES
local_umask=000
anon_umask=000

The foldgers that both local, and anonymous create have permissions 777, but if they copy/paste something it has 000...


edit: the file system that I try to copy files from, is NTFS, and I connect throw windows xp...

---

### Post by HalPomeranz on 2008-06-22
I don't have a lot of experience with vsftpd, but it looks like you're doing everything right.

The next thing I would try testing would be to log into your FTP server using the command-line FTP client and put a file from your XP machine.  If you are able to transfer files with the permissions you want via the command-line client, then the problem you're having is due to whatever graphical file browser your users are using to drag/drop files.

---

### Post by _TED_ on 2008-06-22
nope... it's the same thing with cmd too :(

btw, I just realized that I can't connect from anywhere else but my localnet :(

I have ubuntu server 7.10, and I didn't install any firewalls (is there one from ubuntu?) - (apache server is reachable from the outside world...)

---

### Post by HalPomeranz on 2008-06-23
There is a firewall in Linux, though Ubuntu doesn't enable it by default.  If your web server is reachable and your FTP server isn't, then it's possible that the FTP server itself is configured to block access from networks outside your LAN.

It may also be a configuration issue at the network layer.  For example, if you're doing NAT you may have to configure your router to pass the FTP traffic in to your FTP server.  Also you may have to configure your network-layer firewall to pass the traffic.

I'm stumped at what could be causing the permission problems on uploaded files.  My posting to this thread will bump it up to the top of the queue and and hopefully somebody else will chime in here.

---

