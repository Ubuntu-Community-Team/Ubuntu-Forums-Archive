---
title: "Function to show weather forecast in the terminal"
date: 2013-10-05
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-10-05
Hi Guys,

I found this function that works for the most part.

```


weather(){ curl -s "http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=${@:-<LOCATION>}"|perl -ne '/<title>([^<]+)/&&printf "%s: ",$1;/<fcttext>([^<]+)/&&print $1,"\n"';}




```

See the page:[http://www.commandlinefu.com/commands/view/4821/get-the-weather-forecast-for-the-next-24-to-48-for-your-location.](http://www.commandlinefu.com/commands/view/4821/get-the-weather-forecast-for-the-next-24-to-48-for-your-location.)

My questions are:

1. Does anyone know how I can get rid of the **&amp;de**in the output: See below

October 5, 2013: Overcast. High 10&amp;deg;C (50&amp;deg;F). Winds 14 kph SSW

2. How I can get the name of the city to show at the top of the forecast like in their example. (See sample output on the link above.)

---

### Post by Vaphell on 2013-10-05
1. *s/&amp;deg;/°/g; *at the beginning of the perl code
2. in that xml there is no info about the location other than the timezone

---

### Post by GrouchyGaijin on 2013-10-05
Thanks - I figured you would know right off the bat how to sed that stuff out.
I don't follow on #2.  I thought the place called /<title> was supposed to show the name of the city if it were /location

---

### Post by Vaphell on 2013-10-05
no, <title> stores date.
relevant parts of the xml look like this:
```
<title>October 5, 2013</title>
<fcttext>Chance of Rain. High 19&deg;C (66&deg;F). Winds 25 kph SW</fcttext>
```

the only thing that you can do is to print out the provided parameter or the default value hardcoded in the function, eg
```
weather()
{
  (( $# )) || set -- "London,UK"
  echo "Location: ${1//,/, }"
  curl -s "http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=$1" | perl -ne 's/&amp;deg;/°/g;
                                                                                                s/ \(\d+°F\)//g;
                                                                                                /<title>([^<]+)/ && printf "%s: ",$1;
                                                                                                /<fcttext>([^<]+)/ && print $1,"\n"';
}
```
(oneliners are overrated ;) )
2nd line of the perl block strips Fahrenheits because we don't use them here. If you live in a Fahrenheit country, modify to strip °C with* s/\d+°C \((\d+°F)\)/$1/g;* but i don't think Sweden is one :)

```
$ weather
Location: London, UK
October 5, 2013: Chance of Rain. High 19°C. Winds 25 kph SW
October 6, 2013: Chance of Rain. High 19°C. Winds 10 kph WNW
October 7, 2013: Clear. High 20°C. Winds 10 kph WSW
October 8, 2013: Clear. High 20°C. Winds 10 kph SW
October 9, 2013: Clear. High 19°C. Winds 10 kph West
October 10, 2013: Scattered Clouds. High 19°C. Winds 10 kph NNE
$ weather Washington,DC
Location: Washington, DC
Today: Mostly sunny. Hot with highs in the upper 80s. Northwest winds around 5 mph. 
Tonight: Mostly cloudy. Lows in the upper 60s. Southeast winds around 5 mph. 
Sunday: Partly sunny. Hot with highs in the upper 80s. Southeast winds 5 to 10 mph. 
Sunday Night: Partly cloudy in the evening...then becoming mostly cloudy. Lows in the mid 60s. South winds 5 to 10 mph. 
Monday: Mostly cloudy. Showers...mainly in the afternoon. Highs in the upper 70s. South winds 10 to 15 mph. Chance of rain 80 percent. 
```

---

### Post by GrouchyGaijin on 2013-10-05
Thanks man!

Location: Falun, Sweden
October 5, 2013: Overcast. High 10°C. Winds 14 kph SSW
October 6, 2013: Chance of Rain. High 12°C. Winds 14 kph SSW
October 7, 2013: Overcast. High 13°C. Winds 14 kph SW
October 8, 2013: Partly Cloudy. High 16°C. Winds 14 kph WSW
October 9, 2013: Overcast. High 15°C. Winds 25 kph WSW
October 10, 2013: Scattered Clouds. High 14°C. Winds 21 kph NNW

---

### Post by GrouchyGaijin on 2013-10-05
> **Vaphell said:**
>  but i don't think Sweden is one :)


We use it only if the month has 32 days.;)

---

### Post by GrouchyGaijin on 2013-10-06
@Vaphell

OK Boss, I need some more guidance ;-)

Can you explain why when I run this script:

```


#!/bin/bash
echo
{  curl -s "http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=$1" | perl -ne 's/&amp;deg;/°/g;
                                                                                                s/ \(\d+°F\)//g;
                                                                                                /<title>([^<]+)/ && printf "%s: ",$1;
                                                                                                /<fcttext>([^<]+)/ && print $1,"\n"';
}




```

```
weather Las Vegas
``` 
I'll get a forecast (although in F)

but more often than not particularly if the name of the city has Grand in it. Example: Grand Cayman,Cayman Islands
the script returns nothing.  In that case I need to add the %20 between the words.

Is this because of the way the website is coded or something in the command I am issuing?

---

### Post by Vaphell on 2013-10-06
forecast for USian locations seems to be in a different format, it's more verbose. Probably a different data provider so these s/// related to degrees won't work. You'd have to extract the numbers and convert them by hand, but there is another pain - there are no indicators of degrees so you'd have to recognize which numbers are related to temperatures and which to winds.

