---
title: "Sound Issues"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-11-26
when ever i unmute my sound i get is a rapid critical sound casued from a faulty sound driver i'm using ubuntu latest release.... so i need some way to fix my sound driver.

---

### Post by nhasian on 2008-11-27
lets start with what kind of soundcard you have?

can we have the output of: 

```
lshw -C multimedia
```

---

### Post by 133794m3r on 2008-11-28
it's stopped now but this is it... ```
*-multimedia            
       description: Multimedia audio controller
       product: IXP SB400 AC'97 Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.5
       bus info: pci@0000:00:14.5
       version: 80
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp

```

---

