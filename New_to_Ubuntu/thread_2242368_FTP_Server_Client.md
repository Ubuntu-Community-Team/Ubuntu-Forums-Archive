---
title: "FTP Server Client"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by bigpappajohn1984 on 2014-09-01
I had a Windows Box running FZ Server.  I recently discovered that FileZilla Server isn't supported in Ubuntu.  What is a good (free) FTP client that can be run in Ubuntu?  Relatively easy set-up as well since I am not to familiar with the Ubuntu/Linux Commands.

---

### Post by Lars Noodén on 2014-09-01
Are you sure you really want [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) on a server in 2014?  The FileZilla client (and Nautilus) support SFTP out of the box.  And unlike FTP it can be used for secure file transfers.  All you need on the server is the package  "openssh-server" and you can connect with SFTP.  

If you still really want an FTP server there is proftpd and vsftpd.

PS. Welcome.

---

### Post by bigpappajohn1984 on 2014-09-01
Hey thank you for that information!  Well here's the story from A - Z.  I have a DynDNS account which gave me a web address that I could send out giving access to FileZilla and grant certain user accounts access to view certain things. 

Like grandparents could view pictures etc etc.  That is why I went the FileZilla Server route as I have my router all set-up to port forward based on that.  It seems as if per your response ( and I apologize if I am not understanding correctly) that Ubuntu straight out the gate is capable of being used as FTP?  I just took a look at my about Ubuntu and it seems I am running Lucid Linux 10.04.04.

I tried to use command prompt to install the vsftpd but I get an error:
```

jo15765@jo15765-laptop:~$ sudo apt-get install vsftpd
[sudo] password for jo15765: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

---

### Post by nerdtron on 2014-09-01
Like Lars said. SFTP works out of the box on Ubuntu. Just direct port 22 (SSH) on your Ubuntu. Then let you parents use FileZilla client to connect to your Ubuntu.

Regarding your problem. It says there what command you should run.

---

### Post by bigpappajohn1984 on 2014-09-01
Does FTP work straight out the box or do I have to use SFTP?  From what I have read using SFTP would force the other users to use a FTP client and not be able to use web-based connections.

EDIT--
And please forgive me if I am misunderstanding.  Best of my understanding SFTP is Secure FTP which can only be accessed through an FTP application.  That is why I am wanting to only use FTP as it can be accessed through a web browswer.

---

### Post by nerdtron on 2014-09-01
I have tried SFTP using only Filezilla (or other sftp application) not sure if a browser can do it though.

---

### Post by bigpappajohn1984 on 2014-09-01
A browser is not capable of using SFTP - which is why I would like to mimic the behaviour of FileZilla Server in Ubuntu.  How could I go about doing this?

EDIT -
A standard browswer is not capable.  Firefox has an add-in (which the name escapes me) that will allow the use of SFTP but I was meaning a standard browser.

---

### Post by bigpappajohn1984 on 2014-09-01
And a further search of the forums turned up this which presents several nice alternatives!

[http://ubuntuforums.org/showthread.php?t=2143392](http://ubuntuforums.org/showthread.php?t=2143392)

---

### Post by sandyd on 2014-09-01
> **bigpappajohn1984 said:**
> Hey thank you for that information!  Well here's the story from A - Z.  I have a DynDNS account which gave me a web address that I could send out giving access to FileZilla and grant certain user accounts access to view certain things. 

Like grandparents could view pictures etc etc.  That is why I went the FileZilla Server route as I have my router all set-up to port forward based on that.  It seems as if per your response ( and I apologize if I am not understanding correctly) that Ubuntu straight out the gate is capable of being used as FTP?  I just took a look at my about Ubuntu and it seems I am running Lucid Linux 10.04.04.

I tried to use command prompt to install the vsftpd but I get an error:
```

jo15765@jo15765-laptop:~$ sudo apt-get install vsftpd
[sudo] password for jo15765: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

Also, please note that unless you are using the server edition of 10.04, 10.04 is no EOL and no longer supported.

---

