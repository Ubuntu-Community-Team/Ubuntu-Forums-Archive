---
title: "laptop wireless not working"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by boxercbuk on 2008-08-21
Hi guys please help have recently bought a fugitsu seimens laptop and the soft key (fn f1) to turn on my wireless card isnt working in hardy works fine in vista. I have searched the menus for a way to turn the card on but to no avail have also tried ifconfig and its not listed 

any help would be apreciated so I can get rid of the windows rubbish I am currently being forced to use on it 

cheers
steve

---

### Post by tuxxy on 2008-08-21
Did you read the wireless howto guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by boxercbuk on 2008-08-21
Thankyou tuxxy have just read the link you supplied and get stuck as the device is recognised and a restricted driver is installed to run it but it just wont turn on and its not listed in the network manager :confused:

---

### Post by Flyingjester on 2008-08-21
have you rebooted?




edit:fixed spelling error

---

### Post by pmsumner on 2008-08-21
Hi,

To get the wireless key working on these you will probably need to do 2 things, depending on the hardware you have.

1:- Download, compile and install the acerhk module
2:- Download, compile and install the new madwifi atheros drivers

This can all be done in a few easy steps and there are various guides out there to do it.

Before going too far, try typing in:
```
lspci | grep Wireless
```

And copy/paste the result here first off, to check we're talking about the right hardware.

---

### Post by rixtr66 on 2008-08-21
if your using atheros for a card you can also try ndisgtk ,its a tool to install windows wireless wrappers,i use an acer laptop with an atheros card
and i have no problems,i us the net5416 drivers.ndiswrapper can also be had in the add remove panel,if you have all programs selected,or you can apt-get ndisgtk,then run ndisgtk in the terminal.
i hope this helps.
Rick

---

