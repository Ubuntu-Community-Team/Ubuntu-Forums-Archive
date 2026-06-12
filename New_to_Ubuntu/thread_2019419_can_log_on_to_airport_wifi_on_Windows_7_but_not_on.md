---
title: "can log on to airport wifi on Windows 7 but not on Linux"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by hanzj on 2012-07-07
Hello,

I can't log on to the free airport WiFi on my Linux partition but can on the Windows 7 partition. Can anyone tell me why this is? And how can I fix this problem?

Some info that may help:

This WiFi network tells me that "additional procedures may be necessary"
Signal strength is excellent (full bars)

---

### Post by NikTh on 2012-07-07
Try to open network manager settings as admin.. and add wifi connection manualy. 
```
sudo nm-connection-editor
```

---

### Post by steeldriver on 2012-07-07
"additional procedures" may mean there's some kind of web based captive portal - not sure how well those play with dnsmasq, did you try opening a browser at some public url (google.com or whatever) - if so what happens?

---

### Post by hanzj on 2012-07-08
On Linux, I can see the SSID. Is there still a need to install the program you recommend?

---

