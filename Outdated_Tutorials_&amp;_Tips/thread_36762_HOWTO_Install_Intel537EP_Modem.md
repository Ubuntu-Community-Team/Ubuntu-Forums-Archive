---
title: "HOWTO: Install Intel537EP Modem"
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by nascent16 on 2005-05-24
There are plenty of guides for installing and configuring modems on this page, but I'm adding another because none of them worked for the Intel 537EP.

Before you do this you need to make sure you have the gcc package and the linux-header packages for your kernel version.

[list=1]
[*]Download the 2.60.80.1 driver (uncompiled) [here](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1230&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21). Make sure it's that one and not the .0 version.
[*]Download patch [here](http://www.dis-rj.com.br/537ep/)
[*]Unzip and untar both packages
[*]I recommend that at this point you login as root using "su"
[*]Apply patch to driver by going to the directory that the driver unzipped into and running
```

root@TROYNET01:/home/justint # patch -p0 < /directory/of/the/patch/patch-intel-537ep-kernel2610.diff

```
[*]Run (while still in the directory of the driver)
```

root@TROYNET01:/directory/of/driver # make clean

```
[*]Run
```

root@TROYNET01:/directory/of/driver # make 537

```
[*]Run
```

root@TROYNET01:/directory/of/driver # make install

```
[*]Theoretically the install should be done here. It wasn't for me.
[*]This driver doesn't work very nicely with the version of wvdial that is packaged with ubuntu, so if we link the modem to ttyS15 (an experimental port) we can get wvdial to recognize it. Run
```

root@TROYNET01:/any/directory # rm /dev/ttyS15

```
[*]Run
```

root@TROYNET01:/any/directory # ln -s /dev/537 /dev/ttyS15

```
[*]now the modem is linked to a place that wvdial can get it. I also recommend linking it to /dev/modem. The installer should have done this, so run
```

root@TROYNET01:/any/directory # ls -l /dev/modem /dev/537

```
If this shows up then it is properly linked. Otherwise run
```

root@TROYNET01:/any/directory # ln -s /dev/537 /dev/modem

```
[*]That's it. Run
```

wvdial wvtest.txt

```
to test. It should work! Then you can go to the modem's configuration panel in GNOME and configure as usual. It should autodetect the modem without a problem.
[/list]

---

### Post by marceloguedes on 2005-06-03
This HOWTO not run here! 

I install 'gcc package' and headers.
But when I run the step "make install" a error occur. The Intel537 module don't is make.

I try "modprobe Intel537" but nothing too.
Unfortunelly I don't can send the errors messages...

I am wait a solution. Thanks.

---

### Post by 55eel on 2005-06-29
I followed nascent16's advise but when I applied the patch I got a message:

"Reversed (or previously applied) patch detected!  Assume -R? [n]"

Any advise as to next step I should take.

---

### Post by nascent16 on 2005-07-12
Sounds like you already have the patch.... Why don't you try skipping that step and see if it works?

Justin

---

### Post by _hello_ on 2005-11-20
Hi, I have a INTEL537EP modem.

Are you able to send faxes, with efax, for example?
If so, how can you do this?


Also, if I do rm ttyS0, it deletes the port and I can't use it anymore. (even if I do ln -s /dev/537 /dev/ttyS15):

efax-0.9a: 47:38 Error: can't open serial port /dev/ttyS15: No such file or directory

How can I reinstall a port?


And is there a way just to send a command to the modem and verify what it answers ?

---

### Post by flickerfly on 2005-12-22
I believe the newer versions of the drivers remove the need for the patch steps. This is version 2.70.95. 

I wish I had found this first. It would have saved me a lot of time. :-) Thanks for solving my last problem.

---

### Post by bullet011 on 2006-01-13
[QUOTE=nascent16]There are plenty of guides for installing and configuring modems on this page, but I'm adding another because none of them worked for the Intel 537EP.

Before you do this you need to make sure you have the gcc package and the linux-header packages for your kernel version.

[list=1]
[*]Download the 2.60.80.1 driver (uncompiled) [here](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1230&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21). Make sure it's that one and not the .0 version.
[*]Download patch [here](http://www.dis-rj.com.br/537ep/)
[*]Unzip and untar both packages
[*]I recommend that at this point you login as root using "su"
[*]Apply patch to driver by going to the directory that the driver unzipped into and running
```

root@TROYNET01:/home/justint # patch -p0 < /directory/of/the/patch/patch-intel-537ep-kernel2610.diff

```
[*]Run (while still in the directory of the driver)
```

root@TROYNET01:/directory/of/driver # make clean

```
[*]Run
```

root@TROYNET01:/directory/of/driver # make 537

```
[*]Run
```

root@TROYNET01:/directory/of/driver # make install

```
[*]Theoretically the install should be done here. It wasn't for me.
[*]This driver doesn't work very nicely with the version of wvdial that is packaged with ubuntu, so if we link the modem to ttyS15 (an experimental port) we can get wvdial to recognize it. Run
```

root@TROYNET01:/any/directory # rm /dev/ttyS15

```
[*]Run
```

root@TROYNET01:/any/directory # ln -s /dev/537 /dev/ttyS15

```
[*]now the modem is linked to a place that wvdial can get it. I also recommend linking it to /dev/modem. The installer should have done this, so run
```

root@TROYNET01:/any/directory # ls -l /dev/modem /dev/537

```
If this shows up then it is properly linked. Otherwise run
```

root@TROYNET01:/any/directory # ln -s /dev/537 /dev/modem

```
[*]That's it. Run
```

wvdial wvtest.txt

```
to test. It should work! Then you can go to the modem's configuration panel in GNOME and configure as usual. It should autodetect the modem without a problem.
[/list][/QUOTE]
I have done everithing but it seems that tht /dev/537 is not made(i am sure of it)

---

### Post by flickerfly on 2006-01-14
Could someone post their wvdial.conf? I'm getting the error "Modem not responding" when I run wvdial.

I have these lines that may be pertinent in ~/wvdial.conf

Modem = /dev/modem
Baud = 115200
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Dial Command = ATM1L3DT

If I use Gnome-ppp, I get a bit further. Even though I enter a password at the start, the log reports:

Modem Initialized
Please enter password

When I get that, the line is sometimes busy and it doesn't seem to affect it.

---

### Post by johnrhance on 2009-07-08
Sorry to bump this very dead thread, but I could use some help installing this driver. Tried to download the drivers from the first link, but Intel has since removed them. Any ideas where I could find them?

---

