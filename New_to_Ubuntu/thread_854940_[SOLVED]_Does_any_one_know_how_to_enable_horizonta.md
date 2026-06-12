---
title: "[SOLVED] Does any one know how to enable horizontal scrolling on synaptic touchpad?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by bhadotia on 2008-07-10
Here is the background:
I never knew that I could do horizontal scrolling using the horizontal edge of my touch-pad because it never worked (neither in windows nor in linux).
About a month back I did a fresh  install of my ubuntu (I am always reinstalling my OS:)) and as usual installed gsynaptic and set /etc/X11/xorg.conf accordingly . Surprisingly this time I could do horizontal scrolling.


Here is the problem:
After reinstalling my ubuntu this time:) , the horizontal scrolling is not working - Dunno why. 

What I have tried:
Coz it seemed like some configuration mistake that the horiz. scroll. was not working so I started exploring the xorg.conf file and found an option "HorizEdgeScroll" in there so I set it to one ("1")  in hope it would work- but that did not work.
I also tried to do some google search - did not work.
Ofcourse ,the horizontal scrolling is enabled in gsynaptics.

Any suggestions ?

Many thanks.

---

### Post by tjwoosta on 2008-07-10
do you have the synaptics touchpad driver installed?   (it will work without the driver but you wont be able to use the scrolling)

```
sudo apt-get install xserver-xorg-input-synaptics
```

then go to Preferences-Mouse and click the touchpad tab

Edit: also the reason it didnt work in windows is probably the same   (go to the synaptics website to download the windows driver)

---

### Post by bhadotia on 2008-07-10
Hi,thanks for the reply. 
Thank you very much for the idea:
I just checked my System>Preference>Mouse and the "Enable horizontal scrolling" was not enabled . Its working after enabling it.


Next time I will be more carefull checking my own settings before posting out here:(:)

Sorry for the unnecessary trouble and Thanks a lot:guitar:  

P.S. I did not know there was a synaptic driver:).

---

