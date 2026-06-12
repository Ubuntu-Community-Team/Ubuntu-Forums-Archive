---
title: "LTS for Ubuntu with Lubuntu desktop?"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-04-28
I'm experimenting with 12.04. Didn't care for the default desktop in Ubuntu, so I installed the Lubuntu desktop over top of a standard Ubuntu install. All's fine so far. But when I boot up, the splash screen now says Lubuntu rather than Ubuntu. Will I still have the new 5-year Long Term Support on this installation? The reason I ask is that in the past when I've done a minimum install and added the Xubuntu desktop, the splash screen at boot still said "Ubuntu". Stupid question, but I still want to know.

---

### Post by Frogs Hair on 2012-04-28
Run the following command and if the results indicate 12.04 LTS your good to go . It is still 12.04 no matter what compatible DE/shell you put on it.```
cat /etc/lsb-release
```

---

### Post by grahammechanical on 2012-04-28
Check your software sources. What repositories does the Update Manager give you under Settings. Are they still Ubuntu or are they Lubuntu?

Regards.

---

### Post by snowpine on 2012-04-28
The splash screen is just graphics, it means nothing.

Lubuntu 12.04 is not long-term support and will be supported 18 months. Note that this applies only to the LXDE-specific packages; your core Ubuntu system will receive updates for the full 60 months.

---

### Post by Javelin Dan on 2012-04-28
Thanks for responding everyone...

Frog's Hair - Your command reveals "Ubuntu 12.04 LTS"

grahammechanical - The software sources in Update Manager say "Ubuntu" (but I thought Lubuntu used Ubuntu repositories anyway (?)

snowpine - Cool. 60 months - me likey!

I guess I'll go ahead and mark this as solved. Thanks again!

---

