---
title: "HowTo: Conky hddtemp"
date: 2006-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by tturrisi on 2006-10-22
**How To get conky to display hard drive temperature as a non-root user**

*[color=red]Newer versions of Conky have hddtemp as a built in variable and the below guide is no longer necessary. See this [this post]("http://ubuntuforums.org/showthread.php?p=6919030#post6919030") on page 3 of this thread.[/color]*

**Caveat:**
hddtemp requires root privledges to use.

**Workaround:**
use netcat as a non-root user to obtain the hard drive temperature.

**Prerequisites:**
1. conky installed & working  apt-get install conky
2. hddtemp installed  apt-get install hddtemp

*note: this guide is if have one hard drive though can be modified to use more than one hard drive.*

**config hddtemp to run as a daemon:**
# sudo gedit /etc/default/hddtemp
```
# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# Master system-wide hddtemp switch. The initscript will not run if it is not
# set to true. STOP THE SERVICE BEFORE DISABLING IT!

# [automatically edited by postinst, do not change line format or set it to
# anything but false or true ]
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
DISKS="/dev/hda"  [COLOR="Red"]# your hard drive here hda or hdb etc.[/COLOR]

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures.
SYSLOG="300"  [COLOR="Red"]# 300 = every 5 minutes[/COLOR]

# Other options to pass to hddtemp
OPTIONS=""
```

**edit your .conkyrc**
$ gedit .conkyrc

add this line in the TEXT section:
```
TEXT
Hard Drive Temp: ${execi 300 nc localhost 7634 | cut -c29-30 ;}C
```

What it does:
The conky command $execi executes netcat at an interval of 5 minutes at localhost on the port used by conky 7634 and the result is cut to only the number value, the 29th & the 30th characters of the netcat result above, the hd temp.

example netcat result:
|/dev/hda|FUJITSU MHT2060AT|44|C|

**determine YOUR cut values to use**
Why? Because the result will be the model name of your hard drive and not all drives are the same!
$nc localhost 7634
count the characters in YOUR result and use those values in your .conkyrc

---

### Post by Aberrix on 2006-10-24
nice how-to!

---

### Post by tturrisi on 2006-10-24
Thanks!
This is also a good workaround for those of us w/ laptops that cannot work with lm-sensors.  At least it gives one some idea of the temp inside.

---

### Post by Jellyffs on 2006-11-17
Hdd temp on Conky is one of the harder thing to put up for a beginner. Great "how to" thanks.

---

### Post by nmsmith on 2007-02-14
I get:

```
nick@cloanthus:~$ nc localhost 7634
localhost [127.0.0.1] 7634 (?) : Connection refused
```

any ideas?

---

### Post by nmsmith on 2007-02-17
D'oh! I had "/dev/da" in my hddtemp.conf rather than the more useful "/dev/sda"

Apologies.

---

### Post by ephman on 2007-04-26
hey,

ok i upgraded to fiesty and my hdd temp doesn't work.  when i run the command 
[B]
nc localhost 7634 
[/B]
i get the temp, even when i run 
[B]
hddtemp /dev/sda 
[/B]
again everything fine.  but for some reason in conky 1.4.5 it's a no go.  the code is still the same as well 
[B]
${execi 1 nc 127.0.0.1 7634 | cut -c30-31 ;}C[/B]
 
in the conkyrc file.  any ideas???

thanks,

ephman

---

### Post by testube_babies on 2007-04-26
> **ephman said:**
> hey,

ok i upgraded to fiesty and my hdd temp doesn't work.  when i run the command 
[B]
nc localhost 7634 
[/B]
i get the temp, even when i run 
[B]
hddtemp /dev/sda 
[/B]
again everything fine.  but for some reason in conky 1.4.5 it's a no go.  the code is still the same as well 
[B]
${execi 1 nc 127.0.0.1 7634 | cut -c30-31 ;}C[/B]
 
in the conkyrc file.  any ideas???

thanks,

ephman


Are you sure you're cutting the right characters?

In my upgrade to Feisty, I had to change  
${execi 300 nc localhost 7634 | **cut -c29-30** ;}
to
${execi 300 nc localhost 7634 |** cut -c54-55** ;}

---

### Post by ephman on 2007-04-26
> Are you sure you're cutting the right characters?

In my upgrade to Feisty, I had to change
${execi 300 nc localhost 7634 | cut -c29-30 ;}
to
${execi 300 nc localhost 7634 | cut -c54-55 ;}

thank you it worked... but why?

thanks,
ephman

---

### Post by testube_babies on 2007-04-26
> **ephman said:**
> thank you it worked... but why?

thanks,
ephman

There was a long standing bug with the 2.6.20 Feisty kernel that wouldn't allow SMART values to be read on SMART-enabled hard drives.  It was fixed shortly before release, but one of the side effects is really long hard drive names filled with blank spaces and/or strange characters.

---

### Post by Jellyffs on 2007-04-29
Hi,

I have two disks: hda and sda. And I just moved from Edgy to Feisty.

Here is the stuff:
```

root@superdupont:~# nc localhost 7634
|/dev/hda|Maxtor 6Y080L0|34|C||/dev/sda|Maxtor 6B300S0                          &#65533;|SLP|*|
```

Also:
```

root@superdupont:~# hddtemp /dev/sda 
/dev/sda: Maxtor 6B300S0                          &#65533; : le lecteur est en veille
``` 

"le lecteur est en veille" means: the disk is in sleep mode...

And for the name of the hard drive, it's seems to be what testube_babies said.

SMART function isn't activated in my BIOS. Does Feisty needs it?

Don't know what to do... Any other idea?

Thanks,

Alex.

---

### Post by testube_babies on 2007-04-29
> **Jellyffs said:**
> Hi,
I have two disks: hda and sda. And I just moved from Edgy to Feisty.
...
SMART function isn't activated in my BIOS. Does Feisty needs it?


Yes, you need to activate SMART in your BIOS in order to use this.  If your BIOS doesn't support SMART, then I think you're out of luck.

...Although I'm not sure why it would possibly say the disk is in sleep mode...

---

### Post by Jellyffs on 2007-04-30
Hi,

Okay, I've activated the S.M.A.R.T. function in my bios. But my disk is still at sleep :)

But actually, that confirmed what I thought. What I read about SMART capabilities, is that it was just a way to check disks presence on a system. It just "ping" your drives, so the system knows if a disk is dead.  (cannot find that article now :/ )

But, what I did, is just count as if I was "seeing" the temp. I took:

|/dev/sda|Maxtor 6B300S0

And I added 2 values. I ended up with 26-27. Guess what, it worked.

I'm glad I can keep SMART function turned off, as it is conflicting with overclocking, and just burned electricity for nothing. 

Do you guys really need SMART to be activated?

Thanks,

Alex.

---

### Post by Jellyffs on 2007-04-30
Oh I'm a idiot. Of course it works, it my hda temp, not my sda !!

doh!

Hum.. so it doesn't work. I'll keep searching.

---

### Post by Jellyffs on 2007-04-30
Ok sorted.

