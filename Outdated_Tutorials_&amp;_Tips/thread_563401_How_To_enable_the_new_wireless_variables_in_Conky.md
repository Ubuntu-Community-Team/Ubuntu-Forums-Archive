---
title: "How To enable the new wireless variables in Conky"
date: 2007-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by tturrisi on 2007-09-29
The latest version of Conky has some new variable for wireless.  However, these variable are NOT enabled in a default Conky install from the Debian repos or even when building from source code.

wireless variables: (net = interface name = ethX, athX, wlanX, etc.
```
wireless_essid 	net 	 Wireless access point ESSID (Linux only)
wireless_mode 	net 	Wireless mode (Managed/Ad-Hoc/Master) (Linux only)
wireless_bitrate 	net 	Wireless bitrate (ie 11 Mb/s) (Linux only)
wireless_ap 	net 	Wireless access point MAC address (Linux only)
wireless_link_qual 	net 	Wireless link quality (Linux only)
wireless_link_qual_max 	net 	Wireless link quality maximum value (Linux only)
wireless_link_qual_perc 	net 	Wireless link quality in percents (Linux only)
wireless_link_bar 	(height), (width) net 	Wireless link quality bar (Linux only)  
```

To enable these wireless variables you have to configure with certain flags and then build & install.

First, you need to grab all the required development packaged needed to configure & build Conky:
```
apt-get install build-essential linux-headers-`uname -r` pkg-config libiw-dev libx11-dev libxau-dev libxdmcp-dev libxext-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev xtrans-dev libglib2.0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libxft-dev libxrender-dev x11proto-render-dev zlib1g-dev libxdamage-dev libxfixes-dev x11proto-damage-dev x11proto-fixes-dev
```

Next, download the latest Conky & extract it to /usr/src:
[http://sourceforge.net/projects/conky/](http://sourceforge.net/projects/conky/)

Next, configure with needed flags:
--prefix=/usr iensures Conky gets installed in /usr/bin
--enable-wlan ensures wireless variables are available
```
cd /usr/src/conky-1.4.7
./configure --prefix=/usr --enable-wlan
```

Next, build & install
```
make
make install
```

See this page of mine for screenshots and other info:
[http://members.cox.net/tonyt/d830/](http://members.cox.net/tonyt/d830/)

---

### Post by tturrisi on 2007-10-01
Screenshot of just the wireless variables:

---

### Post by Diabolis on 2007-10-11
It worked perfectly, thanks for the instructions. 

I noticed at the end of the output a line that said "RSS: no", or something like that, so could I enable it with a flag like this one: --enable-rss?. And if that is the case, what could I do with it because I do not remember any rss variables in conky.

---

### Post by tturrisi on 2007-10-11
AFAIK rss is already enabled unless you configure w/out rss.
see /usr/src/conky-1.4.7/doc/variables.html
and see
[http://phorolinux.com/how-to-display-rss-feeds-on-your-ubuntu-desktop.html](http://phorolinux.com/how-to-display-rss-feeds-on-your-ubuntu-desktop.html)

---

### Post by n3tfury on 2007-10-24
thanks for the tute.  1.4.8 just came out so i used that instead, but maybe that's my problem here:

```
conky: timed_thread.c:90: timed_thread_create: Assertion `(start_routine != ((void *)0)) && (interval_usecs >= 50000)' failed.
Aborted (core dumped)

```

an idea what's going on with that?

---

### Post by phil++ on 2007-10-24
> **n3tfury said:**
> thanks for the tute.  1.4.8 just came out so i used that instead, but maybe that's my problem here:

```
conky: timed_thread.c:90: timed_thread_create: Assertion `(start_routine != ((void *)0)) && (interval_usecs >= 50000)' failed.
Aborted (core dumped)

```

an idea what's going on with that?

Yes,that's a new bug with 1.4.8 that you will see:

a) if you do not use a .conkyrc and use the built-in default config instead or
b) set any thread-oriented timing interval to a value <= 0.05 secs.

In most cases, a) will be the reason for that error.  Simply use one
of the many .conkyrc's out there as a starting point and tailor it to fit
your needs.

Look for 1.4.9 soon to fix a few minor issues like this one and also to
externalize the default conky config, e.g. into /etc/conky/conky.conf, 
so sys admins can adjust the default look of conky.

---

### Post by n3tfury on 2007-10-24
good to know, thanks.  i'll try a known wireless config (which is why i wanted the latest version) and see how it goes.

---

### Post by tturrisi on 2007-10-24
Upon further investigation:
--enable-wlan will build w/ RSS capability.

---

### Post by kevdog on 2007-10-24
Great tutorial -- particularly listing the dependencies needed since the conky website is terrible at telling you the dependencies needed to compile the package.

Im currently using the svn of conky(1).  I thought you needed the --enable-rss flag, but I cant be certain since I havent compiled it in a long time.

Wondering if you had found any other new features in the conky svn.  The irc channel isnt too helpful at answering questions.

---

### Post by phil++ on 2007-10-25
> **kevdog said:**
>  The irc channel isnt too helpful at answering questions.

sure we are, just ask nicely :-]

