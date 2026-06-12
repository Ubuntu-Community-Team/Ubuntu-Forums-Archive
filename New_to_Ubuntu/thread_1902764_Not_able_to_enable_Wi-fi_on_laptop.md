---
title: "Not able to enable Wi-fi on laptop"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by SACHINVD on 2011-12-31
Hello

I turned on laptop's switch for wireless.
But when I turned on wireless from network .. it gets turned off immediately.> 

Following is my wireless adapter
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


Output of command iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.


Output of iwup wlan0
> Ignoring unknown interface wlan0=wlan0.

what is the problem .. why I am not able to start wireless on lappy ?

Thanks !

---

### Post by anewguy on 2011-12-31
Try this in a teminal window: sudo rmmod -F wmi

You will probably need to blacklist it also.

If you dual boot with Windows you should make sure to remove all locks there.

Then lsmod and be sure ath9k shows in the list.

Dave ;)

---

### Post by SACHINVD on 2012-01-01
Hi Dave !
Thanks for your help !

My wireless started working after I removed wmi module.

---

### Post by anewguy on 2012-01-01
Glad it's working for you.  Just play it forward when you see someone else post the same problem.

In the mean time, please use the Thread Tools at the top of the thread and mark the thread as "Solved".

Dave ;)

---

