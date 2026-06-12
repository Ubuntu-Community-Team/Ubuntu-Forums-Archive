---
title: "Ubuntu rsync issue"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by todorakiggg on 2013-10-29
From time to time I have very high iowait, after I installed iotop, I've seen that it is caused by rsync program. The weird thing is that I have it just installed and not configured or anything. 
However this thing does something and I am wondering how to stop or configure it. I tried to find some materials on google, but nothing really helpful.
So my question is where is rsync keeping its configuration settings and how to access and change them. It is very annoying when it does something (I guess making backup), but I do not know what is backing up, and more importantly where it is stored. Yesterday I left it alone and in the morning everything was back to normal, no iowait and rsync was not running...
Is it auto started by Cron by default? Or some other custom startup script?

---

### Post by papibe on 2013-10-29
Hi todorakiggg.

I agree with most of your conclusions.

rsync is not used by default on a fresh installation. Although most backup software uses it on the background.

Most likely is either run by your user or root. I'd start checking crontabs:
For you:
```
crontab -l
```
For root:
```
sudo crontab -l
```
I'd also check your 'Starup Applications' and /etc/rc,local

Let us know how it goes.
Regards

---

