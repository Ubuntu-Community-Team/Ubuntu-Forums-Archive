---
title: "gpx visualization viewer"
date: 2013-04-23
forum: Programming Talk
---

### Post by pfeiffep on 2013-04-23
I couldn't discover an appropriate forum so I picked this one! 

I'm embarking on a project to map a local area with the goal of sharing maps with marked waypoints. I've been successful in exporting the data from my iPhone app to email. The current stubmling block is a method to view graphically the exported .gpx file (I believe it's in xml format) below is a sample of the exported file.
```
<?xml version="1.0" encoding="UTF-8"?>
<gpx version="1.1" creator="Maps+" xmlns="http://www.topografix.com/GPX/1/1">
<metadata><link href="http://izeize.com/mapsplus">Maps+</link><time>2013-04-23T16:54:11Z</time></metadata>
<trk><name>Track</name><extensions><total_distance>2001.368253120224</total_distance><total_duration>1167.917102992535</total_duration></extensions><trkseg><trkpt lat="38.83968916794935" lon="-77.47663782794834"><ele>91</ele><time>2013-04-23T16:14:48Z</time><extensions><horizontal_accuracy>10</horizontal_accuracy><vertical_accuracy>8<

```

TIA for any advice

---

### Post by pfeiffep on 2013-04-23
Thus far I've found 2 possible solutions: 1) GPS Visualizer - and on line app; 2) Viking installed from software centre - somewhat complicated but feature rich.

Others??

---

### Post by Herman on 2013-04-26
**3)** You can open GPX files with** Google Earth**. 
From the 'File' Menu, choose 'Open', or type 'ctrl+o'.
In the 'Open' frame, look for the 'Files of Type' spinbox near the bottom and set it to 'Gps' file types, (there's a range of them listed).
Browse for your file and open it.
Google Earth will give you instant gratification if you want to view your data.

**4)** **Quantum GIS** contains tools to easily open almost any file type.
From the 'Layer' menu, go 'Add Vector Layer', or use 'shift+ctlr+v' on your keyboard.
Click 'Browse' from the 'Add Vector Layer' frame and in the 'Open an OGR Supported Layer' frame, set the spinbox above the 'Open' button down in the lower RH corner to 'GPS eXchange Format [GPX] [OGR]. 
Browse for your file and open it.
Besides just viewing your GPS data, Quantum GIS offers a full range of possibilities for doing further work with your data.

---

### Post by pfeiffep on 2013-04-27
@Herman, Thanks for your reply. I'll certainly add those 2 suggestions to my list to try. 

Thus far I was somewhat successful with GPS Visualizer and Viking but neither performed the way I expected.

---

