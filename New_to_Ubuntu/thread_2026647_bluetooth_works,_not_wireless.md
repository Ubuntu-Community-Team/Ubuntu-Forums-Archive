---
title: "bluetooth works, not wireless"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by sean kel on 2012-07-15
i have a presario c500. my broadcom isnt working right. i am baffled on this. i downloaded and installed driver. i hit the wifi switch, and it turns on/off bluetooth, but wont show show i have wifi. can anyone please help.

---

### Post by Bigtime_Scrub on 2012-07-15
Would you post the output of ```
lspci
``` so we can get some more information about your system?

---

### Post by NikTh on 2012-07-15
**Hello and Welcome to Ubuntu Forums !**

Open a terminal (ctrl+alt+t) and copy-paste this command 
```
jockey-gtk
``` it will open a window of additional drivers. Look for a deactivated driver of STA or Broadcom . If you find one , then activate it. (install it) . Maybe reboot needed after activation for driver take place. 

If above not work , then open a terminal again and copy-paste these commands one at time 
```
cat /etc/lsb-release && uname -r 
iwconfig
ifconfig -a 
rfkill list all
```copy-paste the results here , inside [CODE] tags by highlighting the text and click at # symbol on top of message pane. 
Thanks

---

### Post by sean kel on 2012-07-15
didnt work

---

### Post by Bigtime_Scrub on 2012-07-15
What didn't work exactly? The terminal commands?

---

### Post by sean kel on 2012-07-15
i did the terminal commands but i still dont have wireless. i again, hit the wireless button and the bluetooth turns on/ off. but wont find any routers

---

### Post by westie457 on 2012-07-15
Hello and welcome to the forum.

Give us a big clue to help you. Could you post the output of these commands please, and to make things easier for us could you put ```
 brackets around the info by clicking in the # symbol and pasting between the [code] brackets. [CODE]cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```

Thank you.

---

