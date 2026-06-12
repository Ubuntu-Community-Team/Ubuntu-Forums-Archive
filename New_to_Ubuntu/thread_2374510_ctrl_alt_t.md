---
title: "ctrl alt t"
date: 2017-10-16
forum: New to Ubuntu
---

### Post by jhip626 on 2017-10-16
when i first installed lubuntu the ctrl + alt +t would open a terminal window, now all of a sudden it doesnt.... how do i go about re-enabling that?


thanks

and yes i tried to google it, but what was suggested didnt work.

---

### Post by vasa1 on 2017-10-16
Please post the output of```
grep -i terminal $HOME/.config/openbox/lubuntu-rc.xml
```and```
grep -i -A4 'keybind key="C-A-T"' $HOME/.config/openbox/lubuntu-rc.xml
```

Also, please run```
openbox --reconfigure
```from a terminal and tell us what you see.

And, instead of>  and yes i tried to google it, but what was suggested didnt work. it would be more useful if you posted what you tried so that people trying to help you don't make the same suggestion.

---

### Post by HermanAB on 2017-10-17
Install autokey, you won't be sorry!

---

### Post by jhip626 on 2017-10-17
> **vasa1 said:**
> 

Also, please run```
openbox --reconfigure
```from a terminal and tell us what you see.

And, instead ofit would be more useful if you posted what you tried so that people trying to help you don't make the same suggestion.

NOTED. thank you

I ended up reinstalling lubuntu for the 3rd time because there was just too many odd things I couldn't figure out how to fix.

the ctrl alt t. the grey line when I installed CAIRO taskbar. couldn't figure out how to get the default taskbar back..etc.

---

