---
title: "Python+HTML+JavaScript: OpenStreetMap as a coordinate input device"
date: 2012-03-11
forum: Programming Talk
---

### Post by jw37 on 2012-03-11
Hi folks,

I'm making a **desktop** application with Python (and wxPython). The application is going to have a part that allows the user to choose a location from a map. OpenStreetMap seems good for this purpose.

I found the following example from [http://www.free-map.org.uk/course/osm/openlayers.xhtml](http://www.free-map.org.uk/course/osm/openlayers.xhtml)

```

<html>
<head>
<title>OpenLayers Example</title>
<script type='text/javascript' 
src='http://www.openlayers.org/api/OpenLayers.js'></script>
<script type='text/javascript'
src='http://www.openstreetmap.org/openlayers/OpenStreetMap.js'></script>
<script type='text/javascript' 
src='http://www.free-map.org.uk/javascript/ezol.js'></script>
<script type='text/javascript'>

function init()
{
    var map = makeMap("map1");

    var layerOSM = new OpenLayers.Layer.OSM();
    map.addLayer(layerOSM);

    map.setCenter(project(new OpenLayers.LonLat(-0.71,51.06)), 14);

    map.events.register("click",map,clickHandler);
}

function clickHandler(e)
{
    var pos1 = unproject(this.getLonLatFromViewPortPx(e.xy));
    alert("Longitude: " + pos1.lon + " Latitude: " + pos1.lat);
}
</script>
</head>
<body onload="init()">
<h1>OpenLayers Test</h1>
<div id="map1" style="width:800px; height:600px"> </div>
</body>
</html>
```It's really nice. You can just copy the code to a file e.g. "map.html" and view the file with your web browser.

Now the problem is how to link that with the Python program. What is needed:
1) Open a web browser window (of some sort) from wxPython program in a way that disables the caller window until you have selected a location.
2) Somehow send the coordinates to the caller, that is, to the Python program.

I have searched for a solution for many days without success. I don't bother you with the various attempts. Here are, however, the main lines of the sketches:

1) You can easily open the "map.html" file like this:
```
import webbrowser

webbrowser.open_new("map.html")
```but I can't see a way to send the result back to Python. Is it possible?

2) You could use some wxWidget that shows html+javascript. Where is one that works? How to use that widget?


I would be very thankful of any advice.

---

### Post by jw37 on 2012-03-17
I'm trying to send the data via the browser window title. It is easy to set the title.

```
function clickHandler(e)
{
    var pos1 = unproject(this.getLonLatFromViewPortPx(e.xy));
    //alert("Longitude: " + pos1.lon + " Latitude: " + pos1.lat);
    document.title = "Longitude: " + pos1.lon + " Latitude: " + pos1.lat;
}
```

The problem is how to see that window title change in Python. I tried to track it in /proc/<process-id> with [watchdog]("http://packages.python.org/watchdog/") but __[]("http://packages.python.org/watchdog/")no success. First, it seems the title just doesn't appear in any file in /proc/... (could it be true?). Second, you have to be root to be able to search those files.

Is it possible to see the window title change directly? I mean, not via the file system but somehow else.


Another attempt is to write the data to a local file from javascript. That has a security issue. I see it's good that a remote site cannot write to your file system. However, the script is located in the local machine itself, could it be allowed to access the file system?

---

### Post by GeneralZod on 2012-03-17
How keen are you on using wxWidgets? This would be very easy with Qt + QtWebkit - you can inject (native) QObjects into the QWebView, where they can be manipulated via Javascript.  Here's an old QtRuby example I had lying around:

```

#! /usr/bin/ruby

# Use a native Ruby QObject to decide what string to show
# in the HTML text box based on the string entered into the HTML input box.

require 'Qt4'
require 'qtwebkit'

app = Qt::Application.new(ARGV)

class JSObjectTest < Qt::Object
    def initialize()
        super(nil) 
    end
    def doSomethingWithString(string)
      # I'm not very imaginative, so just reverse the string for now.
      # You could, of course, use absolutely any aspect of ruby in order
      # to do more interesting stuff with the string instead :)
      return "Backwards is #{string.reverse}"
    end
    slots 'QString doSomethingWithString(QString)'
end

webView = Qt::WebView.new
webView.page.currentFrame.addToJavaScriptWindowObject("jsObjTest", JSObjectTest.new)

webView.setHtml(
<<-HTMLPAGEEND
<html>
  <head>
    <script type="text/javascript">
      function textChanged()
      {
        // Update the rubytext text with the text returned by the native ruby method.
        inputtextstring = document.getElementById("textinput").value;
        rubytext = document.getElementById("rubytext");
        rubytext.value = jsObjTest.doSomethingWithString(inputtextstring);
      }
      function pageLoaded()
      {
        document.getElementById("textinput").addEventListener("keyup", textChanged);
      }
    </script>
  </head>
  <body onload="pageLoaded()">
    Enter some text:
    <input type="text" id="textinput">

    Ruby sez:
    <input type="text" id="rubytext">
  </body>
</html>
HTMLPAGEEND
)
webView.show

app.exec

```

