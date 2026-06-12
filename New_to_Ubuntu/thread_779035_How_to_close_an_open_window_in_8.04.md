---
title: "How to close an open window in 8.04"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by a.v.l on 2008-05-02
Since installing Ubuntu 8.04 I'm unable to close an opened window because the coloured band at the top of the windows where the minimise, maximise and close buttons live are all missing. How do I apply these please?

---

### Post by GavinZac on 2008-05-02
open a terminal and type "metacity --replace"

Does this bring them back?

---

### Post by a.v.l on 2008-05-02
Thanks for the reply but unfortunately when I tried using the terminal it opened up as a "white square" only, no writing or anything on it so I was unable to input your suggestion. I have found an answer to my problem for the moment by switching off "Visual effects" in System > "Appearance" and by doing this, the terminal returned as normal as did the minimis, maximise and close bar in my opened windows. Odd to say the least.:(




> **GavinZac said:**
> open a terminal and type "metacity --replace"

Does this bring them back?

---

### Post by GavinZac on 2008-05-02
> **a.v.l said:**
> Thanks for the reply but unfortunately when I tried using the terminal it opened up as a "white square" only, no writing or anything on it so I was unable to input your suggestion. I have found an answer to my problem for the moment by switching off "Visual effects" in System > "Appearance" and by doing this, the terminal returned as normal as did the minimis, maximise and close bar in my opened windows. Odd to say the least.:(

Well, the white square works the same as the normal terminal, you just cant see what you're typing. However, you did the right thing, turning off the visual effects is the result i wanted.

It sounds like your Compiz is breaking. Have you set up your video card?

---

### Post by Amarsingh0793 on 2008-05-02
I have this problem too. Everything worked fine in 7.10 but after a clean install, compiz does not work... Must be something to do with restricted drivers.

---

### Post by Oldsoldier2003 on 2008-05-02
if you have issues installing the restricted drivers using the restricted driver manager you can always try envyNG

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by rustutzman on 2008-05-02
Do you have Compiz runnng? If so look under effects and try enabling Window Decoration.

Russ

---

### Post by Amarsingh0793 on 2008-05-02
Unfortunately, EnvyNG did not work. I also checked compiz advanced settings manager and window decoration was already enabled. I am trying to reinstall compiz atm.

---

