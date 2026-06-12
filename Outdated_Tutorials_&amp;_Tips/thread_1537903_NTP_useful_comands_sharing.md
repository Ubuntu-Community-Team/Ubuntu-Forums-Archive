---
title: "NTP: useful comands sharing"
date: 2010-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by ruipedroca on 2010-07-24
Hi,

Just feel like sharing some NTP comands and configurations I use.
Feel free to post yours.


RESTART ntp service:
$ sudo /etc/init.d/ntp restart
[sudo] password for "user":
 * Stopping NTP server ntpd
 * Starting NTP server ntpd

CHECK, see if ntp is running:
$ sudo /etc/init.d/ntp status
[sudo] password for "user":
 * NTP server is running.
NOTE: to "stop" or "start" just replace "status"

see what ntp SERVERS are being used:
$ grep ^server /etc/ntp.conf
server ntp.ubuntu.com

alternative, if you're using dhcp:
$ grep ^server /etc/ntp.conf.dhcp
grep: /etc/ntp.conf.dhcp: No such file or directory

alternative by SERVERNAME:
$ ntptrace $servername
localhost: stratum 3, offset -0.000561, synch distance 0.089180
***Invalid association ID specified
NOTE: as you can see, in this case it gave me an error

alternative by IP ADDRESS:
$ ntpq --numeric --peers
     remote           refid      st t when poll reach   delay   offset  jitter
================================================
 91.189.94.4     193.79.237.14    2 u   32  128  377   39.343  21109.0 7978.74

Determining if NTP is synchronized properly:
$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
=================================================
*europium.canoni 193.79.237.14    2 u    2   64  377   39.463   -0.269   0.164


VIRTUAL WORLD:
NTP SERVER (ubuntu desktop ou server)
$sudo apt-get install ntp
delete all the text in /etc/ntp.conf and replace with:
server 127.127.1.0 minpoll 4 maxpoll 15      
fudge  127.127.1.0 stratum 3         
broadcast 192.168.10.255
server ntp.ubuntu.com
# NOTE: in this case, this server itself talks to another server (ntp.ubuntu.com) in order to synchonise its own time

UBUNTU GUEST
server 192.168.10.104 minpoll 4 maxpoll 15      
#broadcastclient 192.168.10.255
driftfile /var/lib/ntp/ntp.drift
broadcastdelay 0.008
statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable
# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery
# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

FEDORA GUEST
install ntp pacckage and see if the service is active
delete all the text in /etc/ntp.conf and replace with:
restrict default nomodify notrap noquery
server 192.168.10.104   
broadcastclient 192.168.10.255
driftfile /var/lib/ntp/drift
broadcastdelay 0.008

---

### Post by cprofitt on 2010-07-24
On a base install of 10.04 what packages do you need to install to run these commands?

---

### Post by ruipedroca on 2010-07-24
> **cprofitt said:**
> On a base install of 10.04 what packages do you need to install to run these commands?

I believe you only have to install ntp server, but I'm not sure:
$ sudo apt-get install ntp

Debian guys say ntp, ntpdate and ntp-server:
[http://www.debianadmin.com/ntp-server-and-client-configuration-in-debian.html](http://www.debianadmin.com/ntp-server-and-client-configuration-in-debian.html)

---

### Post by dcstar on 2010-07-24
> **ruipedroca said:**
> Hi,

Just feel like sharing some NTP comands and configurations I use.
Feel free to post yours.
..........

No, don't "feel free" to post anything.

This is the forum for **All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu**, if you want to post things like that use the **Tutorials and Tips**  forum, that is what it is for.

---

### Post by ruipedroca on 2010-07-24
> **dcstar said:**
> No, don't "feel free" to post anything.

This is the forum for **All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu**, if you want to post things like that use the **Tutorials and Tips**  forum, that is what it is for.

Ok, so would you be kind enough to tell me how can I move this thread?

---

### Post by Iowan on 2010-07-24
I can help with that part...

---

### Post by ruipedroca on 2010-07-24
> **Iowan said:**
> I can help with that part...

Thanks :)

---

### Post by ruipedroca on 2010-07-25
If you're facing problems setting NTP in a VMWare Server guest virtual machine, it may not be NTP the problem, but instead the host cpu clock that makes virtual machines clock speed up or slow down.

To solve that situation, you must check the host cpu speed at /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq.
If the file doesn't open, copy it to the Desktop and open that copied file.

Then, go to file /etc/vmware/config and add this 3 lines:
host.cpukHz = 2331000 
host.noTSC = TRUE
ptsc.noTSC = TRUE
Obviously, you must replace "2331000" with the your correct value. Also, if the file doesn't exist, you must create it.

I have read in some sites that one could get the cpu clock information by using this command at the console "$ cat /proc/cpuinfo" but in my case it didn't work because it showed a different cpu clock speed.

---

