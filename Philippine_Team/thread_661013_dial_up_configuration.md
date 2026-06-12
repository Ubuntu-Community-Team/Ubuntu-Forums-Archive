---
title: "dial up configuration"
date: 2008-01-07
forum: Philippine Team
---

### Post by ako_si_makoy on 2008-01-07
mga sir help naman. gutsy gibbon user here. hindi ako makaconnect sa internet. nagdadial naman ang modem ko tapos hanggang carrier tone lang. nadidisconnect after.

paano ang tamang configuration ng dialer/modem?

prepaid internet card lang ang gamit ko.. thanks

---

### Post by pinoyskull on 2008-01-07
check this howtos in case you miss something
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

personally i haven't tried using dial-up on Ubuntu

---

### Post by ako_si_makoy on 2008-01-08
ok thanks.. i'd tried already the instructions from your second link, ayaw pa din. pero yung sa first link di ko pa nasubukan. 

thanks sir.

---

### Post by februarius on 2008-01-10
find ur modem using wvdialconf
para makita mo kng phy add nung hardware modem mu,
then edit /etc/wvdial.conf
edit mo ung username pass phone number then ung phys add nung modem, then save
then dial again using wvdial,

kng trip mo medyo graphical ska autodetect try mo i install kppp
apt-get install kppp after installation makikita na sya sa menubar > internet > kppp 

:)

---

