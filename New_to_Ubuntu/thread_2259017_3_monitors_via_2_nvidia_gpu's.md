---
title: "3 monitors via 2 nvidia gpu's"
date: 2015-01-01
forum: New to Ubuntu
---

### Post by Anonymous_Human on 2015-01-01
Currently I have two monitors both connected to my nVidia graphics card gtx550ti . If I wanted to extend my desktop to include a third monitor(just for running a full size terminal session to print errors-I am a developer/programmer), could I do this by adding a second nVidia card? I wanted to ask before I tried it so my driver's don't step on top of each other or mess something up. The new nVidia card I would add is slightly older than the card I have now in my signature.

---

### Post by DuckHook on 2015-01-03
According to the spec sheet, you have an extra mini-HDMI port available on this card. If so, then you won't need another card, which can be problematic in Linux. Instead, the proper cable or adapter can let you attach your third monitor to the HDMI port and you would be good to go.

It used to be that two-card configurations were not good on Linux. I don't know if things have changed recently. I haven't had the need to try configuring two cards in the last two years and things change so fast in Linux that the situation may be entirely different now. That said, if you already have a third video port, then the easiest solution is to make use of it and avoid any potential problems altogether.

---

### Post by Anonymous_Human on 2015-01-06
So the third unused port on my GPU would be able to feed a 3rd monitor eventhough in the specs of this cards it only supports up to two monitors?

---

### Post by DuckHook on 2015-01-06
> **Anonymous_Human said:**
> ...the specs of this cards it only supports up to two monitors?You didn't mention that the specs max out at two. I don't have this card and am just going by the specs on the nVidia website, which are for the reference design. It depends greatly on your actual card design and the implementation of your OEM. The nVidia spec sheet doesn't state a maximum. I'm guessing that your card has two RAMDACs, but these days many cards are designed so that one can be assigned to the two DVI ports, and the other to the HDMI. Splitting one RAMDAC between two DVIs will normally only be successful if the monitors are newish and absolutely identical, and some OEM designs won't allow it no matter what.

Having said all of that, nVidia is unlikely to offer three ports on their reference design unless there was a way of outputting to all three. It's easy enough to try it out before you spring for another card.

P.S. If you *are* thinking of buying another card because of limitations on your current one, you may wish to consider buying a single card that *is* capable of driving multiple monitors. I have a HIS AMD HD 7950 which can drive up to 6 monitors over its DisplayPorts (using some fancy hubs and active adapters) or 4 monitors natively. They are incredibly cheap these days ($120 on NewEgg and eBay) considering all that you are getting. If you are committed to nVidia, I'm sure they make something similar. Linux is still not as sophisticated as Windows in the video department and it's usually best to keep it simple (i.e. stick to a single card). If you successfully get two cards working, I'm sure forum members would be interested in hearing how you managed it.

Cheers and Happy Ubuntuing!

---

### Post by efflandt on 2015-01-06
I have a GTX 550 Ti and did not even realize that the HDMI port is a mini. I guess I have been using DVI to HDMI cable all along with this card. I think it does only have 2 DAC's. The mini-HDMI can be used "instead" of one of the DVI ports (likely the one closest to it) or maybe it could output the same content to both of those ports. One thing that surprised me is that it is capable of doing audio through a DVI to HDMI cable, but apparently that is possible now. I normally use analog stereo (2.1 speaker system with subwoofer). But one time I was using digital audio for wireless Plantronics headset and when the battery ran down on the headset and I unplugged its wireless dongle, my system automatically switched over to digital audio through DVI to HDMI to my HDTV.

I recently switched that card over to a GTX 750 TI (which with Maxwell chip uses half the power, 60w vs 116w). It can support 3 monitors, but one of its outputs is VGA (MSI TwinFrozr Gaming).

---

