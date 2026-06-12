---
title: "Dirty Gnome Weather-applet hack."
date: 2007-07-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Omnios on 2007-07-07
Hi I have been using Ubuntu for a long time and have used gnome-applet with a entry for a town that is about 50 or so clicks away. Anyways got mad today and did a bunch of searching and hacking for a solution.

 This is not a cut and past hack!

[SIZE=3][COLOR=Red]Warning Back up your Locations.xml before tweeking it may get Borked[/COLOR][/SIZE]

 Hacking the Gnome-applet is very dirty as there is nothing straight forward about it. 
Forget using web local codes as the applet uses the aviation TAF and METAR standards.

 There is a lot of info in the two wiki links provided.

 [http://en.wikipedia.org/wiki/METAR](http://en.wikipedia.org/wiki/METAR)

[http://en.wikipedia.org/wiki/Terminal_Aerodrome_Forecast](http://en.wikipedia.org/wiki/Terminal_Aerodrome_Forecast)

 there is also a weather radar map standard but have not played with that yet.

 Now the hardest part of this is searching for the code for your local area which will be any local airport thought it is only easy to find big airports so you might have to do some digging for the code.

 Basiclly so far I have only copied an existing city and changed the town name / names and changed the <CODE> ....... </CODE> which gives working weather. I still have to figure out the 
       <coordinates>45-19N 075-40W</coordinates>

and the codes for the radar and am hoping for some help on this. I tried doing this hack a long time ago and found nothing on it till now as I figured out the aviation standard used. SO so far TAF is the main weather code for the location. METAR seems to be the coordinates but what I have seen online for my city looks different from the examples from the config file.

 Now this is the dirty part which consists of tweeking the the following config file.
/usr/share/gnome-applets/gweather
 Locations.xml is the file that is modified. You will have to open it as gedit-root etc to save it. 

I copied an existing entry in the province I live in starting at <location> and ending at </location>

```
      <location>
        
        <name>Ottawa</name>
        <name xml:lang="ar">&#1571;&#1608;&#1578;&#1575;&#1608;&#1575;</name>
        <name xml:lang="az">Ottawa</name>
        <name xml:lang="bg">&#1054;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="bn">&#2451;&#2463;&#2494;&#2451;&#2527;&#2494;</name>
        <name xml:lang="bn_IN">&#2451;&#2463;&#2494;&#2451;&#2527;&#2494;</name>
        <name xml:lang="bs">Otava (Ottawa)</name>
        <name xml:lang="ca">Ottawa</name>
        <name xml:lang="cs">Ottawa</name>
        <name xml:lang="cy">Ottawa</name>
        <name xml:lang="da">Ottawa</name>
        <name xml:lang="de">Ottawa</name>
        <name xml:lang="dz">&#3944;&#3964;&#3851;&#3914;&#3851;&#3933;&#3853;</name>
        <name xml:lang="el">&#927;&#964;&#964;&#940;&#946;&#945;</name>
        <name xml:lang="en_CA">Ottawa</name>
        <name xml:lang="en_GB">Ottawa</name>
        <name xml:lang="es">Ottawa</name>
        <name xml:lang="et">Ottawa</name>
        <name xml:lang="eu">Ottawa</name>
        <name xml:lang="fa">&#1575;&#1608;&#1578;&#1575;&#1608;&#1575;</name>
        <name xml:lang="fi">Ottawa</name>
        <name xml:lang="fr">Ottawa</name>
        <name xml:lang="gl">Ottawa</name>
        <name xml:lang="gu">&#2707;&#2719;&#2750;&#2741;&#2750;</name>
        <name xml:lang="he">Ottawa</name>
        <name xml:lang="hi">&#2323;&#2335;&#2366;&#2357;&#2366;</name>
        <name xml:lang="hr">Ottawa</name>
        <name xml:lang="hu">Ottawa</name>
        <name xml:lang="id">Ottawa</name>
        <name xml:lang="it">Ottawa</name>
        <name xml:lang="ja">&#12458;&#12479;&#12527;</name>
        <name xml:lang="ka">&#4317;&#4322;&#4304;&#4309;&#4304;</name>
        <name xml:lang="ko">&#50724;&#53440;&#50752;</name>
        <name xml:lang="ky">&#1054;&#1090;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="lt">Otava</name>
        <name xml:lang="lv">Ottawa</name>
        <name xml:lang="mg">Ottawa</name>
        <name xml:lang="mk">Ottawa</name>
        <name xml:lang="ml">&#3347;&#3359;&#3405;&#3359;&#3390;&#3381;&#3390;</name>
        <name xml:lang="mn">Ottawa</name>
        <name xml:lang="mr">&#2323;&#2335;&#2366;&#2357;&#2366;</name>
        <name xml:lang="nb">Ottawa</name>
        <name xml:lang="ne">&#2323;&#2335;&#2381;&#2335;&#2366;&#2357;&#2366;</name>
        <name xml:lang="nl">Ottawa</name>
        <name xml:lang="nn">Ottawa</name>
        <name xml:lang="or">&#2835;&#2847;&#2878;&#2835;&#2893;&#2860;&#2878;</name>
        <name xml:lang="pa">&#2569;&#2591;&#2622;&#2613;&#2622;</name>
        <name xml:lang="pl">Ottawa</name>
        <name xml:lang="pt">Ottawa</name>
        <name xml:lang="pt_BR">Ottawa</name>
        <name xml:lang="ro">Ottawa</name>
        <name xml:lang="ru">&#1054;&#1090;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="sl">Ottawa</name>
        <name xml:lang="sq">Ottawa</name>
        <name xml:lang="sr">&#1054;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="sr@Latn">Otava</name>
        <name xml:lang="sv">Ottawa</name>
        <name xml:lang="ta">&#2962;&#2975;&#3021;&#2975;&#3006;&#2997;&#3006;</name>
        <name xml:lang="te">&#3091;&#3103;&#3134;&#3125;&#3134;</name>
        <name xml:lang="th">&#3629;&#3629;&#3605;&#3605;&#3634;&#3623;&#3634;</name>
        <name xml:lang="tr">Ottawa</name>
        <name xml:lang="uk">&#1054;&#1090;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="vi">Ottawa</name>
        <name xml:lang="zh_CN">&#28197;&#22826;&#21326;</name>
        <name xml:lang="zh_HK">&#28197;&#22826;&#33775;</name>
        <name xml:lang="zh_TW">&#28197;&#22826;&#33775;</name>
        <code>CYOW</code>
       <radar>tyx</radar>
       <coordinates>45-19N 075-40W</coordinates>
      </location>
``` Now this is what I ended up inserting a copy and modding it.

```

 <location>
        
        <name>Oshawa</name>
        <name xml:lang="ar">Oshawa</name>
        <name xml:lang="az">Oshawa</name>
        <name xml:lang="bg">Oshawa</name>
        <name xml:lang="bn">&#2451;&#2463;&#2494;&#2451;&#2527;&#2494;</name>
        <name xml:lang="bn_IN">&#2451;&#2463;&#2494;&#2451;&#2527;&#2494;</name>
        <name xml:lang="bs">Oshawa</name>
        <name xml:lang="ca">Oshawa</name>
        <name xml:lang="cs">Ottawa</name>
        <name xml:lang="cy">Ottawa</name>
        <name xml:lang="da">Ottawa</name>
        <name xml:lang="de">Ottawa</name>
        <name xml:lang="dz">&#3944;&#3964;&#3851;&#3914;&#3851;&#3933;&#3853;</name>
        <name xml:lang="el">&#927;&#964;&#964;&#940;&#946;&#945;</name>
        <name xml:lang="en_CA">Oshawa</name>
        <name xml:lang="en_GB">Oshawa</name>
        <name xml:lang="es">Oshawa</name>
        <name xml:lang="et">Ottawa</name>
        <name xml:lang="eu">Oshawa</name>
        <name xml:lang="fa">&#1575;&#1608;&#1578;&#1575;&#1608;&#1575;</name>
        <name xml:lang="fi">Ottawa</name>
        <name xml:lang="fr">Oshawa</name>
        <name xml:lang="gl">Ottawa</name>
        <name xml:lang="gu">&#2707;&#2719;&#2750;&#2741;&#2750;</name>
        <name xml:lang="he">Ottawa</name>
        <name xml:lang="hi">&#2323;&#2335;&#2366;&#2357;&#2366;</name>
        <name xml:lang="hr">Ottawa</name>
        <name xml:lang="hu">Ottawa</name>
        <name xml:lang="id">Ottawa</name>
        <name xml:lang="it">Ottawa</name>
        <name xml:lang="ja">&#12458;&#12479;&#12527;</name>
        <name xml:lang="ka">&#4317;&#4322;&#4304;&#4309;&#4304;</name>
        <name xml:lang="ko">&#50724;&#53440;&#50752;</name>
        <name xml:lang="ky">&#1054;&#1090;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="lt">Otava</name>
        <name xml:lang="lv">Ottawa</name>
        <name xml:lang="mg">Ottawa</name>
        <name xml:lang="mk">Ottawa</name>
        <name xml:lang="ml">&#3347;&#3359;&#3405;&#3359;&#3390;&#3381;&#3390;</name>
        <name xml:lang="mn">Ottawa</name>
        <name xml:lang="mr">&#2323;&#2335;&#2366;&#2357;&#2366;</name>
        <name xml:lang="nb">Ottawa</name>
        <name xml:lang="ne">&#2323;&#2335;&#2381;&#2335;&#2366;&#2357;&#2366;</name>
        <name xml:lang="nl">Ottawa</name>
        <name xml:lang="nn">Ottawa</name>
        <name xml:lang="or">&#2835;&#2847;&#2878;&#2835;&#2893;&#2860;&#2878;</name>
        <name xml:lang="pa">&#2569;&#2591;&#2622;&#2613;&#2622;</name>
        <name xml:lang="pl">Ottawa</name>
        <name xml:lang="pt">Ottawa</name>
        <name xml:lang="pt_BR">Ottawa</name>
        <name xml:lang="ro">Ottawa</name>
        <name xml:lang="ru">&#1054;&#1090;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="sl">Ottawa</name>
        <name xml:lang="sq">Ottawa</name>         <name xml:lang="en_CA">Oshawa</name>
        <name xml:lang="en_GB">Oshawa</name>
        <name xml:lang="sr">&#1054;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="sr@Latn">Otava</name>
        <name xml:lang="sv">Ottawa</name>
        <name xml:lang="ta">&#2962;&#2975;&#3021;&#2975;&#3006;&#2997;&#3006;</name>
        <name xml:lang="te">&#3091;&#3103;&#3134;&#3125;&#3134;</name>
        <name xml:lang="th">&#3629;&#3629;&#3605;&#3605;&#3634;&#3623;&#3634;</name>
        <name xml:lang="tr">Ottawa</name>
        <name xml:lang="uk">&#1054;&#1090;&#1090;&#1072;&#1074;&#1072;</name>
        <name xml:lang="vi">Ottawa</name>
        <name xml:lang="zh_CN">&#28197;&#22826;&#21326;</name>
        <name xml:lang="zh_HK">&#28197;&#22826;&#33775;</name>
        <name xml:lang="zh_TW">&#28197;&#22826;&#33775;</name>
        <code>CYKZ</code>
       <radar>tyx</radar>
       <coordinates>45-19N 075-40W</coordinates>
      </location>
      <location>

``` K now there are a few tweeks here one of which is the city name
```
 <name>Oshawa</name>
```
Also to make it so you can choose your new town entry you must modify the name for the language you are using.

I need someone to give the US language abbreviation as I live in Canada.
```

        <name xml:lang="en_CA">Oshawa</name>
        <name xml:lang="en_GB">Oshawa</name>

```

 Now this is the part to get your local weather
```

 <code>CYKZ</code>

```
 This is the TAF code you need to look up on the net which may be difficult. You could also possibly phone your local airport for the info you need.

[SIZE=3][COLOR=Red]Warning Back up your Locations.xml before tweeking it may get Borked

 Happy Hacking!
[/COLOR][/SIZE]

---

### Post by Omnios on 2007-07-09
K my dad is a pilot with a light aircraft and I was talking to him yesterday and got Tar and METAR sorted. TAR is the location code for an airport. Every official airport has one which means you should be able to get weather specific to your area, even rural USA/Canada.

 METAR deals with coordinates and may cover a small are or even up to 500 miles. It also used for getting weather from one area to another. The problem I had with Metar is that the coordinates I got where may more than I saw in the config file.

 Also i  am still trying to figure out how to get the local radar weather code also.

 Yet another hack by omnios

---

### Post by colo505 on 2007-07-25
You can find the weather code by installing kweather, and finding your city in /usr/share/apps/kweatherservice/stations.dat

---

### Post by _Stevie_ on 2008-01-05
hmm this looks cool, but i guess i'm still dependent on what data [www.weather.com](www.weather.com) provides, right?
cos i wanted to add the data of a german city. but weather.com has only a
limited amount of german cities so i guess this wont work, right?

---

### Post by Omnios on 2008-01-05
> **_Stevie_ said:**
> hmm this looks cool, but i guess i'm still dependent on what data [www.weather.com]("http://www.weather.com") provides, right?
cos i wanted to add the data of a german city. but weather.com has only a
limited amount of german cities so i guess this wont work, right?

 This might help.

[http://en.allmetsat.com/metar-taf/germany.php](http://en.allmetsat.com/metar-taf/germany.php)

---

### Post by _Stevie_ on 2008-01-09
hi Omnios!

ahh, so the data is relying on allmetsat.com?

---

### Post by 6205 on 2008-02-20
Hmm...i wonder why cannot default GNOME weather applet use Weather.com for collecting forecast where are much more cities to choose from :confused:

---

### Post by Sealbhach on 2008-11-30
I'm outside the US so I can't get a radar map from weather.com

Also, in 8.10, there is no /usr/share/gnome-applets/gweather

There is no gweather file in there.

Anyone know how I can get a radar map for the UK? I tried entering URLs but it dodn't work, I want to see how the urls from weather.com look like...


.

---

### Post by kyphi on 2008-12-13
In 8.04 the path is: /usr/share/gnome/help/gweather

If it is different in 8.10, try "gweather" in "Search for files" under the "Places" menu.

For radar maps, you will have to search for a local weather station in your area that provides radar images and link to their co-ordinates.  

This thread was started one and a half years ago - if you need answers it would be best to start a new thread.

---

### Post by tamccullough on 2010-12-15
So what's the code for Oshawa? :)

---

