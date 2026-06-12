---
title: "Help -- Python, trying to overwrite print"
date: 2015-12-04
forum: Programming Talk
---

### Post by drparsec on 2015-12-04
Hello, I am a newbie so please excuse any transgressions in advance of forum rules. 

I have adapted a Python ver. 2.7.9 program that just displays status data instead of its original purpose of alerting you if the International Space Station is overhead.  The challenge is to just have it *overwrite* the print of the eight lines of status data instead of writing all the lines and repeating. I want to display the output on a small screen display and don't need this continual roll of print output. I have tried using the " \r " command for carriage return before and inside the double quotes after the print command and at the end of line inside and outside the double quotes with no success.  The " \n " used for new line in the program works for a line space. Is there a special library I need to import?  I have read about Python curses but it is all quite confusing. Thanks for any advice. (I used indent formatting for posting illustration, indents should be 4 space increments, in case you want to run the program.)

#ISS tracking status
[COLOR=#000080]**import **[/COLOR]urllib, json, threading, sys

url= [COLOR=#008000]**"https://api.wheretheiss.at/v1/satellites/25544"**[/COLOR];
latitude = [COLOR=#0000ff]0[/COLOR];
longitude = [COLOR=#0000ff]0[/COLOR];
altitude = [COLOR=#0000ff]0[/COLOR];
visibility = [COLOR=#008000]**""**[/COLOR];

[COLOR=#000080]**def **[/COLOR]work():[INDENT][COLOR=#000080]**     global **[/COLOR]latitude;
   [COLOR=#000080]**     global **[/COLOR]longitude;
   [COLOR=#000080]**     global **[/COLOR]altitude;
   [COLOR=#000080]**     global **[/COLOR]visibility;
        response = urllib.urlopen(url);
        data = json.loads(response.read());  
        latitude = data[[COLOR=#008000]**'latitude'**[/COLOR]];
        altitude = data[[COLOR=#008000]**'altitude'**[/COLOR]];
        longitude = data  [[COLOR=#008000]**'longitude'**[/COLOR]];
        visibility = data [[COLOR=#008000]**'visibility'**[/COLOR]];[/INDENT]
[INDENT][COLOR=#000080]**     print**[/COLOR][COLOR=#008000][B]""
[/B][/COLOR][COLOR=#000080]**     print**[/COLOR][COLOR=#008000][B]""
[/B][/COLOR]     printCoordinates();
        threading.Timer([COLOR=#0000ff]10[/COLOR], work).start();[/INDENT]

[COLOR=#000080]**def **[/COLOR]printCoordinates():[INDENT=2][COLOR=#000080]**          print **[/COLOR][COLOR=#008000]**"International Space Station's Current Status Is: "**[/COLOR];
       [COLOR=#000080]**          print**[/COLOR][COLOR=#008000][B]""
[/B][/COLOR][COLOR=#000080]**          print **[/COLOR][COLOR=#008000]**"Latitude ="**[/COLOR],latitude,[COLOR=#008000][B]""
[/B][/COLOR][COLOR=#000080]**          print **[/COLOR][COLOR=#008000]**"Longitude ="**[/COLOR],longitude,[COLOR=#008000][B]""
[/B][/COLOR][COLOR=#000080]**          print **[/COLOR][COLOR=#008000]**"**[/COLOR][COLOR=#000080]**\n**[/COLOR][COLOR=#008000]**Altitude ="**[/COLOR],altitude,[COLOR=#008000][B]""
[/B][/COLOR][COLOR=#000080]**          print **[/COLOR][COLOR=#008000]**"**[/COLOR][COLOR=#000080]**\n**[/COLOR][COLOR=#008000]**Visibility ="**[/COLOR],visibility,[COLOR=#008000][B]""
[/B][/COLOR][/INDENT]
work ();

---

### Post by kostkon on 2015-12-04
You could use the curses module ([here for 2.x]("https://docs.python.org/2.7/library/curses.html")).

---

