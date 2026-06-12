---
title: "How to delete broken packages"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by krasimir2 on 2014-09-17
[COLOR=#333333][FONT=UbuntuRegular]I can not remove broken package. Use the following command: ```
sudo apt-get -f install
``` but I get the following response:[/FONT][/COLOR]
```
Preparing to unpack .../nodejs_0.10.28-1chl1~trusty1_amd64.deb ...
Unpacking nodejs (0.10.28-1chl1~trusty1) over (0.10.25~dfsg2-2ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/nodejs_0.10.28-1chl1~trusty1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/node.1.gz', which is also in package nodejs-legacy 0.10.25~dfsg2-2ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/nodejs_0.10.28-1chl1~trusty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
[COLOR=#333333][FONT=UbuntuRegular]I tried various commands like[/FONT][/COLOR]
 ```
2015  sudo apt-get clean
 2020  sudo dpkg --configure -a
 2023  sudo apt-get autoremove
 2034  sudo apt-get upgrade && sudo apt-get -f install
```
[COLOR=#333333][FONT=UbuntuRegular]But I did not get any result. I can not install synaptic. Any ideas how can I remove the broken package ?[/FONT][/COLOR]

---

### Post by slickymaster on 2014-09-17
Hi krasimir2, welcome to the forums.

Please try the following in a terminal window:```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/nodejs_0.10.28-1chl1~trusty1_amd64.deb
```
If **--force-overwrite** doesn't work, try:```
sudo dpkg -i --force-overwrite-all /var/cache/apt/archives/nodejs_0.10.28-1chl1~trusty1_amd64.deb
```

---

### Post by krasimir2 on 2014-09-17
&#1058;hanks

---

### Post by slickymaster on 2014-09-17
You're welcome.

Please mark your thread as SOLVED so other people searching the forums know that it provides a working solution. Just follow the link in my signature if you don't know how to do it.

---

