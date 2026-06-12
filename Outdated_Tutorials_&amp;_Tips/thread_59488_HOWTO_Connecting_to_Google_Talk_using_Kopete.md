---
title: "HOWTO: Connecting to Google Talk using Kopete"
date: 2005-08-24
forum: Outdated Tutorials &amp; Tips
---

### Post by SGC on 2005-08-24
First install QCA-TLS plugin for SSL support (Univere repository)
```
sudo apt-get install qca-tls
```
* In kopete go to settings -> Confiure Kopete and click on **New** from **Accounts** tab

* Click on **next** on the introduction screen and choose **Jabber** from the next screen

* Enter the following information on **Basic Setup** tab:
-- In the **Jabber ID** enter: [email]USERNAME@gmail.com[/email]
-- Check **Remember password** and enter your password

* And these information on **Connection** tab:
-- Check **Use protocol encryption (SSL)**, **Allow plain-text password authentication** and **Overide default server information**
-- In the server field enter: talk.google.com and 5223 for the port

---

### Post by traherom on 2005-08-24
[QUOTE=SGC]* And these information on **Connection** tab:
-- Check **Use protocol encryption (SSL)**, **Allow plain-text password authentication** and **Overide default server information**
-- In the server field enter: talk.google.com and 5223 for the port[/QUOTE]Um... you sure about 522**3**? I got Gaim working using port 5222... and that's what the Google Talk FAQ says.

---

### Post by Mishura on 2005-08-24
5223 works.  I think I read something on Slashdot about 5222 being default, and 5223 being a "slightly" more secure method of authentication.. but I could be dead wrong.  Either or, it works nonetheless.

---

### Post by schultzy on 2005-08-24
any reason to use kopete over GAIM set up similarly?

---

### Post by Mishura on 2005-08-25
Only if you prefer Kopete more than Gaim.  I'm a KDE user, and I'd love to like Kopete, but that isn't gonna happen just yet.  Gaim's more feature-filled.

It's all down to personal preference, and the ability to use "Whatever you feel like".  So far, Gaim, Kopete, and Psi are three Linux IMs that support Google Talk, and possibly others like Gabber, Sim, etc..  Hell, if there is a console based Jabber client, it should work too.

---

### Post by sam_gupta69 on 2008-11-05
It is giving me error. i followed your instructions.But the error is : "This user is not reachable at the moment. Please make sure you are connected and using a protocol that supports offline sending, or wait until this user comes online."
i entered my personal information. What should i do?

---

### Post by ubonetu on 2009-01-22
Thank you.  Just a quit and restart and I'm up and running.

---

