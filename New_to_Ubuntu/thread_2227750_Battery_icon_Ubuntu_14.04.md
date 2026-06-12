---
title: "Battery icon Ubuntu 14.04"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by josh56 on 2014-06-03
Hello,

I recently installed Ubuntu 14.04  and the battery icon keeps  disappearing. It will show up when I plug the charger in, but when I  restart my laptop it disappears. If I plug the charger in and then  unplug the charger the icon will show up, but when I restart the  computer again it will disappear again. I am a first time Ubuntu user  and Linux user. I have tried Google and it has led to no solution. Any  help would be awesome. 

Thanks

---

### Post by Duncubuntu on 2014-06-03
Go to your Unity launcher bar > System Settings > Power

There is an option there to choose when the battery icon appears.

---

### Post by josh56 on 2014-06-04
It is currently set for "When battery is present." Should it be set for something else?

---

### Post by Duncubuntu on 2014-06-05
Well you want it visible all the time, so that should do it...

Mine worked at that point ^_^ A friend recommends trying the following:

```

sudo apt-get purge indicator-power
sudo apt-get install indicator-power

```

This may or may not fix your problem, I personally have not tested that as I haven't had this exact issue.

---

### Post by josh56 on 2014-06-12
Thanks. I will give it a try and see if it works.

---

### Post by kc1di on 2014-08-04
doesn't work here :)
anyone got a fix for this ?

---

### Post by d1337 on 2014-08-26
> **Duncubuntu said:**
> Well you want it visible all the time, so that should do it...

Mine worked at that point ^_^ A friend recommends trying the following:

```

sudo apt-get purge indicator-power
sudo apt-get install indicator-power

```

This may or may not fix your problem, I personally have not tested that as I haven't had this exact issue.

Warning...this may also remove unity-control-center from your system and may not reinstall it.

---

