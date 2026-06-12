---
title: "Internet speed"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by Sunfist on 2013-07-17
Is there a command in Linux that will show me my current upload/download speeds?

---

### Post by diazepamkit on 2013-07-18
type conky in terminal

---

### Post by sanderj on 2013-07-18
point your webbrowser at [http://www.speedtest.net/](http://www.speedtest.net/)

or 

wget 'http://ftp.belnet.be/ubuntu.com/ubuntu/releases/13.04/ubuntu-13.04-desktop-i386.iso' -O /dev/null

to see your download speed.

---

### Post by BrunoLotse on 2013-07-18
Hi, use nmtool. Among other things nmtool will show you speed of your internet connection. Another thing I am using is NetSpeed GNOME extension [https://extensions.gnome.org/extension/104/netspeed/](https://extensions.gnome.org/extension/104/netspeed/)Cheers, Bruno

---

### Post by dannyboy79 on 2013-07-18
> **diazepamkit said:**
> type conky in terminal
really? that's not an answer to the OP's question.

i've used iftop, you can install it using
```
sudo apt-get install iftop
```
then so that it can access your eth interface you need to run it with sudo, so
```
sudo iftop
```
and that will show you all sorts of info about sent and received packets to your network interface

---

### Post by varunendra on 2013-07-18
The default "System Monitor" shows current upload/download speeds too, but is an overkill for just speed monitoring.

I use nload for live monitoring, runs in a terminal and can be installed with -
```
sudo apt-get install nload
```

For cummulative daily/weekly/monthly bandwidth usage details, vnstat -
```
sudo apt-get install vnstat
```

Usage example of both of above -
```
nload -u K wlan0
vnstat -d -i wlan0
```

---

