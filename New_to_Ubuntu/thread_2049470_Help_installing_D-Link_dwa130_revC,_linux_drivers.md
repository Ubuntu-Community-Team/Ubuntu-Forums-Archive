---
title: "Help installing D-Link dwa130 revC, linux drivers"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Valsion on 2012-08-28
Hi there,

   So I've got a D-Link wireless adapter that connects through USB, model DWA-130, version C1. It seems D-Link has provided drivers for linux, version 2.6, which I have attempted to install on a standard desktop installation of Ubuntu 12.04. 
   I did some reading on using the terminal to compile from source code, but I am yet having trouble. Here's a copy and paste of the terminal text: 
```
                                   n00b@n00b-cluster-c:~$ cd /home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008  
 n00b@n00b-cluster-c:~/Desktop/rtl8192u_linux_2.6.0006.1031.2008$ sudo make  
 [sudo] password for n00b:  
 make: Warning: File `Makefile' has modification time 2.1e+08 s in the future  
 make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'  
 make[1]: Warning: File `/usr/src/linux-headers-3.2.0-23-generic/arch/x86/Makefile' has modification time 3.1e+08 s in the future  
 make[2]: Warning: File `scripts/Makefile.lib' has modification time 3.1e+08 s in the future  
   CC [M]  /home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_rx.o 
 In file included from /home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_rx.c:46:0: 
 /home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211.h:2107:24: error: field ‘ps_task’ has incomplete type  
 make[2]: *** [/home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_rx.o] Error 1  
 make[1]: *** [_module_/home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211] Error 2  
 make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'  
 make: *** [all] Error 2  
 n00b@n00b-cluster-c:~/Desktop/rtl8192u_linux_2.6.0006.1031.2008$ make install  
 make: Warning: File `Makefile' has modification time 2.1e+08 s in the future  
 make[1]: Entering directory `/home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211'  
 make[1]: Warning: File `Makefile' has modification time 2.1e+08 s in the future  
 make -C /lib/modules/3.2.0-23-generic/build M=/home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008 CC=gcc modules 
 make[2]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'  
 make[2]: Warning: File `/usr/src/linux-headers-3.2.0-23-generic/arch/x86/Makefile' has modification time 3.1e+08 s in the future  
 make[3]: Warning: File `scripts/Makefile.lib' has modification time 3.1e+08 s in the future  
 make[3]: warning:  Clock skew detected.  Your build may be incomplete.  
   Building modules, stage 2.  
 make[3]: Warning: File `scripts/Makefile.lib' has modification time 3.1e+08 s in the future  
   MODPOST 0 modules  
 make[3]: warning:  Clock skew detected.  Your build may be incomplete.  
 make[2]: warning:  Clock skew detected.  Your build may be incomplete.  
 make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'  
 rm -fr /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/RTL8192U  
 mkdir -p /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/RTL8192U  
 mkdir: cannot create directory `/lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/RTL8192U': Permission denied  
 make[1]: *** [install] Error 1  
 make[1]: Leaving directory `/home/n00b/Desktop/rtl8192u_linux_2.6.0006.1031.2008/ieee80211'  
 make: *** [install] Error 2  
  n00b@n00b-cluster-c:~/Desktop/rtl8192u_linux_2.6.0006.1031.2008$ sudo reboot

```
Then after the reboot:
```
                                   
n00b@n00b-cluster-c:~$ sudo ifconfig wlan0 up  
 [sudo] password for n00b:  
 SIOCSIFFLAGS: Resource temporarily unavailable  
 n00b@n00b-cluster-c:~$ sudo iwconfig wlan0  
 wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           Retry min limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
           Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 n00b@n00b-cluster-c:~$
  
```


Here are the installation instructions provided by the manufacturer:
"                           <<Method 1>>  
 Runing the scripts accomplish all operations including building up modules  
 from the source code, installing driver to the kernel and starting up the nic.  
     1. Build up the drivers from the source code  
       make  
 

     2. Install the driver to the kernel  
           make install  
           reboot  
 

     3. bring up wlan if nic is not brought up by GUI, such as NetworkManager  
       ifconfig wlan0 up  
       Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name,  
                 since it may change wlan0 to wlan1,etc.  
 

 <<Method 2>>  
 Or only load the driver module to kernel and start up nic.  
      1. Build up the drivers from the source code  
       make  
          2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/  
             cp -rf firmware/RTL8192U /lib/firmware  
           or  
             cp -rf firmware/RTL8192U /lib/firmware/(KERNEL_VERSION)  
           Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware  
 

      3. Load driver module to kernel and start up nic.  
       ./wlan0up  
           Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out  
                 after run ./wlan0up, please run ./wlan0down first, then it should  
                 be ok..  
       Note: If you see the message of "unkown symbol" during ./wlan0up, it  
         is suggested to build driver by <<Method 1>>".





This is my first post; please let me know if any more information is required. I'd greatly appreciate any assistance with the issue. Thank you so much in advance. 

Alex

---

