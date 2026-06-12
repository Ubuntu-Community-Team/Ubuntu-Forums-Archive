---
title: "Remote administration of a Ubuntu system form another Ubuntu system."
date: 2011-09-15
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-09-15
Hello!

I was wondering whether we can administrator any Linux system like Ubuntu from another Ubuntu system sitting anywhere across the world?

I have heard about webmin doing the perfect job, but only on localhost?, not sure

If there is any possibility, please share your views!

---

### Post by Azdour on 2011-09-15
Hi,

Webmin can definately be used remotely:

> Webmin is a web-based interface for system administration for Unix. Using any modern web browser, you can setup user accounts, Apache, DNS, file sharing and much more. Webmin removes the need to manually edit Unix configuration files like /etc/passwd, and **lets you manage a system from the console or remotely**.

---

### Post by haqking on 2011-09-15
> **amityadav9314 said:**
> Hello!

I was wondering whether we can administrator any Linux system like Ubuntu from another Ubuntu system sitting anywhere across the world?

I have heard about webmin doing the perfect job, but only on localhost?, not sure

If there is any possibility, please share your views!


SSH...best and most universal tool IMO and the mainstay of Linux remote administration see here for SSH [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)

see here for webmin [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin) and here [http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/](http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/)

---

### Post by dfarrell07 on 2011-09-15
If you are willing or wanting to learn lots about Ubuntu and Unix commands in general, SSH is your answer. You will get very familiar with the terminal and the underlying, interesting parts of Ubuntu. Overall, I recommend SSH. 

If you don't want to deal with terminal input exclusively, you could run X over SSH, and have the typical GUI to work with. Here is a tutorial: [http://bit.ly/qHynWL](http://bit.ly/qHynWL)

Finally, if you are mostly doing file management, you can setup files on the remote computer, like the home folder of the user you care about, to be mounted on your local PC. It is just like having another file on your local system, but all of that info is actually being transmitted via SSH from the remote.

---

### Post by haqking on 2011-09-15
> **dfarrell07 said:**
> If you are willing or wanting to learn lots about Ubuntu and Unix commands in general, SSH is your answer. You will get very familiar with the terminal and the underlying, interesting parts of Ubuntu. Overall, I recommend SSH. 

If you don't want to deal with terminal input exclusively, you could run X over SSH, and have the typical GUI to work with. Here is a tutorial: [http://bit.ly/qHynWL](http://bit.ly/qHynWL)

Finally, if you are mostly doing file management, you can setup files on the remote computer, like the home folder of the user you care about, to be mounted on your local PC. It is just like having another file on your local system, but all of that info is actually being transmitted via SSH from the remote.


That link ssh for X over SSH using vnc.  If you want to use ssh -X beware that you may need to set up X forwarding. And also across a WAN it can be sometimes pretty slow even though the X loops back.

---

### Post by gigaferz on 2011-09-15
my two cents

ultravnc

teamviewer

both are really easy to set up and use and i think they are secure.

ive had better performance with teamviewer

---

### Post by candtalan on 2011-09-15
+1 for Teamviewer
Sadly it is not Libre software, it is proprietary, but it is no charge for non commercial use. It is advertised as secure, encrypted.

I have even arranged a remote user to run a Live Ubuntu session, install Teamviewer, then I can control the remote live session and prepare and start a remote install. The presence of Teamviewer did not seem to disturb things, however, once the install was well under way I exited Teamviewer just to be sure. It worked well. 
I am in UK and I administer a friend's Ubuntu in France while they are on the phone to me.

---

### Post by haqking on 2011-09-15
Just a point to note, that things like teamviewer have there place and are invaluable for Desktop Support remotely, but for remote administration of say a Ubuntu server then SSH would be preferred as the remote system is llikely to not be runnnig a Desktop Environment.

Not to mention it goes through the teamviewer servers, and for corporate environments where you need to administer your E-commerce web server remotely SSH would be the tool IMO.

remote administration usually refers to this, as not many people remotely administer a desktop system, they may provide desktop support to it though.

---

### Post by Dangertux on 2011-09-15
Umm... I'm not sure you'd want either team viewer or vnc on a production system.

I would stick with SSH. Just my 2 cents.

---

