---
title: "check my crontabs for errors please &lt;3"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by Dori922 on 2011-10-01
sudo crontab -uroot -e

0 1 * * * rsync -az -e ssh root@192.168.1.3:/home /home/backups/daily
0 3 * * 6 cp -R /home/backups/daily/home /home/backups/weekly/
0 5 1 * * cp -R /home/backups/daily/home /home/backups/monthly/

does this look okey, before i test it? (ssh-keys set up between ubuntu-server and ubuntu-client1)

---

### Post by gmargo on 2011-10-01
You should test it and see if you get what you want.  

At the very least you'll find that **cp -R** is not acceptable since you'll blow away all file/group ownership and timestamps. Add a **-p** to preserve those.

---

