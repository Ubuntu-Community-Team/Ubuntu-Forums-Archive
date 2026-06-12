---
title: "MySQL server question"
date: 2010-11-24
forum: Programming Talk
---

### Post by Maaku on 2010-11-24
I have finally started adjusting to Ubuntu and have just installed Apache 2.2.14, PHP5, and MySQL server 5.01. I have setup everything and installed phpMyAdmin as well.

My question is how do I change the name of the MySQL server? It currently is at the minute localhost. I know it is possible because I did this on Windows.

It is not really a issue, but I would like to change it to something else. I also did some checks on the MySQL server and could not find any command that does it; I even went through the configuration file for it in /etc/mysql/.

Any help is appreciated.

If this is in the wrong section, I am extremely sorry.

---

### Post by DaithiF on 2010-11-24
the mysql server itself doesn't have a name, it is identified by the host (and port) on which it is running / listening for connections.

that is why the 'name' is localhost -- it is running on your local machine.  it can also be connected to by IP address (127.0.0.1) or by any hostname alias you specify in /etc/hosts.

so for example if you added an alias 'smithers' in your /etc/hosts file:
```
127.0.0.1   localhost   smithers

```

then you could connect to your mysql server using this name:
```
mysql -h smithers -u root -pxxxxxx
mysql -h localhost -u root -pxxxxxx
mysql -h 127.0.0.1 -u root -pxxxxxx

```

---

### Post by Maaku on 2010-11-24
> **DaithiF said:**
> the mysql server itself doesn't have a name, it is identified by the host (and port) on which it is running / listening for connections.

that is why the 'name' is localhost -- it is running on your local machine.  it can also be connected to by IP address (127.0.0.1) or by any hostname alias you specify in /etc/hosts.

so for example if you added an alias 'smithers' in your /etc/hosts file:
```
127.0.0.1   localhost   smithers

```then you could connect to your mysql server using this name:
```
mysql -h smithers -u root -pxxxxxx
mysql -h localhost -u root -pxxxxxx
mysql -h 127.0.0.1 -u root -pxxxxxx

```

Okay, that actually makes sense. I have added a domain to the hosts file that I specified in vhosts for Apache. So, I tried connecting to it with that particular domain name and it failed.

---

### Post by Maaku on 2010-11-24
Issue solved. The file was not being saved, so I tried doing it with root access and it worked. Thanks for your very informative reply, daithiF. It is something I will keep in mind later on.

---