I'm guessing PyQt would be similar.

Anyway, perhaps wxWidgets has the same feature, but this is another option should the worst come to the worst :)

Edit:

Here we go - an even better example:

```

#! /usr/bin/ruby

# Inspired by: http://ubuntuforums.org/showthread.php?t=1939168

require 'Qt4'
require 'qtwebkit'

app = Qt::Application.new(ARGV)

class JSObjectTest < Qt::Object
    def initialize()
        super(nil) 
    end
    def doSomethingWithCoords(latitude, longtitude)
      # Just print to stdout for now, but the sky's the limit!
      print "Lat: #{latitude} Long: #{longtitude}\n"
    end
    slots 'QString doSomethingWithCoords(QString, QString)'
end

webView = Qt::WebView.new
webView.page.currentFrame.addToJavaScriptWindowObject("jsObjTest", JSObjectTest.new)

webView.setHtml(
<<-HTMLPAGEEND
<html>
<head>
<title>OpenLayers Example</title>
<script type='text/javascript' 
src='http://www.openlayers.org/api/OpenLayers.js'></script>
<script type='text/javascript'
src='http://www.openstreetmap.org/openlayers/OpenStreetMap.js'></script>
<script type='text/javascript' 
src='http://www.free-map.org.uk/javascript/ezol.js'></script>
<script type='text/javascript'>

function init()
{
    var map = makeMap("map1");

    var layerOSM = new OpenLayers.Layer.OSM();
    map.addLayer(layerOSM);

    map.setCenter(project(new OpenLayers.LonLat(-0.71,51.06)), 14);

    map.events.register("click",map,clickHandler);
}

function clickHandler(e)
{
    var pos1 = unproject(this.getLonLatFromViewPortPx(e.xy));
    //alert("Longitude: " + pos1.lon + " Latitude: " + pos1.lat);
    jsObjTest.doSomethingWithCoords(pos1.lat, pos1.lon);
}
</script>
</head>
<body onload="init()">
<h1>OpenLayers Test</h1>
<div id="map1" style="width:800px; height:600px"> </div>
</body>
</html>
HTMLPAGEEND
)
webView.show

app.exec

```

---

### Post by jw37 on 2012-03-18
Thank you very much for your answer, GeneralZod :)

That looks cool. It's the kind of solution I was originally looking for. I just didn't find the proper wxWidget that could be installed (quite easily) on lucid. Well, the reason might be that there is none for lucid. Maybe I need to upgrade to natty or precise. I believe this WebKit is what is needed:

from [http://wxpython.org/recentchanges.php ]("http://wxpython.org/recentchanges.php")> 
[LIST]
[*]26-Dec-2011
[/LIST]
Added wrappers for new WebView classes which came from a successful Google Summer of Code project this year. ** This new module allows you to embed the platform's native HTML/CSS/Javascript rendering engine in a wx application** like we've always been able to do with wx.webkit on Mac or with the various ActiveX modules that we've had for windows, except in the new version it uses the exact same API on all platforms and also provides an implementation for GTK.  Currently on Windows the IE Trident engine is used, and WebKit is used on OSX and GTK.  The code is organized to eventually allow alternate backend renderer implementations. ** The GTK version requires at least version 1.3.1 of libwebkitgtk-dev**, which is the default on most of the recent Linux distributions.  Please note that although these new classes and libraries are using names based on "WebView" I have put the wxPython verison of them in the wx.html2 module because the wxWebKit project already produces a wx.webview module for wxPython.The 1.3.1 version is available for ubuntu 11.04 (natty) and higher:

[https://launchpad.net/ubuntu/+source/webkit](https://launchpad.net/ubuntu/+source/webkit)

---