I installed the latest beta release of Hddtemp. It works perfectly.

If anyone hits this problem again:

[HTML]http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fh%2Fhddtemp%2Fhddtemp_0.3-beta15-36_i386.deb&md5sum=5c8b715b4e581ccfdb68224d972bd4b4&arch=i386&type=main[/HTML]

About the S.M.A.R.T. thing, it seems that some disks DO need it to be activated. If it needs it, Hddtemp "should" tell you by saying "SMART isn't available" or something like it.

Alex.

---

### Post by WiFi Ed on 2007-05-02
Ok, I guess I'm just thick, but I keep getting an odd response to the "nc localhost 7634" command:

edmoran@feisty:~$ nc localhost 7634
|#|???|ERR|*||300|???|ERR|*||=|???|ERR|*||every|???|ERR|*||5|???|ERR|*||minutes|???|ERR|*||/dev/sda|WDC WD1600JS-75NCB3|40|C|edmoran@feisty:~$

I see my hd and the temp reading (40C) but I don't understand the error messages (I think) that show up in the beginning of the string. It looks like the errors are related to this section of the hddtemp file:

# Logging period (in seconds) for the temperatures.
SYSLOG="300"  # 300 = every 5 minutes

I made the hddtemp file as directed in the tutorial (cut and paste) and the only change I made was from DISKS="/dev/hda" to DISKS="/dev/sda" because that's how the drive is described in fstab. 

When I run hddtemp from terminal I get the following:

edmoran@feisty:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD1600JS-75NCB3: 40°C

I won't get into counting characters for the .conkyrc entry at this point (don't quite have that right yet either).

Any ideas for poor, helpless wannabe Unbuntero?

Thanks in advance!

---

### Post by WiFi Ed on 2007-05-02
Nevermind, I figured it out. I adjusted the logging period and messed up the location of a close quote. D'oh!

It was still a bit funky after fixing that, but a full shutdown and re-boot cleared up the remaining anomalies.

---

### Post by derekguy on 2007-05-14
Big ups for this how to! I did a bit of playing around and got it working (more by luck than knowledge) just one question I am trying to be fancy and put the degrees symbol into Conky (i.e 34°C but it renders another symbol next to the ° one a little 'a' with an accent. Any idea as to why this is? Cheers for any ides,
Derek

This is my .conkyrc config file:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 1

# border width
border_width 5

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 1
gap_y 13

# stuff after 'TEXT' will be formatted on screen
# hdb3:  ${fs_free_perc /dev/hdb3}%   ${fs_bar 6 /media/hdb3} --What is hdb3?

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}HDD TEMP ${hr 2}$color
Mashita 80Gb HDD: ${execi 300 nc localhost 7634 | cut -c54-55 ;}°C

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%  ${fs_bar 6 /}$color 
sda1:  ${fs_free_perc /media/Nexstar}%  ${fs_bar 6 /media/Nexstar}$color

${color orange}NETWORK (${addr eth1}) ${hr 2}$color
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by Jellyffs on 2007-05-16
Hi,

You mean you get this symbols: à ?

Alex.

---

### Post by derekguy on 2007-05-17
I get a symbol more or less like this one Â, sorry I don't know the name for it.

Eg: [highlight]Mashita 80Gb HDD:Â°C[/highlight]

It is just a little thing but I am curious as to why it appears and if I can do something about it.

Thanks all,

---

### Post by Jellyffs on 2007-05-17
It might be totally useless but, maybe you can try to put:

```
use_xft yes
```

and/or/then

```
override_utf8_locale yes
```

But hum.. weird problem yeah.

Alex.

---

### Post by tturrisi on 2007-05-18
To get the "degrees symbol" displayed in Conky -
in conkyrc change this:
```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
```
to this:
```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
```

---

### Post by derekguy on 2007-05-18
Sweet, thanks for the advice I tried to enable XFT and it worked but the text became too large and went off the edge of the screen. Any suggestions as to how to reduce the size of text when XFT is enabled?

---

### Post by Jellyffs on 2007-05-19
In your ./conky there is:

```
font arial
```

You can choose any font that you like. What I do is open Ooo Writer, choose a font, and pass it to conky. But the thing is, you now use XFT engine so it has to be for example:

```
xftfont MgOpen Modata-08
```

Or:

```
xftfont arial-08
```

Have fun :)

---

### Post by John.Michael.Kane on 2007-05-19
Have any of you got this howto to work with two sata hard drives?

nc localhost 7634 outputs this
|/dev/sda|WDC WD800JD-60LSA0                       &#65533;|23|C||/dev/sdb|WDC WD2500YD-01NVB1                     &#65533;|33|C|

This code works for |/dev/sda|WDC WD800JD-60LSA0 
${color white}Hard Drive Temp:${color white}${execi 300 nc localhost 7634 | cut -c54-55 ;}C

There does not seem to be a working cut -c for |/dev/sdb|WDC WD2500YD

Is there a way to fix this?

---

### Post by Jellyffs on 2007-05-19
Hi,

Pretty much the same problem I had on page 2 of this subject. 

I couldn't give better advice than grabbing this:

[HTML]http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fh%2Fhddtemp%2Fhddtemp_0.3-beta15-36_i386.deb&md5sum=5c8b715b4e581ccfdb68224d972bd4b4&arch=i386&type=main[/HTML]

Perfectly compatible with Ubuntu (Feisty at least) by the way.

Alex.

EDIT: after installing the .deb, and reloading hddtemp, if you throw a "nc localhost 7634" you "should" get a nice:

```
|/dev/sda|Hitachi HDS721680PLA380|31|C||/dev/sdb|Maxtor 6B300S0|29|C|
```    (In my case)

---

### Post by derekguy on 2007-05-21
Awesome, cheers for helping my understanding to increase. I now have done some more fiddling and my Conky looks great. It is just something small but I know more now :) thanks to all who helped me out.

---

