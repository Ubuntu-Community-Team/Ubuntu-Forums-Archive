---
title: "usb wifi on ubuntu server"
date: 2015-01-20
forum: New to Ubuntu
---

### Post by happyfisherman on 2015-01-20
Hello, this is my first post, sorry if I am in the wrong place or if this has been discussed before,  didn't find the answer i needed by searching for it.  I just installed ubuntu server 14.04.1 on a dedicated server I plan to use for my business website and email and i am somewhat new to all of this.  I have a belkin n300 usb wifi adapter, and I just need to know how to get connected to the internet.  A direct ethernet connection is not easily accessible, so all the other devices in my house run on wifi, and I need the server to run on wifi also.  I have ran the command lsusb and it does detect the wifi adapter, but when i run iwconfig it is not detecting internet under the wlan0.  Any help would be greatly appreciated!!

---

### Post by mastablasta on 2015-01-20
> **happyfisherman said:**
>   I just installed ubuntu server 14.04.1 on a dedicated server I plan to use for my business website and email and i am somewhat new to all of this.
since you are new definitely use a wire. using wi.fi makes it less secure and more easily hackable. I wouldn't put business and email server on Wi-Fi.

>   A direct ethernet connection is not easily accessible, so all the other devices in my house run on wifi, and I need the server to run on wifi also. 
suggest you use a drill to make a hole for the wire. 

otherwise you need to configure the network first  /etc/network/interfaces properly.

check under wireless: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)
I think it's the same in Debian: [https://wiki.debian.org/WiFi/HowToUse](https://wiki.debian.org/WiFi/HowToUse)

but seriously think hard about what I wrote above. you will need to secure the server well (with many layers) if you open it to internet (e.g. a website server). so start with basics - cable.
let's not even mention that wi-.fi suffers from packet losses which can cause bad updates.

---

### Post by happyfisherman on 2015-01-20
Thanks for the input.  I will try to see about getting the router moved into my room so I can have it wired directly.  the router is in the garage, and in order to run a wire to where the server is located, I would have to either run a wire outside the house or drill through a 6" thick concrete wall.  I will try to contact my internet provider to see if they can move the router into my office.  Kind of a long story why the modem and router was put there in the first place but long story short it was the most logical placement at the time.  Thanks again for the reply.  Im sure I will be back on here with more questions soon enough, but most of the questions I have had have been easily answered simply by doing a search in the forum.

---

