---
title: "Automatically Starting something?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by RyanPriceDotCa on 2008-12-01
Hello,

I've installed XAMPP (or LAMPP I guess for Ubuntu).  In order to get it running whenever I boot up I need to run the following command:

sudo /opt/lampp/lampp start

I tried to add it to my Application menu, but it only seems to work when I've already done something using the sudo command in the terminal.

Is there a way to get this to run each time the computer starts up so that I always have my local host and database running as soon as I'm logged in?

---

### Post by Big_astur on 2008-12-01
You have to use these:

gksudo /opt/lampp/lampp start

gksudo /opt/lampp/lampp stop

when you add them to your application menu

---

### Post by nhasian on 2008-12-01
you can have applications launch automatically from System/preferences/Sessions

---

### Post by Dj Melik on 2008-12-01
Go to System > Preferences > Sessions and add it there.

---

### Post by Big_astur on 2008-12-01
Sorry in my first post i didn't notice you wanted it running all the time.

Do as the others tell you.

---

