---
title: "Is ubuntu 12.10 have arrive? I GET IT FROM WUBI INSTALLER.."
date: 2012-09-28
forum: New to Ubuntu
---

### Post by CurseThePhobia on 2012-09-28
Hi there, i just download ubuntu and i was very supprise when i just download new version of ubuntu (Ubuntu 12.10) and it kind a new for my PC. It is because the new enviroment seemsly very different from the latest popular ubuntu, Ubuntu 12.04 LTS. Im just ask, is that ubuntu 12.10 is have been release and what should i do after installing it?..;)

---

### Post by bcbc on 2012-09-28
No, you shouldn't have got 12.10. That's a bug.

File one [here]("https://bugs.launchpad.net/wubi/+filebug") and include your log file (from the %TEMP% directory). i.e. it should be called %TEMP%\wubi-12.04.1-rev269.log

---

### Post by CurseThePhobia on 2012-09-28
But its telling Ubuntu 12.10 in it. I am so supprise when the wubi was said it will installed ubuntu 12.04 LTS, but when i reboot my system, it appears it had been installed ubuntu 12.10 inside. I have checked it and explore some of it. Seems like many changes from ubuntu 12.04 LTS.

---

### Post by bcbc on 2012-09-28
Confirm the release with:
```
cat /etc/lsb-release
```

Then file a bug with that link I provided and attach your wubi log file from the location I mentioned.
Thanks

---

### Post by CurseThePhobia on 2012-09-28
I have uninstall it bro. I want to install Ubuntu 12.04 LTS manually that i've just download. Anyway, i will use yours way if there any change with my Ubuntu..

---

