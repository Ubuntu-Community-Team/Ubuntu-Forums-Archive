---
title: "Trouble manually starting the audio driver"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by FortuneCookie on 2012-09-04
Well my audio isn't working and I'm following [this guide]("https://help.ubuntu.com/community/SoundTroubleshooting") to make it work again. 

I have to manually install my audio driver (HDA Intel)  but when I type the command I get:

```
fortunecookie@fortunecookie-h8-1020nl:~$ sudo modprobe snd-HDA intel
FATAL: Module snd_HDA not found.

```What do I do?

Thanks

Fortunecookie






btw the reason I think HDA Intel is my audio driver is because I got this  when using a hardware information command
```

           *-multimedia
                description: Audio device
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:53 memory:fe640000-fe643fff
```
Thank you for your help

Fortunecookie

---

### Post by Bashing-om on 2012-09-05
FortuneCookie;

  I have limited experience with audio difficulties; But, I am will to help.
Let's start with seeing what driver is actually loaded, submit the results of the terminal command:
```

lspci -v | grep -A7 -i "audio"
```Then we will see if we can get your audio functional.
[INDENT]regards <==BDQ

[/INDENT]

---

