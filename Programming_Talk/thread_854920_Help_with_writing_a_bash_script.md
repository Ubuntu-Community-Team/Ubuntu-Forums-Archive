---
title: "Help with writing a bash script"
date: 2008-07-09
forum: Programming Talk
---

### Post by billiam5 on 2008-07-09
Hey all,

As a student, it is important for me and my roommates to know when the campus buses are going to be at our stop. Fortunately, our transit system's website has a page where you can enter a stop and find to the minute bus times, a-la-GPS on the buses.

I've written a shell script that goes and gets the webpage, parses it for the buses and times, and outputs a text file. This is the foundation of my plan: to have a linux box in the living room with a cron job that runs this script every 20-30 seconds and displays the buses and times on a flatscreen mounted by the door, so that we will always know when the buses will be coming.

Any ideas with explanation about how I could display the data on the screen in a big font, possibly with color coding based on how soon the bus is coming, would be greatly appreciated.

In summary:
-I already have the flatscreen, linux box
-The current script produces a text file with a format as follows
```
BUS NAME due
BUS NAME xx min
BUS NAME xx min
```
-I want to display that text to screen, possibly taking up the entire screen in big letters and color coded.

Thanks!

---

### Post by nanotube on 2008-07-10
well, why not just stick it into an html file, open it with firefox, and set it to refresh every 30 seconds?

come to think of it, skip the shell script, and just point firefox to that transit-system website, and have it refresh every 30 seconds (or a minute, or whatever seems acceptable).

---

### Post by billiam5 on 2008-07-10
That would definitely work, but I was thinking for this to be an exercise in learning more about shell scripting and Linux utilities. It's definitely been a learning experience so far. Also, I was thinking about expanding this project to include weather details, and possibly a space for us to write reminders to the screen, etc.

For now, I would like to find out how to expand my script to format and display the outputted bus information to the screen.

---

### Post by ghostdog74 on 2008-07-10
show your script

---

### Post by mssever on 2008-07-10
Well, if you're looking for a learning exercise, have your shellscript output an HTML file, e.g.: ```
<html>
  <head>
    <title>Bus Schedule</title>
    <link rel="stylesheet" type="text/css" href="path/to/css/file" />
  </head>
  <body>
    <dl>
      <dt>bus1 name</dt>
      <dd>bus1 details</dd>
      <dt>bus2 name</dt>
      <dd>bus2 details</dd>
    </dl>
  </body>
</html>
```Set Firefox to auto-reload the page and put it in fullscreen mode.

If you wanted to make life more interesting, put this on a web server, then use Javascript to auto represh.

---

### Post by henchman on 2008-07-10
Or because it may look ugly when the page refreshes use XMLHttpRequest to load content from the php script and put it into a div :) could be done with smooth fade in / fade out so that it looks neat when the content updates :popcorn:

nice project :>

you could read out the file with php :)

---

### Post by billiam5 on 2008-07-10
Thanks for all the suggestions!

Here's my script.. it's my first one so excuse my inexperiance!

```
#!/bin/sh

rm -f output

wget -q http://transitfx.cumtd.com/public/web/ViewStopMini.aspx?sp=GRNBUSEY&pt=50&r=60&st=Smo
sleep 6

grep lblRouteName ViewStopMini.aspx\?sp\=GRNBUSEY | cut -c102- | tr -d '</>spanb' > bus
grep lblDepartureTime ViewStopMini.aspx\?sp\=GRNBUSEY | cut -c100-105 | tr -d '</' > depart

paste depart bus > output

rm ViewStopMini.aspx\?sp\=GRNBUSEY
rm bus
rm depart

cat output
```

You guys definitely think html would be the way to go? How exactly would I implement that?

---

### Post by archivator on 2008-07-10
Well, there's also zenity but it won't give you rich-edit capabilities and is kind of a far stretch. Still, its list view is something you might want to look into. 

As for the html, I'd suggest writing it to a file and then doing a **xdg-open 'file.html'** . However, you won't get update functionality this way. If you want the info to update automatically, you have two options to consider.

One is to have the script sleep for, say, 2 minutes before looping again and then have the page set up to refresh every 121 sec. That way, Firefox would notice the change and would load the file again. However, this is very error prone as you don't really know how long the download-parsing cycle would take and thus might end up opening an empty file. 

The second thing I can think of is CGI but I'm not really sure if you can use bash as a CGI agent. Apparently, there is [this library](http://bashlib.sourceforge.net/) for exactly that purpose but the whole idea just gives me the creeps. If you choose this way, please, please, rewrite the script in a more sensible language (python, php might be a good choice here). Bash was never meant to be used under CGI. 

Oh, yeah, if you use the xdg-open method, you can always make it a cron job. You'll get your updates that away but something tells me you might end up with more than a few tabs. :D

---

### Post by ghostdog74 on 2008-07-10
```


wget -q -O- "http://transitfx.cumtd.com/public/web/ViewStopMini.aspx?sp=GRNBUSEY&pt=50&r=60&st=Smo" | awk '
/lblRouteName/{ 
 gsub(" *<[^>]+>","");gsub(/ +$/,"")
 printf $0
}

/lblDepartureTime/{
 gsub(" *<[^>]+>","");gsub(/ +$/,"")
 print $0
}'

```

---

### Post by durand on 2008-07-10
> **ghostdog74 said:**
> ```


wget -q -O- "http://transitfx.cumtd.com/public/web/ViewStopMini.aspx?sp=GRNBUSEY&pt=50&r=60&st=Smo" | awk '
/lblRouteName/{ 
 gsub(" *<[^>]+>","");gsub(/ +$/,"")
 printf $0
}

/lblDepartureTime/{
 gsub(" *<[^>]+>","");gsub(/ +$/,"")
 print $0
}'

```

Thats pretty cool :D

Hmm, maybe you could use an xscreensaver to display the text?
```

/usr/lib/xscreensaver/gltext -text "5 GREEN WEST 09 min" -no-spin -no-wander -front

```
or maybe use imagemagick to write the text to an image and then use eog to display it.

```
convert -size 1280x1024 xc:transparent -font Bookman-DemiItalic -pointsize 50 -fill yellow -draw "text 300,300 '`cat test`'" text.png; eog text.png -f
```

Then you can just:
```

sleep 30s
killall -9 eog
```
and use a while loop to loop it over and over again.
It's crude but there is a lot of room for refinement.

---

### Post by mssever on 2008-07-10
> **billiam5 said:**
> You guys definitely think html would be the way to go? How exactly would I implement that?
Well, HTML is far from the only option, but it isn't hard. E.g.:
```
output="$(paste "depart" "bus")"
echo "<html>blah more html<p class=\"data-here\">$output</p>more html</html>"
```Then just pipe the script to a file.

---

### Post by durand on 2008-07-11
Or you could just not follow HTML specs and just use an <h1> tag on its own. Most browers support this, right?

---

