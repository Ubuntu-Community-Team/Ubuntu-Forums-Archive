---
title: "Problem with Time in Ubuntu"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by flex567 on 2014-11-02
In my Ubuntu 14.04 the time is an hour behind the actual time(time on the internet). How can I fix this error?. 
I didn't change the time settings so far, should I change the time now manually ?

In the time & date settings the location is selected correctly and time set is set to automatically  from the internet.

---

### Post by Bucky Ball on 2014-11-02
If you have daylight saving time it's possibly that. Right click the clock and try 'Properties'. Might let you adjust for daylight saving. Using xfce4 so not sure on your setup.

---

### Post by flex567 on 2014-11-02
I cannot right click on the clock.

---

### Post by Impavidus on 2014-11-02
If this is a dual boot there could be confusion between Windows and Ubuntu on whether to set the clock on the motherboard to local time or UTC. But if I'm correct (and this is always very confusing), that would give you an error of one hour in the other direction. Your time zone is Central European Time, winter/standard time, right?

I'm also on xfce, but somewhere in your settings there must be something for date and time, where you can set the time zone. Somebody using Unity may be able to tell where exactly.

---

### Post by flex567 on 2014-11-02
yes CET

---

### Post by Paulgirardin on 2014-11-02
If you are using Ubuntu with Unity, tap the super key (windows key) and enter 'time' into the search field then hit enter.

---

### Post by Penguin360 on 2014-11-03
> **flex567 said:**
> In my Ubuntu 14.04 the time is an hour behind the actual time(time on the internet). How can I fix this error?. 
I didn't change the time settings so far, should I change the time now manually ?

In the time & date settings the location is selected correctly and time set is set to automatically  from the internet.

I had this issue before. I recall this is how I fixed it:

1. Change "Set the time" to Manually and set it to the correct time, then exit the Time and Date settings
2. Go back to Time and Date settings, change it back to "Automatically from the Internet"

---

