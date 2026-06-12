---
title: "suddenly &quot;No modem was found on your system&quot; Ubuntu 10.10 Robotics USB"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by DaveReed on 2011-10-23
For months I'd been using my Robotics USB modem with Ubuntu 10.10 via sudo wvdial, and connecting just fine.  Then suddenly, without making any config changes, I'm getting 
--> WvDial: Internet dialer version 1.60.
--> Initializing modem.
--> Sending: ATZ
--> Sending ATQ0
OK
--> Re-Sending: ATZ
--> Modem not reponding.

...even though the modem's PWR light is on and its DATA light comes on when the above is sent.

Using Gnome PPP to detect the device, which has always resided at /dev/ttyACM0, it now  responds, "No modem was found on your system."

Again, I had been connecting fine using sudo wvdial for months and did not change anything.

Any suggestions would be appreciated.

Thanks,
Dave

---

### Post by LinuxFan999 on 2011-10-23
Why are you using dail-up internet in 2011?

---

### Post by DaveReed on 2011-10-23
> **LinuxFan999 said:**
> Why are you using dail-up internet in 2011?

Because I have a free broadband air card connection provided by the company where I work in e-commerce, and the dialup is just a fallback for emergencies and costs me only $5.50/month.

Thanks,
Dave

---

### Post by lkraemer on 2011-10-29
Dave,
Unplug the USB Modem and power up, open a Terminal Window (Console) and
type:

```

lsusb

```
Then plug in the USB Modem and wait one minute.  Then repeat the above
command.  I'd suggest plugging the USB Modem in the same USB Port each time.
```

lsusb
dmesg | tail

```

You should see that the USB Modem has been detected.

You will need to set up the pap-secrets and/or chap-secrets file by running the following in the Terminal Window:
```

sudo pppconfig

```

You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```

The pap-secrets at /etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
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

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"GeraldJones" provider "MyPassWord"

```


If you named provider something different, then just substitute that
for the provider in pon and poff. Let's assume showmenet

Original ISP named provider
To connect use the first command.  To Disconnect use the second command.
```

pon provider
poff provider

```

Modified ISP named showmenet
```

pon showmenet
poff showmenet

```
This should get you connected. You then need to open your Browser,
and make sure OFFLINE is not checked. It is in the Top Left selection
under FILE:

You should be able to browse, and surf.  Now disconnect and setup wvdial.


When pppconfig is setup, try running wvdialconf to detect the Modem.
```

sudo wvdialconf /etc/wvdial.conf

```

You should get a configuration file like this at
/etc/wvdial.conf (you may need to add/change a few things...)

wvdial.conf contains:
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
; /dev/??? may be different
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```

Now go back and try wvdial. It should now work.
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

Now that it works set up Gnome-PPP.  From now on, you can just click on
Gnome-PPP and run it from the GUI.

[http://ubuntuforums.org/showthread.php?t=1720726&highlight=pppconfig](http://ubuntuforums.org/showthread.php?t=1720726&highlight=pppconfig)
[http://ubuntuforums.org/showthread.php?t=1614599&highlight=pppconfig](http://ubuntuforums.org/showthread.php?t=1614599&highlight=pppconfig)

Post if you have troubles.

LK

---