### Post by tturrisi on 2007-05-21
Have you seen my howto to get conky to display your wan ip address?
[http://ubuntuforums.org/showthread.php?t=413156&highlight=conky+wan+ip](http://ubuntuforums.org/showthread.php?t=413156&highlight=conky+wan+ip)

---

### Post by John.Michael.Kane on 2007-05-21
Has anyone used this guide with two sata drives, and is working correctly?

---

### Post by Jellyffs on 2007-05-22
> **SD-Plissken said:**
> Has anyone used this guide with two sata drives, and is working correctly?

Yes me, did you try what I suggested?

---

### Post by John.Michael.Kane on 2007-05-23
> **Jellyffs said:**
> Yes me, did you try what I suggested?

Retried your method, and this time around with some tweaking it seems to be working, and currently showing both drives temp under conky.

So the hddtemp package that currently ship with feisty must be broken.


Thanks for the tip Jellyffs

---

### Post by Jellyffs on 2007-05-23
Cool. Maybe the version shipped in Feisty is just too old... ?

---

### Post by Technoviking on 2007-05-23
Anyone know how to run to use execi in .conkyrc to run a program as root? I would like to use coretemp to monitor my duo core temperatures, but it has to be ran as root.

---

### Post by brodiepearce on 2007-06-01
> **Jellyffs said:**
> Cool. Maybe the version shipped in Feisty is just too old... ?

Would I be able to see your /etc/defaults/hddtemp file?  I'm not sure how I should format mine to monitor two drives...

---

### Post by Jellyffs on 2007-06-01
> **brodiepearce said:**
> Would I be able to see your /etc/defaults/hddtemp file?  I'm not sure how I should format mine to monitor two drives...

Hi, 

Sure I can:
```

# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# [automatically edited by postinst, do not change line format ]

# hddtemp network daemon switch. If set to true, hddtemp will listen
# for incoming connections.
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
#DISKS="/dev/hda"

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures. If set to a value
# different than 0, hddtemp will run as a daemon periodically logging
# the temperatures through syslog
RUN_SYSLOG="0"

# Other options to pass to hddtemp
OPTIONS=""
```

As you can see I didn't change anything. Hddtemp should get your temp straight away when you type:

```
nc localhost 7634
```

If it doesn't work, either your hddtemp version is too old (probably if you got brand new SATA drives), or your drives are not supported at all (small chance).

Alex.

---

### Post by brodiepearce on 2007-06-01
> **WiFi Ed said:**
> Ok, I guess I'm just thick, but I keep getting an odd response to the "nc localhost 7634" command:

edmoran@feisty:~$ nc localhost 7634
|#|???|ERR|*||300|???|ERR|*||=|???|ERR|*||every|???|ERR|*||5|???|ERR|*||minutes|???|ERR|*||/dev/sda|WDC WD1600JS-75NCB3|40|C|edmoran@feisty:~$


I get similar errors on mine:

> 
brodiepearce@ubuntu:~$ nc localhost 7634
|#|???|ERR|*||300|???|ERR|*||=|???|ERR|*||every|???|ERR|*||5|???|ERR|*||minutes|???|ERR|*||/dev/hdc|WDC WD800JB-00ETA0|34|C||/dev/sda|WDC WD800JD-75LSA0|31|C|brodiepearce@ubuntu:~$ 


I don't quite understand what you mean by incorrent close quotes, and I can't see any obvious errors in my /etc/default/hddtemp file:

```

# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# Master system-wide hddtemp switch. The initscript will not run if it is not
# set to true. STOP THE SERVICE BEFORE DISABLING IT!

# [automatically edited by postinst, do not change line format or set it to
# anything but false or true ]
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
DISKS_1="/dev/hdc"
DISKS_2="/dev/sda"  # your hard drive here hda or hdb etc.

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures.
SYSLOG="300"  

# Other options to pass to hddtemp
OPTIONS=""

```

Same as yours, works perfectly if I do a "sudo hddtemp <drive>" too.

Going to try just getting conky to do "sudo hddtemp <drive>" and see how that goes down haha.

Oh, Jellyffs: that was quick, I've matched my file to yours and I still get the same error as before.  You can see that it is in fact working, it just has a lot of errors spewing out of it.  :/

*edit*
OK so trying to get conky to query hddtemp directly doesn't work either, the odd thing is, it's not outputting anything at all, I'm getting "WD800JD: Â°C  WD800JB: Â°C"  in conky (the execi commands are situated between the drive names and the °Cs).

---

### Post by Jellyffs on 2007-06-01
```
|#|???|ERR|*||300|???|ERR|*||=|???|ERR|*||every|?? ?|ERR|*||5|???|ERR|*||minutes|???|ERR|*||/dev/hdc|WDC WD800JB-00ETA0|34|C||/dev/sda|WDC
```

Seeing this, there's no doubt in my point of view, grab this and you'll be sorted:

[http://ftp.de.debian.org/debian/pool/main/h/hddtemp/hddtemp_0.3-beta15-36_i386.deb](http://ftp.de.debian.org/debian/pool/main/h/hddtemp/hddtemp_0.3-beta15-36_i386.deb)

Another thing that could be the cause, as discussed a few weeks ago with another member, is the famous S.M.A.R.T. function in BIOS that has to be activated for some HDD in order to communicate temps properly.

---

### Post by brodiepearce on 2007-06-01
> **Jellyffs said:**
> ```
|#|???|ERR|*||300|???|ERR|*||=|???|ERR|*||every|?? ?|ERR|*||5|???|ERR|*||minutes|???|ERR|*||/dev/hdc|WDC WD800JB-00ETA0|34|C||/dev/sda|WDC
```

Seeing this, there's no doubt in my point of view, grab this and you'll be sorted:

[http://ftp.de.debian.org/debian/pool/main/h/hddtemp/hddtemp_0.3-beta15-36_i386.deb](http://ftp.de.debian.org/debian/pool/main/h/hddtemp/hddtemp_0.3-beta15-36_i386.deb)

Another thing that could be the cause, as discussed a few weeks ago with another member, is the famous S.M.A.R.T. function in BIOS that has to be activated for some HDD in order to communicate temps properly.

Ah sorry should have mentioned, yes I'm running the latest beta that you linked previously.  I'll do a restart and check if S.M.A.R.T. is enabled.

*edit*  OK it has miraculously started working after the restart, (SMART was already enabled), though Wifi-ed experienced this too I believe.  ATM conky is set to extract the temperatures by running hddtemp for each drive, might change it to nc localhost later if it means less resources being eaten etc.  Now I just need to get rid of the Â before the degrees celcius.

---

### Post by tturrisi on 2007-06-01
> Now I just need to get rid of the Â before the degrees celcius.
see my post on page 1 of this thread

---

### Post by ukripper on 2007-06-13
Just installed hddtemp in feisty.

Added folowing lines to my conkyrc,
```
${hddtemp /dev/hda localhost 7634}
```

worked without making any changes as described in this Howto.
 no need to write exec script (exec takes more processing)

---

### Post by argoo on 2007-06-13
If you change the cmd as follows, you won't have to count characters...

${execi 300 nc localhost 7634 | cut -d"|" -f4 ;}

---

### Post by diskotek on 2007-06-14
hwen i type in the terminal
```
hddtemp /dev/sda
``` 
i got a permission crisis :(

i need to type
```
sudo hddtemp /dev/sda
```
and root password 

anybody knows, why?

---

### Post by forlau on 2007-08-06
I have 2 harddrives: hda and sda and hddtemp version 0.3-beta15.

For the SATA drive i never recieved the temperature.
 
sudo hddtemp /dev/hda
```
/dev/hda: IC35L120AVV207-1: 41°C

```

sudo hddtemp /dev/sda
```
/dev/sda: Hitachi HDT725032VLA360                 &#65533;: drive is sleeping

```

The solution was to wake-up the drive with the parameter -w
sudo hddtemp -w /dev/sda
```
/dev/sda: Hitachi HDT725032VLA360                 &#65533;: 39°C

```


Then modified the /etc/default/hddtemp file to
```

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
DISKS="/dev/hda /dev/sda"

# Other options to pass to hddtemp
OPTIONS="-w"

```

This worked for me and for Gkrellm which was always giving 0°C for sda.

---

### Post by garymc1 on 2007-08-12
When I use the command
nc localhost 7634
I get 
|/dev/hdc|ST3160021A|43|C|garymc@garymc-desktop:~$

what would the values be for the command

Hard Drive Temp: ${execi 300 nc localhost 7634 | cut -c29-30 ;}C

---

### Post by levele304 on 2007-08-28
ok, so I got it to show the temp, but it is perpetually set at 51C.

I tried descreasing the nc value to 80, both in the gedit command you gave and also the conkyrsc file. 

However, the 51C remains unchanging.

---

### Post by herbster on 2007-10-14
I also had to use:

```
 ${execi 300 nc localhost 7634 | cut -c54-55 ;} 
```

Works great, thanks for the HowTo! :)

---

### Post by iva2k on 2007-10-26
Even better - put these into your .conkyrc:

```

HDA Temp: ${exec nc localhost 7634 | cut -f 4 -d "|"} C
HDB Temp: ${exec nc localhost 7634 | cut -f 9 -d "|"} C
SDA Temp: ${exec nc localhost 7634 | cut -f 14 -d "|"} C 

```
or instead of "exec" use "execi X" where X is number of seconds  - interval at which to run.

First T field is at 4, then all fields added at 5 intervals, so edit -f N accordingly. This will keep working even if you swap disk drives, though it will shift if a drive is removed.

Run:
```
nc localhost 7634
```
to see your reported hddtemp's and figure out what numbers to use in -f N in the code above.

-- cheers!

---

### Post by Bravo on 2007-10-30
I've got a weird problem. Last Sunday I configured hddtemp en conky the way described above and it worked like a charm.
Today I had to do a reboot (to get ALSA finally working :) ) and it ain't working anymore. I've checked and rechecked the files but hddtemp seems to be the pain. This is the output it gives:
```
bravo@Scarab:~$ sudo nc localhost 7634
|/dev/sda|ST3300831AS                             &#65533;|29|C|
```
Only the first drive seems to be visible, this also happened to gkrellm. Anyone an idea what has gone wrong?

Some things I already tried: 
Change DISKS to "/dev/sda" "/dev/sdb"
Change DISKS to '/dev/sda1" "/dev/sdb1"

My hddtemp config:
```
# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# Master system-wide hddtemp switch. The initscript will not run if it is not
# set to true. STOP THE SERVICE BEFORE DISABLING IT!

# [automatically edited by postinst, do not change line format or set it to
# anything but false or true ]
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
DISKS="/dev/sda /dev/sdb /dev/sdc /dev/sdd1"

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures.
SYSLOG="300"

# Other options to pass to hddtemp
OPTIONS=""
```

EDIT:
I don't know why, but after switching from Firestarter to my own configured iptables it works again. Although both allow all loopback traffic. I keep my fingers crossed for the next reboot (that'll be in another 15 days or so :D )

---

### Post by herbster on 2007-12-17
Okay, I've just installed Arch and upon running hddtemp /dev/sda and sdb, the temp displays fine, but nc localhost 7634 does absolutely nothing. I am running the hddtemp daemon. Any ideas?

---

### Post by CanonKen on 2007-12-19
Any ideas why I get this?

> ken@ubuntu:~$ nc localhost 7634
localhost [127.0.0.1] 7634 (?) : Connection refused
ken@ubuntu:~$ 


---

### Post by ifmn on 2007-12-22
Why do you need nc at all?

sudo chmod +s /usr/sbin/hddtemp         #use your path

works for me. BTW file owner must be root.
Also, no need for cut - use "-n": ${execi 60 hddtemp /dev/hda -n;}C. Please edit your guide :)

