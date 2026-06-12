---
title: "How much control can cron have"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-12-07
I am a truck driver and am gone for sometimes months at a time, and was wondering if cron can be configured to power up my comp, update and upgrade and power down. Tried to google this and couldn't come up with anything I could use. Thanks for help,

---

### Post by SteveDee on 2011-12-08
> **jerrynewt said:**
> ...and was wondering if cron can be configured to power up my comp...

No, I don't think you'll be able to do that because the central processor is not powered when the computer is off.

The computer can be configured to "wake on lan" which is where another computer sends a wakeup call to the network interface which then boot up the sleeping computer. But this is probably no help to you.

So it depends how keen you are to do this. You could connect your computer to the supply via a 7 day timer, so that on a certain day power is switched on for (say) 1 hour. The computer BIOS would need to be configured to start when power is applied (not all BIOS support this). And then you would have to run the software update via a script and get the computer to power-down when done (or just rely on the power timer to turn off).

---

### Post by lukeiamyourfather on 2011-12-08
Since the machine won't be running neither will cron. The machine would have to be powered on by some other means. Some motherboards have a BIOS option to power on the machine at certain times/days. A outlet timer is another option like mentioned, usually can get them for things like Christmas lights.

If you feel like getting more involved with the process you could create a device to power on the machine using whatever schedule or trigger you like. For example use an Arduino board with a real time clock shield and/or Ethernet shield (by time and date or by network) to trigger a relay on the same circuit as the power switch on the front of the case.

---

### Post by androssofer on 2011-12-08
> **jerrynewt said:**
> I am a truck driver and am gone for sometimes months at a time, and was wondering if cron can be configured to power up my comp, update and upgrade and power down. Tried to google this and couldn't come up with anything I could use. Thanks for help,

> **lukeiamyourfather said:**
> If you feel like getting more involved with the process you could create a device to power on the machine using whatever schedule or trigger you like. For example use an Arduino board with a real time clock shield and/or Ethernet shield (by time and date or by network) to trigger a relay on the same circuit as the power switch on the front of the case.

An easy and cheap way to make your own system (if you like playing about with stuff like this :-), but arent quite at the stage of programming your own arduino board ) would be to get a cheap router that can run [dd-wrt]("http://www.dd-wrt.com/site/index"). dd-wrt is a linux based router firmware. (the reason i'm suggesting a router is they draw less power than a computer would)

you leave the router running and set a cron job on it to wake-on-lan your computer. Then on the computer have a cron job to update and shutdown again.. 

I have something similar running at my house and it works a treat

---

### Post by lukeiamyourfather on 2011-12-08
> **androssofer said:**
> An easy and cheap way to make your own system (if you like playing about with stuff like this :-), but arent quite at the stage of programming your own arduino board ) would be to get a cheap router that can run [dd-wrt]("http://www.dd-wrt.com/site/index"). dd-wrt is a linux based router firmware. (the reason i'm suggesting a router is they draw less power than a computer would)

you leave the router running and set a cron job on it to wake-on-lan your computer. Then on the computer have a cron job to update and shutdown again.. 

I have something similar running at my house and it works a treat

Yeah, WOL is the best route if the hardware supports it. Just throwing ideas out there. :D

---

### Post by marinara on 2011-12-08
most macs can do this, and some windows pc's can
[http://www.google.com/url?sa=t&rct=j&q=mac%20power%20on%20alarm&source=web&cd=1&ved=0CCUQrAIoADAA&url=http%3A%2F%2Fforums.macrumors.com%2Fshowthread.php%3Ft%3D1257334&ei=AZ_gTus4p9rRAa3kpccH&usg=AFQjCNEfgeKgyaAtWx_FXFpFZkVQr7dOpg&sig2=-x3cuefWb49sB0vb-JQMOg&cad=rja](http://www.google.com/url?sa=t&rct=j&q=mac%20power%20on%20alarm&source=web&cd=1&ved=0CCUQrAIoADAA&url=http%3A%2F%2Fforums.macrumors.com%2Fshowthread.php%3Ft%3D1257334&ei=AZ_gTus4p9rRAa3kpccH&usg=AFQjCNEfgeKgyaAtWx_FXFpFZkVQr7dOpg&sig2=-x3cuefWb49sB0vb-JQMOg&cad=rja)

---

### Post by matt_symes on 2011-12-08
Hi

Take a look at ```
man rtcwake
```I could never get it working on my laptop but if works on your machine then that may provide the framework for a solution.

Kind regards

---

### Post by Zill on 2011-12-08
> **jerrynewt said:**
> I am a truck driver and am gone for sometimes months at a time, and was wondering if cron can be configured to power up my comp, update and upgrade and power down...
I have to ask why?  Personally, I would not be at all happy about letting my computer "update and upgrade" without my explicit approval!

As your computer is, presumably, powered down while you are away then there is no risk whatsoever from *any* new software vulnerability.  As long as you install security updates on your next power-up then this should be perfectly adequate IMHO.

---

### Post by SteveDee on 2011-12-08
> **lukeiamyourfather said:**
> ...some motherboards have a BIOS option to power on the machine at certain times/days...

Yes, wake-on-time is probably the best option if your BIOS supports it.

You can check by opening a terminal and typing:-
```

sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"

```
...this should set your system to wakeup 5 minutes from now. To see if this has been set, type in terminal:-
```

cat /proc/driver/rtc

```
...output should look something like this:-
```

rtc_time	: 17:41:39
rtc_date	: 2011-12-08
alrm_time	: 17:46:30
alrm_date	: 2011-12-08
alarm_IRQ	: yes
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: no
BCD		: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

```
...now shutdown your computer, leave the power connected, and make a coffee. By then it should have powered back up (if your system supports it).

---

### Post by lykwydchykyn on 2011-12-08
If you get the power-on issues worked out, look into the cron-apt package for doing the updating.  I use it on my Debian servers to keep up with security updates.

---

