---
title: "Ubuntu 14.04 aircrack-ng [!] WARNING: Failed to associate with xx:xx:xx:xx:xx:xx (ESS"
date: 2014-10-28
forum: New to Ubuntu
---

### Post by Onl on 2014-10-28
sudo -s
[https://code.google.com/p/reaver-wps/downloads/list](https://code.google.com/p/reaver-wps/downloads/list) (DOWNLOAD)
tar xvfz reaver-1.4.tar.gz
sudo apt-get install libpcap-dev
sudo apt-get install libsqlite3-dev
cd reaver-1.4/src
./configure
make
make install
sudo apt-get install aircrack-ng
airmon-ng start wlan0
airodump-ng mon0
 --- reaver -i mon0 -b 30:85:A9:36:9A:80 ---
 

 [https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/247088_681620141945805_8703758469755548721_n.jpg?oh=851435279f7e5e7e7af44ab7ea36c28b&oe=54EC93FB&__gda__=1425346937_d583bc0a7ec116431cd52551e821575e](https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-xpa1/v/t1.0-9/247088_681620141945805_8703758469755548721_n.jpg?oh=851435279f7e5e7e7af44ab7ea36c28b&oe=54EC93FB&__gda__=1425346937_d583bc0a7ec116431cd52551e821575e)
[+] Waiting for beacon from 30:85:A9:36:9A:80
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: (null))
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: (null))
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: WIFINAME)
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: WIFINAME)
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: WIFINAME)
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: WIFINAME)
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: WIFINAME)
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: WIFINAME)
[!] WARNING: Failed to associate with 30:85:A9:36:9A:80 (ESSID: WIFINAME)

---

### Post by westie457 on 2014-10-28
You won't get much help on here for aircrack. It is not supported.

On a side note you went the wrong way for installing it. Aircrack-ng is in the repositories. You might get some help to install however you probably won't get any help on how to use it.

---

### Post by QIII on 2014-10-28
Hello!

We do not support queries with regard to aircrack-ng and similar tools on the forums.

Please review the Forum Rules [here]("http://ubuntuforums.org/misc.php?do=showrules"), in particular this:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

Closed.

---

