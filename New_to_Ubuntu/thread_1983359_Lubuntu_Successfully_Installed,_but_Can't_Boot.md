---
title: "Lubuntu Successfully Installed, but Can't Boot"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by Andavane on 2012-05-20
Using the Startup Disc Creator I made a USB stick of Lubuntu 12.04 and installed it successfully on my EeePC 901 which has 2 tiny SSD hard drives: 4GB & 16GB. I put the root / on the 4GB and the /home on the 16GB. Everything installed fine, the screen flagged "Installation Successful Please Restart".

All I get is a black screen with a winking cursor, so I imagine it's the GRUB not working.

What shall I do next?

---

### Post by pfindan on 2012-05-20
Try booting into the live environment once again. Then run:

```
sudo update-grub
```

In terminal. Then try and boot like normal and see what happens.

---

### Post by Andavane on 2012-05-20
> **pfindan said:**
> Try booting into the live environment once again. Then run:

```
sudo update-grub
```

In terminal. Then try and boot like normal and see what happens.

In LXTerminal it says:

> lubuntu@lubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
lubuntu@lubuntu:~$ 


---

### Post by mijalis on 2012-09-18
> **Andavane said:**
> Using the Startup Disc Creator I made a USB stick of Lubuntu 12.04 and installed it successfully on my EeePC 901 which has 2 tiny SSD hard drives: 4GB & 16GB. I put the root / on the 4GB and the /home on the 16GB. Everything installed fine, the screen flagged "Installation Successful Please Restart".

All I get is a black screen with a winking cursor, so I imagine it's the GRUB not working.

What shall I do next?
I had exactly the same problem! Tried to install lubuntu 12.04 on an Asus eeepc 1000HE on a new SSD. The problem is that for some strange reason grub is installed on usb...
I think this might be the solution to your problem: [http://ourlife01.blogspot.gr/2012/09/step-by-step-installation-of-lubuntu-on.html](http://ourlife01.blogspot.gr/2012/09/step-by-step-installation-of-lubuntu-on.html)

---

### Post by NikTh on 2012-09-18
> **Andavane said:**
> Using the Startup Disc Creator I made a USB stick of Lubuntu 12.04 and installed it successfully on my EeePC 901 which has 2 tiny SSD hard drives: 4GB & 16GB. **I put the root / on the 4GB and the /home on the 16GB**. Everything installed fine, the screen flagged "Installation Successful Please Restart".
Good choice. 
> **Andavane said:**
> All I get is a black screen with a winking cursor, so I imagine it's the GRUB not working.

If grub was not installed correctly , then probably you would take a message like : "no operating system found"

But if you want to be sure , try boot-repair to repair and restore grub : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) , 2nd option from a live/usb. 

If nothing happens , then try this .
When you are in this black screen with blinking cursor , press Ctrl+Alt+F2 and try to login from there (username & password). 
Then give these 2 commands 
```
sudo service lightdm stop 
sudo service lightdm start
``` 

Thanks

---

### Post by YannBuntu on 2012-09-18
Hello
Please first indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL, so that we know your exact current situation.

---

