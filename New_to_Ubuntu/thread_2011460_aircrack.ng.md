---
title: "aircrack.ng"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-06-27
Hey guys. 

I'm trying to install aircrack but I keep reaching a dead end and not sure what I'm doing wrong. 

This is what I typed


apt-get install build-essential libssl-dev
wget [http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz](http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz)
tar -zxvf aircrack-ng-1.1.tar.gz
cd aircrack-ng-1.1
gedit common.mak

then gedit
CFLAGS ?= -g -W -Wall -Werror -O3
to:
CFLAGS ?= -g -W -Wall -O3

followed by 
make
sudo make install

This is where i get the error. when typing sudo make install

[*] Run 'airodump-ng-oui-update' as root (or with sudo) to install or update Airodump-ng OUI file (Internet connection required).

Any thoughts? Ideas? 

Thanking youse

K.m

p.s I'm using Ubuntu 12.04 LTS

---

### Post by Cheesemill on 2012-06-27
Aircrack isn't supported on these forums.

You can try asking in the Aircrak forums instead.

---

### Post by kabukiM0n0 on 2012-06-27
Oh, okay. Cheers

---

### Post by Elfy on 2012-06-27
closed

---

