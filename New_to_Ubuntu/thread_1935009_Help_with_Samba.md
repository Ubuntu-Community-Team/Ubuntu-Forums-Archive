---
title: "Help with Samba"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by giantslor on 2012-03-03
Running Lubuntu 11.10 here, wanting to share files with Windows 7  machines on a home WLAN. I followed exactly the setup instructions for  Samba here:

[http://ubuntuforums.org/showthread.php?t=1623346](http://ubuntuforums.org/showthread.php?t=1623346)

But my Lubuntu machine still doesn't show up under "Network" on the Windows machines. There must be some step(s) missing.

Also,  on Lubuntu I can access the Windows machines only by typing their IP  address. Using the computer name doesn't work. Also, typing "smb://"  shows me the "WORKGROUP" folder, but when I try to open that I get the  messages, "Failed to retrieve share list from server" and "The specified  location is not mounted."

What steps should I take?

---

### Post by linux6994 on 2012-03-03
What has worked for me is to add 'force user = yourmane' in the smb.conf file. open a terminal, sudo gedit /etc/samba/smb.conf then add the force user line just below the workgroup one. The log out and back in.

---

### Post by HermanAB on 2012-03-03
Howdy,

IMHO, Samba is best avoided.  Of all the ways to share files with a Windows machine it is the most difficult and annoying to install.

FTP is the simplest, OpenSSH is the securest, NFS is the easiest and Samba is the difficultest...

So, if your needs are simple, install vsftpd on Linux and FileZilla on Windows, or install FileZilla Server on Windows and use Nautilus to connect to it on Linux.

If you are serious about using Samba, then you need to read the documentation.  Buy the book or go to the project web site and start reading.

---

### Post by audiomick on 2012-03-03
You may find some help here.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Morbius1 on 2012-03-03
> But my Lubuntu machine still doesn't show up under "Network" on the Windows machines.Preliminary steps:
[1] Run the following command in lubuntu and count the number of characters:
```
hostname
```If it's 16 characters or more in length then your machine is invisible to the rest of the network.

[2] Change the order of how host names are resolved to ip addresses:

To do both:
Edit smb.conf as root ( I'm using gedit here because I don't know the default editor in Lubuntu ):
```
gksu gedit /etc/samba/smb.conf
```Then add the following line to the [global] section of smb.conf - right under the workgroup line to fix the hostname problem if there is one:
```
netbios name = something
```[COLOR=Blue]*something must be 15 characters or less in length*[/COLOR]

Still in gedit add another line under that one:
```
name resolve order = bcast host lmhosts wins
``` Save smb.conf and then restart samba services:
```
sudo service smbd restart
sudo service nmbd restart
```Note: Every time you restart samba services the network has a fit so wait a few minutes and see how far this advice got you.

---

### Post by NadirPoint on 2012-03-03
Samba is easily by far the best and easiest way to share files with Windows.  It integrates seamlessly and requires zero effort on the part of the Windows users accessing the Samba server by virtue of that seamless integration.  It just takes a correct configuration which BTW, is not too difficult either.

A few simple steps like Morbius suggests and you will be fine.

---

### Post by giantslor on 2012-03-04
Thank you to Morbius1 for fixing my problem, and to NadirPoint for persuading me to go with Morbius1's solution. Audiomick also provided an interesting link that I'm reading.

Great first experience with the Ubuntu community. Thanks, guys! :D

---

