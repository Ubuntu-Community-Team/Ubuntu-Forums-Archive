---
title: "vsftpd not in init.d"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by david227 on 2014-06-09
We're unable to run vsftpd on an Ubuntu 14.04 instance.  For background:

To start clean I run this:
```
sudo apt-get remove --purge --auto-remove vsftpd -y
```

Then this:
```
sudo apt-get install vsftpd -y
```

Unfortunately, running this:
```
sudo /etc/init.d/vsftpd restart
```
returns this:
```
sudo: /etc/init.d/vsftpd: command not found
```

And sure enough, there is no "vsftpd" created in the /etc/init.d directory.

When I try:
```
sudo service vsftpd start
```
I get the "Unknown Instance" problem here: [http://ubuntuforums.org/showthread.php?t=1628800](http://ubuntuforums.org/showthread.php?t=1628800) and the solution proposed there made no difference.

This is running on an AWS instance I wonder if there's configuration issue there?

Any help, greatly appreciated...

---

### Post by david227 on 2014-06-10
Solution found!  For future reference:  Here's the problem [https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1313450](https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1313450)[COLOR=#000000][FONT=Helvetica].  and here's a direct link to the kernel update:[/FONT][/COLOR]  [http://www.deinon.com/wiki/doku.php?id=linux:ubuntu](http://www.deinon.com/wiki/doku.php?id=linux:ubuntu)

---

