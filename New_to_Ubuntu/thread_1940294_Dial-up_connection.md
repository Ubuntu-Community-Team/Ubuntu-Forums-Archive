---
title: "Dial-up connection"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by The Mop on 2012-03-13
Hi all,
   
  No luck trying to install wvdial, it says to install via the normal software channels.
  Thanks for any ideas.
   
  [[IMG]http://i132.photobucket.com/albums/q23/Clogzz/22/th_Dial_up.jpg[/IMG]]("http://s132.photobucket.com/albums/q23/Clogzz/22/Dial_up.jpg")

---

### Post by roger_1960 on 2012-03-13
Hi

Looking at the screen shot, you were not online when you tried to install it.  This may well be the problem.

---

### Post by raja.genupula on 2012-03-13
Yup! that's also one point . but what you got when you have typed


```
sudo apt-get install wvdial

```

in your terminal.

EDIT: Because that message ICON is Bold that makes me think . but try it in the terminal and let us know what you got .

---

### Post by The Mop on 2012-03-13
Thanks Roger, &#9786;
   
  The catch is that the modem would have to work to go online.
  I&#8217;m exploring [linmodems.org]("http://www.linmodems.org/") for inspiration.

---

### Post by The Mop on 2012-03-13
And thanks, Raja, &#9786;
   
  The problem is on another computer, that&#8217;s how I can be online.
  I&#8217;ll try your suggestion tomorrow and let you know what I&#8217;ve made of it.
  I&#8217;m in Australia, and it&#8217;s night here now.

---

### Post by lkraemer on 2012-03-14
The Mop,
NOTE: the dependencies Version may have changed Versions, depending on the Ubuntu version you have installed....ie it may be version 4.7 now!
ALSO, I'm assuming Ubuntu 10.04 for this information.  Change the 10.04 to the Ubuntu version you have installed.....

You need to download wvdial, and the following dependencies for whatever
version you have installed......and get the 32 or 64 bit debs to match
your installed version.......then install via Synaptics...............
realizing you don't have Ethernet or Wifi.....available yet on Ubuntu and
are trying your best to get wvdial installed and configured to get Dialup Working......

wvdial & dependencies: (ALL are .deb files)
```

libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

```
Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP or Ubuntu, then copy the *.deb files to USB Flash Drive, & then to Ubuntu subdirectory /var/cache/apt/archives & then install using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install wvdial from the CDR.


First, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window (Console):
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

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


Power up the modem, and connect it to your serial port.
In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
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

wvdial.conf info:
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

PPP HOWTO:
[http://tldp.org/HOWTO/PPP-HOWTO/index.html](http://tldp.org/HOWTO/PPP-HOWTO/index.html)

PAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1034.html](http://tldp.org/HOWTO/PPP-HOWTO/x1034.html)

CHAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1053.html](http://tldp.org/HOWTO/PPP-HOWTO/x1053.html)

Setting up PPP Manually
[http://tldp.org/HOWTO/PPP-HOWTO/manual.html](http://tldp.org/HOWTO/PPP-HOWTO/manual.html)


Finally, when wvdial is working you can configure/set up Gnome-PPP.


**WINMODEM:**
But, your Modem might be a WinModem, then you need to go to the
[http://www.linmodems.org/](http://www.linmodems.org/) site, then download
the ScanModem.tool and execute that script to get the information
on the modem. Then subscribe to the Linmodems discussion list.
Then send Marvin an email (in plain text..ONLY) to the discussion
list. He will analyze your results and get back to you on what to
do to get the correct drivers to get the Modem working.



lk

---

### Post by The Mop on 2012-03-14
Thanks a lot, lk, that’ll keep me off the streets for a good while. 

I have Win XP on dial-up, with Ubuntu 11.10 - 32 bit installed in its own separate partition. 
The CD of the 2007 vintage Agere PCI modem has Linux drivers.
I also have a second SDRAM-vintage computer on dial-up, where I’ve saved your post to read while I’m tackling Ubuntu.

I can’t find terminals as mentioned up the thread by Raja.
I’ll try SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES first, it looks like my best chance to get on my way.

Many thanks for your troubles, and I’ll let you know how I’m going.

---

### Post by ubudog on 2012-03-14
The terminal is located in Applications>Accessories>Terminal.

Then try lkraemer's post.  :)

---

### Post by The Mop on 2012-03-16
Thanks, Ubudog, 
   
  I still can’t get in the engine room, there isn’t much on the control panel.
  The screenshot may give you an idea of where I’m sinning. 
   
  [[IMG]http://i132.photobucket.com/albums/q23/Clogzz/22/th_Startup_applications.jpg[/IMG]](http://s132.photobucket.com/albums/q23/Clogzz/22/Startup_applications.jpg)

---

### Post by Bartender on 2012-03-16
Hey, mop -

My #1 suggestion.  Find some place where you can take your PC that has a fast connection.  A friend's house, college computer lab, whatever.

I mucked around with Ubuntu and dial-up for a few years before we finally went to satellite.  From personal experience, I can tell you that the following combination is a lonely and frustrating place to be:

1. Relatively new to Linux
2. Nothing but dial-up at home
3. A brand-new install of Ubuntu, which will only have the pppconfig dialer
4. A winmodem that will not "just work" out of the box

It sounds to me like you're hitting on all four cylinders.

Do you know for sure that your dial-up ISP works with Linux?  Most do, but some don't.  If you call your ISP, they'll almost certainly tell you they don't "support" Linux.  That doesn't mean it won't work.

Although it's old, and hasn't been revised for newer versions of Ubuntu, my old dial-up thread might help.  [This one]("http://ubuntuforums.org/showthread.php?t=1377619") has a link to the previous one.

lkraemer's directions might work, but wow that's a lot of gory detail for someone new to this.  I don't know if I could follow it.  The problem with a whole bunch of steps like that, one after the other, is that something will almost certainly fail to work exactly as described, but a newbie may not realize it when it happens.   You could continue for hours on a futile quest.  

BTW, pppconfig still ships with Ubuntu.  I've got 12.04 Beta installed on a lappy, and pppconfig came up when I opened a terminal and typed 

```
sudo pppconfig
```

That screenshot you posted with the description of wvdial?  Canonical is lying when they say that "your modem will be detected automatically".  They know full well that most modems WON'T be detected.  I want to make that clear in case you're hoping that installing wvdial will solve your problems.  It won't.

---

