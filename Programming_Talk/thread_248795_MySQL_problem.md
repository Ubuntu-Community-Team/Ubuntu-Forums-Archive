---
title: "MySQL problem"
date: 2006-09-01
forum: Programming Talk
---

### Post by frankabel on 2006-09-01
Hi all!

I can't connect from outside (inside of my box I can connect perfectly) dapper box to mysql server. In the table "user" at "mysql" db I have only one row to the User "root" with a Host field set to '%'. The error that the server say is: "ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.0.55' (10061)"

Can any body help me?

Salute
Frank Abel

---

### Post by mortsahl on 2006-09-01
I will assume that the machines are networked together so you can communication between them and there is no firewall in the way ...

Let's say the machine that MySQL is on is named MachineA and the remote machine is MachineB.

On MachineA, get to the MySQL prompt and enter ...

Grant all on *.* to 'root'@'MachineB' identified by 'password' with grant option

Then try it again.

---

### Post by ifokkema on 2006-09-02
If the host is set to %, the user can connect from all hosts. BUT MySQL will have to listen to the external IP address, that's what's holding you. This is less secure than just having MySQL listening on 127.0.0.1, so that's why it's disabled by default. You can enable it through editing the config file. I'm not sure if it'll work with dpkg-reconfigure.

If you get it to work, I would suggest to set the % in the host field to whatever host to connect from, as the current setup allows people to brute-force the MySQL root account from anywhere.

---

### Post by frankabel on 2006-09-02
The problem was solved when I enable other network interface. Thanks for yours reply.

Salute
Frank Abel

---

