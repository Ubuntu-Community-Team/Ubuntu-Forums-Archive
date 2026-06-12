---
title: "Authenticate problem with apt"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by speme on 2012-11-08
Running software center or other GUI program with root priority.
Show a window about request the root password. when I input the right password. It alert me input the wrong password. But, The password it true.
It's the sudoer's password. I don't have root user.

Also, In this time, It always show a window about Dbus Error.

---

### Post by 2F4U on 2012-11-08
What version of Ubuntu are you using? What happens if you execute

sudo apt-get update

in a terminal?

---

### Post by atkrad on 2012-11-08
Hello
Run the following command and see what happens?

```

sudo apt-get clean
sudo apt-get update

```

---

### Post by speme on 2012-11-09
These commands works good, but the problem also exist.

---

### Post by speme on 2012-11-09
I modify the > /etc/sudoersfile when I install ubuntu 12.10 shortly. I fail to gain the root priority. So, I add a line > user   ALL=(ALL:ALL) ALL.

---

