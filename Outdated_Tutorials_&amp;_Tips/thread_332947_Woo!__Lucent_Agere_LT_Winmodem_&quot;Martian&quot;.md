---
title: "Woo!  Lucent Agere LT Winmodem &quot;Martian&quot; + GnomePPP Works!!!"
date: 2007-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by zerhacke on 2007-01-06
I just got my Lucent Agere LT Winmodem "Martian" to work.  As it's not plugged into a phone line, I didn't connect (I have DSL.  I was just playing with the modem to prepare for a day that my DSL might be out or some such nonsense.)

Here's the steps I took to make it work.

Download, unzip, chmox +x this file - [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

Once it's unzipped and you have set the executable bit, go into a terminal and type ./scanModem

This will search for your modem type (in my case a Martian) and output a couple files to ~/Modem

Be sure to read the file named 1stRead.txt.  It contains valuable information.  Once you've read that file, in my case you need to read the file called AgereDSP.txt.  The AgereDSP.txt file will point you to the website [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)  (assuming you're running a 2.6 kernel and not some really old version of Ubuntu.  uname -a in a terminal will tell you a good bit about what kernel you're running).

Go to that site and download the file [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz) for a regular x86 Ubuntu install.

Unzip the file you just downloaded, and go into that directory with a terminal.  The file will unzip a directory called martian, usually in your home folder.

If you have not yet, at this time use synaptic or apt-get to install the metapackage build-essential.  You'll need it.  It'll also be a good idea to get the package named gnome-ppp.

In that directory inside of your terminal, type make all and hit enter.

After a few seconds, type in sudo make install, hit enter, provide your password, hit enter again.

Now that it's all installed, you need to insert the kernel module.  In a terminal, type in the following:

sudo modprobe martian_dev

And hit enter.  This will load the kernel module.  I do not yet know how to install this module automatically at boot, so if someone would be so kind as to add to this tutorial, that would be appreciated.

Now that that's taken care of, you're almost done.

As root, edit /etc/wvdial.conf and add the following line to the bottom of the file, being sure to add a carriage return after the file.  This means press enter so there's a blank line at the bottom of the file.  Insert:

Carrier Check =  no

into the file, press enter, save, exit.

Every time you wish to use the modem, you must run a helper application (again, I'm not the most knowledgeable so another person could tell us how to automatically run the helper app at login).

To load this helper app, you open a terminal and type:

sudo martian_modem

and hit enter.  For some reason, this program MUST be ran as root as far as I can tell.  It never worked as a regular Joe for me, it always complained about permission being denied.  Leave this program running as long as you wish to continue using the modem!  This program will tell you what device the modem is.  If you do not supply a device name, it defaults to /dev/ttySM0 - that's a ZERO, not a capital o.

Now all you have to do is feed this device into your dialing program.  In my instance, I could not run gnome-ppp as a regular user.  It would tell me I didn't have the permissions to use /dev/ttySM0 as a regular Joe, so I circumvented this by opening ANOTHER terminal ( do not use the same terminal that martian_modem is using.  This program has to keep running.  Open a new terminal). and running:

sudo gnome-ppp

in the new terminal.  You should have two terminals open now.  Don't close either one until you're ready to sign off your dialup line.

Yes, this is a somewhat dirty way of doing things.  I don't particularly like having to have two root-enabled terminals up while I'm dialing in.  I don't know a more elegant way of doing this, so I'm hoping someone with more knowledge of what is going on can come in here and show a more elegant way of doing things.

At any rate, I have a winmodem working!

---

### Post by renatosilva on 2007-01-14
you can have at least one terminal:

#martian_modem **--daemon**

This will free the shell so that you can call wvdial in the same term ;)

---

### Post by PatheticMoFo on 2007-01-25
Very nice, this helped a lot. Also, I wanted to mention that you don't need to run gnome-ppp or kppp etc as root if you just create a symlink to /dev/modem like so:

sudo ln -s /dev/ttySM0 /dev/modem

At least I didn't have to.

---

### Post by Bomper on 2007-01-26
> **zerhacke said:**
> 
...   For some reason, this program MUST be ran as root as far as I can tell.  It never worked as a regular Joe for me, it always complained about permission being denied.....

  ....  In my instance, I could not run gnome-ppp as a regular user  .....

sudo gnome-ppp



Configuration for a dialup connection over a modem Lucent to run gnome-ppp as a regular user  (NON sudo):

```

  $ sudo adduser USERNAME dip          
  $ sudo adduser USERNAME dialout

  $ sudo martian_modem --daemon --user=root --group=dialout --mode=0660

  
```  

 NOTE: Where of course USERNAME has to be substituted (Example: Joe)


  Configuring [gnome-ppp]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02") in "stupid mode".

In mode grafic [gnome-ppp]("http://www.debianadmin.com/images/dailup/27.png") search "stupic mode".


```

  $ gnome-ppp 
```  

  THE END.

  [Dialup Modem Howto]("https://help.ubuntu.com/community/DialupModemHowto")
  [Setting up dial up connection in ubuntu]("http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html")

---

### Post by edgarde on 2007-02-27
Been trying to get this to work for weeks. Did everything in the initial post, and all the above works, until:

Dial in, handshake, then fails with remote system sending "invalid login" message.

login/password check out, no capslock issue, re-checked & re-entered repeatedly. Been reading the LinModems site for some time, but no cure. What next?

Login Script Debug Window
-----
ATZ
OK
ATM1L1
OK
ATDT2159652421
CONNECT 53333 V42bis
-----


PPP Log
-----
Feb 27 12:13:39 localhost pppd[5771]: pppd 2.4.4b1 started by edley, uid 1000
Feb 27 12:13:39 localhost pppd[5771]: using channel 4
Feb 27 12:13:39 localhost pppd[5771]: Using interface ppp0
Feb 27 12:13:39 localhost pppd[5771]: Connect: ppp0 <--> /dev/pts/2
Feb 27 12:13:39 localhost pppd[5771]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x58ebc40c> <pcomp> <accomp>]
Feb 27 12:13:41 localhost pppd[5771]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xab44a2b8> <pcomp> <accomp> <auth pap>]
Feb 27 12:13:41 localhost pppd[5771]: sent [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xab44a2b8> <pcomp> <accomp> <auth pap>]
Feb 27 12:13:42 localhost pppd[5771]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x58ebc40c> <pcomp> <accomp>]
Feb 27 12:13:42 localhost pppd[5771]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x58ebc40c> <pcomp> <accomp>]
Feb 27 12:13:42 localhost pppd[5771]: sent [LCP EchoReq id=0x0 magic=0x58ebc40c]
Feb 27 12:13:42 localhost pppd[5771]: sent [PAP AuthReq id=0x1 user="estokes" password=<hidden>]
Feb 27 12:13:43 localhost pppd[5771]: rcvd [LCP EchoRep id=0x0 magic=0xab44a2b8]
Feb 27 12:13:43 localhost pppd[5771]: rcvd [PAP AuthNak id=0x1 "Invalid Login"]
Feb 27 12:13:43 localhost pppd[5771]: Remote message: Invalid Login
Feb 27 12:13:43 localhost pppd[5771]: PAP authentication failed
Feb 27 12:13:43 localhost pppd[5771]: sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
Feb 27 12:13:46 localhost pppd[5771]: sent [LCP TermReq id=0x3 "Failed to authenticate ourselves to peer"]
Feb 27 12:13:49 localhost pppd[5771]: Connection terminated.
Feb 27 12:13:49 localhost pppd[5771]: Modem hangup
Feb 27 12:13:49 localhost pppd[5771]: Exit.
-----


