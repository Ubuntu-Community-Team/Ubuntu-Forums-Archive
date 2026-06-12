---
title: "FTP Client?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by JohnTheMacGeek on 2008-06-23
Are there any FTP clients available for Ubuntu? Thanks!

---

### Post by cpetercarter on 2008-06-23
I use gFTP (downloadable from Synaptic). You can also get the FireFTP extension for Firefox, which is really good.

---

### Post by Zulu-Zeffir on 2008-06-23
There is ftp in ubuntu already.
Open shell and type ftp.

If you want a gui client then check here:
[http://gftp.seul.org/]("http://gftp.seul.org/")

aptitude install gftp

---

### Post by JohnTheMacGeek on 2008-06-24
> **Zulu-Zeffir said:**
> There is ftp in ubuntu already.
Open shell and type ftp.

If you want a gui client then check here:
[http://gftp.seul.org/]("http://gftp.seul.org/")

aptitude install gftpWhich version of gftp would I download? Does Ubuntu 8.04 come with GTK? I'm a little confused about this. Thanks for the help!

---

### Post by Zulu-Zeffir on 2008-06-24
Just open a terminal and run the following:
sudo aptitude install gftp

This should get you the most current stable release installed and ready to go.

---

### Post by dca on 2008-06-24
...or click on the 'Add/Remove Software' under 'Applications' menu and enter 'gftp' in the search...
 
...once installed it should show up under your 'Internet' sub-menu under 'Applications.

---

### Post by Golem XIV on 2008-06-24
There's also FileZilla, in the repos:
```
sudo apt-get install filezilla
```

---

### Post by sujoy on 2008-06-24
ncftp, lftp, gftp (gui) ... lots of choice. just search in synaptic for ftp clients

---

### Post by mcduck on 2008-06-24
Just go to Places-menu and use the "connect to server" or whatever it's called. Your FTP location will be mounted to your desktop so you can just drag&drop files there..

If you need more options & tools, I recommend gFTP.

---

### Post by JohnTheMacGeek on 2008-06-24
> **dca said:**
> ...or click on the 'Add/Remove Software' under 'Applications' menu and enter 'gftp' in the search...
 
...once installed it should show up under your 'Internet' sub-menu under 'Applications.Thanks! That worked perfectly and the application also works great!

---

### Post by whitethorn on 2008-06-24
> **cpetercarter said:**
> I use gFTP (downloadable from Synaptic). You can also get the FireFTP extension for Firefox, which is really good.
You can also use Filezilla, ftp client from mozilla.  You can get it in 
Synaptic

---

