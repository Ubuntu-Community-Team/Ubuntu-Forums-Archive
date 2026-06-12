---
title: "Touchpad and keyboard freeze after a few minutes use, but ONLY on battery power"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by Winchman on 2012-08-25
Hi,

  I am new to Ubuntu, having been running Ubuntu 12.04 for only one week. I am running it on a Medion Akoya E1222 netbook. The problem I have is the touchpad and keyboard freeze after a few minutes use, but ONLY on battery power. All works fine when plugged in to mains power.
 I have read up on various solutions to this problem, but I am confused as to what to try. Most solutions appear to revolve around making some changes to the power settings. However in my case 'power management' would appear to be already set to 'off' (see below) and also I cannot see that pm-utils is installed.
 

 iwcofnig reads as follows:
 

 mps@mps-E122X:~$ iwconfig 
 lo        no wireless extensions. 
  
 wlan0     IEEE 802.11bgn  ESSID:"Belkin_0DAA59"   
           Mode:Managed  Frequency:2.432 GHz  Access Point: 94:44:52:0D:AA:59    
           Bit Rate=150 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off 
           Power Management:off 
           Link Quality=54/70  Signal level=-56 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:6   Missed beacon:0 
  
 eth0      no wireless extensions. 
  
 mps@mps-E122X:~$  
 

 I really need to solve this because if I don't there is little point in taking the netbook with me when travelling.
 Can anyone offer some advice as to how to solve this problem?
 

 Thank you

---

### Post by 2F4U on 2012-08-25
I am a bit curious, but how can you be sure that just keyboard and mouse freeze, and not the whole machine? If you have a second computer available, can you try to ping or ssh to the netbook?
If I were you, I would start by looking into the system log file after such a freeze and see if you can get any hints on the cause of the problem.

---

### Post by Winchman on 2012-08-25
Thanks.
As I am totally new to all this can you give me some clue as to which entries in the log file I should look out for that might give an indication of the problem?

---

