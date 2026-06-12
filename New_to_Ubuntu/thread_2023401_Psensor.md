---
title: "Psensor"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-07-12
Having got Psensor installed and running on my Ubuntu (12.04) machine, I find that it is monitoring six items :
[LIST]
[*]Physical id 0
[*]Core 0
[*]Core 1
[*]Core 2
[*]Core 3
[*]cpu usage
[/LIST]

I have four questions arising, if anyone can help

1)  Is the top item, 'Physical id 0' to do with some part of the motherboard?

2)  According to [**[COLOR="Red"]this page[/COLOR]**](http://wpitchoune.net/blog/psensor/), it can monitor the rotation speed of the fans, but I have no such reading. What can I do, if anything, to get a reading for fan speed?

3)  Which fan would the above apply to? The CPU fan? The case fan? (I have one connected so far.)

4)  I have a SSD installed - no HDD. Is the notion of monitoring the temperature of a SSD inappropriate?

---

### Post by jmfal on 2012-07-12
Run sensors in a terminal and match up the info

Is the cpu fan plugged into the cpu fan  on mobo

Did you answer yes to all questions when you did sensor- detect??

You  can run sensor-detect again if you didn't

---

### Post by Penfold1971 on 2012-07-12
> **jmfal said:**
> Run sensors in a terminal and match up the info

Is the cpu fan plugged into the cpu fan  on mobo

Did you answer yes to all questions when you did sensor- detect??

You  can run sensor-detect again if you didn't

You've been such a great help today, jmfal. Thank you.

Can I take your responses one at a time? I'll start with the fan question.

I have the CPU fan plugged into the CPU fan header (labelled) on the mobo. The one case fan I have working at present is plugged into a fan header on the mobo labelled SYS FAN. I noticed that this fan header has four pins while the 'plug' on the fan's lead was a female connector with three holes only. Would this make a difference?

---

### Post by jmfal on 2012-07-12
The cpu fan should show rpms unless you replaced it with a regular fan, which won't have a rpm sensor built in. The only other thing I can think of is that lm sensors is not detecting the fan.

The system fan has 4 wires, the fourth being a rpm sensor

---

### Post by Penfold1971 on 2012-07-12
I'll run sensor-detect again. And I'll double-check the fan connections in the case. I do remember the fan header for the CPU fan was labelled as such and was blue in colour, and was close to the CPU slot. The white fan header labelled SYS FAN was over to the side.

I'll have to check this all out tomorrow. Nothing's ever straight forward when I'm involved ;)

---

### Post by NikTh on 2012-07-12
Hi , 
i am not sure if hddtemp can read an ssd  but you can check it out. 
```
sudo apt-get install hddtemp
``` during install will ask you if hddtemp runs as daemon .. answer yes. Navigate with Tab and select with Enter. 
After finish , reboot you system. 
Thanks

---

### Post by Penfold1971 on 2012-07-13
> **jmfal said:**
> Run sensors in a terminal and match up the info
Is the cpu fan plugged into the cpu fan  on mobo
Did you answer yes to all questions when you did sensor- detect??
You  can run sensor-detect again if you didn't

1)  I ran sensors in Terminal, and got :
```
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0: +75ºC
Core 0: +69ºC
Core 1: +73ºC
Core 2: +75ºC
Core 3: +73ºC
```
Each temperature was followed by:
```
(high= +80ºC, crit= +98ºC)
```

My temps were all OK then. (Connecting the remaining two case fans only reduced the temperatures by a couple of degrees now and then.)

2)  The CPU fan was correctly plugged into the header marked CPU-FAN right next to the CPU slot.

3)  I did answer 'yes' to all the questions when I did sensor-detect

4)  I ran sensor-detect again anyway, just to be sure.

I suppose 'fan speed' isn't overly critical - the temperatures are of more immediate importance. I'm just wondering why it doesn't appear. :confused:

---