---

### Post by herbster on 2007-12-22
> **ifmn said:**
> Why do you need nc at all?

mv /usr/sbin/hddtemp /bin
sudo chmod +s /bin/hddtemp

works for me.
Also, no need for cut: ${execi 60 /bin/hddtemp /dev/disk/by-uuid/AAAA-AAAA -n;}C. Please edit your guide :)

Moved hddtemp accordingly, but adding that to my .conkyrc don't work :(

---

### Post by ifmn on 2007-12-22
file owner must be root and your fs must support setuid. also use your own hard drive f.e /dev/sda or use uuid as me.

---

### Post by Cammy on 2008-01-25
Ok, I got this working following the guide on the first page of this thread, and everything was perfect.

Now I've noticed that one of my drives (/dev/hda) won't show temp.

I made the changes that ifmn suggested, and now I can get temp from conky using ${hddtemp /dev/hd*} but it only works for hdb, and not for hda.

If I open a terminal, both work:
```

hddtemp /dev/hda
/dev/hda: ST380215A: 24°C

hddtemp /dev/hdb
/dev/hdb: ST380011A: 26°C
```

But in conky only the second one works.  The first one shows "N/A".

Same with the nc method:

```
nc localhost 7634
|/dev/hdb|ST380011A|26|C|
```

Why on earth would hda suddenly disappear, and how do I get it back?

---

### Post by BassKozz on 2008-04-03
I followed the instructions but the displayed result in Conky is "**LRC**", what does that mean:confused:

Here is what it looks like in term:
```
nc localhost 7634
|/dev/sda|WDC WD1500ADFD-00NLR5|29|C||/dev/sdb|HDS724040KLSA80|27|C|cholate@cholate-
```

---

### Post by JT9161 on 2008-05-08
Does anyone know how I can change the unit used from Celsius to Fahrenheit?

---

### Post by toorima on 2008-05-09
hddtemp --unit=F

---

### Post by thorcik on 2008-05-21
big thanks, it works! now I could finish refining my system monitor ;o)

---

### Post by twodayslate on 2008-06-16
> **CanonKen said:**
> Any ideas why I get this?

I get the same error.

---

### Post by piponazo on 2008-08-11
Hi! I can retrieve the hard drive temperaturas easily with:

```

Temp HDD-IDE: ${hddtemp /dev/hdb}
Temp HDD-SATA: ${hddtemp /dev/sda}
```

However, it seems the update intervals are longer than the value of the update_interval variable (1 second).

Anoyone have this problem? Is it normal?

---

### Post by Kooothor on 2008-09-10
thanks :D

---

### Post by detroit/zero on 2008-09-23
**How To get conky to display hard drive temperature as a non-root user**

**Caveat:**
hddtemp requires root privledges [sic] to use.

**Workaround:**
change permissions of the hddtemp command so non-root users can execute it.

**Prerequisites:**
1. conky installed & working  apt-get install conky
2. hddtemp installed  apt-get install hddtemp

**The process:**
Once you've got hddtemp installed, go to your terminal prompt and enter the following:
```
chmod u+s /usr/sbin/hddtemp
```That's it! You're done!

