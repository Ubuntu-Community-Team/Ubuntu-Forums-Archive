---
title: "/bin/bash: Dealing with semi-colons and commas"
date: 2010-06-18
forum: Programming Talk
---

### Post by GraysonPeddie on 2010-06-18
Hi, y'all. Consider that I have the following that copies the output of "weather" to "weather.txt."

```
weather > weather.txt
```

```
Temperature: 77.0 F (25.0 C)
Relative Humidity: 84%
Wind: Calm
Weather: light rain; Cumulonimbus clouds observed
Sky conditions: mostly cloudy
Precipitation last hour: 0.01 inches
Friday night... Low 77, 30% chance of precipitation.
Saturday... Thunderstorm, high 93, 50% chance of precipitation.
Saturday night... Low 76, 20% chance of precipitation.
Sunday... Thunderstorm, high 90.
Sunday night... Low 75.
```

Notice the semi-colon next to "light rain?" I can use sed to replace the semi-colon with the word "and" and output it like so...

```
cat weather.txt | grep "Weather: " | sed -e 's/; / and /g'
```

and it will produce the following:

```
Weather: light rain and Cumulonimbus clouds observed
```

It works.

Now, I am going to have the weather information broadcast through eSpeak, I am going to have to make it so that the eSpeak sounds more like an English speaker by giving clear and concise information via my speakers. What I mean is, I want to use conditions (if...else...fi) for determining if there's a comma or not. If there is one, I can convert the ", " into " and " and change semi-colons to commas.

Can anyone give me the example of how I can get it to work?

I'd like to give you my whole code to share with anyone. When I get it all fixed up, I can contribute this code to everyone (what you'll need for this script to work is espeak (or festival or just a normal "echo" that is included in Linux) and weather-utils). 

Here is my entire code. It does have errors, though, so if you can help, that'd be great.

```
#!/bin/bash
# Speak out to the user telling that you want to give the user
# a weather report.
OUTPUT=/usr/bin/espeak
$OUTPUT "Hello. This is e-Speak speech synthesizer located in my Ubuntu Server."
#sleep 1
$OUTPUT "I would like to give you the weather information that is close to Orlando International Airport. Please hold on for a second."
#sleep 3
$OUTPUT "The today's temperature is $(awk '/Temperature/ { print $2 }' weather.txt) degrees."
#sleep 1
$OUTPUT "The sky condition is $(cat weather.txt | grep "Sky conditions: " | sed 's/Sky conditions: //g') and the detailed weather condition is"
WC="$(cat weather.txt | grep 'Weather: ' | sed -e 's/Weather: //g' -e 's/ observed//g')"
MORETHANTWO="$(echo '$WC' | sed -e 's/; / more /g') | awk '{print $2)')"
if echo MORETHANTWO -eq "more"
then
    $OUTPUT "$(cat '$WC' | sed 's/; / and /g')."
else
    $OUTPUT "$(cat '$WC' | sed 's/, / and /g')."
fi
WIND="$(cat weather.txt | grep 'Wind ')"
if echo "$(awk '{print $2}' $WIND)" -eq "Calm"
then
    $OUTPUT "The wind is calm at this time."
else
    $OUTPUT "The current direction of the wind is from $(awk '/Wind/ { print $4,"at",$8,"miles per hour" }' weather.txt | sed -e 's/N/west/g' -e 's/NNE/north-northeast/g' -e 's/NE/northeast/g' -e 's/ENE/east-northeast/g' -e 's/E/east/g' -e 's/ESE/east-southeast/g' -e 's/SE/southeast/g' -e 's/SSE/south-southeast/g' -e 's/S/south/g' -e 's/SSW/south-southwest/g' -e 's/SW/southwest/g' -e 's/WSW/west-southwest/g' -e 's/W/west/g' -e 's/WNW/west-northwest/g' -e 's/NW/northwest/g' -e 's/NNW/north-northwest/g').
fi
sleep 1
#$OUTPUT "$(awk '/Precipitation last hour: / { print "For the precipitation, there has been",$4,"inches of
rain during the last hour."}' weather.txt)"
```

It will take me some time to get familiar with the bash scripting language and some tools like sed, grep, and awk, although I'm mostly used to grep just for basic use, like so...

```
cat weather.txt | grep "Wind: "
```

...for example, and I have not made use of the grep's command switches, although I did get some help when it comes to removing/replacing words with sed thanks to the Internet.

So anyway, if you can help point me in the right direction, that will be appreciated. Of course, you can help improve the code if you like. That way, other users can make use of this code and have it in a cron job when the user wakes up. "Good morning, Grayson! It's 7 o'clock in the morning and it's time for you to wake up and prepare yourself for class." Heh heh! It kind of reminds me of [HomeSeer](www.homeseer.com) for Windows that I used to play with a couple of years ago but I couldn't afford it. I used it with home automation with only Insteon Lamp modules. It's kind of fun! :) Whoops, sorry! I didn't mean to digress off my subject of this thread. :) Anyway, I am going to use this code in my Ubuntu Server.

Ah, the beauty of Linux and open source... *lays back in my chair* ;)

(Gee, no wonder I laughed at myself. :))

---

### Post by ju2wheels on 2010-06-19
Honestly, I think you just may be overcomplicating it a bit. I would just run sed on the file twice and convert all commas and semicolons into "and". If there arent any commas or semicolons then sed wont do anything.

```

#!/bin/bash

/usr/bin/weather > /tmp/curweather.txt;

/bin/sed -i '/;/ and /' /tmp/curweather.txt;
/bin/sed -i '/,/ and /' /tmp/curweather.txt;

TEMP=`/bin/grep "Temperature:" /tmp/curweather.txt | /usr/bin/cut -d" " -f2`;
SKY=`/bin/grep "Sky conditions:" /tmp/curweather.txt | /usr/bin/cut -d":" -f2`;
WC=`/bin/grep "Weather:" /tmp/curweather.txt | /usr/bin/cut -d":" -f2 | /bin/sed -e 's/observed//g'`;

#Then you can pass each of the above variables to espeak if they arent empty
if [ "${VAR}" != "" ]; then
  #espeak ${VAR};
fi


```

[edit] Note I dont have weather installed so I cant test the above...

---

### Post by GraysonPeddie on 2010-06-19
Actually, I found something in the Internet. I am familiar with C# and I didn't know which keywords to use during my search until now.

The keywords I used in Google Search is: bash shell string contains

This is the first link I came across.
[http://stackoverflow.com/questions/229551/string-contains-in-bash](http://stackoverflow.com/questions/229551/string-contains-in-bash)

I found this code that works:

```
string='My string';

if [[ $string == *My* ]]
then
  echo "It's there!";
fi
```

I really don't understand how this works, but when I test my code:

```
grayson@ubuserver:~$ if [[ $(cat weather.txt) == *Wind* ]]; then echo "Wind is
here."; else echo "Wind is not here."; fi
Wind is here.
```

It works.

So with that in mind, I can use the portion of the code you have, including the one that I got help from the Internet.

Thanks for your help, though.

---

