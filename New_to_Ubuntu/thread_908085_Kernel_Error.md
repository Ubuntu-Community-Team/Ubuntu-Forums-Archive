---
title: "Kernel Error???"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by ffmpegfailure on 2008-09-02
Hi, earlier when booted up I got told I had a Kernel Error and also, on another bootup something about a crc error. Normally I just turn it on and off and it's all ok but seeing as my computers been playing up I'd like to know what these mean.

---

### Post by Dedoimedo on 2008-09-02
Hello,

Can you post the exact message?

Try the following:

sudo cat /var/log/messages |grep kernel > messages.log
sudo dmseg |grep kernel > dmesg.log

Post the contents of these files here ...

Dedoimedo

---

