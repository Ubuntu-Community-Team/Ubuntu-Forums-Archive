---
title: "[SOLVED] Wireless Internet not working?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Pioneer5000 on 2008-05-26
Internet not working. Im using Dell Inspiron 1501 it was working with 7.04. To get everything setup i just went into prefences --> restricted drivers and then just had to update driver and then got it working. But this is bs that doesnt work in 8.04 the driver doesnt even show up for upgrading. And its so anoying why can Windows do this automatically just pick up the wireless connection so i can connect but Ubuntu cant?

Please help! Thanks.

---

### Post by dRock1286 on 2008-05-26
Ubuntu can't because it has to use a proprietary driver.  Windows has no problem doing this because Windows is based on the idea of proprietary software.  Do you remember what the driver was that you were using before?  You can always search for that and try to install it again...

---

### Post by superprash2003 on 2008-05-26
incase its a broadcom.. you can try this.. [http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html) .. some steps require internet access.. so try connectin your laptop to the internet via LAN and then installing drivers

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

.........or go back to 7.04 until updates are out to correct the 8.04 issues.

:guitar:

---

### Post by Pioneer5000 on 2008-05-31
Ive managed to get it working but to do this you need to have connection to net so connect through Ethernet or USB just to do this. I got this from a post from another user on these forums:

```

sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter

```

After completing the above code in terminal, restart computer then click on connection icon in top right corner of screen and it should detect your wireless connection.

**Full credit to sam_delta**

---

### Post by thinking2loud on 2008-06-03
Cancel.

---

