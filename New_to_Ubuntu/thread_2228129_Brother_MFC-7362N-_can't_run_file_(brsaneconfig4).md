---
title: "Brother MFC-7362N- can't run file (brsaneconfig4)"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by psyclone on 2014-06-05
Hi, believe I've installed the Scan Driver for Model: MFC-7362N (Brother), The Ubuntu Software Center states to run " brsaneconfig4" in terminal.
How can I do that? Basic question  I know, but essential. 

Cheers.

---

### Post by cwmoser on 2014-06-06
Press Control + Alt + T to bring up the Terminal command prompt.

---

### Post by cwmoser on 2014-06-06
I don't know if this is helpful or not, but here are my notes when I installed the
Scanner driver for my Brother MFC440CN:

[B]Brother MFC440CN:
Install Scanner:

1. Install the Brother scanner driver

$ sudo  dpkg  -i  brscan2-0.2.4-0.amd64.deb

2. To use your machine as a network scanner, you need to set the friendly name, model name and IP address or node name in the driver using the commands below:

brsaneconfig2 -a name=SCANNER model=MFC-440CN ip=192.168.0.212

3. You can check the result by running the command:

brsaneconfig2 -q

If the setting is done correctly, you will see the result as below:
0 SCANNER1 "MFC-440CN" I:192.168.0.212[/B]

---

### Post by psyclone on 2014-06-06
Thanks for your posts,
What I meant to say in my original post was; what basic command do I use and how to use them-to run "brscanconfig4" (or a reference to Ubuntu Documentation). I just have a usb connection from the printer to the pc. I have the printing driver installed an working, but the when I hit scan, it states that the data is being sent but the pc doesn't pick it up.

---

### Post by plucky on 2014-06-07
From [Here](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04)

> Ubuntu 10.10, 11.4, 11.10, 12.04, 12.10, 13.04, 13.10
    1. Click here to download the file.(brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1, 2KB)
    2. Run the command.
    Command: dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb

Maybe that is the problem.

Can you post output for ```
dpkg -l | grep -i brother
```

Have you installed "sane-utils"?

```
sudo apt-get install sane-utils
```

Also try to run simple-scan in superuser mode ```
sudo simple-scan
``` and then try to scan,If that works then you probably need to intall the udev-rule deb and then reboot.

> what basic command do I use and how to use them-to run "brscanconfig4"

That should only be used if you are installing as a Network scanner.


Good Luck

---

### Post by psyclone on 2014-06-07
Thanks for your post.
I'm able to run simple scan, and then use **gscan2pdf** to combine & convert jpg files into a single pdf. I'm just unable to use gscan2pdf to scan and convert. I was able to do it all-in-one with my last printer.
Cheers.

---

### Post by psyclone on 2014-06-07
output:

e-desktop@edesktop-MS-7788:~$ dpkg -l | grep -i brother

ii  brother-cups-wrapper-common                 1.0.0-10-0ubuntu5                       Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                  1.2.1-0ubuntu3                          Cups Wrapper drivers for extra brother printers
ii  brother-cups-wrapper-laser1                 1.0.2-1-0ubuntu7                        Cups Wrapper drivers for laser1 brother printers
ii  brother-lpr-drivers-common                  1.0.0-4-0ubuntu1                        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                   1.2.0-2-0ubuntu4                        LPR drivers for extra brother printers
ii  brother-lpr-drivers-laser1                  1.0.0-3-0ubuntu5                        LPR drivers for laser1 brother printers
ii  brscan-skey                                 0.2.4-1                                 Brother Linux scanner S-KEY tool
ii  brscan4                                     0.4.2-1                                 Brother Scanner Driver
ii  cupswrappermfc7362n:i386                    2.0.4-2                                 Brother MFC7362N CUPS wrapper driver
ii  mfc7362nlpr:i386                            2.1.0-1                                 Brother MFC-7362N LPR driver

---

### Post by psyclone on 2014-06-07
I installed **brother-udev-rule-type1, **and I'm finally able to run gscan2pdf. Thanks again.

---