wvdial.conf
-----
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 2159652421
Modem = /dev/ttySM0
Username = estokes
Password = XXXXXXXXXXXXXX
Carrier Check = no
Baud = 460800
Stupid Mode = yes
-----
(Password deleted here but explicit in wvdial.conf)

/dev/ttySM0 is linked to /dev/modem


kppp Config for "Critical Path Project"
-----
Dial
	Phone number: 2159652421
	Authentication: PAP
	Callback type: None
Configuration
	Dynamic PI address
	(unchecked) Auto-configure hostname from this IP
Gateway
	(checked) Default Gateway
DNS
	Domain name: CritPath.org
	Configuration: Manual
	DNS IP address: none
	DNS Address list: 204.170.82.3, 204.170.82.8
	(unchecked) Disable existing DNS servers during connection
Login Script
	(none configured)
Execute
	(none configured)
Accounting
	No Accounting
-----
Tried every authentication options -- Script-based, CHAP, Terminal-based, PAP/CHAP.


kppp Config for modem
-----
Device
	Modem name: modem zero
	Modem device: /dev/modem
	Flow control: Hardware [CRTSCTS]
	Line termination: CR/LF
	Connection speed: 115200
	(tried checked & unchecked) Use lock file
	Modem timeout: 60 sec
Modem
	(checked) Wait for dial tone before dialing
	Busy wait: 5 sec
	Modem volume: medium
Misc
	pppd version: 2.4.4
	pppd timeout: 30 sec
	(unchecked) Automatic redial on disconnect
	(unchecked) Automatic redial on NO CARRIER
	(checked) Minimize window on connect
-----
Also tried just CR and just LF for Line termination.

Es.

---

