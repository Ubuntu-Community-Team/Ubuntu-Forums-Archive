---
title: "See current connections (IP, Port, Protocol)?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-12-01
I'm thinking about setting up UFW and since I'm a newbie was I hoping that there is someway to see what IP, Protocol's, port's that is in use atm, to hopefully make configuring easier. Is there a way to do this?

---

### Post by Peter09 on 2008-12-01
I believe that Firestarter, which is in the repositories is a GUI front end for the firewall.

---

### Post by EdThaSlayer on 2008-12-01
The program called "iftop" should be useful to you.

Even though it's a terminal program it's still very useful.

iftop: display bandwidth usage on an interface by host

just type the following in the terminal

> sudo apt-get install iftop


then type in iftop in the terminal and you are ready to go(you might have to type in *sudo iftop* since well, sometimes it won't let you access your network cards input output info for security reasons)

---

### Post by kpkeerthi on 2008-12-01
> **SpinningAround said:**
> I'm thinking about setting up UFW and since I'm a newbie was I hoping that there is someway to see what IP, Protocol's, port's that is in use atm, to hopefully make configuring easier. Is there a way to do this?

```

netstat -antp

```

---

