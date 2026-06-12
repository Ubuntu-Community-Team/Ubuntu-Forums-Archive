---
title: "Figured you guys may know..  Conky, possible to list multiple interfaces as arguments"
date: 2008-01-08
forum: Programming Talk
---

### Post by Mysticle31 on 2008-01-08
I'm not sure if I worded everything correctly.  I'm very new to this sort of thing.

Basically on my laptop there are two networking options.  Wireless and Wired.

I was trying to find a way to make it display the SSID, Bitrate, Mode, AP MAC, Signal strength and IP to eth1 only when the wireless was "connected"  

However that seems impossible.

So I will settle for being able to bind Downspeed, Upspeed, the downspeed and upspeed graphs..etc to two interfaces.

Is this possible?

Here is an excerpt of my conkyrc file

> ${color yellow}NETWORKING (${addr eth1})${color red}(${addr eth0}) ${color yellow}${hr 2}$color
${color white}SSID: ${color green} ${wireless_essid eth1} - ${wireless_ap eth1}$alignr ${wireless_link_qual eth1}%
${color white}Mode: ${color green} ${wireless_mode eth1} $alignr ${color white}Bitrate: ${color green}${wireless_bitrate eth1}
${color white}Public IP: ${color green}${execi 7200 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
${color white}Down: ${color green}${downspeed eth1} k/s ${alignr}${color white}Up:${color green} ${upspeed eth1} k/s
${color #DFDFDF}${downspeedgraph eth1 25,140 FF8200 ff0000} ${alignr}${upspeedgraph eth1 
25,140 FF0000 FF9900}$color
${color white}Total: ${color green}${totaldown eth1} ${alignr}${color white}Total:${color green} ${totalup eth1}
${color white} Inbound:${color green} ${tcp_portmon 1 32767 count} ${color white}Outbound:${color green} ${tcp_portmon 32768 
61000 count}${alignr} ${color white}Total: ${color green}${tcp_portmon 1 65535 count}

I'd be looking for something like.. 

${downspeed eth1+eth0} k/s

Keep in mind I have no idea what I'm doing.  You guys get the idea :P

---

