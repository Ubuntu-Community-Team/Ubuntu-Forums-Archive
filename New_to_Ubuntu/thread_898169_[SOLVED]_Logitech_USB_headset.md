---
title: "[SOLVED] Logitech USB headset"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by NewNerd99 on 2008-08-23
Hi guys,
       I have followed various threads in relation to this problem which have all led down different paths, none of which fixed my problem.

I have a Logitech USB headset. When plugged in the opening Ubuntu log in jingle plays through the laptop speakers not through the headset.
When playing a movie in VLC sound comes from the laptop not the headset.
When playing an MP3 in Amorok the music comes from the laptop not the headset.
When playing a movie in Movie Player the sound does come out of the headset.

I have a Compaq Presario F500 laptop running Hardy Heron 8.04 with all updates applied through universe and multiverse options and am currently searching for the command to list my soundcard. I am very new to using the terminal but am keen to expand my use of it.

Any help would be appreciated.

Cheers
Chris

---

### Post by NewNerd99 on 2008-09-12
Still not having any joy with the headset....

---

### Post by Bölvaður on 2008-09-12
I also have usb headset and was posting a question like 11 minutes ago, I figured that the program is listening to wrong device. so you need to look up in /dev/ if there is a dsp1 file before we take next step



*edit*

Because I dont know what you have done before I'll give you the most simple solution I know, GUI and everything :)
System -> Preference -> Sound

Change "Music and Movies" to USB Audio (that is if /dev/dsp1 is detected the same way as for me).
Well you can just for the test change all of the choices there to USB Audio.

---

### Post by Armaron on 2008-09-13
I got a logitech usb headset and I just plugged it in and changed the sound settings to usb device, but no sound is comming out of my headset.

Any help is welcome. :)

---

### Post by Bölvaður on 2008-09-13
I am not sure, but it might be useful to have it plugged in before the bootup. I think in kUbuntu I only got usb headset automaticly detected if I had it at startup.

Btw have you tried checking what audio devices and services are available to you? For me there are 2 USB devices but only one of them is the headphone, USB Audio (Alsa mixer)

---

### Post by Armaron on 2008-09-15
Yeah, connecting it on bootup is working for me, thanks!

---

### Post by billgoldberg on 2008-09-15
I have written on how I got my logitech usb headset to work on my blog.

It is actually pretty easy.

[http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/](http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/)

---

### Post by NewNerd99 on 2008-09-16
Thanks guys for your assistance, and thanks Bill for the weblog.
I now have the Logitech headset working in all media playing devices except VLC. 
I can therefore only assume that its something I have yet to discover in VLC somewhere.

Thanks again, very impressed with the level of help available in a FRIENDLY, laymans terms sort of way.

Chris

---

### Post by NewNerd99 on 2008-09-16
Its nice when its a basic fix ..... then again it does leave you with the 
'Why am I so stupid sometimes' question over your head!!

VLC:
Settings>Preference
tick advanced options on the Audio tab and change the drop down box to
'ALSA Audio Output' on the 'Output Modules' tab

case closed

Chris

---

### Post by HousieMousie2 on 2008-09-16
> **NewNerd99 said:**
> Thanks guys for your assistance, and thanks Bill for the weblog.
I now have the Logitech headset working in all media playing devices except VLC. 
I can therefore only assume that its something I have yet to discover in VLC somewhere.

Thanks again, very impressed with the level of help available in a FRIENDLY, laymans terms sort of way.

Chris

Hey Chris?  Would you please mark this thread as Solved? (Thread Tools/ Mark this thread as solved)  It will make it a little easier for the next person who has the same problem to find a working solution.

Thank you and glad you got it working correctly!

---

