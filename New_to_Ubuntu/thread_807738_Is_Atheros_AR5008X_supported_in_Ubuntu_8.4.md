---
title: "Is Atheros AR5008X supported in Ubuntu 8.4"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Dax0n on 2008-05-26
hey :D I really want to switch from Vista to Ubuntu but as i need it for school, i'll need to have my wireless card working. I own a Atheros AR5008X, but does anyone know if it is supported in Ubutnu 8.4?

I've installed 8.4 some time ago (deleted it again as wireless didn't work) but i couldn't find any wireless networks, even though i was sitting next to my wireless AP.

If you know a way to get AR5008 to work, i would greatly appreciate if you would post a dummy proof guide :D

Thanks in advance.

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

---

### Post by teaker1s on 2008-05-26
madwifi should support it but the driver you need is
[http://svn.madwifi.org/madwifi/trunk/]("http://svn.madwifi.org/madwifi/trunk/")
[http://ubuntuforums.org/archive/index.php/t-596310.html]("http://ubuntuforums.org/archive/index.php/t-596310.html")

---

