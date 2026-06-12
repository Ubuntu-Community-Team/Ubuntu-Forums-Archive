---
title: "ubuntu tablet packages"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by hookitup on 2012-05-14
so hello people, i have a gateway tablet laptop, i installed ubuntu on it, what packages do i need to enable the touch capabilities and stuff , it is the most current version of ubuntu 12.04.


Thanks

---

### Post by Favux on 2012-05-15
Hi hookitup,

It depends on what model it is.  Can you post that?  Is it a slate tablet or convertible?

Does it have a stylus?  Or is it suppose to be just touch?  Or have both?

If it is an older model it might require the fpit driver, some had a Wacom digitizer.

What is the output in a terminal of?
```
lsusb
```
and
```
xinput list
```

---

### Post by hookitup on 2012-05-15
thanks for the quick reply, it is a gateway laptop/tablet model: M280E, so the screen flips around and flattens against the keyboard to make a tablet. and yes it has a stylist and i dont thinks it reacts to human touch. 

 this is the outcome of the two commands:

cj@Touch:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cj@Touch:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
cj@Touch:~$

---