Now, go to a terminal and type "hddtemp" and your device name at the prompt. For example:
```
zero@zero-laptop:~$ hddtemp /dev/sda
/dev/sda: Hitachi HTS541612J9SA00: 42°C
```Or, for the $execi command inside conky, it's as easy as (using myself as the example):
```
zero@zero-laptop:~$ hddtemp /dev/sda | cut -c36-40
42°C
```and that will give you a happy little degree symbol in the output and everything, if that's your thing.

Or, if it's not, you can just use conky's built-in $hddtemp variable now and avoid using the $execi variable altogether, since the [conky variable page]("http://conky.sourceforge.net/variables.html") says of all $exec commands:
```
warning: this takes a lot more resources than other variables. 
I'd recommend coding wanted behaviour in C and posting a patch. 
```By using this method, not only do you make conky use more resources by calling on netcat, but then you have netcat calling on hddtemp on top of it. Why involve three programs to do the work of one?

Just my two cents.

---

### Post by Simon-v on 2008-09-27
I looked into the methods of getting the hddtemp in conky as described here, and here are my findings:
**${hddtemp}** has the drawback of returning a value of "35C" for example, whereas i would like to have a "35°C".
Until this behavior is fixed in conky, it seems that i would have to rely on **execi**. However, there are several ways to get the reading; i tried to compare them in terms of efficiency by running every command between two **date +%N** commands, which lets us see the time (in nanoseconds) it takes to execute the command.
The results are as follows:

1) **hddtemp /dev/hda -n**
```
simon-v@SimonV:~$ date +%N; hddtemp /dev/hda -n; date +%N
025314728
37
208139494
simon-v@SimonV:~$
```
The result is in the range of 0.12-0.18 seconds, not too bad, and can be appended with a "°C" in conky for prettyness.

2) **hddtemp /dev/hda | cut -d:  -f3**
```
simon-v@SimonV:~$ date +%N; hddtemp /dev/hda | cut -d:  -f3; date +%N
362321492
 39°C
519916187
simon-v@SimonV:~$
```
The result is in the range of 0.12-0.15 seconds, which is not bad too, and gives us the reading ready for display. And it is despite the fact we had to run two programs instead of one.

3) **nc localhost 7634 | cut -d\| -f4**
```
simon-v@SimonV:~$ date +%N ;nc localhost 7634 | cut -d\| -f4; date +%N
177928746
40
224826219
simon-v@SimonV:~$
```
The result is in the range of 0.04-0.14 seconds, which is, surprisingly, the best result of the three, despite there are three programs involved. It too gives the raw reading, which is good.

I have little idea why it is quicker to netcat hddtemp than to call hddtemp (it makes some sense i must admit), but i think i'll just stick to the third option for now.

End note: $hddtemp itself seems to be using a call to the hddtemp daemon. Why should we be any different?

---

### Post by anhvu2875 on 2008-11-08
```
anhvu2875@ubuntu:~$ nc localhost 7634
|/dev/sg1|ST3160215AS|46|C||/dev/sg2|ST3250310AS|43|C||/dev/sda|ST3160215AS|46|C||/dev/sdb|ST3250310AS|43|C|anhvu2875@ubuntu:~$ 
```

my conky still does not show harddisk temp , any ideas ??
THANKS !

---

### Post by ubdime on 2008-11-08
I have 8 disks: /dev/sda to /dev/sdh

my conkyrc ended up including it like this:

```

temp: ${execi 30 nc localhost 7634 | awk -F"|" '{print "sda:",$4"C sdb:",$9 "C sdc:",$14"C sdd:",$19"C               sde:",$24"C sdf:",$29"C sdg:",$34"C sdh:",$39"C"}' | fold -w44}

```

awk keeps me from having to run 8 different nc commands that each have to query the server..

mine's set for a width of 50.. if you don't care about width, you can take out that fold and all that whitespace.. or edit out some stuff like the C or the temp: and sd[a-h]:

ends up looking like:
```

temp: sda: 35C sdb: 32C sdc: 33C sdd: 34C
      sde: 36C sdf: 36C sdg: 34C sdh: 36C

```

---

### Post by rusty_jones on 2008-11-08
```
:~$ hddtemp /dev/sdb 
/dev/sdb: ST31000333AS: 28°C
:~$ hddtemp /dev/sda
/dev/sda: WDC WD2500KS-00MJB0: 36°C

```

This is my readout for my machine. This the code for my conkyrc file.
```
${font Arial:bold:size=10}${color White}sda Temp: ${exec nc localhost 7634 | cut -f 4 -d "|"}°C
${font Arial:bold:size=10}${color White}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
${font Arial:bold:size=10}${color White}sdb Temp: 
/disk $alignc ${fs_used /dev/sdb1} / ${fs_size /dev/sdb1} $alignr ${fs_free_perc /dev/sdb1}%
${fs_bar /dev/sdb1}
```

the code for SDA works correctly, even though I don't have any code for SDB nothing I have tried does not work. Would anyone help a noob?

Rusty

---

### Post by ubdime on 2008-11-08
instead of pasting the output of hddtemp /dev/sda and hddtemp /dev/sdb,

1. look at the output of nc localhost 7634
2. look at the output of nc localhost 7634 | cut -f 4 -d "|"

then you will understand why what you were doing doesn't work
i'm guessing you need to use -f 9 for the output of your second hd
you might also want to put a time increment on your exec

---

### Post by anhvu2875 on 2008-11-08
problem was solved ! :D:D:guitar::guitar:

---

### Post by rusty_jones on 2008-11-08
First, when i put a time in on the first line of code my temp disappears.

second, i have tried what you suggested and put in my code -f 9 through about 40 all I get is a blank line in terminal.

Third, since I am new to linux I have to do a lot of reading in the forum, and I have and haven't been able to find anything that works.

Rusty

---

### Post by ubdime on 2008-11-09
What does the command "nc localhost 7634" show?

It could also be your hddtemp daemon is only set to show the first hard drive.. in which case you'll have to check your config file..

for example mine shows:
dime@lanfear:~$ nc localhost 7634
|/dev/sda|ST3500641NS|31|C||/dev/sdb|ST3500641NS|29|C||/dev/sdc|ST3500641NS|29|C||/dev/sdd|ST3500641NS|31|C||/dev/sde|ST3500641NS|32|C||/dev/sdf|ST3500641NS|32|C||/dev/sdg|WDC WD2500LB-55EDA0|34|C||/dev/sdh|WDC WD2500LB-55EDA0|34|C|

about the interval, it's not that big a deal, but it could be because you're using the "exec" variable and not the "execi" variable, which supports an interval

---

### Post by rusty_jones on 2008-11-09
nc localhost 7634 only show one hard drive.

sudo fdisk -l shows two drives

Rusty

---

### Post by rusty_jones on 2008-11-10
Problem Solved

---

### Post by duanedesign on 2008-11-23
here is another option for monitoring your hard drive temp. GNOME Sensors Applet is an applet for the GNOME Panel to display readings from hardware sensors, including CPU temperature, fan speeds and voltage readings under Linux. Alarms can be set for each sensor to notify the user once a certain high or low value has been reached, and can be configured to execute a given command at specific repeated intervals. 


This is the Terminal command:

