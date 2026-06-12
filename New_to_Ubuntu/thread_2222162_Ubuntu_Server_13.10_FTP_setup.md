---
title: "Ubuntu Server 13.10 FTP setup?"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by M_de_Luis on 2014-05-05
Hi,

Need some help FTPing into my /var/www/ apache2 webserver content directory:

Have a single user with a home directory that I can happily FTP files up to and down from. Would like to be able to upload and download files from the apache2 server content directory /var/www/, but at present can only retrieve files from there?

TIA,
M

---

### Post by M_de_Luis on 2014-05-05
/var/www drwxr-xr-x root root
/var/www/index.htm -rw-r--r-- root root
/home/username drwxr-xr-x username username

---

### Post by M_de_Luis on 2014-05-05
Okay, so if I change the /var/www directory permissions to drwxr-xrwx, then I can upload files to the apache2 content directory as my 'username' user, but that isn't what I want, is it - world writable webserver content root, I mean?

---

### Post by M_de_Luis on 2014-05-05
Well, no. Although I might be able to write the files to a world readable web content directory as my 'username' user, the webserver won't serve them as they now belong to a different user with constrained permissions:

/var/www/index.php -rw------- username username

????

---

### Post by jdeca57 on 2014-05-05
Sorry, but what I'm missing in all of this is the ftp server. Something like [http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux) but If your question is how to copy files on a single computer from my home directory and back then there are solutions. Personally I prefer mc but that's an acquired taste.

---

### Post by Lars Noodén on 2014-05-05
If you are the only user of that machine then you can just take ownership of the directories in question.

```

sudo chown -R mdeluis /var/www/

```

If you are sharing access, then you want to use groups.  

```

sudo addgroup webmasters

sudo gpasswd --add mdeluis webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs,o=rx "{}" \;

sudo find /var/www -type f -exec chmod g=rws,o=r "{}" \;

```

Also, did you really mean [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) or did you mean SFTP?  The former should not be used any more except in certain edge cases.  The latter is built in to the package openssh-server and needs no further configuration for basic use.

---

### Post by M_de_Luis on 2014-05-05
Thanks jdeca57.

Yep, Midnight Commander is a real blessing for file management on text based console systems. Great tip for anyone starting out with just a shell.

I'm trying to upload and files to a server on my private LAN, using the file sync utility of a very old copy of Dreamweaver. It doesn't allow file or directory permissions to be manipulated remotely, so that's something I also have to get right from the get go.

Eeek!

---

### Post by M_de_Luis on 2014-05-05
Ah, great. Thanks, Lars.

Yes, FTP is way insecure, but this is only being used to load a server on a private network.

Okay, I just take ownership of the /var/www directory as you have suggested. How then do I get the permissions of files FTP uploaded to the webserver content directory to automatically adopt a certain pattern that the webserver can distribute? My old copy of Dreamweaver drops them off as -rw-------, but I'm thinking a world readable file would be more servable? Something like -rw-r--r-- maybe?

---

### Post by Lars Noodén on 2014-05-05
Can you set the umask differently for Dreamweaver?

---

### Post by M_de_Luis on 2014-05-05
Thanks, Lars. Evidently no, as my 2000 copy of Ultradev 4 doesn't understand permissions, however I can set the umask to 022 in the setup for the FTP server vsftpd. That fixes all but one of my problems tonight, the last one being unrelated.

Great work, Lars. Couldn't have gotten it anytime soon without your help.

Thanks!

---

### Post by M_de_Luis on 2014-05-05
Hmm, curious...

My apache2 configuration allows [http://192.168.0.5/phpinfo.php](http://192.168.0.5/phpinfo.php) to be retrieved happily enough, but refuses [http://192.168.0.5/index.php](http://192.168.0.5/index.php) citing '500 Internal Server Error'. Oddly it will retrieve that same index file when it's referenced as just [http://192.168.0.5/]("http://192.168.0.5/index.php")

??

--------------------------------------------------

Oops - nope, that's a scripting error, not an apache2 problem. I'm all sorted out. Thanks everyone.

M. :-)

---

