---
title: "Screen total white out....video card problems"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-07-19
Hi All,

After my install and updates all is well unless I choose to open the restricted driver for my video card which is a Radeon 9800 Pro.

When I select it the screen goes to a complete white out.

Bummer..so I wanted to try out Kubuntu and kde4 anyway so just installed it.
When I did the same with card after the install in kde the screen went all black with a small white box in the middle. *LOL*

So as reinstalled unbuntu and as long as I dont mess with the restricted driver(video in this case) all is well. 

Any feedback on this video card Radeon 9800 pro ?

thanks,
bikinguy :lolflag:

---

### Post by PmDematagoda on 2008-07-19
If you installed the restricted ATi driver, try reinstalling the driver with:-
```
sudo apt-get install --reinstall xorg-driver-fglrx
```
and then see if the white screen and other graphics problems have been resolved.

---

