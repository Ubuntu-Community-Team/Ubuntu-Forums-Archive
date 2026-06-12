---
title: "Wireless Internet (Atheros AR5007EG)"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-05-26
I have been trying to get online wirelessly with my Ubuntu laptop that uses an Atheros AR5007EG wireless thing-a-majig. However, I have encountered problems whilst trying to do this.

The first thing I tried was to attempt connecting wirelessly in the LiveCD environment--this didn't work; I just got a window saying 'Wired Connection: roaming mode enabled' and 'Point to point connection: this network interface is not configured', with no mention of wireless in the slightest.

I then found [this thread]("http://ubuntuforums.org/showthread.php?t=800686"), but that doesn't work either--the first command **sudo apt-get install build-essential** doesn't work. I get a message about there not being a package named 'build-essential'; I think it banks on you having some form of Internet connection on the Ubuntu system already (I am currently posting this on a different computer running Windows XP).

Could anybody tell me what to do?

---

### Post by AndrewTheArt on 2008-05-26
You probably just need to add your install CD as a installation source  so that you can grab packages off of it.

Look here - 

[http://www.monkeyblog.org/ubuntu/installing/#add_cd](http://www.monkeyblog.org/ubuntu/installing/#add_cd)

> Open Synaptic and select an option in its menubar: Settings &#8594; Repositories. There's a button labeled *Add CDrom*; press this, insert your install CD and it will be added to the repositories. You can now install software through Synaptic without being connected to the Internet, provided the install CD is inserted. Note that the install CD has software solely from the main repository, not Universe, Multiverse or Restricted!

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

:guitar:

---

### Post by Jaded Misanthrope on 2008-05-26
About the Linux Emporium items;

If I buy the Edimax 54 Mbps Wireless USB stick with Antenna, can I just plug that into my laptop as is and get online wirelessly without screwing about with the wireless card I have at the moment?

---

### Post by crazdawgs90 on 2008-05-26
I have a PRO/Wireless 2915ABG card. I had a problem with Windows not even recognizing my wireless card. When I went through Ubuntu, however, it did. They way I checked to see if it was working was System->Administration->Hardware Testing. That showed me that my wireless card was working. Next, I went to System->Administration->Network. That shows you the different forms of connections. For me, I have to unlock the program by using the administrator password, then select wireless and click the properties button. It allows you to select roaming mode or type in manually your IP Address and Access point. I don't have experience with your type of wireless card, but that is what I did, and mine is working now so I hope this helps.

The answer is here: [http://richott.com/?p=12](http://richott.com/?p=12)

---

### Post by phidia on 2008-05-31
> **mapes12 said:**
> Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

:guitar:

Thanks for the link on the replacement card. I have this atheros card in my laptop and although I have an external drive install of 7.10 64bit that does work-I don't do any updates on that though-I couldn't keep it working on my internal HD install. It had been working but after an update I lost connection (the card still sees the connection) I can't get it to work now so I think the ar5007eg is not worth the aggravation. I will definitely give the card you recommended a look. Thanks

---

### Post by shifty_powers on 2008-05-31
given that you have an atheros based card, have you tried madwifi?

[http://madwifi.org/](http://madwifi.org/)

---

### Post by ugm6hr on 2008-05-31
> **phidia said:**
> Thanks for the link on the replacement card. I have this atheros card in my laptop and although I have an external drive install of 7.10 64bit that does work-I don't do any updates on that though-I couldn't keep it working on my internal HD install. It had been working but after an update I lost connection (the card still sees the connection) I can't get it to work now so I think the ar5007eg is not worth the aggravation. I will definitely give the card you recommended a look. Thanks

The Atheros 5007 is now supported by a patched madwifi in Hardy (32-bit), and will hopefully have full support soon.

There are plenty of How-Tos on this.

If you have a laptop with a mini-PCI wifi card (Atheros 5007), then a replacement mini-PCI card is probably a better idea.

Funnily enough, Atheros (and Intel) cards are best supported.

---

### Post by ugm6hr on 2008-05-31
> **Jaded Misanthrope said:**
> Could anybody tell me what to do?

Yes.

If you haven't already bought a new card - post back.

Easiest way is to use an ethernet cable and follow the How-to.

If that is totally out of the question, it can still be done, albeit with a bit of fiddling.

---

### Post by phidia on 2008-06-01
AFAIK there is no support by madwifi for the 64 bit atheros driver.
With a lot of trial and error I have gotten ndiswrapper to load the window's driver-sometimes the re-install of ndiswrapper and the driver are required.

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

