---
title: "Interface not created for Netgear N600 usb adapter."
date: 2012-12-27
forum: New to Ubuntu
---

### Post by heavyd1001 on 2012-12-27
Hello,

I am attempting to set-up a computer with Ubuntu 12.10 to act as a media centre. I am having problem setting up a Netgear N600 usb adapter.

I have installed ndiswrapper from the ubuntu software centre and have tried several drivers.

```
account_name@xxxx~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -i bcmn43xx32.inf 
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx32 ...
```>                                   **Re: Netgear WNDA 3100 v2 wireless adapter -- How to install?**             
                                                                No problem.  You seemed confident and resourceful so I omitted the details. I'll be  happy to explain. First, go to the location of the zip file I attached;  right-click it and select *Extract Here*.Now open a terminal and change directories to the location of the drivers I attached. For example:    
```
      cd Desktop/some_folder/Broadcom_bcm43xx_USB_32_64bit_v2_amended 
```Now we install the needed driver:     
```
      sudo ndiswrapper -i bcmn43xx32.inf 
```'i' means to **i**nstall. Now we check to see if it installed:
```
      ndiswrapper -l 
```'l' is for **l**ist. If it says driver installed, device present, we're nearly there. 

Was a wireless interface created?
     ```
      iwconfig 
```If you have a wlan0, click the Network Manager icon and try to connect.

Post back any errors, warnings, sparks or smoke, if any, and we'll try to fix it.
                                                                                               __________________I tried the above directions found [here ]("http://ubuntuforums.org/showthread.php?t=1964173")but the response to iwconfig was 
```
lo        no wireless extensions.

eth0      no wireless extensions.


```

Any help would be appreciated.

Thanks
Dan

---

### Post by squakie on 2012-12-27
With the adapter plugged in, type:

lsusb

and post the results back here.  It's rather unusual to actually need ndiswrapper these days, so perhaps what you were following was out of date.  We'll be able to tell more once you post that output request.

---

### Post by kurt18947 on 2012-12-28
There's another thread which indicates that NDISwrapper found in the repositories is buggy.  There was a link to an updated NDISwrapper.  Unfortunately there are a few WiFi adapters that do require NDISwrapper,  there is currently no  linux driver for them.  I don't know enough about NDISwrapper to comment further.

And yes, the command "lsusb" in a terminal then copy-paste here should be helpful.

---

### Post by squakie on 2012-12-29
If you find any of the old threads about downloading and possibly compiling ndiswrapper - don't.  Those are old threads.

Still waiting on the lsusb (unless I missed it in your original post) - this will tell us the manufacturer/product id that the hardware sees, so we can identify the chipset.  Once we have that information we can go from there.

*IF* ndiswrapper is needed for your adapter I can help you with that when all other options are exhausted.

---

