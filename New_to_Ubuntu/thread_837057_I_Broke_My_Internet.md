---
title: "I Broke My Internet"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by krlhc8 on 2008-06-22
I was tinkering around and installed a newer dhcp package, which completely messed up my internet on my laptop.  Network Manager shows the SSIDs, and tries to connect, but never eventually establishes a connection.  In trying to fix the situation, I tried uninstalling Network Manager only to reinstall a new package that I downloaded from another computer and failed to figure out how to install that with Synaptic.  I am super frustrated.  Please help me; I so ronery without my internet.:cry:

---

### Post by ad_267 on 2008-06-22
I'm not sure if this is what you're asking exactly but if you have a .deb package you can just double click on it do open with the debian package installer and install it.

You can also use "dpkg install packagename.deb"

---

### Post by krlhc8 on 2008-06-22
What do I do if the Ubuntu repositories site contains a bunch of archives of precompiled source where Network Manager won't compile.  So there's a .deb version somewhere then?

---

### Post by ad_267 on 2008-06-22
If you can't get network manager from the repositories you can download it from packages.ubuntu.com. Eg [http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager)

---

### Post by krlhc8 on 2008-06-23
What I want to do is completely reinstall all packages relating to my wireless internet connection.  How am I supposed to know all of the packages that compose the wireless/internet system?  Is the command apt-get apt-build what I'm looking for?  Yet I just want to download the packages on a windows laptop and transfer/install them on my ubuntu laptop, so I'm not sure what to do now.

---

### Post by krlhc8 on 2008-06-25
Bump, set, spike...

---

### Post by dwhitney67 on 2008-06-25
In 30 minutes you could do a complete re-install.  I know it sounds drastic, but I bet using alternate methods you will probably spend more time trying to get the networking stuff functioning again.

If as a noob, you want to live on the edge and experiment with adding/deleting packages without fully understanding the repercussions, then get used to having to rebuild.

P.S.  If you decide to follow my advice, make sure you set up partitioning schema such that you have a dedicated partition set aside for /home.  That way, in the future, if you have to rebuild, your /home partition with user account(s) and data can be preserved.

---

