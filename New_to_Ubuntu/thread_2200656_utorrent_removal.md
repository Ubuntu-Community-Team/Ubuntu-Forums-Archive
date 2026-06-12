---
title: "utorrent removal"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by andrew58 on 2014-01-20
Dear folks,
By following this link 
[http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step](http://askubuntu.com/questions/104094/how-to-install-utorrent-step-by-step) or [http://www.liberiangeek.net/2012/01/install-utorrent-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2012/01/install-utorrent-in-ubuntu-11-10-oneiric-ocelot/)
I installed the utorrent in my firefox web browser but this is not working for some reason. So that's not the problem. The problem is i want to get rid of it completely from my web browser.

So i followed this link to get it out of my system but i couln't do so..
[http://ubuntuforums.org/showthread.php?t=1842951](http://ubuntuforums.org/showthread.php?t=1842951)

Now i am posting the output as directed by ubudog

abc@xyz-desktop:~$ ps ax | grep utserver
11972 pts/5    Sl+    0:09 utserver -settingspath /opt/utorrent-server-v3_0/
14173 pts/7    S+     0:00 grep --color=auto utserver
abc@xyz-desktop:~$ 


Plese help me find out this thing.

Thank you

---

### Post by ian-weisser on 2014-01-20
> **andrew58 said:**
> 
abc@xyz-desktop:~$ ps ax | grep utserver
[COLOR=#ff0000]**11972**[/COLOR] pts/5    Sl+    0:09 utserver -settingspath /opt/utorrent-server-v3_0/
14173 pts/7    S+     0:00 grep --color=auto utserver

To stop the current utserver:
```
$ kill 11972
```

To delete utserver from your system permanently:
```
$ which utserver     # Find out where the application is located
/some/path/to/utserver

$ sudo rm /some/path/to/utserver    # Delete the application
```

---

