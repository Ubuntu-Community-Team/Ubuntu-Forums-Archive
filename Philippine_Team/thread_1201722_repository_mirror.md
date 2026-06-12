---
title: "repository mirror"
date: 2009-07-01
forum: Philippine Team
---

### Post by kiminaiseah on 2009-07-01
haler,

wakeup ko lang to, natanong ko na e2 before,

ano ba mirror ng ubuntu para sa latest uptodate and bleeding edge mirror ng ubuntu?

i-example ko na ang debian, kasi debian ako since 8yrs ago,

currently i used:

(testing/squeeze/future release)
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) squeeze main contrib non-free
-or-
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) testing main contrib non-free

(unstable/sid/sidux release)
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) sid main contrib non-free

(unstable/experimental)
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) experimental main contrib non-free

pag gamit ko yang mga mirror na yan lahat ng latest and upto date version lib/apps/etc pde mo acquire, and securely 100% miski mag dist-upgrade kasama pati kernel mag aaupdate, ang firewall ko 3years naka debian naka cron ang auto dist-upgrade and weekly reboot, so far hindi nag eeror, headless setup, 100% kampante ako sakanya @ 32MB RAM tumatakbo.

meron ba parang ganyan ang ubuntu? instead of using:

##JAUNTY UPDATES MAIN#
#deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) jaunty-updates main
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
## JAUNTY UPDATES UNIVERSE
deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) jaunty universe
deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) jaunty-updates universe
#BACKPORTS REPOSITORY#
deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) jaunty-backports main universe
#JAUNTY PARTNERS#
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

#SECURITY REPO#
deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) jaunty-security main
deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) jaunty-security universe
deb [http://lug.mtu.edu/ubuntu/](http://lug.mtu.edu/ubuntu/) jaunty-proposed main universe

kasi sa ubuntu after life end ng isang release, execpt LTS, cguro mga 50% lang gagana, may incompat issue or depreciation sa libs, as mention sa isang thread, hindi nag bo-boot yung grub, yan ang pansin ko pag, i tried install ubuntu 8.10 tpos nag apt-cdrom add ako ng jauntu, tpos dist-upgrade, ayun di na nag boot, grub error

---

