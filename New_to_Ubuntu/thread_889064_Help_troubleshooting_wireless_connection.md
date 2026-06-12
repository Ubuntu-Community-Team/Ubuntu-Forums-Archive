---
title: "Help troubleshooting wireless connection"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-13
Before this my wireless connection worked like a charm without additional setting  whatsoever (ndiswrapper etc). But today, when I want to test my conky, my laptop fail to connect to internet wirelessly. I can see ESSID for the network applet in the panel and when I turn on my wireless switch, the applet even change to wireless graph bar. However, that is all! I'm really stuck and have no idea to troubleshoot. Can anyone guide me to get back my wireless connection.

---

### Post by phidia on 2008-08-13
Open a terminal (Applications > Acessories > Terminal) and enter > iwconfig post the output of that.
There is a pretty comprehensive guide [here]("http://ubuntuforums.org/showthread.php?t=684495") too. I just inserted that in case you want to look there.

---

### Post by wariskampar on 2008-08-14
Here is the result:
aznan@aznan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
How come it is unassociated ESSID even after I turning on the wireless

---

### Post by wariskampar on 2008-08-14
I got this message when turning on the wireless;
Waiting for Network Key for 'essid'
What does it mean?

---

### Post by phidia on 2008-08-14
Basically when you get this: > Access Point: Not-Associated  you are not connecting. If you know the network name which is also the essid you can try and select that or create a new network using the correct network name.

---

