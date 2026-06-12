---
title: "HELP. Problem with mouse on 12.04"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by dep0 on 2012-08-16
HI, i just upgraded to ubuntu 12.04 on a hp mini notebook and i cannot get the mouse to work properly. It keeps flashing and disappears everytime i click on a link, folder or any other option.
I tried to install additional drivers, but i keep getting the message "no additional drivers are in use in this system".
Any suggestions?

---

### Post by AoFhEkOl on 2012-08-16
Can't you go into package manager and reinstall the mouse?
 
Or this?
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Khal1d on 2012-08-16
Yes...it seems to be a driver problem...

I'd un-install and reinstall the drivers in that case.

---

### Post by Scott Harrison on 2012-08-17
What mouse are you using?

---

### Post by jskinner1724 on 2012-08-17
Hi Dep0

Copy the text below and save it to your drive and run it afterwards. Then open the text file it creates and paste the results here.

```
#! /bin/bash

# Retrieves system info
# for troubleshooting
# Name this file SystemInfo

touch system_info.txt
echo === lspci info === >> ~\system_info.txt
lspci -knn >> ~\system_info.txt
echo ` ` >> ~\system_info.txt
echo === lsusb == >> ~\system_info.txt
lsusb >> ~\system_info.txt
echo ` ` >>~\system_info.txt
echo === lsmod === >> ~\system_info.txt
lsmod >> ~\system_info.txt
echo ` ` >> ~\system_info.txt
echo === kernel version === >> ~\system_info.txt
uname -r >> ~\system_info.txt
```

---

