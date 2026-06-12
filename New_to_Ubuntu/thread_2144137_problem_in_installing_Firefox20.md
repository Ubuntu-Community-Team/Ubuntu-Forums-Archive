---
title: "problem in installing Firefox20"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by tusharkoshti on 2013-05-11
Hi frinds !
I m a newcomer in Linux world. 
I have just installed Ubuntu 13.04. 
On some website I read about Firefox20. So I want to upgrade my firefox. But in help there is 
one step in that I have to move firefox directory ( which actually came after extracting file firefox-21.ob7.tar.bz2)
to /opt folder. For that , 1st if u have previous firefox version remove it by following command :

sudo rm -r /opt/firefox

and then move firefox directory to /opt with follwing command :

sudo mv firefox /opt/firefox20

But in both the cases I got error like there is no such file or directory. 

So I tried manually but I think there is no copy/cut  paste option in /opt. ( I saw /opt properties and got 
following message : 
" U r not the owner so u can't change the permission " 

So can anyone help me in installing firefox20 ? 
Thank u in advance.

---

### Post by hakermania on 2013-05-11
Hi tusharkoshti!

Can you please link us to the page where you get your information about installing firefox 20?

Also, please try extracting  firefox-21.ob7.tar.bz2 (also, it says firefox **21**, which version are you finally trying to install?) in your home folder, try opening a terminal through Ctrl+Alt+T and then give the second command,
```
sudo mv firefox /opt/firefox20
```

---

### Post by Impavidus on 2013-05-11
Firefox 20 is the current version, it should be installed by default (if it wasn't yet in the disk image (I don't remember when FF20 came out) you should get an update automatically). The firefox-21.ob7.tar.bz2 archive contains firefox 21, wich is the beta version. So if you want firefox 20 you don't have to do anything. If you want the beta version, you'll have to install 21.

That page that told you about FF20 may have been outdated, written when FF20 was still in beta.

---

### Post by gordintoronto on 2013-05-11
You might have saved yourself a lot of trouble by running Firefox and clicking Help/About.

---

### Post by tusharkoshti on 2013-05-12
Hi , 
I tried to extract but error is  " U dont have the right to extract this archieve .... " 
I am giving the link : 

[URL="http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint"]http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint

[COLOR=#000000]I think link is outdated as per [/COLOR][/URL][[COLOR=#000000]"Impavidus"[/COLOR]]("http://ubuntuforums.org/member.php?u=1417721")[URL="http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint"]saying. 
[/URL]

---

### Post by zombifier25 on 2013-05-12
The package provided on Mozilla's website contains the entire prepackaged binary of Firefox, like a portable version. You needn't, and shouldn't use it. Unless you are using an unsupported Ubuntu version (which means you need to upgrade ASAP), Firefox will be upgraded automatically by Ubuntu, and you don't need to do anything more.

---

### Post by tusharkoshti on 2013-05-12
Thank you Zombifier25  :)

---

