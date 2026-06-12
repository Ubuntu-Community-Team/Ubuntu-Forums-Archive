---
title: "Brother MFC 240c Scanner"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by dragon2600 on 2012-06-25
Hi all

i really need some help with installing my printer scanner (brother mfc 240c)
 I have the printer working with no problems but I cant get the scanner to work at all, I have followed all the guides that i can find on the web and this forum but with no results.

I am new to linux so I could really use some help.

Thanks

---

### Post by Daveth on 2012-06-25
Hallo. Welcome to the Ubuntu forum. 
So, what  happens if you fire up Simple Scan? Anything? Did you try installing Brother's Linux scanner driver yet? Be useful to know what you tried and what failed miserably for you. The scanner does seem to work under Linux, though it seems to need a small tweak to get you to run it as a user rather than a super-user. But first things first! I assume you are running Precise Pangolin?

---

### Post by dragon2600 on 2012-06-26
Thanks for the reply, I'll answer your questions in order.

Simple scan :- No Scanners detected
Yes i installed the brother scanner driver (brscan2-0.2.5-1.amd64deb)
I'm running 12.04 LTS x64

---

### Post by plucky on 2012-06-26
> **dragon2600 said:**
> Thanks for the reply, I'll answer your questions in order.

Simple scan :- No Scanners detected
Yes i installed the brother scanner driver (brscan2-0.2.5-1.amd64deb)
I'm running 12.04 LTS x64

From [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)


> Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

Have you done this?

Also post the output from a terminal for ```
dpkg -l | grep -i brother
```

Good Luck

---

### Post by dragon2600 on 2012-06-26
Yes Ive done all of the above.

and here is the output 

ii  brother-cups-wrapper-bh7               1.0.0-10-0ubuntu5                       Cups Wrapper drivers for bh7 brother printers
ii  brother-cups-wrapper-common            1.0.0-10-0ubuntu5                       Common files for Brother cups wrapper packages
ii  brother-lpr-drivers-bh7                1.0.1-1-0ubuntu5                        LPR drivers for bh7 brother printers
ii  brother-lpr-drivers-common             1.0.0-4-0ubuntu1                        Common files for brother-lpr-drivers packages
ii  brscan-skey:i386                       0.2.1-3                                 Brother Linux scanner S-KEY tool
ii  brscan2                                0.2.5-1                                 Brother Scanner Driver
ii  printer-driver-ptouch                  1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

Thanks.

---

### Post by plucky on 2012-06-26
That looks ok.

What happens if you start simple scan with sudo permissions?
```
gksudo simple-scan
```

Can you access the scanner?

Please post output for ```
lsusb | grep -i brother
scanimage --l
```

---

### Post by kurt18947 on 2012-06-26
If I may butt in a bit, this thread may be relevant if the O.S. is 64 bit and 11.10 or 12.04.  In addition to the rules edit,  you may have to copy or symlink some files.  There is a link to the Brother FAQ in this thread:

[http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother](http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother)

Which files get copied/linked vary with brscan #.

---

### Post by dragon2600 on 2012-06-29
> **plucky said:**
> That looks ok.

What happens if you start simple scan with sudo permissions?
```
gksudo simple-scan
```Can you access the scanner?

Please post output for ```
lsusb | grep -i brother
scanimage --l
```


ok sorry for the delay, lost of work the last couple of days.

If I start simple scan with root still nothing, and the output for the commands is,

Bus 003 Device 002: ID 04f9:01ab Brother Industries, Ltd MFC-240C

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by plucky on 2012-06-29
This is what I get for those commands

> lsusb | grep -i brother
Bus 002 Device 003: ID 04f9:0190 Brother Industries, Ltd DCP-120C

> scanimage --l
device `brother2:bus1;dev3' is a Brother DCP-120C USB scanner

The other thing that you could try is to install **sane-utils** and then reboot.
```
sudo apt-get install sane-utils
```

Then run the two commands and see if you can now see the scanner.

Good Luck

---

### Post by dragon2600 on 2012-06-29
Ive done all that, this is giving me a real headache ubuntu still says I have no scanner!

---

### Post by plucky on 2012-06-29
> Bus 003 Device 002: ID 04f9:01ab Brother Industries, Ltd MFC-240C


Last thing you can try is to give permission to the USB port with the command ```
sudo chmod a+w /dev/bus/usb/003/002
``` where /003/002 is given by the Bus and Device number above.

Other than that,I don't know what else to recommend.

Good Luck

---

### Post by wallaroo on 2012-06-29
dragon2600

You haven't responded to kurt18947's post yet.

I run several Brother Printer/Scanner units on Ubuntu and I know that if you don't copy the files in /usr/lib64 to /usr/lib the scanner will definitely not be found.

---

### Post by dragon2600 on 2012-06-30
> **wallaroo said:**
> dragon2600

You haven't responded to kurt18947's post yet.

I run several Brother Printer/Scanner units on Ubuntu and I know that if you don't copy the files in /usr/lib64 to /usr/lib the scanner will definitely not be found.


Sorry I didnt answer his question, but I did all of that before asking for help, I didnt mean to ignore him

---

### Post by dragon2600 on 2012-06-30
> **plucky said:**
> Last thing you can try is to give permission to the USB port with the command ```
sudo chmod a+w /dev/bus/usb/003/002
``` where /003/002 is given by the Bus and Device number above.

Other than that,I don't know what else to recommend.

Good Luck

Tried this command and rebooted still no scanner detected GGRR, 

I have virtual box with a copy of Win7 would it be possible to pass the scanner though to the V. machine?

---

### Post by kurt18947 on 2012-06-30
> **wallaroo said:**
> dragon2600

You haven't responded to kurt18947's post yet.

I run several Brother Printer/Scanner units on Ubuntu and I know that if you don't copy the files in /usr/lib64 to /usr/lib the scanner will definitely not be found.

I don't know if it's necessary but I also created a user/lib/sane folder like that found in usr/lib64/sane and copied those files over as well, rather than copying user/lib64/sane files to usr/lib as the instructions seem to indicate.

---

### Post by Ruhani04 on 2012-10-06
This is what brother says:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

---

