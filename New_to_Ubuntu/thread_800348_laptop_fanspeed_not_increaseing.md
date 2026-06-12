---
title: "laptop fanspeed not increaseing"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-19
i have a problem with my fan speed
my cpu on my laptop dell xps 1210 heats up to 71C with out a noticeable increase in my fanspeed.

my reguler cpu temp is 43c

is there anyway to make the fan speed more aggressive so it speeds up eariler?

can i manually set the thresholds for fan speeds?


i found that many have a directory  /proc/acpi/fan/(some other directoty)
i dont have this directory.
i lmsensors shows no information about my fans.
in windows i can HEAR the fans run hard during a game
in ubuntu the same game has no increase in fan speed that i can hear

nutz

---

### Post by sdennie on 2008-05-19
Depending on the CPU, 71C isn't exceedingly hot (it's hot but probably not nearly dangerous hot) so it's possible that your fans just haven't decided to come on full blast at that point.  One thing that I've found useful is getting some compressed air and cleaning out all my laptop vents with it.  It's surprising how much dust can get into a laptop and cleaning it can make a huge difference in temperature.

---

### Post by nutpants on 2008-05-20
found some help for my xps1210


Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k


and i found this

On my laptop (not a dell) there are trip-points specified in

/proc/acpi/thermal_zone/TZ1

critical (S5): 93 C
passive: 91 C: tc1=1 tc2=2 tsp=100 devices=0xeffce7e0
active[0]: 78 C: devices=0xdffe14e0
active[1]: 72 C: devices=0xdffe1440
active[2]: 67 C: devices=0xdffe13c0
active[3]: 55 C: devices=0xdffe1340

Means: under 55C, there's no fan at all. My fan is off most of the time, unless on hot summer days or when the CPU is working *hard*.
All I know from vista is that it uses system ressources massively. Will your fan turn on if you make your computer work 100% for some time?
Here's my stupid perl-script to heat up my CPU a little. ;-) I wrote it because of some sort of a strange error: My fan never completely shut down unless I overstepped a trip-point..


#!/usr/bin/perl

while(){
open (TEMP, '/proc/acpi/thermal_zone/TZ1/temperature'); #given there is your temperature stored.

$a = <TEMP>;
close TEMP;
$a =~ s/\D//g;
exit if ($a > 67);
for $b (1..1000000){}
system (cat, '/proc/acpi/thermal_zone/TZ1/temperature', '/proc/acpi/thermal_zone/TZ1/state');
#..adjust if your temperature and thermal_zone messages are found somewhere else in /proc
}

(launch from terminal to see temperature & fan state)

cheers
:m)


but it is strange that the files in this directory have no information in them

nutz

---

