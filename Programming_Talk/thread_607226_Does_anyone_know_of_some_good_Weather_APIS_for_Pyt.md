---
title: "Does anyone know of some good Weather APIS for Python"
date: 2007-11-08
forum: Programming Talk
---

### Post by Xavieran on 2007-11-08
I'm writing a little script to retrieve and display weather info for Australia to help me to learn about interacting with the Internet and also because my mum needs a weather application that gives the information for towns other than Sydney!
So tips on how to do this and also links to usable weather API's for the Southern Hemisphere are welcome.
Python is the language I'm using.

---

### Post by ThinkBuntu on 2007-11-08
See how the guys behind the ForecastFox plugin do it...shouldn't need to be in Python either.

---

### Post by Xavieran on 2007-11-08
Well see Python is the only language I know/am learning. 
I'll check it out though ;)

---

### Post by ThinkBuntu on 2007-11-08
Learn to use Python as a glue language maybe, like Perl. Anyway, the "source" link on their site went to nowhere, but maybe you need to poke around.

---

### Post by Xavieran on 2007-11-08
I found the site they get their weather info from.
It's AccuWeather.com.At the moment I'm checking out a gadgets code of theirs its called netweather.
I'll try and see where it grabs it's weather info from.

Edit:I found the code for the NetWeather Gadget.It is in Java( I'm pretty sure it is anyway) and I have tried following the links inside it.
If anyone could tell me what it does thanks!
```
//v1.0
function AC_AddExtension(src, ext)
{
  if (src.indexOf('?') != -1)
    return src.replace(/\?/, ext+'?'); 
  else
    return src + ext;
}

function AC_Generateobj(objAttrs, params, embedAttrs) 
{ 
  var str = '<object ';
  for (var i in objAttrs)
    str += i + '="' + objAttrs[i] + '" ';
  str += '>';
  for (var i in params)
    str += '<param name="' + i + '" value="' + params[i] + '" /> ';
  str += '<embed ';
  for (var i in embedAttrs)
    str += i + '="' + embedAttrs[i] + '" ';
  str += ' ></embed></object>';

  document.write(str);
}

function adcVideoPlayer(code,issub,subindex,adfirst)
{
	var newWin;
	newWin = window.open("http://www.accuweather.com/media-player.asp?vidcode="+code+"&issub="+issub+"&subindex="+subindex+"&adfirst="+adfirst,"adcMediaPlayer","scrollbars=no,statusbar=no,toolbar=no,resizeable=no,HEIGHT=550,WIDTH=700");
}


function RunNetWeather(){
  var ret = 
    AC_GetArgs
    (  arguments, ".swf", "movie", "clsid:d27cdb6e-ae6d-11cf-96b8-444553540000"
     , "http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version="
     , "http://www.macromedia.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash"
     , "application/x-shockwave-flash", "7,0,0,0"
    );
  AC_Generateobj(ret.objAttrs, ret.params, ret.embedAttrs);
}

function AC_SW_RunContent(){
  var ret = 
    AC_GetArgs
    (  arguments, ".dcr", "src", "clsid:166B1BCA-3F9C-11CF-8075-444553540000"
     , "http://fpdownload.macromedia.com/pub/shockwave/cabs/director/sw.cab#version="
     , "http://www.macromedia.com/shockwave/download/"
     , null, "8,5,0,0"
    );
  AC_Generateobj(ret.objAttrs, ret.params, ret.embedAttrs);
}

function AC_GetArgs(args, ext, srcParamName, classid, codebase, pluginsPage, mimeType, cbVers){
  var ret = new Object();
  ret.embedAttrs = new Object();
  ret.params = new Object();
  ret.objAttrs = new Object();
  for (var i=0; i < args.length; i=i+2){
    var currArg = args[i].toLowerCase();    

    switch (currArg){	
      case "codebase":
      case "pluginspage":
      case "type":
      case "classid":
        break;
      case "src":
      case "movie":	
        args[i+1] = AC_AddExtension(args[i+1], ext);
        ret.embedAttrs["src"] = args[i+1];
        ret.params[srcParamName] = args[i+1];
        break;
      case "minversion":
        cbVers = args[i+1];
        break;
      case "width":
      case "height":
      case "align":
      case "vspace": 
      case "hspace":
      case "class":
      case "title":
      case "accesskey":
      case "name":
      case "id":
      case "tabindex":
        ret.embedAttrs[args[i]] = ret.objAttrs[args[i]] = args[i+1];
        break;
      default:
        ret.embedAttrs[args[i]] = ret.params[args[i]] = args[i+1];
    }
  }
  ret.objAttrs["classid"] = classid;
  ret.objAttrs["codebase"] = codebase + cbVers;
  ret.embedAttrs["pluginspage"] = pluginsPage;
  if (mimeType) ret.embedAttrs["type"] = mimeType;
  return ret;
}

RunNetWeather ("id", "netWxV2", "minversion", "8,0,0,0", "movie","http://netwx.accuweather.com/netWx-V212?zipcode=OCN|AU|NSW|BROKEN HILL|&customtheme=&theme=1&metric=0&target=_self&lang=uke&url=&video=&category=&logo=1&tStyle=whteYell&partner=netweather","src", "http://netwx.accuweather.com/netWx-V212?zipcode=OCN|AU|NSW|BROKEN HILL|&customtheme=&theme=1&metric=0&target=_self&lang=uke&url=&video=&category=&logo=1&tStyle=whteYell&partner=netweather", "width", "240","height", "406", "name", "netWxV2", "wmode","transparent");
```

---

### Post by dwblas on 2007-11-08
Adesklets is written in Python and has a weather app.  You can install it via Synaptic.  It gets the weather from weather.com.  In the U.S. you just supply the zip code.  For other countries I think you just supply the city and country, or  whatever you would normally supply to weather.com

---

### Post by Xavieran on 2007-11-08
For some reason when I input Broken Hill,Aus as my city it just came up with 0 degrees and 0 for all the other stuff. I can tell you it isn't 0 degrees here!

---

### Post by dwblas on 2007-11-09
This is what I got
[http://www.weather.com/outlook/travel/businesstraveler/local/ASXX0255?from=search_city](http://www.weather.com/outlook/travel/businesstraveler/local/ASXX0255?from=search_city)

---

### Post by Xavieran on 2007-11-09
I did this instead.

```
#Really simple weather info getting script
#Author:Xavieran
#License:GPL v2.0
import sys
from urllib import urlopen
#Have added a while loop so that the user can update the weather info
while 1 is 1:
	weather_url=urlopen('http://www.bom.gov.au/cgi-bin/wrap_fwo.pl?IDN60060.txt')
#not sure if this \/ is needed
	raw_weather=weather_url.read()
#Use find function
	Start=raw_weather.find('BROKEN HILL')
	Stop=raw_weather.find('COBAR')
	weather=raw_weather[Start:Stop]
	weather_url.close()
#some nice pretty formatting and print it!
	print '''Last updated 2212 on Friday 09/11/2007
----------------------------------------------------------------
LOCATION       HOUR  WIND  TEMP  Press'    RAIN   
		EST  Dir/  deg.C Hpa
		     km/h       
----------------------------------------------------------------\n''',weather
	exit=raw_input("Hit ENTER to update info")
	if exit=='exit':sys.exit()
```

---

### Post by ThinkBuntu on 2007-11-09
> **Xavieran said:**
> 
```
weather=raw_weathe[Start:Stop]

```

I see a typo there, "weathe[". Was that in your original source?

---

### Post by Xavieran on 2007-11-09
No that was not in my original script.
I changed the variable names when posting because I just had random letters for names.

Thanks for weeding that out I'll edit it. :-)

---

### Post by btdown on 2007-11-09
Hi,

I'm trying to learn python and I was not able to get the script to work, even after fixing the weathe[ typo.

Could you post the working script when you get a chance? Examples like these help me learn...thanks!

---

### Post by RetiredInMaine on 2007-11-10
To xavieran, FYI java does not have functions. Java calls it's functions methods and they are all encapsulated within a class,  there is no keyword identifier.
Based on one of the  input parameters (classid) my guess would be c++. I'm not familiar with c# or one of the newer c++/java  wannabes so maybe it's one of them. 

Not that it really matters.:)

---

### Post by Xavieran on 2007-11-10
> **btdown said:**
> Hi,

I'm trying to learn python and I was not able to get the script to work, even after fixing the weathe[ typo.

Could you post the working script when you get a chance? Examples like these help me learn...thanks!

Glad to be of service :-). I too am learning python and have been at it for 3 months so far. Here is the code it works fine for me. There are some good tutorials[ here]("http://www.dickbaldwin.com/tocpyth.htm"). They are a very rigorous introduction to python data types. I am currently doing [these]("http://www.freenetpages.co.uk/hp/alan.gauld/").