Either way when you have [COLOR="#0000FF"]*[http://something/something/index.xml?query=something](http://something/something/index.xml?query=something)[/COLOR] something,something something*, the url will obviously end at the first space (as evidenced by the forum software ;-) ). In other words space is not a valid url char and has to be replaced with %20. Sure, you can type url with spaces into the webbrowser and it will work but it's a convenience for nublet webusers. Standards are there for a reason :)
replace $1 with *${1// /%20}*.

You need to type the location as a single parameter, eg quoted because $1. *weather Las Vegas * will return 'Location: Las' because Vegas is $2 and doesn't matter.
If you want your script/function more tolerant you'd have to code around the cases where you can feed multiple params
something like 
```

(( $# )) || set -- "Falun, Sweden"
loc=$*
echo "Location: $loc"
url="http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=${loc// /%20}"
  
curl -s "$url" | perl -ne 's/&amp;deg;/°/g;
                           s/ \(\d+°F\)//g;
                           /<title>([^<]+)/ && printf "%s: ",$1;
                           /<fcttext>([^<]+)/ && print $1,"\n";'

```

difference between $@ and $* is this
```
$ set -- a b c d e
$ printf "[%s]\n" "$*"
[a b c d e]
$ printf "[%s]\n" "$@"
[a]
[b]
[c]
[d]
[e]
```
$* glues all parameters into a single string using first char of IFS as a glue (obviously space by default).
```
$ IFS=:; printf "[%s]\n" "$*"
[a:b:c:d:e]
```

---

### Post by ian-weisser on 2013-10-06
> **GrouchyGaijin said:**
> http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?

That service seems to be deprecated.
Wunderground.com has moved to a purchased-key model for api access. See [http://www.wunderground.com/weather/api/](http://www.wunderground.com/weather/api/) 

For US locations, I use data from the National Weather Service. No api key required. For how I do it, see [http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html](http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html)

The Ubuntu Phone weather app gets worldwide data from OpenWeatherMap.org. It also uses an api key for access, but the price is $0. See [http://openweathermap.org/API#forecast](http://openweathermap.org/API#forecast)

---

### Post by GrouchyGaijin on 2013-10-06
Man, you are a [COLOR=#0000ff]**WIZARD **[/COLOR]:popcorn:

---

### Post by GrouchyGaijin on 2013-10-06
> **ian-weisser said:**
> That service seems to be deprecated.
Wunderground.com has moved to a purchased-key model for api access. See [http://www.wunderground.com/weather/api/](http://www.wunderground.com/weather/api/) 

For US locations, I use data from the National Weather Service. No api key required. For how I do it, see [http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html](http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html)

The Ubuntu Phone weather app gets worldwide data from OpenWeatherMap.org. It also uses an api key for access, but the price is $0. See [http://openweathermap.org/API#forecast](http://openweathermap.org/API#forecast)

Thanks for the update Ian.

OK so I got a free key from the weather underground.  Their developer level is free.
I can now download an xml file of the current conditions in my area.
The thing is I don't know how to go from that to showing in the terminal my current conditions and forecast.
Ideally something like the function that started this thread, but also including the current conditions would be great.

I really appreciate the help guys!

Here is the xml file:

```




<response>
	<version>0.1</version>
	<termsofService>http://www.wunderground.com/weather/api/d/terms.html</termsofService>
	<features>
		<feature>conditions</feature>
	</features>
		<current_observation>
		<image>
		<url>http://icons-ak.wxug.com/graphics/wu2/logo_130x80.png</url>
		<title>Weather Underground</title>
		<link>http://www.wunderground.com</link>
		</image>
		<display_location>
		<full>Falun, Sweden</full>
		<city>Falun</city>
		<state></state>
		<state_name>Sweden</state_name>
		<country>SN</country>
		<country_iso3166>SE</country_iso3166>
		<zip>00000</zip>
		<magic>6</magic>
		<wmo>02435</wmo>
		<latitude>60.59999847</latitude>
		<longitude>15.63333321</longitude>
		<elevation>116.00000000</elevation>
		</display_location>
		<observation_location>
		<full>Kämparvet, Falun, DALARNA</full>
		<city>Kämparvet, Falun</city>
		<state>DALARNA</state>
		<country>SWEDEN</country>
		<country_iso3166>SE</country_iso3166>
		<latitude>60.606194</latitude>
		<longitude>15.639073</longitude>
		<elevation>50 ft</elevation>
		</observation_location>
		<estimated>
		</estimated>
		<station_id>IDALARNA23</station_id>
		<observation_time>Last Updated on October 6, 6:47 PM CEST</observation_time>
		<observation_time_rfc822>Sun, 06 Oct 2013 18:47:04 +0200</observation_time_rfc822>
		<observation_epoch>1381078024</observation_epoch>
		<local_time_rfc822>Sun, 06 Oct 2013 18:47:05 +0200</local_time_rfc822>
		<local_epoch>1381078025</local_epoch>
		<local_tz_short>CEST</local_tz_short>
		<local_tz_long>Europe/Stockholm</local_tz_long>
		<local_tz_offset>+0200</local_tz_offset>
		<weather>Clear</weather>
		<temperature_string>54.3 F (12.4 C)</temperature_string>
		<temp_f>54.3</temp_f>
		<temp_c>12.4</temp_c>
		<relative_humidity>74%</relative_humidity>
		<wind_string>From the SE at 2.0 MPH</wind_string>
		<wind_dir>SE</wind_dir>
		<wind_degrees>135</wind_degrees>
		<wind_mph>2.0</wind_mph>
		<wind_gust_mph>0</wind_gust_mph>
		<wind_kph>3.2</wind_kph>
		<wind_gust_kph>0</wind_gust_kph>
		<pressure_mb>1012</pressure_mb>
		<pressure_in>29.89</pressure_in>
		<pressure_trend>0</pressure_trend>
		
		<dewpoint_string>46 F (8 C)</dewpoint_string>
		<dewpoint_f>46</dewpoint_f>
		<dewpoint_c>8</dewpoint_c>
		
		
		<heat_index_string>NA</heat_index_string>
		<heat_index_f>NA</heat_index_f>
		<heat_index_c>NA</heat_index_c>
		
		
		<windchill_string>NA</windchill_string>
		<windchill_f>NA</windchill_f>
		<windchill_c>NA</windchill_c>
		
        <feelslike_string>54.3 F (12.4 C)</feelslike_string>
        <feelslike_f>54.3</feelslike_f>
        <feelslike_c>12.4</feelslike_c>
		<visibility_mi>6.2</visibility_mi>
		<visibility_km>10.0</visibility_km>
		<solarradiation></solarradiation>
		<UV>-1</UV>
		<precip_1hr_string>0.00 in ( 0 mm)</precip_1hr_string>
		<precip_1hr_in>0.00</precip_1hr_in>
		<precip_1hr_metric> 0</precip_1hr_metric>
		<precip_today_string>0.00 in (0 mm)</precip_today_string>
		<precip_today_in>0.00</precip_today_in>
		<precip_today_metric>0</precip_today_metric>
		
		
		
		<icon>clear</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/nt_clear.gif</icon_url>
		<forecast_url>http://www.wunderground.com/global/stations/02435.html</forecast_url>
        
        <history_url>http://www.wunderground.com/weatherstation/WXDailyHistory.asp?ID=IDALARNA23</history_url>
        
		<ob_url>http://www.wunderground.com/cgi-bin/findweather/getForecast?query=60.606194,15.639073</ob_url>
	</current_observation>


   
</response>
	




```

---

### Post by Vaphell on 2013-10-06
time for some python :cool:

```
#!/usr/bin/env python

import sys
import urllib2
import xml.etree.ElementTree as ET

data = ( (  "Location: {0}", [ "display_location/full" ] ),
         (  "Time: {0}", [ "observation_time_rfc822" ] ),
         (  "Conditions: {0}", [ "weather" ] ),
         ( u"Temperature: {0}\u00b0C ({1}\u00b0F), feels like {2}\u00b0C ({3}\u00b0F)", [ "temp_c", "temp_f", "feelslike_c", "feelslike_f" ] ),
         (  "Wind: {0} km/h, from the {1}", [ "wind_kph", "wind_dir" ] ),
         (  "Pressure: {0} hPa", [ "pressure_mb" ] ),
         ( u"Dew point: {0}\u00b0C ({1}\u00b0F)", [ "dewpoint_c", "dewpoint_f" ] ) )

#url = "https://???"
#req = urllib2.Request( url )
#f = urllib2.urlopen( req )
f = open( "test.xml", "r" )
xmlroot = ET.fromstring( f.read() )

for x in data:
  print x[0].format( *[ xmlroot.findall(".//"+i)[0].text for i in x[1] ] )
```

```
$ ./weather.py 
Location: Falun, Sweden
Time: Sun, 06 Oct 2013 18:47:04 +0200
Conditions: Clear
Temperature: 12.4°C (54.3°F), feels like 12.4°C (54.3°F)
Wind: 3.2 km/h, from the SE
Pressure: 1012 hPa
Dew point: 8°C (46°F)
```


it uses a local file with the data now, but in comments there is a code for gobbling the data directly from the server that should work.
data describes lines of output: format string + [ fields/xml tags ] which are supposed to go into {integer} placeholders so it's trivial to come up with your own format.
I don't see forecast there so...

---

### Post by GrouchyGaijin on 2013-10-06
I am speechless.
I was mucking around with sed and you pull a really cool script out like it's nothing.
By comparing the xml with your python script I think I can kind of see what you are doing.

I tried with the forecast xml file and mucked it up a bit.

```




<response>
	<version>0.1</version>
	<termsofService>http://www.wunderground.com/weather/api/d/terms.html</termsofService>
	<features>
		<feature>forecast</feature>
	</features>
	<forecast>
		<txt_forecast>
		<date>2:00 PM CEST</date>
		<forecastdays>
		<forecastday>
		<period>0</period>
		<icon>partlycloudy</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/partlycloudy.gif</icon_url>
		<title>Sunday</title>
		<fcttext><![CDATA[Overcast in the morning, then partly cloudy. High of 57F. Winds from the SSW at 5 to 10 mph.]]></fcttext>
		<fcttext_metric><![CDATA[Overcast in the morning, then partly cloudy. High of 14C. Winds from the SSW at 10 to 15 km/h.]]></fcttext_metric>
		<pop>0</pop>
		</forecastday>
		<forecastday>
		<period>1</period>
		<icon>mostlycloudy</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/mostlycloudy.gif</icon_url>
		<title>Sunday Night</title>
		<fcttext><![CDATA[Mostly cloudy in the evening, then overcast. Fog overnight. Low of 45F. Winds from the WSW at 5 to 15 mph.]]></fcttext>
		<fcttext_metric><![CDATA[Mostly cloudy in the evening, then overcast. Fog overnight. Low of 7C. Breezy. Winds from the WSW at 10 to 20 km/h.]]></fcttext_metric>
		<pop>20</pop>
		</forecastday>
		<forecastday>
		<period>2</period>
		<icon>mostlycloudy</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/mostlycloudy.gif</icon_url>
		<title>Monday</title>
		<fcttext><![CDATA[Mostly cloudy. High of 61F. Winds from the WSW at 5 to 10 mph.]]></fcttext>
		<fcttext_metric><![CDATA[Mostly cloudy. High of 16C. Breezy. Winds from the WSW at 10 to 20 km/h.]]></fcttext_metric>
		<pop>0</pop>
		</forecastday>
		<forecastday>
		<period>3</period>
		<icon>cloudy</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/cloudy.gif</icon_url>
		<title>Monday Night</title>
		<fcttext><![CDATA[Overcast with  rain after midnight. Low of 50F. Winds from the WSW at 5 to 10 mph.]]></fcttext>
		<fcttext_metric><![CDATA[Overcast with  rain after midnight. Low of 10C. Winds from the WSW at 5 to 15 km/h.]]></fcttext_metric>
		<pop>60</pop>
		</forecastday>
		<forecastday>
		<period>4</period>
		<icon>rain</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/rain.gif</icon_url>
		<title>Tuesday</title>
		<fcttext><![CDATA[Overcast with  a chance of rain in the afternoon. Fog early. High of 59F. Winds from the SW at 5 to 15 mph. Chance of rain 40%.]]></fcttext>
		<fcttext_metric><![CDATA[Overcast with  a chance of rain in the afternoon. Fog early. High of 15C. Breezy. Winds from the SW at 10 to 20 km/h. Chance of rain 40%.]]></fcttext_metric>
		<pop>40</pop>
		</forecastday>
		<forecastday>
		<period>5</period>
		<icon>mostlycloudy</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/mostlycloudy.gif</icon_url>
		<title>Tuesday Night</title>
		<fcttext><![CDATA[Overcast. Fog overnight. Low of 46F. Winds from the SW at 10 to 15 mph.]]></fcttext>
		<fcttext_metric><![CDATA[Overcast. Fog overnight. Low of 8C. Breezy. Winds from the SW at 15 to 20 km/h.]]></fcttext_metric>
		<pop>0</pop>
		</forecastday>
		<forecastday>
		<period>6</period>
		<icon>cloudy</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/cloudy.gif</icon_url>
		<title>Wednesday</title>
		<fcttext><![CDATA[Overcast. High of 57F. Winds from the SW at 10 to 15 mph.]]></fcttext>
		<fcttext_metric><![CDATA[Overcast. High of 14C. Breezy. Winds from the SW at 20 to 25 km/h.]]></fcttext_metric>
		<pop>0</pop>
		</forecastday>
		<forecastday>
		<period>7</period>
		<icon>cloudy</icon>
		<icon_url>http://icons-ak.wxug.com/i/c/k/cloudy.gif</icon_url>
		<title>Wednesday Night</title>
		<fcttext><![CDATA[Overcast with  a chance of rain after midnight. Fog overnight. Low of 37F. Winds from the WSW at 5 to 10 mph shifting to the NE after midnight.]]></fcttext>
		<fcttext_metric><![CDATA[Overcast with  a chance of rain after midnight. Fog overnight. Low of 3C. Winds from the WSW at 5 to 15 km/h shifting to the NE after midnight.]]></fcttext_metric>
		<pop>20</pop>
		</forecastday>
		</forecastdays>
		</txt_forecast>
		<simpleforecast>
		<forecastdays>
		<forecastday>
		<date>
  <epoch>1381093200</epoch>
  <pretty_short>11:00 PM CEST</pretty_short>
  <pretty>11:00 PM CEST on October 06, 2013</pretty>
  <day>6</day>
  <month>10</month>
  <year>2013</year>
  <yday>278</yday>
  <hour>23</hour>
  <min>00</min>
  <sec>0</sec>
  <isdst>1</isdst>
  <monthname>October</monthname>
  <weekday_short>Sun</weekday_short>
  <weekday>Sunday</weekday>
  <ampm>PM</ampm>
  <tz_short>CEST</tz_short>
  <tz_long>Europe/Stockholm</tz_long>
</date>
					<period>1</period>
					<high>
						<fahrenheit>57</fahrenheit>
						<celsius>14</celsius>
					</high>
					<low>
						<fahrenheit>45</fahrenheit>
						<celsius>7</celsius>
					</low>
					<conditions>Partly Cloudy</conditions>
					
					<icon>partlycloudy</icon>
					<icon_url>http://icons-ak.wxug.com/i/c/k/partlycloudy.gif</icon_url>
					<skyicon>partlycloudy</skyicon>
					<pop>0</pop>
					<qpf_allday>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_allday>
					<qpf_day>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_day>
					<qpf_night>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_night>
					<snow_allday>
						<in>0</in>
						<cm>0</cm>
					</snow_allday>
					<snow_day>
						<in>0</in>
						<cm>0</cm>
					</snow_day>
					<snow_night>
						<in>0</in>
						<cm>0</cm>
					</snow_night>
					<maxwind>
						<mph>9</mph>
						<kph>14</kph>
						<dir>SW</dir>
						<degrees>220</degrees>
					</maxwind>
					<avewind>
						<mph>8</mph>
						<kph>13</kph>
						<dir>SW</dir>
						<degrees>225</degrees>
					</avewind>
					<avehumidity>78</avehumidity>
					<maxhumidity>97</maxhumidity>
					<minhumidity>66</minhumidity>
				</forecastday>
				
				<forecastday>
					<date>
  <epoch>1381179600</epoch>
  <pretty_short>11:00 PM CEST</pretty_short>
  <pretty>11:00 PM CEST on October 07, 2013</pretty>
  <day>7</day>
  <month>10</month>
  <year>2013</year>
  <yday>279</yday>
  <hour>23</hour>
  <min>00</min>
  <sec>0</sec>
  <isdst>1</isdst>
  <monthname>October</monthname>
  <weekday_short>Mon</weekday_short>
  <weekday>Monday</weekday>
  <ampm>PM</ampm>
  <tz_short>CEST</tz_short>
  <tz_long>Europe/Stockholm</tz_long>
</date>
					<period>2</period>
					<high>
						<fahrenheit>61</fahrenheit>
						<celsius>16</celsius>
					</high>
					<low>
						<fahrenheit>50</fahrenheit>
						<celsius>10</celsius>
					</low>
					<conditions>Mostly Cloudy</conditions>
					
					<icon>mostlycloudy</icon>
					<icon_url>http://icons-ak.wxug.com/i/c/k/mostlycloudy.gif</icon_url>
					<skyicon>mostlycloudy</skyicon>
					<pop>0</pop>
					<qpf_allday>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_allday>
					<qpf_day>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_day>
					<qpf_night>
						<in>0.05</in>
						<mm>1.3</mm>
					</qpf_night>
					<snow_allday>
						<in>0</in>
						<cm>0</cm>
					</snow_allday>
					<snow_day>
						<in>0</in>
						<cm>0</cm>
					</snow_day>
					<snow_night>
						<in>0</in>
						<cm>0</cm>
					</snow_night>
					<maxwind>
						<mph>10</mph>
						<kph>16</kph>
						<dir>WSW</dir>
						<degrees>252</degrees>
					</maxwind>
					<avewind>
						<mph>7</mph>
						<kph>11</kph>
						<dir>WSW</dir>
						<degrees>248</degrees>
					</avewind>
					<avehumidity>86</avehumidity>
					<maxhumidity>100</maxhumidity>
					<minhumidity>67</minhumidity>
				</forecastday>
				
				<forecastday>
					<date>
  <epoch>1381266000</epoch>
  <pretty_short>11:00 PM CEST</pretty_short>
  <pretty>11:00 PM CEST on October 08, 2013</pretty>
  <day>8</day>
  <month>10</month>
  <year>2013</year>
  <yday>280</yday>
  <hour>23</hour>
  <min>00</min>
  <sec>0</sec>
  <isdst>1</isdst>
  <monthname>October</monthname>
  <weekday_short>Tue</weekday_short>
  <weekday>Tuesday</weekday>
  <ampm>PM</ampm>
  <tz_short>CEST</tz_short>
  <tz_long>Europe/Stockholm</tz_long>
</date>
					<period>3</period>
					<high>
						<fahrenheit>59</fahrenheit>
						<celsius>15</celsius>
					</high>
					<low>
						<fahrenheit>46</fahrenheit>
						<celsius>8</celsius>
					</low>
					<conditions>Rain</conditions>
					
					<icon>rain</icon>
					<icon_url>http://icons-ak.wxug.com/i/c/k/rain.gif</icon_url>
					<skyicon>cloudy</skyicon>
					<pop>40</pop>
					<qpf_allday>
						<in>0.05</in>
						<mm>1.3</mm>
					</qpf_allday>
					<qpf_day>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_day>
					<qpf_night>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_night>
					<snow_allday>
						<in>0</in>
						<cm>0</cm>
					</snow_allday>
					<snow_day>
						<in>0</in>
						<cm>0</cm>
					</snow_day>
					<snow_night>
						<in>0</in>
						<cm>0</cm>
					</snow_night>
					<maxwind>
						<mph>11</mph>
						<kph>18</kph>
						<dir>SW</dir>
						<degrees>230</degrees>
					</maxwind>
					<avewind>
						<mph>9</mph>
						<kph>14</kph>
						<dir>SW</dir>
						<degrees>223</degrees>
					</avewind>
					<avehumidity>91</avehumidity>
					<maxhumidity>100</maxhumidity>
					<minhumidity>82</minhumidity>
				</forecastday>
				
				<forecastday>
					<date>
  <epoch>1381352400</epoch>
  <pretty_short>11:00 PM CEST</pretty_short>
  <pretty>11:00 PM CEST on October 09, 2013</pretty>
  <day>9</day>
  <month>10</month>
  <year>2013</year>
  <yday>281</yday>
  <hour>23</hour>
  <min>00</min>
  <sec>0</sec>
  <isdst>1</isdst>
  <monthname>October</monthname>
  <weekday_short>Wed</weekday_short>
  <weekday>Wednesday</weekday>
  <ampm>PM</ampm>
  <tz_short>CEST</tz_short>
  <tz_long>Europe/Stockholm</tz_long>
</date>
					<period>4</period>
					<high>
						<fahrenheit>57</fahrenheit>
						<celsius>14</celsius>
					</high>
					<low>
						<fahrenheit>37</fahrenheit>
						<celsius>3</celsius>
					</low>
					<conditions>Overcast</conditions>
					
					<icon>cloudy</icon>
					<icon_url>http://icons-ak.wxug.com/i/c/k/cloudy.gif</icon_url>
					<skyicon>cloudy</skyicon>
					<pop>0</pop>
					<qpf_allday>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_allday>
					<qpf_day>
						<in>0.00</in>
						<mm>0.0</mm>
					</qpf_day>
					<qpf_night>
						<in>0.08</in>
						<mm>2.0</mm>
					</qpf_night>
					<snow_allday>
						<in>0</in>
						<cm>0</cm>
					</snow_allday>
					<snow_day>
						<in>0</in>
						<cm>0</cm>
					</snow_day>
					<snow_night>
						<in>0</in>
						<cm>0</cm>
					</snow_night>
					<maxwind>
						<mph>14</mph>
						<kph>22</kph>
						<dir>SW</dir>
						<degrees>232</degrees>
					</maxwind>
					<avewind>
						<mph>10</mph>
						<kph>16</kph>
						<dir>SW</dir>
						<degrees>230</degrees>
					</avewind>
					<avehumidity>83</avehumidity>
					<maxhumidity>100</maxhumidity>
					<minhumidity>64</minhumidity>
				</forecastday>
				
			</forecastdays>
		</simpleforecast>
	</forecast>   
    
</response>




```

---

### Post by Vaphell on 2013-10-06
weather.py
```
#!/usr/bin/env python

import re
import sys
import urllib2
import xml.etree.ElementTree as ET

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
styles = { '[END]'    : '\033[0m',
           '[B]'      : '\033[1m',
           '[RED]'    : '\033[91m',           
           '[GREEN]'  : '\033[92m',
           '[YELLOW]' : '\033[93m',
           '[BLUE]'   : '\033[94m',
           '[MAGENTA]': '\033[95m',
           '[CYAN]'   : '\033[96m' }

field_rgx = r'\{[^}]*[a-z]+[^}]*\}'

# open xmls with data
cxml = ET.fromstring( open( 'current.xml', 'r' ).read() )
fxml = ET.fromstring( open( 'forecast.xml', 'r' ).read() )

format = {}
data = []

# load formatting data           
for ln in open( 'weather_format.txt', 'r' ):
  ln = ln.rstrip()
  if ln.startswith('!'):
    f_id = ln.lstrip('! ')
    format[f_id] = []
    data.append( ( f_id, cxml if 'current' in f_id else fxml ) )
  elif ln.startswith('#'):
    continue
  else:
    for s in styles:
      ln = ln.replace( s, styles[s] )
    fields = [ x.strip('{}') for x in re.findall( field_rgx, ln ) ]
    for i in range( 0, len(fields) ):
      ln = re.sub( field_rgx, '{{{0}}}'.format(i), ln, 1 )
    format[f_id].append( [ ln, fields[:] ] )


# print info
for (k,xml) in data:
  for x in xml.findall( k ):
    for ln in format[k]:
      print ln[0].format( *[ x.findtext( './/'+i ) for i in ln[1] ] )
  print



```

sample weather_format.txt:
```
# current weather
! .//current_observation
   [CYAN]Location:[END] [B][GREEN]{display_location/full}[END]
       [CYAN]Time:[END] {observation_time_rfc822}
 [MAGENTA]Conditions:[END] [B][YELLOW]{weather}[END]
[MAGENTA]Temperature:[END] [B][YELLOW]{temp_c}°C[END] ({temp_f}°F), feels like [B][YELLOW]{feelslike_c}°C[END] ({feelslike_f}°F)
       [RED]Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
   [MAGENTA]Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
  [BLUE]Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END] ({dewpoint_f}°F)
# forecast in text format
! .//txt_forecast/forecastdays/forecastday
[CYAN]{title}:[END]
  {fcttext_metric}
# forecast in simple format
! .//simpleforecast/forecastdays/forecastday
[MAGENTA]{weekday}, {date/monthname} {date/day}, {date/year}:[END]
  {conditions}, high {high/celsius}°C, low {low/celsius}°C
  Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h
```


so the forecast appears to be in 2 formats in parallel: text based (text_forecast) and field based (simpleforecast). Just for kicks i tapped into both of them ;-)
Also i extracted the formatting data to external txt file so it's easier to manipulate than by tweaking tuples and lists by hand in the code.

# lines are comments so ignored
! XXX are headers of templates and point to portions of xml on which their templates are based.  {} markers indicate which xml fields will fill the blanks. The file format is pretty straightforward and for bonus points i added colors and bold :cool:

---

### Post by GrouchyGaijin on 2013-10-07
THANK YOU!!

I was going to ask how to incorporate downloading the xml data into the python script, but I just put the curl -s <url> command in a bash script.
Vaphell, you are amazing.  
You are in Poland right?  If you ever come to Sweden, let me know.  I owe you a beer!

Here is a screen shot of my weather.
[http://screencloud.net/v/BUAf](http://screencloud.net/v/BUAf)

---

### Post by Vaphell on 2013-10-07
you should change these random colors in the current conditions section to something more sane, that was a showcase/test ;-) You can reformat it, or plug another data, just look at xml fields and try to add some.

where does that lame #None come from? I must have missed something :/

> I was going to ask how to incorporate downloading the xml data into the python script

it would be something like this
```

current_url = 'https://???'
forecast_url = 'https://???'
# open xmls with data
cxml = urllib2.urlopen( urllib2.Request( current_url ) ).read()
fxml = urllib2.urlopen( urllib2.Request( forecast_url ) ).read()
```

> You are in Poland right? If you ever come to Sweden, let me know. I owe you a beer!
me+Sweden is quite probable, my homie (3x the programmer i am btw ;-) ) works in Karlskrona and said i should visit him some time. That free beer would be nice, i wouldn't want to expose myself to your 1st world prices too much and bankrupt myself ;-)

---

### Post by GrouchyGaijin on 2013-10-07
Anytime you come, let me know.  The offer for a brew is real.
The #none appeared when I commented out the longer text forecast and kept only the simple forecast.

---

### Post by GrouchyGaijin on 2013-10-07
When I tried to add the name of the weather station to the output, it crashed because ascii could not display <city>Kämparvet, Falun</city>.
Is it possible to use uni code? or maybe substitute with sed the ä for an a?

---

### Post by Vaphell on 2013-10-07
in theory that part of cfg file should be totally ignored if commented out

i changed this part a bit (removed print that separated sections and added strip() to deal with cases where the value is padded with spaces for whatever reason and ruins formatting
```
for (k,xml) in data:
  for x in xml.findall( k ):
    for ln in format[k]:
      print ln[0].format( *[ x.findtext( './/'+i ).strip() for i in ln[1] ] )
```

with this:
```
# current weather
! .//current_observation
     [CYAN]Location:[END] [B][GREEN]{display_location/full}[END]
         [CYAN]Time:[END] [B][GREEN]{observation_time_rfc822}[END]
   [CYAN]Conditions:[END] [B][YELLOW]{weather}[END]
  [CYAN]Temperature:[END] [B][YELLOW]{temp_c}°C[END], feels like [B][YELLOW]{feelslike_c}°C[END]
         [CYAN]Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
[CYAN]Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today
     [CYAN]Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
     [CYAN]Humidity:[END] [B][YELLOW]{relative_humidity}[END]
    [CYAN]Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END]
   [CYAN]Visibility:[END] [B][YELLOW]{visibility_km} km[END]

# forecast in text format
#! .//txt_forecast/forecastdays/forecastday
#[CYAN]{title}:[END]
#  {fcttext_metric}
# forecast in simple format
! .//simpleforecast/forecastdays/forecastday
[YELLOW]{weekday}, {date/monthname} {date/day}, {date/year}:[END]
  [BLUE]{conditions}, high {high/celsius}°C, low {low/celsius}°C
  Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]
```
i get this, obviously in bold/color:
```
     Location: Falun, Sweden
         Time: Sun, 06 Oct 2013 18:47:04 +0200
   Conditions: Clear
  Temperature: 12.4°C, feels like 12.4°C
         Wind: 3.2 km/h, from the SE
Precipitation: 0 mm in 1hr, 0 mm today
     Pressure: 1012 hPa
     Humidity: 74%
    Dew point: 8°C
   Visibility: 10.0 km

Sunday, October 6, 2013:
  Partly Cloudy, high 14°C, low 7°C
  Winds 13 km/h from the SW, max 14 km/h
Monday, October 7, 2013:
  Mostly Cloudy, high 16°C, low 10°C
  Winds 11 km/h from the WSW, max 16 km/h
Tuesday, October 8, 2013:
  Rain, high 15°C, low 8°C
  Winds 14 km/h from the SW, max 18 km/h
Wednesday, October 9, 2013:
  Overcast, high 14°C, low 3°C
  Winds 16 km/h from the SW, max 22 km/h

```

---

### Post by GrouchyGaijin on 2013-10-07
I keep getting the unicode error.  It doesn't like the ä in the station name.

---

### Post by Vaphell on 2013-10-08
I think I tackled the unicode problem with the *codecs* module, but I can't say if the script would work properly in case of direct dl from the server, no url, no test ;-)
Also I cleaned up the code to improve readability and trim the fat... but then added few functions to do some cool stuff ;-)

.py:
```
#!/usr/bin/env python

import codecs
import re
import sys
import urllib2
import xml.etree.ElementTree as ET

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
styles = { '[END]'    : '\033[0m',
           '[B]'      : '\033[1m',
           '[RED]'    : '\033[91m',           
           '[GREEN]'  : '\033[92m',
           '[YELLOW]' : '\033[93m',
           '[BLUE]'   : '\033[94m',
           '[MAGENTA]': '\033[95m',
           '[CYAN]'   : '\033[96m' }

field_rgx = r'\{[^:}]*[a-z]+[^:}]*[:}]'

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0:02d}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )
def passthrough( x ): return x

def get_fun( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    else:                      return passthrough( val )


# open xmls with data
cxml = ET.fromstring( open( 'current.xml', 'r' ).read() )
fxml = ET.fromstring( open( 'forecast.xml', 'r' ).read() )

# load formatting data  
data = []         
for ln in codecs.open( 'weather_format.txt', 'r', 'utf-8' ):
    ln = ln.rstrip()
    if ln.startswith('!'):
        f_id = ln.lstrip('! ')
        format = { 'id': f_id, 'template':'', 'fields':[], 'xml':( cxml if 'current' in f_id else fxml ) }
        data.append( format )
    elif ln.startswith('#'): 
        continue
    else:
        format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len(format['template'])>0 else ln )
        format['fields'] += [ x.strip('{}:') for x in re.findall( field_rgx, ln ) ]

for d in data:
    for s in styles:
        d['template'] = d['template'].replace( s, styles[s] )
    for node in d['xml'].findall( d['id'] ):
        print d['template'].format( **dict( ( i, get_fun( i, node.findtext( './/'+str(i) ).strip() ) ) for i in d['fields'] ) )


```

.txt:
```
# current weather
! current_observation
       [CYAN]Location:[END] [B][GREEN]{display_location/full}[END] [GREEN]({display_location/latitude} {display_location/longitude})[END]
[CYAN]Weather station:[END] [B][GREEN]{observation_location/full}[END] [GREEN]({observation_location/latitude} {observation_location/longitude})
           [CYAN]Time:[END] [B][GREEN]{observation_time_rfc822}[END]
     [CYAN]Conditions:[END] [B][YELLOW]{weather}[END]
    [CYAN]Temperature:[END] [B][YELLOW]{temp_c}°C[END], feels like [B][YELLOW]{feelslike_c}°C[END]
           [CYAN]Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
  [CYAN]Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today
       [CYAN]Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
       [CYAN]Humidity:[END] [B][YELLOW]{relative_humidity}[END]
      [CYAN]Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END]
     [CYAN]Visibility:[END] [B][YELLOW]{visibility_km} km[END]

# forecast in text format
#! forecast/txt_forecast/forecastdays/forecastday
#[CYAN]{title}:[END]
#  {fcttext_metric}
# forecast in simple format
! forecast/simpleforecast/forecastdays/forecastday
[YELLOW]{weekday}, {date/monthname} {date/day}, {date/year}:[END]
  [BLUE]{conditions}, high {high/celsius}°C, low {low/celsius}°C
  Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]
```

stdout:
```

       Location: Falun, Sweden (60°35'59"N 15°37'59"E)
Weather station: Kämparvet, Falun, DALARNA (60°36'22"N 15°38'20"E)
           Time: Sun, 06 Oct 2013 18:47:04 +0200
     Conditions: Clear
    Temperature: 12.4°C, feels like 12.4°C
           Wind: 3.2 km/h, from the SE
  Precipitation: 0 mm in 1hr, 0 mm today
       Pressure: 1012 hPa
       Humidity: 74%
      Dew point: 8°C
     Visibility: 10.0 km

Sunday, October 6, 2013:
  Partly Cloudy, high 14°C, low 7°C
  Winds 13 km/h from the SW, max 14 km/h
Monday, October 7, 2013:
  Mostly Cloudy, high 16°C, low 10°C
  Winds 11 km/h from the WSW, max 16 km/h
Tuesday, October 8, 2013:
  Rain, high 15°C, low 8°C
  Winds 14 km/h from the SW, max 18 km/h
Wednesday, October 9, 2013:
  Overcast, high 14°C, low 3°C
  Winds 16 km/h from the SW, max 22 km/h
```

---

### Post by GrouchyGaijin on 2013-10-08
WORKS like a charm!!
You the man!

How in the world do you remember how to do this stuff??

---

### Post by Vaphell on 2013-10-08
i don't, that's what stackoverflow and google are for ;-) python is not my forte, i know builtin data types and how to do comprehensions, but I have to check the docs all the time to see if there is a method that does what I want to do and how to use it.

read
[http://docs.python.org/2/library/string.html](http://docs.python.org/2/library/string.html)
[http://docs.python.org/2/library/xml.etree.elementtree.html](http://docs.python.org/2/library/xml.etree.elementtree.html)
and you are golden ;-)

---

### Post by GrouchyGaijin on 2013-10-09
I found that they also have an xml file that gives things like sunrise sunset and the phase of the moon.

I see in your code:

```
format = { 'id': f_id, 'template':'', 'fields':[], 'xml':( cxml if 'current' in f_id else fxml ) }
```

How can I change that for three choices? elif?

The astronomy xml file is:
```




<response>
	<version>0.1</version>
	<termsofService>http://www.wunderground.com/weather/api/d/terms.html</termsofService>
	<features>
		<feature>astronomy</feature>
	</features>
		<moon_phase>
		<percentIlluminated>21</percentIlluminated>
		<ageOfMoon>4</ageOfMoon>
		<current_time>
		<hour>7</hour>
		<minute>33</minute>
		</current_time>
		<sunset>
		<hour>18</hour>
		<minute>04</minute>
		</sunset>
		<sunrise>
		<hour>7</hour>
		<minute>23</minute>
		</sunrise>
	</moon_phase>
	<sun_phase>
		<sunset>
		<hour>18</hour>
		<minute>04</minute>
		</sunset>
		<sunrise>
		<hour>7</hour>
		<minute>23</minute>
		</sunrise>
	</sun_phase>
</response>

```

(see [http://www.wunderground.com/weather/api/d/docs?d=data/astronomy&MR=1](http://www.wunderground.com/weather/api/d/docs?d=data/astronomy&MR=1) )

---

### Post by Vaphell on 2013-10-09
on that page the example datasets are in json format, where do you get xmls from? I think they are dumping xml and moving to json, shouldn't you be using that instead? :-)

```

#!/usr/bin/env python

import codecs
import re
import sys
import urllib2
import xml.etree.ElementTree as ET

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
styles = { '[END]'    : '\033[0m',
           '[B]'      : '\033[1m',
           '[RED]'    : '\033[91m',           
           '[GREEN]'  : '\033[92m',
           '[YELLOW]' : '\033[93m',
           '[BLUE]'   : '\033[94m',
           '[MAGENTA]': '\033[95m',
           '[CYAN]'   : '\033[96m' }

field_rgx = r'\{[^:}]*[a-z]+[^:}]*[:}]'

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def moon_phase( x ):
    phases = [ 'New Moon', 'Waxing Crescent', 'First Quarter', 'Waxing Gibbous', 'Full Moon', 'Waning Gibbous', 'Third Quarter', 'Waning Crescent' ]
    i = int(x)
    if   i==0:  idx=0
    elif i<7:   idx=1
    elif i==7:  idx=2
    elif i<14:  idx=3
    elif i==14: idx=4
    elif i<21:  idx=5
    elif i==21: idx=6
    else:       idx=7 
    return phases[idx]

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )


def get_fun( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    elif 'ageOfMoon' in name:  return moon_phase( val )
    else:                      return val



# load data  
xmls = {} 
data = []     
for ln in codecs.open( 'weather_format.txt', 'r', 'utf-8' ):
    ln = ln.rstrip()
    if ln.startswith('!'):
        xmlname, xmlpath = ln.lstrip('! ').split(':')
        if not xmlname in xmls:
            xmls[xmlname] = ET.fromstring( open( xmlname, 'r' ).read() )
        format = { 'path': xmlpath, 'template':'', 'fields':[], 'xml': xmls[xmlname] }
        data.append( format )
    elif ln.startswith('#'): 
        continue
    else:
        format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
        format['fields'] += [ x.strip('{}:') for x in re.findall( field_rgx, ln ) ]

# output
for d in data:
    for s in styles:
        d['template'] = d['template'].replace( s, styles[s] )
    for node in d['xml'].findall( d['path'] ):
        print d['template'].format( **dict( ( i, get_fun( i, node.findtext( './/'+str(i) ).strip() ) ) for i in d['fields'] ) )



```

script doesn't guess the source file anymore, file is now explicitly mentioned in the cfg [noparse](file:xml_path)[/noparse]
```
# current weather
! current.xml:./current_observation
[CYAN]       Location:[END] [B][GREEN]{display_location/full}[END] [GREEN]({display_location/latitude} {display_location/longitude})[END]
[CYAN]Weather station:[END] [B][GREEN]{observation_location/full}[END] [GREEN]({observation_location/latitude} {observation_location/longitude})
[CYAN]           Time:[END] [B][GREEN]{observation_time_rfc822}[END]
[CYAN]     Conditions:[END] [B][YELLOW]{weather}[END]
[CYAN]    Temperature:[END] [B][YELLOW]{temp_c}°C[END], feels like [B][YELLOW]{feelslike_c}°C[END]
[CYAN]           Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
[CYAN]  Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today
[CYAN]       Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
[CYAN]       Humidity:[END] [B][YELLOW]{relative_humidity}[END]
[CYAN]      Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END]
[CYAN]     Visibility:[END] [B][YELLOW]{visibility_km} km[END]
#
#
# astronomy
! astronomy.xml:.
[CYAN]            Sun:[END] [B][YELLOW]{sun_phase/sunrise/hour}:{sun_phase/sunrise/minute}[END] - [B][YELLOW]{sun_phase/sunset/hour}:{sun_phase/sunset/minute}[END]
[CYAN]           Moon:[END] [B][YELLOW]{moon_phase/ageOfMoon} ({moon_phase/percentIlluminated}%)[END]
#
# forecast in text format
#! forecast.xml:./forecast/txt_forecast/forecastdays/forecastday
#[CYAN]{title}:[END]
#  {fcttext_metric}
#
#
# forecast in simple format
! forecast.xml:./forecast/simpleforecast/forecastdays/forecastday
[YELLOW]{weekday}, {date/monthname} {date/day}, {date/year}:[END]
[BLUE]  {conditions}, high {high/celsius}°C, low {low/celsius}°C
  Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]
```

i don't really know what that integer in ageOfMoon field means, my best guess is it's the number of days since the new moon. I couldn't find the exact info what the range of values is and how to map these integers to actual phases. I went with a lame assumption that quarters happen every 7 days even though this calc
[http://www.timeanddate.com/calendar/moonphases.html?year=&n=239](http://www.timeanddate.com/calendar/moonphases.html?year=&n=239) says the whole cycle is 29+days long

It would be very easy to calculate the right value having both age and illumination (let's say if ilumination is within 1% threshold from 0, 50, 100 assume main phases and if age <14 then ..., if >14 then...), but the script works with a single field at a time and doesn't have access to its siblings. I'd have to rethink my approach.

---

### Post by GrouchyGaijin on 2013-10-09
> **Vaphell said:**
> on that page the example datasets are in json format, where do you get xmls from? I think they are dumping xml and moving to json, shouldn't you be using that instead? :-) 

They offer the data in both xml and json formats.  I chose xml simply because the original function this evolved from used xml.
Is there an advantage to using json?
 



> **Vaphell said:**
>  i don't really know what that integer in ageOfMoon field means, my best guess is it's the number of days since the new moon. I couldn't find the exact info what the range of values is and how to map these integers to actual phases. I went with a lame assumption that quarters happen every 7 days even though this calc
[http://www.timeanddate.com/calendar/moonphases.html?year=&n=239](http://www.timeanddate.com/calendar/moonphases.html?year=&n=239) says the whole cycle is 29+days long

It would be very easy to calculate the right value having both age and illumination (let's say if ilumination is within 1% threshold from 0, 50, 100 assume main phases and if age <14 then ..., if >14 then...), but the script works with a single field at a time and doesn't have access to its siblings. I'd have to rethink my approach.

Don't worry about that man.  I just wanted to know how much daylight I'll have.  In the dead of winter we are down to a couple of hours, unless it is cloudy, then forget daylight.

[IMG]https://dl.dropboxusercontent.com/u/23115609/sun-moon.png[/IMG]

---

### Post by Vaphell on 2013-10-09
Looks like too much information already, location doesn't fit in the standard sized terminal window ;-) You should get rid of some unimportant fields or fit 2 in 1 line :-)

I don't think there is much difference, though json is probably more condensed and less readable.
in my playground dir i have some programs that utilize json, so don't think there would be a problem with the transition by copy paste. Care to post some json examples so i can give them a spin? I could register to get the api key but I don't feel like it ;-)

have you tried to load data directly from server?

---

### Post by GrouchyGaijin on 2013-10-09
> **Vaphell said:**
> Looks like too much information already, location doesn't fit in the standard sized terminal window ;-) You should get rid of some unimportant fields or fit 2 in 1 line :-) 

Yeah, I'll tweak it later. Right now, I'm just _*really happy*_ it works.  This is exactly what I wanted.  I loath having to drag my a** out to some website to get the forecast.  I wanted something that I can pull up in the terminal.

> **Vaphell] Care to post some json examples so i can give them a spin? I could register to get the api key but I don't feel like it  said:**
> 

Here they are: Astronomy
```
{
    "response": {
        "version": "0.1"
        ,"termsofService": "http://www.wunderground.com/weather/api/d/terms.html"
        ,"features": {
        "astronomy": 1
        }
    }
        ,    "moon_phase": {
        "percentIlluminated":"27",
        "ageOfMoon":"5",
        "phaseofMoon":"Waxing Crescent",
        "current_time": {
        "hour":"22",
        "minute":"18"
        },
        "sunrise": {
        "hour":"7",
        "minute":"23"
        },
        "sunset": {
        "hour":"18",
        "minute":"04"
        }
    },
    "sun_phase": {
        "sunrise": {
        "hour":"7",
        "minute":"23"
        },
        "sunset": {
        "hour":"18",
        "minute":"04"
        }
    }
}

```

Current
```



{
    "response": {
        "version": "0.1"
        ,"termsofService": "http://www.wunderground.com/weather/api/d/terms.html"
        ,"features": {
        "conditions": 1
        }
    }
        ,    "current_observation": {
        "image": {
        "url":"http://icons-ak.wxug.com/graphics/wu2/logo_130x80.png",
        "title":"Weather Underground",
        "link":"http://www.wunderground.com"
        },
        "display_location": {
        "full":"Falun, Sweden",
        "city":"Falun",
        "state":"",
        "state_name":"Sweden",
        "country":"SN",
        "country_iso3166":"SE",
        "zip":"00000",
        "magic":"6",
        "wmo":"02435",
        "latitude":"60.59999847",
        "longitude":"15.63333321",
        "elevation":"116.00000000"
        },
        "observation_location": {
        "full":"Kämparvet, Falun, DALARNA",
        "city":"Kämparvet, Falun",
        "state":"DALARNA",
        "country":"SWEDEN",
        "country_iso3166":"SE",
        "latitude":"60.606194",
        "longitude":"15.639073",
        "elevation":"50 ft"
        },
        "estimated": {
        },
        "station_id":"IDALARNA23",
        "observation_time":"Last Updated on October 9, 10:17 PM CEST",
        "observation_time_rfc822":"Wed, 09 Oct 2013 22:17:53 +0200",
        "observation_epoch":"1381349873",
        "local_time_rfc822":"Wed, 09 Oct 2013 22:17:56 +0200",
        "local_epoch":"1381349876",
        "local_tz_short":"CEST",
        "local_tz_long":"Europe/Stockholm",
        "local_tz_offset":"+0200",
        "weather":"Partly Cloudy",
        "temperature_string":"47.5 F (8.6 C)",
        "temp_f":47.5,
        "temp_c":8.6,
        "relative_humidity":"94%",
        "wind_string":"Calm",
        "wind_dir":"East",
        "wind_degrees":90,
        "wind_mph":0.0,
        "wind_gust_mph":0,
        "wind_kph":0.0,
        "wind_gust_kph":0,
        "pressure_mb":"1001",
        "pressure_in":"29.56",
        "pressure_trend":"0",
        "dewpoint_string":"46 F (8 C)",
        "dewpoint_f":46,
        "dewpoint_c":8,
        "heat_index_string":"NA",
        "heat_index_f":"NA",
        "heat_index_c":"NA",
        "windchill_string":"48 F (9 C)",
        "windchill_f":"48",
        "windchill_c":"9",
        "feelslike_string":"48 F (9 C)",
        "feelslike_f":"48",
        "feelslike_c":"9",
        "visibility_mi":"6.2",
        "visibility_km":"10.0",
        "solarradiation":"--",
        "UV":"0","precip_1hr_string":"0.00 in ( 0 mm)",
        "precip_1hr_in":"0.00",
        "precip_1hr_metric":" 0",
        "precip_today_string":"0.00 in (0 mm)",
        "precip_today_in":"0.00",
        "precip_today_metric":"0",
        "icon":"partlycloudy",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/nt_partlycloudy.gif",
        "forecast_url":"http://www.wunderground.com/global/stations/02435.html",
        "history_url":"http://www.wunderground.com/weatherstation/WXDailyHistory.asp?ID=IDALARNA23",
        "ob_url":"http://www.wunderground.com/cgi-bin/findweather/getForecast?query=60.606194,15.639073"
    }
}



```

Forecast
```



{
    "response": {
        "version": "0.1"
        ,"termsofService": "http://www.wunderground.com/weather/api/d/terms.html"
        ,"features": {
        "forecast": 1
        }
    }
        ,
    "forecast":{
        "txt_forecast": {
        "date":"2:00 PM CEST",
        "forecastday": [
        {
        "period":0,
        "icon":"mostlycloudy",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/mostlycloudy.gif",
        "title":"Wednesday",
        "fcttext":"Mostly cloudy in the morning, then overcast. High of 59F. Winds from the SW at 5 to 15 mph.",
        "fcttext_metric":"Mostly cloudy in the morning, then overcast. High of 15C. Breezy. Winds from the SW at 10 to 20 km/h.",
        "pop":"0"
        }
        ,
        {
        "period":1,
        "icon":"chancerain",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/chancerain.gif",
        "title":"Wednesday Night",
        "fcttext":"Overcast with a chance of rain after midnight. Low of 39F. Winds from the SW at 5 to 10 mph shifting to the NNE after midnight. Chance of rain 50%.",
        "fcttext_metric":"Overcast with a chance of rain after midnight. Low of 4C. Winds from the SW at 5 to 20 km/h shifting to the NNE after midnight. Chance of rain 50%.",
        "pop":"50"
        }
        ,
        {
        "period":2,
        "icon":"rain",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/rain.gif",
        "title":"Thursday",
        "fcttext":"Overcast with rain, then a chance of rain in the afternoon. High of 48F. Winds from the NNE at 5 to 10 mph. Chance of rain 80%.",
        "fcttext_metric":"Overcast with rain, then a chance of rain in the afternoon. High of 9C. Winds from the NNE at 10 to 15 km/h. Chance of rain 80%.",
        "pop":"80"
        }
        ,
        {
        "period":3,
        "icon":"clear",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/clear.gif",
        "title":"Thursday Night",
        "fcttext":"Clear in the evening, then overcast. Low of 32F. Winds from the NNW at 5 to 10 mph.",
        "fcttext_metric":"Clear in the evening, then overcast. Low of 0C. Winds from the NNW at 10 to 15 km/h.",
        "pop":"0"
        }
        ,
        {
        "period":4,
        "icon":"partlycloudy",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/partlycloudy.gif",
        "title":"Friday",
        "fcttext":"Mostly cloudy. High of 54F. Winds less than 5 mph.",
        "fcttext_metric":"Mostly cloudy. High of 12C. Winds less than 5 km/h.",
        "pop":"0"
        }
        ,
        {
        "period":5,
        "icon":"clear",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/clear.gif",
        "title":"Friday Night",
        "fcttext":"Clear. Low of 36F. Winds less than 5 mph.",
        "fcttext_metric":"Clear. Low of 2C. Winds less than 5 km/h.",
        "pop":"0"
        }
        ,
        {
        "period":6,
        "icon":"partlycloudy",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/partlycloudy.gif",
        "title":"Saturday",
        "fcttext":"Partly cloudy. High of 57F. Winds less than 5 mph.",
        "fcttext_metric":"Partly cloudy. High of 14C. Winds less than 5 km/h.",
        "pop":"0"
        }
        ,
        {
        "period":7,
        "icon":"clear",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/clear.gif",
        "title":"Saturday Night",
        "fcttext":"Clear. Low of 37F. Winds less than 5 mph.",
        "fcttext_metric":"Clear. Low of 3C. Winds less than 5 km/h.",
        "pop":"0"
        }
        ]
        },
        "simpleforecast": {
        "forecastday": [
        {"date":{
    "epoch":"1381352400",
    "pretty":"11:00 PM CEST on October 09, 2013",
    "day":9,
    "month":10,
    "year":2013,
    "yday":281,
    "hour":23,
    "min":"00",
    "sec":0,
    "isdst":"1",
    "monthname":"October",
    "weekday_short":"Wed",
    "weekday":"Wednesday",
    "ampm":"PM",
    "tz_short":"CEST",
    "tz_long":"Europe/Stockholm"
},
        "period":1,
        "high": {
        "fahrenheit":"59",
        "celsius":"15"
        },
        "low": {
        "fahrenheit":"39",
        "celsius":"4"
        },
        "conditions":"Mostly Cloudy",
        "icon":"mostlycloudy",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/mostlycloudy.gif",
        "skyicon":"mostlycloudy",
        "pop":0,
        "qpf_allday": {
        "in": 0.01,
        "mm": 0.3
        },
        "qpf_day": {
        "in": 0.00,
        "mm": 0.0
        },
        "qpf_night": {
        "in": 0.14,
        "mm": 3.6
        },
        "snow_allday": {
        "in": 0,
        "cm": 0
        },
        "snow_day": {
        "in": 0,
        "cm": 0
        },
        "snow_night": {
        "in": 0,
        "cm": 0
        },
        "maxwind": {
        "mph": 11,
        "kph": 18,
        "dir": "WSW",
        "degrees": 237
        },
        "avewind": {
        "mph": 7,
        "kph": 11,
        "dir": "SW",
        "degrees": 233
        },
        "avehumidity": 79,
        "maxhumidity": 98,
        "minhumidity": 68
        }
        ,
        {"date":{
    "epoch":"1381438800",
    "pretty":"11:00 PM CEST on October 10, 2013",
    "day":10,
    "month":10,
    "year":2013,
    "yday":282,
    "hour":23,
    "min":"00",
    "sec":0,
    "isdst":"1",
    "monthname":"October",
    "weekday_short":"Thu",
    "weekday":"Thursday",
    "ampm":"PM",
    "tz_short":"CEST",
    "tz_long":"Europe/Stockholm"
},
        "period":2,
        "high": {
        "fahrenheit":"48",
        "celsius":"9"
        },
        "low": {
        "fahrenheit":"32",
        "celsius":"0"
        },
        "conditions":"Rain",
        "icon":"rain",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/rain.gif",
        "skyicon":"partlycloudy",
        "pop":80,
        "qpf_allday": {
        "in": 0.26,
        "mm": 6.6
        },
        "qpf_day": {
        "in": 0.13,
        "mm": 3.3
        },
        "qpf_night": {
        "in": 0.00,
        "mm": 0.0
        },
        "snow_allday": {
        "in": 0,
        "cm": 0
        },
        "snow_day": {
        "in": 0,
        "cm": 0
        },
        "snow_night": {
        "in": 0,
        "cm": 0
        },
        "maxwind": {
        "mph": 10,
        "kph": 16,
        "dir": "NNE",
        "degrees": 29
        },
        "avewind": {
        "mph": 7,
        "kph": 11,
        "dir": "NNE",
        "degrees": 14
        },
        "avehumidity": 78,
        "maxhumidity": 90,
        "minhumidity": 69
        }
        ,
        {"date":{
    "epoch":"1381525200",
    "pretty":"11:00 PM CEST on October 11, 2013",
    "day":11,
    "month":10,
    "year":2013,
    "yday":283,
    "hour":23,
    "min":"00",
    "sec":0,
    "isdst":"1",
    "monthname":"October",
    "weekday_short":"Fri",
    "weekday":"Friday",
    "ampm":"PM",
    "tz_short":"CEST",
    "tz_long":"Europe/Stockholm"
},
        "period":3,
        "high": {
        "fahrenheit":"54",
        "celsius":"12"
        },
        "low": {
        "fahrenheit":"36",
        "celsius":"2"
        },
        "conditions":"Partly Cloudy",
        "icon":"partlycloudy",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/partlycloudy.gif",
        "skyicon":"partlycloudy",
        "pop":0,
        "qpf_allday": {
        "in": 0.00,
        "mm": 0.0
        },
        "qpf_day": {
        "in": 0.00,
        "mm": 0.0
        },
        "qpf_night": {
        "in": 0.00,
        "mm": 0.0
        },
        "snow_allday": {
        "in": 0,
        "cm": 0
        },
        "snow_day": {
        "in": 0,
        "cm": 0
        },
        "snow_night": {
        "in": 0,
        "cm": 0
        },
        "maxwind": {
        "mph": 6,
        "kph": 10,
        "dir": "WNW",
        "degrees": 286
        },
        "avewind": {
        "mph": 5,
        "kph": 8,
        "dir": "WNW",
        "degrees": 291
        },
        "avehumidity": 70,
        "maxhumidity": 88,
        "minhumidity": 56
        }
        ,
        {"date":{
    "epoch":"1381611600",
    "pretty":"11:00 PM CEST on October 12, 2013",
    "day":12,
    "month":10,
    "year":2013,
    "yday":284,
    "hour":23,
    "min":"00",
    "sec":0,
    "isdst":"1",
    "monthname":"October",
    "weekday_short":"Sat",
    "weekday":"Saturday",
    "ampm":"PM",
    "tz_short":"CEST",
    "tz_long":"Europe/Stockholm"
},
        "period":4,
        "high": {
        "fahrenheit":"57",
        "celsius":"14"
        },
        "low": {
        "fahrenheit":"37",
        "celsius":"3"
        },
        "conditions":"Partly Cloudy",
        "icon":"partlycloudy",
        "icon_url":"http://icons-ak.wxug.com/i/c/k/partlycloudy.gif",
        "skyicon":"partlycloudy",
        "pop":0,
        "qpf_allday": {
        "in": 0.00,
        "mm": 0.0
        },
        "qpf_day": {
        "in": 0.00,
        "mm": 0.0
        },
        "qpf_night": {
        "in": 0.00,
        "mm": 0.0
        },
        "snow_allday": {
        "in": 0,
        "cm": 0
        },
        "snow_day": {
        "in": 0,
        "cm": 0
        },
        "snow_night": {
        "in": 0,
        "cm": 0
        },
        "maxwind": {
        "mph": 4,
        "kph": 6,
        "dir": "WNW",
        "degrees": 299
        },
        "avewind": {
        "mph": 3,
        "kph": 5,
        "dir": "NNW",
        "degrees": 340
        },
        "avehumidity": 80,
        "maxhumidity": 90,
        "minhumidity": 62
        }
        ]
        }
    }
}



```


[QUOTE=Vaphell] Have you tried to load data directly from server?
Actually, since we started using more than one xml file.  I haven't been able to get it to work when I tried to have the script pull the data from their server.

---

### Post by drmrgd on 2013-10-09
> **Vaphell said:**
>  <snip>

have you tried to load data directly from server?

As a learning exercise (plus I think this is pretty dang cool!) I've been trying to get it to work with a direct server query too.  Unfortunately, I don't know Python very well at all (yet...just bought a book and I'm planning to start now), and so I can't quite figure it out.  If I pull the XMLs with curl and then push them to the script, no problem.  If I try to directly pull it from the server, though, I get:

```

Traceback (most recent call last):
  File "weather.py", line 76, in <module>
    for node in d['xml'].findall( d['id'] ):
AttributeError: 'str' object has no attribute 'findall'

```

I set up two variables with the URLs for the current and and forecast xmls:

```

current_url = "http://api.wunderground.com/api/<my_key>/conditions/q/MD/Frederick.xml"
forecast_url = "http://api.wunderground.com/api/<my_key>/forecast/q/MD/Frederick.xml"

```

Then I changed the lines for the 'cxml' and 'fxml' variables as such:

```

cxml = urllib2.urlopen(urllib2.Request(current_url)).read()
fxml = urllib2.urlopen(urllib2.Request(forecast_url)).read()

```

but I seem to be getting the following error no matter what I try:

Traceback (most recent call last):
  File "weather.py", line 76, in <module>
    for node in d['xml'].findall( d['id'] ):
AttributeError: 'str' object has no attribute 'findall'

[/code]

I know the URLs work.  I just think I'm not reading in the XML correctly, and I can't seem to figure out how. [COLOR=#000000]GrouchyGaijin might be seeing the same error?  Are we parsing the XML from the server correctly?  I tried a couple different variations on that call, but can't quite get it right.


[/COLOR]

---

### Post by Vaphell on 2013-10-09
with that you get only raw data, you still need to parse it with some Etree function (ET.fromstring(string) or ET.parse(filehandler)) to generate a tree of python objects
[http://docs.python.org/2/library/xml.etree.elementtree.html](http://docs.python.org/2/library/xml.etree.elementtree.html)

json stuff
```
#!/usr/bin/env python

import codecs
import re
import urllib2
import json

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
styles = { '[END]'    : '\033[0m',
           '[B]'      : '\033[1m',
           '[RED]'    : '\033[91m',           
           '[GREEN]'  : '\033[92m',
           '[YELLOW]' : '\033[93m',
           '[BLUE]'   : '\033[94m',
           '[MAGENTA]': '\033[95m',
           '[CYAN]'   : '\033[96m' }

field_rgx = r'\{[^:}]*[a-z]+[^:}]*[:}]'

# function to get nodes/values from the data tree
def get( start, path ):
    n = start
    path = path.split('/')
    for p in path:
        if len(p)==0: continue
        n = n[p]
    if isinstance( n, dict ): return [n]
    return n

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )

def fix( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    else:                      return val


# load data  
json_data = {} 
print_data = []     
for ln in codecs.open( 'weather_format.txt', 'r', 'utf-8' ):
    ln = ln.rstrip()
    if ln.startswith('!'):
        jname, jpath = ln.lstrip('! ').split('#')
        if not jname in json_data:
            json_data[jname] = json.load( urllib2.urlopen( urllib2.Request( jname ) ) )
        format = { 'path': jpath.replace( '.', '/' ), 'template':'', 'fields':[], 'src': json_data[jname] }
        print_data.append( format )
    elif ln.startswith('#'): 
        continue
    else:
        format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
        format['fields'] += [ x.strip('{}').replace('.', '/') for x in re.findall( field_rgx, ln ) ]

for d in print_data:
    for s in styles:
        d['template'] = d['template'].replace( s, styles[s] )
    for n in get( d['src'], d['path'] ):
        print d['template'].format(**dict( (k, fix( k, get(n,k))) for k in d['fields'] ) )
```


```

# template headers that start with ! have 2 parts separated by #:
#    - file url, path to data in the tree
#    - path to data
#
# current weather
#-------------------------------------------------------------------------------------------------
! file:///home/me/test/json_weather/current.json#current_observation
#-------------------------------------------------------------------------------------------------
[CYAN]       Location:[END] [B][GREEN]{display_location/full}[END] [GREEN]({display_location/latitude} {display_location/longitude})[END]
[CYAN]Weather station:[END] [B][GREEN]{observation_location/full}[END] [GREEN]({observation_location/latitude} {observation_location/longitude})
[CYAN]           Time:[END] [B][GREEN]{observation_time_rfc822}[END]
[CYAN]     Conditions:[END] [B][YELLOW]{weather}[END]
[CYAN]    Temperature:[END] [B][YELLOW]{temp_c}°C[END], feels like [B][YELLOW]{feelslike_c}°C[END]
[CYAN]           Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
[CYAN]  Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today
[CYAN]       Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
[CYAN]       Humidity:[END] [B][YELLOW]{relative_humidity}[END]
[CYAN]      Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END]
[CYAN]     Visibility:[END] [B][YELLOW]{visibility_km} km[END]
#
#
# astronomy
#-------------------------------------------------------------------------------------------------
! file:///home/me/test/json_weather/astronomy.json#
#-------------------------------------------------------------------------------------------------
[CYAN]            Sun:[END] [B][YELLOW]{sun_phase/sunrise/hour}:{sun_phase/sunrise/minute}[END] - [B][YELLOW]{sun_phase/sunset/hour}:{sun_phase/sunset/minute}[END]
[CYAN]           Moon:[END] [B][YELLOW]{moon_phase/phaseofMoon} ({moon_phase/percentIlluminated}%)[END]         
#
# forecast in text format
#-------------------------------------------------------------------------------------------------
#! file:///home/me/test/json_weather/forecast.json#forecast/txt_forecast/forecastday
#-------------------------------------------------------------------------------------------------
#[CYAN]{title}:[END]
#  {fcttext_metric}
#
#
# forecast in simple format
#-------------------------------------------------------------------------------------------------
! file:///home/me/test/json_weather/forecast.json#forecast/simpleforecast/forecastday
#-------------------------------------------------------------------------------------------------
[YELLOW]{date/weekday}, {date/monthname} {date/day}, {date/year}:[END]
 [BLUE]  {conditions}, high {high/celsius}°C, low {low/celsius}°C
   Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]
```

So i went with file:// format of file paths in the cfg to test if the urllib2 business would work, which would mean the direct dl from server is very likely too. It works just fine on local files.
I also changed the separator of the ! line from : to # because : is rather frequent in urls (eg http: ) and # is a legit char for separating file handlers from internal ids so i went with that


in case there is a common core of the urls and i bet there is, it would be ok to go with something like this
```
urlcore = 'file:///home/me/test/json_weather/'  # core part of the url

  ... urllib2.Request( urlcore+jname ) ...
```

and have only url tails in the cfg file, eg
```
! apikey/*/forecast.json#forecast/simpleforecast/forecastday
```

---

### Post by GrouchyGaijin on 2013-10-10
I am doing something wrong.

I changed the file path in the weather_format.txt to

```

# current weather
! http://api.wunderground.com/api/<my_key>/conditions/q/Sweden/Falun.xml:./current_observation

```

but then when I run the script I get:
```

Traceback (most recent call last):
  File "/home/john/scripts/falun-weather/falun-weather.py", line 62, in <module>
    xmlname, xmlpath = ln.lstrip('! ').split(':')
ValueError: too many values to unpack




```

---

### Post by Vaphell on 2013-10-10
as i said near the jsons, full urls with : collide with the old separator ( *split(':')* returns 3 values but there are only 2 variables for them) and i changed it to #
that means *.split('#')* is required


that said, try json files, they seem to be more complete, eg astronomy has a legit data field for the moon phase that is simply missing in xml

---

### Post by GrouchyGaijin on 2013-10-10
Hmmmm

```

! http://api.wunderground.com/api/<my_key>/conditions/q/Sweden/Falun.xml#./current_observation
! http://api.wunderground.com/api/<my_key>/astronomy/q/Sweden/Falun.xml#.
! http://api.wunderground.com/api/<my_key>/forecast/q/Sweden/Falun.xml#./forecast/simpleforecast/forecastdays/forecastday

```

Returns this error:
```

Traceback (most recent call last):
  File "/home/john/scripts/falun-weather/falun-weather.py", line 64, in <module>
    xmls[xmlname] = ET.fromstring( open( xmlname, 'r' ).read() )
IOError: [Errno 2] No such file or directory: u'http'

```

Did I put the # in the wrong place?

---

### Post by Vaphell on 2013-10-10
open( name, mode ) is strictly for local files and you try to push url as name. You need to go the urllib2 way for that.



try this one (json again, haven't looked in xmls for some time)
```

#!/usr/bin/env python

import codecs
import re
import urllib2
import json

#url = { 'url': 'file:///home/me/test/json_weather/{key}/{dataset}/q/{country}/{city}.json' }
[COLOR="#0000FF"]url = { 'url': 'http://api.wunderground.com/api/{key}/q/{dataset}/{country}/{city}.json' }[/COLOR]

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
styles = { '[END]'    : '\033[0m',
           '[B]'      : '\033[1m',
           '[RED]'    : '\033[91m',           
           '[GREEN]'  : '\033[92m',
           '[YELLOW]' : '\033[93m',
           '[BLUE]'   : '\033[94m',
           '[MAGENTA]': '\033[95m',
           '[CYAN]'   : '\033[96m' }

field_rgx = r'\{[^:}]*[a-z]+[^:}]*[:}]'

# function to get nodes/values from the data tree
def get( start, path ):
    n = start
    path = path.split('/')
#    print n, path
    for p in path:
        if len(p)==0: continue
        n = n[p]
    if isinstance( n, dict ): return [n]
    return n

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )

def fix( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    else:                      return val


# load data  
json_data = {} 
print_data = []     
for ln in codecs.open( 'weather_format.txt', 'r', 'utf-8' ):
    ln = ln.rstrip()
    if ln.startswith('#'): 
        continue
    if ln.startswith('@'):
        url['key'], url['country'], url['city'] = ( x.strip() for x in ln.lstrip('@ ').split(',') )
    elif ln.startswith('!'):
        jname, jpath = ln.lstrip('! ').split('#')
        if not jname in json_data:
            json_data[jname] = json.load( urllib2.urlopen( urllib2.Request( url['url'].format( dataset=jname, **url ) ) ) )
        format = { 'path': jpath.replace( '.', '/' ), 'template':'', 'fields':[], 'src': json_data[jname] }
        print_data.append( format )
    else:
        format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
        format['fields'] += [ x.strip('{}') for x in re.findall( field_rgx, ln ) ]

for d in print_data:
    for s in styles:
        d['template'] = d['template'].replace( s, styles[s] )
    for n in get( d['src'], d['path'] ):
        print d['template'].format(**dict( (k, fix( k, get(n,k))) for k in d['fields'] ) )


```

cfg
```

# @ KEY, COUNTRY, CITY
[COLOR="#0000FF"]@ 12345, Sweden, Falun[/COLOR]
#
# template headers that start with ! have 2 parts separated by #:
#    - file url, path to data in the tree
#    - path to data
#
# current weather
#-------------------------------------------------------------------------------------------------
! [COLOR="#0000FF"]conditions[/COLOR]#current_observation
#-------------------------------------------------------------------------------------------------
[CYAN]       Location:[END] [B][GREEN]{display_location/full}[END] [GREEN]({display_location/latitude} {display_location/longitude})[END]
[CYAN]Weather station:[END] [B][GREEN]{observation_location/full}[END] [GREEN]({observation_location/latitude} {observation_location/longitude})
[CYAN]           Time:[END] [B][GREEN]{observation_time_rfc822}[END]
[CYAN]     Conditions:[END] [B][YELLOW]{weather}[END]
[CYAN]    Temperature:[END] [B][YELLOW]{temp_c}°C[END], feels like [B][YELLOW]{feelslike_c}°C[END]
[CYAN]           Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
[CYAN]  Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today
[CYAN]       Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
[CYAN]       Humidity:[END] [B][YELLOW]{relative_humidity}[END]
[CYAN]      Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END]
[CYAN]     Visibility:[END] [B][YELLOW]{visibility_km} km[END]
#
#
# astronomy
#-------------------------------------------------------------------------------------------------
! [COLOR="#0000FF"]astronomy[/COLOR]#
#-------------------------------------------------------------------------------------------------
[CYAN]            Sun:[END] [B][YELLOW]{sun_phase/sunrise/hour}:{sun_phase/sunrise/minute}[END] - [B][YELLOW]{sun_phase/sunset/hour}:{sun_phase/sunset/minute}[END]
[CYAN]           Moon:[END] [B][YELLOW]{moon_phase/phaseofMoon} ({moon_phase/percentIlluminated}%)[END]         
#
# forecast in text format
#! forecast#forecast/simpleforecast/forecastday
#[CYAN]{title}:[END]
#  {fcttext_metric}
#
#
# forecast in simple format
#-------------------------------------------------------------------------------------------------
! [COLOR="#0000FF"]forecast[/COLOR]#forecast/simpleforecast/forecastday
#-------------------------------------------------------------------------------------------------
[YELLOW]{date/weekday}, {date/monthname} {date/day}, {date/year}:[END]
 [BLUE]  {conditions}, high {high/celsius}°C, low {low/celsius}°C
   Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]


```
in this version i can easily switch between local files and remote ones because a single string controls that (in blue). Local files are in 12345/{conditions,forecast,astronomy}/q/Sweden (Falun.json). I expect remote ones to work just fine as well.

In the cfg file i moved key,country and city to yet another header line, this time marked with @. Old headers keep only the name of the dataset as in (astronomy, conditions, forecast)

---

### Post by drmrgd on 2013-10-10
This is pretty close, but I'm seeing a format issue with the return data that I can't get around.  First, I'm getting the following error with the new script:

```

Traceback (most recent call last):
  File "./weather.py", line 75, in <module>
    for n in get( d['src'], d['path'] ):
  File "./weather.py", line 30, in get
    n = n[p]
KeyError: u'current_observation'

```

So, it looks like the data's being handled as unicode text.  To confirm, i added the following lines to the loop just after you load in the JSON data:

```

if not jname in json_data:
            json_data[str(jname)] = json.load( urllib2.urlopen( urllib2.Request( url['url'].format( dataset=jname, **url ) ) ) )
            print json_data[jname]
            sys.exit()

```

and the results look like they're all unicode strings, which is (I think) why they're not getting parsed correctly.  I can't figure out how to convert them to strings that can be looked up in the dict, though.  Maybe I'm not right and it's something else, though.

---

### Post by Vaphell on 2013-10-10
do you have proper api key? without it you won't dl correct data and most likely you get something like this instead
```
{u'response': {u'termsofService': u'http://www.wunderground.com/weather/api/d/terms.html', u'version': u'0.1', u'features': {}, u'error': {u'type': u'keynotfound', u'description': u'this key does not exist'}}}
```
there is no current_observation on the first level so key error
in case of success *print json_data[jname]* should return a huge dict of dicts

Does it work for you with local dummy files and the url in file:///local/path/... format?

---

### Post by drmrgd on 2013-10-10
Yes, I have the API key and I'm getting the correct JSON return data.  I've hacking away at this and it doesn't have anything to do with the unicode issue that I thought.  It's definitely chocking on the 'current_observation' key in the 'get' function.  

I loaded up pprint and had a look at the return data from the API.  This is what I'm seeing:

```

[{'fields': [u'display_location/full',
             u'display_location/latitude',
             u'display_location/longitude',
             u'observation_location/full',
             u'observation_location/latitude',
             u'observation_location/longitude',
             u'observation_time_rfc822',
             u'weather',
             u'temp_c',
             u'feelslike_c',
             u'wind_kph',
             u'wind_dir',
             u'precip_1hr_metric',
             u'precip_today_metric',
             u'pressure_mb',
             u'relative_humidity',
             u'dewpoint_c',
             u'visibility_km'],
  'path': u'current_observation',
  'src': {u'response': {u'features': {},
                        u'results': [{u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:80504.3.99999',
                                      u'name': u'Frederick',
                                      u'state': u'CO',
                                      u'zmw': u'80504.3.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:62639.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'IL',
                                      u'zmw': u'62639.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:21701.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'MD',
                                      u'zmw': u'21701.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:73542.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'OK',
                                      u'zmw': u'73542.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:19435.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'PA',
                                      u'zmw': u'19435.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:57441.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'SD',
                                      u'zmw': u'57441.1.99999'}],
                        u'termsofService': u'http://www.wunderground.com/weather/api/d/terms.html',
                        u'version': u'0.1'}},
  'template': u'[CYAN]       Location:[END] [B][GREEN]{display_location/full}[END] [GREEN]({display_location/latitude} {display_location/longitude})[END]\n[CYAN]Weather station:[END] [B][GREEN]{observation_location/full}[END] [GREEN]({observation_location/latitude} {observation_location/longitude})\n[CYAN]           Time:[END] [B][GREEN]{observation_time_rfc822}[END]\n[CYAN]     Conditions:[END] [B][YELLOW]{weather}[END]\n[CYAN]    Temperature:[END] [B][YELLOW]{temp_c}\xb0C[END], feels like [B][YELLOW]{feelslike_c}\xb0C[END]\n[CYAN]           Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}\n[CYAN]  Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today\n[CYAN]       Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]\n[CYAN]       Humidity:[END] [B][YELLOW]{relative_humidity}[END]\n[CYAN]      Dew point:[END] [B][YELLOW]{dewpoint_c}\xb0C[END]\n[CYAN]     Visibility:[END] [B][YELLOW]{visibility_km} km[END]'},
 {'fields': [u'sun_phase/sunrise/hour',
             u'sun_phase/sunrise/minute',
             u'sun_phase/sunset/hour',
             u'sun_phase/sunset/minute',
             u'moon_phase/phaseofMoon',
             u'moon_phase/percentIlluminated'],
  'path': u'',
  'src': {u'response': {u'features': {},
                        u'results': [{u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:80504.3.99999',
                                      u'name': u'Frederick',
                                      u'state': u'CO',
                                      u'zmw': u'80504.3.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:62639.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'IL',
                                      u'zmw': u'62639.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:21701.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'MD',
                                      u'zmw': u'21701.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:73542.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'OK',
                                      u'zmw': u'73542.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:19435.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'PA',
                                      u'zmw': u'19435.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:57441.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'SD',
                                      u'zmw': u'57441.1.99999'}],
                        u'termsofService': u'http://www.wunderground.com/weather/api/d/terms.html',
                        u'version': u'0.1'}},
  'template': u'[CYAN]            Sun:[END] [B][YELLOW]{sun_phase/sunrise/hour}:{sun_phase/sunrise/minute}[END] - [B][YELLOW]{sun_phase/sunset/hour}:{sun_phase/sunset/minute}[END]\n[CYAN]           Moon:[END] [B][YELLOW]{moon_phase/phaseofMoon} ({moon_phase/percentIlluminated}%)[END]'},
 {'fields': [u'date/weekday',
             u'date/monthname',
             u'date/day',
             u'date/year',
             u'conditions',
             u'high/celsius',
             u'low/celsius',
             u'avewind/kph',
             u'avewind/dir',
             u'maxwind/kph'],
  'path': u'forecast/simpleforecast/forecastday',
  'src': {u'response': {u'features': {},
                        u'results': [{u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:80504.3.99999',
                                      u'name': u'Frederick',
                                      u'state': u'CO',
                                      u'zmw': u'80504.3.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:62639.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'IL',
                                      u'zmw': u'62639.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:21701.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'MD',
                                      u'zmw': u'21701.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:73542.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'OK',
                                      u'zmw': u'73542.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:19435.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'PA',
                                      u'zmw': u'19435.1.99999'},
                                     {u'city': u'Frederick',
                                      u'country': u'US',
                                      u'country_iso3166': u'US',
                                      u'country_name': u'USA',
                                      u'l': u'/q/zmw:57441.1.99999',
                                      u'name': u'Frederick',
                                      u'state': u'SD',
                                      u'zmw': u'57441.1.99999'}],
                        u'termsofService': u'http://www.wunderground.com/weather/api/d/terms.html',
                        u'version': u'0.1'}},
  'template': u'[YELLOW]{date/weekday}, {date/monthname} {date/day}, {date/year}:[END]\n [BLUE]  {conditions}, high {high/celsius}\xb0C, low {low/celsius}\xb0C\n   Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]'}]

```

Have to head off to work and won't be able to play with this for a while today.  Hope this info is helpful!

---

### Post by Vaphell on 2013-10-10
i think your data breaks the script because you have ambiguous criteria, judging by all these Fredericks. Try Frederick, MD instead of Frederick, US.

---

### Post by GrouchyGaijin on 2013-10-10
I get the same error.
In the config file I have:
```

# @ KEY, COUNTRY, CITY
@ <my_key>, Sweden, Falun

```

The output is:
```
KeyError: u'current_observation'
```

---

### Post by Vaphell on 2013-10-10
>_<
maybe you exceeded the quota and get something else? 10 requests/hr is not much

this sounds cool, check this out so we don't waste 3 requests on a single run
[http://www.wunderground.com/weather/api/d/docs?d=data/index](http://www.wunderground.com/weather/api/d/docs?d=data/index)
to do that you are supposed to mash dataset names together like this: 'astronomy/conditions/forecast' :-)


if you manage to produce a query that returns everything in 1 piece paste the data here

by the way it shows the structure of USian and international locations, and then it shows how to remove location ambiguosity with zmw

---

### Post by ian-weisser on 2013-10-10
> **Vaphell said:**
> 10 requests/hr is not much

Great point. Many 'current' weather observations (like METAR reports) update hourly under normal conditions. If you know when the data updates, you can reduce the number of requests.
 
For example, my local stations update data at :52 and :54, and the server updates between :55 and :02. So I pull current data for that station hourly at :05.

Deciphering current conditions from METAR reports, by the way, is available using the *metar* package. It pulls worldwide METARs from US National Weather Service servers (including for ESSD). No api key needed and no download limit. It does not, however, do forecasts, alerts, radar, or satellite images. Just METARs.

---

### Post by GrouchyGaijin on 2013-10-10
Hmmm I waited over an hour before trying to run the script again and still got the same error.  Is it working for you Ian?

Just to be sure:
The py script should have
```

url = { 'url': 'http://api.wunderground.com/api/{key}/q/{dataset}/{country}/{city}.json' }

```
and the weather_format.txt file should have:
```

# @ KEY, COUNTRY, CITY
@ <my_key>, Sweden, Falun

``` at the top of the file and each section should have one of the following:
```

! conditions#current_observation
! astronomy# 
! forecast#forecast/simpleforecast/forecastday

```
is this correct?

---

### Post by Vaphell on 2013-10-10
from what i have read if you exceed the quota you get tempbanned for the rest of the day. Check some valid url in the webbrowser address bar, contents of the file should be shown directly in the browser or dump the file with curl and look at contents.

edit: so i registered, because it becomes slightly annoying :)

---

### Post by GrouchyGaijin on 2013-10-10
I wonder if we are looking at the same page on the weather underground site?

Under my key it list the plan as:

[COLOR=#FFFFFF][FONT=Arial]Your Selected Plan: Cumulus Developer
[/FONT][/COLOR][COLOR=#333333][FONT=Arial][CENTER][COLOR=#F79420]
Monthly Pricing**[/COLOR]
[COLOR=#18599B]$0[/COLOR]


[COLOR=#F79420]Calls Per Day[/COLOR]
[COLOR=#18599B]500[/COLOR]


[COLOR=#F79420]Calls Per Minute[/COLOR]
[COLOR=#18599B]10[/COLOR]


[COLOR=#F79420]+ History[/COLOR]
[COLOR=#18599B]$0[/COLOR]
[/CENTER]


[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][CENTER][COLOR=#F79420]TOTAL[/COLOR]
[COLOR=#18599B]$0 USD per month[/COLOR]
[/CENTER]
[/FONT][/COLOR]






To me this reads 10 requests per minute with a maximum of 500 a day.

---

### Post by Vaphell on 2013-10-10
yeah, i remembered it wrong, but still run the script 4 times in quick succession for whatever reason and poof, 12 requests under 1 minute :-)

so i pulled the data in a single query, now reworking the script :-)

---

### Post by Vaphell on 2013-10-10
ok, this thing works for me with data pulled directly from their server

```

#!/usr/bin/env python

import codecs
import re
import urllib2
import json
import sys

def_url = { 'url': 'http://api.wunderground.com/api/{key}/{dataset}/q/{location}.json' }

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
styles = { '[END]'    : '\033[0m',
           '[B]'      : '\033[1m',
           '[RED]'    : '\033[91m',           
           '[GREEN]'  : '\033[92m',
           '[YELLOW]' : '\033[93m',
           '[BLUE]'   : '\033[94m',
           '[MAGENTA]': '\033[95m',
           '[CYAN]'   : '\033[96m' }

field_rgx = r'\{[^:}]*[a-z]+[^:}]*[:}]'

# show available params
def show_help( args ):
    print args[0]
    print '    --help\tthis help'
    print '    --info\tshows debug info, data structure'

# function showing data tree
def show_struct( x, name, lvl=0, offset=4 ):
    ln = ' '*lvl*offset+'{0}'
    print ln.format( name )
    if isinstance( x, list ):
        show_struct( x[0], '*', lvl=lvl+1 )
    elif isinstance( x, dict ):
        for k in x:
            show_struct( x[k], k, lvl=lvl+1 )

# load json
def load_datafile( url ):
    return json.load( urllib2.urlopen( urllib2.Request( url['url'].format( **url ) ) ) )

# debug/struct info
def dump_info( url, json_data ):
    print 'key: {key}\nlocation: {location}\nurl: {url}\n'. format( **url )
    show_struct( json_data, 'data structure:' )

def parse_header_line( ln, url ):
    for x in ln.lstrip('@ ').split(';')[0:2]:
        k, v = ( i.strip() for i in x.strip().split('=') )
        if k == 'dataset':
            url['dataset'] = '/'.join( i.strip() for i in v.split(',') )
        elif k == 'location':
            url['location'] = v.strip().replace(' ', '%20' )


# function to get nodes/values from the data tree
[COLOR="#4B0082"]def json_get( start, path ):
    n = start
    path = path.split('/')
    for p in path:
        if p: n = n[p]
    if   isinstance( n, dict ):           return [n]
    elif isinstance( n, (str, unicode) ): return n.strip()
    return n[/COLOR]

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )

def fix( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    else:                      return val



# --------- main ---------------------

if __name__ == '__main__':

# settings (--help, --info)
    settings = dict( (k, True) for k in sys.argv[1:] )
    if '--help' in settings:
        show_help( sys.argv )
        sys.exit(0)
        
    url = def_url.copy()
    url['key'] = open( 'api.key' ).read().strip()
      
# load data  
    json_data = {}
    print_data = []     
    for ln in codecs.open( 'weather_format.txt', 'r', 'utf-8' ):
        ln = ln.rstrip()
        if ln.startswith('#'): 
            continue
        if ln.startswith('@'):
            parse_header_line( ln, url )
            json_data = load_datafile( url )
            if '--info' in settings:
                dump_info( url, json_data )
                sys.exit(0)
        elif ln.startswith('!'):
            jpath = ln.lstrip('! ')
            format = { 'path': jpath, 'template':'', 'fields':[], 'src': json_get( json_data, jpath ) }
            print_data.append( format )
        else:
            format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
            format['fields'] += [ x.strip('{}') for x in re.findall( field_rgx, ln ) ]

#    print [ d for d in print_data ]

    for d in print_data:
        for s in styles:
            d['template'] = d['template'].replace( s, styles[s] )
        for n in d['src']:
            print d['template'].format(**dict( (k, fix( k, json_get(n,k))) for k in d['fields'] ) )


```

```
# @ location = ...; dataset = ..., ...,
#     location:
#         - zmw:00000.9.12345 (unamibiguous) <- pick this format
#         - US_STATE_ABBREV/City
#         - Country/City
#
# Falun, Sweden: astronomy, current conditions, forecast
@ location = zmw:00000.6.02435; dataset = astronomy, conditions, forecast
#
# template headers starting with !
# - path to data (empty if pointing to the top level)
#
# current weather
#-------------------------------------------------------------------------------------------------
! current_observation
#-------------------------------------------------------------------------------------------------
[CYAN]       Location:[END] [B][GREEN]{display_location/full}[END] [GREEN]({display_location/latitude} {display_location/longitude})[END]
[CYAN]Weather station:[END] [B][GREEN]{observation_location/full}[END] [GREEN]({observation_location/latitude} {observation_location/longitude})
[CYAN]           Time:[END] [B][GREEN]{observation_time_rfc822}[END]
[CYAN]     Conditions:[END] [B][YELLOW]{weather}[END]
[CYAN]    Temperature:[END] [B][YELLOW]{temp_c}°C[END], feels like [B][YELLOW]{feelslike_c}°C[END]
[CYAN]           Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
[CYAN]  Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today
[CYAN]       Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
[CYAN]       Humidity:[END] [B][YELLOW]{relative_humidity}[END]
[CYAN]      Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END]
[CYAN]     Visibility:[END] [B][YELLOW]{visibility_km} km[END]
#
#
# astronomy (no path because its data is on the top level)
#-------------------------------------------------------------------------------------------------
!
#-------------------------------------------------------------------------------------------------
[CYAN]            Sun:[END] [B][YELLOW]{sun_phase/sunrise/hour}:{sun_phase/sunrise/minute}[END] - [B][YELLOW]{sun_phase/sunset/hour}:{sun_phase/sunset/minute}[END]
[CYAN]           Moon:[END] [B][YELLOW]{moon_phase/phaseofMoon} ({moon_phase/percentIlluminated}%)[END]         
#
# forecast in text format
#! forecast#forecast/simpleforecast/forecastday
#[CYAN]{title}:[END]
#  {fcttext_metric}
#
#
# forecast in simple format
#-------------------------------------------------------------------------------------------------
! forecast/simpleforecast/forecastday
#-------------------------------------------------------------------------------------------------
[YELLOW]{date/weekday}, {date/monthname} {date/day}, {date/year}:[END]
 [BLUE]  {conditions}, high {high/celsius}°C, low {low/celsius}°C
   Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]
```

proof:
```
$ ./weather.py
       Location: Falun, Sweden (60°35'59"N 15°37'59"E)
Weather station: Kämparvet, Falun, DALARNA (60°36'22"N 15°38'20"E)
           Time: Thu, 10 Oct 2013 23:17:44 +0200
     Conditions: Clear
    Temperature: 2.7°C, feels like 3°C
           Wind: 3.7 km/h, from the NNW
  Precipitation:  0 mm in 1hr, 7 mm today
       Pressure: 1023 hPa
       Humidity: 98%
      Dew point: 2°C
     Visibility: 10.0 km
            Sun: 7:25 - 18:01
           Moon: Waxing Crescent (38%)
Thursday, October 10, 2013:
   Overcast, high 11°C, low -1°C
   Winds 13 km/h from the NNE, max 18 km/h
Friday, October 11, 2013:
   Partly Cloudy, high 12°C, low 1°C
   Winds 5 km/h from the WNW, max 8 km/h
Saturday, October 12, 2013:
   Clear, high 17°C, low 1°C
   Winds 5 km/h from the NW, max 8 km/h
Sunday, October 13, 2013:
   Fog, high 16°C, low 1°C
   Winds 5 km/h from the NE, max 6 km/h
```

new stuff:
1. script requires api.key file with the key alone - it should be easier to share templates and configs without exposing the key by accident
2. added parameters: --help which does next to nothing and --info which makes the script print out stuff about the cfg and the data structure (tree of keys).

---

### Post by drmrgd on 2013-10-10
Just getting back; what a long day! I'm not sure why it spit out all of those Fredericks since I put Frederick, MD in the query.  But, I tried your new script, and it works perfectly and is now giving the same output as when I just tried to load the JSON file directly:

```

$ ./weather.py 
       Location: Frederick, MD (39°25'05"N 77°20'10"W)
Weather station: Lake Linganore, New Market, Maryland (39°24'51"N 77°17'54"W)
           Time: Thu, 10 Oct 2013 20:00:10 -0400
     Conditions: Rain
    Temperature: 12.2°C, feels like 12.2°C
           Wind: 0.0 km/h, from the WNW
  Precipitation:  2 mm in 1hr, 47 mm today
       Pressure: 1019 hPa
       Humidity: 95%
      Dew point: 11°C
     Visibility: 11.3 km
            Sun: 7:14 - 18:37
           Moon: Waxing Crescent (39%)
Thursday, October 10, 2013:
   Rain, high 15°C, low 9°C
   Winds 19 km/h from the NNE, max 22 km/h
Friday, October 11, 2013:
   Rain Showers, high 16°C, low 12°C
   Winds 14 km/h from the North, max 16 km/h
Saturday, October 12, 2013:
   Rain, high 17°C, low 12°C
   Winds 10 km/h from the NNE, max 13 km/h
Sunday, October 13, 2013:
   Chance of Rain, high 18°C, low 6°C
   Winds 11 km/h from the NE, max 13 km/h

```

This is very, very cool and I'm very grateful for your hard work!  Also, this is a nice thing for me to study as I start working with Python (although a lot of this is quite a bit over my head at the moment).  Definitely going to spend some time analyzing and studying this example.  The idea of formatting the output from an external file is a new one to me, and I think this might be something that I can find useful later on.

Thanks again for another lesson Vaphell!

**EDIT:** By the way, the zmw string is definitely the way to go!  For anyone else that would like to use this script and get this location string, you can retrieve the string by using their autocomplete service.  One way, is to directly query it and then parse the JSON file it produces.  For me:

```

curl -s "http://autocomplete.wunderground.com/aq?query=Frederick&c=US"

```

This gave me all partial matches with the query I put in and since i had all of the information, it was the first element in the JSON.  More details on this here:

[http://www.wunderground.com/weather/api/d/docs?d=autocomplete-api](http://www.wunderground.com/weather/api/d/docs?d=autocomplete-api)


**Edit2:**
I made one little tweak to your script.  This is something that I would like to have linked in my bin directory so that I can call it from anywhere.  But, it seems that my cwd must be where the script resides or it won't find the api.key or weather_format files.  So, I added a chunk at the top where I can control that by adding the following lines (probably a better way, but this seems to work):

```

script_loc = os.path.realpath(__file__)
script_dir = os.path.dirname(script_loc)
api_key = script_dir + '/api.key' # api.key must be the file name!
format_file = script_dir + '/weather_format.txt' # weather_format must be the filename.

```

To the modules list at the top, be sure to add 'import os' so that these functions will be loaded.  Then change the actual calls to read the new variable names:

**line 105**
```

url['key'] = open( api_key).read().strip()

```

**line 111**
```

for ln in codecs.open( format_file, 'r', 'utf-8' ):

```

That will allow you to make a directory containing the scripts and then make a symbolic link to the python script somewhere like $USER/bin so that you can call it from anywhere.

---

### Post by Vaphell on 2013-10-10
good point about the paths.

I got rid of the cruft in this function and added stripping whitespace paddings which ruin alignment as evidenced by precipitation 1hr.
```
def json_get( start, path ):
    n = start
    for p in path.split('/'):
        if p: n = n[p]
    if   isinstance( n, dict ):           return [n]
    elif isinstance( n, (str, unicode) ): return n.strip()
    return n
```

my python-fu still sucks, pretty much all i know is how to abuse comprehensions :D

what i did learn when writing this script is how awesome str.format() function is. I knew about positional parameters but the revelation that you can pass a dict with keys matching to named {key} placeholders and witness the magic happening... that was unexpected :-)
i am sure in perl one can do even better things but for someone who usually plays with rigid shell scripts this flexibility is borderline absurd :D
```
>>> s = '/{dict1}/{0}/{dict2}/{dict1}/{named}/{1}/{2}/{dict2}/{3}/'
>>> s.format( 'zero', *[11,22,33], named='N', **{'dict1':'===', 'dict2':'@@@'} )
'/===/zero/@@@/===/N/11/22/@@@/33/'
```

---

### Post by GrouchyGaijin on 2013-10-11
Pretty awesome!
It works for me too.

Thank you so much Vaphell
@Drmrgd, thanks for the really useful tip about the zmw string.

I don't quite follow the part of the discussion about the paths.
I did it a **crude** way.  
I made a directory called <city-name>-weather.
I put that directory in path.
I made a copy of the script and called it by the city name I want the weather for.
I put the script in the <city-name>-weather directory.
I edited the python script to open the weather_format.txt file in the appropriate <city-name>-weather directory.  
I do have to keep the api-key file in home, but everything runs now by typing <city-name>.py

---

### Post by drmrgd on 2013-10-11
> **Vaphell said:**
> 

what i did learn when writing this script is how awesome str.format() function is. I knew about positional parameters but the revelation that you can pass a dict with keys matching to named {key} placeholders and witness the magic happening... that was unexpected :-)
i am sure in perl one can do even better things but for someone who usually plays with rigid shell scripts this flexibility is borderline absurd :D
```
>>> s = '/{dict1}/{0}/{dict2}/{dict1}/{named}/{1}/{2}/{dict2}/{3}/'
>>> s.format( 'zero', *[11,22,33], named='N', **{'dict1':'===', 'dict2':'@@@'} )
'/===/zero/@@@/===/N/11/22/@@@/33/'
```

Actually, the timing of this exercise is very fortuitous as I've been playing around with bash color escape sequences trying to figure out how it works for the last couple days.  Then I got the 'bright idea' to try to output some text from perl scripts by appending the color codes, and it seems to work.  So, now that I see this can be taken even one step further, this gives me a few other ideas.
 
[QUOTE=Vaphell]
[COLOR=#000000]my python-fu still sucks, pretty much all i know is how to abuse comprehensions [/COLOR]:grin:
[/QUOTE]

There's more to python than this? :D

---

### Post by Vaphell on 2013-10-11
sure, for example exceptions aka 'It is Easier to Ask for Forgiveness than Permission' :-)

hmm, i think it should be possible to use format( **dict ) to automatically fill template, just like with weather data, instead of looping to replace(). Why didn't i think of that o.O

---

### Post by Vaphell on 2013-10-11
so after yet another iteration of improvements my current setup is like this:

```
bin/weather -> weather_files/weather.py
bin/weather_files:
api.key
weather_format.txt
weather_locations.txt
weather.py
```

.py
```
#!/usr/bin/env python

import codecs
import re
import urllib2
import json
import sys
import os

def_url = { 'url': 'http://api.wunderground.com/api/{key}/{dataset}/q/{location}.json' }

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
class Term:
    END     = '\033[0m'
    B       = '\033[1m'
    RED     = '\033[91m'           
    GREEN   = '\033[92m'
    YELLOW  = '\033[93m'
    BLUE    = '\033[94m'
    MAGENTA = '\033[95m'
    CYAN    = '\033[96m'

field_rgx = r'\{[^.}]*[a-z]+[^.}]*\}'

# params
def params( args ):
    avail = ( '--help', '--info', '--locations' )
    pdict = { 'loc_idx': 0 }
    for p in args:
        if p in avail:
            pdict[p] = True
        else:
            try:
                pdict['loc_idx'] = int(p)               
            except:
                pass
    return pdict
    
# show available params
def show_help( args ):
    print 'usage: {0} [option] [location_id]'.format( args[0] )
    print '    --help\tthis help'
    print '    --info\tshows debug info, data structure'
    print '    --locations\tshows available locations in the (id, code, description)'
 

# function showing data tree
def show_struct( x, name, lvl=0, offset=4 ):
    ln = ' '*lvl*offset+'{0}'
    print ln.format( name )
    if isinstance( x, list ):
        show_struct( x[0], '*', lvl=lvl+1 )
    elif isinstance( x, dict ):
        for k in x:
            show_struct( x[k], k, lvl=lvl+1 )

# load json
def load_weather_data( url ):
    return json.load( urllib2.urlopen( urllib2.Request( url['url'].format( **url ) ) ) )

# debug/struct info
def dump_info( url, w_data ):
    print 'key: {key}\nlocation: {location}\nurl: {url}\n'.format( **url )
    show_struct( w_data, 'data structure:' )

# locations file
def load_locations( f ):
    loc = []
    for ln in codecs.open( f, 'r', 'utf-8' ):
        if ln.startswith('#'): 
            continue
        elif '=':
            d = {}
            d['id'], d['desc'] = ( x.strip() for x in ln.split('=', 1) )
            loc.append( d )
    return loc

# print locations    
def print_locations( l ):
    print 'Available locations:'
    for idx in range(0, len(l)):
      print u'{idx}:\t{id} ({desc})'.format( idx=idx, **l[idx] )

# def parse format file
def parse_header_line( ln, url ):
    url['dataset'] = ln.lstrip('@/, ').replace(' ','').replace(',', '/')

# def parse format file
def load_format_and_data( f, url ):
    print_data = []  
    for ln in codecs.open( f, 'r', 'utf-8' ):
        ln = ln.rstrip()
        if ln.startswith('#'): 
            continue
        if ln.startswith('@'):
            parse_header_line( ln, url )
            w_data = load_weather_data( url )
        elif ln.startswith('!'):
            jpath = ln.lstrip('! ')
            format = { 'template':'', 'src': wdata_get( w_data, jpath ) }       
            print_data.append( format )
        else:
            format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
    return ( w_data, print_data )

# function to get nodes/values from the data tree
def wdata_get( start, path ):
    n = start
    for p in path.split('/'):
        if p: n = n[p]
    if   isinstance( n, dict ):           return [n]
    elif isinstance( n, (str, unicode) ): return n.strip()
    return n

def get_fields( t ):
    return [ x.strip('{}') for x in re.findall( field_rgx, t ) ]

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )

def fix( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    else:                      return val

# output
def print_output( pd, f_obj ):
   for d in pd:
        for n in d['src']:
            t = d['template']
            print t.format( TERM=f_obj, **dict( (k, fix( k, wdata_get(n,k))) for k in get_fields( t ) ) )



# --------- main ---------------------

if __name__ == '__main__':
# settings (--help, --info)
    settings = params( sys.argv[1:] )
    if '--help' in settings:
        show_help( sys.argv )
        sys.exit(0)

    url = def_url.copy()
    script_dir = os.path.dirname( os.path.realpath(__file__) )
    locations = load_locations( script_dir + '/weather_locations.txt' )
    
    if '--locations' in settings:
        print_locations( locations )
        sys.exit(0)
    url['key'] = open( script_dir + '/api.key' ).read().strip()
    if settings['loc_idx'] < len(locations):
        l_idx = settings['loc_idx']
    else:
        print 'warning:  location id out of range, using default value'
        l_idx = 0
    url['location'] = locations[l_idx]['id'].replace(' ', '%20' )
    format_file = script_dir + '/weather_format.txt'
      
# load data  
    w_data, print_data = load_format_and_data( format_file, url )    

    if '--info' in settings:
        print_locations( locations )
        dump_info( url, w_data )
        sys.exit(0)

    print_output( print_data, Term() )


```


format file is changed, location is no more and [X] formats are changed to {TERM.X}
```
@ astronomy, conditions, forecast
#-------------------------------------------------------------------------------------------------
! current_observation
#-------------------------------------------------------------------------------------------------
{TERM.CYAN}       Location:{TERM.END} {TERM.B}{TERM.GREEN}{display_location/full}{TERM.END} {TERM.GREEN}({display_location/latitude} {display_location/longitude}){TERM.END}
{TERM.CYAN}Weather station:{TERM.END} {TERM.B}{TERM.GREEN}{observation_location/full}{TERM.END} {TERM.GREEN}({observation_location/latitude} {observation_location/longitude})
{TERM.CYAN}           Time:{TERM.END} {TERM.B}{TERM.GREEN}{observation_time_rfc822}{TERM.END}
{TERM.CYAN}     Conditions:{TERM.END} {TERM.B}{TERM.YELLOW}{weather}{TERM.END}
{TERM.CYAN}    Temperature:{TERM.END} {TERM.B}{TERM.YELLOW}{temp_c}°C{TERM.END}, feels like {TERM.B}{TERM.YELLOW}{feelslike_c}°C{TERM.END}
{TERM.CYAN}           Wind:{TERM.END} {TERM.B}{TERM.YELLOW}{wind_kph} km/h{TERM.END}, from the {wind_dir}
{TERM.CYAN}  Precipitation:{TERM.END} {TERM.B}{TERM.YELLOW}{precip_today_metric} mm{TERM.END} today
{TERM.CYAN}       Pressure:{TERM.END} {TERM.B}{TERM.YELLOW}{pressure_mb} hPa{TERM.END}
{TERM.CYAN}       Humidity:{TERM.END} {TERM.B}{TERM.YELLOW}{relative_humidity}{TERM.END}
{TERM.CYAN}      Dew point:{TERM.END} {TERM.B}{TERM.YELLOW}{dewpoint_c}°C{TERM.END}
{TERM.CYAN}     Visibility:{TERM.END} {TERM.B}{TERM.YELLOW}{visibility_km} km{TERM.END}
#
#
# astronomy
#-------------------------------------------------------------------------------------------------
! 
#-------------------------------------------------------------------------------------------------
{TERM.CYAN}            Sun:{TERM.END} {TERM.B}{TERM.YELLOW}{sun_phase/sunrise/hour}:{sun_phase/sunrise/minute}{TERM.END} - {TERM.B}{TERM.YELLOW}{sun_phase/sunset/hour}:{sun_phase/sunset/minute}{TERM.END}
{TERM.CYAN}           Moon:{TERM.END} {TERM.B}{TERM.YELLOW}{moon_phase/phaseofMoon} ({moon_phase/percentIlluminated}%){TERM.END}         
#
# forecast in simple format
#-------------------------------------------------------------------------------------------------
! forecast/simpleforecast/forecastday
#-------------------------------------------------------------------------------------------------
{TERM.YELLOW}{date/weekday}, {date/monthname} {date/day}, {date/year}:{TERM.END}
 {TERM.BLUE}  {conditions}, high {high/celsius}°C, low {low/celsius}°C
   Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h{TERM.END}
```


weather_locations.txt
```
# comment line
zmw:00000.6.02435 = Falun, Sweden
zmw:21701.1.99999 = Frederick, Maryland
```


script indexes these location entries starting from 0, 0 is default
```
$ weather --locations
Available locations:
0:	zmw:00000.6.02435 (Falun, Sweden)
1:	zmw:21701.1.99999 (Frederick, Maryland)

$ weather
       Location: Falun, Sweden (60°35'59"N 15°37'59"E)
.....
$ weather 1
       Location: Frederick, MD (39°25'05"N 77°20'10"W)
.......
...
```

---

### Post by Sector11 on 2013-10-12
I am at a loss here ...

```
 12 Oct 13 | 09:09:48 ~
    $ find /home/sector11 2 -name london.py
/home/sector11/bin/london.py
 
 12 Oct 13 | 09:11:00 ~
    $ find /home/sector11 2 -name api.key
/home/sector11/bin/api.key
 
 12 Oct 13 | 09:11:21 ~
    $ find /home/sector11 2 -name weather_format.txt
/home/sector11/bin/weather_format.txt
 
 12 Oct 13 | 09:12:23 ~
    $ pwd
/home/sector11
 
 12 Oct 13 | 09:13:33 ~
    $ cd bin
 
 12 Oct 13 | 09:13:38 ~/bin
    $ pwd
/home/sector11/bin
 
 12 Oct 13 | 09:13:42 ~/bin
    $ london.py
Traceback (most recent call last):
  File "/home/sector11/bin/london.py", line 118, in <module>
    format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
TypeError: 'builtin_function_or_method' object has no attribute '__getitem__'
 
 12 Oct 13 | 09:13:49 ~/bin
        $ $PATH
bash: /usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/sector11/bin: No such file or directory
 
 12 Oct 13 | 09:13:59 ~/bin
    $ 

```

**/home/sector11/bin/london.py**
```
#!/usr/bin/env python

import codecs
import re
import urllib2
import json
import sys

def_url = { 'url': 'http://api.wunderground.com/api/{key}/{dataset}/q/{location}.json' }

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
styles = { '[END]'    : '\033[0m',
           '[B]'      : '\033[1m',
           '[RED]'    : '\033[91m',
           '[GREEN]'  : '\033[92m',
           '[YELLOW]' : '\033[93m',
           '[BLUE]'   : '\033[94m',
           '[MAGENTA]': '\033[95m',
           '[CYAN]'   : '\033[96m' }

field_rgx = r'\{[^:}]*[a-z]+[^:}]*[:}]'

# show available params
def show_help( args ):
    print args[0]
    print '    --help\tthis help'
    print '    --info\tshows debug info, data structure'

# function showing data tree
def show_struct( x, name, lvl=0, offset=4 ):
    ln = ' '*lvl*offset+'{0}'
    print ln.format( name )
    if isinstance( x, list ):
        show_struct( x[0], '*', lvl=lvl+1 )
    elif isinstance( x, dict ):
        for k in x:
            show_struct( x[k], k, lvl=lvl+1 )

# load json
def load_datafile( url ):
    return json.load( urllib2.urlopen( urllib2.Request( url['url'].format( **url ) ) ) )

# debug/struct info
def dump_info( url, json_data ):
    print 'key: {key}\nlocation: {location}\nurl: {url}\n'. format( **url )
    show_struct( json_data, 'data structure:' )

def parse_header_line( ln, url ):
    for x in ln.lstrip('@ ').split(';')[0:2]:
        k, v = ( i.strip() for i in x.strip().split('=') )
        if k == 'dataset':
            url['dataset'] = '/'.join( i.strip() for i in v.split(',') )
        elif k == 'location':
            url['location'] = v.strip().replace(' ', '%20' )


# function to get nodes/values from the data tree
def json_get( start, path ):
    n = start
    path = path.split('/')
    for p in path:
        if p: n = n[p]
    if   isinstance( n, dict ):           return [n]
    elif isinstance( n, (str, unicode) ): return n.strip()
    return n

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )

def fix( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    else:                      return val



# --------- main ---------------------

if __name__ == '__main__':

# settings (--help, --info)
    settings = dict( (k, True) for k in sys.argv[1:] )
    if '--help' in settings:
        show_help( sys.argv )
        sys.exit(0)

    url = def_url.copy()
    url['key'] = open( 'api.key' ).read().strip()

# load data
    json_data = {}
    print_data = []
    for ln in codecs.open( '/home/sector11/bin/weather_format.txt', 'r', 'utf-8' ):
        ln = ln.rstrip()
        if ln.startswith('#'):
            continue
        if ln.startswith('@'):
            parse_header_line( ln, url )
            json_data = load_datafile( url )
            if '--info' in settings:
                dump_info( url, json_data )
                sys.exit(0)
        elif ln.startswith('!'):
            jpath = ln.lstrip('! ')
            format = { 'path': jpath, 'template':'', 'fields':[], 'src': json_get( json_data, jpath ) }
            print_data.append( format )
        else:
            format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
            format['fields'] += [ x.strip('{}') for x in re.findall( field_rgx, ln ) ]

#    print [ d for d in print_data ]

    for d in print_data:
        for s in styles:
            d['template'] = d['template'].replace( s, styles[s] )
        for n in d['src']:
            print d['template'].format(**dict( (k, fix( k, json_get(n,k))) for k in d['fields'] ) )

```

**/home/sector11/bin/weather_format.txt**
```
# @ location = ...; dataset = ..., ...,
#     location:
#         - zmw:00000.9.12345 (unamibiguous) <- pick this format
#         - US_STATE_ABBREV/City
#         - Country/City
# Get zmw at:  curl -s "http://autocomplete.wunderground.com/aq?query=<city_name>"

# London, Canada: astronomy, current conditions, forecast
@ location = zmw:00000.1.71623; dataset = astronomy, conditions, forecast
#
# template headers starting with !
# - path to data (empty if pointing to the top level)
#
# current weather
#-------------------------------------------------------------------------------------------------
! current_observation
#-------------------------------------------------------------------------------------------------
[CYAN]       Location:[END] [B][GREEN]{display_location/full}[END] [GREEN]({display_location/latitude} {display_location/longitude})[END]
[CYAN]Weather station:[END] [B][GREEN]{observation_location/full}[END] [GREEN]({observation_location/latitude} {observation_location/longitude})
[CYAN]           Time:[END] [B][GREEN]{observation_time_rfc822}[END]
[CYAN]     Conditions:[END] [B][YELLOW]{weather}[END]
[CYAN]    Temperature:[END] [B][YELLOW]{temp_c}°C[END], feels like [B][YELLOW]{feelslike_c}°C[END]
[CYAN]           Wind:[END] [B][YELLOW]{wind_kph} km/h[END], from the {wind_dir}
[CYAN]  Precipitation:[END] [B][YELLOW]{precip_1hr_metric} mm[END] in 1hr, [B][YELLOW]{precip_today_metric} mm[END] today
[CYAN]       Pressure:[END] [B][YELLOW]{pressure_mb} hPa[END]
[CYAN]       Humidity:[END] [B][YELLOW]{relative_humidity}[END]
[CYAN]      Dew point:[END] [B][YELLOW]{dewpoint_c}°C[END]
[CYAN]     Visibility:[END] [B][YELLOW]{visibility_km} km[END]
#
#
# astronomy (no path because its data is on the top level)
#-------------------------------------------------------------------------------------------------
!
#-------------------------------------------------------------------------------------------------
[CYAN]            Sun:[END] [B][YELLOW]{sun_phase/sunrise/hour}:{sun_phase/sunrise/minute}[END] - [B][YELLOW]{sun_phase/sunset/hour}:{sun_phase/sunset/minute}[END]
[CYAN]           Moon:[END] [B][YELLOW]{moon_phase/phaseofMoon} ({moon_phase/percentIlluminated}%)[END]
#
# forecast in text format
#! forecast#forecast/simpleforecast/forecastday
#[CYAN]{title}:[END]
#  {fcttext_metric}
#
#
# forecast in simple format
#-------------------------------------------------------------------------------------------------
! forecast/simpleforecast/forecastday
#-------------------------------------------------------------------------------------------------
[YELLOW]{date/weekday}, {date/monthname} {date/day}, {date/year}:[END]
 [BLUE]  {conditions}, high {high/celsius}°C, low {low/celsius}°C
   Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h[END]

```

**/home/sector11/bin/api.key**
```
one-line-only-top-secret
```

1. I know I don't have to cd to ~/bin, it's in my $PATH but since I get the same error in ~/ I figured why not.
2. I also tried /home/sector11/bin/london.py as /home/sector11/bin/london - with the same results.

Any help appreciated.

---

### Post by Sector11 on 2013-10-12
> **Vaphell said:**
> so after yet another iteration of improvements my current setup is like this:

However this works perfectly ...

```
 12 Oct 13 | 10:18:40 ~
    $ vph.py 0
       Location: Falun, Sweden (60°35'59"N 15°37'59"E)
Weather station: Kämparvet, Falun, DALARNA (60°36'22"N 15°38'20"E)
... ... ...
 12 Oct 13 | 10:18:59 ~
    $ vph.py 1
       Location: Frederick, MD (39°25'05"N 77°20'10"W)
Weather station: Lake Linganore, New Market, Maryland (39°24'51"N 77°17'54"W)
... ... ...
 12 Oct 13 | 10:19:04 ~
    $ vph.py 2
       Location: London, Ontario (43°01'47"N 81°09'00"W)
Weather station: London, (43°01'47"N 81°09'00"W)
... ... ...
```

**and now the BIG test ....** ***[COLOR="#B22222"]Ringo ... drum roll please....[/COLOR]***
```
 12 Oct 13 | 10:23:29 ~
    $ vph.py 3
       Location: Buenos Aires, Argentina (34°34'11"S 58°25'11"W)
Weather station: Buenos Aires, (34°34'11"S 58°25'11"W)
... ... ...

```

YES!!!!!!!!!!!!!!!!!!!!!!

In case GrouchyGaijin never mentioned it ... *I'm a weather nut!...* - Conky - OpenBox Menus - Scripts ...  ):P

[CENTER][[img]http://s20.postimg.org/w469uvg21/2013_10_12_10_33_54_1920x1080_Sector11.jpg[/img]](http://postimg.org/image/w469uvg21/)

[FONT=Book Antiqua][SIZE=4][COLOR="#006400"]KUDOS Vaphell![/COLOR][/SIZE][/FONT]
Now to tweak the template!  :twisted:[/CENTER]

---

### Post by Vaphell on 2013-10-12
> **Sector11 said:**
> In case GrouchyGaijin never mentioned it ... *I'm a weather nut!...* - Conky - OpenBox Menus - Scripts ...  ):P

[CENTER][[img]http://s20.postimg.org/w469uvg21/2013_10_12_10_33_54_1920x1080_Sector11.jpg[/img]](http://postimg.org/image/w469uvg21/)

[FONT=Book Antiqua][SIZE=4][COLOR="#006400"]KUDOS Vaphell![/COLOR][/SIZE][/FONT]
Now to tweak the template!  :twisted:[/CENTER]

what is this... i don't even... o.O Son, i see pixels of the wallpaper, i am disappoint :P :D

---

### Post by Sector11 on 2013-10-12
> **Vaphell said:**
> what is this... i don't even... o.O Son, i see pixels of the wallpaper, i am disappoint :P :D

Son?  ME! hahahahahahahahahahaha been many a year since I've been called that!

Doesn't matter... I was only swimming on the surface ... a [COLOR="#0000CD"]**[SIZE=4]lot[/SIZE]**[/COLOR] more where they came from ... :rolleyes:
[CENTER][[img]http://s20.postimg.org/f7h72g8i1/2013_10_12_11_47_33_1920x1080_Sector11.jpg[/img]](http://postimg.org/image/f7h72g8i1/)[/CENTER]

---

### Post by Vaphell on 2013-10-12
so i guess that newfangled thing for underage idiots, called 'internet meme' didn't catch your attention? :-)
[http://knowyourmeme.com/memes/son-i-am-disappoint](http://knowyourmeme.com/memes/son-i-am-disappoint)

---

### Post by GrouchyGaijin on 2013-10-12
OK I'm back online.  Internet access has been restored to the city of Falun :-)
[COLOR=#ff0000][B]NEVER MIND

[/B][/COLOR]Sometimes I'm a dumb a**.  The script works absolutely fine when you give it the right zmw code

---

### Post by Sector11 on 2013-10-12
> **Vaphell said:**
> so i guess that newfangled thing for underage idiots, called 'internet meme' didn't catch your attention? :-)
[http://knowyourmeme.com/memes/son-i-am-disappoint](http://knowyourmeme.com/memes/son-i-am-disappoint)

I was certain I had answered to this ... BUT:

Nooooooooooo!! :lolflag: I didn't know that ... GG tells me I live in a bubble ... *I'll blame him.*
Hey there GG, buddy, pal, chum, amigo, &#21451;&#20154;, vän ... ):P

Did not mean anything negative by my comment though - peace! ...

I have been playing and when I get the "yad" box cleaned up I'll post that too.

my **vph.py** file was changed just a tad to include more colours - then didn't use them all - and added "os.system('clear')"
```
#!/usr/bin/env python
# by: Vaphell - Oct 2013
# http://ubuntuforums.org/showthread.php?t=2178780&page=6&p=12813725#post12813725
# ~/bin/vph.py

import codecs
import re
import urllib2
import json
import sys
import os
os.system('clear')

def_url = { 'url': 'http://api.wunderground.com/api/{key}/{dataset}/q/{location}.json' }

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
class Term:
    End       = '\033[0m'
    Default   = '\033[39m'
    B         = '\033[1m'
    Black     = '\033[30m'
    Red       = '\033[31m'
    Green     = '\033[32m'
    Yellow    = '\033[33m'
    Blue      = '\033[34m'
    Magenta   = '\033[35m'
    Cyan      = '\033[36m'
    Lgray     = '\033[37m'
    Lred      = '\033[91m'
    Lgreen    = '\033[92m'
    Lyellow   = '\033[93m'
    Lblue     = '\033[94m'
    Lmagenta  = '\033[95m'
    Lcyan     = '\033[96m'
    White     = '\033[97m'

field_rgx = r'\{[^.}]*[a-z]+[^.}]*\}'

# params
def params( args ):
    avail = ( '--help', '--info', '--locations' )
    pdict = { 'loc_idx': 0 }
    for p in args:
        if p in avail:
            pdict[p] = True
        else:
            try:
                pdict['loc_idx'] = int(p)
            except:
                pass
    return pdict

# show available params
def show_help( args ):
    print 'usage: {0} [option] [location_id]'.format( args[0] )
    print '    --help\tthis help'
    print '    --info\tshows debug info, data structure'
    print '    --locations\tshows available locations in the (id, code, description)'


# function showing data tree
def show_struct( x, name, lvl=0, offset=4 ):
    ln = ' '*lvl*offset+'{0}'
    print ln.format( name )
    if isinstance( x, list ):
        show_struct( x[0], '*', lvl=lvl+1 )
    elif isinstance( x, dict ):
        for k in x:
            show_struct( x[k], k, lvl=lvl+1 )

# load json
def load_weather_data( url ):
    return json.load( urllib2.urlopen( urllib2.Request( url['url'].format( **url ) ) ) )

# debug/struct info
def dump_info( url, w_data ):
    print 'key: {key}\nlocation: {location}\nurl: {url}\n'.format( **url )
    show_struct( w_data, 'data structure:' )

# locations file
def load_locations( f ):
    loc = []
    for ln in codecs.open( f, 'r', 'utf-8' ):
        if ln.startswith('#'):
            continue
        elif '=':
            d = {}
            d['id'], d['desc'] = ( x.strip() for x in ln.split('=', 1) )
            loc.append( d )
    return loc

# print locations
def print_locations( l ):
    print 'Available locations:'
    for idx in range(0, len(l)):
      print u'{idx}:\t{id} ({desc})'.format( idx=idx, **l[idx] )

# def parse format file
def parse_header_line( ln, url ):
    url['dataset'] = ln.lstrip('@/, ').replace(' ','').replace(',', '/')

# def parse format file
def load_format_and_data( f, url ):
    print_data = []
    for ln in codecs.open( f, 'r', 'utf-8' ):
        ln = ln.rstrip()
        if ln.startswith('#'):
            continue
        if ln.startswith('@'):
            parse_header_line( ln, url )
            w_data = load_weather_data( url )
        elif ln.startswith('!'):
            jpath = ln.lstrip('! ')
            format = { 'template':'', 'src': wdata_get( w_data, jpath ) }
            print_data.append( format )
        else:
            format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
    return ( w_data, print_data )

# function to get nodes/values from the data tree
def wdata_get( start, path ):
    n = start
    for p in path.split('/'):
        if p: n = n[p]
    if   isinstance( n, dict ):           return [n]
    elif isinstance( n, (str, unicode) ): return n.strip()
    return n

def get_fields( t ):
    return [ x.strip('{}') for x in re.findall( field_rgx, t ) ]

# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    deg = float( x )
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )

def fix( name, val ):
    if   'latitude'  in name:  return latitude( val )
    elif 'longitude' in name:  return longitude( val )
    else:                      return val

# output
def print_output( pd, f_obj ):
   for d in pd:
        for n in d['src']:
            t = d['template']
            print t.format( TERM=f_obj, **dict( (k, fix( k, wdata_get(n,k))) for k in get_fields( t ) ) )



# --------- main ---------------------

if __name__ == '__main__':
# settings (--help, --info)
    settings = params( sys.argv[1:] )
    if '--help' in settings:
        show_help( sys.argv )
        sys.exit(0)

    url = def_url.copy()
    script_dir = os.path.dirname( os.path.realpath(__file__) )
    locations = load_locations( script_dir + '/vph-weather_locations.txt' )

    if '--locations' in settings:
        print_locations( locations )
        sys.exit(0)
    url['key'] = open( script_dir + '/vph-api.key' ).read().strip()
    if settings['loc_idx'] < len(locations):
        l_idx = settings['loc_idx']
    else:
        print 'warning:  location id out of range, using default value'
        l_idx = 0
    url['location'] = locations[l_idx]['id'].replace(' ', '%20' )
    format_file = script_dir + '/vph-weather_format.txt'

# load data
    w_data, print_data = load_format_and_data( format_file, url )

    if '--info' in settings:
        print_locations( locations )
        dump_info( url, w_data )
        sys.exit(0)

    print_output( print_data, Term() )
```

and **vph-weather_format**
```
@ astronomy, conditions, forecast
#-------------------------------------------------------------------------------------------------
! current_observation
#-------------------------------------------------------------------------------------------------
{TERM.Lcyan}
{TERM.Cyan}       Location:{TERM.Default} {display_location/full} {TERM.Lred}({TERM.Lcyan}{display_location/latitude} {display_location/longitude}{TERM.Lred})
{TERM.Cyan}        Station:{TERM.Lcyan} {observation_location/full} {TERM.Lred}({TERM.Lcyan}{observation_location/latitude} {observation_location/longitude}{TERM.Lred})
{TERM.Cyan}           Time:{TERM.Lcyan} {observation_time_rfc822}
{TERM.Cyan}     Conditions:{TERM.Default} {weather}
{TERM.Cyan}    Temperature:{TERM.Lgray} {temp_c}°{TERM.Blue}    ± {TERM.Blue}{feelslike_c}°{TERM.Lcyan}
{TERM.Cyan}           Wind:{TERM.Lcyan} {wind_kph} km/h from the {wind_dir}
{TERM.Cyan}  Precipitation:{TERM.Lcyan} {precip_today_metric} mm today
{TERM.Cyan}       Pressure:{TERM.Lcyan} {pressure_mb} hPa
{TERM.Cyan}       Humidity:{TERM.Lcyan} {relative_humidity}
{TERM.Cyan}      Dew point:{TERM.Lcyan} {dewpoint_c}°
{TERM.Cyan}     Visibility:{TERM.Lcyan} {visibility_km} km
#
#
# astronomy
#-------------------------------------------------------------------------------------------------
!
#-------------------------------------------------------------------------------------------------
{TERM.Cyan}            Sun:{TERM.Lgray} &#8593; {sun_phase/sunrise/hour}:{sun_phase/sunrise/minute} {TERM.Blue}«»{TERM.Lblue} &#8595; {sun_phase/sunset/hour}:{sun_phase/sunset/minute}
{TERM.Cyan}           Moon:{TERM.Lcyan} {moon_phase/phaseofMoon} {TERM.Lred}({TERM.Green}{moon_phase/percentIlluminated}%{TERM.Lred})
#
# forecast in simple format
#-------------------------------------------------------------------------------------------------
! forecast/simpleforecast/forecastday
#-------------------------------------------------------------------------------------------------
{TERM.Default} {date/weekday}, {date/monthname} {date/day}, {date/year}:{TERM.Lcyan}
{TERM.Lred}   {high/celsius}°  {TERM.Blue}{low/celsius}°{TERM.Default}   {conditions}
{TERM.Lblue}   Winds {avewind/kph} km/h from the {avewind/dir}, max {maxwind/kph} km/h{TERM.Lcyan}
```

and as a test: **vph-weather-locations**
```
# comment line - starts with 0, 1, 2, 3, 4,
zmw:00000.1.87582 = Buenos Aires, Argentina
zmw:00000.1.71623 = London, Canada
zmw:00000.6.02435 = Falun, Sweden
zmw:21701.1.99999 = Frederick, Maryland
```

More coming....
[CENTER][[img]http://s20.postimg.org/h3vjo25mx/2013_10_12_17_00_15_1920x1080_Sector11.jpg[/img]](http://postimg.org/image/h3vjo25mx/) [[img]http://s20.postimg.org/argee82kp/2013_10_12_17_10_37_1920x1080_Sector11.jpg[/img]](http://postimg.org/image/argee82kp/)[/CENTER]

---

### Post by GrouchyGaijin on 2013-10-12
> **Sector11 said:**
> ...and added "os.system('clear')"


Hey S11,

I'm surprised you don't have personal weather station and send your data to the Weather Underground.
I can't get my wife's home town.  There are no personal weather stations there.  The closest airport is 30 kilometers away.

What does os.system('clear') do?

Are you guys able to run the script without the .py?
When I type weather I get a message that:
```

The program 'weather' is currently not installed.  You can install it by typing:
sudo apt-get install weather-util

```

---

### Post by Sector11 on 2013-10-12
> **GrouchyGaijin said:**
> Hey S11,

I'm surprised you don't have personal weather station and send your data to the Weather Underground.

Hey GG ...

Can't afford it or I would ... believe me.  :D
Imagine ... weather by S11  :D

> **GrouchyGaijin said:**
> 
I can't get my wife's home town.  There are no personal weather stations there.  The closest airport is 30 kilometers away.

Sanjo?
I get it:
```
	{
		"name": "Sanjo, Japan", 
		"type": "city", 
		"c": "JP",
		"zmw": "00000.7.47572",
		"tz": "Asia/Tokyo",
		"tzs": "JST",
		"l": "/q/zmw:00000.7.47572"
	}
```
**BUT...........**
```
Traceback (most recent call last):
  File "/home/sector11/bin/vph", line 193, in <module>
    print_output( print_data, Term() )
  File "/home/sector11/bin/vph", line 156, in print_output
    print t.format( TERM=f_obj, **dict( (k, fix( k, wdata_get(n,k))) for k in get_fields( t ) ) )
  File "/home/sector11/bin/vph", line 156, in <genexpr>
    print t.format( TERM=f_obj, **dict( (k, fix( k, wdata_get(n,k))) for k in get_fields( t ) ) )
  File "/home/sector11/bin/vph", line 147, in fix
    if   'latitude'  in name:  return latitude( val )
  File "/home/sector11/bin/vph", line 143, in latitude
    def latitude( x ):  return _lat_long( x, 'NS' )
  File "/home/sector11/bin/vph", line 135, in _lat_long
    deg = float( x )
ValueError: could not convert string to float: 
 
 12 Oct 13 | 19:32:49 ~
    $ 

```


> **GrouchyGaijin said:**
> What does os.system('clear') do?

Clears the screen ... same as bash "clear"  but 0j0: it need to be AFTER: *import os*

> **GrouchyGaijin said:**
> Are you guys able to run the script without the .py?
When I type weather I get a message that:
```

The program 'weather' is currently not installed.  You can install it by typing:
sudo apt-get install weather-util

```

"weather" by itself doesn't work because it's in your list of programs you have not installed, you know when you do a:
```
sudo apt-get update
```

```
 12 Oct 13 | 19:05:39 ~
    $ ser weather
{snip}
p   weather-util                                       - command-line tool to obtain weather conditions and forecasts 
p   weather-util-data                                  - optional correlation data for weather-util search feature    
{snip} 
 12 Oct 13 | 19:05:48 ~
    $ 
```
rename "weather.py" file: "ggwx" and run *ggwx* - it will work.

---

### Post by Habitual on 2013-10-12
Am I a dinosaur because I can and do still use conkyForecast?
(outside of conky btw)

Rumor has it the service is now subscription and XOAP_LICENCE_KEYs are mostly ineffective, but mine still works.
I don't have any XOAP_PARTNER_ID enabled in my .conkyForecast.config

---

### Post by Sector11 on 2013-10-12
> **Habitual said:**
> Am I a dinosaur because I can and do still use conkyForecast?
(outside of conky btw)

Rumor has it the service is now subscription and XOAP_LICENCE_KEYs are mostly ineffective, but mine still works.
I don't have any XOAP_PARTNER_ID enabled in my .conkyForecast.config

Habitual!!! ):P  Long time no see ... you changed your avatar! I would never have recognized you.  ;)

If you're a dinosaur, we're dino's together, but then I'm a dino by age - so my oldest son says!  I never gave up on conkyForecast.  When weather.com killed the free stuff and went "pay" - it did stop for some people.  People that kept their cache files in /tmp and lost them on the next boot.  I think that only lasted for a short while though because a lot came back and said it started working again.

I found your bash script and expanded on it, [that's it in my last post here with screenshots]("http://ubuntuforums.org/showthread.php?t=2178780&page=6&p=12814647#post12814647") - made it 10 days.

**cf** - by habitual - bent, folded and mutilated by  Sector11:
```
#!/bin/bash
# --- original ---
# 4 Day Weather forecast script for Boardman, OH
# Written by John Jones ie: Habitual
# 11.01.2010 12:10:07
# --- Edited by Sector11 ---
# today & 8 Day Forecast for Buenos Aires Argentina
# ~/bin/cf
# 24 Mar 13 | 14:10:06 - UTC -3
# conkyForecast by: Kaivalagi

# tput Color Capabilities:
#     tput setab [1-7] – Set a background color using ANSI escape
#     tput setb [1-7] – Set a background color
#     tput setaf [1-7] – Set a foreground color using ANSI escape
#     tput setf [1-7] – Set a foreground color

# tput Text Mode Capabilities:
#     tput bold – Set bold mode
#     tput dim – turn on half-bright mode
#     tput smul – begin underline mode
#     tput rmul – exit underline mode
#     tput rev – Turn on reverse mode
#     tput smso – Enter standout mode (bold on rxvt)
#     tput rmso – Exit standout mode
#     tput sgr0 – Turn off all attributes

# Color Code for tput:
# tput setaf 0 – Black		# tput setf 0 – Black
# tput setaf 1 – Red		# tput setf 1 – Blue
# tput setaf 2 – Green		# tput setf 2 – Green
# tput setaf 3 – Yellow		# tput setf 3 – Cyan
# tput setaf 4 – Blue		# tput setf 4 – Red
# tput setaf 5 – Magenta	# tput setf 5 – Magenta
# tput setaf 6 – Cyan		# tput setf 6 – Yellow
# tput setaf 7 – White		# tput setf 7 – White

# Clear the screen
tput clear
# Draw the lines
tput cup 5 0; tput setaf 4;
echo "--> `conkyForecast --location=ARBA0009 -d CN`"
tput cup 5 35; tput setaf 4;
echo "--> `conkyForecast --location=ARBA0009 -d CO`"
tput cup 10 0; tput setaf 7;
echo "--------------------------------"
tput cup 10 35
echo "--------------------------------"
tput cup 15 0
echo "--------------------------------"
tput cup 15 35
echo "--------------------------------"
tput cup 20 0
echo "--------------------------------"
tput cup 20 35
echo "--------------------------------"
tput cup 25 0
echo "--------------------------------"
tput cup 25 35
echo "--------------------------------"


# Today - 1st Group - Left
tput cup 0 0; tput setaf 3;
  echo `date --date="0 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 0 17; tput setaf 2;
  echo "Now" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits`
tput cup 0 26; tput setaf 6;
  echo "±" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits`
tput cup 1 0; tput setaf 7;
  echo `conkyForecast --location=ARBA0009 -L en -d CT`
tput sgr0
tput cup 2 0
  echo "DP" `conkyForecast --location=ARBA0009 -L en -d DP --hideunits`
tput cup 2 8
  echo "UI" `conkyForecast --location=ARBA0009 -L en -d UI`
tput cup 2 14
  echo `conkyForecast --location=ARBA0009 -L en -d BR`
tput cup 2 24; tput setaf 6
  echo `conkyForecast --location=ARBA0009 -L en -d BD`
	tput sgr0
tput cup 3 0
  echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM`
tput cup 3 8
  echo `conkyForecast --location=ARBA0009 -L en -d WD` "@" `conkyForecast --location=ARBA0009 -L en -d WS`
tput cup 4 17
echo "Moon Phase -->"
tput sgr0;

# Today Forcast - 1st Group - Right
	tput cup 0 35; tput setaf 3
	  echo "Todays Forecast"
	tput cup 0 52; tput setaf 2
	  echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 0`
	tput cup 0 61; tput setaf 6
	  echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 0`
	tput cup 1 35
	tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=0`
	tput sgr0
	tput cup 2 35
	echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 0`
	tput cup 2 43
	echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 0`
	tput cup 2 51
	echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=0` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=0`
	tput cup 3 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 0`
	tput cup 3 44; tput setaf 3
	echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 0`
	tput cup 3 53; tput setaf 4
	echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 0`
	tput sgr0
	tput cup 4 35
	echo `conkyForecast --location=ARBA0009 -L en -d MP`
	tput sgr0;

# Day 1 - - 2nd Group - Left
tput cup 6 0; tput setaf 3
echo `date --date="1 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 6 17; tput setaf 2
echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 1`
tput cup 6 26; tput setaf 6
echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 1`
tput cup 7 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=1`
tput sgr0
tput cup 8 0
echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 1`
tput cup 8 8
echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 1`
tput cup 8 16
echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=1` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=1`
tput cup 9 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 1`
tput cup 9 9; tput setaf 3
echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 1`
tput cup 9 18; tput setaf 4
echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 1`
tput sgr0;

# Day 2 - - 2nd Group - Right
	tput cup 6 35; tput setaf 3
	echo `date --date="2 day" | awk '{print $1", "$3" "$2" "$6}'`
	tput cup 6 52; tput setaf 2
	echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 2`
	tput cup 6 61; tput setaf 6
	echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 2`
	tput cup 7 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=2`
	tput sgr0
	tput cup 8 35
	echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 2`
	tput cup 8 43
	echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 2`
	tput cup 8 51
	echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=2` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=2`
	tput cup 9 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 2`
	tput cup 9 44; tput setaf 3
	echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 2`
	tput cup 9 53; tput setaf 4
	echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 2`
tput sgr0;

# Day 3 - 3rd Group - Left
tput cup 11 0; tput setaf 3
echo `date --date="3 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 11 17; tput setaf 2
echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 3`
tput cup 11 26; tput setaf 6
echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 3`
tput cup 12 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=3`6
tput sgr0
tput cup 13 0
echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 3`
tput cup 13 8
echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 3`
tput cup 13 16
echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=3` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=3`
tput cup 14 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 3`
tput cup 14 9; tput setaf 3
echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 3`
tput cup 14 18; tput setaf 4
echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 3`
tput sgr0;

# Day 4 - 3rd Group - Right
	tput cup 11 35; tput setaf 3
	echo `date --date="4 day" | awk '{print $1", "$3" "$2" "$6}'`
	tput cup 11 52; tput setaf 2
	echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 4`
	tput cup 11 61; tput setaf 6
	echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 4`
	tput cup 12 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=4`
	tput sgr0
	tput cup 13 35
	echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 4`
	tput cup 13 43
	echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 4`
	tput cup 13 51
	echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=4` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=4`
	tput cup 14 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 4`
	tput cup 14 44; tput setaf 3
	echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 4`
	tput cup 14 53; tput setaf 4
	echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 4`
tput sgr0;

# Day 5 - 4th Group - Left
tput cup 16 0; tput setaf 3
echo `date --date="5 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 16 17; tput setaf 2
echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 5`
tput cup 16 26; tput setaf 6
echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 5`
tput cup 17 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=5`
tput sgr0
tput cup 18 0
echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 5`
tput cup 18 8
echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 5`
tput cup 18 16
echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=5` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=5`
tput cup 19 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 5`
tput cup 19 9; tput setaf 3
echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 5`
tput cup 19 18; tput setaf 4
echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 5`
tput sgr0;

# Day 6 - 4th Group - Right
	tput cup 16 35; tput setaf 3
	echo `date --date="6 day" | awk '{print $1", "$3" "$2" "$6}'`
	tput cup 16 52; tput setaf 2
	echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 6`
	tput cup 16 61; tput setaf 6
	echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 6`
	tput cup 17 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=6`
	tput sgr0
	tput cup 18 35
	echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 6`
	tput cup 18 43
	echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 6`
	tput cup 18 51
	echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=6` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=6`
	tput cup 19 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 6`
	tput cup 19 44; tput setaf 3
	echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 6`
	tput cup 19 53; tput setaf 4
	echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 6`
tput sgr0;

# Day 7 - 5th Group - Left
tput cup 21 0; tput setaf 3
echo `date --date="7 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 21 17; tput setaf 2
echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 7`
tput cup 21 26; tput setaf 6
echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 7`
tput cup 22 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=7`
tput sgr0
tput cup 23 0
echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 7`
tput cup 23 8
echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 7`
tput cup 23 16
echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=7` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=7`
tput cup 24 0; tput setaf 7
echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 7`
tput cup 24 9; tput setaf 3
echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 7`
tput cup 24 18; tput setaf 4
echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 7`
tput sgr0;

# Day 8 - 5th Group - Right
	tput cup 21 35; tput setaf 3
	echo `date --date="8 day" | awk '{print $1", "$3" "$2" "$6}'`
	tput cup 21 52; tput setaf 2
	echo "H" `conkyForecast --location=ARBA0009 -L en -d HT --hideunits --startday 8`
	tput cup 21 61; tput setaf 6
	echo "L" `conkyForecast --location=ARBA0009 -L en -d LT --hideunits --startday 8`
	tput cup 22 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d CT --startday=8`
	tput sgr0
	tput cup 23 35
	echo "CR" `conkyForecast --location=ARBA0009 -L en -d PC --startday 8`
	tput cup 23 43
	echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM  --startday 8`
	tput cup 23 51
	echo `conkyForecast --location=ARBA0009 -L en -d WD --startday=8` "@" `conkyForecast --location=ARBA0009 -L en -d WS --startday=8`
	tput cup 24 35; tput setaf 7
	echo `conkyForecast --location=ARBA0009 -L en -d SR  --startday 8`
	tput cup 24 44; tput setaf 3
	echo `conkyForecast --location=ARBA0009 -L en -d DL --startday 8`
	tput cup 24 53 tput setaf 4
	echo `conkyForecast --location=ARBA0009 -L en -d SS --startday 8`

## Back to the command prompt
tput sgr0; tput cup 25 0
```

Oh course I have various versions cfd (D=sister = Winnipeg) cfa (Alert NWT, Canada) and more:

[Alert, Nunavut, Canada]("https://en.wikipedia.org/wiki/Alert,_Nunavut") shown here:
[[img]http://s20.postimg.org/o9naqieq1/2013_10_12_20_52_42_558x510_Sector11.jpg[/img]](http://postimg.org/image/o9naqieq1/)

Better late than never: *Thank you, Habitual!* BTW, I still have a few conky's using it as well.

**EDIT:**
- Line 71 in the code mistakenly used   **--startday 0** - corrected
- Line 83 ```
echo "HM" `conkyForecast --location=ARBA0009 -L en - -d HM --startday 0`
```changed to```
echo "HM" `conkyForecast --location=ARBA0009 -L en -d HM `
```
- all instances of ```
-L en - -d
```changed to```
-L en -d
```

---

### Post by Vaphell on 2013-10-13
> my vph.py file was changed just a tad to include more colours - then didn't use them all - and added "os.system('clear')"
move* os.system('clear')* below the __main__ line where the program actually starts to run. It's a bit lame to do runtime stuff in the middle of definitions :-) And if you ever wanted to open vph in another script to use its classes and functions, you'd get a clear screen on *import vph* :)

> **GrouchyGaijin said:**
> Hey S11,

I'm surprised you don't have personal weather station and send your data to the Weather Underground.
I can't get my wife's home town.  There are no personal weather stations there.  The closest airport is 30 kilometers away.

What does os.system('clear') do?

Are you guys able to run the script without the .py?
When I type weather I get a message that:
```

The program 'weather' is currently not installed.  You can install it by typing:
sudo apt-get install weather-util

```

yes. this is copypasted from my terminal
```
$ weather 1
       Location: Falun, Sweden (60°35'59"N 15°37'59"E)
```

run
```
ln -s ~/path/to/weather.py ~/bin/weather
```
if ~/bin is in PATH it should work. By default ubuntu picks up the dir upon login and adds it to the PATH env var.


> 
```
	{
		"name": "Sanjo, Japan", 
		"type": "city", 
		"c": "JP",
		"zmw": "00000.7.47572",
		"tz": "Asia/Tokyo",
		"tzs": "JST",
		"l": "/q/zmw:00000.7.47572"
	}
```
yes, the script crashes pretty hard in this case. Looked at the data for that city - it is garbage and half is missing. Just open url by hand in the browser or *curl* it and see.
Lat/long conversion function fails because there is an empty string in json. I added exception to handle that.
```
def _lat_long( x, nsew ):
[COLOR="#0000FF"]    try:
        deg = float( x )
    except:
        return ''[/COLOR]
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )
```
if conversion to number fails, return empty string and be done with it. From now on the script will work, but the output won't be pretty.



Any ideas for additional features?
- running queries providing pretty list of results and allowing to add chosen location to the file
- some additional formatting options, eg fixed width, align, upper/lowercase

also after looking at the conkyweather stuff (hardcore amounts of micromanaging) i'd like to figure out how to control the cursor positioning, probably with this [http://docs.python.org/2/howto/curses.html](http://docs.python.org/2/howto/curses.html) but it would require a new kind of template.

---

### Post by Vaphell on 2013-10-13
script that queries the server and prints a pretty list of results (zmw/name)

```
#!/usr/bin/env python

import urllib2
import json
import sys

url = 'http://autocomplete.wunderground.com/aq?query={0}'

if __name__ == '__main__':

    if len(sys.argv) == 1:
        print 'argument missing'
        sys.exit(1)
    jdata = json.load( urllib2.urlopen( urllib2.Request( url.format( sys.argv[1] ) ) ) )
    results = jdata['RESULTS']
    for r in results:
        print '{zmw}\t{name}'.format( **r )
```


```
$ ./weather_qry.py Stockholm
00000.1.02485	Stockholm, Sweden
00000.1.02460	Stockholm Arlanda, Sweden
00000.1.02464	Stockholm Bromma, Sweden
04783.1.99999	Stockholm, Maine
07460.1.99999	Stockholm, New Jersey
57264.1.99999	Stockholm, South Dakota
78569.2.99999	Stockholm, Texas
54769.1.99999	Stockholm, Wisconsin
```

---

### Post by GrouchyGaijin on 2013-10-13
Killer - thanks V

---

### Post by Habitual on 2013-10-13
> **Sector11 said:**
> Habitual!!! ):P  Long time no see ... you changed your avatar! I would never have recognized you.  ;)

If you're a dinosaur, we're dino's together, but then I'm a dino by age - so my oldest son says!  I never gave up on conkyForecast.  When weather.com killed the free stuff and went "pay" - it did stop for some people.  People that kept their cache files in /tmp and lost them on the next boot.  I think that only lasted for a short while though because a lot came back and said it started working again.

I found your bash script and expanded on it, [that's it in my last post here with screenshots]("http://ubuntuforums.org/showthread.php?t=2178780&page=6&p=12814647#post12814647") - made it 10 days.

**cf** - by habitual - bent, folded and mutilated by  Sector11:

Better late than never: *Thank you, Habitual!* BTW, I still have a few conky's using it as well.
I just love that script. I had learned something new making it.
[B]
conkyForecast v2.24[/B] still won't go past 4 days with this output.
--ERROR: --startday set beyond forecast limit, reset to maximum of 4

Do I need another version? You know, us #OldGuysRule club members sometimes have "outdated" stuff. (because it still works?!)

Buenos Aires Argentina? Aren't you in the Northern Hemisphere, or are you thinking about a vacation? ;)

---

### Post by GrouchyGaijin on 2013-10-13
I dig it - the thread is expanding and taking on a life of its own.

---

### Post by GrouchyGaijin on 2013-10-13
> **Vaphell said:**
> 

Any ideas for additional features?
- running queries providing pretty list of results and allowing to add chosen location to the file
- some additional formatting options, eg fixed width, align, upper/lowercase



YES an option to add the chosen location to the weather_locations.txt file would be great!
As long as we are shouting out ideas, an option to run the script in C or in F would be cool.

---

### Post by Sector11 on 2013-10-13
> **Vaphell said:**
> move* os.system('clear')* below the __main__ line where the program actually starts to run. It's a bit lame to do runtime stuff in the middle of definitions :-) And if you ever wanted to open vph in another script to use its classes and functions, you'd get a clear screen on *import vph* :)

Got you on moving the *os.system('clear')* .. and I was so proud of myself for doing that.  I don't do scripts, I just bend fold and mutilate them once created.

It will take me a sec to get just where to plug that lat/long stuff in ... see line above  :D

**EDIT:**  *DUH*!  Too easy ... search for "_lat_long_"  BINGO! got it .  Thank you!

> **Vaphell said:**
> Any ideas for additional features?
- running queries providing pretty list of results and allowing to add chosen location to the file
- some additional formatting options, eg fixed width, align, upper/lowercase

also after looking at the conkyweather stuff (hardcore amounts of micromanaging) i'd like to figure out how to control the cursor positioning, probably with this [http://docs.python.org/2/howto/curses.html](http://docs.python.org/2/howto/curses.html) but it would require a new kind of template.

Yea, and that *hardcore amounts of micromanaging* came from Habitual ... I would never have figured that out, but once I saw the little 4 day script he did ... the rest was just an easy (well, not easy easy) "layout" tweak.

The best I can do here, not being a programmer, is:  I love templates and segregated files working together idea ... the latest for me comes down to:
[LIST][*]/home/sector11/bin/vph
[*]/home/sector11/bin/vph-api.key
[*]/home/sector11/bin/vph-weather_format.txt
[*]/home/sector11/bin/vph-weather_locations.txt[/LIST]

Easier to do things this way, more changes and I'll have to do with your scripts what I do with others.
vph2, vph3, etc...

Someone recently told me, delete all that old stuff and use this ... YEA RIGHT!  it's still here the new stuff renamed.  I'm a "script and conky" pack rat, I toss nothing out.  :D

---

### Post by Sector11 on 2013-10-13
> **Vaphell said:**
> script that queries the server and prints a pretty list of results (zmw/name)

Add one: /home/sector11/bin/vph-city
```
 13 Oct 13 | 12:20:41 ~
    $ vph-city Buenos Aires
00000.1.87582	Buenos Aires, Argentina
00000.3.78772	Buenos Aires, Costa Rica
00000.11.WMMPN	Buenos Aires, Mexico
00000.7.84405	Buenos Aires, Peru
00000.7.80308	Buenos Aires, Colombia
00000.4.78733	Buenos Aires, Nicaragua
00000.7.78717	Buenos Aires, Honduras
 
 13 Oct 13 | 12:21:00 ~
    $ 
```

AWESOME!!!!!

---

### Post by Sector11 on 2013-10-13
> **Habitual said:**
> I just love that script. I had learned something new making it.
**conkyForecast v2.24** still won't go past 4 days with this output.
--ERROR: --startday set beyond forecast limit, reset to maximum of 4

Do I need another version? You know, us #OldGuysRule club members sometimes have "outdated" stuff. (because it still works?!)

Buenos Aires Argentina? Aren't you in the Northern Hemisphere, or are you thinking about a vacation? ;)

I just love that script and learned something stealing it ... ummmm absconding with it ... err ...  carbon-copying it ... still have it/them:
[LIST][*]/home/sector11/bin/4days
[*]/home/sector11/bin/4days_orig[/LIST]

OK, this is where having the "old" 'pay once for life' XOAP_LICENCE_KEY & XOAP_PARTNER_ID keys to get the 10 day forecast comes in handy.  While the "free" service was dropped (and continued to work if you had the "cache" files) the /.conkyForecast.config files that had the paid for 10 day service continues to this day, and I can even create new locations.  Not sure if that function will work for you though.  Can you get weather for Buenos Aires ( ARBA0009 ) with your script?

We have the same version:
```
 13 Oct 13 | 12:40:02 ~
    $ conkyForecast --version
conkyForecast v2.24
 
 13 Oct 13 | 12:40:09 ~
    $ 
```
Hard part is if the KEYS became public ... they'd kill them as well.  Imagine 500 calls a day from the same KEYS from 500 different ISP's!  Would not take long and they'd be gone.

***Say what?  No PM?***

Ummmm been here in BsAs for almost 14 years, but I am a Canuck.

---

### Post by GrouchyGaijin on 2013-10-13
> **Sector11 said:**
> 
Someone recently told me, delete all that old stuff and use this ... YEA RIGHT!  it's still here the new stuff renamed.  I'm a "script and conky" pack rat, I toss nothing out.  :D

Jeez what kind of a goofball would tell you to do that?? ;-)

---

### Post by Sector11 on 2013-10-13
> **GrouchyGaijin said:**
> YES an option to add the chosen location to the weather_locations.txt file would be great!
As long as we are shouting out ideas, an option to run the script in C or in F would be cool.

+1 on the C/F one


*Alias this one:*
```
 13 Oct 13 | 13:01:27 ~
    $ vph-city Calgary>>~/bin/vpn-city-list.txt && medit ~/bin/vpn-city-list.txt
 
 13 Oct 13 | 13:02:36 ~
    $ vph-city buenos Aires>>~/bin/vpn-city-list.txt && medit ~/bin/vpn-city-list.txt
 
 13 Oct 13 | 13:03:02 ~
```
**/home/sector11/bin/vpn-city-list.txt**
```
00000.1.71877	Calgary, Canada
00000.9.71877	Calgary International, Canada
00000.1.71860	Calgary Springbank, Canada
00000.1.87582	Buenos Aires, Argentina
00000.3.78772	Buenos Aires, Costa Rica
00000.11.WMMPN	Buenos Aires, Mexico
00000.7.84405	Buenos Aires, Peru
00000.7.80308	Buenos Aires, Colombia
00000.4.78733	Buenos Aires, Nicaragua
00000.7.78717	Buenos Aires, Honduras
```

):P:lolflag::lolflag:

Opps - Have to rename that vph-cities-list.txt  :oops:

---

### Post by Sector11 on 2013-10-13
> **GrouchyGaijin said:**
> Jeez what kind of a goofball would tell you to do that?? ;-)

Look in a mirror, the guy staring back is the last in a long line ...  :lolflag::lolflag:

---

### Post by Vaphell on 2013-10-13
i am thinking how to do switching metric/imperial units on the fly. Currently it looks quite painful because of the inconsistent structure of the data
in current_observation you get something like this: temp_f temp_c
but in forecast you get something like this high { celsius, fahrenheit} }, low {celsius, fahrenheit} - tidy groups of the same value expressed in different units. Nice.
In other words i can't make nice assumptions that would work everywhere and am pretty much forced to micromanage all these cases with C/F, kph/mph, mi/km etc by hand.


quick and dirty solution would be to clone the template with different sets of units and parametrize the script to read template name too.

---

### Post by Sector11 on 2013-10-13
> **Vaphell said:**
> i am thinking how to do switching metric/imperial units on the fly. Currently it looks quite painful because of the inconsistent structure of the data
in current_observation you get something like this: temp_f temp_c
but in forecast you get something like this high { celsius, fahrenheit} }, low {celsius, fahrenheit} - tidy groups of the same value expressed in different units. Nice.
In other words i can't make nice assumptions that would work everywhere and am pretty much forced to micromanage all these cases with C/F, kph/mph, mi/km etc by hand.


quick and dirty solution would be to clone the template with different sets of units and parametrize the script to read template name too.

Doesn't wunderground as you (can't remember) what units you want when you sign up for a key?

---

### Post by GrouchyGaijin on 2013-10-13
I don't think the key is tied to units.  When you visit their site they either know (based on cookies) or guess (based on ip address) at least that is how I think it works.
I guess we could sign up for two keys and use one key in a F template and one key in a C template.

---

### Post by drmrgd on 2013-10-13
> **Vaphell said:**
> i am thinking how to do switching metric/imperial units on the fly. Currently it looks quite painful because of the inconsistent structure of the data
in current_observation you get something like this: temp_f temp_c
but in forecast you get something like this high { celsius, fahrenheit} }, low {celsius, fahrenheit} - tidy groups of the same value expressed in different units. Nice.
In other words i can't make nice assumptions that would work everywhere and am pretty much forced to micromanage all these cases with C/F, kph/mph, mi/km etc by hand.


quick and dirty solution would be to clone the template with different sets of units and parametrize the script to read template name too.

Wow!  This thread has blown up since Friday.  Love how this thing is grown!

I was thinking about this too as (as embarrassing as it is) I'm in one of the few countries smart enough to use the metric system.  One thought I had was to expand the dict and the template file to capture both metric and American measurements, and use a command line option (or hardcoded option in a variable so you don't have to enter the option each time you call the script) to only print one or the other.  Been out of town all weekend and haven't had chance to think about this too much more, but I think this might not be too difficult.  Maybe use different leading characters in the format table to alternatively call the format if need be (or some keyword identifier?).

The other clunky way I thought about it was to just code the conversions within the script and have it do the work.  Not sure that's very elegant though.

---

### Post by Habitual on 2013-10-13
> **Sector11 said:**
> I just love that script and learned something stealing it ... ummmm absconding with it ... err ...  carbon-copying it ... still have it/them:
[LIST]
[*]/home/sector11/bin/4days 
[*]/home/sector11/bin/4days_orig 
[/LIST]

OK, this is where having the "old" 'pay once for life' XOAP_LICENCE_KEY & XOAP_PARTNER_ID keys to get the 10 day forecast comes in handy.  While the "free" service was dropped (and continued to work if you had the "cache" files) the /.conkyForecast.config files that had the paid for 10 day service continues to this day, and I can even create new locations.  Not sure if that function will work for you though.  Can you get weather for Buenos Aires ( ARBA0009 ) with your script?

We have the same version:
```
 13 Oct 13 | 12:40:02 ~
    $ conkyForecast --version
conkyForecast v2.24
 
 13 Oct 13 | 12:40:09 ~
    $ 
```
Hard part is if the KEYS became public ... they'd kill them as well.  Imagine 500 calls a day from the same KEYS from 500 different ISP's!  Would not take long and they'd be gone.

***Say what?  No PM?***

Ummmm been here in BsAs for almost 14 years, but I am a Canuck.

I turned on PMs just for *you* ;)

My key I believe is from an Xfce dev project. it always works.
I have a couple of rem'd out #XOAP_PARTNER_ID but haven't messed with it in ages.
4 days is okay by me. I'm not **that** "Type A" (My Wife would disagree)

```
/usr/bin/conkyForecast --location=ARBA0009 -d CT
Mostly Cloudy

```

I'm glad someone got some mileage out of my forecast script.
That tput is a neat trick.

As for
> **Sector11 said:**
> Yea, and that *hardcore amounts of micromanaging* came from Habitual
*Smile* when ya say that. ;)

Peace!

---

### Post by Sector11 on 2013-10-13
> **Habitual said:**
> I turned on PMs just for *you* ;)

4 days is okay by me. I'm not **that** "Type A" (My Wife would disagree)

Too late I lost interest!
Your wife must be related to mine.

... and you can create cache files ... PERFECT!

> **Habitual said:**
> I'm glad someone got some mileage out of my forecast script.
That tput is a neat trick.

I blame you ... you got me started.

> **Habitual said:**
> As for

*Smile* when ya say that. ;)

Peace!

Like: :D , O:) or \\:D/

---

### Post by Sector11 on 2013-10-13
@ GrouchyGaijin

I think you are right. They read where you are from and force feed you what they think you want?

Will Smith voice in ID4
[QUOTE=S11 impersonating Will Smith in ID4]AND WHY THE *HE"double-hockey-sticks"** DOES GOOGLE THINK I AM IN A FRENCH COUNTRY![/QUOTE]

Just another thing about the net to add to my hate list ... 

What if I want options!  What if I want *xyz.com*, in English and not *xyz.com.ar* in Spanish ... or Google who really misses the boat: *xyz.com.fr *??????????????????

* can't swear here.
{rant over}

---

### Post by Habitual on 2013-10-14
> **Sector11 said:**
> I blame you ... you got me started.

There are worse habits a man could have.
I've had more than most, hence the Nick.

Today, we are grateful.

Thanks for the Christmas present.

John

---

### Post by Sector11 on 2013-10-14
> **Habitual said:**
> There are worse habits a man could have.
I've had more than most, hence the Nick.

Today, we are grateful.
Thanks for the Christmas present.

So true ... we all have our share ... and 'de nada' - least I could do.

---

### Post by Vaphell on 2013-10-16
check this thing out

```
#!/usr/bin/env python

import codecs
import re
import urllib2
import json
import sys
import os
import locale

def_url = { 'url': 'http://api.wunderground.com/api/{key}/{dataset}/q/{location}.json' }

pretty_units = {   'f': u'\u00b0F',   'c' : u'\u00b0C',
                 'mph': ' mph',       'kph': ' km/h',
                  'mi': ' mi',         'km': ' km',
                  'in': ' in',         'mm': ' mm',
                  'cm': ' cm',         'mb': ' hPa' }

field_rgx = r'\{[^.}]*[a-z]+[^.}]*\}'

# http://misc.flogisoft.com/bash/tip_colors_and_formatting
class Term:
    End       = '\033[0m'
    Default   = '\033[39m'
    B         = '\033[1m'
    Black     = '\033[30m'
    Red       = '\033[31m'
    Green     = '\033[32m'
    Yellow    = '\033[33m'
    Blue      = '\033[34m'
    Magenta   = '\033[35m'
    Cyan      = '\033[36m'
    LGray     = '\033[37m'
    LRed      = '\033[91m'
    LGreen    = '\033[92m'
    LYellow   = '\033[93m'
    LBlue     = '\033[94m'
    LMagenta  = '\033[95m'
    LCyan     = '\033[96m'
    White     = '\033[97m'

def get_unit_set( idx, units ):
    return dict( (k.lstrip('--'), units[k][idx]) for k in units )

# params
def params( args, loc ):
    avail = ( '--help', '--info', '--locations', '--cls' )
    units = {     '--temp': ( 'f','c' ),
              '--pressure': ( 'in', 'mb' ),
                '--precip': ( 'in', 'mm' ),
                  '--snow': ( 'in', 'cm' ),
                 '--speed': ( 'mph', 'kph' ),
              '--distance': ( 'mi', 'km' ) }

    pdict = { 'loc_idx': 0, 'units': {} }
    loc_c = loc[0].split( '_' )[-1]
    u_idx = 0 if loc_c in ('US','MM','LR') else 1
    pdict['units'] = get_unit_set( u_idx, units )  
    for p in args:
        if p in avail:
            pdict[p] = True
        elif p == '--imperial':
            pdict['units'] = get_unit_set( 0, units )
        elif p == '--metric':
            pdict['units'] = get_unit_set( 1, units )
        elif p.startswith( tuple( units.keys() ) ):
            k, v = p.split('=')
            v = v.lower()
            pdict['units'][k.lstrip('--')] = v
        else:
            try:
                pdict['loc_idx'] = int(p)               
            except:
                pass
    return pdict
    
# show available params
def show_help( args ):
    print 'usage: {0} [option(s)] [location_id]'.format( args[0] )
    print '    --help\t\tthis help'
    print '    --cls\t\tclear screen'
    print '    --info\t\tshow debug info, data structure'
    print '    --locations\t\tshow available locations (id, code, description)'
    print '    --metric\t\tuse metric units'
    print '    --imperial\t\tuse imperial units'
    print '    --temp=UNIT\t\toverride unit of temperature (c, f)'
    print '    --pressure=UNIT\toverride unit of pressure (mb, in)'
    print '    --precip=UNIT\toverride unit of precipitation (mm, in)'
    print '    --snow=UNIT\t\toverride unit of snow (cm, in)'
    print '    --speed=UNIT\toverride unit of speed (kph, mph)'
    print '    --distance=UNIT\toverride unit of distance (km, mi)'
 

# function showing data tree
def show_struct( x, name='data structure:', lvl=0, offset=4 ):
    ln = u' '*lvl*offset+'{0}'
    print ln.format( name )
    if isinstance( x, list ):
        show_struct( x[0], '*', lvl=lvl+1 )
    elif isinstance( x, dict ):
        for k in sorted( x.keys() ):
            show_struct( x[k], k, lvl=lvl+1 )

# load json
def load_weather_data( url ):
    return json.load( urllib2.urlopen( urllib2.Request( url['url'].format( **url ) ) ) )

# debug/struct info
def dump_info( url, w_data ):
    print 'key: {key}\nlocation: {location}\nurl: {url}\n'.format( **url )
    for k in w_data.keys():
         show_struct( w_data[k][0], k )

# locations file
def load_locations( f ):
    loc = []
    for ln in codecs.open( f, 'r', 'utf-8' ):
        if ln.startswith('#'): 
            continue
        elif '=':
            d = {}
            d['id'], d['desc'] = ( x.strip() for x in ln.split('=', 1) )
            loc.append( d )
    return loc

# print locations    
def print_locations( l ):
    print 'Available locations:'
    for idx in range(0, len(l)):
      print u'{idx}:\t{id} ({desc})'.format( idx=idx, **l[idx] )

# def parse format file
def load_format_and_data( f, url, settings ):
    dataset = { 'forecast' :  { 'path': 'forecast/simpleforecast/forecastday' },
                'astronomy':  { 'path': 'moon_phase' },
                'conditions': { 'path': 'current_observation' } }
    print_data = []  
    for ln in codecs.open( f, 'r', 'utf-8' ):
        ln = ln.rstrip()
        if ln.startswith('#'): 
            continue
        if ln.startswith('@'):
            pass
        elif ln.startswith('!'):
            dset = ln.lstrip('! ')
            format = { 'dataset': dset, 'template':'', 'src':[] }       
            print_data.append( format )
        else:
            format['template'] = ( '\n'.join( ( format['template'], ln ) ) if len( format['template'] )>0 else ln )
    
    url['dataset'] = '/'.join( set( x['dataset'] for x in print_data ) )
    raw_data = load_weather_data( url )
    n_data = {}
    for ds in set( x['dataset'] for x in print_data ):
        n_data[ds] = []
        for d in wdata_get( raw_data, dataset[ds]['path'] ):
             n_data[ds].append( normalize_data( d ) )  

    for pd in print_data:
        pd['src'] = n_data[pd['dataset']]
    return ( n_data, print_data )


# function to get nodes/values from the data tree
def wdata_get( start, path ):
    n = start
    if not isinstance( path, list ):
        path = path.split('/')
    for p in path:
        if p:
            n = n[p]
    if   isinstance( n, dict ):           return [n]
    elif isinstance( n, (str, unicode) ): return n.strip()
    return n


# functions to tweak some values, based on name
def _lat_long( x, nsew ):
    try:
        deg = float( x )
    except:
        return ''
    c = ( nsew[1] if deg<0 else nsew[0] )
    deg = int( abs(deg*3600) )
    d = deg/3600
    m = deg%3600/60
    s = deg%60
    return u'{0}\u00b0{1:02d}\'{2:02d}"{3}'.format( d, m, s, c )

def latitude( x ):  return _lat_long( x, 'NS' )
def longitude( x ): return _lat_long( x, 'EW' )


# normalize data to coherent format
def normalize_data( d, path='' ):
    _units = tuple( '_'+u for u in pretty_units )
    if isinstance( d, list ):
        pass
    else:
        r = {}
        p = path+'_' if path else ''
        for k in d.keys():
            if   isinstance( d[k], dict ):
                if k == 'display_location':
                    r.update( normalize_data( d[k], p+'location' ) )
                elif k == 'observation_location':
                    r.update( normalize_data( d[k], p+'observation' ) )
                elif k == 'moon_phase':
                    r.update( normalize_data( d[k], 'astronomy' ) )
                else:
                    r.update( normalize_data( d[k], p+k ) )     
            elif k.endswith( _units ):
                kn, ku = k.rsplit( '_', 1 )            
                r[p+'/'.join( (kn, ku) )] = d[k]
            elif k in pretty_units:
                r[path+'/'+k] = d[k]
            elif k in ( 'fahrenheit', 'celsius' ):
                r[path+'/'+k[0]] = d[k]
            elif k in ( 'precip_1hr_metric', 'precip_today_metric' ):
                r[p+k.rsplit('_', 1 )[0]+'/mm'] = d[k]
            elif k == 'ageOfMoon':
                r[p+'age_of_moon'] = d[k]
            elif k == 'phaseofMoon':
                r[p+'phase_of_moon'] = d[k]
            elif k == 'percentIlluminated':
                r[p+'percent_illuminated'] = d[k]
            else:
                r[p+k] = d[k]
    return r

# return value with a proper unit
def get_value( d, k, settings ):
    if k not in d:
        try:
            ku = [ k+'/'+uv for ut, uv in settings['units'].items() if k+'/'+uv in d ][0]
            return get_value( d, ku, settings )
        except:
            return ''
    elif '/' in k:
        ku = k.rsplit('/')[1]
        return u'{v}{u}'.format( k=k, v=d[k], u=pretty_units[ku] )
    elif   'latitude'  in k:
        return latitude( d[k].strip() )
    elif 'longitude' in k:
        return longitude( d[k].strip() )
    else:
        return d[k]
    return v

# output
def print_output( pd, f_obj, settings ):
   for d in pd:
        for src in d['src']:
            t = d['template']
            pdict = dict( (k, get_value( src, k, settings ) ) for k in src.keys() )
            addkeys = [ x.rsplit('/', 1)[0] for x in src.keys() if '/' in x ]
            addvalues = [ get_value( src, x.rsplit('/', 1)[0], settings) for x in src.keys() if '/' in x ]
            add_dict = dict( zip( addkeys, addvalues) )     
            pdict.update( add_dict )
            print t.format( TERM=f_obj, **pdict )

    

# --------- main ---------------------

if __name__ == '__main__':
    loc = locale.getdefaultlocale()

# settings (--help, --info)
    settings = params( sys.argv[1:], locale.getdefaultlocale() )
    
    if '--cls' in settings:
        os.system( 'clear' )
    
    if '--help' in settings:
        show_help( sys.argv )
        sys.exit(0)
    
    url = def_url.copy()
    script_dir = os.path.dirname( os.path.realpath(__file__) )
    locations = load_locations( script_dir + '/weather_locations.txt' )
    
    if '--locations' in settings:
        print_locations( locations )
        sys.exit(0)
    url['key'] = open( script_dir + '/api.key' ).read().strip()
    if settings['loc_idx'] < len(locations):
        l_idx = settings['loc_idx']
    else:
        print 'warning: location id out of range, using default'
        l_idx = 0
    url['location'] = locations[l_idx]['id'].replace(' ', '%20' )
    format_file = script_dir + '/weather_format.txt'
      
    w_data, print_data = load_format_and_data( format_file, url, settings )    
   
    if '--info' in settings:
        print_locations( locations )
        dump_info( url, w_data )
        sys.exit(0)

    print_output( print_data, Term(), settings )

```


```

! conditions
#-------------------------------------------------------------------------------------------------
{TERM.LCyan}       Location:{TERM.End} {TERM.B}{TERM.LGreen}{location_full}{TERM.End} {TERM.LGreen}({location_latitude} {location_longitude}){TERM.End}
{TERM.LCyan}Weather station:{TERM.End} {TERM.B}{TERM.LGreen}{observation_city}, {observation_country}{TERM.End} {TERM.LGreen}({observation_latitude} {observation_longitude})
{TERM.LCyan}           Time:{TERM.End} {TERM.B}{TERM.LGreen}{observation_time_rfc822}{TERM.End}
{TERM.LCyan}     Conditions:{TERM.End} {TERM.B}{TERM.Yellow}{weather}{TERM.End}
{TERM.LCyan}    Temperature:{TERM.End} {TERM.B}{TERM.Yellow}{temp}{TERM.End}, feels like {TERM.B}{TERM.Yellow}{feelslike}{TERM.End}
{TERM.LCyan}           Wind:{TERM.End} {TERM.B}{TERM.Yellow}{wind}{TERM.End}, from {wind_dir}
{TERM.LCyan}  Precipitation:{TERM.End} {TERM.B}{TERM.Yellow}{precip_today}{TERM.End} today
{TERM.LCyan}       Pressure:{TERM.End} {TERM.B}{TERM.Yellow}{pressure}{TERM.End}
{TERM.LCyan}       Humidity:{TERM.End} {TERM.B}{TERM.Yellow}{relative_humidity}{TERM.End}
{TERM.LCyan}      Dew point:{TERM.End} {TERM.B}{TERM.Yellow}{dewpoint}{TERM.End}
#-------------------------------------------------------------------------------------------------
! astronomy
#-------------------------------------------------------------------------------------------------
{TERM.LCyan}            Sun:{TERM.End} {TERM.B}{TERM.Yellow}{sunrise_hour}:{sunrise_minute}{TERM.End} - {TERM.B}{TERM.Yellow}{sunset_hour}:{sunset_minute}{TERM.End}
{TERM.LCyan}           Moon:{TERM.End} {TERM.B}{TERM.Yellow}{phase_of_moon} ({percent_illuminated}%){TERM.End}         
#-------------------------------------------------------------------------------------------------
! forecast
{TERM.LYellow}{date_weekday}, {date_monthname} {date_day}, {date_year}:{TERM.End}
 {TERM.LBlue}  {conditions}, high {high}, low {low}
   Winds {avewind} km/h from the {avewind_dir}, max {maxwind}{TERM.End}

```
i removed the need for the @ line and exact paths (i hardcoded name -> data relation in the script, just use 'conditions' or 'astronomy' or 'forecast' in the ! line ) and heavily reshuffled data because it was an incoherent mess. I flattened the structure and renamed tons of stuff to normalize everything and shorten long identifiers. Available keywords can be seen when the script is run with **--info**

In the output of **--info** there are plenty of pairs in the NAME/UNIT format (eg temp/f, temp/c). If you use one of them explicitly the value will use the UNIT, but you can also the skip /UNIT part (temp) and the script will pick the unit that is set as the default for that script execution. By default script choses metric/imperial set of units based on locale (USA, Liberia, Myanmar = imperial), but that can be overriden with **--metric** or **--imperial** and/or selectively overriden with **--CATEGORY=UNIT**. if you want to combine both methods, do it in this order: --metric/--imperial --CATEGORY=unit
--help has all the information what categories/units are there.

I also added **--cls** to clear screen if needed and extended the color list to match the sector's one, with slight changes (name Lyellow imo sucked ass so i changed it to LYellow, etc :-) )

---

### Post by GrouchyGaijin on 2013-10-16
> **Vaphell said:**
> check this thing out


i removed the need for the @ line and exact paths (i hardcoded name -> data relation in the script, just use 'conditions' or 'astronomy' or 'forecast' in the ! line ) and heavily reshuffled data because it was an incoherent mess. I flattened the structure and renamed tons of stuff to normalize everything and shorten long identifiers. Available keywords can be seen when the script is run with **--info**

In the output of **--info** there are plenty of pairs in the NAME/UNIT format (eg temp/f, temp/c). If you use one of them explicitly the value will use the UNIT, but you can also the skip /UNIT part (temp) and the script will pick the unit that is set as the default for that script execution. By default script choses metric/imperial set of units based on locale (USA, Liberia, Myanmar = imperial), but that can be overriden with **--metric** or **--imperial** and/or selectively overriden with **--CATEGORY=UNIT**. if you want to combine both methods, do it in this order: --metric/--imperial --CATEGORY=unit
--help has all the information what categories/units are there.

I also added **--cls** to clear screen if needed and extended the color list to match the sector's one, with slight changes (name Lyellow imo sucked ass so i changed it to LYellow, etc :-) )

My man!
COOL!!

I'm working at the moment, but will play with this tonight.

(Next thing you know, you'll be packaging this in a PPA like K did with his conky scripts.)

Myanmar = imperial, I did not know that.

---

### Post by Vaphell on 2013-10-16
> Myanmar = imperial, I did not know that. 

in general it's a mess but this says these 3 countries are most backwards when it comes to metrication
[http://en.wikipedia.org/wiki/Metrication](http://en.wikipedia.org/wiki/Metrication)
and if someone happens to dislike the quick and dirty script defaults, there are switches :-)

---

### Post by drmrgd on 2013-10-16
Wow, Vaphell, you've really outdone yourself this time!  This is fantastic!  I can't believe how many functions and features you added, and they all work great and conveniently!  I wish I had more time to play with this, but so far, I've loaded up 3 or 4 locations (using the convenient location query script you put together...thanks for that too!), and everything's working great!  

From a totally OCD person such as myself, the only recommendation I would make is to use 'getopt' for the cli options handling so that you can handle bad args.  If you feed the script any argument that doesn't really exist at the moment, it happily chugs along without raising an error, which may or may not be what you want, and given all the neat and handy options we can use now, there is a potential for mistakes.

Amazing work Vaphell!

---

### Post by Vaphell on 2013-10-16
yeah i know i should use something more robust for parameter handling. I spent so much time on data standarization and the automatic choice of units  (2 days of poking around and thinking how to overcome inconsistent structure of the data) that i had no mental strength left to push for something more elegant. I hacked out quick and dirty solution that is usable, that's why currently there are only params in the long form --xxx[=yyy], because that makes any param in the param list self contained and lazy split('=') returns relevant chunks.

I'll look into getopts when i regain some mental juice :-)

---

### Post by GrouchyGaijin on 2013-10-16
I'm getting the weather but I also get this right after the moon information: 
I gave the script the original name of nwx.py (new weather) ;-)
```

Traceback (most recent call last):
  File "/home/grouchygaijin/scripts/newwx/nwx.py", line 302, in <module>
    print_output( print_data, Term(), settings )
  File "/home/grouchygaijin/scripts/newwx/nwx.py", line 260, in print_output
    print t.format( TERM=f_obj, **pdict )
ValueError: Single '{' encountered in format string

```

---

### Post by Vaphell on 2013-10-16
well, it says you have an unpaired '{' somewhere which confuses the format function using {X} placeholders.

---

### Post by GrouchyGaijin on 2013-10-16
**[COLOR=#ff0000]NEVER MIND - [/COLOR]**I found it.  The problem was in the weather_format.txt.
I was indeed missing a } at the end of the last line.

---

### Post by GrouchyGaijin on 2013-10-16
Houston: All systems go

       Location: Falun, Sweden (60°35'59"N 15°37'59"E)
Weather station: Kämparvet, Falun, SWEDEN (60°36'22"N 15°38'20"E)
           Time: Wed, 16 Oct 2013 22:42:10 +0200
     Conditions: Overcast
    Temperature: 4.3°C, feels like 4°C
           Wind: 0.0 km/h, from ESE
  Precipitation: 0 mm today
       Pressure: 1008 hPa
       Humidity: 83%
      Dew point: 2°C
            Sun: 7:40 - 17:43
           Moon: Waxing Gibbous (95%)
Wednesday, October 16, 2013:
   Partly Cloudy, high 7°C, low 4°C
   Winds 5 km/h km/h from the SSE, max 8 km/h
Thursday, October 17, 2013:
   Rain, high 7°C, low -2°C
   Winds 6 km/h km/h from the ENE, max 10 km/h
Friday, October 18, 2013:
   Partly Cloudy, high 6°C, low -3°C
   Winds 13 km/h km/h from the WNW, max 14 km/h
Saturday, October 19, 2013:
   Mostly Cloudy, high 4°C, low -4°C
   Winds 3 km/h km/h from the West, max 6 km/h

---

### Post by Sector11 on 2013-10-16
> **Vaphell said:**
> check this thing out

I also added **--cls** to clear screen if needed and extended the color list to match the sector's one, with slight changes (name Lyellow imo sucked ass so i changed it to LYellow, etc :-) )

Just got here.  Yea I agree Lyellow looks "sick" - mine have changed "lcolourname"

Now *I have to try this new one* ... back later ... not a lot of free time 'right now' ...

---

### Post by Vaphell on 2013-10-18
@ sector
your conkyweather something, cleaned up a bit ;-) My teeth did hurt from looking at it so i figured out i'll do something for my health ;-)
Should work but i can't know that as i don't have the whole thing configured :-) Layout looks ok to me with fake filler

```
#!/bin/bash
# --- original ---
# 4 Day Weather forecast script for Boardman, OH
# Written by JJ ie: Habitual
# 11.01.2010 12:10:07
# --- Edited by Sector11 ---
# today & 8 Day Forecast for Buenos Aires Argentina
# ~/bin/cf
# Last edit: 24 Mar 13 | 14:10:06 - UTC -3
# conkyForecast by: Kaivalagi

# tput Color Capabilities:
#     tput setab [1-7] &#8211; Set a background color using ANSI escape
#     tput setb [1-7] &#8211; Set a background color
#     tput setaf [1-7] &#8211; Set a foreground color using ANSI escape
#     tput setf [1-7] &#8211; Set a foreground color

# tput Text Mode Capabilities:
#     tput bold &#8211; Set bold mode
#     tput dim &#8211; turn on half-bright mode
#     tput smul &#8211; begin underline mode
#     tput rmul &#8211; exit underline mode
#     tput rev &#8211; Turn on reverse mode
#     tput smso &#8211; Enter standout mode (bold on rxvt)
#     tput rmso &#8211; Exit standout mode
#     tput sgr0 &#8211; Turn off all attributes

# Color Code for tput:
#     0 &#8211; Black
#     1 &#8211; Red
#     2 &#8211; Green
#     3 &#8211; Yellow
#     4 &#8211; Blue
#     5 &#8211; Magenta
#     6 &#8211; Cyan
#     7 &#8211; White

declare -A colors
colors=(
         [black]=0
         [red]=1
         [green]=2
         [yellow]=3
         [blue]=4
         [magenta]=5 
         [cyan]=6 
         [white]=7
       )

clscreen()  { tput clear; }
pos()       { tput cup "$@"; }
fgcolor()   { tput setaf "${colors[$1],,}"; }
bgcolor()   { tput setab "${colors[$1],,}"; }
resetall()  { tput sgr0; }

# label+value
conqry()
{
  local label=$1; shift
  local var=$1; shift
  local val=$( conkyForecast --location="$loc" -L en -d "$var" "$@" )
  [[ -z $label ]] && pf="%s%s" || pf="%s %s"
  printf "$pf" "$label" "$val"
}

# draw lines
lines()
{
  fgcolor white
  for y in {10..25..5}
  do
    for x in 0 35
    do
      pos "$y" "$x"
      printf -- "--------------------------------"
    done
  done
  resetall
}

# current conditions
current()
{
  pos 0 0;   fgcolor yellow;  date +'%a, %d %b %Y'
  pos 0 17;  fgcolor green;   conqry "Now" HT --hideunits
  pos 0 26;  fgcolor cyan;    conqry "±"   LT --hideunits
  pos 1 0;   fgcolor white;   conqry ""    CT
  resetall
  pos 2 0;                    conqry "DP"  DP --hideunits
  pos 2 8;                    conqry "UI"  UI
  pos 2 14;                   conqry ""    BR
  pos 2 24;  fgcolor cyan;    conqry ""    BD
  resetall
  pos 3 0;                    conqry "HM"  HM --startday 0
  pos 3 8;                    conqry ""    WD
                              conqry " @"  WS  
  pos 4 17;                   printf "Moon Phase -->"
  pos 4 35;                   conqry ""    MP
  resetall
}

# forecast
forecast()
{
  local day=$1
  local y=$2 
  local x=$3
  local label=$4;
  
  pos $((y))   $((x));    fgcolor yellow;  printf "$label"
  pos $((y))   $((x+17)); fgcolor green;   conqry "H"  HT --startday "$day" --hideunits
  pos $((y))   $((x+26)); fgcolor cyan;    conqry "L"  LT --startday "$day" --hideunits
  pos $((y+1)) $((x));	  fgcolor white;   conqry ""   CT --startday "$day"
  resetall
  pos $((y+2)) $((x));                     conqry "CR" PC --startday "$day"
  pos $((y+2)) $((x+8));                   conqry "HM" HM --startday "$day"
  pos $((y+2)) $((x+16));                  conqry ""   WD --startday "$day"
                                           conqry " @" WS --startday "$day"
  pos $((y+3)) $((x));    fgcolor white;   conqry ""   SR --startday "$day"
  pos $((y+3)) $((x+9));  fgcolor yellow;  conqry ""   DL --startday "$day"
  pos $((y+3)) $((x+18)); fgcolor blue;    conqry ""   SS --startday "$day"
  resetall
}


#=============================================================================================

loc=${1:-ARBA0009} # if no param, default to ARBA0009

# Clear the screen
clscreen

pos 5 0;   fgcolor blue;   conqry "-->" CN
pos 5 35;  fgcolor blue;   conqry "-->" CO

# Draw the lines
lines

#current
current

# forecast 0
forecast 0 0 35 "Todays forecast"

# forecast 1-8
for day in {1..8}
do
  y=$(( (day+1)/2*5+1 ))
  x=$(( (day+1)%2*35 ))
  forecast "$day" "$y" "$x" "$( date -d "$day day" +'%a, %d %b %Y' )"
done

## Back to the command prompt
resetall
pos 25 0


```
are current conditions supposed to use --startday 0, the same as forecast for today?

---

### Post by Sector11 on 2013-10-18
[SIZE=6][CENTER]**[COLOR="#006400"]NICE!!!!!!!!![/COLOR]**
**[COLOR="#006400"]Thank you![/COLOR]**[/CENTER][/SIZE]

> **Vaphell said:**
> @ sector
your conkyweather something, cleaned up a bit ;-) My teeth did hurt from looking at it so i figured out i'll do something for my health ;-)
Should work but i can't know that as i don't have the whole thing configured :-) Layout looks ok to me with fake filler

cough cough spit spit sputter sputter ...
```
# Written by JJ ie: Habitual
# 11.01.2010 12:10:07
```
**^^^^^^^^^^^^^^^**Blame him
:lolflag:   Actually - Credit him, I do and always will.  Like JJ, I learned a lot with that, even if it did make your teeth hurt!
We all start someplace.

**What "fake filler" ????**

> **Vaphell said:**
> are current conditions supposed to use --startday 0, the same as forecast for today?

Calling conkyForecast ----
- with NO "--startday 0" gives "current" information 
- with "startday 0" gives what is forecasted for today

Be careful with *--startday 0* for temperatures ... *see below* for the differences of using HT and LT for today, there are 4 options.

People have been know to use "Today: LT &#8211; Feels Like Temp &#8211; WITHOUT: &#8220;&#8211;startday=0&#8243; [--datatype LT]" thinking they are getting the "Forecast Low" for today - NOT!

Yea that looks really good ... the same - except for that hot pink (magenta)  YUK!
[[img]http://s20.postimg.org/iajary2a1/2013_10_18_14_59_03_1226x575_Sector11.jpg[/img]](http://postimg.org/image/iajary2a1/)


```
 18 Oct 13 | 15:11:43 ~
    $ conkyForecast
21°C
 
 18 Oct 13 | 15:11:48 ~
    $ conkyForecast -d CC
Clear
 
 18 Oct 13 | 15:12:07 ~
    $ conkyForecast -d CC --startday 0
Partly Cloudy
 
 18 Oct 13 | 15:12:23 ~
    $ conkyForecast -d CC --startday 0 -L es
Parcialmente Nublado
 
 18 Oct 13 | 15:16:11 ~
    $ 
```

[I]Hmmmmmmmmmmmmmmmmmm
Clear and Partly Cloudy - I have to check the code....[/I]

From: [conkyForecast.py help]("http://conky.pitstop.free.fr/wiki/index.php5?title=ConkyForecast_help_%28en%29")
```
Usage: conkyForecast [options]
Options:

-h, --help            show this help message and exit

-C FILE, --config=FILE
[default: ~/.conkyForecast.config] The path to the
configuration file, allowing multiple config files to
be used.

  -l CODE, --location=CODE
location code for weather data [default set in
config]. Use the following url to determine your
location code by city name:

http://xoap.weather.com/search/search?where=Norwich

Change NORWICH for your city name!

-d DATATYPE, --datatype=DATATYPE
[default: HT] The data type options are:

Today: LT &#8211; Feels Like Temp &#8211; WITHOUT: &#8220;&#8211;startday=0&#8243; [--datatype LT]
Today: HT &#8211; Current Temp &#8211; WITHOUT: &#8220;&#8211;startday=0&#8243; [--datatype HT]

Today: LT &#8211; Forcasted Low Temp: &#8211; WITH: &#8220;&#8211;startday=0&#8243; [-- startday=0 --datatype LT]
Today: HT &#8211; Forecasted High Temp: &#8211; WITH: &#8220;&#8211;startday=0&#8243; [-- startday=0 --datatype HT]

Forecast: LT &#8211; Low Temp &#8211; use with &#8211;startday=1 to 4 [-- startday=1 --datatype LT]
Forecast: HT &#8211; High Temp &#8211; use with &#8211;startday=1 to 4 [-- startday=1 --datatype HT]

Font commands:

BF (Bearing Font)
BS (Bearing font with Speed)
MF (Moon Font)
WF (Weather Font output)

Images commands (conky v1.7.1 or greater)
- Usage:
BI (Bearing Icon Path)
- ${image [--datatype=BI] -p xx,xx -s yyxyy}
- ${image [--datatype=BI --startday=1] -p xx,xx -s yyxyy}
MI (Moon Icon Path)
- ${image [--datatype=MI] -p xx,xx -s yyxyy}
WI (Weather Icon Path) -
- ${image [--datatype=WI] -p xx,xx -s yyxyy}
- ${image [--datatype=WI --startday=1] -p xx,xx -s yyxyy}

BD (Barometer Description)
BR (Barometer Reading)
CC (Current Conditions)
CN (City Name)
CO (Country)
CT (Conditions Text)
DL (DayLight)
DP (Dew Point)
DW (Day of Week)
HM (Humidity)
LF (Last Fetch from weather.com). Not applicable at command line when using templates.
LU (Last Update at weather.com)
MP (Moon Phase)
OB (Observatory)
PC (Precipitation Chance)
SR (SunRise)
SS (SunSet)
UI (UV Index)
UT (UV Text)
VI (Visibility)
WA (Wind Angle - in degrees)
WD (Wind Direction)
WG (Wind Gusts)
WM (weather map fetch and image path returned)
WS (Wind Speed)

  -s NUMBER, --startday=NUMBER
define the starting day number, if omitted current
conditions are output. Not applicable at command line
when using templates.

  -e NUMBER, --endday=NUMBER
define the ending day number, if omitted only starting
day data is output. Not applicable at command line
when using templates.

  -S NUMBER, --spaces=NUMBER
[default: 1] Define the number of spaces between
ranged output. Not applicable at command line when
using templates.

  -t FILE, --template=FILE
define a template file to generate output in one call.
A displayable item in the file is in the form
[--datatype=HT --startday=1].

The following are possible options within each item:

--location
--datatype
--startday
--endday
--night
--shortweekday
--imperial
--beaufort
--metrespersecond
--hideunits
--hidedegreesymbol
--spaces
--minuteshide

Note that the short forms of the options are not
supported! If any of these options is set from the
commandline, it sets the default value of the
option for all template items.

  -L LOCALE, --locale=LOCALE
override the system locale for language output
(bg=bulgarian, cs=czech, de=german, es=spanish,
en=english, es=spanish, fj=fijian, fr=french,
it=italian, nl=dutch, pl=polish, ro=romanian,
sk=slovak, more to come)

  -i, --imperial        request imperial units, if omitted output is in
metric.

  -b, --beaufort        request beaufort scale for wind speeds, if omitted
output is either metric/imperial.

  -M, --metrespersecond
request metres per second for wind speeds, if omitted
output is either metric/imperial.

  -n, --night           switch output to night data, if omitted day output
will be output. ~/.conkyForecast.config now has: AUTO_NIGHT = True/False  Default: False

  -w, --shortweekday    Shorten the day of week data type to 3 characters.

  -u, --hideunits       Hide units such as mph or C, degree symbols (°) are
still shown.

  -x, --hidedegreesymbol
Hide the degree symbol used with temperature output,
this is only valid if used in conjunction with
--hideunits.

  -m NUMBER, --minuteshide=NUMBER
Works only with LU and LF. If present, hides the date
part of the LU or LF timestamp if the day of the
timestamp is today. The time part is also hidden, if
the timestamp is older than minutes specified in this
argument. If set to 0, the time part is always shown.
If set to -1, the value EXPIRY_MINUTES from the config
file is used.

  -c WIDTH, --centeredwidth=WIDTH
If used the output will be centered in a string of the
set width, padded out with spaces, if the output width
is greater than the setting it will be truncated

  -r, --refetch         Fetch data regardless of data expiry.

  -v, --verbose         Request verbose output, not a good idea when running
through conky!

  -V, --version         Displays the version of the script.

  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
filepath.

  --infologfile=FILE    If a filepath is set, the script appends info to the
filepath.
```

---

### Post by Sector11 on 2013-10-18
Line 71 in my original **cf** script posted in [post #63]("http://ubuntuforums.org/showthread.php?t=2178780&page=7&p=12814738#post12814738") had an error and has been corrected in that post

Line 71
```
  echo `conkyForecast --location=ARBA0009 -L en - -d CT --startday 0`
```

should read:
```
  echo `conkyForecast --location=ARBA0009 -L en - -d CT`
```

***[COLOR="#B22222"]Heads up to Habitual, GG and of course Vaphell[/COLOR]***

---

### Post by Vaphell on 2013-10-18
magenta was there for a moment because i looked at the wrong number when switching to the color dictionary, i edited it later. Either way it should be much more readable now so it's easy to find screwups like bad colors or parameters that should not be there.

fake filler as in 'random chars put in place of true conkyforecast data', i don't use it nor have it configured so i had to plug something else in to get the idea about the layout.


what about HM, it got --startday 0 too.

I noticed the formatting was not entirely right in places near "@" (that part landed in the line below), will have to rework a bit. Edited.

---

### Post by Sector11 on 2013-10-18
**_@ Vaphell_**

*RE magenta* - Oh! OK .. :D

*RE: fake filler* - OH my, you did that with NO conkyForecast installed!  **Colour me impressed!**

*RE: HM* - Yup, I fixed that locally and was about to do that in #63 and leave a notice.  :D  I can be such a DUH! at times.

*RE: @* - Yea I caught that too - but *RE: fake filler* still applies.

Also all **-L en - -d** changed to **-L en -d**

---

### Post by GrouchyGaijin on 2013-10-19
How are you guys getting CF to work?
I reinstalled CF pulled out an old CF config file, that at one time did work.
Now I get an error that the location is not in the cache and that the license key is invalid.

---

### Post by Sector11 on 2013-10-19
> **GrouchyGaijin said:**
> How are you guys getting CF to work?
I reinstalled CF pulled out an old CF config file, that at one time did work.
Now I get an error that the location is not in the cache and that the license key is invalid.

As explained before.

 - cF was always free because it used the 5 day forecast
 - IF a person "paid for the 10 day KEY, ID" at that time cF could use the fill 10 days and those ID and KEY's are still working.

 - also IF a person had changed:
```
CACHE_FOLDERPATH = /tmp/
```
to something like
```
CACHE_FOLDERPATH = /media/5/Conky/cache/
```
you would not have lost your "cache" files when you turned your machine off and the 5 day cF would still be running.

That act alone allowed the "free" cF to continue working as you had a file for cF to update.

People that used /tmp/ lost the cache file and cF stopped working, although I was under the impression it came back.

---

### Post by Habitual on 2013-10-20
> **Sector11 said:**
> 
```
# Written by JJ ie: Habitual
# 11.01.2010 12:10:07
```
**^^^^^^^^^^^^^^^**Blame him

Damn typos/edits... ;)
Original:
```
#!/bin/bash
# 4 Day Weather forecast script for Boardman, OH
# Written by John Jones 
# 11.01.2010 12:10:07
```
make: *** No rule to make target `JJ'.  Stop.

I too never throw anything away.

I don't even code conkys anymore, too flat, linear, ie.... boring.

---

### Post by Sector11 on 2013-10-20
> **Habitual said:**
> Damn typos/edits... ;)
Original:
```
#!/bin/bash
# 4 Day Weather forecast script for Boardman, OH
# Written by John Jones 
# 11.01.2010 12:10:07
```
make: *** No rule to make target `JJ'.  Stop.

I too never throw anything away.

I don't even code conkys anymore, too flat, linear, ie.... boring.

hanging head in shame ... {digging big toe in ground}
**[COLOR="#B22222"] "Oops! I is sorry!"[/COLOR]**

Conky flat? Boring?

Clearly you have not seen the "interactive" masterpieces by mepeachy and [falldown]("http://www.youtube.com/watch?v=jnV4GDQzzxQ"), nor the latest mechanical clock by easysid [with gears that rotate]("http://crunchbang.org/forums/viewtopic.php?pid=339025#p339025") <<--- that's a sneak peak at the pre-release.

---

### Post by Habitual on 2013-10-20
Have not seen it until "now". Looks cool.
My last [hurrah]("http://i771.photobucket.com/albums/xx360/E522260/desktop_9_21_2010.png") with spanking conkys.

Thanks!

---

### Post by Vaphell on 2013-10-20
is that world map dynamic? If so, the day/night zones are wrong ;-)

---

### Post by Habitual on 2013-10-21
```
# Daylight map.
# Written by John Jones / Habitual)
# 09/10/2010 07:37:21 AM
# Conky 1.8.0
# Remote image(s) is/are updated twice an hour on http://static.die.net and there are only 4 available.
# http://static.die.net/earth/mercator/640.jpg is 640x355
# http://static.die.net/earth/mercator/800.jpg is 800x444
# http://static.die.net/earth/mercator/1024.jpg is 1024x568
# http://static.die.net/earth/mercator/1280.jpg 1280px × 710px (scaled to 1148px × 637px)
# http://static.die.net/earth/mercator/1600.jpg # 1600x887
# Use daylight.sh to retrieve the remote image of your choice/size.

# Completely (re)written by John Jones on 09/01/2010 
# from other people's code, but it's MY layout, so there.

# -== Window Layout & Options ==- #
# Screen size = 1440x900
own_window yes                    # Boolean. Create own window to draw?
own_window_colour brown            # set a specified background colour (defaults to black). ONLY if Transparent = no, then this has effect.
own_window_transparent yes        # set transparency? sets background opacity to 0%
own_window_type override        # if own_window is yes, you may specify type normal, desktop, dock, panel or override (default: normal)
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes                # Use double buffering (reduces flicker, may not work for everyone)
text_buffer_size 1024            # Size of the standard text buffer (default is 256 bytes). # This is NEEDED for the calendar.sh output.
use_xft yes                        # Use Xft (anti-aliased font and stuff)
alignment mm                    # Screen placement
gap_x 0                            # gap_x is the distance from the edge of your screen - relative to Alignment value
gap_y 0                            # gap_y is the distance from the top/bottom edge of your screen. 

# -== Colors, Sizes, & Margins ==- #
update_interval 1.0
minimum_size 800 444 
maximum_width 800
imlib_cache_size 0            # Maximum width of window in pixels
stippled_borders 3            # Border stippling (dashing) in pixels
border_width 0                # Window's border width in pixels.
default_color white            # Default color and border color
pad_percents 2                # Pad percentages to this many decimals (0 = no padding)
top_name_width 8            # Width for $top name value (defaults to 15 characters)
default_bar_size 100 6            # Specify a default width and height for bars
short_units yes                # Shortens units to a single character (kiB->k, GiB->G, etc.). Default is off

# -== Text ==- #
draw_outline yes            # Boolean. Draw outlines?    
draw_borders no                # Boolean. Draw borders around text?
font Monospace:size=8:weight=bold    # Font name in X
uppercase no                # Boolean value, if true, text is rendered in upper case
draw_shades yes                # Boolean. Draw shades? 
mail_spool $MAIL            # localmail spool count

#lua_load /home/jj/Documents/Conky/Moon/moon.lua 
#lua_draw_hook_pre main /tmp/earth/earth_image

TEXT
${voffset -100}${image /home/jj/Pictures/daylight.jpg}
```

I ran a cron to grab the image 4 times an hour all day, every day, so the day|night image appeared to "move" across the screen.

---

### Post by Vaphell on 2013-10-21
oh i missed the date in the img name, near the equinox these zones will be vertical stripes in Mercator projection indeed. I thought it's a current screenshot and the border should be more sinusoid-like, which is shown in current images slurped from the website. No objections then :-)

---

### Post by Sector11 on 2013-10-21
@ Habitual - Cool!!!

No RSVP required. ):P

---

### Post by GrouchyGaijin on 2013-10-21
That is very cool!

---

### Post by Habitual on 2013-10-21
more conky-daylight goodness

---

### Post by Habitual on 2013-10-21
> **Sector11 said:**
> 
**[COLOR=#B22222] "Oops! I is sorry!"[/COLOR]**

Don't even sweat it.
I just now realize I post files with "jj" plastered all over them ;)

Talk about brain dead.

Well there ain't no change in the weather
Ain't no changes in me
And i ain't hidin' from nobody
Nobody's hidin' from me
Oh, that's the way its supposed to be

---

