---
title: "printer sharing so windoze clients can print"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by scwinn on 2008-08-31
How can I set it up so that my LINUX desktop can share its printer with other computers (all Windows xp) on my home network.:popcorn:

---

### Post by ggaaron on 2008-08-31
'localhost:631' in your browser, add a printer (if you haven't already), administration->Share published printers connected to this system. Now go to printers, select your printer, copy path from your browser, use it as path to network printer/external printer or something on Windows.

---

### Post by InfinityCircuit on 2008-08-31
```
sudo apt-get install samba
```

This will allow your computer to act as a samba server.  Then go to System -> Administration -> Printing, right click on your printer, go to Preferences, and click enable sharing.

---

### Post by ggaaron on 2008-08-31
NOOOOOOOO, DON'T USE SAMBA FOR THIS.

I've already done this several times and I've already tried with samba - unnecessary added complexity, harder to make it to work (you have to set up samba), more load (you have to run samba server) and cups is everything you need to make it work without problems, I don't remember, but possibly if you let cups publish printers other machines will see them when scanning for printers.

---

### Post by _sAm_ on 2008-08-31
No need for Samab. Follow this nice and easy guide and it will work just fine:
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by scwinn on 2008-08-31
Thanks for the help, but I have Hardy and there is no "Server Settings" menu, or tab. Also "policies seems to be setup that way by default"

---

### Post by ggaaron on 2008-08-31
Try 'localhost:631' - it's default cups configuration GUI, nice and does the same as this printer conf you don't have.

---

### Post by scwinn on 2008-08-31
Doesn't work. Page not wound. I typed [http://localhost:631/printers/DESKJET_3820](http://localhost:631/printers/DESKJET_3820)

ALSO

[http://localhost:631/printers/](http://localhost:631/printers/)

Any ideas??:guitar:

---

### Post by ggaaron on 2008-08-31
Have you stopped cups? 'sudo /etc/init.d/cupsd start'

---

### Post by scwinn on 2008-08-31
no. btw thanks for taking the time.

---

### Post by ggaaron on 2008-08-31
If you can't access localhost:631 then either you've configured your firewall not to let you, or cups is not running, start it with above command.

---

### Post by scwinn on 2008-08-31
I tired your suggestion and here is what happened...

root@dad-desktop:/home/dad# 'sudo /etc/init.d/cupsd start'
bash: sudo /etc/init.d/cupsd start: No such file or directory
root@dad-desktop:/home/dad# 

tHANKS.

---

### Post by ggaaron on 2008-08-31
Sorry:
'sudo /etc/init.d/cupsys restart'
Things are unfortunately named differently under different distributions=/

---

### Post by john test on 2008-09-02
Please ignore offtopic post
Sorry--

---

### Post by ggaaron on 2008-09-02
If this were the questions (mailed to me by email daemon):
What happens if you type sudo /etc/init.d/cupsd start' at the local console?

What happens if you open firefox on the local console and browse to localhost:631 at the local console?

What happens if you type ps -ef | grep cupsd at the $prompt on the local console?
then answers are:
1. you start CUPS daemon (CUPS stands for Common Unix Printing System and is responsible for printer management)
2. CUPS opens www server on port 631 that lets you configure it, co you access this server
3. ps -ef gives you list of running processes and grep cupsd searches for cupsd in this list effectively telling you if CUPS is running

---

### Post by scwinn on 2008-09-05
If I try the Localhost command on the workstation running the printer. I see the printer utility. I still cannot share it though.

---

### Post by ggaaron on 2008-09-05
Have you checked 'Share published printers connected to this system' in Administration tab?

---

