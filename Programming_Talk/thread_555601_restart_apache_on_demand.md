---
title: "restart apache on demand"
date: 2007-09-20
forum: Programming Talk
---

### Post by tocleora on 2007-09-20
Alright I *think* this should go in programming - my apologies if not.

I need a way for someone viewing a page on server A (Fedora 4) to be able to restart Apache on server B (Ubuntu).  server A is the primary web site but some things come from server B... but for some reason Apache on server B keeps hanging.  I know PHP won't do root commands and of course if Apache is hung I obviously can't get to PHP from server A to even use it to restart it.  I hope that makes sense, any suggestions?

---

### Post by fazavon on 2007-09-20
install webmin (webmin.com) and set up a custom command when Apache stops responding.

thanks

//j

---

### Post by tocleora on 2007-09-20
You mean a cron job?  and how do I detect when apache stops responding?

This web app is for a sales floor and the supervisors will need to be able to restart it so they don't have to call us on the weekends.  So webmin isn't the best solution if it needs to be done manually.  TIA!

---

### Post by fazavon on 2007-09-20
no you set up a monitor, if Apache goes down it will restart the service for you.

---

