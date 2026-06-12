---
title: "Ubuntu black screen with x cursor"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by lucacilevinandrei on 2014-03-15
Last night i was installing my printer drivers and i downloaded a driver app and that driver app i think installed a video card driver and now i get a black screen. The laptop has an on board intel video card and a nvidia video card. Any ideas how to remove the drivers the program installed?

---

### Post by lucacilevinandrei on 2014-03-15
So i found on the internet sudo apt-get remove --purge nvidia-* and now i what to know how to i instal the proper invidia driver so i dont get into this problem again.

---

### Post by squakie on 2014-03-15
Look in additional drivers amd see if it shows any video driver in use or available for use.

---

### Post by ajgreeny on 2014-03-15
Is this an optimus hybrid graphic setup?

Have a search for bumblebee optimus if so and see if that helps.
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Vladlenin5000 on 2014-03-15
One thing I really don't understand: Why on Earth a "printer's driver" would mess with the graphics driver?
Please tell us what printer are you trying to install and what have you downloaded.

---