---

### Post by tturrisi on 2007-10-25
> **kevdog said:**
> Wondering if you had found any other new features in the conky svn. .
Have a look at the doc dir in /usr/src/conky.

---

### Post by tturrisi on 2007-10-27
moved here from a private message:
> First i tried the "wireless_essid" and it works. Also the "wireless_ap" works. But signal quality and stuff dosent work at all. It says "ukn" (probably unknown) and "0" for "wireless_link_qual" and "wireless_link_qual_perc". Any ideas why conky wont show my signal strenght? I got a Cnet cwp 854 PCI adapter. And running ubuntu 7.10. Conky 1.4.7 are in the repositories and i have also installed 1.4.8 from src. But neither of them works with the signal quality. The gnome network applet shows me signal strength tho, so its kinda strange.
Marsan
Post your .conkyrc.
It is possible that the Ralink chipset is not fully supported by Conky wireless variables.

---

### Post by Marsan on 2007-10-27
Thanks for the reply tturrisi. Here is my .conkyrc with a screen of conky print.

```
# Create own window instead of using desktop (required in nautilus)
# Note that own_window_type is set to normal so that it will run on fluxbox; default is override
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
#use_spacer yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
#minimum_size 275 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font -*-dejavu sans-medium-*-*-*-9-*-*-*-*-*-*-*
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
#stippled_borders 3

# border margins
#border_margin 9

# border width
#border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
#default_color grey

#own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10
TEXT

SYSTEM ${hr 2}
$nodename
$time
Uptime: $uptime_short
$kernel on $machine

CPU ${hr 2}
CPU: $freq_g Ghz
CPU temp: $acpitemp C
CPU use: $cpu % $alignc${cpubar 8}
Processes: $running_processes/$processes

MEMORY ${hr 2}
Memorey usage: $mem/$memmax
$memperc % $alignc${membar 8}

NAME CPU% MEM%
${top name 1}${top cpu 1} ${top mem 1}
${top name 2}${top cpu 2} ${top mem 2}

DISKS ${hr 2}
Home: ${fs_free /home} ${fs_used_perc /home}% ${fs_bar 8 /home}
Lager: ${fs_free /media/Lager} ${fs_used_perc /media/Lager}% ${fs_bar 8 /media/Lager}

NETWORK ${hr 2}
IP: ${addr wlan0}
Signal: ${wireless_link_qual_perc wlan0}
Down: ${downspeed wlan0} Kb/s ${alignr}Up: ${upspeed wlan0} Kb/s
${downspeedgraph wlan0 15,50 ffffff ffffff} ${alignr}${upspeedgraph wlan0 15,50 ffffff ffffff}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
```

---

### Post by tturrisi on 2007-10-27
are you using ndiswrapper?

---

### Post by Marsan on 2007-10-27
Nope. Using the RT2500 driver from the kernel.

---

### Post by tturrisi on 2007-10-28
Did you completely remove-uninstall the conky you gout from the repos?

---

### Post by Marsan on 2007-10-28
Yeah. I completly removed the package from the repo when i tried the 1.4.8 src version.

---

### Post by tturrisi on 2007-10-29
Odd that it doesn't work.
Open a term and run:
conky -v
Post the result.
It should look s/g like this:
```
 d830:~# conky -v
Conky 1.4.7 compiled Tue Sep 25 14:26:28 EDT 2007 for Linux 2.6.22-2-686 (i686)

Compiled in features:

 X11:
  * Xdamage extension
  * Xdbe extension (double buffer)
  * xft

 Music detection:
  * mpd

 General features:
  * hddtemp
  * portmon
  * wireless

```

