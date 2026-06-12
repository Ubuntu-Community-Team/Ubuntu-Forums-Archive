---
title: "Deluge not working"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by aRagnis on 2011-09-02
Yesterday I updated to Ubuntu 11.10 and now Deluge won't start up anymore.

Has anyone had similiar problem, or know, how to fix it?

---

### Post by sonicb00m on 2011-09-02
Mine is starting ok but I have noticed that closing and reopening often causes it to not restart. It's obviously something quite buggy at the moment.

---

### Post by cariboo on 2011-09-02
What error messages do you get when you start deluge from a terminal?

---

### Post by Timothy Coxon on 2011-09-09
Having the same issues I think. Running deluge from terminal does nothing.. no error code or anything. Pretty sure it worked earlier.
When I checked my system monitor I noticed that deluged was working so I just installed the webui and accessed it fine like that.. the issue seems to be specifically within "deluge".

---

### Post by cariboo on 2011-09-09
I used to be a deluge user, but I found Qbittorrent suits me better.

---

### Post by webme on 2011-09-09
> **Timothy Coxon said:**
> Having the same issues I think. Running deluge from terminal does nothing.. no error code or anything. Pretty sure it worked earlier.
When I checked my system monitor I noticed that deluged was working so I just installed the webui and accessed it fine like that.. the issue seems to be specifically within "deluge".

delete .config/deluge
although you will loose the torrents

---

### Post by JonM33 on 2011-09-10
> **cariboo907 said:**
> I used to be a deluge user, but I found Qbittorrent suits me better.

I concur, much better option!

---

### Post by t1497f35 on 2011-09-10
Make sure you got deluged installed (sudo apt-get install deluged), if not, install and reboot.

---

