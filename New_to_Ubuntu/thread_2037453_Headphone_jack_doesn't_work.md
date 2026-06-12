---
title: "Headphone jack doesn't work"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by mcimafonte on 2012-08-04
Hello, 

I am trying to install the headphone jack driver for Ubuntu 12.04 on my Dell Vostro V131. Thanks.

---

### Post by ubudog on 2012-08-06
Hi mcimafonte,

What happens when you plug in your headphones?  What model headphones are you using?

Check the "Output" tab of your sound settings when your headphones are plugged in.

Best of luck,
ubudog

---

### Post by NikTh on 2012-08-06
Hi , 
try to see if "automute" is enabled in alsamixer. 

Open a terminal (ctrl+alt+t) and write ```
alsamixer
``` 
Check out if automute is enabled. It must be.
 If it's not , then Enable it. 

Thanks

---

