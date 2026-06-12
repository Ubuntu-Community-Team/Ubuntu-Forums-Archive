---
title: "Change Layout of this Output?"
date: 2006-03-30
forum: Programming Talk
---

### Post by bluevoodoo1 on 2006-03-30
I am trying to get the output of pymetar to display horizontally instead of vertically.

now it shows...

Temp: 100 F
Humidity: 50%

but I'd like it to be...

Temp: 100 F Humidity: 50%

is this possible? Here's the code with the temp/humidity part in red.

```

#!/usr/bin/python2.4 -tt
# -*- coding: iso-8859-15 -*-

__version__="1.0"

import pymetar
import sys

#print "pymet v%s using pymetar lib v%s"%(__version__,pymetar.__version__)

if len(sys.argv)<2 or sys.argv[1]=="--help":
    sys.stderr.write("Usage: %s <station id>\n"% sys.argv[0])
    sys.stderr.write("Station IDs can be found at: http://www.nws.noaa.gov/tg/siteloc.shtml\n")
    sys.exit(1)
elif (sys.argv[1] == "--version"):
    print "pmw v%s using pymetar lib v%s"%(__version__,pymetar.__version__)
    sys.exit(0)
else:
    station=sys.argv[1]

try:
    rf=pymetar.ReportFetcher(station)
    rep=rf.FetchReport()
except Exception, e:
    sys.stderr.write("Something went wrong when fetching the report.\n")
    sys.stderr.write("These usually are transient problems if the station ")
    sys.stderr.write("ID is valid. \nThe error encountered was:\n")
    sys.stderr.write(str(e)+"\n")
    sys.exit(1)

rp=pymetar.ReportParser()
pr=rp.ParseReport(rep)

#print "Weather report for %s (%s) as of %s" %\
#    (pr.getStationName(), station, pr.getISOTime())
#print "Values of \"None\" indicate that the value is missing from the report."
[COLOR="Red"]print "Temp: %s F" % (pr.getTemperatureFahrenheit()) 
print "Humidity: %s%%" % (pr.getHumidity())[/COLOR]
#if pr.getWindSpeed() is not None:
#    print "Wind speed: %0.2f m/s" % (pr.getWindSpeed())
#else:
#    print "Wind speed: None"
#    
#print "Wind direction: %s deg (%s)" %\
#    (pr.getWindDirection(), pr.getWindCompass())
#if pr.getPressure() is not None:
#    print "Pressure: %s hPa" % (int(pr.getPressure()))
#else:
#    print "Pressure: None"
#
#print "Dew Point: %s C / %s F" %\
#    (pr.getDewPointCelsius(), pr.getDewPointFahrenheit())
#print "Weather:",pr.getWeather()
#print "Sky Conditions:",pr.getSkyConditions() 

```

---

### Post by IYY on 2006-03-30
If I was doing this, I wouldn't even change the source code but just make a script to modify the output. However, changing the code here looks very easy, just replace the red lines with something like:

print "Temp: %s F" % (pr.getTemperatureFahrenheit()) + "Humidity: %s%%" % (pr.getHumidity())

(this is just a guess, I don't really know python well, but I think it concatenates using +)

---

### Post by supirman on 2006-03-30
Just put a comma at the end of the first red line, which will suppress the newline.

That is:
```

print "Temp: %s F" % (pr.getTemperatureFahrenheit()) ,
print "Humidity: %s%%" % (pr.getHumidity())

```

---

### Post by bluevoodoo1 on 2006-03-30
[QUOTE=supirman]Just put a comma at the end of the first red line, which will suppress the newline.

That is:
```

print "Temp: %s F" % (pr.getTemperatureFahrenheit()) ,
print "Humidity: %s%%" % (pr.getHumidity())

```[/QUOTE]


Great! Easy as adding a comma! Thank you!

---

