---
title: "no internet without typing sudo dhclient eth0"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by angelsneverdie on 2012-10-01
so, this randomly started happening:

one day i couldn't connect to the internet through my wired connection.  did some googling on my laptop and found the suggestion of typing

sudo dhclient eth0

in the terminal.  and it worked!

only problem is that now i have to type that every time computer restarts - is there a way to automate this?

thanks.

---

### Post by wojox on 2012-10-01
Have you tried [How to automate running the dhclient in ubuntu?]("http://superuser.com/questions/151936/how-to-automate-running-the-dhclient-in-ubuntu")

---

### Post by Avery Bolles on 2012-10-03
This is another method you could use to create a launcher

[http://askubuntu.com/questions/193074/have-to-run-sudo-dhclient-eth0-automatically-every-boot](http://askubuntu.com/questions/193074/have-to-run-sudo-dhclient-eth0-automatically-every-boot)

---

