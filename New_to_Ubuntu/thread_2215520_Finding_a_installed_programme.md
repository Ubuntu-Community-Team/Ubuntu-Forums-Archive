---
title: "Finding a installed programme"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by rohan-j on 2014-04-07
Please excuse me as i am new to Ubuntu.

I have installed a software package (Airvision2). Once installed where do I find the application execute the programme.
Tried looking under user\shared\applications but cannot find it there.
If I try to reinstall it says "Installed" and if I want to "Reinstall"

Please help

regards

---

### Post by sotiris2 on 2014-04-07
Which version of Ubuntu are you using? If its Ubuntu (with no letter before ,not Xubuntu/Lubuntu/Kubuntu) try pressing your windows key and search for airvision. Run it and an icon for it will appear on the sidebar. If you wish to you can right click on it to 'lock' it there.

---

### Post by rohan-j on 2014-04-07
I am using Ubuntu 13.04. I did as mentioned doing a search with the windows key. It will find the downloaded file but not the application. If I click on the downloaded file it states "Installed"

---

### Post by andrew.46 on 2014-04-07
Could you describe how you attempted to install this package and where you downloaded the archive from?

---

### Post by coldraven on 2014-04-07
To find out where the files were installed to, open a terminal and run```
dpkg -L airvision2
```
Also try typing airvision2 in a terminal and see if it works. If you get an icon in the launcher bar then lock it there as sotiris2 has mentioned.

---

### Post by rohan-j on 2014-04-07
Thanks to all who replied. Sorry my mistake. It is not a programme that is executable. Need to put the ip address in the browser. Works well now
Thanking everyone
Regards

---

