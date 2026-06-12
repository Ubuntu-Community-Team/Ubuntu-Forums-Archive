---
title: "I need help installing (reinstalling) Adobe flash"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by mjp29mjp29 on 2012-05-04
I was at accuweather.com and it says it needs the plug in

My system also has been telling me it can't update Adobe Flash

What can I type into terminal to fix this.


I'm currenlty using:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

---

### Post by 2ta8gdfte on 2012-05-04
Try using the firefox plugin flashaid.  [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by mjp29mjp29 on 2012-05-04
The Adobe flash plug in is giving the operating system fits.  Reporting that it is broken.  That it is not a genuine package.  That it is being uninstalled.  Etc...

Is it time for me to upgrade this system to the latest version of Ubuntu - ?

---

### Post by pqwoerituytrueiwoq on 2012-05-04
remove flash then let flash aid handle it (it will fix it system wide)

---

### Post by mjp29mjp29 on 2012-05-04
Please give specific instructions on how to remove flash

---

### Post by pqwoerituytrueiwoq on 2012-05-04
run this in a terminal
```
sudo apt-get purge adobe-flash*
```

flash aid will do this if needed but you said it the package manager was complaining about flash

---

### Post by mjp29mjp29 on 2012-05-04
ok, removed.  now, excuse me for being so beginner, but how do i make flash aid handle reinstalling it

---

### Post by pqwoerituytrueiwoq on 2012-05-04
just install the addon and click it (button near address bar on right) go to the wizard and click the options you want

[html5 video]("http://tc.v8.cache7.c.youtube.com/videoplayback?upn=AF891KzmozQ&sparams=cp%2Cid%2Cip%2Cipbits%2Citag%2Cratebypass%2Csource%2Cupn%2Cexpire&fexp=912211%2C903945%2C913103%2C919306&itag=22&ip=24.0.0.0&signature=CC2FC631FCD1869E7C4715D7C80E2197838F105C.409F8A989C261F0495614DAD6813DC6588F2ACB4&sver=3&ratebypass=yes&source=youtube&expire=1336201716&key=yt1&ipbits=8&cp=U0hSS1JLT19GUENOMl9KRVNIOlpSbW4zVlpyTXdL&id=665513cec0a3b247") sorry if this link method breaks any rules i was trying to link to the html5 version since the one who need to view it does not have flash

---

### Post by mjp29mjp29 on 2012-05-04
Received these type of messages below

Could not install the add on

Subprocess installed pre-removal script returned error

system may be in an unstable state

I've fooled with it enough tonight.  If anyone has any more suggestions, post them and I'll try your suggestions tomorrow.

---

### Post by pqwoerituytrueiwoq on 2012-05-04
```
sudo apt-get install -f
```try that

BTW if you try to upgrade with the system the way it is it will go south fast

---

