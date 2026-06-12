---
title: "How to Share Files Over Network"
date: 2015-06-19
forum: New to Ubuntu
---

### Post by akash14 on 2015-06-19
is there way to share windows or Any Linux File System with Ubuntu machine on same wi-fi network? 

Sorry i am super dumb in linux, just joined.
Thank You In Advance :)

---

### Post by dino99 on 2015-06-19
this can be done via 'samba' : google around 'ubuntu sharing' to find many howtos & wikis

---

### Post by leunam12 on 2015-06-19
Open a terminal and type```
sudo apt-get update 
sudo apt-get install samba
```press enter after each line. Samba will either install or tell you that it is the latest version (meaning that it's installed already). Then set a password for your user in samba```
sudo smbpasswd -a *username*
```Replace username with your actual user name. After you restart to access a Windows shared folder open Nautilius and press CTRL+L and type ```
network:///
```press enter and you will see the Windows computer where the folders are shared. To share an Ubuntu folder follow the link below:

[http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7](http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7)

---

### Post by cariboo on 2015-06-19
Samba will be installed automagically it you just open nautilus (the file manager) and select Local network share. Just follow the prompts. There is a small bug in the process, you have to install libpam-smbpass manually. When asked to install it, open a terminal (Ctrl-t) and enter the following command:

```
sudo apt-get install libpam-smbpass
```

As a side note, to share files on a window system make sure smbclient is installed on your Ubuntu system.

---

### Post by akash14 on 2015-06-20
Thank You Dino99, leunam12, cariboo for helping me, thanks alot from heart :)

---

### Post by trag on 2015-06-25
Try Nitroshare
sudo add-apt-repository ppa:george-edison55/nitroshare

sudo apt-get update

sudo apt-get install nitroshare

---

### Post by nerdtron on 2015-06-25
Come on people, he's a noob, let's make our help as simple as possible, they could easily get scared on using the command line. Let's be gentle on our recommendations. (sorry i'm a little hungry right now so excuse me for my words)

You can use the public folder of Ubuntu. All GUI: [http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/](http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/)

---

### Post by HermanAB on 2015-06-26
Howdy,

The problem with Samba is that it is immensely complicated.  The Samba manual is 2 inches thick - I actually read it - and since then I do my best to avoid using Samba.  MS made a total mess of that protocol over the decades.

That being said, the easiest way to share files is with an even older protocol that goes back to the 1970s, called FTP.  You can get FileZilla Server and install it on Windows, then you can use pretty much any file browser from Linux to access that server.

[https://filezilla-project.org/download.php?type=server](https://filezilla-project.org/download.php?type=server)

On the Linux machine, open a file or web browser and either type [ftp://ip.add.re.ss](ftp://ip.add.re.ss) or look in the File menu for 'Connect to Server' or some such and Bob's your Uncle.

---

### Post by lzeimet on 2015-06-26
I just did all of this and I documented it in the case that someone out there might need it.  Only difference is you wont need to follow all of the steps unless the folder you want to share is not on the local drive.  The folder I wanted to share was on a 3TB HDD that I use to house all my movies.



**SettingSamba up to share a folder on another hard drive**
**UBUNTU14.04**


If you don't already have Samba installed please do so with thefollowing command


**Sudo apt-getinstall samba**


Now that you have samba installed you can create the shared folder. For this example, I am gonna show you what I had to do to get it towork properly.


**Sudo nano/etc/samba/smb.conf**


Scroll all the way to the bottom and insert the following:



[LIST]
[*]
[*]**[Share] **
[LIST]
[*]
[*]        (This will be the name of the folder you are sharing.. if you want        it to be something else, input something different
[/LIST]
[/LIST]



[LIST]
[*]
[*]**path =     /media/coolbreeze/0f51dec1-5f40-4401-8a6e-e85c5624902a/home/lucas/Videos**
[LIST]
[*]
[*]        I had to use the UUID of that particular drive, you can find that        by going to Files, right-clicking on the hard drive that has the        file path you wish to share and selecting properties.
[/LIST]
[/LIST]



[LIST]
[*]
[*]**valid users    = root**
[LIST]
[*]
[*]        You can make your user what ever you want it to be just don't        forget it
[/LIST]
[/LIST]



[LIST]
[*]
[*]**guest ok =    no**
[/LIST]



[LIST]
[*]
[*]**writable =    yes**
[/LIST]



[LIST]
[*]
[*]**browsable =    yes**
[/LIST]


Now do the following:

[LIST]
[*]
[*]**CTRL+X**
[*]Enter    **'Y'**
[*]Hit    **ENTER**
[/LIST]


Now you want to add your '**valid user'** to samba share andassign it a password.  Again I will use my example



[LIST]
[*]
[*]**sudo    smbpasswd -a root**
[*]    New smb password: *******
[*]    re-enter password: *******
[/LIST]


Now you should be all set.

---

### Post by GrouchyGaijin on 2015-06-26
The _**easiest**_ way is Dropbox.

---

