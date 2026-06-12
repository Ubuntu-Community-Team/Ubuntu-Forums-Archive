---
title: "shared folder"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by flex567 on 2015-08-10
I have 2 lubuntu computers connected to the same router. How can I create shared folder on those 2 computers?

---

### Post by HermanAB on 2015-08-10
Umpteen ways:
FTP, SSH, WebDAV, NFS, SAMBA, Netcat...

The easiest way is to install an anonymous FTP server on one or the other.  The Ad Hoc way is to copy files with SSH and scp, or even Netcat. The most complicated and difficult way is the one that everybody else will recommend, SAMBA.

---

### Post by flex567 on 2015-08-10
where can I get anonymous FTP and how can I set it up ?

---

### Post by leunam12 on 2015-08-10
I thought it was just a matter of right-clicking the folder and select share option. In case samba is not installed run: ```
sudo apt-get update
sudo apt-get install samba
sudo smbpasswd -a <username>
``` where <username> is your actual user name. Then try sharing again.

Using this method I can share with my phone, my tablet, Windows computers and Ubuntu computers.

---

### Post by flex567 on 2015-08-11
what about the FTP way ?

---

### Post by nerdtron on 2015-08-11
hhhmmmm..SFTP

1. Install ssh-server on both machines.
```
 sudo apt-get install openssh-server 
```
2. On your file manager (from one of the machine), type on the address bar: sftp://IPaddress.x.x
** That is the IP address of the other machine you want to connect to. You will be asked for the username and password of the remote machine.

If in case, you have an error like "Sorry, could not display all the contents of “vmalep (sftp)”: The   specified location is not supported" then also install the gvfs package on both namchine.
```
 
sudo apt-get install gvfs-backends
```

---

### Post by bab1 on 2015-08-11
> **flex567 said:**
> what about the FTP way ?
It helps if you can help yourself.  

Here is a google search using the keywords " *[anonymous ftp server ubuntu]("https://www.google.com/search?q=annonomous+ftp+server+ununtu&btnG=Go!&gws_rd=ssl#q=anonymous+ftp+server+ubuntu")*".

The first listing is the Official Ubuntu Documentation for FTP servers.  ;-)

---

