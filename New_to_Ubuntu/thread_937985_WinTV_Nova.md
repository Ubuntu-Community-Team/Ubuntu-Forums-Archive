---
title: "WinTV Nova"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by GrimBlaZter on 2008-10-04
Could anyone help me set up an old WinTV Nova-S (2000) on Ubuntu?... I've tried bfr on gutsy as well, but I got confused, nw I'm trying it again, but I'm still confused as to how I can set it up. I tried mythtv, but it was too confusing to set up for me. Then I tried Me TV which gave me this:

"There are no usable channels in the channels.conf file."

Not really sure how to put the channels in there. LSPCI gives me this for the DVB:

00:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

*Edit:*
When I tried scanning through mplayer, I got this

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace >     ~/.mplayer/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

---

### Post by cariboo on 2008-10-04
You may have to set the tuner parameter to get your card to work properly. To be able to help you we need to know what chipset your tv tuner card has. In a Applications-->Accessories-->Terminal type:

```
lspci | grep Multmedia
```

This should just output the info for your tv tuner card, please post the results in your next post.

Jim

---

### Post by GrimBlaZter on 2008-10-12
Sorry, for the delay, been having probs with ati gfx.

I entered that command into the terminal and this is the output:

00:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

It's the same at the lspci I sent before

---

