---
title: "Where does the gnome calender get its weather data ?"
date: 2008-11-28
forum: Programming Talk
---

### Post by prepstyles on 2008-11-28
Does anyone know which feed the current gnome calendar pulls its weather data from?

I'd like to have an accurate weather feed to use in my own apps.

I've looked around a little but can't find anything.

Anyone know were the gnome app pulls this from? 

If not were might I look to find out ?

Thanks.

---

### Post by slavik on 2008-11-28
my guess is weather.com

---

### Post by mdebusk on 2008-11-29
> **prepstyles said:**
> I'd like to have an accurate weather feed to use in my own apps.

I think they pull from weather.com. [Here's how to get their XML feed]("http://www.weather.com/services/xmloap.html"). You have to sign up.

The National Weather Service has some feeds, both XML and RSS. [Here's the source for current conditions]("http://www.weather.gov/xml/current_obs/").

You could [consider Yahoo! Weather]("http://developer.yahoo.com/weather/").

[Weather Underground has an API]("http://wiki.wunderground.com/index.php/API_-_XML") you can use.

You might also check the package [weather-util]("http://fungi.yuggoth.org/weather/") in the repos. It uses data from NOAA/NWS and is written in Python. It might be easy to simply pipe output from it to your apps rather than re-inventing the wheel.

---

