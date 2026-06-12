---
title: "How to prevent immediate wake ups when using Wake On Phy / Unicast?"
date: 2018-05-01
forum: New to Ubuntu
---

### Post by hollov.ub on 2018-05-01
Right now I can use wake on lan with magic packets but I'd like to be  able to wake my machine by network activity, so I don't have to use a  tool to send magic packets. It should wake if I'd like to access it eg.  via samba share.
  
As far as I know wol p (phy) or u (unicast) options should do the trick (according to [ethtool man]("https://wiki.archlinux.org/index.php/Wake-on-LAN#Enable_WoL_on_the_network_adapter")). But when I turn on either of these options my machine wakes up immediately from sleep (S3) or shutdown (S5).

Please note that if I turn on **just** the g (magic packet activity) option it stops waking automatically (and successfully wakes when I send magic packet to it).
  
[LIST]
[*]OS: Lubuntu 17.10 
[*]My machine is an Intel D525MW 
[/LIST]
  I'm guessing it wakes up automatically because it is connected to the  router. But if it's true, how am I suppose to use "Wake on phy  activity" or "Wake on unicast messages" then? Can anyone point me in the  right direction?

---

