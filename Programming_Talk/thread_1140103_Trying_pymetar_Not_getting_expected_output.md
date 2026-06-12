---
title: "Trying pymetar: Not getting expected output"
date: 2009-04-27
forum: Programming Talk
---

### Post by sakista on 2009-04-27
I am trying out pymetar. I know it is meant to download the metar data from a site and then parse that data, but I want to input the metar data from a file and parse it. 
 
So I tried the following test code first:
 
```

import sys
import time
import pymetar
 
if __name__ == "__main__":
    t = time.time()
    dailyList = []
    station = {'VEGT': 'Guwahati', \
               'VIDP': 'Delhi', \
               'VIJP': 'Jaipur'}
    metar = ['VEGT 241300Z 00000KT 4500 HZ FEW020 SCT100 31/23 Q1004 NOSIG=', \
             'VIDP 241230Z 31008G18KT 4500 DU NSC 34/02 Q1008 NOSIG=', \
             'VIJP 241230Z 33006KT 4000 HZ FEW100 36/M03 Q1009 NOSIG=']
    for row in metar:
        airport = row[:4]
        rm = pymetar.ReportFetcher(airport).MakeReport(airport, row)
        pm = pymetar.ReportParser()
        pr = pm.ParseReport(rm)
        print "Weather report for %s (%s) as of %s" %\
              (pr.getStationName(), airport, pr.getISOTime())
        print "Values of \"None\" indicate that the value is missing from the report."
        print "Temperature: %s C / %s F" %\
              (pr.getTemperatureCelsius(), pr.getTemperatureFahrenheit())
        print "Rel. Humidity: %s%%" % (pr.getHumidity())
        if pr.getWindSpeed() is not None:
            print "Wind speed: %0.2f m/s (%i Bft)" % \
                  (pr.getWindSpeed(), pr.getWindSpeedBeaufort())
        else:
            print "Wind speed: None"
 
        print "Wind direction: %s deg (%s)" %\
              (pr.getWindDirection(), pr.getWindCompass())
        if pr.getPressure() is not None:
            print "Pressure: %s hPa" % (int(pr.getPressure()))
        else:
            print "Pressure: None"
            print "Dew Point: %s C / %s F" %\
                (pr.getDewPointCelsius(), pr.getDewPointFahrenheit())
            print "Weather:",pr.getWeather()
            print "Sky Conditions:",pr.getSkyConditions()                
    print "\n Time Taken: %.3f" % (time.time()-t)        

```
 
The output -
 
> 
Weather report for None (VEGT) as of None
Values of "None" indicate that the value is missing from the report.
Temperature: None C / None F
Rel. Humidity: None%
Wind speed: None
Wind direction: None deg (None)
Pressure: None
Dew Point: None C / None F
Weather: None
Sky Conditions: None
 
Weather report for None (VIDP) as of None
Values of "None" indicate that the value is missing from the report.
Temperature: None C / None F
Rel. Humidity: None%
Wind speed: None
Wind direction: None deg (None)
Pressure: None
Dew Point: None C / None F
Weather: None
Sky Conditions: None
 
Weather report for None (VIJP) as of None
Values of "None" indicate that the value is missing from the report.
Temperature: None C / None F
Rel. Humidity: None%
Wind speed: None
Wind direction: None deg (None)
Pressure: None
Dew Point: None C / None F
Weather: None
Sky Conditions: None
 
Time Taken: 5.398

 
Why does the output all have 'None' values rather then the parsed values? Any help appreciated.

---

