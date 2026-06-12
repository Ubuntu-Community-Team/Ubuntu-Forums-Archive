---
title: "Qualcomm Atheros AR9285 Wireless Network adapter issue"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by prasanna9 on 2015-09-08
Hello am new to ubuntu & i have installed ubuntu 14.04 LTS ,i am facing issue like am not able to connect to wifi ,so how to sortout this? let me know you that i tried lots of time to get solution but failed so its my last hope from you. Note- my kernel driver in use is- ath9k.

---

### Post by sandyd on 2015-09-08
Hi, please run the following, and attach the files wireless-info.txt and wireless-info.tar.gz, which will be located in your home folder. If you do not have internet via a wired connection, you will have to use  USB drive or something else to transfer the files to a computer where you have internet

```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by prasanna9 on 2015-09-10
Hello sandyd Today i found my wifi is properly working..one of my friend told me to try this comand .
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf

sudo modprobe -rfv ath9k

sudo modprobe -v ath9k

i think this code is working so please dont mind if any further issue comes up with wifi then i will ping you..

---

### Post by prasanna9 on 2015-09-23
Hello sorry to say that again WI-FI Issue arises.I dont know why when i was trying to connect to wifi its not connecting.i have already tried your command but no result.so please help me.

---

