---
title: "Aircrack-ng-1.1"
date: 2012-06-12
forum: Packaging and Compiling Programs
---

### Post by Kimaris on 2012-06-12
So, I've tried working on this problem on my own for about a week. And have come up with out any success...
I'm trying to install aircrack-ng-1.1 
 The code you are supposed to use is:
 ```
sudo make install
```but I get this response
```
edward@ubuntu:~/aircrack-ng-1.1$ sudo make install
[sudo] password for edward: 
make -C src install
make[1]: Entering directory `/home/edward/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/edward/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/edward/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/edward/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/edward/aircrack-ng-1.1/src/osdep'
make -C osdep install
make[2]: Entering directory `/home/edward/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/edward/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/edward/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/edward/aircrack-ng-1.1/src/osdep'
install -d /usr/local/bin
install -m 755 aircrack-ng airdecap-ng packetforge-ng ivstools kstats makeivs-ng airdecloak-ng /usr/local/bin
install -d /usr/local/sbin
install -m 755 aireplay-ng airodump-ng airserv-ng airtun-ng airbase-ng /usr/local/sbin
make[1]: Leaving directory `/home/edward/aircrack-ng-1.1/src'
make -C scripts install
make[1]: Entering directory `/home/edward/aircrack-ng-1.1/scripts'
install -m 755 airmon-ng airdriver-ng airodump-ng-oui-update /usr/local/sbin
make[1]: Leaving directory `/home/edward/aircrack-ng-1.1/scripts'
make -C manpages install
make[1]: Entering directory `/home/edward/aircrack-ng-1.1/manpages'
rm -f /usr/local/man/man1/aircrack-ng.1
rm -f /usr/local/man/man1/airdecap-ng.1
rm -f /usr/local/man/man1/airdriver-ng.1
rm -f /usr/local/man/man1/aireplay-ng.1
rm -f /usr/local/man/man1/airmon-ng.1
rm -f /usr/local/man/man1/airodump-ng.1
rm -f /usr/local/man/man1/airserv-ng.1
rm -f /usr/local/man/man1/airtun-ng.1
rm -f /usr/local/man/man1/ivstools.1
rm -f /usr/local/man/man1/kstats.1
rm -f /usr/local/man/man1/makeivs-ng.1
rm -f /usr/local/man/man1/airbase-ng.1
rm -f /usr/local/man/man1/packetforge-ng.1
rm -f /usr/local/man/man1/airdecloak-ng.1
rm -f /usr/local/man/man1/airolib-ng.1
rm -f /usr/local/man/man1/wesside-ng.1
rm -f /usr/local/man/man1/tkiptun-ng.1
rm -f /usr/local/man/man1/buddy-ng.1
rm -f /usr/local/man/man1/easside-ng.1
install -d /usr/local/man/man1
install -m 644 aircrack-ng.1 airdecap-ng.1 airdriver-ng.1 aireplay-ng.1 airmon-ng.1 airodump-ng.1 airserv-ng.1 airtun-ng.1 ivstools.1 kstats.1 makeivs-ng.1 airbase-ng.1 packetforge-ng.1 airdecloak-ng.1  /usr/local/man/man1
make[1]: Leaving directory `/home/edward/aircrack-ng-1.1/manpages'
 
[B]
[*] Run 'airodump-ng-oui-update' as root (or with sudo) to install or update Airodump-ng OUI file (Internet connection required).[/B]

```I'm having a problem with that last line, I have already run that program with sudo. It is entirely up to date, but I keep getting that response... Does anyone have any ideas as to how to fix this?
(And sorry if this is a crappily worded post.. It's my first one)

---

### Post by O2Blevel on 2012-06-12
This guide helped me a lot:  [www.janoweb.net/tutorials/installing-aircrack-ng.html#axzz1xdSQvdc2](www.janoweb.net/tutorials/installing-aircrack-ng.html#axzz1xdSQvdc2)

---

