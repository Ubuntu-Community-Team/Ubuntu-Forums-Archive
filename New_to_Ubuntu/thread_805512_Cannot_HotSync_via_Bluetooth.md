---
title: "Cannot HotSync via Bluetooth"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by t.septekin on 2008-05-24
Hello folks,

Here are my particulars:
PC: [INDENT]hp pavilion zv6245, running ubuntu 7.04;[/INDENT]
PDA: [INDENT]palm TX[/INDENT]

PROBLEM: cannot HotSync via Bluetooth.

In Terminal, when I enter:

```
hcitool scan
```
 it shows the BDADDR and name of palm device.

```
hidd --connect BDADDR
```
 returns:
	Can't get device information: Success

```
sudo hcitool info BDADDR
```
 lists the BD Address, LMP Version, etc.

```
pilot-xfer -p net:any -l
```
	while it is listening I tap on the HotSync icon of palm TX, the activity light on the Bluetooth dongle flashes, then I get
	"HotSync Problem - Unable to initiate HotSync operation
	because the port is in use by another application."

I am using the dongle for the convenience of its indicator light (and the possibility of switching off the built-in WIFi and Bluetooth).

Here is the annoying part: back in February when I first tried the combination they worked; I could get a listing of tha palm's content and I could HotSync.
At that time I'd made a note of all the Communication settings of palm, they are no good any more.

This morning I lowered myself to boot into Windows XP and there Palm Desktop HotSynched with palm TX fine!

The only advice I could find in Palm Forums was "a soft reset usually clears this problem".
Well, not in this case. I have even hard reset the palm and set it up from virgin state, same problem.

Is there anyone out there who has solved a similar problem, or is there someone who can give me any suggestions, please?

Thanks in advance,

teoman

---

