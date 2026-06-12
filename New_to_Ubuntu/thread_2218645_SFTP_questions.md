---
title: "SFTP questions"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by antony7 on 2014-04-21
Hi there,

I have a number of questions regarding SFTP which I've setup as per these instructions:

[http://blog.srmklive.com/2013/04/24/how-to-setup-sftp-server-ftp-over-ssh-in-ubuntu/](http://blog.srmklive.com/2013/04/24/how-to-setup-sftp-server-ftp-over-ssh-in-ubuntu/)

1) When I ftp in I can upload to the home directory but I can also navigate the entire server. How can I stop that so users can't browse outside their home directory?

2) Is there a way to setup virtual users for SFTP in the same way you can using PAM and vsftpd?

3) What is the best way to change the home directory for a user - is it to change the home directory or is it to change the folder path in the ssh conf? Basically I want the user to login to /var/www/USER/www and only be able to see that folder and create sub folders/uploads etc but only in this folder but preferably as a virtual user not as a real user every time.

Thanks

Antony

---

### Post by The Cog on 2014-04-21
I've not done it myself, but I know it can be done. Google for "sftp chroot".

It has to be a user on the system, and I think that once you pin them to their home folder they cannot be used as a normal login any more. But I'm not certain of that, so unless someone comes here with a good link, use that google search.

---

### Post by Lars Noodén on 2014-04-21
As mentioned above, chroot is what you want here.  The manual page for [sshd_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) will have the details in the paragraphs on **ChrootDirectory**   For questions 1 and 3, you could look at the examples here:

[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-only_Accounts](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-only_Accounts)

Though for number 3, you probably want to chroot to /var/www/%u
One of the catches with SFTP chroot is that the target has to be owned by root and not writable by anyone else.  That does not apply to the files and subdirectories there, however, so you could have /var/www/%u/ owned by root and /var/www/%u/www/ owned by the user.   

As for number 2, as far as I know, SFTP requires system users.  But in addition to chroot + forcecommand, you can also set the user shell to /usr/sbin/nologin

---

