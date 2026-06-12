---
title: "behringer U-Control UCA222 ubuntu studio"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by nounderstandstudio on 2016-02-02
Hi all, 

it drive me nuts, the soundcard behringer U-Control UCA222 cannot be used for sound playback by Ubuntu Studio (Ubuntu Studio 15.10 Wily)... 
I cannot choose the usb sound card as hardware or output device. It´s really a bit annoying me, because it always had been a stuck to get this to work, every new installation of ubuntu studio and every 
time as the same issue as last installation which was nearly 2 years past where if forgot the solution. 
Yes, the card works using windows, also the headphone output from the laptop where studio is installed (thinkpad T60) works, but both sounds a old drunken trash can compared with full usage from the usb sound 
device under ubuntu.

the lsusb  within the terminal shows the USB-Card, also hwinfo --sound shows the loading of the driver had been done sucessful. 
So there is no unrecognized or unknown hardware there.... 

Has anyone an idea? 
Thanks and regards,

---

### Post by Vladlenin5000 on 2016-02-02
Hi and welcome.

No guarantees it'll work but it's worth trying: [http://jamie.lentin.co.uk/peripherals/behringer-uca-222/](http://jamie.lentin.co.uk/peripherals/behringer-uca-222/)

---

### Post by nounderstandstudio on 2016-02-04
Thanks a lot  for your quick reply,   now it works... but its a bit spooky because i am not sure what exactly cause the issue, may the most complicated issue- the user itself ;.)   

What i had done:  1) some research:   [https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices#Information_as_of_2014.2C_March_20](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices#Information_as_of_2014.2C_March_20)    

2) I changed the card index in /etc/modprobe.d/alsa-base.conf eg. like this options snd-usb-audio index=0    

3) today started ubuntu studio again, started audacity opend "edit" "Preferences", "Devices" and then had choosen as "playback device" the USB sound

turned on amplifier, started music and - drumroll - YES! Music  no longer  f...ng drunken cat which will play trasbin! Well, for all dean martin fans also good news: He sounds as he always was best in singing: a bit oily and drunken!

---

