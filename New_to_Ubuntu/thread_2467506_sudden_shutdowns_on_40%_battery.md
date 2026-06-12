---
title: "sudden shutdowns on 40% battery"
date: 2021-09-28
forum: New to Ubuntu
---

### Post by optmed on 2021-09-28
please make ref. to [https://ubuntuforums.org/showthread.php?t=2467191&p=14059519#post14059519](https://ubuntuforums.org/showthread.php?t=2467191&p=14059519#post14059519) for a full description of the problem. I now have Ubuntu 20.04 installed on my HP ZBook G2. I have just experienced a sudden shutdown on a 40% battery. 

here's my log: [https://paste.ubuntu.com/p/Yz63RZtB47/](https://paste.ubuntu.com/p/Yz63RZtB47/)

please let me know if you need further info. Thanx.

---

### Post by Autodave on 2021-09-29
I am running Xubuntu, but this should be very similar to what you are using.  Under Settings Manager -> Power Manager -> System.  I have a Critical Power setting where I can choose the power level and what I want the machine to do when that level is achieved.

---

### Post by optmed on 2021-09-29
thanks Autodave. While I can't see the option you're referring to in Ubuntu 20.04 (in "settings"), I did use in Mint and Kubuntu, and even specifically told the OS to never ever shut down (please see my original post [https://ubuntuforums.org/showthread.php?t=2467191&p=14059519#post14059519](https://ubuntuforums.org/showthread.php?t=2467191&p=14059519#post14059519) - end of second paragraph). It didn't help.

---

### Post by Autodave on 2021-09-29
Where did you get the battery from?  Did you get it right from HP or some second party supplier/rebuilder?

---

### Post by optmed on 2021-09-29
HP - though I have no idea what kind of battery they installed: it never occurred to me to check, particularly because this HP ZBook came with Windows 10 installed, and the problem i described never occurred until I replaced it with Linux (please see my original post). What do you have in mind?

---

### Post by Autodave on 2021-09-29
The "after market" batteries are junk.....most of the time.  I run about 25% good on those: the rest either don't work when received, die shortly afterwards, don't last even a fraction of the time they are supposed to run, etc.  I would assume since HP did it that they used an HP battery.  You could still have a bad battery, but not likely.

I see no other problems of that type on these forums relating to HP ZBooks, so I still think that the problem is on the laptop's end and not Linux.

---

### Post by cookiecruncher on 2021-09-29
Try this :

```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```

On my laptop I get:

```
 native-path:          BAT0  vendor:               SONY
  model:                42T4795
  serial:               5033
  power supply:         yes
  updated:              Wed 29 Sep 2021 20:48:28 SAST (92 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              50.61 Wh
    energy-empty:        0 Wh
    energy-full:         50.61 Wh
    energy-full-design:  50.54 Wh
    energy-rate:         20.084 W
    voltage:             12.143 V
    percentage:          100%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-full-charged-symbolic'



```

---

### Post by optmed on 2021-09-30
[I]~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               Hewlett-Packard
  model:                Primary
  serial:               00001 2020/03/14
  power supply:         yes
  updated:              Thu 30 Sep 2021 16:15:34 EET (12 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              42.772 Wh
    energy-empty:        0 Wh
    energy-full:         65.4604 Wh
    energy-full-design:  65.4604 Wh
    energy-rate:         25.0416 W
    voltage:             14.92 V
    time to empty:       1.7 hours
    percentage:          65%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (charge):
    1633011285    65.000    discharging
  History (rate):
    1633011334    25.042    discharging
    1633011331    27.054    discharging
    1633011310    24.834    discharging
    1633011285    36.586    discharging
    1633011261    24.923    discharging
    1633011233    32.619    discharging[/I]

thanks cookiecruncher for looking into this. Do you see any anomaly?

---

### Post by optmed on 2021-09-30
Autodave: 
[I]
I see no other problems of that type on these forums relating to HP  ZBooks, so I still think that the problem is on the laptop's end and not  Linux.

[/I]I can't argue against this, except that I'm still wondering why the problem wouldn't occur on Windows 10.

---

### Post by optmed on 2021-10-03
totally by chance, I thought about switching to Intel graphics (when on battery) from Nvidia graphics: 

[I]$ sudo prime-select intel

[/I]...and it seems (seems) to have solved the issue. I've tested it twice, so far, and both times there hasn't been any sudden shutdown without warning. 

In other words, by way of preliminary conclusion, it would appear that the issue is somehow caused by the use of Nvidia graphics on battery use. 

I'll test it further and report back.

---

### Post by optmed on 2021-10-03
sadly it was coincidental. Just had two sudden shutdowns (on Intel, see above) - the first one while installing software and on battery on 48%, the second one while performing light, routine operations, with battery on the usual 40%.

is there any way to check (in a log) if the shutdowns were due to temperature reaching its critical value?

---

