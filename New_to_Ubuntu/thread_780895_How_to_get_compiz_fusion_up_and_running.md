---
title: "How to get compiz fusion up and running"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by AeThEr777 on 2008-05-03
Hey i was juts wondering if anyone could outline the steps to get compiz fusion up and running! 

AeThEr777

---

### Post by sam_delta on 2008-05-03
are you using ubuntu 8.04? which graphic card?

if everything is working fine and you have the correct video drivers, you shouldbe able to activate it by going into system>preferences>appearence, then into the "visual effects" tab and select normal or extra

---

### Post by Sinkingships7 on 2008-05-03
> **AeThEr777 said:**
> Hey i was juts wondering if anyone could outline the steps to get compiz fusion up and running! 

AeThEr777

Compiz is installed and ready by defualt. Make sure your graphics drivers are installed and type this code into the terminal (or copy and paste):

```
sudo apt-get install compizconfig-settings-manager
```

Then go to System -> Preferences -> Advanced Desktop Effects Settings

Play around from there and come back and ask if you want a certain effect!

---

### Post by AeThEr777 on 2008-05-03
No im using gutsy gibbon so 7.10 i believe. Ummm i dont really know how to check what graphics card it is but im pretty sure its a 128 bit integrated ATI chipset.

---

### Post by Rocket2DMn on 2008-05-03
Can you please post the output of
```
lspci | grep VGA
```

---

### Post by sam_delta on 2008-05-03
alright then, lets see if you have the correct drivers installed and working properly for compiz

post the ouput of 
```
lspci | grep direct
```

sam

---

### Post by AeThEr777 on 2008-05-03
this is the output of that cmd:

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

---

### Post by Rocket2DMn on 2008-05-03
Try running
```
compiz --replace
```
If it tells you it is aborting because you are using the open source driver, follow this workaround: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by Serpentinsek on 2008-05-03
> **AeThEr777 said:**
> No im using gutsy gibbon so 7.10 i believe. Ummm i dont really know how to check what graphics card it is but im pretty sure its a 128 bit integrated ATI chipset.
Please post contents of your /etc/X11/xorg.conf file via [http://pastebin.com/](http://pastebin.com/) and paste the link over here

---

