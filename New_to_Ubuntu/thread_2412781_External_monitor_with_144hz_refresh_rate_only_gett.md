---
title: "External monitor with 144hz refresh rate only getting 40-50fps"
date: 2019-02-17
forum: New to Ubuntu
---

### Post by mayaru on 2019-02-17
hi Guys! i just got an external monitor with 144hz refresh rate. now, the problem is that although its set to 144hz, when i check with [https://www.testufo.com/refreshrate](https://www.testufo.com/refreshrate), i get only 40-50hz. I read something about a bug in mutter (the window compositor), but i have no clue how to fix it. Any ideas?


**Distribution (run `cat /etc/os-release`):**
NAME="Pop!_OS"
VERSION="18.10"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Pop!_OS 18.10"
VERSION_ID="18.10"
HOME_URL="https://system76.com/pop"
SUPPORT_URL="http://support.system76.com"
BUG_REPORT_URL="https://github.com/pop-os/pop/issues"
PRIVACY_POLICY_URL="https://system76.com/privacy"
VERSION_CODENAME=cosmic
UBUNTU_CODENAME=cosmic

---

### Post by NM5TF on 2019-02-17
the website you referenced clearly states that it [COLOR="#FF0000"]does not work with Linux[/COLOR].....
try this one instead  [https://www.displayhz.com/](https://www.displayhz.com/)

you might find this article interesting....[https://www.avadirect.com/blog/frame-rate-fps-vs-hz-refresh-rate/](https://www.avadirect.com/blog/frame-rate-fps-vs-hz-refresh-rate/)

open a terminal and key in

```
xrandr
```

it will look something like mine...

```
[tommy@tommy ~]$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+
   1366x768      59.79  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    59.94  
   720x400       70.08  

```

also post the output of 

```
inxi -G
```

these will show what card & driver is in use plus the resolution options for your monitor...

use code tags to make the output more readable....use [COLOR="#FF0000"]adv reply button[/COLOR] & paste the results between the [COLOR="#FF0000"]#'s[/COLOR]


tommy

---

