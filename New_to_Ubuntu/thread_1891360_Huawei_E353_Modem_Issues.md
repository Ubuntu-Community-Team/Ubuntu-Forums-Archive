---
title: "Huawei E353 Modem Issues"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by derek_botha on 2011-12-05
Hi All

Can i ask if anyone can assist in order to get a Huawei E353 modem to work in 11.04?

I have tried all the hack's on the all the support forums without any success. (From saki3g, sudo aptitude install usb-modeswitch, and all else)

Any assistance would be greatly appreciated

---

### Post by derek_botha on 2011-12-05
just to add, the modem comes up as a cd drive the whole time???

---

### Post by tomski on 2011-12-05
i got the following from a forum but alas cannot remember where BUT you can use it as a base to get yours going but you will need to use:
LSUSB 

to get the relevant product & venor ID's:


**Step 1 - Add the required usb_modeswitch config for the E367:**



Add the following lines to the end of the /etc/usb_modeswitch.conf file:



```
########################################################

# Huawei E367



EnableLogging=1



DefaultVendor= 0x12d1

DefaultProduct=0x1446



TargetVendor= 0x12d1

TargetProductList="1001,1406,140b,140c,1412,141b,14ac,1506"



CheckSuccess=20



MessageEndpoint= 0x01

MessageContent="55534243123456780000000000000011062000000100000000000000000000"
```





**Step 2:**



Run the usb_modeswitch command:



```
root@zeroshell root> usb_modeswitch
```





**Step 3 (May not be required): **



If you have another USB serial device connected to your Zeroshell appliance, you will need to unload the usbserial module by running "rmmod usbserial" 

or even easier, just unplug the other serial device device to unload the usbserial driver.



You can confirm this has been done successfully, by running the "lsmod" command and seeing if the usbserial module is in the list. 

As long as it's not present, you can proceed.





**Step 4: **

Run the modprobe command to insert the usbserial module and bind to the E367's serial ports:



```
root@zeroshell root> modprobe usbserial vendor=0x12d1 product=0x1506


```

Step 5:

Confirm the driver has loaded and created the ttyUSB* devices by running "ls /udev/ttyUSB*



If you're successful, you should get output similar to the below:



```
root@zeroshell root> ll /udev/ttyUSB*

crw-rw---- 1 root root 188, 0 Jun 6 14:53 /udev/ttyUSB0

crw-rw---- 1 root root 188, 1 Jun 6 14:51 /udev/ttyUSB1

crw-rw---- 1 root root 188, 2 Jun 6 14:51 /udev/ttyUSB2

crw-rw---- 1 root root 188, 3 Jun 6 14:53 /udev/ttyUSB3
```



**Step 6: **



Finally, configure your new PPP device as normal through the web interface. 

You will need to use /udev/ttyUSB0 as the actual modem device for establishing the PPP connection. 

ttyUSB1 and 2 appear to have no functionality (you cannot communicate with the modem via them) and ttyUSB3 is the "management" interface. 

This allows you to query signal strength (at+csq, etc) while the modem is online.





I hope the above is of assistance to somebody. 

Maybe the above changes could be incorporated into the next release, to avoid having to take the above steps on each boot? 

I now use a small bash script to automate the above steps:





```


#!/bin/bash



cd /Database/extradata



# Copy modeswitch config file to /etc

echo '########################################################

# Huawei E367



EnableLogging=1



DefaultVendor= 0x12d1

DefaultProduct=0x1446



TargetVendor= 0x12d1

TargetProductList="1001,1406,140b,140c,1412,141b,14ac,1506"



CheckSuccess=20



MessageEndpoint= 0x01

MessageContent="55534243123456780000000000000011062000000100000000000000000000"' >> /etc/usb_modeswitch.conf





# Run modeswitch command

usb_modeswitch



# Run modprobe command

modprobe usbserial vendor=0x12d1 product=0x1506
```[/quote]

---

