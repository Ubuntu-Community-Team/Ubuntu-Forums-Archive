---
title: "Dell 2400 dimension wireless help"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by retardoposer on 2008-06-15
i know people have been asking frequently about installing a wireless network on there new Ubuntu OS

but I've been searching for hours and cant come to a solution for my situation 

i really need help 

Situation: 

i have a dell dimension 2400, with a wireless wmp300n wireless adapter. and my OS is hardy heron

I've tried using ndiswrapper but no luck when i got to synaptic and try to add a package it doesn't work

any help???

---

### Post by shifty_powers on 2008-06-15
ok, bit more info.

is the wireless adapter a usb dongle or a pci card to being with?

---

### Post by retardoposer on 2008-06-15
it is a card. i attached it to the mother board, and there is a little node to pick up the signal

---

### Post by shifty_powers on 2008-06-15
can you post the output of

```
lspci
```

when typed in a terminal? (aand press enter of course ;))

---

### Post by retardoposer on 2008-06-15
it says command not found.

---

### Post by shifty_powers on 2008-06-15
are you sure? lspci?

could you typr it in, then post a screenshot of the output please?

---

### Post by Happy_Man on 2008-06-15
Just so we're clear, it's "lspci" not "1spci"

```
lspci
```

Were you entering that?

---

### Post by retardoposer on 2008-06-15
Sorry got the letters wrong

---

### Post by retardoposer on 2008-06-15
ok i got it

here it is

[http://i33.photobucket.com/albums/d60/retardoposer/Screenshot.png](http://i33.photobucket.com/albums/d60/retardoposer/Screenshot.png)

---

### Post by shifty_powers on 2008-06-15
aha, a broadcom. they are known for being a pain in the ***, well at least some models..

incidentally, what is the ouput of

```
sudo iwlist scan
```

in the terminal?

---

### Post by waspbr on 2008-06-15
sounds like a job for our hero, ndsiwrapper!!!!!!!!!

---

### Post by shifty_powers on 2008-06-15
try

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

or otherwise you might want to think about getting a cheap usb dongle. the broadcom chipsets are known for being awkward..

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

says it all ;)

edit: and what exactly did you do with ndiswrapper?

---

### Post by retardoposer on 2008-06-15
okie dokes

---

### Post by shifty_powers on 2008-06-15
have you tried the bwcutter thingimajig? (lovely technical term that ;))

---

### Post by retardoposer on 2008-06-15
o        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


Out put

---

