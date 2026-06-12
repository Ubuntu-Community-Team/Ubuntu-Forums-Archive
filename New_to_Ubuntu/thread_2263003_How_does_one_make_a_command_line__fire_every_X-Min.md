---
title: "How does one make a command line  fire every X-Minutes?"
date: 2015-01-28
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2015-01-28
Thanks for reading

question. I found a command script---that will allow for manual changing of a MAC Address

```

macaddr=$(dd if=/dev/urandom bs=1024 count=1 2>/dev/null|md5sum|sed 's/^\(..\)\(..\)\(..\)\(..\)\(..\)\(..\).*$/\1:\2:\3:\4:\5:\6/')
echo $macaddr

"Attribution Credit"  @[gucki]("http://serverfault.com/users/83616/gucki")
[http://serverfault.com/questions/299556/how-to-generate-a-random-mac-address-from-the-linux-command-line](http://serverfault.com/questions/299556/how-to-generate-a-random-mac-address-from-the-linux-command-line)

```


I read on another site about creating a *.d file and putting somewhere in etc/...... to have it fire on reboot.....but maybe every few minutes? 
What is a normal length of time if one wants to remain anonymous? Thanks! 

Also necessary to change a "Name" as well?

---

### Post by yancek on 2015-01-28
I'm not really sure what your intentions are but if you want to run a specific command every 5 minutes, just put an entry in /etc/cron.  Open a terminal and run:  crontab -e
If it is a system script you need to run it with sudo.

---

### Post by Holger_Gehrke on 2015-01-29
> **whereismymindat2 said:**
> 
question. I found a command script---that will allow for manual changing of a MAC Address
```

macaddr=$(dd if=/dev/urandom bs=1024 count=1 2>/dev/null|md5sum|sed 's/^\(..\)\(..\)\(..\)\(..\)\(..\)\(..\).*$/\1:\2:\3:\4:\5:\6/')
echo $macaddr

"Attribution Credit"  @[gucki]("http://serverfault.com/users/83616/gucki")
[http://serverfault.com/questions/299556/how-to-generate-a-random-mac-address-from-the-linux-command-line](http://serverfault.com/questions/299556/how-to-generate-a-random-mac-address-from-the-linux-command-line)

```


That's not what this does. It only generates something random that looks like a MAC  address, it doesn't change your MAC address. And if you look at the site from which you took it a bit more careful, you will notice that this is just about the worst of the generators offered, as it wastes 1024 bytes of randomness to produce 6 random bytes (true randomness is valuable, read 'man 4 random')

---

### Post by HermanAB on 2015-01-29
Howdy,

You can schedule things with 'cron' or you can make something run in a little while with 'at'.  Read the man page for details.

Anyhoo, what you are trying to do with your MAC address isn't really useful.

---

