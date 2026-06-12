---
title: "audio and window prefs help"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-06
so in [this thread]("http://ubuntuforums.org/showthread.php?t=814985"), i was instructed to have my computer remeber the window settings at login. later i unchecked that, and it keeps on doing it! whats up with that???


also, in this account, the sound doesnt work in most games (sauerbraten, battle for wesnoth, etc.) but in other accounts, it does. It used to, but one day stopped. It is an onboard NVidia NForce 405, and for all of my accounts the sound settings are the same. Help?

---

### Post by tom56 on 2008-06-07
Regarding the audio problem, compare what groups the account is in with the account that works.
```
cat /etc/group
```

---

### Post by Zopiac on 2008-06-07
> **tom56 said:**
> Regarding the audio problem, compare what groups the account is in with the account that works.
```
cat /etc/group
```


my main account:

zopiac@zopiac:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
fax:x:21:mombode,zopiac,root,macosx,vistaaero,simple,test,gaming
voice:x:22:
cdrom:x:24:haldaemon,zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
floppy:x:25:haldaemon,zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
tape:x:26:mombode,zopiac,root,macosx,vistaaero,simple,test,gaming
sudo:x:27:
audio:x:29:zopiac,mombode,pulse,root,macosx,vistaaero,simple,test,gaming
dip:x:30:zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:zopiac,macosx,vistaaero,simple,test,gaming
sasl:x:45:
plugdev:x:46:haldaemon,zopiac,root,macosx,vistaaero,simple,test,gaming
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
nvram:x:105:
fuse:x:106:mombode,zopiac,root,macosx,vistaaero,simple,test,gaming
ssl-cert:x:107:
lpadmin:x:108:zopiac,root,macosx,vistaaero,simple
messagebus:x:109:
admin:x:110:zopiac,root,macosx,vistaaero,simple
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:zopiac
haldaemon:x:116:
powerdev:x:117:haldaemon,zopiac
gdm:x:118:
zopiac:x:1000:
mombode:x:1001:
libuuid:x:120:
pulse:x:121:
pulse-access:x:122:
pulse-rt:x:123:
mlocate:x:124:
polkituser:x:125:
sambashare:x:119:zopiac,root,macosx,vistaaero,simple
macosx:x:1002:
vistaaero:x:1003:
simple:x:1005:
guest:x:1004:
test:x:1007:
gaming:x:1008:


gaming account:

gaming@zopiac:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
fax:x:21:mombode,zopiac,root,macosx,vistaaero,simple,test,gaming
voice:x:22:
cdrom:x:24:haldaemon,zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
floppy:x:25:haldaemon,zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
tape:x:26:mombode,zopiac,root,macosx,vistaaero,simple,test,gaming
sudo:x:27:
audio:x:29:zopiac,mombode,pulse,root,macosx,vistaaero,simple,test,gaming
dip:x:30:zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:zopiac,macosx,vistaaero,simple,test,gaming
sasl:x:45:
plugdev:x:46:haldaemon,zopiac,root,macosx,vistaaero,simple,test,gaming
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,zopiac,mombode,root,macosx,vistaaero,simple,test,gaming
nvram:x:105:
fuse:x:106:mombode,zopiac,root,macosx,vistaaero,simple,test,gaming
ssl-cert:x:107:
lpadmin:x:108:zopiac,root,macosx,vistaaero,simple
messagebus:x:109:
admin:x:110:zopiac,root,macosx,vistaaero,simple
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:zopiac
haldaemon:x:116:
powerdev:x:117:haldaemon,zopiac
gdm:x:118:
zopiac:x:1000:
mombode:x:1001:
libuuid:x:120:
pulse:x:121:
pulse-access:x:122:
pulse-rt:x:123:
mlocate:x:124:
polkituser:x:125:
sambashare:x:119:zopiac,root,macosx,vistaaero,simple
macosx:x:1002:
vistaaero:x:1003:
simple:x:1005:
guest:x:1004:
test:x:1007:
gaming:x:1008:

---

### Post by Zopiac on 2008-06-07
bump

---

### Post by Zopiac on 2008-06-14
well it seems that when i log in it doesnt remember windows, but starts a window set: nautilus, pidgin, and opera. This implies that it is the 'remember Current settings' and not 'remember settings each time i log out/in', so there's something. Is there any way to completely disable this?

audio still baffles me, though.

---

### Post by Zopiac on 2008-06-17
bump????

---

