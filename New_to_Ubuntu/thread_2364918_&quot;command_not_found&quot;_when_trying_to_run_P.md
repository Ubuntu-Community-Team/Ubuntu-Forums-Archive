---
title: "&quot;command not found&quot; when trying to run Powerbroker Idenity Service"
date: 2017-06-29
forum: New to Ubuntu
---

### Post by tonyclifton on 2017-06-29
Hello, I'm a Noob so this is prob an easy answer. At the Terminal i installed PBIS(Allows for Active directory authentication)It installs no problem.
I'm still in the Downloads folder and when I run the command to launch the program(domainjoin-gui) I get an [COLOR=#ff0000]"command not found" error. [/COLOR][COLOR=#000000]Do I need to be in a different
folder to run this? The instructions I'm using is running the command from the Download directory!!!


Thanks
[/COLOR]

---

### Post by tonyclifton on 2017-06-29
I got it working~~~
:)

---

### Post by yancek on 2017-06-29
I'm not familiar with the software.  Did you get it from the Ubuntu repositories or download it from another site?  If you downloaded it and extracted it, you should have some king of README file.  Doing an online search brings up quite a few links.  From what I have found, it is apparently referred to as 'pbis' and is in the /opt directory so try that or try in a terminal which pbis or whereis pbis.

---

### Post by tonyclifton on 2017-06-29
I downloaded it from GitHub, yes it's 'pbis' which replaced Likewise which allows you to connect to a Windows Domain. After doing some more research I found that I had to edit the avahi-daemon.conf file and "Presto" it works now.
Thanks for replying back!!!

---

