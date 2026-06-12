---
title: "trying to run drivers for vid card"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by Tom_Everett on 2013-09-22
I downloaded the Nvidia linux driver for my GTX 650 ti, but it is a ".run" executable and my ubuntu doesn't know what to run it with. Can anyione help me?
I just downloaded ubunto and updated it so I have the latest and greatest

---

### Post by santosh83 on 2013-09-22
> **Tom_Everett said:**
> I downloaded the Nvidia linux driver for my GTX 650 ti, but it is a ".run" executable and my ubuntu doesn't know what to run it with. Can anyione help me?
I just downloaded ubunto and updated it so I have the latest and greatest

Hi, the drivers for your card should be available in the Ubuntu repositories provided you have enabled restricted as well. Start with the documentation here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

The installation process should normally identify the common Nvidia cards and install the open source Noveau drivers for it. Later on, if the open source drivers don't work as you expect you can try installing the proprietary ones provided by Nvidia under the 'nvidia-*' names. The system *should* have automatically installed the appropriate noveau driver. Are you experiencing any issues?

---

### Post by Tom_Everett on 2013-09-22
No, I'm just  used to windows that  only installs the bare minimum. I wanted to be sure I get all I can out of the card. Sounds like Ubuntu has that covered. Thanks for your help

---

