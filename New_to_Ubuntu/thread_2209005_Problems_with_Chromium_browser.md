---
title: "Problems with Chromium browser"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by AmitSinha on 2014-03-03
Hi,

I am using Ubuntu 13.10 - with Chromium browser. This is my favorite browser, and I had become too much dependent on it(will all my passwords saved, and more..)
But, 2 days back, the power went off all of a sudden, and the backup failed too. So, there was an abrupt shutdown.

When I restarted my machine, Chromium would not start up ! I tried to uninstall and reinstall it, but now I am open it only in the "temporary profile" mode. This way, I have to fill in all the details(password and all), when I am trying to open a website. Each time I open the browser, it forgets everything of the previous session.

Please help me out, to get my Chromium back.

Thanks in advance !
Amit

---

### Post by Vladlenin5000 on 2014-03-03
[https://support.google.com/chrome/answer/142059?hl=en](https://support.google.com/chrome/answer/142059?hl=en)

---

### Post by IvoGuerreiro on 2014-03-03
Hi, 
Have you tried remove your personal configuration[FONT=UbuntuRegular][COLOR=#333333]?
[/COLOR][/FONT]```
[FONT=Ubuntu Mono]rm .config/chromium -rf[/FONT][FONT=UbuntuRegular][COLOR=#333333]
[/COLOR][/FONT]
```[FONT=UbuntuRegular][COLOR=#333333]
and start over.


[/COLOR][/FONT]

---

### Post by endlessinstant on 2014-03-03
If you can't get anything salvaged from clearing out the configuration files as above, you might want to try starting completely over```
sudo apt-get purge chromium-browser
```This will completely remove chromium and all personal settings from your system.   Just to be 100% you might want to run```
sudo apt-get updatesudo apt-get install chromium-browser
```afterwards.   Assuming you are signed into chromium so that all your settings can sync, the browser should be able to pull everything back for you.

---

### Post by AmitSinha on 2014-03-28
Thanks for the prompt response. The problem still persists. I tried both - clearing out the configuration files, and then re-installing the browser all over again.
What options do I have now ?

Thanks.

---

