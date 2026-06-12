---
title: "Ip geolocating wallpaper [bash]"
date: 2010-01-26
forum: Programming Talk
---

### Post by twinky2021 on 2010-01-26
[SIZE="3"]So pretty much i'm making a script to map connected ip addresses to a world map i have set as my wallpaper. I've broken this down into 5 steps, 2 of which i've more or less completed....
[/SIZE]

[COLOR="Red"]**1. Attain a list of connected ip addresses.** [/COLOR]
How could I do this? I've found 3 possible solutions, iftop, netstat, or bmon.... but i have no idea how to "parse" the output and recive a list of connected ips.

[COLOR="green"]**2. Find the approx lat & long of each ip**[/COLOR]
geoiplookup -f /usr/local/share/GeoIP/GeoIPCity.dat $curr_ip | grep -E "[-]?[0-9]*[.]{0,1}[0-9]{4}" -o

[COLOR="red"]**3. Translate lat & long to pixel locations on a map (<- this is what i need help with most)**[/COLOR]
don't even know where to start.

[COLOR="green"]**4. Use imagemagik to draw a dot and text to a map**[/COLOR]
convert world_wallpaper.png -fill "red" -draw "circle 500,500 501,501" -draw 'text 505,495 "$curr_ip"' world_wallpaper_ip.png

[COLOR="Red"]**5. write a properly formatted script to do all mentioned above.**[/COLOR]
I've just been calling this the hard part.


Also if i've missed anything (i'm sure i have) please be sure to tell me as this is my first post here and i'm not 100% on posting ediquette/form yet.

Edit: hmmmm it might help if i included the map(s) i'm planning on using
map 1: [http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg](http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg)
map 2: [http://i50.tinypic.com/30usdox.png](http://i50.tinypic.com/30usdox.png)

---

### Post by Habbit on 2010-01-26
Regarding your point #3: you need to know the [projection]("http://en.wikipedia.org/wiki/Map_projection") used in your map, and then you will most likely be able to find a mathematical model for that projection that you can use to transform the spherical coordinates into a point on the map.

For example, assuming a Mercator projection, [The Guide]("http://en.wikipedia.org/wiki/Mercator_projection#Mathematics_of_the_projection") gives (x,y) as a function of (long,lat). Note that the article assumes that the origin for your cartesian coordinate system is at the centre of the map: in image manipulation programs the origin is usually at the top left, so you'd have to translate the coordinates accordingly.

---

### Post by ve4cib on 2010-01-27
You might want to look into an actual geoprocessing service/application to place the map points.  ArcGIS (which is proprietary, and terribly expensive, but does offer a free Javascript API for web applications) would be able to place labelled points on a map very easily.  Something like OSGeo and OpenLayers (open-source projects similar to ArcGIS) would be able to do it too.  Heck, the Google Maps or Bing Maps Javascript APIs could do it too.

The easiest way might be to create a simple web application (or application that uses an embedded browser and JS engine), place the points and labels on the map, and then export the annotated map as an image.  You'd need to check the specific APIs in question, but it should be a fairly simple matter, really.  And it saves you from doing all of the work reprojecting map points to screen points.

EDIT:

An even easier way might be to use Google's Static Maps API and use wget to just download the image.  Basically all you'd need to do is something like this:

```
wget http://maps.google.com/maps/api/staticmap?center=0,0&zoom=0&size=1280x800&maptype=hybrid\
&markers=color:blue|label:192.168.1.1|40.702147,-74.015794&markers=color:green|label:127.0.0.1|40.711614,-74.012318\
&sensor=false&key=MAPS_API_KEY
```

You'd need to automatically generate the URL with the correct number of markers with their IP addresses, latitudes, and longitudes.  But it might be easier than cobbling the whole thing together manually.

API docs for the Static Map service are here: [http://code.google.com/apis/maps/documentation/staticmaps/](http://code.google.com/apis/maps/documentation/staticmaps/)

---