### Post by lenar4 on 2007-04-04
i have an problem after entering make all

I have build essential the logs is:

cc1: error: include/linux/autoconf.h: No such file or directory
In file included from include/linux/sched.h:4,
                 from include/linux/module.h:9,
                 from /home/kamil/martian/kmodule/martian.c:44:
include/linux/auxvec.h:4:24: error: asm/auxvec.h: No such file or directory
In file included from include/linux/module.h:9,
                 from /home/kamil/martian/kmodule/martian.c:44:
include/linux/sched.h:42:36: error: asm/param.h: No such file or directory


and much more errors..

my kernel 2.6.17-11, ubuntu 6.10

do I need linux kernel sources or headers to compile it ? do you have "/libs/modules/ 2.6.17-11/build" directory ? and what do you have in it ? I made symlink build to /usr/src/2*sources/ because while compiling there was errors and after download kernel sources and creating symlink to it this error dissapeard but others come :-(

---

### Post by equability on 2007-04-11
Ciao zerhacke.

> **zerhacke said:**
> IAnd hit enter.  This will load the kernel module.  I do not yet know how to install this module automatically at boot, so if someone would be so kind as to add to this tutorial, that would be appreciated.

[quote="AgereDSP.txt created by scanModem"]
 To automate martian_modem action upon martian_dev loading,
 the following SINGLE line can be added to one of the files /etc/modprobe* 
 or to a new file /etc/modprobe.d/martian 
 install martian_dev  modprobe --ignore-install martian_dev ; /usr/sbin/martian_modem

 However, there is a report that (at least in some Systems), boot up processes
 are slowed. This is associated with bootup testing of potentially needed modules.
 Thus you may choose not to use this automation.[/quote]

If you want to load the module at boot, only, try:

~$ echo martian_dev | sudo tee -a /etc/modules


Hope, that will help.

---

### Post by equability on 2007-04-12
Ciao lenar4.

> **lenar4 said:**
> my kernel 2.6.17-11, ubuntu 6.10

do I need linux kernel sources or headers to compile it ? do you have "/libs/modules/ 2.6.17-11/build" directory ? and what do you have in it ? I made symlink build to /usr/src/2*sources/ because while compiling there was errors and after download kernel sources and creating symlink to it this error dissapeard but others come :-(

Do you still having this problem?

---

### Post by Turin Turambar on 2007-05-01
All you have to do is to edit
 
```

sudo gedit /etc/rc.local 
```

and put

```

martian_driver --daemon --user=YOURUSER --group=dialout

```

Rename YOURUSER to... well, your user. ;)
Just make sure to put it above "exit 0".

Next time you boot the machine, martian_driver will start automatically and Gnome PPP will not have any issues.

---

### Post by sixgun on 2007-07-17
> **lenar4 said:**
> i have an problem after entering make all

I have build essential the logs is:

cc1: error: include/linux/autoconf.h: No such file or directory
In file included from include/linux/sched.h:4,
                 from include/linux/module.h:9,
                 from /home/kamil/martian/kmodule/martian.c:44:
include/linux/auxvec.h:4:24: error: asm/auxvec.h: No such file or directory
In file included from include/linux/module.h:9,
                 from /home/kamil/martian/kmodule/martian.c:44:
include/linux/sched.h:42:36: error: asm/param.h: No such file or directory


and much more errors..

my kernel 2.6.17-11, ubuntu 6.10

**do I need linux kernel sources or headers to compile it ?** do you have "/libs/modules/ 2.6.17-11/build" directory ? and what do you have in it ? I made symlink build to /usr/src/2*sources/ because while compiling there was errors and after download kernel sources and creating symlink to it this error dissapeard but others come :-(

ABSOLUTELY!! Update the kernel, headers, and restricted stuff. Being fairly a new to linux, I Chased my tail for days, referencing several sites, and had no luck. It come down to the only one thing, that none of these sites mentioned or had only vaguely mentioned, UPDATE...UPDATE...UPDATE. Once I did that, badda bing badda boom, it was working. Well, almost. That got me past my initial issues. I did however experience several other head aches. 
Using the above method, on the initial posting, I experienced difficulty with the **martian-full-20061203.tar.gz** files. So after pulling my hair out for weeks, I decided to try something kind of contradicting to my above statement. I downgraded to the **martian-full-20061005.tar.gz** files, and the setup went smoothly from there. My only remaining issues now, are just getting martian to start up automatically after reboots, and getting it to redial automatically. Hopefully this forum has solved the reboot issue for me.

Thanks for the help. Now if someone could just tell me how to make my conexants run 56k, with out paying anually for a license.

---

### Post by XxPoseidoNxX on 2008-03-22
Thanks this guide really helped

---

