---
title: "Pinnacle PCTV 300i DVB and Analogue card"
date: 2006-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by IainUx on 2006-01-04
(Using Ubuntu breezy badger 386, but may be changing to AMD64 any time soon - any issues with the 64 bit version anyone?)

I have been working to egt my pinnacle card (spec above) installed and usable for both DVB and analogue.

So far I have followed the howtos (amny thanks to the MANY threads giving sound advice and steps to follow, especially :

[http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html)

which takes it to the nth degree (just dont forget to keep entering sudo).  Unfortunately, I am still trying to find out how to set myth tv to pick up UK channels - the uk_rt grabber does not seem to go well with it, but the other problem I am having is getting my card to operate as a DVB receiver.  It has both digital and analogue capability, but so for TV Viewer and Zapping TV, and KDETV can only get the analogue channels (KDETV has some erratic behaviour which only receives 1 channel, allows teletext, but no picture!!)

What must I do to get this device DVB-active for Ubuntu?

Any clues any one?

---

### Post by IainUx on 2006-01-18
Well, I guess no-one was too ready with the answer for that 1, but things have moved on: I now have a patch installed for PCTV 300i, but have found another problem...

Though I have DVB installed, Kaffeine 'cant bind info socket!' and when I run scan, it reports:

scanning /usr/share/doc/dvb-utils/examples/scan/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1882: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file o r directory

I can see frontend0 is actually in /dvb/adapter0/frontend0 and not /dev/dvb/...

I guess therefore I need some advice on configuring DVB - I have by the way tried using a DEC2000T Hauppauge device, to double check that it wasn't still and issue with the particular card, and that has not worked either, so we must be in a GENERIC DVB SETUP DISCUSSION...

Any guiding hands?

(I didn't think it would be as awkward as this)

---

