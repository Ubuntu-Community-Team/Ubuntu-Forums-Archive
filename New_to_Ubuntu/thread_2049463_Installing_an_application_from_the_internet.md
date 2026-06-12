---
title: "Installing an application from the internet"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by SparkyLinux on 2012-08-28
Hi guys,

I'm new to Ubuntu and I'm trying to install an application. Usually I  install from the software center but I saw this application on reddit [http://postman-delivery.appspot.com/](http://postman-delivery.appspot.com/)

I searched for it in the software center but cannot find it. The website  says to either download a file or enter some commands. Which one should  I do? :razz:

Plz help. Thanks!!!!

---

### Post by Cheesemill on 2012-08-28
Just use the commands, this way it will be added to the Software Centre and be automatically updated whenever a new version is available:
```
sudo add-apt-repository ppa:schumifer/postman
sudo apt-get update
sudo apt-get install postman
```

---

### Post by irv on 2012-08-28
Yes, running the commands one at a time in a terminal will work. I am using 12.04 and I installed it yesterday, and all works well.

---

### Post by SparkyLinux on 2012-08-28
Thanks for the responses!

Once the application is added to the Ubuntu software center, will I be able to remove the repository and still get updates from Ubuntu?

---

### Post by Cheesemill on 2012-08-28
Removing the repository will remove the application from the Software Centre and stop it from receiving updates.

---

### Post by SparkyLinux on 2012-08-28
> **Cheesemill said:**
> Removing the repository will remove the application from the Software Centre and stop it from receiving updates.

Thanks, that clears things up!

---

