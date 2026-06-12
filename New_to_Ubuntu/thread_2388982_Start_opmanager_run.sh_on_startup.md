---
title: "Start opmanager run.sh on startup"
date: 2018-04-10
forum: New to Ubuntu
---

### Post by am.steen on 2018-04-10
Dear All

I have a shell file run.sh that works from inside its 
Folder only So **[COLOR=#ff0000]I have to go to its folder first befroe run it[/COLOR]**

cd /opt/OpManager/bin/
sudo sh run.sh

**[COLOR=#0000ff]Then run it -- it will run successfully [/COLOR]**

I need to run this shell file at startup

I try every thing but fail 

I work on ubuntu ver 17.10

Please help

---

### Post by monkeybrain20122 on 2018-04-10
[https://askubuntu.com/questions/290099/how-to-run-a-script-during-boot-as-root](https://askubuntu.com/questions/290099/how-to-run-a-script-during-boot-as-root)

---

### Post by am.steen on 2018-04-12
I try every thing on that link but nothing works

there are two points :-

1. **[COLOR=#ff0000]I am using ubuntu 17.10 server ( no GUI )[/COLOR]**
2. **[COLOR=#0000ff]The script run only from its folder /opt/OpManager/bin[/COLOR]**
    if try to run it from anywhere it failed 
    ( for example ===> sudo sh /opt/OpManager/bin/run.sh  this way failed )

Thanks in advance
Eng. Amgad

---

### Post by am.steen on 2018-04-17
Ok they send me another sh file and it works

For any one needed same issue follow this link:-

[https://pitstop.manageengine.com/portal/kb/articles/how-to-start-opmanager-as-service-in-systemd-linux-versions](https://pitstop.manageengine.com/portal/kb/articles/how-to-start-opmanager-as-service-in-systemd-linux-versions)

it is fron the same company

Thanks any way

Eng. Amgad

---

### Post by yancek on 2018-04-17
Another method which should work is an entry in crontab which will run the script on login:

 > !/bin/sh
@reboot /bin/sh /opt/OpManager/bin/run.sh

If that does not work, you may need to put the corrrect PATH in the script.

---

