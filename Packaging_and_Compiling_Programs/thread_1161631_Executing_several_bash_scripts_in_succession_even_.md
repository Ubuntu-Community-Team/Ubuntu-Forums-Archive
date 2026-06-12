---
title: "Executing several bash scripts in succession even after reboot"
date: 2009-05-16
forum: Packaging and Compiling Programs
---

### Post by fantasyland on 2009-05-16
Hi,

I am new to shell programming. I am trying to automate setting up a network using several scripts. Some of the scripts require to reboot in order to continue with the setup. Is it possible to enter another script as soon as the system reboots. Also, if the last line of the script is bash "anotherscript.sh" will "anotherscript.sh" start up ? 

Thanks in advance.

---

### Post by lswb on 2009-05-16
Not sure if this is what you want. ubuntu and many other linux distributions will run a script "/etc/rc.local" after all /etc/init.d boot scripts are finished. By calling your script from this file (or putting the code in /etc/rc/local itself) you can have your script run upon reboot. You could create a file that maintains the state of your installation process across reboots, and have your script read the file and run the appropriate code. Remember to have proper owner and permissions on your scripts.

As for your 2nd question, the short answer is yes. Actually, after anotherscript.sh finishes, execution will return to calling script. To prevent the return you can call the line with exec, i.e. "exec bash anotherscript.sh"

FYI, if you chmod +x a script and have #!/bin/bash as the first line, it is not necessary to call it as "bash script", it can be directly invoked by it's name.

Here is a really good bash tutorial you may be interested in:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

There is also an older version of this guide in the ubuntu repositories. Or for downloadable version or other guides on the same site: [http://tldp.org/guides.html](http://tldp.org/guides.html)

---

### Post by fantasyland on 2009-05-17
Thanks so much lswb. Your solution seems perfect.

---