---

### Post by Marsan on 2007-10-29
Hei tturrisi. Thanks for another reply. My conky -v looks like this:

```

marsan@marsan-desktop:~$ conky -v
Conky 1.4.7 compiled Thu Sep  6 11:25:25 GMT 2007 for Linux 2.6.15.7 (i686)

Compiled in features:

 X11:
  * Xdamage extension
  * Xdbe extension (double buffer)
  * xft

 Music detection:
  * mpd

 General features:
  * hddtemp
  * portmon
  * rss
  * wireless


```

---

### Post by tturrisi on 2007-10-29
OK, I just wanted to be sure that the correct vers of conky runs.
This quality.sh  should diaplay the qualities, if not then I have no clue....
```
#!/bin/bash

# Find device used for wifi.
devlist=$(cat /proc/net/wireless | tail --lines=1) 2>/dev/null
devleft=${devlist#' '*}
devright=${devlist%%':'*}
echo $devright | grep "" > /tmp/dev_pure
device=$(cat /tmp/dev_pure)

# Get Quality
iwconfig $device | grep Link > /tmp/link
quality=$(cat /tmp/link | grep "Link")
echo $quality 
```

---

### Post by Marsan on 2007-10-30
Thanks for all your help tturrisi. I think this is a no go for now. The quality.sh gave me this:

```

marsan@marsan-desktop:~$ bash quality.sh
Link Signal level=-68 dBm

```

Not so diffrent from the link signal level in my iwconfig:

```

wlan0     IEEE 802.11g  ESSID:"Steinaasen40"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
         ** Link Signal level=-68 dBm  **
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by tturrisi on 2007-10-30
OK.  If the script and iwconfig give only thise results then the chipset driver does not support all of the wireless extensions.  No joy....

---

### Post by mongobongo on 2008-02-26
I installed Conky 1.4.8 and wireless worked fine for me.  All I had to do was reference eth1 (which is my wireless adapter) instead of eth0.

${color #5b6dad}Wireless:
 ${color #5b6dad}Down:${color #7f8ed3} ${downspeed **eth1**} k/s${color #5b6dad}${offset 80}Up:${color #7f8ed3} ${upspeed **eth1**} k/s
${color #000000}${downspeedgraph **eth1** 32,150 000000 7f8ed3} ${color #000000}${upspeedgraph **eth1** 32,150 000000 7f8ed3}
 ${color #5b6dad}Address: ${color #7f8ed3}${addr eth1}${alignr}${color #5b6dad}TCP Connections: ${color #7f8ed3}${tcp_portmon 1 65535 count}  

I am using ndiswrapper also.

---

### Post by halitech on 2008-07-31
just followed this with the new 1.6.0 on Hardy and it worked like a charm :) Now I can keep track of my wireless signal

---

### Post by onek1ll on 2009-06-13
Here is my conky setup and desktop with the wifi signal percent variable. Looking lovely!

---

### Post by bobmendon on 2009-08-13
Onekill, would you mind sharing your code? I liked the layout and I'm looking for something for my notebook.

---

### Post by graaant on 2009-10-19
My wireless signal sits at 70% all the time, even though NM-Applet tells me 100% the bar however is indicating 100%
Anyone know why this would be?

```
NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0}/ps
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0}/ps
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local IP: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public IP: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
```

Another little thing that bugs me, although off topic.. I want Local IP and Public IP to retain the uppercase/caps for IP however it displays as Ip and looks funny.

Anyone know how to remedy that?

---

### Post by graaant on 2009-10-19
Ah! I see now!

"wlan0     IEEE 802.11abgn  ESSID:"CCCUpstairs"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:4D:03:E7:F4   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-21 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
"

So it's 70/70 which is really 100% but this is a weird display. Can I change this?

---

### Post by robbiemacg on 2010-09-03
This is an old thread, but I just recently encountered the same issue mentioned by [URL="http://ubuntuforums.org/member.php?u=862040"]graaant
[/URL] above.
If your Conky is displaying signal strength as a fraction of some arbitrary number you just have to change a small piece of your code:
Find
```
${wireless_link_qual wlan0}
``` change it to
```
${wireless_link_qual_perc wlan0}
```That should fix your problem.

---

