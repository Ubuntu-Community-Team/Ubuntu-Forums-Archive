---
title: "Turning off laptop touchpad"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by darkliight on 2011-09-28
I didn't post this in my last thread because it was completely unrelated.

How can I disable the touchpad on my Dell Inspiron 1525? I am using an external USB mouse and have no use for the touchpad and it actually makes working a nightmare of accidental clicks and mouse drags.

Thanks for the help!

/*Also if this is in the wrong forum, I apologize.*/

---

### Post by in·ter·punct on 2011-09-28
You could install a small indicator that allows you to enable/disable the touchpad.

To install, run the following in the terminal:
```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

[https://launchpad.net/touchpad-indicator](https://launchpad.net/touchpad-indicator)

---

### Post by darkliight on 2011-09-29
Thanks! That has been driving me crazy.

---

