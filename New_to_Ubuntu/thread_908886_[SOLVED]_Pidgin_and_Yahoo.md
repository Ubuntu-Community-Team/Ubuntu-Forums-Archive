---
title: "[SOLVED] Pidgin and Yahoo"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by tqprvn on 2008-09-02
hi guys

Getting this error this morning on Pidgin from my two Yahoo messenger accounts.  

"[account name] disconnected.
Could not establish a connection with the server:
Error resolving scs.msg.yahoo.com
Name or service not known"

Seems most of my staff getting the same.

Any ideas?

Matt

---

### Post by aimpau on 2008-09-02
Is it just this morning?

---

### Post by hvac3901 on 2008-09-02
I get that all the time at work, does it work for you at home?

I only mention because you said all of you staff are getting the same error.

---

### Post by aimpau on 2008-09-02
Press CTRL+P in Pidgin.

Make sure you autodetect your IP and automatically port forward. Are you under a proxy server?

---

### Post by tqprvn on 2008-09-02
It has always worked for all of us before.  This morning, we came in to work - it had been a 4 day weekend here, so nothing on since Friday last week - and we are all out.

One girl using Windows and the official Yahoo IM client  - she seems fine...

---

### Post by tqprvn on 2008-09-02
> **aimpau said:**
> Press CTRL+P in Pidgin.

Make sure you autodetect your IP and automatically port forward. Are you under a proxy server?

IP autodetect - check
Auto port fwd - check

Proxy server - no.

---

### Post by iaculallad on 2008-09-02
Try this on your Account Setting (Accounts->(select your account name)->Edit Account, and "Advanced" tab.

Proxy Options (Proxy Type) : Use GNOME Proxy Settings

---

### Post by tqprvn on 2008-09-02
hey actually I stand corrected - it was already on Gnome proxy settings - no go.  I then switched it to 'no proxy' - still no go.

---

### Post by aimpau on 2008-09-02
Click accounts>>Edit your account>>>Advanced

Make sure you use Global Proxy Settings. If that doesnt work, try the other options. Make sure you uncheck Yahoo Japan. My pager port is 5050.

---

### Post by tqprvn on 2008-09-02
and now...outta nowhere...it connected.

uh - not sure anyone or anything actually helped the situation just now, but thanks for trying guys.

---

### Post by aimpau on 2008-09-02
No problem.

---

### Post by moisadoru on 2008-10-31
I also encountered this Pidgin/Yahoo behavior. Actualy, I also tried Kopete and I get the same error. I did a test with a dummy yahoo user accout, and surprisingly, using that one it worked, However, If I disconnect and try to connect with the old username, it still gives me the error message.

I can only conclude that Yahoo is behind this circus, way to go Yahoo ... knock off your users. 

Doru
=====
Long live the Dentist

---

### Post by brmc on 2009-07-31
its very simple yahoo people must have changed their server settings

so just change advance settings
replace scs.msg.yahoo.com  to  scsa.msg.yahoo.com
then it should be ok
or u can install pidgin 2.5.8
if u wana update your exciting pidgin,
simply run these in terminal

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

 echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
   
then run the update manager 

if u need more assistance 
go to : [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

chinthaka bandara

---

### Post by VarshaJaikumar on 2010-09-05
I am getting the error. Unable to connect: HTTP proxy connection error 503.

---

