---
title: "Need to run several commands after reboot or startup."
date: 2014-07-14
forum: New to Ubuntu
---

### Post by carmelo3 on 2014-07-14
I will like to be able to have the server launch the several daemons and session on startup.

This would be what I would run manually, How do I go about automating this?


sudo isracoind -daemon
sudo litecoind -daemon
sudo reddcoind -daemon
sudo karmad -daemon
sudo sexcoind -daemon


screen -dmS redis
screen -dmS nomp


screen -r redis
redis-server
CTRL + A + D to detach from screen


screen -r nomp
cd nomp
node init.js
CTRL + A + D to detach from screen

---

### Post by ubudog on 2014-07-14
For your various daemons, you could add a @reboot entry into the root crontab to start them:
```
sudo crontab -e
```
Pick your preferred editor, and add:
```

@reboot /usr/bin/isracoind -daemon
@reboot /usr/bin/litecoind -daemon
@reboot /usr/bin/reddcoind -daemon
@reboot /usr/bin/karmad -daemon
@reboot /usr/bin/sexcoind -daemon

```

Make sure that the correct path to each daemon is provided, as each one may not be in /usr/bin.  To find out, for example, type:
```
which irsacoind
```

As for starting your screen instances, you could either do the same with crontab above, or edit /etc/rc.local, and add:
```
/usr/bin/screen -dmS redis redis-server
/usr/bin/screen -dmS nomp bash -c 'cd nomp ; node init.js'
```
before 'exit 0'.

Hope that helps you!

---

### Post by carmelo3 on 2014-07-14
VERY HELPFUL!

Wow, thanks!

Will this also work on startups? not only reboot.

---

### Post by ubudog on 2014-07-14
Yes, @reboot runs every startup and /etc/rc.local runs on startup.

Glad it was helpful! :-)

---

