---
title: "POVray won't draw!! Urgent!!"
date: 2007-03-05
forum: Programming Talk
---

### Post by raul_ on 2007-03-05
When i try to render the image, it will appear for one second and then it's gone. here is the output. i noticed that "continued trace" is turned off. I don't know if it has something to do with it

```
Copyright 1991-2002 POV-Ray Team(tm)
Parsing Options
  Input file: teste.pov (compatible to version 3.5)
  Remove bounds........On  Split unions........Off
  Library paths: /usr/share/povray-3.5 /usr/share/povray-3.5/include
Output Options
  Image resolution 320 by 240 (rows 1 to 240, columns 1 to 320).
  Output file: teste.png, 24 bpp PNG
  Graphic display......On  (type: 0, palette: 3, gamma:  2.2)
  Mosaic preview......Off
  CPU usage histogram.Off
  Continued trace......On  Allow interruption..Off  Pause when done.....Off
  Verbose messages.....On
Tracing Options
  Quality:  9
  Bounding boxes.......On  Bounding threshold: 3 
  Light Buffer.........On  Vista Buffer.........On  Draw Vista Buffer...Off
  Antialiasing........Off
Animation Options
  Clock value....   0.000  (Animation off)
Redirecting Options
  All Streams to console.........Off
  Debug Stream to console.........On
  Fatal Stream to console.........On
  Render Stream to console........On
  Statistics Stream to console....On
  Warning Stream to console.......On


Parsing.....

Creating bounding slabs.
Scene contains 2 frame level objects; 1 infinite.

Resuming interrupted trace from /home/raul/Desktop/teste.png
Displaying...
Using 24 bit TrueColor visual..........
Rendering...
Done Tracing
Statistics for teste.pov (Partial Image Rendered), Resolution 320 x 240
----------------------------------------------------------------------------
Pixels:               0   Samples:               0   Smpls/Pxl: -
Rays:                 0   Saved:                 0   Max Level: 0/5
----------------------------------------------------------------------------
Ray->Shape Intersection          Tests       Succeeded  Percentage
----------------------------------------------------------------------------
----------------------------------------------------------------------------
Calls to Noise:                  0   Calls to DNoise:             10
----------------------------------------------------------------------------
----------------------------------------------------------------------------
Smallest Alloc:                 10 bytes   Largest:             9608
Peak memory used:            71863 bytes
----------------------------------------------------------------------------

```

Help please. I really have to get this working

---

### Post by raul_ on 2007-03-05
Running POV-Ray for windows 3.6 in wine.

They can't make me use windows!! :twisted:

---

