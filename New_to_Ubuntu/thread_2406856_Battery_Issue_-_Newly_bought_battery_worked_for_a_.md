---
title: "Battery Issue - Newly bought battery worked for a week only"
date: 2018-11-26
forum: New to Ubuntu
---

### Post by sherafghan on 2018-11-26
Hi
I purchased a new battery. It was working fine for a week. but after that it suddenly goes to zero percentage and charging but it never gets charged. On unplugging the AC adapter it turned of the laptop. Following are the outputs of few commands:
sher@sher-7G-Series:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  model:                MWL32b
  power supply:         yes
  updated:              Di 27 Nov 2018 01:20:37 CET (70 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         848,602 Wh
    energy-full-design:  268,65 Wh
    energy-rate:         0 W
    voltage:             12,382 V
    percentage:          0%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-caution-charging-symbolic'


sher@sher-7G-Series:~$ upower -i $(upower -e | grep BAT) | grep --color=never -E "state|to\ full|to\ empty|percentage"
    state:               charging
    percentage:          0%


sher@sher-7G-Series:~$ acpi -V
Battery 0: Charging, 0%, charging at zero rate - will never fully charge.
Battery 0: design capacity 18152 mAh, last full capacity 2007 mAh = 11%
Adapter 0: on-line
Thermal 0: ok, 41.0 degrees C
Thermal 0: trip point 0 switches to mode hot at temperature 105.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 104.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10
Cooling 2: x86_pkg_temp no state information available
Cooling 3: Processor 0 of 10
Cooling 4: intel_powerclamp no state information available
Cooling 5: Processor 0 of 10
sher@sher-7G-Series:~$

---

### Post by mastablasta on 2018-11-29
claim it with the seller. i hope it wasn't ordered from China as it is difficult to claim it there.

---

### Post by Autodave on 2018-11-29
I have had several aftermarket batteries that either didn't work right out of the box or died shortly after starting use.  I know that the price for an OE one is outta sight, but you pay your money and you take your chance.

Realize that a lot of these cheaper aftermarket batteries are actually remanufactured ones: the cells have been replaced, but the control board is out of a failed battery.  If the control board was the cause of the previously failed unit, it is now the cause of failure of what you just purchased.

---

### Post by angisky on 2018-12-02
Yeah I got a replacement battery for an HP laptop a while back and the battery no longer works. It'll cut power out after about 15 minutes of use. You can boot back up and use it another 15 minutes and it'll shut off again. The temptation is there for me to risk it again for my Thinkpad x131e. It still holds most of it's charge but I was considering buying on because Power Statistics shows it isn't getting the full designed charge anymore.

Your battery shows an oddly high designed full charge. I think that battery might just be a complete dud.

---

### Post by angisky on 2018-12-02
I'm coming back and making another reply because I found more information for my case that might help you too. I suggest you get the make and model of your OEM battery or look up compatible batteries. In my case I noticed that there are 2 models that are compatible with my machine and Lenovo actually sells replacement OEM parts for my thinkpad. Since they are OEM and brand new they are more likely to actually work. Also the 2 models in my case were completely different prices even they had the same capacity. I'm going to buy the cheaper one which is still more expensive than the cheapest batteries I found on Amazon and Ebay but since it's OEM it's less of a risk.

---

