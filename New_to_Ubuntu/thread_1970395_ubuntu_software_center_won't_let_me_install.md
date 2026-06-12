---
title: "ubuntu software center won't let me install"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by LERON F on 2012-05-01
Hey Friends, I just installed ubuntu 12.04 and it works fine but whenever i try installing anything forom software center it won't work. The use sousce button is there but it cannot be pressed. I can install from the terminal though. 
PLEASE HELP!

---

### Post by JRV on 2012-05-01
Welcome aboard!

Start software-center from a terminal.  
This will allow you to see any error messages.

This is what I see, software center is working: ```

jack@manx:~$ software-center
2012-05-01 06:07:37,083 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-05-01 06:07:37,120 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-05-01 06:07:37,465 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file


```

---

### Post by 00negative on 2012-05-01
> **LERON F said:**
> Hey Friends, I just installed ubuntu 12.04 and it works fine but whenever i try installing anything forom software center it won't work. The use sousce button is there but it cannot be pressed. I can install from the terminal though. 
PLEASE HELP!

Maybe try reinstalling software center from terminal.  I dont remember the commands off hand but would be same as reinstalling any program so commands should be easy to find. 

I think someone else had this same issue and after an update run from terminal and maybe a reboot the software center was working again

---

### Post by cortman on 2012-05-01
The best fix for USC issues is a quick reinstallation.

```
sudo apt-get remove software-center
sudo apt-get install software-center
```

---

### Post by zombifier25 on 2012-05-01
> **cortman said:**
> The best fix for USC issues is a quick reinstallation.

```
sudo apt-get remove software-center
sudo apt-get install software-center
```
Why don't we just
```
sudo apt-get install --reinstall software-center
```

---

### Post by LERON F on 2012-05-01
Thanks guyz for ur quick response. I tried the update then reboot but that didn't solve my problem. Any ideas? My previous installation of ubuntu gave no such problem.

---

### Post by thatguruguy on 2012-05-01
You still haven't posted what messages you receive when you try to run software center from the command line.

---

### Post by cortman on 2012-05-01
> **zombifier25 said:**
> Why don't we just
```
sudo apt-get install --reinstall software-center
```

Yes, either way will work.

---

### Post by LERON F on 2012-05-01
Thanks guys for ur quick response. I tried the update then reboot but my problem stil exists. Any ideas?

---

### Post by LERON F on 2012-05-01
I get no error messages. It just refuses to install anythin. Reinstalling software center did not fix problem. Should I reinstall the entire os?

---

### Post by thatguruguy on 2012-05-01
> **LERON F said:**
> Thanks guys for ur quick response. I tried the update then reboot but my problem stil exists. Any ideas?

Here's an idea.

Run it from the command line, and post the results here.

---

### Post by texasboy2084 on 2012-05-01
Try: ```
sudo apt-get update
```I had the same problem as the OP. I don't know what happen but the command line said it couldn't resolve us.archive.ubuntu.com:http, and the above fixed it.





Edit for a mod:
Since I don't post much, can someone change my distro to 12.04 please?

---

