---
title: "ndp command is not available"
date: 2021-10-01
forum: New to Ubuntu
---

### Post by toot-fluegelhorn on 2021-10-01
No neighbour discovery protocol commands for ip6 make it.
The equivalent to 'ndp' command, [FONT=&quot]netstat -f inet6 -rn yields an error


[/FONT]root@scorcher:/etc/gnome# netstat -f inet6
netstat: feature `AF BLUETOOTH' not supported.
Please recompile `net-tools' with newer kernel source or full configuration.

so what's the method to dump the ip6 neighbor cache?

Please advise

---

### Post by Holger_Gehrke on 2021-10-01
I think your Google-fu has failed you, young grasshopper ;)

Searching for 'ipv6 ndp tools linux' has 'ndisc6' as one of the first hits. It's in the repositories and it's description makes me think it's what you're looking for.

netstat is definitely the wrong tool for this (much too high level ... it's concerned with existing connections, mainly) and the option -f is short for --rfcomm (radio frequency communications ? that would explain the error you get ...). You probably meant 'netstat --protocol=inet6' or 'netstat -A inet6' or 'netstat -6' ...

Holger

---

### Post by TheFu on 2021-10-01
Doesn't **ip neigh** do something similar?  I don't use IPv6 (have it disabled on all my systems), but for ipv4, it seems to show the arp table. Is that what you seek?

The ip manpage has a few other options too.

---

### Post by The Cog on 2021-10-02
Yes, **ip neighbor** or just **ip n** for short shows the content of both the IPv4 and IPv6 neighbour caches.

@Holger_Gehrke: Ooh, thanks. I didn't know of that package.

---

### Post by toot-fluegelhorn on 2021-10-06
Thank you all for your insights. 
@Holger_Gerke my arms hurt from lifting that red hot vase.. What say you, holding a pint of Dortmunder Union to it might help?

---