### Post by Penfold1971 on 2012-07-13
> **NikTh said:**
> Hi , 
i am not sure if hddtemp can read an ssd  but you can check it out. 
```
sudo apt-get install hddtemp
``` during install will ask you if hddtemp runs as daemon .. answer yes. Navigate with Tab and select with Enter. 
After finish , reboot you system. 
Thanks
Thanks, NikTh.
Got the reply :
```
hddtemp is already the newest version
hddtemp set to manually installed
```

Don't know what the last line means?

---

### Post by QIII on 2012-07-13
Despite what is shown there as the critical temps, I'd be concerned about those core temps.  For an AMD CPU, 60 is death.  70 for Intel.

AMD APUs run hotter, maxing at around 100.  If this is an AMD APU, you are not critical, but still on the high side for idle.

---

### Post by Penfold1971 on 2012-07-13
Hmmm. This *is* a problem.

The CPU is an Intel Core i7 2600k.

I'll have to get advice about reducing the percentage of CPU used by Folding@home over on the FAH forums.

Thanks.

EDIT: I just noticed your comment about 'high side for idle'. These temps are for FAH running full tilt continuously. The % CPU used is listed by Psensor as 100%.

---

### Post by jmfal on 2012-07-13
The fan speed isn't real important, it's nice to know that it's speeding up when temp. rises.

If you close the psensors window there should be a thermometer icon in the top right menu bar, you can click on that and it will show readings without the window.

---

### Post by Penfold1971 on 2012-07-13
Yes, I found the menulet (is that what it's called?) at top right in the menu bar.

This machine appears to be running hot, even with the three case fans going. I'll have to think alternatives here.

As I said in my reply to Q111, one tack will be to try and reduce the % CPU taken by FAH. I suppose another would be to replace the CPU fan with a more aggressively cooling after market job.

---

### Post by jmfal on 2012-07-13
You can try a new cpu heatsink/fan.

I replaced mine with a cooler master  520  I think and dropped temps about 10-12 C

About $35 US  thermal grease included

---

### Post by QIII on 2012-07-13
OK.  I see the temps are under load.

Are you using the stock fan?  At sustained high loads the stock HSFs for both Intel and AMD are woefully inadequate.

If you are going to be doing Folding, I'd recommend a good after-market HSF.  Not a $30 job, sorry jmfal.
:)

For sustained high CPU loads, I'd go with a top notch one.  That's cheaper than a new i7.  Call it insurance.

I usually go with Noctuas on the machines I flog like that.

I run one machine 24x7 doing Rosetta on BOINC and I have an NH-C14 on that one because the D14 won't quite clear the case.

I use the ATI GPU client on a Windows machine for Folding, so CPU temps aren't an issue.  But 4 5870s running full blast make so much noise I only do that at night!

---

### Post by Penfold1971 on 2012-07-13
> **QIII said:**
> Are those temps under load?

Are you using the stock fan?  At sustained high loads the stock HSFs for both Intel and AMD are woefully inadequate.

If you are going to be doing Folding, I'd recommend a good after-market HSF.  Not a $30 job, mind you.

Interesting and useful tip there, Q111 - thanks.

Yes - those temps are under load (100% CPU) and yes - it's the stock fan that came with the CPU, plus the three case fans. And I *will* be doing Folding - round the clock. It's specifically why I built this machine - pure Folding. I had been Folding on our Intel iMac, but the temps went through the roof, so I thought I'd spare it from a fiery death. :grin:

As of now, I'm now on the trail of a good after-market HSF. Any suggestions? I wouldn't trust myself to choose.

I've been folding on this machine since 25th of June, so with any luck I won't have done too much damage - is that an over-optimistic pov?

---

### Post by jmfal on 2012-07-13
No problem, merely a suggestion without knowing what pc is being used for..

---

