---
title: "i can't control tvtime volume control, its stuck at 0"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by opendevlite on 2014-03-06
my

```
cat /proc/asound/cards
```

returns

```

0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe244000 irq 43
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe240000 irq 16
 2 [Generic_2      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe140000 irq 44
 3 [Device         ]: USB-Audio - Generic USB Audio Device
                      Generic USB Audio Device at usb-0000:00:13.0-3, full speed
```

i tried

```
tvtime --mixer="hw:1/Line"
```

but still no go, i have sound though and can control Line-In outside of tvtime in alsa-mixer gui, Line-In by the way can be controlled in [Generic_1    ]

can somebody help me

thanks

---

### Post by opendevlite on 2014-03-07
please excuse me, just trying to bump my last one

---

