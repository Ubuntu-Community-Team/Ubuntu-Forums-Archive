---
title: "How-To: Install Nessus 3 and Nessus Client in Breezy."
date: 2006-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by bjweeks on 2006-02-22
Nessus 3 is now closed source so we have to install from a .deb but the client is still opensource.

To download Nessus 3 you must regester on there site and give your name and e-mail if you don't want to you can sill use nessus 2 in the repoes.

Ok, lets start by downloading Nessus 3.

[http://www.nessus.org/download/](http://www.nessus.org/download/)



Regester and download the deb file to your home directory. Use a real email cuase you need the serial that is emailed.


Nessus depends on openssl so lets install that first.

```

      sudo apt-get update
      sudo apt-get install openssl

```

Now to install it.

```

      sudo dpkg -i Nessus-3.0.1-debian3_i386.deb

```

Use the code you got emailed to register it.

```

      sudo /opt/nessus/bin/nessus-fetch --register *your code here*    

```

Add the admin user with pass auth and no rules

```

      sudo /opt/nessus/sbin/nessus-add-first-user

```

Start the nessus server.

```

      sudo /etc/init.d/nessusd start

```

The nessus server is now started and running so you can use the the windows client or another linux box. 

If you want to install the client on the same box as the server keep reading.


Download the client tarball to your home directory.

[http://www.nessus.org/download/](http://www.nessus.org/download/)

Before we build it we need some packages.

```

      sudo apt-get update
      sudo apt-get install build-essential libssl-dev libz-dev libgtk2.0-dev

```
Extract it.

```

      tar -xzf NessusClient-1.0.0.RC4.tar.gz

```

cd into its directory.

```

      cd NessusClient-1.0.0.RC4

```

```

      ./configure
      make
      sudo make install

```

Nessus client is now installed to run it

```

      NessusClient

```

---

### Post by Monoman on 2006-02-25
nice thanks!

---

### Post by EvilAngel on 2006-03-07
Thanks a lot for this great HowTo.

I just have a problem, during the installation, I can't download the plugins!
> ****@mojito:~$ sudo /opt/nessus/sbin/nessus-update-plugins
****@mojito:~$It just waits and then I have the shell again


Any idea ?

Thanks

---

### Post by flummoxed on 2006-03-07
What is the point of nessus? It checks your system for vulnerabilities?

---

### Post by bjweeks on 2006-03-10
[QUOTE=flummoxed]What is the point of nessus? It checks your system for vulnerabilities?[/QUOTE]

Yes, you can get more info on there [Website.]("http://www.nessus.org/")

---

### Post by Slugger on 2006-03-10
Nice thanks

---

### Post by bjweeks on 2006-03-10
[QUOTE=EvilAngel]Thanks a lot for this great HowTo.

I just have a problem, during the installation, I can't download the plugins!
It just waits and then I have the shell again


Any idea ?

Thanks[/QUOTE]

Thats it what is ment to happen, your good.:D

---

### Post by wokka on 2006-05-02
When running the **./configure **I receive the following message;

**Configure : error : libz is needed.**

I have been searching the package manager and cannot find anything. Does anyone know the exact package is required, and where to find it?

---

### Post by rainchild on 2006-09-28
nice and sweet!! what about the configuration part with the client and the SSL certs. If I'm successful I'll contribute the configuration.

---

### Post by arsui on 2007-08-11
Thks your how to

when i install all and start the nessus , things happen like below

```
sudo /etc/init.d/nessusd start
$Starting Nessus : bind() failed : Address already in use
.
```

could you tell me what happen? and when i edit the desktop file like 

[Desktop Entry]
Name=Nessuse
Comment=Nessus
Exec=nessus
Icon=/usr/share/pixmaps/nessus.xpm
Terminal=false
Type=Application
Categories=Application;System;

it doesn't work, it tips not the nessus file

---

### Post by jdownloader.com on 2008-03-08
When I try to install it, it gives me this;

nessus depends on libssl0.9.7 (>= 0.9.7e); however:
  Package libssl0.9.7 is not installed.
dpkg: error processing nessus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nessus

and I got libssl.0.9.8 installed and i have symbolic links to libssl.so.0.9.7 and still it doesn't work.... any tip is welcome.

---

### Post by trehune on 2008-03-12
Hi,

If you download the 3.2.0 version that available if you click the link in the e-mail you received from Nessus, it will work with libssl.0.9.8.

Nessus-3.2.0-debian4_i386.deb

Regards,
Tomas

---

### Post by hackertarget on 2008-03-31
> **arsui said:**
> Thks your how to

when i install all and start the nessus , things happen like below

```
sudo /etc/init.d/nessusd start
$Starting Nessus : bind() failed : Address already in use
.
```



You will probably find that Nessus is already running.

ps -ef | grep nessusd

Hence it is already using the port (usually 1241)

netstat -an | grep 1241

Nessus is a world class vulnerability scanner. Good for scanning your server for security holes.

---

### Post by hallve_revera on 2009-05-26
hii
i have a lil prob here
im a newbie so i do not now how to connect to nessus server
i followed all steps in ur tutor without missing anything
what should i fill in the host box to connect to nessus server...???

---