# [COLOR="Red"]sudo apt-get install sensors-applet
[/COLOR]
visit the site for all kinds of info on supported interfaces and customizing tips.

[COLOR="Red"]http://sensors-applet.sourceforge.net/index.php?content=home[/COLOR]

---

### Post by PatrickMoore on 2009-03-08
im having trouble with getting hddtemp to work
```
patrick@patrick-laptop:~$ ps -fC hddtemp
UID        PID  PPID  C STIME TTY          TIME CMD
```

my script

```
# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# Master system-wide hddtemp switch. The initscript will not run if it is not
# set to true. STOP THE SERVICE BEFORE DISABLING IT!

# [automatically edited by postinst, do not change line format or set it to
# anything but false or true ]
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
DISKS="/dev/sda" 

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures.
SYSLOG="300"  # 300 = every 5 minutes

# Other options to pass to hddtemp
OPTIONS=""
```

any help would be appreciated. i really want this to read on my conky

---

### Post by Just64 on 2009-03-15
I have a problen with conky and hddtemp, because i dont know what is my  IP address and port of the hddtemp interface. How i can know it?

---

### Post by WiFi Ed on 2009-03-15
> **Just64 said:**
> I have a problen with conky and hddtemp, because i dont know what is my  IP address and port of the hddtemp interface. How i can know it?

These entries from the default hddtemp config file work for me:

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

Have you followed the steps outlined in the first post of this thread? After installing hddtemp did you reboot and run "sudo nc localhost 7634" from terminal?

---

### Post by Just64 on 2009-03-15
> **WiFi Ed said:**
> These entries from the default hddtemp config file work for me:

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

Have you followed the steps outlined in the first post of this thread? After installing hddtemp did you reboot and run "sudo nc localhost 7634" from terminal?

I did it all... :S

```
pato@pato-desktop:~$ sudo nc localhost 7634
[sudo] password for pato: 
localhost [127.0.0.1] 7634 (?) : Connection refused
pato@pato-desktop:~$ 

```

---

### Post by jjgomera on 2009-03-16
are you sure hddtemp is runing? to start it:

 sudo /etc/init.d/hddtemp start

---

### Post by XanTrax on 2009-03-18
If anyone uses hddtemp with conky and also uses the netstat command on the regular, you may want to use this fix for hddtemp:

