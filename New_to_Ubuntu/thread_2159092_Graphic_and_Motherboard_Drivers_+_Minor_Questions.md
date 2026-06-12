---
title: "Graphic and Motherboard Drivers + Minor Questions"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by HeroSoNoob on 2013-07-01
Greetings Community!

First, I would live to apologize if this was asked a million times, I am fairly new to Linux based OSs. I just switched to, and planning to fully switch to Ubuntu from Windows 8, I am wondering on how can I fully install my hardware drivers as the website does not offer drivers for Ubuntu/Linux.

OS: Ubuntu 13.04 AMD64

Graphics Card: Sapphire HD 7970 with Boost (DualX)
Motherboard: AsRock Z77 Extreme4


Another problem I am currently encountering is setting up a mouse speed (pointer speed/sensitivity). I have read some tutorials on how to do it, as well as read the documentation of xinput which lead me to a solution that I should change it using the terminal. I might need a little help here, my xinput is as follow:

```

:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer  Razer Abyssus                        id=9    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Arctosa                         id=11    [slave  pointer  (2)]


&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Razer Razer Arctosa                         id=10    [slave  keyboard (3)]

```

I have little idea on what to do with that information, should I set my Razer peripherals as Master since it is set in slave? How do I do that? I have tried using ```
 xinput --set-pointer "Razer Razer Abyssus"
``` but I am probably wrong.


I'm glad and excited to be here, thank you in advance!


Edit: Added OS Version

---

### Post by Mark Phelps on 2013-07-02
Basically, you do NOT install drivers on your own in Linux; you do that in MS Windows.  Ubuntu will scan your hardware and install the right drivers.  Once you're up and running, you can go to Additional Drivers and see if there is something there for the AMD video chipset -- but be advised, since that will be a Linux driver, it may not do anything with the "boost" option.

---

### Post by dannyboy79 on 2013-07-02
not sure why the previous poster states that you do NOT install drivers in linux cause there are times that you do, although in linux they are referred to as modules and it's called "loading" them versus installing them but I digress. The most common hardware out on the market today has the modules (drivers) built into the kernel OR based on your hardware they get auto-loaded BUT there are times when you can get better performace from installing a propreitary module versus using an open source module (driver) 

Perfect example is in fact the graphics modules (drivers). What graphics driver is currently loaded? Can you report back what entering this command into a terminal window returns please?
```
lshw -class display
```

I can't help with mouse sensitivity but have you looked within system settings?

---

