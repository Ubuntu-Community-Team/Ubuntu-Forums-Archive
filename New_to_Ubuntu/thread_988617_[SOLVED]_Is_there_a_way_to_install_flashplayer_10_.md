---
title: "[SOLVED] Is there a way to install flashplayer 10 on Gutsy?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by orwellus on 2008-11-20
Hello:

Well, I tried both Hardy and 8.10. I have to say I was a bit underwhelmed. Hardy seems to have all kinds of problems. 8.10, for some reason, removed most of synaptic. Plus both systems insist on putting little locks on files every time I try to transfer some old files from a cd on to my desktop. So, I'm back with Gutsy. 

One thing, I miss though from my Hardy days, is having Adobe Flash player 10. Is there a way to install Flash player 10 in Gutsy?

---

### Post by PriceChild on 2008-11-20
You can download it from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

You can install from the tar.gz (there are instructions inside)

I also 'believe' that the deb "for ubuntu 8.04" will work with gutsy... "but you shouldn't use packages for gutsy on hardy".

---

### Post by hyper_ch on 2008-11-20
and adobe provides even 64bit flash now :)

---

### Post by aysiu on 2008-11-20
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar -xvzf install_flash_player_10_linux.tar.gz
cd install_flash_player_10_linux/
sudo ./flashplayer-installer
```

---

### Post by orwellus on 2008-11-20
Thanks for the replies. I tried your method aysiu, everything is fine until the final step. When I try sudo ./flashplayer-installer, I get a message that says please enter your installation path Mozilla, Netscape, Opera. I tried Mozilla, but it gives me an error message. Then I tried /usr/lib/mozilla/plugins but I get a message that says WARNING: Please enter a valid installation path. Any suggestions?

---

### Post by aysiu on 2008-11-20
Maybe try /usr/lib/firefox

---

### Post by handydan918 on 2008-11-20
> **hyper_ch said:**
> and adobe provides even 64bit flash now :)

Yes, but you can only use it on Linux!


OMG, how long have I waited to say that!


:popcorn::guitar:

---

### Post by Keen101 on 2008-11-20
```
sudo apt-get install flashplugin-nonfree
```


if you still want to try using the .tar.gz method, i think the correct path is /usr/lib/firefox-3.0.1

---

### Post by orwellus on 2008-11-20
/usr/lib/firefox 

worked as a valid path.

Went to youtube, everything seems okay.

Thanks, aysiu.

---

