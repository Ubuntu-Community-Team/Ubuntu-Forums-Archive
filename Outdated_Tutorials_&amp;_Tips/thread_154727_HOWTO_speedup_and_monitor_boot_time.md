---
title: "HOWTO: speedup and monitor boot time"
date: 2006-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-04-03
Tested on Ubuntu Linux 6.04 (Dapper)
originally posted at: [http://howtoforums.net/viewtopic.php?t=12](http://howtoforums.net/viewtopic.php?t=12)

**Summary:**
apt-get install bootchart
apt-get install bum
reboot
mkdir ~/bootchart
cp -v /var/log/bootchart/*.png ~/bootchart
file browse to ~/bootchart 
view the results with an image viewer
optimize afterwards using /usr/bin/bum


Then if you are lazy you can automate it by copying this into a shell:
```

echo "
#!/bin/bash
# run BUM to reduce Boot Time
# apt-get install bum if you do not have it
# /usr/bin/bum
cp -v /var/log/bootchart/*.png ~/bootchart" >~/bootchart/copychart.sh

```

next time just run:
```

sh ~/bootchart/copychart.sh

```

*You could also symlink this to a boot script and a web server if you are running apache for example:
To Symlink to a runlevel so that you can view your bootchart the next time you boot copy this into a shell:
```

sudo ln -s /home/${USER}/bootchart/copychart.sh /etc/rcS.d/S99bootchart
chmod 770 /home/${USER}/bootchart/copychart.sh

```

To Symlink to apache (tested with apache 1.3.34)
```

sudo ln -s /home/${USER}/bootchart/ /var/www/bootchart

```
Then you should be able to browse to [http://localhost/bootchart](http://localhost/bootchart)

reference: thanks to christooss:
[http://www.ahacic.5gigs.com/blog/?p=21](http://www.ahacic.5gigs.com/blog/?p=21)

enjoy !
;-)

---