```
#Really simple weather info getting script
#Author:Xavieran
#License:GPL v2.0
import sys
from urllib import urlopen
#Have added a while loop so that the user can update the weather info
while 1 is 1:
	weather_url=urlopen('http://www.bom.gov.au/cgi-bin/wrap_fwo.pl?IDN60060.txt')
#not sure if this \/ is needed
	raw_weather=weather_url.read()
#Use find function
	Start=raw_weather.find('BROKEN HILL')
	Stop=raw_weather.find('COBAR')
	weather=raw_weather[Start:Stop]
	weather_url.close()
#some nice pretty formatting and print it!
	print '''Last updated 2212 on Friday 09/11/2007
----------------------------------------------------------------
LOCATION       HOUR  WIND  TEMP  Press'    RAIN   
		EST  Dir/  deg.C Hpa
		     km/h       
----------------------------------------------------------------\n''',weather
	exit=raw_input("Hit ENTER to update info")
	if exit=='exit':sys.exit()
```

---

### Post by smartbei on 2007-11-10
> **Xavieran said:**
> 
Edit:I found the code for the NetWeather Gadget.It is in Java( I'm pretty sure it is anyway) and I have tried following the links inside it.

That is definitely JavaScript, not Java, c++, etc.

As for what it does... It appears to generate the full <object ...> ... </object> block for a flash object. The function call to function RunNetWeather is probably dynamically generated with the current information about the user request. The function itself adds a bunch of stuff that is static (for example the object's format, the location of the .swf on the server, etc.) and then it is sent to AC_Generateobj to actually print the stuff on the page with the correct attributes. The function AC_SW_RunContent does not seem to be in use in this excerpt.

---

### Post by Xavieran on 2007-11-10
Thanks I was needing to know if it was accessing any simple .txt file that it read it's weather info from.

---

