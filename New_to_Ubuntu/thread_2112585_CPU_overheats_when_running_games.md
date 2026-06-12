---
title: "CPU overheats when running games"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by stefan987 on 2013-02-05
Hello

Since installing Linux on my Toshiba C660 laptop my computer has overheated whenever I run any sort of game. This can result in my computer shutting down when the temperature reaches critical levels(~90 degrees Celsius based on data from lm-sensors). When idle, the system temperatures range from 48 to 60 degrees Celsius. Also the fans sound like they are running at a lower speed than they were with windows. 

In preparation for altering the fan speed I ran "*sensors-detect*" which only found information on "coretemp" so the command "*sensors*" generates the following output:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +53.0°C  (high = +80.0°C, crit = +90.0°C)
Core 2:       +54.0°C  (high = +80.0°C, crit = +90.0°C)

And "*pwmconfig*" yeilded this output:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

How should I proceed? Thank you in advance for any help with this issue.

---

### Post by Mark Phelps on 2013-02-05
Most folks want to slow fans down, not speed them up-- so, I don't know if the command linked below will help:

[http://linux.die.net/man/8/fancontrol]("http://linux.die.net/man/8/fancontrol")

---

### Post by Thee on 2013-02-05
Have you tried cleaning the cooler? It's probably dusty.

---

