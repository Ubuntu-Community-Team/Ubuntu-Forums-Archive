---
title: "Users and Groups setup?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by JameoPotato on 2008-05-23
Hi,
I created an FTP server with vsftpd to manage my webfiles.
I would like 2 users:
1 my normal server login (full unrestricted access)
1 other user called, "user2" that can only access /var/www/jameopotato, but has full rights inside that folder to do whatever he/she wants.

I have already made the user and set him up in his own group called restricted (GID 1001) but I don't know where to go from there.

Currently I can login with both users. User1 has the same rights as user2 for remote logins, so I set the owner of my web directory to user1 (UID 1000) but this only makes it so that user2 cannot access it.

I know how to go to CHMOD and CHOWN but i don't see how I could set it up.
At first I set owner of my web directory to user1 so he had full access but that doesn't work for user2.

[B]Who should be owner of the web directory (root)?
How do I set up group access rights to certain folders?
How do I set a remote user to unrestricted (like root) access (user1)?
What exactly does "group R/W/X rights" do if it doesn't ask what group? (i'm talking about setting access rights to files/folders. The group read, write, execute options) what group do they apply to?[/B]

---

### Post by superprash2003 on 2008-05-23
havent used vsftpd before.You could try using proftpd and install gproftpd(gui for proftpd) its quite easy to configure gproftpd , you could get a ftp server running in no time

---

### Post by JameoPotato on 2008-05-24
I'm running 8.04 Server Edition. So all shell commands. 
And from what I have read and head vsftpd sounds like its one of the best out there.. thanks for the suggestion tho.

---

