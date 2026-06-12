---
title: "Scanner fails once, works twice with XSane"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-09-23
I've got a Canon Lide 100 flatbed USB scanner that I use with XSane.

When I plug in the scanner and run Xsane, when I hit Scan, comes back with an error saying it cannot communicate with the scanner.

Ok.

Leave scanner plugged in and run XSane again, hit Scan, no problems, works a treat.

Does same on my Asus laptop running Ubuntu 12.04.

Ideas?

---

### Post by Kirboosy on 2013-09-23
It might take a second for it to register and setup the connection to the device.How long of a wait before it starts working properly?

Can you copy and paste the exact error that it is giving you?

---

### Post by Senior_Buckethead on 2013-09-24
Thanks for the reply. I start XSane, the scanner fails, so I shut XSane, and re-open it, scanner works fine. I have tried leaving XSane, once it has detected the scanner, for a couple of minutes before hitting scan. Doesn't seem to make any difference. I find I need to quit XSane, re open it, and then hit Scan. Works every time like that.

Here is the error message I get when I first start Xsane, after selecting which scanner.
[IMG]http://glennstuartmorrissey.bugs3.com/images/error.jpg[/IMG]

---

### Post by Kirboosy on 2013-09-24
I did a quick google with your model number and found this page. I don't think you have to compile SANE but maybe setting permissions will help??
[URL="http://bdhacker.wordpress.com/2011/04/25/canon-lide-100-scanner-in-ubuntu-with-sane-installation-permission-fixes/"][SIZE=2]
[/SIZE][/URL][h=1][[SIZE=2]Canon Lide 100 Scanner in Ubuntu with sane: Installation & Permission Fixes[/SIZE]]("http://bdhacker.wordpress.com/2011/04/25/canon-lide-100-scanner-in-ubuntu-with-sane-installation-permission-fixes/")[/h]
Hope that helps!
~Caboose

---

### Post by tgalati4 on 2013-09-24
Open a terminal and run *xsane*.  Post any useful errors.  The first time you connect, there is usually a delay as the light-bulb warms up, so I would expect the first error.  But after that, as long as the scanner is plugged in and warmed up, you should be able to scan continuously.  I don't know if you can update the firmware of the scanner, but that might help.

---

### Post by Jonathan Precise on 2013-09-24
Yes, try the link there, or run the commands (if you do not want to look at the link):

> **Shafiul Azam]1) ```
sudo apt-get install libusb-dev build-essential libsane-dev
sudo apt-get install git-core
git clone git://git.debian.org/sane/sane-backends.git
cd sane-backends
cd sane-backends
export BACKENDS="net mustek mustek_usb genesys"
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
```
2) ```
sudo nano /lib/udev/rules.d/40-libsane.rules
```

Add the following line:

[QUOTE]# Canon CanoScan Lide 100
 ATTRS{idVendor}==&#8221 said:**
> 

3) Then run:

```
sudo scanimage -L
```

If your scanner is there, skip to step 5. If not, go to step 4.

4) ```
sudo cp ~/sane-backends/backend/genesys.conf.in /etc/sane.d/genesys.conf
```

Go to step 3 again.

5) ```
sudo chmod 0777 /dev/bus/usb/[COLOR="#FF8C00"]xxx[/COLOR]/[COLOR="#0000FF"]yyy[/COLOR]
```

Replace xxx and yyy with the output you got in step 3.

6) You are done!!!

7) There is no step 7

i) Square-root of -1

P.S. (Off-topic) Where did you get the transparency theme (border)?

---

### Post by Senior_Buckethead on 2013-09-26
[/CODE]
...

kpathsea: Running mktexmf ptmr7t
! I can't find file `ptmr7t'.
<*> ...:=ljfour; mag:=1; nonstopmode; input ptmr7t
                                                  
Please type another input file name
! Emergency stop.
<*> ...:=ljfour; mag:=1; nonstopmode; input ptmr7t
                                                  
Transcript written on mfput.log.
grep: ptmr7t.log: No such file or directory
mktextfm: `mf-nowin -progname=mf \mode:=ljfour; mag:=1; nonstopmode; input ptmr7t' failed to make ptmr7t.tfm.
kpathsea: Appending font creation commands to missfont.log.
make[1]: *** [sane.dvi] Error 1
make[1]: Leaving directory `/home/glenn/sane-backends/doc'
make: *** [all-recursive] Error 1
glenn@design:~/sane-backends$ 

[/CODE]

Can anyone enlighten me as to the error message during make?

I tried re-running make as sudo make, appears to produce the same error code.

(off-topic) I don't remember where exactly I got the transparency theme, I think I was noodling around in gconf or something similar, trying to make my machine look more windowsey. I'm afraid if I do any more, my machine will implode and become a black hole.

---

### Post by scbingham on 2013-09-26
Your scanner comes with Cannon's scangearmp software.
I use it for scanning on my Cannon Pixma printer & I didn't have to go through anything as complicated as already mentioned above. Have you tried it?

---

### Post by Senior_Buckethead on 2013-09-28
[http://www.usa.canon.com/cusa/support/consumer/scanners/canoscan_series/canoscan_lide100#DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/scanners/canoscan_series/canoscan_lide100#DriversAndSoftware)

---

### Post by Senior_Buckethead on 2013-10-24
Can someone please enlighten me as to the "Error 1" I had when running make in the above post.
Is it a standard error, or just specific to what I was trying to build from source?

---

