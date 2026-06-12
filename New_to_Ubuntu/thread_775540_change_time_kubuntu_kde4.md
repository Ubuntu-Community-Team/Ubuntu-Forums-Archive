---
title: "change time kubuntu kde4"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ogcub on 2008-04-30
How to change time in kde4?

system settings shows all time panel disabled, administrator mode button is nowhere to be found, sudo systemsettings says systemsettings doesn't exist. kdesu also fails, forum search also shows nothing.
Any suggestions?

---

### Post by srikar on 2008-04-30
Even i faced the same problem. There was no administrative button.I did the old way.

sudo apt-get install kcontrol.

after u install this run sudo kcontrol in the konsole. Chenge the time there.

This solves the problem , but if u find another method widout installing kcontrol , just personal message me : )

---

### Post by ogcub on 2008-04-30
> **srikar said:**
> Even i faced the same problem. There was no administrative button.I did the old way.

sudo apt-get install kcontrol.

after u install this run sudo kcontrol in the konsole. Chenge the time there.

This solves the problem , but if u find another method widout installing kcontrol , just personal message me : )

Thanks kcontrol worked for me also :)

---

### Post by oaussieo on 2008-05-01
hi I tried installing Kcontrol but I get Kcontrol already installed no change made, still looking for a way to change from 24h to 12h, and help on this would be great...

Thanks

---

### Post by jetsetbk on 2008-05-02
> **oaussieo said:**
> hi I tried installing Kcontrol but I get Kcontrol already installed no change made, still looking for a way to change from 24h to 12h, and help on this would be great...

Thanks

oaussieo, fortunately you can change the 24h to 12h without kcontrol. Go to System Settings > Regional & Language > Time & Dates > Time Format. Drop it down to the option with AMPM and you'll be set.

---

### Post by regx on 2010-03-19
or you can just do this:
sudo /etc/init.d/ntp stop
sudo ntpdate pool.ntp.org

---

