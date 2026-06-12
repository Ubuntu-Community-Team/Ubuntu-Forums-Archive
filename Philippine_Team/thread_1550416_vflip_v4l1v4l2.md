---
title: "vflip v4l1/v4l2"
date: 2010-08-11
forum: Philippine Team
---

### Post by Script Warlock on 2010-08-11
anyone knows how to change the webcam orientation in ubuntu like vertical flip? got a4tech on my shop and mount it upside down and i'd like to change the setting.

---

### Post by Script Warlock on 2010-08-13
hayz 2days of hunting the vflip wala pa talagang malinaw na solution siguro pabyaan ko muna to until na malagyan ng vflip option ang zc3xx...

---

### Post by Script Warlock on 2010-08-13
ehm i got a temporary fix for my concern:

export LIBV4LCONTROL_FLAG=3

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so gyachi
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and the a4tech webcam flips!!!

para di babalik sa dating image settings ginawan lang ng wrapper script ang lahat na apps na nangangailangan ng flip webcam like messengers but not facebook :) pero sige lang atleast nagawa ko na baliktarin ang aking mukha sa webcam hekhek.

@loell, boss paano ba magmark ng solved?

---

