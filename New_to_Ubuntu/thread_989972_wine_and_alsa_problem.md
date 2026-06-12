---
title: "wine and alsa problem"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by c_o_c_a_s on 2008-11-22
I'm trying to run a batch process which converts a sound format into wav. To achieve this i'm using wine to run a convert.exe file which is a windows app and the only app which I know it converts this format. 

I'm running wine in ubuntu server with no sound card, but I've installed alsa-base alsa-oss alsa-utils libesd-alsa0.

Wine returns this error:

ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open)

I've tried to load snd_seq with modprobe but apparently it does not find the module file. It returns:

FATAL: Could not load /lib/modules/2.6.18-028stab059.6/modules.dep: No such file or directory

Do I need to have a soundcard to make this works? Is there any virtual device which I can use instead? Do you know any other way to overcome this problerm?


My Ubuntu version:

Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

Best Regards

---

