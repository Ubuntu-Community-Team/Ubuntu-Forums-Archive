---
title: "Weather Indicator - meteo log"
date: 2012-10-07
forum: Programming Talk
---

### Post by iconmaroon on 2012-10-07
Hi all,

I'm wondering if it is possible for me to extract data from the Weather Report (weather indicator) applet for the GNOME2/MATE panel. Does it log any data such as date, time, temperature, etc etc so that it can be put into a Calc sheet for chart creation etc?

I can't see any log files in /var/logs for the indicator so I'm stumped as to any other place to look if it does have a log system. 

You see I'm too skint to buy a digital weather station and too lazy to look at a thermometer :lolflag:

My programming skills are sadly limited to XML form creation in Writer, and that's through drag-and-drop GUIs so I don't know if I'm undone before I've even started. 

PS: If this is in the wrong forum please feel free to move it.

---

### Post by Zugzwang on 2012-10-08
> **iconmaroon said:**
> 
My programming skills are sadly limited to XML form creation in Writer, and that's through drag-and-drop GUIs so I don't know if I'm undone before I've even started. 


Your limited programming skills might be a problem for your task. Apparently the weather applet does not write a log file, which is not surprising. Just imagine for a second that every application would write a log file about what it receives all the time. Your hard disk would have quite some work to write that all to disk.

Having said that, the weather applet seems to use libgweather for obtaining the information ([http://developer.gnome.org/libgweather/2.30/libgweather-weather.html](http://developer.gnome.org/libgweather/2.30/libgweather-weather.html)).

The source package for libgweather has a test program "test_metar" which you might use for extracting weather information on the command line/in the terminal. However, if you never build a piece of software, getting it to run might be a bit tricky for you.

---

### Post by greenpeace on 2012-10-08
You could give it a try... the Yahoo Weather Service provides an RSS Feed which might help.  And assuming that their data is accurate... 

[http://developer.yahoo.com/weather/](http://developer.yahoo.com/weather/)

[install feedparser for python]("http://pypi.python.org/pypi/feedparser/#downloads") to help you interpret the results.

Then just a few lines of python will give you the temperature:

```
#!/usr/bin/python
import feedparser

url  = "http://weather.yahooapis.com/forecastrss"
lctn = "753692"
unit = "c"

url += "?w=%s&u=%s" % (lctn, unit)
feed = feedparser.parse(url)

print feed["items"][0]["yweather_condition"]["temp"]
```

Here the **lctn** parameter represents Barcelona... you'll need to find your own location ID using the instructions on the yahoo website.

change the **unit** to **f** if you want results in Fahrenheit.


Finally you'll need to 

a. find a way to execute the script on a regular basis .. and
b. modify the script to write the data to where you want it... perhaps with the time/date it was requested?  

depends on what you want to do with the data I suppose... but you should be able to work it out from here.

Good luck!

---

