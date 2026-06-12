---
title: "Using dial up with 12.04"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by Polydorus on 2012-11-02
I've installed wvdial on Ubuntu 12.04 (64 bit) and was able to connect to the internet for two weeks.  During the time I could connect, it did not appear that wvdial was completely reading the conf file.  When it would dial the Terminal would show ATDT544-555 even thought my Dial Command = ATDP.   For some reason that worked for awhile now, after a long delay, I'm losing the signal.

Error Message:
CONNECT 37333/ARQ/V92/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
NO CARRIER
--> Connected, but carrier signal lost!  Retrying...

wvdial.conf:
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = 544-5555
Password = PASSWORD
Username = Polydorus

[Dialer phone2]
Phone = 785-5555

[Dialer pulse]
Dial Command = ATDP

The ISP works OK with Windows.  Is there something wrong with my conf file?

TIA

---

### Post by Polydorus on 2012-11-04
Can anyone help?

TIA

---

### Post by Linux_junkie on 2012-11-04
Would the info in the following link help you?

[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)

---

### Post by Polydorus on 2012-11-04
Thanks for the link.  My problem is more, why did it work for two weeks then stop?   On October 30, I was no longer able to connect.  I hadn't changed anything and the ISP still works with Windows.  I was guessing the modem was dialing tone rather than pulse but the error messages don't match up with that.

---

### Post by lkraemer on 2012-11-05
Polydorus,
You need to add yourself to DIP group, or verify that you are a member of that group.
```

groups

```

Refer to posting #2 at [http://ubuntuforums.org/showthread.php?t=1943624](http://ubuntuforums.org/showthread.php?t=1943624)


Then, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window (Console):
```

sudo pppconfig

```

You will need your **userlogin, password, ISP provider information**, and **pap or chap** information for
the connection. (You can set up pap and then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if you need to from the menu selections.

The pap-secrets at /etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04, later versions may have changed the format)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```
ASSUME:
your loging name is GeraldJones
your password is MyPassWord

Your last section of the pap-secrets file should be:
```

# OUTBOUND connections

# Here you should add your userid & password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"GeraldJones" provider "MyPassWord"

```


Do you have read access to /dev/ttyACM? Depending on the config of your box, it may only be accessible by root.
```

id
ls -l /dev/ttyACM0

```

**WHAT YOUR USB DEVICE IS DETECTED AS....**

**DETECT THE DEVICE - USB:**
Open a Linux Terminal window and copy/paste the following commands with the USB to Serial Adapter unplugged
from a USB port.
```

dmesg | tail
lsusb

```

My Results were:
> 
larry@ubuntu:~$ dmesg | tail
[10797.964432] domain 0: span 03
[10797.964434] groups: 01 02
[10797.964436] domain 1: span 03
[10797.964438] groups: 03
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3

larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Then plug in the USB Device to one of your USB ports. (REMEMBER to ALWAYS use this same port when using your USB Device) Wait for about 15 seconds, then cut and paste the following command in your Linux Terminal Window:
```

dmesg | tail
lsusb

```
My results were:
> 
larry@ubuntu:~$ dmesg | tail
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3
[12091.200574] usb 6-1: new full speed USB device using uhci_hcd and address 4
[12091.358706] usb 6-1: configuration #1 chosen from 1 choice
[12091.363887] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[12091.363914] cdc_acm 6-1:1.0: ttyACM0: USB ACM device

My device is /dev/ttyACM0

> 
larry@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Now, copy/paste your information with the following command in your Linux Terminal Window:
```

lsusb -v -d 058f:9720

```

My results were:
> 
Bus 006 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 2 Communications
bDeviceSubClass 0
bDeviceProtocol 0
bMaxPacketSize0 8
idVendor 0x058f Alcor Micro Corp.
idProduct 0x9720 USB-Serial Adapter
bcdDevice 0.00 


To locate the possible COMM PORTS in Ubuntu, copy and paste the following commands with the USB Modem plugged in.:
```

ls -l /dev/ttyS*
ls -l /dev/ttyU*
ls -l /dev/ttyA*

```

Notice that ttyS0 through ttyS3 are detected as shown. You may have /dev/ttyUSB0 or /dev/ttyACM0 if it was properly detected.

```

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3

```


In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
Your USB Modem should be properly detected.  If /dev/ttyACM0 isn't properly detected you can use a 
Symbolic link to link it to /dev/ttyS?

You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains something like this, but yours will be slightly different:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.


Larry

---

### Post by Polydorus on 2012-11-05
> **lkraemer said:**
> You should hear the modem go OFFHOOK with dialtone,

Wow, a lot of material there, thank you very much Larry.   I have a U.S.Robotics 56K USB modem which does not have a speaker.  Wish it did, then I would be able to tell if it is dialing using tone or pulse.

The modem is recognized and somehow is connecting.  I was able to connect for two weeks now the handshake is taking way to long and I think the connection is timing out.  The lack of a speaker doesn't help with that either. :-)

---

### Post by lkraemer on 2012-11-05
Polydorus,
You may to chose to pick up the Handset of your Phone as the dial is
in progress, so you can listen to the dialing.  Just be aware that you
might not get a good connection, but you can always hang up the handset
and redial with the modem.  After all, you just want to hear the tones or
pulses as they are being dialed.  Who cares what number is dialed or
if anyone answers.  You're after the Tones or Pulses, nothing else.

If it dials, Connects and then disconnects, your configuration is incorrect
in wvdial, or your Authentication is incorrect.
 
You might want to add:
```

Stupid mode = yes

```

Are you trying pap or chap?


Larry

---

### Post by Polydorus on 2012-11-06
> **lkraemer said:**
> You need to add yourself to DIP group, or verify that you are a member of that group.

I'm listed as member of group dip.

---

### Post by Polydorus on 2012-11-06
> **lkraemer said:**
> You may to chose to pick up the Handset of your Phone as the dial is in progress, so you can listen to the dialing.  Just be aware that you
might not get a good connection, but you can always hang up the handset
and redial with the modem.  After all, you just want to hear the tones or
pulses as they are being dialed.  Who cares what number is dialed or
if anyone answers.  You're after the Tones or Pulses, nothing else.

Thanks, I will give that a try.

> **lkraemer said:**
> If it dials, Connects and then disconnects, your configuration is incorrect
in wvdial, or your Authentication is incorrect.

There are no error messages it just appears to time out and the line is dropped.
 
> **lkraemer said:**
> You might want to add:
[code]
Stupid mode = yes

I will, what does it do?

> **lkraemer said:**
> Are you trying pap or chap?.

I haven't tried it yet but it appears more for multiple users/ISPs.  This is a single user set up with one ISP.

I ran wvdialconf and was able to get online with the result.  What does pap or chap add to that?

Once again thank you for your reply.

---

### Post by Polydorus on 2012-11-09
Yesterday I began having sign on problems with Windows.  I had thought this was more along the line of a hardware problems with the modem/phone.  I was looking around for another modem to try with Ubuntu.  I changed my tack this morning and tried the same setup that had failed with a different ISP and it worked!  I didn't really answer why, but I'm back online with both Ubuntu and Windows.  My thanks to lkraemer and Linux_junkie for their assistance.

---

