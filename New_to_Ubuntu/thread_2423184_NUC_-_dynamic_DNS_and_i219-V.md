---
title: "NUC - dynamic DNS and i219-V"
date: 2019-07-18
forum: New to Ubuntu
---

### Post by grrfield on 2019-07-18
Hi all,
   
  I recently stopped using my Raspberry Pi 3B+ (which was working on Raspbian) and I replaced it with an Intel NUC8I5BEH. Since I was hosting a (personal) cloud and some doom servers and other stuff, I thought some extra power would be nice (don&#8217;t ask me about the price though).
   
  I have some basic knowledge about computers, operating systems and even programming, but this just something to have fun with in my (scarce) spare time. So I must be the noob in your eyes [FONT=&amp]&#55357;&#56842;[/FONT]. I installed stuff, configured and sometimes messed up big time, always with google as my guide in doing things to that poor pi.
   
  The NUC though was different from the start on. I tried to install Debian onto it (just because this was the OS I was most familiar with) but failed miserably since it did not have drivers for the Intel I219-V Ethernet controller. I mention this specifically because I read there might be problems with the I219-V and this might be related to my problem.
   
  I decided to install Ubuntu (18.04.2) and, hurray, it indeed delivered the drivers Debian was missing. I reconfigured the whole thing to my needs and saw it was good and much more powerful than the pi (To be honest, I tried Debian with a net install before Ubuntu. That worked, but brought me to the same problems I&#8217;m discussing next).
   
  The last step was &#8220;going headless&#8221; with the thing, connecting it to my outside world router, only to gain access to it with ssh, and using a dynamic DNS (duckdns) &#8211; just like I did with my Raspberry Pi. All worked fine, I thought. I will keep a long story short and share my findings about the problems that I am encountering since installing and configuring the thing.
   
  My main (troublesome) use cases are
   
  [FONT=Tahoma]1.    [/FONT]Bitvise (sftp client) for file transfer to and from my NUC 
  [FONT=Tahoma]2.    [/FONT]Nextcloud (16.0.3)
  [FONT=Tahoma]3.    [/FONT]Hosting Doom servers (Zandronum)
   
  The thing is, when I connect those applications with a direct ip addres (192.168.0.X) everything works just great. My cloud reaching speeds up to 800 Mb/sec and all. I can only perform this from within my own network ofcourse.
   
  When I try to use the same applications with my dynamic dns (example.com), I can easily login with ssh, but when I start using the network more heavily then sudden the speeds fall back to a mere 50 Kb/sec and the connection in my terminal becomes slow. Finally the NUC becomes irresponsive, and furthermore, my modem/router breaks the connection to the internet. I always need to reboot both in order to get things fixed. I have this within my own network and in the &#8220;outside&#8221; world.**update:** **This happens as well as i use my "direct" external ip (like 178.23.XX.XX). **
   
  Another thing. In the pi time, the ping to my doom servers was max. 2 ms. Now standard latency is more like 20 ms.
   
  things I tried:
  [FONT=Tahoma]-       [/FONT]disable ipv6 (heard to the grapevine this might be a culprit) : did not work
  [FONT=Tahoma]-       [/FONT]I have an internet modem and a router. I tried to move it inbetween my PC and router, not hanging it directly to the outside world (to test if my internet modem was the culprit): not helping
  [FONT=Tahoma]-       [/FONT]I even reinstalled Ubuntu 2 times, since I might have messed up in choosing the wrong installation options or having messed up just like that
   
  I am desperate here. I need to have access through DNS since I want have connection to my cloud from the outside world and I want people to have access to my doom servers.

---

### Post by grrfield on 2019-07-18
As another update:

I tried to install the latest drivers, but i got this error:

> grrfield@grrfield:~/e1000e-3.4.2.4/src$ sudo make install
make -C /lib/modules/4.18.0-25-generic/build CC=gcc SUBDIRS=/home/grrfield/e1000e-3.4.2.4/src modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-25-generic'
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/netdev.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/ethtool.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/param.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/82571.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/ich8lan.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/80003es2lan.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/mac.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/nvm.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/phy.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/manage.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/kcompat.o
  CC [M]  /home/grrfield/e1000e-3.4.2.4/src/ptp.o
  LD [M]  /home/grrfield/e1000e-3.4.2.4/src/e1000e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/grrfield/e1000e-3.4.2.4/src/e1000e.mod.o
  LD [M]  /home/grrfield/e1000e-3.4.2.4/src/e1000e.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-25-generic'
gzip -c ../e1000e.7 > e1000e.7.gz
# remove all old versions of the driver
find /lib/modules/4.18.0-25-generic -name e1000e.ko -exec rm -f {} \; || true
find /lib/modules/4.18.0-25-generic -name e1000e.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000e.ko /lib/modules/4.18.0-25-generic/updates/drivers/net/ethernet/intel/e1000e/e1000e.ko
/sbin/depmod -a 4.18.0-25-generic || true
install -D -m 644 e1000e.7.gz /usr/share/man/man7/e1000e.7.gz
man -c -P'cat > /dev/null' e1000e || true
man: command exited with status 1: (cd /usr/share/man && /usr/lib/man-db/zsoelim) | (cd /usr/share/man && /usr/lib/man-db/manconv -f UTF-8:ISO-8859-1 -t UTF-8//IGNORE) | (cd /usr/share/man && preconv -e UTF-8) | (cd /usr/share/man && tbl) | (cd /usr/share/man && nroff -mandoc -rLL=97n -rLT=97n -Tutf8) | gzip -c7
grrfield@grrfield:~/e1000e-3.4.2.4/src$

i am baffled....

---

