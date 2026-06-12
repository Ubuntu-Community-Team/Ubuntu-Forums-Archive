---
title: "Javascript - Web browser checker"
date: 2009-06-23
forum: Programming Talk
---

### Post by slimx3m on 2009-06-23
hi,
i would like some assistance with the following script at this link.[Dynamic Drive DHTML Scripts- Browser Sniffer Script](http://www.dynamicdrive.com/dynamicindex9/browsersniffer.htm).  i would like to have the script checking the web browser version on IE5 and IE6 and reject them or giving them a pop-up message saying that they need to upgrade their web browser.

i have tried everything on the documentation but it doesn't seem to work.

thanks in advance.

---

### Post by Ubu2010 on 2009-06-23
Did you put the script in the <HEAD> section of an HTML file, or save it as an external .js file ?

---

### Post by Reiger on 2009-06-23
The navigator object holds many fields/secrets but none of them can be trusted (i.e. someone using Opera or Konqueror might trick you into believing he/she uses IE 6)...

... You can code towards features. For instance, I know there's a quirk in Opera which makes some key evens behave oddly. I also know that in Opera there exists a special object called `opera' (which I can't access but that is not my intention). So I know when to invoke my special Opera key handling:
```

function isOpera() {
 return typeof(opera) != 'undefined' ? true : false;
}

```

Similar approaches should work for MSIE. (typeof(featureToTest) will should work as well.)

---

### Post by morkelkey on 2009-06-24
OpenLayers.Util.getBrowserName = function() { 
    var browserName = ""; 
     
    var ua = navigator.userAgent.toLowerCase(); 
    if ( ua.indexOf( "opera" ) != -1 ) { 
        browserName = "opera"; 
    } else if ( ua.indexOf( "msie" ) != -1 ) { 
        browserName = "msie"; 
    } else if ( ua.indexOf( "safari" ) != -1 ) { 
        browserName = "safari"; 
    } else if ( ua.indexOf( "mozilla" ) != -1 ) { 
        if ( ua.indexOf( "firefox" ) != -1 ) { 
            browserName = "firefox"; 
        } else { 
            browserName = "mozilla"; 
        } 
    } 
     
    return browserName; 
};


I think this code is enough for you to identify browser....

---

### Post by loell on 2009-06-24
try looking at 

[sevenup javascript]("http://code.google.com/p/sevenup/")

---

### Post by slimx3m on 2009-06-24
> **Ubu2010 said:**
> Did you put the script in the <HEAD> section of an HTML file, or save it as an external .js file ?
yes, i do have it specified on the **head** but still does not want to work.  pretty weird.

> **loell said:**
> try looking at 

[sevenup javascript]("http://code.google.com/p/sevenup/")
i tried this with IE6 and IE7 and it wouldn't give me any error message.  i check the error on the web browser and it says that there is an error "**'option'**" not found.  that is the weirdest thing i ever seen.  i am following all the documentations (which is relatively easy) and it wouldn't work :confused:.

any thoughts?

---

### Post by slimx3m on 2009-06-24
never mind.... thanx everybody for your help.  i was able to fix it with this script that i found that does exacly what i want to do.

```
<html>
<head>
<script type="text/javascript">
function detectBrowser()
{
var browser=navigator.appName;
var b_version=navigator.appVersion;
var version=parseFloat(b_version);
if ((browser=="Netscape"||browser=="Microsoft Internet Explorer") && (version>=4))
  {
  alert("Your browser is good enough!");
  }
else
  {
  alert("It's time to upgrade your browser!");
  }
}
</script>
</head>

<body onload="detectBrowser()">
</body>

</html>

```

from [http://w3schools.com/js/tryit.asp?filename=tryjs_browser2](http://w3schools.com/js/tryit.asp?filename=tryjs_browser2)

---

### Post by s.fox on 2009-06-24
Hi,

Small point.  I **think** a problem with this approach is that the browser identity can be 'spoofed' because, in many modern browsers, the navigator.appVersion (and navigator.appName) and navigator.userAgent string properties are user configurable strings. A user or browser distributor can put what they want in the navigator.userAgent string"

-Ash R

---

### Post by slimx3m on 2009-06-24
i didn't know that.  that would be a really good point if what you are saying is true.  but, i think that most of the users would really use the right name on the web browser name.

---

### Post by Reiger on 2009-06-24
> **Reiger said:**
> The navigator object holds many fields/secrets but none of them can be trusted (i.e. someone using Opera or Konqueror might trick you into believing he/she uses IE 6)...


Time to quote myself, then?

Braindead scripts like your `fixed' version are the reason why people did, do and will continue to spoof their browser identity if they are given the chance to. Have you actually looked at the code? Surely you must have realized the glaring bugs there? Just out of interest: want to bet what will happen when I use Opera 10 to browse to a site using _that piece of junk_ ? My money is on a silly alert that is completely mistaken and nonsensical to boot.

---

### Post by loell on 2009-06-24
> **slimx3m said:**
> 
i tried this with IE6 and IE7 and it wouldn't give me any error message.  i check the error on the web browser and it says that there is an error "**'option'**" not found.  that is the weirdest thing i ever seen.  i am following all the documentations (which is relatively easy) and it wouldn't work :confused:.

any thoughts?

not sure what's happening, but you can use [http://browsershots.org/]("http://browsershots.org/") to confirm if it's just your browser or it's really the script not funtioning as intended.

---

### Post by slimx3m on 2009-06-25
> **loell said:**
> not sure what's happening, but you can use [http://browsershots.org/]("http://browsershots.org/") to confirm if it's just your browser or it's really the script not funtioning as intended.
i confirmed myself using IE6 on a old computer that i have laying around.  thnx for the info though.

---

