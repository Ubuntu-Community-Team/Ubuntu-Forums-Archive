---
title: "touchpad not working:-("
date: 2012-09-19
forum: New to Ubuntu
---

### Post by kened112 on 2012-09-19
Hi! 

Could you please me as well..I have the same problem..i have tried to use the code u offered but it doesn't work for me.  So in terminal I got following output..could u help pls..pls. Thanks
 
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SIGMACH1P U+P Mouse                         id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=13    [slave  keyboard (3)]

---

### Post by newb85 on 2012-09-19
Please describe your problem and what you've tried in better detail.

---

### Post by kened112 on 2012-09-19
Hi, i have recently updated to ubuntu 12.04 and suddenly noticed touchpad not working at all..can only access with external mouse which is kind of disturbing me. been reading alot for solution but nothing is changing so far. my last attempt was putting this code in the terminal:  
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true 

pls help

---

### Post by newb85 on 2012-09-19
Try these:

```
sudo apt-get install xserver-xorg-input-synaptics
sudo dpkg-reconfigure xserver-xorg-input-synaptics
```

---

### Post by cortman on 2012-09-19
After running newb85's commands, try

```
synclient TouchPadOff=0
```

---

### Post by ericsonlouis on 2012-09-19
You are sure you just do not have touch pad disabled with the fn ?

---

