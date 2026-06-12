---
title: "Trying to install ATT aircard"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by jesse100 on 2008-05-31
I am trying to get an aircard (Sierra 881). I am completely stumped. I will start with my first holdup. What exactly is "extracting the Kernel?" All I know is that I have ubuntu 7.04 feisty fawn. I think my kernal is 2.6.20.15

Could someone help this newbie? 

Jesse

The addy for the following info is: [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=607)

Follow these steps to install the patch:

   1. Extract the Kernel by typing the following command:

                  # tar -jxf linux-2.6.x.xtar.bz2
   2. Download the Patch from this location and extract it to the same base directory as you extracted the Kernel to.
   3. Apply the patch by typing the following commands:

                  # cd linux-2.6.x.x
                  # patch -p1< ../the-patch-file.patch
   4. Copy the sierra.c driver into the usbserial directory (Linux-2.6.x.x/drivers/usb/serial).
   5. Compile and install the Kernel. (Check with your Linux distribution for more details).
                  # make clean
                  # make all   
                  # make modules_install
                  # make install
   6. Reboot and insert the TRU-Install device. It should be identified as USB modem device.

---

