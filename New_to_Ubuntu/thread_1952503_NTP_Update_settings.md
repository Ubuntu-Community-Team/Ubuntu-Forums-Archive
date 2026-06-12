---
title: "NTP Update settings"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by MinnieThePooh on 2012-04-04
Does anyone know how to change the sites contacted by the NTP update process ?

For example, is it possible to delete some or add others from the list of sites used to get time and date updates?

---

### Post by oldos2er on 2012-04-04
Edit the file /etc/default/ntpdate, you will need root privileges to do so. ```
gksu gedit /etc/default/ntpdate
```

---

### Post by MinnieThePooh on 2012-04-04
> **oldos2er said:**
> Edit the file /etc/default/ntpdate, you will need root privileges to do so. ```
gksu gedit /etc/default/ntpdate
```


That file currently has only one entry....ntp.ubuntu.com

however.....

I see about 30 or 40 other sites being contacted using IPBLOCK on the 123 port.

Where else could ntpdate be getting those other IP addresses ?

Thanks again.

---

### Post by Doug S on 2012-04-04
Do you have a file on your system /etc/ntp.conf , as would have been installed if you ever installed ntpd? If you do, then ntpdate seems to use that. Even if you have removed ntpd via```
sudo apt-get remove ntp
```the file /etc/ntp.conf stays. You would have to purge with```
sudo apt-get purge ntp
```All of that being said, I have found little correlation between the contents of ntp.conf and ntp servers actually accessed (but I really didn't look into it).

---

### Post by Cheesemill on 2012-04-04
In the ntp.conf file you should find the following entries:

0.pool.ntp.org
1.pool.ntp.org
2.pool.ntp.org
3.pool.ntp.org

These entries don't point to a single server (or servers), instead they point to a random set of servers that change every hour on a round-robin basis to distribute ntp requests to any one of a number of ntp servers around the world (currently about 3000).

You should be able to change these entries to point to specific servers but by doing this you would lose the redundancy that is built into the ntp system.

More information can be found here:
[http://www.pool.ntp.org/en/](http://www.pool.ntp.org/en/)

---

