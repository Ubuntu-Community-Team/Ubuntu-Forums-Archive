---
title: "My-Weather-Indicator suddenly broke?"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by d4m1r on 2013-04-04
Hey guys, today I logged into my Ubuntu desktop and realized my-weather-indicator icon was not appearing on my top menu. I checked my processes and sure enough, it was not running. I launched it manually (normally is started automatically upon login) and I can see the process for a second, and then it disappears. I guess it is crashing? It is weird because I haven't updated anything on this machine for at least a week and my-weather-indicator has otherwise been running on it fine for months. I can't think of ways to troubleshoot this further even...

I am connected to the internet and I have tried reinstalling it, to no avail :(

---

### Post by Theeboon on 2013-04-11
I have the same thing, can't get it to start.

---

### Post by Frogs Hair on 2013-04-11
Mine was also not working, but started manually from dash. Try changing the weather service in preferences as an experiment.

---

### Post by BrunoLotse on 2013-04-11
Just for a thought...
I am using this GNOME extention
[https://extensions.gnome.org/extension/613/weather/](https://extensions.gnome.org/extension/613/weather/)
Works like a charm:)
Cheers,
Bruno

---

### Post by d4m1r on 2013-04-11
> **Frogs Hair said:**
> Mine was also not working, but started manually from dash. Try changing the weather service in preferences as an experiment.

I can't even get to the preferences...The whole thing starts up for a split second (I see the process) and then crashes. I have NOT updated my Ubuntu of the app itself and last month it was working fine which is the weird part of this...What broke it and how can I fix it? :confused:

@Bruno, thanks but I don't want to switch to something else.

---

### Post by RedAceBe on 2013-04-11
Using Yahoo as weather service causes the program to crash apparently.
The solution is pretty simple: delete the configuration file in *~./config/my-weather-indicator*
and restart the program. You should be able to select another weather service than Yahoo
and then everything should work as before, see [https://bugs.launchpad.net/my-weather-indicator/+bug/1135921](https://bugs.launchpad.net/my-weather-indicator/+bug/1135921)

---

### Post by d4m1r on 2013-04-12
That did indeed fix my problem...Very strange but thanks for the link!

---

### Post by arpanaut on 2013-04-12
Fixed me up too!
Thanks

---

### Post by kyfho23 on 2013-04-20
Yahoo discontinued or premimumized their weather API, I believe. 

My best suggestion is to go to WeatherUnderground.com, and get a free account. Then, at the bottom of every pafe in the "fine print", look for the "developer" section. Click that & follow the instructions for generating an API key. (It's the number in the drop down box, NOT the number farther down the page.)

Once you have that, go to preference/weather services and type (for some reason Weather Underground won't let you copy & paste) type that number into MWI's box for Weather Underground. Click activate-and be a little patient, it seems to take up to a minute. You'll know it's ready when the round check box is "live" & lets you tick it.

I've had few problems with this combination, and the WU service is hyper local.

---

### Post by Baldrick_NZ on 2013-04-21
You can also get a fairly pain-free freeAPI by signing up with World Weather Online, too. [www.worldweatheronline.com](www.worldweatheronline.com)

---

### Post by d4m1r on 2013-04-21
I just switched it to use OpenWeatherMap and while it is not as accurate as the Yahoo one used to be, it gets the job done.

---

