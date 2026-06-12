---
title: "Battery charge always says 0%"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2008-05-24
Hi all,

Just did a fresh install of Hardy on my Sony Vaio VGN FS620 and got most everything working fine. Only problem is the battery monitor always says 0%. It detects AC power on and off but the battery status never changes. 

some info:
```
@:~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         0 mAh
last full capacity:      0 mAh
battery technology:      non-rechargeable
design voltage:          0 mV
design capacity warning: 1000 mAh
design capacity low:     400 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  100 mAh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
@:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      0 mAh
present voltage:         unknown
```

Anyone have any ideas?

THANKS!

---

### Post by nowhere@cox.net on 2008-05-26
Bump. Trying to get somewhere with this. I finally got my wife to give Ubuntu a try but she can't tell how much time or charge she has on the battery. It won't say how long before it dies, and it won't tell her when it's fully charged.

Not the best way to convert a Windows user. Need some help here. I can't find anything specific on the bug lists I know about nor any mention of this particular issue here on this forum. 

I did find the fix to make her function keys work so she was happy about that but I'm afraid no battery status is a killer for the Ubuntu deal...

Thanks!

BTW it works fine in WinXP so it's not a bad battery...

---

### Post by nowhere@cox.net on 2008-06-05
No one has any ideas?

---

### Post by dasunst3r on 2008-06-05
Have you tried unplugging your laptop to see what happens?  It may be the case that the battery's lease on life is over and that you'll need a new one.

---

### Post by nowhere@cox.net on 2008-06-05
I have unplugged and plugged back in the battery. The monitor detects the change in AC status but still says zero battery. The battery is brand new by the way...

---

### Post by django0909 on 2008-06-05
Try following the instructions here:

[https://help.ubuntu.com/community/ACPIBattery]("https://help.ubuntu.com/community/ACPIBattery")

If you have any problems post back :)

---

### Post by Ptero-4 on 2008-06-05
Load M$ Linux on that lappy, just to see if it's some sort of M$ made trap chip in the battery. If it is just let the lappy with that Linux distro (not the best, but at least gets the monitor working. If it still won't work then I don't know what else to try.

---

### Post by nowhere@cox.net on 2008-06-05
Ptero,
You mean this distro here? [http://www.mslinux.org/](http://www.mslinux.org/) ;)

Thanks django. I will explore those options. I would like to avoid recompiling the kernel for obvious reasons but there are some workarounds on the same page...

---

### Post by wpshooter on 2008-06-05
Nowhere:

I would not trust the info relating to power/UPS/battery, etc. given off by Ubuntu any further than I could throw this building I am sitting in.

Mind you, I like Ubuntu **BUT** they have a long way to go when it comes to this area of this O/S.

Primarily, what needs to happen is for one or more of the major UPS manufacturers to be convinced to write a decent UPS shutdown software with a GUI that will properly monitor, control and gracefully shutdown a computer that is operating under a Ubuntu/Linux operating system (for instance, just like the APC powerchute program provided for windows based systems).  

But as long as the Ubuntu and Linux community does not begin to petition the UPS manufacturers to do this by calling them and telling them that they are NOT going to buy their UPS products until they write this software, this is never going to happen.  If anyone is brave enough to call one of these UPS manufacturers, you might mention to them that if they are the first ones to come to market with such a software product, then their UPS hardware is what you are going to be buying.

Thanks.

---

### Post by django0909 on 2008-06-06
> Thanks django. I will explore those options. I would like to avoid recompiling the kernel for obvious reasons but there are some workarounds on the same page...


Best of luck, I hope you get somewhere. If you can't, it might be worth just dealing with it. Hope it doesn't put you off the Ubuntu way ;)

---

### Post by Joeb454 on 2008-06-06
You may notice in the output of the command in your first post, it says ```
battery technology:      non-rechargeable
``` Now I'm not sure about anybody else, but I can see a non-rechargeable battery being a little problematic ;)

---

### Post by Ptero-4 on 2008-06-06
> **nowhere@cox.net said:**
> Ptero,
You mean this distro here? [http://www.mslinux.org/](http://www.mslinux.org/) ;)


Actually, I meant this [http://www.opensuse.org/](http://www.opensuse.org/).

---

### Post by nowhere@cox.net on 2008-06-07
> **Joeb454 said:**
> You may notice in the output of the command in your first post, it says ```
battery technology:      non-rechargeable
``` Now I'm not sure about anybody else, but I can see a non-rechargeable battery being a little problematic ;)

Yes I noticed that. It's definitely not a non-rechargable. Windows reports it "correctly" or at least gives an indication of life left.

I haven't had a chance to try to fix anything yet. My wife swapped her harddrive back out back to Windows for now. Haven't been able to get her to spend some time on Ubuntu yet...

Thanks, I'll report back.

---

### Post by Charbs on 2009-01-08
Has anyone had success with any of the info in the thread. I too have a 0% battery all the time. It dissapears once fully charged, but once the power cable is unplugged it obviously comes back with the 0% Discharging message. I can still use the laptop for about 2 hours tho. 

And there is no warning that the battery is getting low and about to shut the laptop off. It will just abruptly shutdown.

---

### Post by nowhere@cox.net on 2009-01-09
Hey Charbs,

I haven't messed with it too much. I may boot up the Intrepid LiveCD from my USB drive and see what it does. We are having quite a bit of trouble with the laptop and the battery now these months later. The windows Sony battery drivers are reporting an incompatible battery or some bunk all of the sudden and will put up a pop up with only an OK to hibernate button. You have to find the process in the task manager and kill it or it eventually forces the hibernation. I can't stop just the battery process from loading at boot without breaking all the sony hardware drivers (function keys etc). 

The battery is an off brand since Sony seems to think their battery is worth $225. They also wanted to charge me $25 for the media of the info on the recovery partition. They offered to send it to me only on DVD but the laptop has a CD-RW drive.

Is your laptop a Sony?

---

### Post by Charbs on 2009-01-09
No its not a Sony its a Compaq Presario V2000. Its about 4 years old with the original battery (which still works fine)

---

