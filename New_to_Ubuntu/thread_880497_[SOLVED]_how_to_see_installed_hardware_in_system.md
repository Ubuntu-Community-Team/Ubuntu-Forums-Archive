---
title: "[SOLVED] how to see installed hardware in system"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by steve joe bob on 2008-08-05
i was wondering if there was something along the lines of device manager in ubuntu? i'm having trouble with a wireless card and i don't even know if the driver is loaded for it or if the system is seeing it. i installed something on the system that supposedly allows you to use windows wireless drivers and i installed the one for the card but am still unable to connect to the wireless network. (i know the strength is good because i have a 2nd computer literally sitting right next to it and it connects just fine with plenty of signal strength) any input would help. thnx in advance

---

### Post by cariboo on 2008-08-05
If you open a Applications-->Accesories-->Terminal and type:

```
lspci
```

It will list all the installed hardware. It won't tell you if it working or not, but if your wireless card is listed, then there is hope. I would suggest you post the list in your next post, and we will see if we can help you to get it working properly.

Jim

---

### Post by zipperback on 2008-08-05
Network interface listing

```

ifconfig

```

Wireless interface listing

```

iwconfig

```

Also the following is helpful

Shows recognized hardware
```

lspci

```

And for usb hardware

```

lsusb

```


- zipperback
:popcorn:

---

### Post by hyper_ch on 2008-08-05
```

lshw -html > ~/Desktop/hardware.html

```

---

### Post by zipperback on 2008-08-05
> **steve joe bob said:**
> i'm having trouble with a wireless card and i don't even know if the driver is loaded for it or if the system is seeing it. 



Please post the output of:

```

lspci

```

Then we can help you get your wifi working.

Please tell us what kind of computer this is on also.

I have an Acer Aspire 5050-3371 laptop.

- zipperback
:popcorn:

---

### Post by steve joe bob on 2008-08-06
ok so i have some screen shots of what i see when i run those commands.... doesn't make a whole lotta sense to me but hopefully to you guys it will!

---

### Post by sujoy on 2008-08-06
in the first pic the description and product info is pretty straightforward, the rest of the info is geared more towards the actual bridges, interfaces and ports used by the  products.

now if you mean device manager as in you can install and unistall devices from then I guess you just have to use these as info and install necessary drivers manually or edit  the corresponding files.

now i too have a broadcom card but i was lucky to get mine working with restricted hardware drivers from ubuntu, you could try that

---

### Post by steve joe bob on 2008-08-07
hey guys thnx for all your help. i got the card working (it was very easy.... i probably should've started with this) all's i had to do was install all the recommended updates, restart, then it told me that for the hardware to wrk i needed to download a firmware update that did not come with ubuntu 8.04 and everything wrked perfectly. just gotta stay current with the updates i guess!

---

### Post by lost. on 2009-04-14
Just stumbled upon this thread on the internet, and I had a quick question:

I tried the suggested ```
lshw -html > ~/Desktop/hardware.html
``` from the above post, and it worked great.  It gave me this output:

[http://imgur.com/LE03K.png]("http://imgur.com/LE03K.png")

I'm not able to enable desktop effects. Is my card too old, or is it significant that the card is in white while every other piece of hardware is in yellow (for example, a driver is not installed).

Thanks much.

---

### Post by Jakey_TheSnake on 2009-04-14
If you can't enable desktop effects, you probably haven't installed drivers for your graphics card. 

Do you have any such options under System > Administration > Hardware Drivers?

edit: otherwise you will _probably_ have to download this driver: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

(Click download, accept, then click on the name of it again, save as) 

Save it to your desktop, right click and press "Extract here", then install :)

---

### Post by lost. on 2009-04-14
Awesome! I've got the file, but how do I install it? There's an install.sh, but it does nothing when I double click it.

---

### Post by lost. on 2009-04-14
Quick update -- I looked it up and I apparently have to do a "sudo make install" to create the installer. I ran that, and it gives me errors:

```
Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


```

What does this mean?

---

