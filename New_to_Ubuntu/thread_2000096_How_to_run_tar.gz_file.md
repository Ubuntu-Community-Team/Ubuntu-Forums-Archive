---
title: "How to run tar.gz file?"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by rafsuntaskin on 2012-06-09
I have downloaded teamviewer.tar.gz   it is a executable file... but I am unable to run it..........pls help..

I tried  sudo apt-get install teamviewer but it was unable to locate the package though it is in HOme directory

---

### Post by codemaniac on 2012-06-09
Just untar the file and see what are the contents inside the tar.gz .
There might be some README or INSTALL file that can contain the installation steps .

```
tar -xvzf teamviewer.tar.gz
```

---

### Post by mapes12 on 2012-06-09
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by zombifier25 on 2012-06-09
Extract the package to your home folder (right click the package and choose "Extract Here", or use the command line method like codemaniac posted) Then when you want to run teamviewer, run this command:
```
~/teamviewer7/teamviewer
```
NOTE: There's a .deb package on their homepage. You better use that so that it's integrated into the system, no need to type the command.

---

### Post by nampat on 2012-06-09
If you are using Ubuntu, you could download .deb file: [http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb) )for 32-bit Ubuntu. There is 64-bit deb also available on their page.

---

### Post by Gone fishing on 2012-06-09
Just had a look at teamviewer and it is a remote access program. Ubuntu has  alternatives in the repositories for example VNC.

You may need to install nothing as remote desktop client will allow connections via VNC, SSH. SFTP and RDP and Desktop sharing can allow others to connect to your desktop.

---

### Post by mapes12 on 2012-06-09
Just read through the Teamviewer documentation. It says that the remote client you are looking to support needs to download and exceute **Teamviewer QuickSupport**. I can see the download for windoze and Mac but not Linux? So how would I help out someone with a Linux machine?

I've been looking for something like this for ages....

---

### Post by ibbill on 2012-06-09
I am running Ubuntu 64 bit. Person I helped just downloaded the regular team viewer not sure what quick support is.

It took a while to download the 64 bit but it works fine for myself and my friend.

---

### Post by rafsuntaskin on 2012-06-09
> **zombifier25 said:**
> Extract the package to your home folder (right click the package and choose "Extract Here", or use the command line method like codemaniac posted) Then when you want to run teamviewer, run this command:
```
~/teamviewer7/teamviewer
```NOTE: There's a .deb package on their homepage. You better use that so that it's integrated into the system, no need to type the command.
Thanks every one  :D....
Thanks Zombi it worked as you said , I tried the .deb file too but It was not installing Or I just don't know what to .deb files ???

---

### Post by codemaniac on 2012-06-09
in order to install .deb packages . just open up a terminal , brouse to the location where your .deb file is kept and run the below command .

```
dpkg -i filename.deb
```

Or simply double clicking the .deb file would do .

---

### Post by zombifier25 on 2012-06-09
Double clicking the .deb file should open up Ubuntu Software Center for you to install the package.
EDIT: Ninja'd!

---

