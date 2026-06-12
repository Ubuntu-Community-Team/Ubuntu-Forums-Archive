---
title: "launching QWindow at unbuntu login screen."
date: 2010-06-10
forum: Programming Talk
---

### Post by alibaba163 on 2010-06-10
Hello everyone,
               I have a daemon that writes log of current time five time at location "/opt/NetSupport/NetSupportManager/file.log".

I want my daemon to launch a window at ubuntu login screen(this is the screen where ubuntu takes username and password to log in). Since by this time gdm(gnome display manager) will be available so my daemon(writeLog) should be able to launch an xwindow app.

Please see the attached program that runs as daemon and writes logs. You will have to untar the file and go to daemon folder and then run

sudo ./install

after that the daemon will write logs in /opt/NetSupport/NetSupportManager/file.log on system reboot(I am running this on UBUNTU 8.10 gnome)
 
So my question is HOW CAN I GET THIS DAEMON TO DO EITHER OF THESE TWO THING

1. To launch an  application that can display a simple window (lets say QWindow) at login screen. please be aware that I want to display this window at login screen NOT after user has logged.


                 OR

2. Daemon can launch a GUI mode of itself so that it can display a window at login screen.


Any help will be really appreciated.

Regards,

Sheikh.

---