### Post by NikTh on 2012-07-13
> **Penfold1971 said:**
> Thanks, NikTh.
Got the reply :
```
hddtemp is already the newest version
hddtemp set to manually installed
```Don't know what the last line means?
Hi,
Yes but where is the hdd (or ssd in your case) temp ? Maybe hddtemp is unable to measure that temp ? (ssd i mean)
Give this command and see the output..
```
sudo hddtemp /dev/sda
```Thanks

---

### Post by QIII on 2012-07-13
> **Penfold1971 said:**
> I've been folding on this machine since 25th of June, so with any luck I won't have done too much damage - is that an over-optimistic pov?

I'd take a break from Folding until you get the HSF.

As for damage, it's hard to say...

By the way, if you do

```
sudo dpkg-reconfigure hddtemp
```

and just hit enter all the way through you won't have to use sudo on hddtemp and you can use a monitor like gkrellm or conky to monitor the temp -- if it is useful with an SSD.

---

### Post by Penfold1971 on 2012-07-13
> **NikTh said:**
> Give this command and see the output..
```
sudo hddtemp /dev/sda
```Thanks

This is the output :

```
WARNING: Drive /dev/sda doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me .....
WARNING: See --help, --debug and --drivebase options.
/dev/sda: INTEL SSDSC2CT060A3: no sensor
```

Info seems hard to find very quickly - I have seen that its max operating temp is 70ºC though.

---

### Post by NikTh on 2012-07-13
> **Penfold1971 said:**
> This is the output :

```
WARNING: Drive /dev/sda doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me .....
WARNING: See --help, --debug and --drivebase options.
/dev/sda: INTEL SSDSC2CT060A3: no sensor
```Info seems hard to find very quickly - I have seen that its max operating temp is 70ºC though.
Hi,
Try 
```
sudo hddtemp -D /dev/sda
``` I suppose /dev/sda is you SSD , right ?
Thanks

---

### Post by Penfold1971 on 2012-07-14
> **NikTh said:**
> Hi,
Try 
```
sudo hddtemp -D /dev/sda
``` I suppose /dev/sda is you SSD , right ?
Thanks

I tried that code with these results :
```
====hddtemp 0.3-beta15====

Model: INTEL SSDSC2CT060A3

field(5)             = 0
field(9)             = 3
field(12)            = 17
field(181)           = 0
field(182)           = 0
field(192)           = 16
field(225)           = 131
field(232)           = 0
field(233)           = 0
field(241)           = 131
field(242)           = 149
field(249)           = 45

If one of these value seems to match the temperature, be sure to read
the hddtemp man page before sending a report (section REPORT). Thanks
```
None of the values matched any temperature.

I don't know what " /dev/sda "  means, I'm following the advice of others all the way through here :)

---

### Post by Penfold1971 on 2012-07-14
This morning I took the side of the case off (lhs, so I'm looking at the top/front of the motherboard), and after a short while saw a decent drop in temps over what they had been just prior to taking the side off :

Physical id 0: 66C    Core 0: 62C    Core 1: 65C    Core 2: 67C    Core 3: 65C   -   these values can vary ± a degree or two.

Not a solution, but interesting to see. Having said that, today is a coolish day here, so ambient is 17C in the Umac's room.

---

### Post by NikTh on 2012-07-14
Hi , 
Ok , about your Hard Drive . 
**/dev/sda** is your Intel SSD 
> **Penfold1971 said:**
> 
```
/dev/sda: INTEL **SSD**SC2CT060A3: no sensor
```

Its possible those drives have not a temperature sensor inside them , or hddtemp not support this drive. 
I read that those electronic drives have no problem with temp as a mechanic HDD . 
They use much less power (about 1W) when are idle , and no worries about temp. 
I will not dig more about this (SSD temp i mean) , if you want you can send a report to hddtemp developer about your drive and don't forget to include your drive's specs.
Thanks

---

### Post by Penfold1971 on 2012-07-14
Thanks NikTh.

---

