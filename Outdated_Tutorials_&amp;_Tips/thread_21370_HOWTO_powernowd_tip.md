---
title: "HOWTO: powernowd tip"
date: 2005-03-21
forum: Outdated Tutorials &amp; Tips
---

### Post by fizgig on 2005-03-21
I run Hoary on a laptop and it, per default, loads the powernowd daemon at startup.  This was kind of annoying because I don't care about CPU frequency when my laptop is plugged in - especially when the cool screensavers were running.  As such, I wanted mt laptop to not run powernowd when it's plugged in.

To accomplish this, I had to do two things:
1.  Modify the /etc/init.d/powernow init script to check the ac power is disconnected before starting the daemon
2.  Modify the /etc/acpi/power.sh script to start and stop the daemon appropriately.

Enjoy!

---

### Post by bgrant75 on 2005-03-23
Hi, thanks for the tip. It works allright.

Seems from a lot of other forums people have the same problem and this tip certianly helps.

It would be good if a laptop section could be created and maintained with tips, howto's etc.

Anyway thanks - Brian

---

### Post by PinGzor on 2005-03-26
Thanks alot!

---

### Post by Anubis on 2005-04-09
How about :
apt-get remove powernowd

---

### Post by DJ_Max on 2005-04-09
[QUOTE=Anubis]How about :
apt-get remove powernowd[/QUOTE]
 Umm, that removes it. You can't use something if you uninstall it. :-?

---

### Post by Muchacho_Gasolino on 2005-04-09
kind of off-topic, but what exactly is the purpose of powernowd?
I know it runs AMD Cool & Quiet, but is that even a good idea to run on a desktop?

---

### Post by DJ_Max on 2005-04-09
[QUOTE=Muchacho_Gasolino]kind of off-topic, but what exactly is the purpose of powernowd?
I know it runs AMD Cool & Quiet, but is that even a good idea to run on a desktop?[/QUOTE]
[http://freshmeat.net/projects/powernowd/](http://freshmeat.net/projects/powernowd/)

---

### Post by darkaudit on 2005-05-01
That answers the 'What is it?' part, but what about the rest? Is it necessary, or wise, to run powernowd on a desktop?

Granted, it does save a bit of wear on my overclocked 2500+ :)

---

### Post by EcliptuX on 2005-05-19
Nice tip !!!

But maybe it's possible to improve it ?
I had notice this : 
- when I'm booting with AC, the CPU working at 100%. OK no problem.
- when I'm unplugging the AC during the laptop is power on, the CPU slow down to work at 50%. OK, perfectly :)
- if I re-plugged AC without rebooting the laptop, the CPU is still working at 50%. Is it possible to make it work at 100% again automaticaly, without rebooting ?

---

### Post by boobytrapped on 2005-05-30
Interesting approach.  I solved this problem using a different technique. Instead of powernowd, I installed "cpufreqd".  Its a daemon similar to powernowd, but their default policy is something I like much better.  Its more customizable than powernowd, and keeps my laptop at 100% cpufreq when I am plugged into AC power.

HOWTO:

```
sudo apt-get install cpufreqd
```

---

### Post by Kebabji on 2005-10-05
ive got a speedstep on my 800/1.2ghz dell c610 laptop and when i install cpufreq it cant seem to recognize my cpu speedstep capabilities - powernowd, however, just keeps the processor at 66%

---

### Post by floyd27 on 2005-10-06
Is it possible to use thsi powernowd on a desktop cpu?

---

### Post by _bacon_ on 2005-10-07
[QUOTE=floyd27]Is it possible to use thsi powernowd on a desktop cpu?[/QUOTE]

Depends if your cpu supports frequency scaling, such as [AMD Mobile]("http://en.wikipedia.org/wiki/Power_Now%21") or [Pentium M]("http://en.wikipedia.org/wiki/SpeedStep") do. (Theses chips are found mostly in laptops)

---

### Post by earthfall on 2005-10-07
Current AMD64 CPU supports the Cool and Quiet (CnQ) technology, which enables CPU frequency stepping. As most recent motherboard can adjust their fan speed according to the system temperature, CnQ greatly help the temperature and the noise level of your system.

---

### Post by RoyCowboy on 2005-10-16
Does anyone know what I have to do to make the frequency selectable in the cpu frequency monitor applet? I remember I enabled this some time ago.. I think I had to chmod or chown some file in /proc..

Any one know?

Thanks

---

### Post by 23meg on 2005-11-14
[QUOTE=RoyCowboy]Does anyone know what I have to do to make the frequency selectable in the cpu frequency monitor applet? I remember I enabled this some time ago.. I think I had to chmod or chown some file in /proc..
[/QUOTE]

```
sudo chmod +s /usr/bin/cpufreq-selector
```

---

### Post by funkenstein on 2005-11-17
what can I say.. YAY for cpufreqd! defaults are lovely, and /etc/cpufreqd.conf is exceedingly easy to use!!
:D

thanks for pointing it out!
:KS :KS

---

### Post by Bruce M. on 2008-02-22
> **Anubis said:**
> How about :
apt-get remove powernowd

I'll keep this in mind when I see the answer.

> **Muchacho_Gasolino said:**
> kind of off-topic, but what exactly is the purpose of powernowd?
I know it runs AMD Cool & Quiet, but is that even a good idea to run on a desktop?

> **DJ_Max said:**
> [http://freshmeat.net/projects/powernowd/](http://freshmeat.net/projects/powernowd/)

The link talks about laptops ... hmmmmm

> **darkaudit said:**
> That answers the 'What is it?' part, but what about the rest? Is it necessary, or wise, to run powernowd on a desktop?

> **floyd27 said:**
> Is it possible to use thsi powernowd on a desktop cpu?

> **_bacon_ said:**
> Depends if your cpu supports frequency scaling, such as [AMD Mobile]("http://en.wikipedia.org/wiki/Power_Now%21") or [Pentium M]("http://en.wikipedia.org/wiki/SpeedStep") do. (Theses chips are found mostly in laptops)

Since I'm running an OLD Desktop Intel P-III, I would assume that I really don't need this app and can get rid of it.  (see Sig)

Am I correct is assuming I do not need this?

---

### Post by zirtik on 2008-08-21
> **23meg said:**
> ```
sudo chmod +s /usr/bin/cpufreq-selector
```

Great tip, Thanks!

---

### Post by silvagroup on 2008-11-07
It's been awhile since there have been any posts but I have been having intermittent freezes, that last for sevral seconds to a minute, and according to this post it could be related to powenowd, interestingly however when I am using Firefox my intermittent freezing goes away. Go figure.

Anyway for my question, has anyone tried the new powernowd version 1.0? and does it work any better?

From what I can see the Hardy version is .97.

Thanks in advance.

---

### Post by Stigmata13 on 2010-05-21
Sorry for the necro, but I find powernowd completely worthless on my laptop, as with its 1.6 ghz cpu, flash video becomes laggy and unbearable in fullscreen.

---

### Post by @lpha on 2010-10-08
I've had system freezes too on Ubuntu 10.4 supposedly due to powernowd as seen on this forum. 
[http://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy]("http://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy")

I get the exact same symptoms since I have the same specs. The thing is that the 'powernowd and powernowd$ row' weren't on the table when running: *sudo sysv-rc-conf*
What else can I do to disable it?

---

### Post by @lpha on 2010-10-10
Solved the issue. Info is in my thread. Link below.

[http://ubuntuforums.org/showthread.php?t=1589135](http://ubuntuforums.org/showthread.php?t=1589135)

---

