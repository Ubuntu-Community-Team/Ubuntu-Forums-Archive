---
title: "[bash] Parsing an RSS feed in bash"
date: 2009-05-19
forum: Programming Talk
---

### Post by Volt9000 on 2009-05-19
So I decided to dive into shell programming, as it seems incredibly powerful (much more powerful than other command-line environments, *cough*Windows shell*cough*.)

As a simple project I decided to just parse an RSS feed from a weather site and display it; I actually got the idea from another thread.

Here's the RSS feed I'm trying to parse:
[http://rss.weather.com/weather/rss/local/CAXX0504](http://rss.weather.com/weather/rss/local/CAXX0504)

As you can see there are several items, but the only one that interests me now is the first one, which is the current weather. Now I *could* just find the specific line each time, but I want to make the script more robust, and of course, learn something. ;) I'd like to be able to parse all the <item>s and find the appropriate one. Unfortunately I really don't know how to do this.

Due to my limited knowledge of the tools available to me (and the complexity of things like sed and awk, argh!!) my algorithm was very simplistic:

1) Use wget to grab the file
2) Use grep to find the line number that has 'Current Weather'
3) Grab the entire <item>
4) Parse the <item> and look for the <description> tag

Steps 1 and 2 I figured out myself no problem, but 3 is where I'm getting stuck. I had an idea, but realize it would be very complex and I'm sure there's a much simpler of way of doing it:

- Get the line number of 'Current Weather'
- grep the file to find the last occurrence of <item> up until the aforementioned line number
- grep the file to find the first occurrence of </item> starting at the aforementioned line number
- Grab this whole section, from <item> to </item> and grep it again for the <description> tag

This seems a bit overkill. I'm sure there's a much simpler way of doing it. Could someone help me out?

---

### Post by ghostdog74 on 2009-05-19
this is not a full solution. just a basic idea
```

wget -q -O- http://rss.weather.com/weather/rss/local/CAXX0504| awk 'BEGIN{RS="<title>"}
/Current Weather/{
 gsub(/.*<description>|<\/description>.*/,"")
 print
}'

```
output
```

 # ./test.sh
<![CDATA[<img src="http://image.weather.com/web/common/wxicons/31/27.gif?12122006" alt="" />Mostly Cloudy, and 64 &deg; F. For more details?]]>


```

---

### Post by Volt9000 on 2009-05-19
Holy crap, that's great, thanks! :D

Now perhaps could you explain to me what all that awk gobbledygook means? I only understand the "wget" part.

---

### Post by ghostdog74 on 2009-05-19
> **Volt9000 said:**
> Holy crap, that's great, thanks! :D

Now perhaps could you explain to me what all that awk gobbledygook means? I only understand the "wget" part.

i can't explain better than what the manual can see my sig for effective awk.

try this to get a feel..
```

wget -q -O- http://rss.weather.com/weather/rss/local/CAXX0504| awk 'BEGIN{RS="<title>"}
{
 print "record : " $0

}'

```

look at the output closely

---

### Post by Volt9000 on 2009-05-19
Ok, I think I understand a little bit... but what's the

```

BEGIN{RS="<title>"}

```

for? Why are you matching <title>?

---

### Post by ghostdog74 on 2009-05-19
> **Volt9000 said:**
> Ok, I think I understand a little bit... but what's the

```

BEGIN{RS="<title>"}

```

for? Why are you matching <title>?

what do you understand? 
because the "Current Weather" and its items you want occurs from  title to the next title. So i use <title> to be record separator. as you can see from the output (a sample)
```

record : <![CDATA[Current Weather Conditions In Toronto, Canada]]></title>
      <link><![CDATA[http://www.weather.com/weather/local/CAXX0504?cm_pla=city_page&cm_ite=cc&site=city_page&cm_ven=LWO&cm_cat=&par=LWO_]]></link>
      <description><![CDATA[<img src="http://image.weather.com/web/common/wxicons/31/29.gif?12122006" alt="" />Partly Cloudy, and 61 &deg; F. For more details?]]></description>
    </item>
    <item>
      <guid isPermaLink="false">0.8908561051410682</guid>
      <pubDate>Wed, 20 May 2009 03:24:56 GMT</pubDate>

record : <![CDATA[Your Local Doppler Radar]]></title>
      <link><![CDATA[http://www.weather.com/weather/map/CAXX0504?cm_ven=LWO&cm_pla=map&site=map&cm_ite=doplr_sat&cm_cat=&par=LWO_]]></link>
      <description><![CDATA[This map shows the location and intensity of precipitation in your area. The color of the precipitation corresponds to the rate at which it is falling.  This map is updated every 15 minutes.]]></description>
    </item>
    <item>
      <guid isPermaLink="false">0.00527958005442164</guid>
      <pubDate>Wed, 20 May 2009 03:24:56 GMT</pubDate>



```
each record is from <title> to the next <title>. this allow you to find /Current Weather/ by searching for it in $0 (which represents the whole record)
the <description> you want is found in $0, so i just do a substitution using gsub, from the start of $0 till where <description> is...and then from </description> till the end of $0. this will leave the block of text between <description> and </description>.
Like i said, please look at the manual for more intro to awk

---

### Post by Volt9000 on 2009-05-20
Thanks, that's a bit clearer now... although I'll still have to dive much more deeply into awk so I can fully grasp this.

Thanks again!

---

### Post by phrostbyte on 2009-05-20
awk looks complicated but it really isn't. Just learn the syntax and commands. It's a advanced text parser.

---

