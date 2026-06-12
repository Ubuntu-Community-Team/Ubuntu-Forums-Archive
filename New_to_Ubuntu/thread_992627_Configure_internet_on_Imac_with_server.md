---
title: "Configure internet on Imac with server?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by abeisgreat on 2008-11-24
I really didn't know where to post this... so yea.

I install 8.10 server on my imac, I skipped the DHCP setup on install because I didn't have an internet connection at the time, I do now and would like to get internet working, what do I need to do?

---

### Post by pi.boy.travis on 2008-11-24
I believe that Network Manager should detect and configure it automatically. . . If not, you can right click on the applet (should be in the notification area, it looks like two little monitors side by side), select edit connections, and then configure it manually.

---

### Post by abeisgreat on 2008-11-24
I'm running Ubuntu Server so its terminal only, any help?

---

### Post by pi.boy.travis on 2008-11-24
> **abeisgreat said:**
> I'm running Ubuntu Server so its terminal only, any help?

My bad. . . 

Try this: ```
sudo ifconfig eth0 up
```

---

### Post by abeisgreat on 2008-11-24
Hmm is there a sure-fire way to test the connection? I can ping a network IP but I cant update apt-get without error.

---

### Post by ja660k on 2008-11-25
if you have ethernet plugged into the imac

try this command i just learnt :)

```
sudo dhclient eth0
```
this tries to force connect your server to the net

if your network port isnt called eth0 then use what yours is named
you can see this by doing
```
ifconfig
```

---

