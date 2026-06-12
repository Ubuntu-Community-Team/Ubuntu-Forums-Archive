---
title: "[SOLVED] help with wireless"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Ryuuga on 2008-07-04
hey guys,
I'm totally 150% new to this OS and i though i find it alot more complicated to use than Windows, i feel its for the better.
Thing is, i just installed ubuntu yesterday and was happy I got it running in less than half an hour. However, i could not connect wirelessly to my router(NETGEAR) with my wireless adapter/dongle (belkin F5D7050)
i googled it up and found some solutions, one of them being compat_wireless. Then, i had to google some more to find out how to install the tarball... ok as i said, im totally noob to this.

After successfully installing it, i rebooted and the boot screen got stuck on bluetooth without the [OK] at the end. Frustrated, i rebooted it again and to no surprise, it failed to boot.

then I booted windows and make things worst, my wireless mouse(microsoft wireless intellimouse explorer 2.0) failed to work. Device manager reports the device working fine, but the cursor just doesnt move at all.

i then completely uninstalled ubuntu and reinstalled the mouse driver, but still it fails me.

So having understood my situation, my questions are:
1) how can i get the belkin wireless adapter to connect to my router
2) did installing compat_wireless probably have caused the bluetooth failure and soon after, the wireless mouse?

thanks for your replies, i would really like to have ubuntu up and running smoothly ^^

EDIT: i just realized i installed ubuntu INSIDE windows. perhaps thats the reason why failure of bluetooth in ubuntu affected windows as well??

---

### Post by ZabiGG on 2008-07-04
Hi, 

1) You should probably not attempt to install from source until you have a better grasp of how ubuntu/linux works.

There's lots of great starter info if you click on the "Look here" link in my signature below.

2) There's a clear and descriptive howto [here]("http://ubuntuforums.org/showthread.php?t=571188") to set up wireless. I recommend that you read the entire guide and following posts first, to see what issues you might run into when setting it up, and then start following it.

Not sure about the install inside Windows (my first Ubuntu install was a dual-boot), that might affect how the drivers are handled. Do a quick search like "wubi driver" on the forum. You might pick up great info from people who are experiencing the same problems.


Hope this helps,

Z.

---

### Post by Ryuuga on 2008-07-06
thanks for the reply~!! your links definitely helped alot ^^

i have solved my problem and can now go online wirelessly on ubuntu
few things i did:

1) i uninstalled the ubuntu inside windows and did a full installation on my external drive.
2) then, i googled for more help and came up with this link which gave me a step by step instructions for a complete linux noob like myself:
[http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/]("http://ankurs.com/2008/04/installing-ndiswrapper-on-ubuntu-804/")

3) however, please make sure the .inf AND .sys file is in the same folder
4) when you're done, just reboot and voila! wireless internet access with belkin F5D7050 ^^

the wireless mouse is still not working, i think... but no matter, i'll just use a wired one, too happy i finally got ubuntu online and running yay~
thanks for the help zabi GG ^^

---

### Post by ZabiGG on 2008-07-06
My pleasure ;)

About your mouse: is it USB or Bluetooth? And what brand is it?

---

### Post by Ryuuga on 2008-07-10
its uhm, Microsoft Wireless Intellimouse Explorer 2.0 
lol pretty damn long name xD

---

