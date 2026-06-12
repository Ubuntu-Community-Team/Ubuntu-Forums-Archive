---
title: "Agrere modems and help installing tarballs"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by dstin1 on 2008-08-14
I recently found my self stuck with dial up.  The problem I am having is I have a agrere modem I should be able to make it work with martian or ltmodem but after downlowing the tarballs I can not make either work.  Some simple instructions would be appreceiated.  

I am writing this from winblows which I only gave 5g on my hard drive.

---

### Post by Bachstelze on 2008-08-14
I used to know how do install that, but haven't done it in ages :p Can you tell me where you downloaded those tarballs from ?

---

### Post by dstin1 on 2008-08-14
the exact sites I don't remember.  However I go martian from a link from linmodems.com I think.  Ltmodem I got from a google search it was the first one.

IMHO
Getting a modem to work should not be a difficult thing but microsoft has the power the make it so.  

sorry about the spelling errors I am stuck using IE not firefox.

---

### Post by Bachstelze on 2008-08-14
> **dstin1 said:**
> the exact sites I don't remember.  However I go martian from a link from linmodems.com I think.  Ltmodem I got from a google search it was the first one.

IMHO
Getting a modem to work should not be a difficult thing but microsoft has the power the make it so.  

sorry about the spelling errors I am stuck using IE not firefox.

I think you'd better post a message about your issue to the Linmodems mailing-list (be sure to include the ModemData.txt file produced by scanModem!).

---

### Post by S.A.A on 2008-08-14
Hey, I have agere modem too, and this's how i get it to work:
   
1- install **build-essential** package from the live CD.
2- install martian from [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz)
3- now compile martian with:
```
sudo make all
sudo make install
```
4- finally load martian driver:
```
sudo modprobe martian_dev 
sudo martian_modem
```
Note: this will install the driver for the current session, so you need to do this:
```
sudo gedit /etc/rc.local
```
Now, add these two lines above the "exit 0" line
```
/sbin/modprobe martian_dev
martian_modem
```

---

### Post by dstin1 on 2008-08-14
Thanks I will try again when I get off work.

What does build essential do that my be where I have been going wrong.

---

### Post by S.A.A on 2008-08-14
> **dstin1 said:**
> Thanks I will try again when I get off work.

What does build essential do that my be where I have been going wrong.

It's needed for compiling sources.

---

### Post by mishivia on 2008-10-15
Thank you. I will try this again. Ubuntu seriously needs to support winmodems. Hopefully Intrepid will do exactly this. 

:KS> **S.A.A said:**
> Hey, I have agere modem too, and this's how i get it to work:
   
1- install **build-essential** package from the live CD.
2- install martian from [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz)
3- now compile martian with:
```
sudo make all
sudo make install
```
4- finally load martian driver:
```
sudo modprobe martian_dev 
sudo martian_modem
```
Note: this will install the driver for the current session, so you need to do this:
```
sudo gedit /etc/rc.local
```
Now, add these two lines above the "exit 0" line
```
/sbin/modprobe martian_dev
martian_modem
```

---

### Post by dstin1 on 2008-10-15
This will only work with an Agrere modem and some of them are not supported by martian modem I had to finally install an older modem to get it to work.

I can help you do all this if you want, I got it all figured out in about 3 days.

---

### Post by mishivia on 2008-10-15
dstin here is some of the modemtxt.data thanx again
-----system information ------
CPU=i686,
Linux version 2.6.24-19-generic  (buildd@palmer)  (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7	))  #1 SMP Wed Jun 18 14:43:41 UTC 2008 scanModem update of: 2008_08_06

PCI slot= 00:09.0  PCI iD 11c1:0441  SubsystemID 1468:0041 Name Communication controller Agere Systems 56k WinModem

modem chipset detected on
controller: Agere Systems 56k WinModem"
class=0780
pcidev=11c1:0441
subsys=1468:0441
irq=3
ident=Agere.DSP
support type needed or chipset: Agere.DSP

---

### Post by michael.fries on 2008-11-09
In the directions, what does "install martian" entail?  I unzipped it, is there anything esle that needs to be done?  

Also, is there a specific director that you need to be in when you issue the commands in the step 3?

Thanks,
Mike

---

### Post by dstin1 on 2008-11-09
Try this

If you are sure that martian will work for you step by step instructions

Make sure you have the package build essential installed

delete all of the martians you have

download the latest version from here
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080625.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080625.tar.gz)

extract it to your desktop which will create a folder martian-full-20080625

open terminal
$ cd martian-full-20080625
$ make clean
$ make all
$ sudo make install

for setup:
$ sudo modprobe martain_dev

you can get a report
$ sudo dmesg | grep martian
should look something like this
[ 4742.716000] martian loaded - 20071011
[ 4742.716000] "martian_dev": detaching 11c1:445 from serial
[ 4742.732000] "martian_dev": added device 11c1:445 BaseAddress =
0x2040, CommAddres = 0xd4c660ac, irq = 11

test basic sanity with:
$ sudo martian_modem --info countries
find your country code

activate martian modem
$ sudo martian_modem --country=us
you can leave out the country code from now on

you should see something that looks like this.
martian: info: Your port is /dev/ttySM0

if you don't stop here

Leave martian modem running and open a new terminal tab

start creating a dialout config file:

$ sudo wvdialconf /etc/wvdial.conf

should see something like this
--------
ttySM0<*1>: ATQ0 V1 E1 -- OK
ttySM0<*1>: ATQ0 V1 E1 Z -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.30
ttySM0<*1>: Speed 4800: AT -- OK
ttySM0<*1>: Speed 9600: AT -- OK
ttySM0<*1>: Speed 19200: AT -- OK
ttySM0<*1>: Speed 38400: AT -- OK
ttySM0<*1>: Speed 57600: AT -- OK
ttySM0<*1>: Speed 115200: AT -- OK
ttySM0<*1>: Speed 230400: AT -- OK
ttySM0<*1>: Speed 460800: AT -- OK
ttySM0<*1>: Max speed is 460800; that should be safe.
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySM0.
--------

edit config file
$ sudo gedit /etc/wvdial.conf

this is what mine looks like take out the ; and insert personal info where my xxxx are

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = xxxxxxx
ISDN = 0
Username = [email]xxxxxxxx@isp.net[/email] don't forget @isp
; Dial Command = ATDP
Password = xxxxxxx password for isp
Modem = /dev/ttySM0
Carrier Check = No
Baud = 460800

next dial in

$ sudo wvdial

to hang up control C
to exit martian modem control C

---

