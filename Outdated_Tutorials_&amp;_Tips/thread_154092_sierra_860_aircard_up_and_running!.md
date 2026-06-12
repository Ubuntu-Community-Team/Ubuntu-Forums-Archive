---
title: "sierra 860 aircard up and running!"
date: 2006-04-02
forum: Outdated Tutorials &amp; Tips
---

### Post by yekibud on 2006-04-02
I was so happy about getting this running that I had to post - hope this is the right catagory...

Basically, follow the instructions at [http://mycusthelp.com/sierrawireless/supportkbitem.asp?sSessionID=&Inc=2870&sFilA=FAQ%20Category&sFilB=Products&sFilC=&FA=19&FB=23&FC=-1](http://mycusthelp.com/sierrawireless/supportkbitem.asp?sSessionID=&Inc=2870&sFilA=FAQ%20Category&sFilB=Products&sFilC=&FA=19&FB=23&FC=-1)

to get up and running with the latest sierra card, just replacing the 775 files with the 860 files.  I also had to use PAP/CHAP authentication on kppp, not simply PAP as suggested in the instructions.

Hope this helps someone trying to use a sierra GPRS card...

---

### Post by yekibud on 2006-04-08
Oh, also - use a "noauth" argument for the modem in kppp.

Now my only problem is depressingly low connection speeds.  Can anyone help with this?  The card is giving me a throughput of ~45Kb/sec according to 2wire.com - the kppp monitor maxes at 20Kb/sec, with an average aroudn 7Kb/sec.  I assume this is all down speed.

Haven't troubleshot this on a natively installed Ubuntu 5.10 2.6.12 system yet - maybe important to know that this is all booted from an external bus powered drive...

Thanks!

---

### Post by mrnicksgirl on 2006-05-10
I have the same card, I'm running the latest update (as of a week ago)

I have this error in my messages log:

[date] localhost firmwar_helper[5638]: main: error loading '/lib/firmware/SW_7xx_SER.cis' for device '/class/firmware/0.0' with driver '(unknown)' 


any insight?

---

### Post by stucki on 2006-06-27
Here are some notes which might help you to get this card running.

I sent these notes to Sierra but unfortunately they didn't add this to their website yet...

=== cut ===
Thanks for providing at least some minimal support for Aircards on Linux. I
could successfully set it up but had a lot of problems til it worked.

Here is a list of hints which I would like you to add to the article:

- The Aircard will not work unless you disable the SIM lock (boot Windows for
this)
- In case the speed is very slow, you should try upgrading the firmware
version - I gained some speed after this.
- The manual is designed for the deprecated "pcmcia-cs" utilities, and there
were no hints on how to use it with the modern "pcmciautils" package which is
designed for the Linux kernel 2.6 series. Finally the solution is pretty
easy:

1. You don't need to edit /etc/pcmcia/config anymore.
2. You will need to install a hotplug system helper, e.g. "udev" or "hotplug".
3. Place the file SW_8xx_SER.cis in /lib/firmware/.
4. Copy, rename or symlink the file to "SW_7xx_SER.cis".

The reason for this change is that both card identify themselves as "0x0192,
0x0710", and this product ID is hardcoded in the Linux source code to load
the firmware file "SW_7xx_SER.cis". See drivers/serial/serial_cs.c in your
Linux source code.

Thanks for mentioning these hints on your website. 
=== cut ===

---

### Post by errolsiegel on 2006-07-18
You wrote:

"- The Aircard will not work unless you disable the SIM lock (boot Windows for this)"

Would you elaborate on this?  The only software that came with my card is the Cingular Communication Manager.  I looked through all the menus but did not find any settings for SIM lock.

Thanks,
Errol

---

### Post by stucki on 2006-07-24
Hi Errol,
> **errolsiegel said:**
> You wrote:

"- The Aircard will not work unless you disable the SIM lock (boot Windows for this)"

Would you elaborate on this?  The only software that came with my card is the Cingular Communication Manager.  I looked through all the menus but did not find any settings for SIM lock.

Thanks,
Errol
I'm using a different software "Watcher" which was shipped with my card. Maybe you will have to contact the Sierra support for more information?

- michael

---

### Post by Makyver on 2006-09-13
I can't get my card up and running .. the lights on it turn green and I have followed all the steps but can't find what /dev/"node" it is being mapped or not mapped as ... I am using Dapper with all the updates but still no go ... any one know how to find out what if any dev node it's being mapped as 

Thanks Guys/Girls for the help on this. Oh yeah and has anyone used GPRS Easy Connect it looks cool but with out the node it's being mapped as I can't use it either ... Dmesg doesn't show the tty or node for it either.

UPDATE
Ok so I found my first Problem and got the card to come up as ttyS2 and wvdail to initialize it but can't get GPRS Easy Connect to work with it.. So I'm going to try and use several other dialers ...

UPDATE II
Ok so I got it working with KPPP but can't use GPRS Easy Connect and the speed is so slow I might as well be using a couple of tin cans and a string and having a freind read the web to me ...

---

### Post by sidster262 on 2006-09-13
I've been trying to get my Sierra Aircard 775 working on Dapper 6.06.1 for a few days now. The help on Sierra's web page is getting me nowhere. This is the first bit of help that makes any sense.

Unfortunately, (this is the part where I have to apologise for being a noob :-k ) I can't make sense of why you keep referring to the file as "SW_8xx_SER.cis" or "SW_7xx_SER.cis". I can only find "SW_7xx_SER.dat" on sierra's web site but no metion of the .cis file. Are these different files or did you make the .cis yourself? I know the answer is obvious but i just can't seem to figure it out.

Any help would be greatly appreciated.

:p

---

### Post by stucki on 2006-09-13
> **stucki said:**
> Hi Errol,

I'm using a different software "Watcher" which was shipped with my card. Maybe you will have to contact the Sierra support for more information?

- michael

Update: You don't need to unlock your card. It seems like "catty" allows you to specify the PIN whenever the card is being plugged in: [http://catty.sourceforge.net/]("http://catty.sourceforge.net/")
For details, see [http://wiki.chaostreff.ch/index.php/Sierra_Wireless_AC850]("http://wiki.chaostreff.ch/index.php/Sierra_Wireless_AC850") (sorry, German only)

- michael

---

### Post by stucki on 2006-09-13
> **sidster262 said:**
> I've been trying to get my Sierra Aircard 775 working on Dapper 6.06.1 for a few days now. The help on Sierra's web page is getting me nowhere. This is the first bit of help that makes any sense.

Unfortunately, (this is the part where I have to apologise for being a noob :-k ) I can't make sense of why you keep referring to the file as "SW_8xx_SER.cis" or "SW_7xx_SER.cis". I can only find "SW_7xx_SER.dat" on sierra's web site but no metion of the .cis file. Are these different files or did you make the .cis yourself? I know the answer is obvious but i just can't seem to figure it out.

Any help would be greatly appreciated.

:p
I'm referring to SW_7xx_SER.cis because this filename is hardcoded in the Linux source code. For details, see linux-2.6.xx/drivers/serial/serial_cs.c and search for that string.
The problem is that both AirCard 750 and AirCard 850 are identifying themselves as the same product, therefore Linux requests the firmware file mentioned above.

Technically, this is exactly what you have downloaded as *.dat, you just need to rename it.

- michael

---

### Post by mrghiz on 2006-09-21
> **Makyver said:**
> I can't get my card up and running .. the lights on it turn green and I have followed all the steps but can't find what /dev/"node" it is being mapped or not mapped as ... I am using Dapper with all the updates but still no go ... any one know how to find out what if any dev node it's being mapped as 

Thanks Guys/Girls for the help on this. Oh yeah and has anyone used GPRS Easy Connect it looks cool but with out the node it's being mapped as I can't use it either ... Dmesg doesn't show the tty or node for it either.

UPDATE
Ok so I found my first Problem and got the card to come up as ttyS2 and wvdail to initialize it but can't get GPRS Easy Connect to work with it.. So I'm going to try and use several other dialers ...


I've got the same problem with a sierra 850 aircard, ie I cannot get any ttyS device to access it. Could you please explain  how you managed to map it to a node? 
Thanks
Ghiz

PS I'm running pcmciautils on a >=2.6.17 kernel and followed all hints concernig sierra .CIS files renaming. Card is detected correctly by pccard  info and shows up in /sys ...

---

### Post by magicfab on 2007-01-26
I am puttin gotgether all the information I could gather about this setup, including some I will be updating from this thread. To all interested in reviewing it / participating, please see:
[https://wiki.ubuntu.com/AirCard8X0](https://wiki.ubuntu.com/AirCard8X0)

---

### Post by uk_falang on 2007-02-01
hI

Please let me know if you have any sucess in getting it to work with Gnome.

I have been trying to use wvdialer but no sucess, although the wvdialer config can see the modem and identify it

Are there any dialers like kppd for gnome, as pppd does not work and neither does wvdialer.

Thanks

> **Makyver said:**
> I can't get my card up and running .. the lights on it turn green and I have followed all the steps but can't find what /dev/"node" it is being mapped or not mapped as ... I am using Dapper with all the updates but still no go ... any one know how to find out what if any dev node it's being mapped as 

Thanks Guys/Girls for the help on this. Oh yeah and has anyone used GPRS Easy Connect it looks cool but with out the node it's being mapped as I can't use it either ... Dmesg doesn't show the tty or node for it either.

UPDATE
Ok so I found my first Problem and got the card to come up as ttyS2 and wvdail to initialize it but can't get GPRS Easy Connect to work with it.. So I'm going to try and use several other dialers ...

UPDATE II
Ok so I got it working with KPPP but can't use GPRS Easy Connect and the speed is so slow I might as well be using a couple of tin cans and a string and having a freind read the web to me ...

---

### Post by linux_2007 on 2007-06-04
I have been trying the below for a week...and not much  progress 

I have been trying to configure Sierra Aircard 860 on ubuntu 7.04 laptop IBM T43 thinkpad ..
I follwed the instructions as given by this link
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=118](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=118)

I followed all the steps except for the serial_cs.c [which I couldnt find]
the Aircard flashes green which I believe it is ready
when I run the wvdialConf create the below message is thrown
I installed the gnome-ppp but and I get the message /dev/modem not found - Not sure how to go ahead ?
===============================
Editing `create'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1 S2 S3

Sorry, no modem was detected! Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by linux_2007 on 2007-06-04
though my syslog and dmesg displays
pcmcia: registering new device pcmcia0.0
0.0: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

But my the modem isnt detected through GPRS connect, Kppp and gnome-ppp....
Contacted Sierra too and they too had no idea as their support on linux is limited

---

### Post by serum on 2007-07-03
> **mrnicksgirl said:**
> I have the same card, I'm running the latest update (as of a week ago)

I have this error in my messages log:

[date] localhost firmwar_helper[5638]: main: error loading '/lib/firmware/SW_7xx_SER.cis' for device '/class/firmware/0.0' with driver '(unknown)' 


any insight?

#

Copy the firmware file and overwrite the older version 7xx into /lib/firmware:

sudo mv  SW_8xx_SER.dat /lib/firmware/SW_7xx_SER.cis

---

### Post by FrankIOM on 2007-11-20
I am using the Sierra 850 Aircard for 3G
I followed all the directions
pccardctl ident
Socket 0:
  product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"
  manfid: 0x0192, 0x0710
  function: 2 (serial)

And I had a green light flashing, So I thought all was going well. I followed the instructions on the WIKI created the files as instructed. but after using the "pon ac850" command all I got was "Permission denied  Connect script failed" I even tried adding sudo in front in case extra authority was needed. As a newbie I am not sure what else to do. I did run "wvdialconf create" on the off chance but I got the "no modem detected"  as normal !  I also tried this
 dmesg | grep tty
[   31.511399] audit(1195587690.965:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4842 profile="/usr/sbin/cupsd"
[   86.332417] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A

Any how I am hoping this feed back helps those with better knowledge than me to sort this out. Should any extra information be needed let me know

3G provider - Manx Telecom - Isle of Man
no user or password is in the windows

Frank

---

### Post by achim_59 on 2008-09-01
> **FrankIOM said:**
> I am using the Sierra 850 Aircard for 3G
I followed all the directions
pccardctl ident
Socket 0:
  product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"
  manfid: 0x0192, 0x0710
  function: 2 (serial)

And I had a green light flashing, So I thought all was going well. .....
Frank

Your problem lies in that message from *pccardctl* which says: "function: 2 (serial)". It should be "function: 6 (network)". It means your card is not being recognised as a network device. Sadly I've got the same problem, but no solution in sight yet. 

I started my own thread before stumbling across this one.
[http://ubuntuforums.org/showthread.php?p=5704390]("http://ubuntuforums.org/showthread.php?p=5704390")
I've kept track of the steps I've taken there. A periodical check of that thread might offer some insight into the problem.

Good Luck

Achim

A colleague has advised me that "function: 2 (serial)" is OK, since the aircard is mapped to a serial device. Sorry if this has sent anyone up a blind alley.

I keep coming back to this issue every few months (I am very, very busy with other things) but I hava few spare evenings at the moment. I am currently running karmic koala on an IBM T43... still no joy.

current problem; the 99-aircard.rules file seems to be ignored, so no /dev/umts device is mapped.

Achim

---

### Post by achim_59 on 2008-09-01
> **errolsiegel said:**
> You wrote:

"- The Aircard will not work unless you disable the SIM lock (boot Windows for this)"

Would you elaborate on this?  The only software that came with my card is the Cingular Communication Manager.  I looked through all the menus but did not find any settings for SIM lock.

Thanks,
Errol

I think this confuses SIM-Lock and PIN. The latter can indeed be turned off using Windoze, though it isn't essential. There are many ways to enter the PIN with Linux.

A SIM-Lock is a diferent matter. Some providers lock the device (i.e. the PCMCIA card) so that only the one provider's SIM card can be used in it. If your provider does this, you will need to obtain a code for unlocking the device. If your initial contract is not yet expired this may well cost (gasp) money. ;) 

From what I have read to date Cingular does **not** seem do this. So you're safe.

Achim

---