[http://ubuntuforums.org/showthread.php?t=1093828](http://ubuntuforums.org/showthread.php?t=1093828)

---

### Post by tturrisi on 2009-03-18
HDDTEMP must be running as a daemon..

HDDTEMP is now a built in variable and netcat is not required anymore.

hddtemp dev, (host,(port)) 
Displays temperature of a selected hard disk drive as reported by the hddtemp daemon running on host:port. Default host is 127.0.0.1, default port is 7634.

example:
```
Hard Disk 1:$alignr{hddtemp /dev/sda 127.0.0.1 7634}
Hard Disk 2:$alignr{hddtemp /dev/sdb 127.0.0.1 7634}
```

---

### Post by cyberkost on 2009-04-19
Hmm ... so I just added
```

/dev/sda: ${hddtemp /dev/sda 127.0.0.1 7634}
/dev/sdb: ${hddtemp /dev/sdb 127.0.0.1 7634}
/dev/sdc: ${hddtemp /dev/sdc 127.0.0.1 7634}
/dev/sdd: ${hddtemp /dev/sdd 127.0.0.1 7634}

```
to my .conkyrc.  The interesting thing is that for 30 seconds it shows the actual temps, and then
/dev/sda: C
/dev/sdb: 30C
/dev/sdc: 31C
/dev/sdc: 30C
(no temp readout for /dev/sda) for another 30 sec, then back to normal, then back to missing temp for the first drive on the list.

When I make /dev/sdb the first drive on the list (and /dev/sda second) the problem moves to /dev/sdb, i.e., it's not attached to /dev/sda, but is rather attached to the 1st of the series of 'hddtemp' calls.   Has anyone seen /dealt with this?

---

### Post by tturrisi on 2009-04-20
You could try changing something in the /etc/default/hddtemp file, not sure what to change, but may affect something.  You could also try using execi to control the invervals used for each reading of temp.
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by adamvan2000 on 2009-05-06
For anyone who has more than one drive and can't get hddtemp working for them, this worked for me:
```
${execi 300 nc localhost 7634 | cut -c29-30 ;}&#7506;C
${execi 300 nc localhost 7634 | cut -c63-64 ;}&#7506;C
```

As you can see, to get the temp of the second hdd, you simply continue counting from where you left off for the previous one.  Here was the result of running ```
$ nc localhost 7634
``` in terminal.

```
|/dev/sg0|SAMSUNG SP0802N/R|39|C||/dev/sg1|MAXTOR STM3500630A|47|C||/dev/sda|SAMSUNG SP0802N/R|39|C||/dev/sdb
```

The first value, 39, is characters 29+30, and the second value, 47, is characters 63+64.

Hope that helps someone.

~adamvan2000

---

### Post by o0Chris0o on 2009-05-14
I am having some issues trying to get conky to read the hdd temps. I only have one Sata(sda) drive. My hddtemp config is default, so no need to post it. 

I am able to check the temp using the hddtemp command:

```
chris@TuX:~$ hddtemp /dev/sda
/dev/sda: Hitachi HDT721010SLA360: 35°C
chris@TuX:~$ 

```


I tried everything in this thread, so far no good. Unless I am missing something. Any help is appreciated :D

---

### Post by cyberkost on 2009-05-14
> **o0Chris0o said:**
> I am having some issues trying to get conky to read the hdd temps. I only have one Sata(sda) drive. My hddtemp config is default, so no need to post it. 

I am able to check the temp using the hddtemp command:

```
chris@TuX:~$ hddtemp /dev/sda
/dev/sda: Hitachi HDT721010SLA360: 35°C
chris@TuX:~$ 

```


I tried everything in this thread, so far no good. Unless I am missing something. Any help is appreciated :D

If the above is an excerpt from an actual xterm session, then the following should work in conky
```
${execpi 300 hddtemp /dev/sda | cut -c35-39}
```

---

### Post by o0Chris0o on 2009-05-14
> **cyberkost said:**
> If the above is an excerpt from an actual xterm session, then the following should work in conky
```
${execpi 300 hddtemp /dev/sda | cut -c35-39}
```

Very interesting it works! I had: ```
${execi 10 hddtemp --unit=F /dev/sda | cut -b11-28;}
``` but it didnt work

How do I show the make of my hard drive and model

---

### Post by cyberkost on 2009-05-14
The 'cut' command cuts (and outputs) the specified characters from the output of 'hddtemp'.  This will give you the entire output of hddtemp:
```
${execpi 300 hddtemp /dev/sda}
```
This will drop the "/dev/sda: " part:
```
${execpi 300 hddtemp /dev/sda | cut -c11-}
```

---

### Post by dino99 on 2009-05-16
hi,
Previously, on Intrepid & before, there was specialized applet for the output to place on top screen; but with Jaunty this applet don't exist !!!

After googling about hddtemp, i install conky & ask for temp each 15 seconds:
big surprise : now my hdd is badly noisy each time conky read hddtemp, and no graphic output !!!
I can't understand those devs choices; it's that way to have a more friendly distro: replace something that work well by a crappy choice ?

So, to stop this hdd noise, i uninstall conky but noise goes on and i need to erase hddtemp (/etc/init.d/hddtemp)

Now no more noise, but still no more temp

REGRESSION

---

### Post by tturrisi on 2009-05-16
> **dino99 said:**
> hi,
Previously, on Intrepid & before, there was specialized applet for the output to place on top screen; but with Jaunty this applet don't exist !!!

After googling about hddtemp, i install conky & ask for temp each 15 seconds:
big surprise : now my hdd is badly noisy each time conky read hddtemp, and no graphic output !!!
I can't understand those devs choices; it's that way to have a more friendly distro: replace something that work well by a crappy choice ?

So, to stop this hdd noise, i uninstall conky but noise goes on and i need to erase hddtemp (/etc/init.d/hddtemp)

Now no more noise, but still no more temp

REGRESSION
Hard disk noise is NOT caused by software.  You have a drive that is on its way out.  The noise you hear is the arm in the drive.  Backup your data to other media asap and replace the drive.

---

### Post by bLiZz247 on 2009-05-20
Hi, I am trying to get this to work but I keep getting "Permission Denied" Error in Terminal:

```
:~$ conky
Conky: /home/***/.conkyrc: 6: config file error
Conky: desktop window (14000a7) is subwindow of root window (13c)
Conky: window type - normal
Conky: drawing to created window (0x1a00001)
Conky: drawing to double buffer
/dev/sda: open: Permission denied

```

Also does anyone know what the config file error is as well?

Here is my .conkyrc file:

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type overide
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
 ${color 6694B2}${font OpenLogos:size=20} u t
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   
   ${font weather:size=28}x ${font}HDD ${execpi 300 hddtemp /dev/sda}°C 

   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py username password 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  UpTime:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
     ${font Radio Space:size=25}${time %I:%M %p}

```

---

### Post by cyberkost on 2009-05-20
What happens when you do ```
hddtemp /dev/sda
``` in a terminal window?  If the same things happens do ```
sudo dpkg-reconfigure hddtemp
``` and answer 'yes' to the question about whether or not you want hddtemp to be runable by regular users.

---

### Post by bLiZz247 on 2009-05-20
> **cyberkost said:**
> ```
sudo dpkg-reconfigure hddtemp
``` and answer 'yes' to the question about whther or not you want hddtemp to be runable by regular users.

Thank you! Works like a charm :D

---

### Post by gandalf2000 on 2009-05-29
Code:

sudo dpkg-reconfigure hddtemp

and answer 'yes' to the question about whther or not you want hddtemp to be runable by regular users. 


Thank you from me too.  I just built a new system and upgraded to 9.04 at the same time and have been struggling with this for hours.  Was just about to post a question when I came across this thread.  Now, what else do I want to do to my Conky?

---

### Post by cyberkost on 2009-05-29
Here's a [thread]("http://ubuntuforums.org/showthread.php?p=1645914") that probably covers everything there is in conky.  Below is a screenshot of mine.

---

### Post by Lumperhozen on 2009-06-19
hmm this doesn't seem to be working for me... when I enter the code:

**chmod u+s /usr/sbin/hddtemp** 

I get the response

**chmod: changing permissions of `/usr/sbin/hddtemp': Operation not permitted**


I'm a noob to linux- please inform me on what I'm doing wrong :(

---

### Post by cyberkost on 2009-06-19
Lumperhozen, try```
sudo chmod u+s /usr/sbin/hddtemp
``` or ```
sudo dpkg-reconfigure hddtemp
``` (answering 'Y' to the relevant question).

---

### Post by frogotronic on 2009-12-29
> **ukripper said:**
> Just installed hddtemp in feisty.

Added folowing lines to my conkyrc,
```
${hddtemp /dev/hda localhost 7634}
```

worked without making any changes as described in this Howto.
 no need to write exec script (exec takes more processing)

Awesome, this totally fixed my ERRoC message!

Thanks

---

### Post by neznajut on 2010-06-02
I have a problem

$ nc localhost 7634
|/dev/sg0|WDC WD1601ABYS-01C0A0|45|C||/dev/sg1|ST3500320AS|41|C||/dev/sda|WDC WD1601ABYS-01C0A0|45|C||/dev/sdb|ST3500320AS|41|C|

Then I put to conkyrc

HDD:${alignr}${execi nc localhost 7638 | cut -c33-34 ;} °C

And it doesn't work. Pleae help.

---

### Post by Simon-v on 2010-06-05
> **neznajut said:**
> I have a problem

$ nc localhost 7634
|/dev/sg0|WDC WD1601ABYS-01C0A0|45|C||/dev/sg1|ST3500320AS|41|C||/dev/sda|WDC WD1601ABYS-01C0A0|45|C||/dev/sdb|ST3500320AS|41|C|

Then I put to conkyrc

HDD:${alignr}${execi nc localhost 7638 | cut -c33-34 ;} °C

And it doesn't work. Pleae help.

Try putting it like this:
```
nc localhost 7634 | cut -f14 -d\|
```

You seem to have more than one HDD. This returns you the temperature of the first. To get second one, replace the **-f14** with **-f19**.

Finally, you might find the `cut` manual an interesting read. Good luck!

---

### Post by jcolyn on 2010-08-21
I have conky displaying my hard drive temp but only for 5 minutes then the temp reading drops leaving only the '°C' showing.

The temp reading in conky matches when I do the below in the terminal.

```
$ sudo hddtemp /dev/sda
[sudo] password for colyn: 
/dev/sda: SAMSUNG SP2504C: 37°C
```If I change the execi to different numbers that is how long it will display the temp.

Any ideas on how to keep the temp from dropping off.

Below is the line for hddtemp in my .conkyrc file.

```
${color white}Hard Drive Temp: $color ${execi 300 nc localhost 7634 | cut -c27-28 ;}°C
```And below is my /etc/default/hddtemp.conf file


```
# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# [automatically edited by postinst, do not change line format ]

# hddtemp network daemon switch. If set to true, hddtemp will listen
# for incoming connections.
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
DISKS="/dev/hda /dev/sda"

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures. If set to a value
# different than 0, hddtemp will run as a daemon periodically logging
# the temperatures through syslog
RUN_SYSLOG="300"

# Other options to pass to hddtemp
OPTIONS=""
```

---

### Post by cyberkost on 2010-08-21
Could it be that your hddtemp daemon dies (for whatever reason) in these 5 mins (I guess you can check is the daemon is running as well as to look into the daemon's log file)?  Why not make hddtemp user-runnable with ```
sudo dpkg-reconfigure hddtemp
``` and call the hddtemp command with execi?

---

### Post by jcolyn on 2010-08-22
> **cyberkost said:**
> Could it be that your hddtemp deamon dies (for whatever reason) in this 5 mins (I guess you can check and for that and read the daemon's log file)?  Why not make hddtemp user-runable with ```
sudo dpkg-reconfigure hddtemp
``` and call the hddtemp command with execi?

Thanks

I changed the execi 300 to execi 10 in my .conkyrc. It's been up without dropping off for over an hour now so hopefully I got it working..

---

### Post by veilside on 2010-09-26
i also used this howto for my conky but it is not working

```
hddtemp_host 127.0.0.1
hddtemp_port 7634


TEXT
1:${hddtemp /dev/sda 127.0.0.1:7634}
2:${hddtemp /dev/sdb 127.0.0.1 7634}
3:${hddtemp /dev/sdc 127.0.0.1 7634}
4:${hddtemp /dev/sdd 127.0.0.1 7634}
```here is my code and i get an output of N/A, the console error is Conky: could not connect to hddtemp host
if i just write hddtemp /dev/sda into the console it shows me the right temperature... pleaese help thanks

---

### Post by frogotronic on 2011-02-04
Upgraded to Lucid

Now Conky HDDTEMP will NOT work.

Followed this guide, but to no avail.

- CH    :popcorn:

---

### Post by MichaelGld on 2011-02-08
Not working for me either, just get an "N/A". And I do know that hdtemp is working, as I have an Avant Window Navigator applet that reads all my temps, including hard drives.

---

### Post by frogotronic on 2011-02-08
> **MichaelGld said:**
> Not working for me either, just get an "N/A". And I do know that hdtemp is working, as I have an Avant Window Navigator applet that reads all my temps, including hard drives.

Solution:

(from my .conkyrc file)

```
HDD: ${execi 5 hddtemp /dev/sda | cut -c 24-30}
```

The **cut -c** command cuts the output of the device; in this case /dev/sda from position 24 to position 30.

Use

```
hddtemp /dev/sda
/dev/sda: ST9160823AS: 38°C
```

to generate the output and count the characters from left to right.

- CH

---

### Post by MichaelGld on 2011-02-08
> **cement_head said:**
> Solution:

(from my .conkyrc file)

```
HDD: ${execi 5 hddtemp /dev/sda | cut -c 24-30}
```The **cut -c** command cuts the output of the device; in this case /dev/sda from position 24 to position 30.

Use

```
hddtemp /dev/sda
/dev/sda: ST9160823AS: 38°C
```to generate the output and count the characters from left to right.

- CH

Forgive me if I seem obtuse, but I don't understand the second bit of code. All that does is print what it says. I'd appreciate it if you could clarify for a non-programmer/relative newbie.

Thanks

---

### Post by frogotronic on 2011-02-08
@MichaelGld

No problem.

In a terminal (Applications>Accessories>Terminal)

```
sudo dpkg-reconfigure hddtemp
```

Read the instructions to make make hddtemp accessible as normal user (not as a super, or root only user).

then type 

```
$ hddtemp /dev/sda
```

into a termimal and you should get something like this back:

```
/dev/sda: ST9160823AS: 42°C
```

Then, count the number of characters from the first forward slash "/" to the first digit (in this case a 4) and to the C of degrees C.  This range is character 24 to character 30 in my case.  Yours may differ depending on the name of your drive (in my case ST9160823AS).

After that put this information into your .conkyrc file
```

HDD: ${execi 5 hddtemp /dev/sda | cut -c 24-30}
```

Post back if you still have questions.

- CH    :guitar:

---

### Post by MichaelGld on 2011-02-08
> **cement_head said:**
> @MichaelGld

No problem.

In a terminal (Applications>Accessories>Terminal)

```
sudo dpkg-reconfigure hddtemp
```Read the instructions to make make hddtemp accessible as normal user (not as a super, or root only user).

then type 

```
$ hddtemp /dev/sda
```into a termimal and you should get something like this back:

```
/dev/sda: ST9160823AS: 42°C
```Then, count the number of characters from the first forward slash "/" to the first digit (in this case a 4) and to the C of degrees C.  This range is character 24 to character 30 in my case.  Yours may differ depending on the name of your drive (in my case ST9160823AS).

After that put this information into your .conkyrc file
```

HDD: ${execi 5 hddtemp /dev/sda | cut -c 24-30}
```Post back if you still have questions.

- CH    :guitar:
Ok, now I understand it.

Problem is, I get nothing on the conky area from that except the "HDD".

Ok, I just checked the output to a terminal window and it's saying "open, permission denied."  I'm sure it needs a "sudo" in there somewhere. Any idea how to implement that?

Thanks

---

### Post by frogotronic on 2011-02-09
> **MichaelGld said:**
> Ok, now I understand it.

Problem is, I get nothing on the conky area from that except the "HDD".

Ok, I just checked the output to a terminal window and it's saying "open, permission denied."  I'm sure it needs a "sudo" in there somewhere. Any idea how to implement that?

Thanks

Yes, you need to do the

```
sudo dpkg-reconfigure hddtemp
```

part of my post and then reboot

- CH

---

### Post by MichaelGld on 2011-02-09
> **cement_head said:**
> Yes, you need to do the

```
sudo dpkg-reconfigure hddtemp
```part of my post and then reboot

- CH
That worked! Many thanks!

---

### Post by Skip Da Shu on 2011-03-02
> **cyberkost said:**
> If the above is an excerpt from an actual xterm session, then the following should work in conky
```
${execpi 300 hddtemp /dev/sda | cut -c35-39}
```

Would think this would also work:

```
${hddtemp /dev/sda -n}
```

---

### Post by AllGamer on 2011-08-30
I did it with this way, it looks much more informative, also you can see exactly which drive it is.

Doing it just with temp, and then manually entering text in conky might get you the wrong info, if you ever changed, move, or replaced a drive, /dev/drive letter will change and the information becomes innacurate.

This method will automatically keep the correct drive letter + disk model + temp in 1 line

```

${execi 1 nc localhost 7634 | cut -f01-04 -d\|}C
${execi 1 nc localhost 7634 | cut -f06-09 -d\|}C
${execi 1 nc localhost 7634 | cut -f11-14 -d\|}C
${execi 1 nc localhost 7634 | cut -f16-19 -d\|}C
${execi 1 nc localhost 7634 | cut -f21-24 -d\|}C
${execi 1 nc localhost 7634 | cut -f26-29 -d\|}C
${execi 1 nc localhost 7634 | cut -f31-34 -d\|}C
${execi 1 nc localhost 7634 | cut -f36-39 -d\|}C
${execi 1 nc localhost 7634 | cut -f41-44 -d\|}C
${execi 1 nc localhost 7634 | cut -f46-49 -d\|}C
${execi 1 nc localhost 7634 | cut -f51-54 -d\|}C
${execi 1 nc localhost 7634 | cut -f56-59 -d\|}C
${execi 1 nc localhost 7634 | cut -f61-64 -d\|}C
${execi 1 nc localhost 7634 | cut -f66-69 -d\|}C

```

output looks like this

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201125&stc=1&d=1314733505[/IMG]

---

