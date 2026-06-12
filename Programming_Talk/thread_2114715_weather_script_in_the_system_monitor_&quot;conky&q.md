---
title: "weather script in the system monitor &quot;conky&quot;"
date: 2013-02-10
forum: Programming Talk
---

### Post by majorburt on 2013-02-10
i'm looking for a script that will work in place of the weather script for "conky". the database it uses fro the weather doesn't contain a NOAA station anywhere near me and , as such, i don't have accurate weather
the script is this
```
${weather http://weather.noaa.gov/pub/data/observations/metar/stations/ LQBK temperature temperature 30} °F${font}
```

i'm looking for a database that will work in place of the current site that contains NOAA or otherwise weather stations for west Virginia

---

### Post by Habitual on 2013-02-11
I still use conkyForecast from c-l, like [so...]("http://www.bournetoraiseshell.com/article.php/20101101123337204")
I do NOT use, or code conky anymore, but this script came from an extensive conky setup I had way back when...

Check out [http://xoap.weather.com/search/search?where=West%20Virginia](http://xoap.weather.com/search/search?where=West%20Virginia)
I've heard that weather from this source doesn't work anymore and has been turned into a subscription-based source of weather. That said, I have an XOAP_KEY that I believe belongs to the Xfce desktop dev team that I have been using for over 200 days, and it rarely fails to pull my local weather data.

NOTE: That script came from [this desktop's massive conky layout]("http://i771.photobucket.com/albums/xx360/E522260/desktop_9_21_2010.png") weatherrc file, 
mostly contained the the c-li script I still use.

YMMV.

HTH.

---

### Post by majorburt on 2013-02-11
> **Habitual said:**
> I still use conkyForecast from c-l, like [so...]("http://www.bournetoraiseshell.com/article.php/20101101123337204")
I do NOT use, or code conky anymore, but this script came from an extensive conky setup I had way back when...

Check out [http://xoap.weather.com/search/search?where=West%20Virginia](http://xoap.weather.com/search/search?where=West%20Virginia)
I've heard that weather from this source doesn't work anymore and has been turned into a subscription-based source of weather. That said, I have an XOAP_KEY that I believe belongs to the Xfce desktop dev team that I have been using for over 200 days, and it rarely fails to pull my local weather data.

NOTE: That script came from [this desktop's massive conky layout]("http://i771.photobucket.com/albums/xx360/E522260/desktop_9_21_2010.png") weatherrc file, 
mostly contained the the c-li script I still use.

YMMV.

HTH.

will this work with "Conky-Lua"? [here.]("http://www.unixmen.com/configure-conky-lua-in-ubuntu-11-10-12-04-fedora-debian-and-linuxmint-howto-conky/")


also, how do i add the code to conky?

---

### Post by Habitual on 2013-02-11
> **Habitual said:**
> I do NOT use, or code conky...

slow down.

I'd start with installing conkyforecast IF there is a location "near you" at [http://xoap.weather.com/search/search?where=West%20Virginia?](http://xoap.weather.com/search/search?where=West%20Virginia?)

[http://www.google.com/search?q=conkyforecast+lua+site:ubuntuforums.org](http://www.google.com/search?q=conkyforecast+lua+site:ubuntuforums.org)

---

### Post by majorburt on 2013-02-12
> **Habitual said:**
> slow down.

I'd start with installing conkyforecast IF there is a location "near you" at [http://xoap.weather.com/search/search?where=West%20Virginia?](http://xoap.weather.com/search/search?where=West%20Virginia?)

[http://www.google.com/search?q=conkyforecast+lua+site:ubuntuforums.org](http://www.google.com/search?q=conkyforecast+lua+site:ubuntuforums.org)

"slow down" lol!

there's a location a few miles up the road from me so that's not an issue. 


also, just for the sake of showing off, here's a screenshot of conky. lol!
[IMG]http://ubuntuforums.org/picture.php?albumid=2521&pictureid=8581[/IMG]

---

### Post by Habitual on 2013-02-12
Great. Output!

Yes, the conkyforecast can be utilized in a conky weather rc file.

---

### Post by majorburt on 2013-02-12
> **Habitual said:**
> Great. Output!

Yes, the conkyforecast can be utilized in a conky weather rc file.

is conkyforcast a separate file that i would add to the conky folder in "home"? 
or is it something i would add to the ".conkyrc" file?

---

### Post by Habitual on 2013-02-13
> **majorburt said:**
> is conkyforcast a separate file that i would add to the conky folder in "home"? 
or is it something i would add to the ".conkyrc" file?

```
sudo apt-cache search conkyforecast
``` You install it.
Configure ~/.conkyForecast.config with your copy of an XOAP_LICENCE_KEY details and run conkyforecast from within your conkyrc file

[http://ubuntuforums.org/showthread.php?p=7773912](http://ubuntuforums.org/showthread.php?p=7773912)
376 pages of conky weather instruction.

[http://ubuntuforums.org/showthread.php?p=10790614](http://ubuntuforums.org/showthread.php?p=10790614)
This is the conky uber-thread. Live it. :)

Some of those instructions are available at [http://conky.pitstop.free.fr/wiki/index.php5?title=Main_Page](http://conky.pitstop.free.fr/wiki/index.php5?title=Main_Page)

Good Luck.

---

### Post by majorburt on 2013-02-13
> **Habitual said:**
> ```
sudo apt-cache search conkyforecast
``` You install it.
Configure ~/.conkyForecast.config with your copy of an XOAP_LICENCE_KEY details and run conkyforecast from within your conkyrc file

[http://ubuntuforums.org/showthread.php?p=7773912](http://ubuntuforums.org/showthread.php?p=7773912)
376 pages of conky weather instruction.

[http://ubuntuforums.org/showthread.php?p=10790614](http://ubuntuforums.org/showthread.php?p=10790614)
This is the conky uber-thread. Live it. :)

Some of those instructions are available at [http://conky.pitstop.free.fr/wiki/index.php5?title=Main_Page](http://conky.pitstop.free.fr/wiki/index.php5?title=Main_Page)

Good Luck.

you rock!!!

---

### Post by Habitual on 2013-02-13
ah shucks.

Thanks.:D

---

