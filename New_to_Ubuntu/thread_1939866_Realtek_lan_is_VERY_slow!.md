---
title: "Realtek lan is VERY slow!"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by Birdman2010 on 2012-03-12
My connection to the Internet is VERY slow. In addition, I keep getting messages from Mail.com and Google.com that state that I am no longer connected to the Internet.  I keep hitting Refresh and I eventually get the page that I want.

I have hit a lot of forums and I have determined that the default driver for "Realtek PCIe GBE Family Controller" is a bad one. Instead, the forums say, I should download and install the driver from Realtek.  I downloaded the driver and saved it to my Ubuntu desktop.  When I double-click on the autorun.sh file, it offers to Display, Run, or Run in Terminal.  When I run in a terminal, I see messages that say "Access Denied" and the new driver fails to install.

I am very new to Ubuntu.  I would like to use this operating system, but I can't seem to figure out this basic problem.  Would someone walk me through this process step-by-step?  I cannot use Ubuntu if I cannot use the Internet.

Thanks!

---

### Post by TeoBigusGeekus on 2012-03-12
Open a terminal, navigate to the location of your extracted folder, make the install script executable
```
chmod +x autorun.sh
```
and execute it as root
```
sudo ./autorun.sh
```

---

### Post by Birdman2010 on 2012-03-12
TeoBigusGeekus, thank you!  The Internet is much faster now!

---

### Post by TeoBigusGeekus on 2012-03-12
You're welcome my friend.

---

