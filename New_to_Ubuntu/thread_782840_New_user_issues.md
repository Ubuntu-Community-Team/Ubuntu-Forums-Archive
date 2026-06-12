---
title: "New user issues"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Flash-genie on 2008-05-05
I decided to dive into Ubuntu to see if it's really as good as various people have told me, and browsing such phrases as "Ubuntu is stabile, Ubuntu is easy". I do a lot of web design and development to pay my rent, so I thought this would be an interesting experience. 

I need (well don't exactly need but wouldn't want to do without) 3 things initially. 

1. I need my dual monitors to work. I have followed I don't know how many different posts trying to explain how it can be done (using a NVidia graphic card). Using 7.10 there is even a Screen & Graphics Preference (or something like that), which works fine when mirroring the primary monitor, but extending it makes the interface in the primary window too big for the monitor so I have to go to an edge of the screen to scroll up or down to get to the bars.

2. Isn't there a simple guide anywhere so that I can get my Intellipoint mouse buttons to work? All I want is mouse button 4 to take me back in Firefox. I've also followed various examples as stated in [http://ubuntuforums.org/showthread.php?t=28374](http://ubuntuforums.org/showthread.php?t=28374) to no avail.

3. I need to setup a LAMP system, ideally with SVN and Eclipse, I was hoping to find something that would help me to achieve this, but so far no joy. I followed some instructions to get apache, php and mysql which definately did something and even installed a apache directory, which contains a file that points to a var directory which contains a www directory...do I need FTP to upload files to there, from for example my desktop? I can't seem to move files there or even create them. Also how do I fire up apache, pointing a browser to [http://localhost](http://localhost) displays nothing as yet.

Thanks to anyone who can point me to some definitive material or help me further.

Taff

---

### Post by superprash2003 on 2008-05-05
try [http://127.0.0.1](http://127.0.0.1) instead.. you can use ftp to transfer files.. you could try installling proftpd and then install gproftpd (gui for proftpd).. or you could install samba.. its basically used for file sharing between windows pcs.. [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by T-Virus on 2008-05-05
Also try [http://127.0.0.2](http://127.0.0.2). I had my Apache default at this point.

---

### Post by Flash-genie on 2008-05-06
Thank you both for your replies. Once I get a little free time I'll go dance with the devil again :guitar:

I thought I could update files directly and see the results as they would be viewed on the server, similar to how I do it currently with XAMPP. Currently I browse to C:\xampp\htdocs\wherever and open up the file I want to change with an application, change something and can see directly under [http://localhost/wherever](http://localhost/wherever)

All the best,
Taff

---

### Post by hyper_ch on 2008-05-06
if you're the only user on the system that uses apache you might want to chown the default webfolder to your user so you have permissions to write to it:

```

sudo chown -R USER.USER /var/www

```
Of course replace USER with your username.

Apache should auto-start and same for mysql. Run those:
```

ps aux | grep apache
ps aux | grep mysql

```
They should return running apache / mysql processes.

Very likely php5 is not yet enabled on your system:
```

sudo a2enmod php5

```

As for accessing it. After you have chowned that folder, you can write with your user to it. If you want access from a different computer, then the simplest way to proceed is by ssh:
```

sudo apt-get install openssh-server
```

You can then use WinSCP from another windows computer to connect to your computer. from outside the lan you'll have to forward port 22 to your local one.

---

