---
title: "Ubuntu and GNOME3"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by ksrsubramanian on 2012-01-12
Hi all,
       I had my ubuntu 11.04 natty going good. I installed gnome-tweak-tool and some dependencies.I played with themes and stuffs. It was working well. But there was one problem, the desktop notifications like new mail,chat notifications of ubuntu were gone. So in the course of getting it back, i accidentally uninstalled some librarys that send nofications to daemon(libnotify lik dat..) when i rebooted my system the login screen appeared but i couldnt login it showed " COuldnt update .IEC authority'" close. 

I searched some threads. I ran some commands thru terminal. But nothing paid off. I also removed gnome shell using the command "sudo apt-get autoremove gnome-shell" also the gnome session "sudo apt-get autoremove gnome-session" so i didn even get the log in screen thereafter. I could ly notice a change the path it was showing for coulnt update .IEC authority changed in that dialog box appearing from "/home/usr/" to "/var/lib/gdm/".....this was due to the commands i ran. Also once in the course i once enabled autologin for the user  using the command "sudo nano /etc/gdm/custom.conf" later i disabled the autologin using the same command.

Also in the course i used nmcli command to connect my usb modem to the network.It paid off once thru which i reinstalled the gnome-shell( i eventually removed it as said b4). Now the available connections are not shown by the command "nmcli con"...but my usb modem is shown in the list shown by "nmcli dev"..... now i couldn able to connect to the inenet too....


The Bottom line is when i boot into linux a black screen appears and suddenly a dialog box stating "could not update .IECauthority  in /var/lib/gdm/"..... but the locate command shows two locations of the file one in /home/usr/.... other in /var/lib/gdm/....


So what i am supposed to do now.


Thanks,
Sundar

---

### Post by androssofer on 2012-01-12
> **ksrsubramanian said:**
> Hi all,
       I had my ubuntu 11.04 natty going good. I installed gnome-tweak-tool and some dependencies.I played with themes and stuffs. It was working well. But there was one problem, the desktop notifications like new mail,chat notifications of ubuntu were gone. So in the course of getting it back, i accidentally uninstalled some librarys that send nofications to daemon(libnotify lik dat..) when i rebooted my system the login screen appeared but i couldnt login it showed " COuldnt update .IEC authority'" close. 

I searched some threads. I ran some commands thru terminal. But nothing paid off. I also removed gnome shell using the command "sudo apt-get autoremove gnome-shell" also the gnome session "sudo apt-get autoremove gnome-session" so i didn even get the log in screen thereafter. I could ly notice a change the path it was showing for coulnt update .IEC authority changed in that dialog box appearing from "/home/usr/" to "/var/lib/gdm/".....this was due to the commands i ran. Also once in the course i once enabled autologin for the user  using the command "sudo nano /etc/gdm/custom.conf" later i disabled the autologin using the same command.

Also in the course i used nmcli command to connect my usb modem to the network.It paid off once thru which i reinstalled the gnome-shell( i eventually removed it as said b4). Now the available connections are not shown by the command "nmcli con"...but my usb modem is shown in the list shown by "nmcli dev"..... now i couldn able to connect to the inenet too....


The Bottom line is when i boot into linux a black screen appears and suddenly a dialog box stating "could not update .IECauthority  in /var/lib/gdm/"..... but the locate command shows two locations of the file one in /home/usr/.... other in /var/lib/gdm/....


So what i am supposed to do now.


Thanks,
Sundar


sounds like quite the pickle. Unfortunately I have no idea how you would go about fixing this.. there is so much to it!

what i would do is get an external hard drive and a live cd/usb back up my stuff and re-install..

---

### Post by ksrsubramanian on 2012-01-12
:( :( :(............but my terminal is still ALIVE!!!??

---

### Post by ksrsubramanian on 2012-02-01
Hi ,
          Problem solved . I successfully upgraded my ubuntu 11.04 to 11.10 from an offline upgrade cd....

Thanks all

---

