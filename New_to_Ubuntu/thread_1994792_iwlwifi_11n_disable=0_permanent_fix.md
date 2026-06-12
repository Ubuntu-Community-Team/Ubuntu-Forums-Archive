---
title: "iwlwifi 11n_disable=0 permanent fix"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by yasitha on 2012-06-03
Hi all, I'm a newbie to linux so please bear with me. I've searched and can't find how to make this fix permanent. In summary I can get my wireless to work by entering a couple of lines at the terminal (see below). However I can't figure out how to make this a permanent fix.

I have 12.04 installed on my laptop (lenovo x220) and couldn't get my wireless to work properly. It would connect to the router and get a valid IP address, but I couldn't ping the router or get any internet access. After searching around I found the issue was that wireless n was disabled. Typing the following in the terminal fixes the issue:
sudo modprobe iwlwifi -r
sudo modprobe iwlwifi 11n_disable=0

Wireless works!:p

I then created a file /etc/modprobe.d/iwlwifi.conf and entered the following lines
options iwlwifi -r
options iwlwifi 11n_disable=0

After rebooting the first line seems to work because the wireless is disabled, however it doesn't reconnect. If I then type sudo modprobe iwlwifi 11n_disable=0 in the terminal I get this error:
                                  FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)  
  
It doesn't matter what I name the file, I get the same error. As soon as I delete the file and try that line again at the terminal, wireless works! 

I'm not really sure what I've done wrong...can someone help?

Cheers,
Yas

---

### Post by josephmills on 2012-06-03
> **yasitha said:**
> 
I have 12.04 installed on my laptop (lenovo x220) and couldn't get my wireless to work properly. It would connect to the router and get a valid IP address, but I couldn't ping the router or get any internet access. After searching around I found the issue was that wireless n was disabled. Typing the following in the terminal fixes the issue:
sudo modprobe iwlwifi -r
sudo modprobe iwlwifi 11n_disable=0

Wireless works!:p



simple work around would be. 

make script and place in /usr/sbin/
```

#!/usr/bin/env bash
sudo modprobe iwlwifi -r
sudo modprobe iwlwifi 11n_disable=0

```

save that ^^ in /usr/sbin as wireless-fix

open terminal 
```
cd /usr/sbin/
```
```
sudo chmod +x wireless-fix
```
```
gnome-session-properties
```

Click on Add 
 name : wireless-fix
 command: /usr/sbin/wireless-fix
 comment: temp fix till I fix upstream

Click add again

[img]http://ubuntuforums.org/attachment.php?attachmentid=219152&stc=1&d=1338731492[/img]


This will be a temp fix. Next post I will talk about Upstream and fixing the source code its-self

---

### Post by josephmills on 2012-06-03
can we also see a 
```
cat /etc/modprobe.d/iwlwifi.conf
```
if it is not there please find and show us 
```
sudo find / -name "iwlwifi.conf"
```
also a ```
dmesg
``` 
would also help Take out sensitive info plz

---

### Post by idoitprone on 2012-06-04
remove this line
```
 options iwlwifi -r
```
it is not necessary since the modules is parsing all the files before they load it

the options must be defined in
```
modinfo iwlwifi
```

or else it will spit errors

---

### Post by yasitha on 2012-06-04
> **idoitprone said:**
> remove this line
```
 options iwlwifi -r
```it is not necessary since the modules is parsing all the files before they load it

Looks like that was the issue, removed that line from the .conf file and it works fine.

Thanks all for your help!

Yas

---

### Post by yasitha on 2012-06-28
An update on this.

 I don't think this issue had anything to do with wireless n being disabled (at least not directly). It turns out that booting my laptop without it being plugged in causes the problem. 

:???:

---

