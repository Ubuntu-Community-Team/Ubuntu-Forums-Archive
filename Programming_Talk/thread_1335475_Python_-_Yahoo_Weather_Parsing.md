---
title: "Python - Yahoo Weather Parsing"
date: 2009-11-23
forum: Programming Talk
---

### Post by MikeVaughanG on 2009-11-23
how do I use this code:

```

import urllib
from elementtree.ElementTree import parse

WEATHER_URL = 'http://xml.weather.yahoo.com/forecastrss?p=46112'
WEATHER_NS = 'http://xml.weather.yahoo.com/ns/rss/1.0'

def weather_for_zip(zip_code):
    url = WEATHER_URL % zip_code
    rss = parse(urllib.urlopen(url)).getroot()
    forecasts = []
    for element in rss.findall('channel/item/{%s}forecast' % WEATHER_NS):
        forecasts.append({
            'date': element.get('date'),
            'low': element.get('low'),
            'high': element.get('high'),
            'condition': element.get('text')
        })
    ycondition = rss.find('channel/item/{%s}condition' % WEATHER_NS)
    return {
        'current_condition': ycondition.get('text'),
        'current_temp': ycondition.get('temp'),
        'forecasts': forecasts,
        'title': rss.findtext('channel/title')
    }
```

To print the precipitation, and highs and lows?

Thanks to anyone who can help.

---

