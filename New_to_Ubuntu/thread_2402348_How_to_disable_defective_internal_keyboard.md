---
title: "How to disable defective internal keyboard"
date: 2018-09-28
forum: New to Ubuntu
---

### Post by mingab on 2018-09-28
Hi. My 8-year old Dell Inspiron laptop's keyboard is already defective - ex. repeats typing 7's and b's on its own and disrupts whatever it is I'm doing. How do I disable this internal keyboard and enable instead a USB keyboard?

---

### Post by Holger_Gehrke on 2018-09-29
Plug the USB keyboard in. Both keyboards should now be working. In a terminal enter 'xinput --list'. The result should look somewhat like this:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```
With 'xinput --disable 12' (replace the '12' with the id of your defective keyboard) or 'xinput --disable "AT Translated Set 2 keyboard"' (replace the name with the name of your defective keyboard) you can make X disregard the defective device. To reactivate a disabled device use 'xinput --enable device-id-or-name'. Using the name is probably the better idea, the id might not stay the same from one boot to the next.

Holger

---

### Post by mingab on 2018-10-20
> **Holger_Gehrke said:**
> Plug the USB keyboard in. Both keyboards should now be working. In a terminal enter 'xinput --list'. The result should look somewhat like this:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```
With 'xinput --disable 12' (replace the '12' with the id of your defective keyboard) or 'xinput --disable "AT Translated Set 2 keyboard"' (replace the name with the name of your defective keyboard) you can make X disregard the defective device. To reactivate a disabled device use 'xinput --enable device-id-or-name'. Using the name is probably the better idea, the id might not stay the same from one boot to the next.

Holger
Thank you for the reply. I tried the above but the keyboard's still there. I mean, I wrote "xinput list" and the defective keyboard was still there with no change in its details.

I also tried "xinput float (id number)". It worked for that session but after rebooting, that keyboard was working again.

Is there another way to permanently disable the internal keyboard?

---

### Post by Holger_Gehrke on 2018-10-21
Just put that command in a script and make Ubuntu run it at the start of the session. How you do that depends on the flavour of Ubuntu you're using, on XUbuntu for example you have an applet in settings named "Session and Startup" which will do this.

Holger

---

