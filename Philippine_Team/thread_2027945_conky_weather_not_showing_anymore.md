---
title: "conky weather not showing anymore"
date: 2012-07-17
forum: Philippine Team
---

### Post by killer_d76 on 2012-07-17
can anyone point me out to a free weather forecast?, yung sa accuweather free license eh di na gumagana for a long time ago, at yung weather information/image is not showing anymore, baka pede patulong naman ;), maraming salamat!

---

### Post by daxumaming on 2012-07-19
how about Wunderground? though I'm not sure how to configure it with conky widgets since I'm using a more minimalistic out-of-the-way indicator-weather.

---

### Post by killer_d76 on 2012-07-19
thanks Dax!, hhmmmm i am quite interested on this minimalistic out-of-the-way indicator-weather you are talking about :confused:, i wanted to be updated with the weather condition there in the Philippines since my family is living by the hills in Quezon City, if you could possibly point me out this weather indicator you are talking about, I would highly appreciate it! ;)

---

### Post by daxumaming on 2012-07-19
Below's a screenshot of my indicator-weather. Just install it from the repo but it'll only work if you're using Unity or Unity2D. I don't believe it works on non-unity desktop.

[IMG]http://i.imgur.com/VbmlX.png[/IMG]

---

### Post by killer_d76 on 2012-07-19
Thank you so much Dax.. it works!, I tried installing on my non-Unity Desktop (Gnome) through terminal using```
sudo apt-get install indicator-weather
``` and after the installation process, I tried running it through the terminal by simply typing ```
indicator-weather
``` and voila! here it is, I would perhaps change the location though ;) again thanks for the help Dax.. :KS :KS :KS

[IMG]http://a1.sphotos.ak.fbcdn.net/hphotos-ak-ash3/s720x720/582021_4349148492646_1508247268_n.jpg[/IMG]

---

### Post by Shadius on 2012-07-19
My suggestion is to check out the [Conky thread]("http://ubuntuforums.org/showthread.php?t=281865&page=2023") if you ever wanted to get the weather working in Conky. Whichever works for you. :)

---

### Post by killer_d76 on 2012-07-19
thanks for the reply Shadius, but enabling weather on conky these days is way over my head!, I mean, I used to have a free license from XOAP then all of a sudden it's not working anymore.. I tried searching for a nice free weather forecast but making it work on conky is too technical for me :(, but I would love to see the weather showing on my conky again! ;)

---

### Post by daxumaming on 2012-07-19
oh look. i was not aware that it'll work on gnome. yay!

---

### Post by 6wires on 2012-07-20
install:

[FONT=Courier New][COLOR=Red]sudo apt-get install indicator-weather[/COLOR][/FONT]

---

### Post by Sector11 on 2012-08-24
> **killer_d76 said:**
> thanks for the reply Shadius, but enabling weather on conky these days is way over my head!, I mean, I used to have a free license from XOAP then all of a sudden it's not working anymore.. I tried searching for a nice free weather forecast but making it work on conky is too technical for me :(, but I would love to see the weather showing on my conky again! ;)

If you are still looking...

[URL="http://crunchbanglinux.org/forums/topic/19235/conky-weather-scripts-using-accuweatherwundergroundnwsweathercom/"]
Conky weather scripts using Accuweather/WUnderground/NWS/Weather.com[/URL]
Easy to set up and samples you can grab and run - will need some tweaking.

[weather in conky (LUA scripts) - mrpeachy's v9000 LUA script]("http://crunchbanglinux.org/forums/topic/16100/weather-in-conky-lua-scripts/")
Again with samples ... and people are willing to help.  I'm one of them.

Some of my v9000 and Teo's weather samples
[[IMG]http://t.imgbox.com/absJdh47.jpg[/IMG]](http://imgbox.com/absJdh47)

---

