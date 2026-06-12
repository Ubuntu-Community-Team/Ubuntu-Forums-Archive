---
title: "[wlan1 txpower off ] turns wlan0 off why ?"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by PADDYKCSDC on 2012-05-08
Hello I'm a newbie to Ubuntu but have learned alot in 3 days. Anyway to start with I am running 3.2.0-24-generic alongside windows (ahh i need to delete it)on a small compact Q laptop. I am having problems with my wireless ...basically what i want to do is turn my internal wireless card off...I have an external alfa awus036h and i have the correct drivers installed all good ,now i want to disable the internal antenna i have tried BIOSes but my internal card is disabled on boot up ?...and there was no option to disable it all together. Also if I try using the kill switch (i.e the button to turn wireless off) that switches off both my internal wireless card and my external alfa.....my alfi is wlan0 and my internal is wlan1.....so i run this code in terminal.....
sudo iwconfig wlan1 txpower off   after that i run iwconfig to check and the terminal says tx-power is off for the internal adapter and on (27dbm) for the external adapter but as soon as i run the sudo iwconfig wlan1 txpower off i can see the green light go out on my alfa ? 
I am only turning my internal card off why does my external card turn off ?
Terminal says it has Tx-power=27 dbm how can it be off ?
Plus when i ran the alfa on windows the led was alot brighter is it not getting enough power ?

ALSO AIRCRACK IS REFUSING TO UNZIP FROM TERMINAL OR GUI ?
it is saying it doesnt look like a zip file when i downloaded it from aircracj-ng ????
should i start a new thread for this question ?

---

### Post by cariboo on 2012-05-09
I'm not sure about your internal wireless device, but if it is turned off in the bios, what else do you need.

As far as aircrack_ng is concerned, it isn't in the repositories any more, so we don't support it here. For support, check the [BackTrack forums]("http://www.backtrack-linux.org/forums/forum.php")

---

### Post by PADDYKCSDC on 2012-05-09
There is no option in BIOS to disable it permanantly there is an option to disable it at boot time but that does nothing for me because it is still running --- i have also ran rfkill list and killed the cirrect device but that to kills both adapters i have tried everything now it just keeps turning both devices off (even though i inly specify my internal adapter) 
SO FAR I HAVE TRIED
rfkill 
Hardware switch
BIOSes
And sudo wlan1 down

Any suggestions please ?

---

### Post by westie457 on 2012-05-09
Hi

As far as I know when using a wireless dongle that is **not** a USB modem the onboard wireless chip must be turned on whether the drivers for it are installed or not.

As an example my laptop has the infamous b43xx chip built in and my USB dongle has a Ralink chipset. I can connect with both at the same time (not sure which has control). If I remove the B43 drivers and leave the chip powered on the dongle remains connected however move the switch to the off position network access is lost.

In conclusion whether you use the on board wireless or just the USB dongle the ON-board wireless chip must have power running through it regardless.

Hope this is not too confusing.

---

