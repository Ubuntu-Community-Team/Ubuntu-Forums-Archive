---
title: "date time change"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-02-24
Hi friends,

I am trying to change date and time without sudo rights. for that i openned sudoers file and add an entry to the end of the file like this;
jug ALL=/bin/date

After that restarted the system to make effect. but still i cannot change date and time.

Friends pls give some tricks to make it done.

---

### Post by debodas on 2013-02-25
Can't this be done under date and time settings? Usually accessible by clicking on the time in the panel, and by changing the time manually from there.

---

### Post by pmohankumar on 2013-02-25
Hi,

I need to change date and time without sudo rights.

---

### Post by sudodus on 2013-02-25
I think you can solve your problem with the help of this link

[[COLOR="Red"]http://ubuntuforums.org/showpost.php?p=10472282&postcount=17[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10472282&postcount=17")

---

### Post by audiomick on 2013-02-25
> **pmohankumar said:**
> Hi,

I need to change date and time without sudo rights.

> **kingnick42 said:**
> Can't this be done under date and time settings? Usually accessible by clicking on the time in the panel, and by changing the time manually from there.

On this 10.10 install, at least, yes, the time an date can be changed without having to acquire root privileges. Right click on the time in the panel, choose "settings", choose "time settings", change and confirm. No password request involved at all.

---

### Post by pmohankumar on 2013-02-26
Thanks sudodus, your link worked for me.
Its really helpful for beginners.
Thanks again.

---

