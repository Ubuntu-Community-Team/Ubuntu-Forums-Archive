---
title: "How to know problems in my system?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by hotuserl on 2013-06-28
I am newbie to ubuntu...Recently i was installed ubuntu 12.04LTS. The problem is my system hanged regularly..everytime i was restarted and used the sytem....i dont know whats the problem....so my request is any software is there to finds the complete problems in my system ?...so plz help me

---

### Post by dino99 on 2013-06-28
To get some usefull help, you need first to describe your system: how it has been installed, which desktop is used to login with, which graphic driver is used. They are the main details.

[http://www.google.fr/#gs_rn=18&gs_ri=psy-ab&cp=21&gs_id=2a&xhr=t&q=ubuntu+troubleshooting&es_nrs=true&pf=p&sclient=psy-ab&oq=ubuntu+troubleshootin&gs_l=&pbx=1&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925](http://www.google.fr/#gs_rn=18&gs_ri=psy-ab&cp=21&gs_id=2a&xhr=t&q=ubuntu+troubleshooting&es_nrs=true&pf=p&sclient=psy-ab&oq=ubuntu+troubleshootin&gs_l=&pbx=1&bav=on.2,or.r_qf.&bvm=bv.48572450,d.d2k&fp=c6186e8a239b59e&biw=1674&bih=925)

If you want to know what is wrong, then the logs are the places where to glance at: /home/your_user/.xsession-errors (ctrl+h to unhide it), and into /var/log/dmesg
As it hang, its probably related to the grahic driver; check it with jockey:  sudo jockey-gtk

---

### Post by android4682 on 2013-06-28
> **hotuserl said:**
> I am newbie to ubuntu...Recently i was installed ubuntu 12.04LTS. The problem is my system hanged regularly..everytime i was restarted and used the sytem....i dont know whats the problem....so my request is any software is there to finds the complete problems in my system ?...so plz help me

How many disk space you have left on your Ubuntu partion?

---

