---
title: "dvbt+kaffeine + ubuntu 12.04lts"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by then_dude on 2013-06-12
Hello everybody,  i always got the same problem.   i have a dvbt card, and like to use kaffeine as software.   when i search for channels: it looks like it detects some cause the signal level meter goes up to 100% but no channel pops up on the list, and so no channel is saved.  i know it has to work, because the setup worked nice before (with 10.04lts).   i had saved and copied the old scanfile.dvb over the new: but no result  i'm running w_scan now  anybody some ideas ? thanks

---

### Post by tea for one on 2013-06-12
Good afternoon

Have you tried to scan using the scanning software that is bundled with Kaffeine?

First, ensure that your device is recognised and your source is enabled via:-

Digital TV > Television > Configure Television.

Then you can try the Kaffeine scanning software via:-

Digital TV > Television > Channels

Best wishes

---

### Post by then_dude on 2013-06-12
good afternoon

yes i have tried all of that, it seams like signals are picked up (in the signal strenght bar)
but none of them are displayed by name, and thus none of them are saved...

thanks

---

### Post by tea for one on 2013-06-13
I did not realise that you had already tried the built-in channel scanner withi Kaffeine. Regrettably, I can offer no more assisstance with this other than suggest that you try another application for your TV capture.

Do you have VLC installed because I came across a web page a while ago showing how to use VLC for DVB TV?

Here is the info:-

[http://catlingmindswipe.blogspot.co.uk/2012/11/how-to-watch-digital-tv-in-vlc-player.html](http://catlingmindswipe.blogspot.co.uk/2012/11/how-to-watch-digital-tv-in-vlc-player.html)

If this works then we can hopefully eliminate any hardware incompatibility.

I must admit that TV capture is not an easy topic to troubleshoot...........

---

### Post by then_dude on 2013-06-13
thanks, i'm gonna try that first and see what happens thanks again

---

### Post by then_dude on 2013-06-16
well vlc does not work either. 

i cannot find any frequencies when i scan with kaffeine, or w-scan , although i know there are. I haven't changed anything on the hardware setup and before the upgrade it worked perfectly. 

i have another pc at home, it has the same card in it. ASUS My Cinema P7131 Dual; i copied the sqlite.db and scanfile.dvb file to the new pc: the channels appear, but when i tune in , no program is showed... 

there are some things i have to install first to make shure it runs, the question is which ones?

thanks

---

### Post by tea for one on 2013-06-16
Good evening

If I understand correctly, you upgraded from 10.04 to 12.04 and now Kaffeine does not scan the channels?

I have always installed LTS versions from new and added Kaffeine after installation..................and, consequently, I find that Kaffeine and my DVB device function OK.

I suspect that the upgrade may have introduced some conflict.

As a suggestion, if you have a spare partition, install a virgin copy of Ubuntu 12.04, then add Kaffeine and see if the channel scanner functions correctly.

I realise that this is not an ideal suggestion, but nothing venture nothing gained.

Kind regards

---

### Post by then_dude on 2013-06-16
no i did a clean reinstall and i cannot find the channels anymore when i scan. 

I first did an upgrade and everything kept on working (also the channels...) but the pc was very slow after the update...

i always install the LTS versions, pitty that i had to give up the 10.04lts

---

### Post by howefield on 2013-06-16
Check the transmitter information in the scan file is correct.

---

### Post by then_dude on 2013-06-16
thanks, please elaborate a bit. 
what should it look like?

---

### Post by howefield on 2013-06-16
> **then_dude said:**
> what should it look like?

That depends on the transmitter :)

When I install kaffeine I need to update the information in the following file otherwise it won't find any channels, might be a long shot but you never know. 

```
.kde/share/apps/kaffeine/scanfile.dvb
```
.kde/share/apps/kaffeine/scanfile.dvb

---

### Post by then_dude on 2013-06-16
ok, i understand. 

well the two pc's are next to each other; 
and the transmitter frequencies are in the scanfile list
so that cannot be the problem (if this is what you are refering to)

thanks

---

### Post by then_dude on 2013-06-21
anybody got an idea ?  thanks

---

### Post by then_dude on 2013-06-23
i got it working,  but you will never believe how.   i had 12.04lts fresh installed, it could detect the card, but while scanning no channels were found.   i put in an extra old (very troublesome) usb dvb-t dongle and all of a sudden a window pops up to say that there are additional drivers to install.   i let it run the additional setup and all of a sudden my pci-dvb-t card works just fine....  how about that...  how can you ask ubuntu to go and download the extra drivers without jacking in an old usb dvb-t key?  (i know you can go to system settings > additional drivers... But that didn't find anything for the pci-dvbt- card, it only did when i put in the dvb-t usb dongle...

---

