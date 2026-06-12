---
title: "Mystery LEDS (MLED &amp; WLED) on a ASUS A2500H Laptop"
date: 2010-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by georgemc on 2010-09-01
Working Mystery LEDS on a ASUS A2500H Laptop 
  
 The LEDS in question are those two on the front/lower/left side next to the Green Power/On and the Orange Charging LED on a ASUS A2500H.  I only have one Laptop, however, it is my understanding that this could/should work on other ASUS laptops.  Feel free to explore and add. 
  
 I searched the Internet and found very little on this subject.  Two places with good information are: 
  
 [http://dev.iksaif.net/projects/acpi4asus](http://dev.iksaif.net/projects/acpi4asus) 
 [http://sourceforge.net/projects/acpi4asus](http://sourceforge.net/projects/acpi4asus) 
  
 Some of this information is old and cryptic and required some digging, trial & error, and side tracking to ACPI and how that works.  Thank you to the many contributors on all the sites I visited and researched. 
  
  
 _My system specifications: _
 ASUS A2500H  with a 
 Intel IPW2200 WIFI PCI card 
 2.8GHz single threaded CPU 
 1.5GBytes RAM 
 Ubuntu 10.04.1LTS Lucid Lynx 
  
  
 _The Mystery LEDS _
  
 The Blue one is identified as MLED (M for Mail) and the Yellow one is identified as WLED (W for Wifi or Wlan).  You can easily check your system if the kernel already has the options enabled.  If you have the files: 
  
 /sys/class/leds/asus::mail/brightness  and 
 /sys/devices/platform/asus_laptop/wlan 
  
 then your kernel already supports the M|WLEDs and the modules are loaded and you can skip to "My practical applications". 
  
 _Need to re-configure the kernel_
 

 If the kernel does not support the LEDs then to make the LEDs work on the ASUS A2500H laptop there needs to be several things put into place. 
  
 First and foremost you need to recompile the kernel with the following switches on: 
  
 CONFIG_LEDS_CLASS 
 CONFIG_BACKLIGHT_CLASS_DEVICE 
 CONFIG_ASUS_LAPTOP 
  
 For kernel compiling instructions see the thread "http://ubuntuforums.org/showthread.php?t=311158".  A big Thank You to Master_Kernel. 
  
 Best to identify the config options as Modules where possible and USE AT YOUR OWN PERIL.  When you have the kernel compiled and the asus_laptop module loaded then you should be able to find the LED files: 
  
 /sys/class/leds/asus::mail/brightness  and 
 /sys/devices/platform/asus_laptop/wlan 
  
 The default settings of the "asus_laptop" module should be fine, however, I enabled the WLAN and disabled the Bluetooth option. This are my /etc/modules entry: 
  
 asus_laptop wapf=1 wlan_status=1 bluetooth_status=0 
  
 I chose to set the Bluetooth OFF, not using it at this time.  The wlan_status is the main option to be enabled. 
  
 When all is in place you can manipulate the LEDs with this: 
  
 ```
 
 #Blue 
 sudo sh -c "echo '0' > /sys/class/leds/asus::mail/brightness" 
 sudo sh -c "echo '1' > /sys/class/leds/asus::mail/brightness" 
  
 #Yellow 
 sudo sh -c "echo '1' > /sys/devices/platform/asus_laptop/wlan" 
 sudo sh -c "echo '0' > /sys/devices/platform/asus_laptop/wlan" 
 
``` That should be it.  Now you can turn those mystery LEDs on and off. 
  
 

 _My practical applications. _
  
 WLED follows WiFi connection. 
  
 My Intel ipw2200 WiFi controller module has a parameter or option LED.  Not sure why the ipw2200 led=1 entry does not do what I think it should do, so I modified /etc/NetworkManager/dispatch.d/01ifupdown and added 'echo "1" > /sys/devices/platform/asus_laptop/wlan' and 'echo "0" > /sys/devices/platform/asus_laptop/wlan' to make the WLED follow the connection state of the WiFi card.  Connected to some where == LED ON, not connect == LED off.  Also FN-F2 on my Laptop turns the WIFI power on/off, even though it is not labeled on the keyboard.   Simply edit the file and add the two lines in the appropriate places.  Scroll down a little, in the up and down section.
  
 /etc/NetworkManager/dispatch.d/01ifupdown 
 ```
 
 #!/bin/sh -e 
 # Script to dispatch NetworkManager events 
 # 
 # Runs ifupdown scripts when NetworkManager fiddles with interfaces. 
  
 if [ -z "$1" ]; then 
     echo "$0: called with no interface" 1>&2 
     exit 1; 
 fi 
  
 # Fake ifupdown environment 
 export IFACE="$1" 
 export LOGICAL="$1" 
 export ADDRFAM="NetworkManager" 
 export METHOD="NetworkManager" 
 export VERBOSITY="0" 
  
 # Run the right scripts 
 case "$2" in 
     up) 
     export MODE="start" 
     export PHASE="up" 
  
     if [ -d /var/run/network/ ] ; then 
         tmpfile=`mktemp -t` 
         if [ -e /var/run/network/ifstate ] ; then 
             cat /var/run/network/ifstate | grep -v ^$IFACE= > $tmpfile || true 
         fi 
         echo $IFACE=$IFACE >> $tmpfile 
         mv $tmpfile /var/run/network/ifstate 
     fi 
 # added to work the ASUS Mystery LEDS - Home Brew 
 echo "1" > /sys/devices/platform/asus_laptop/wlan 
 # end of add 
     exec run-parts /etc/network/if-up.d 
     ;; 
     down) 
     export MODE="stop" 
     export PHASE="down" 
  
     if [ -e /var/run/network/ifstate ] ; then 
         tmpfile=`mktemp -t` 
         cat /var/run/network/ifstate | grep -v ^$IFACE= > $tmpfile || true 
         mv $tmpfile /var/run/network/ifstate 
     fi 
 # added to work the ASUS Mystery LEDS - Home Brew 
 echo "0" > /sys/devices/platform/asus_laptop/wlan 
 # end of add 
     exec run-parts /etc/network/if-down.d 
     ;; 
     pre-up) 
     export MODE="start" 
     export PHASE="pre-up" 
     exec run-parts /etc/network/if-pre-up.d 
     ;; 
     post-down) 
     export MODE="stop" 
     export PHASE="post-down" 
     exec run-parts /etc/network/if-post-down.d 
     ;; 
     *) 
     echo "$0: called with unknown action \`$2'" 1>&2 
     exit 1 
     ;; 
 esac 
 
``` _Another application: MLED follows the AC/Battery status_ 
  
 Since I am not using any kind of mail on this system I commandeered the MLED to follow the AC/Battery status.  When on AC then the MLED is off and when on Battery the MLED is on. 
  
 Yes the screen dims when on battery, however, that is adjustable and I at times miss the "On Battery" change in the indicator in the top panel.  I find that the Blue LED stands out well enough. 
  
 I added my Home Brew "Power_indicator.sh" script to the directories "/etc/laptop-mode/batt-start[stop]".  This will now light the Blue LED when we go on batteries and turn it off when we are back on AC. 
  
 /etc/laptop-mode/batt-start|stop/Power_indicator.sh 
 ```
 
 #!/bin/bash 
 #Power_indicator.sh 
 #Home Brew - turn on Blue LED if on Battery (MLED) not using it for mail 
  
 state=`/bin/cat /sys/class/power_supply/AC/online` 
  
 if [ "$state" == "0" ] 
 then 
     /bin/echo '1' > /sys/class/leds/asus::mail/brightness 
 else 
     /bin/echo '0' > /sys/class/leds/asus::mail/brightness 
 fi 
  
 # end Home Brew 
 
```  _Summary_
 

 The two practical application examples work for me and I can see that other applications can be useful, not only a “You have mail” indicator.
 

 Reading/digging through the various documents I feel that many other ASUS models and some IBM models should be able to utilize some of this write up to get those mystery LEDs working.
 

 Please add your experience and “practical applications”
 

 George

 _Reference: _
 [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)   # Master Kernel Thread 
 [http://dev.iksaif.net/projects/acpi4asus](http://dev.iksaif.net/projects/acpi4asus) 
 [http://sourceforge.net/projects/acpi4asus/](http://sourceforge.net/projects/acpi4asus/)

---

