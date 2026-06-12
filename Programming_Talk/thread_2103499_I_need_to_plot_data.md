---
title: "I need to plot data"
date: 2013-01-10
forum: Programming Talk
---

### Post by conradin on 2013-01-10
Hi all,
I have a website that plots data sets that are (200-800 x) and (+/-1 y)
from data that looks like this:
[http://interchemnet.um.maine.edu/DataFiles//senju/130109_5.TXT](http://interchemnet.um.maine.edu/DataFiles//senju/130109_5.TXT)

the current system we have is junk, and impossible to maintain. Ive been looking into other options, but there are so many, and in the time it takes to get to know even one, its hard to know if its a waste of my time, or worth while. 

does anyone have a solid recommendation for plotting /charts software on a website?

---

### Post by epicoder on 2013-01-10
It would be a simple proposition to parse the data with python/perl/whatever you like. Actually plotting the data is another thing entirely... I have never done something like this, so take my recommendations with a grain of salt. For creating a graph, there are two methods I know of:
Gnuplot: [http://gnuplot.info](http://gnuplot.info)
This is a nifty little command-line utility that does exactly what it says on the tin. It takes input and graphs it. It is fairly versatile and allows labels, customization of x and y ranges, and it can output to a wide variety of raster and vector image formats.

ImageMagick: [http://imagemagick.org/](http://imagemagick.org/)
This is a more general purpose library (as opposed to program). It has basic shape drawing capabilities (polygons, circles, Bézier curves) as well as nice text rendering. However, it does not support just taking raw data and graphing it like gnuplot does, so you will have to handle most of the calculations yourself. I would not recommend using this unless you need to support some obscure image format that gnuplot doesn't or you want extremely fine-grained control over the look of the resulting image.

---

### Post by ofnuts on 2013-01-10
> **conradin said:**
> Hi all,
I have a website that plots data sets that are (200-800 x) and (+/-1 y)
from data that looks like this:
[http://interchemnet.um.maine.edu/DataFiles//senju/130109_5.TXT](http://interchemnet.um.maine.edu/DataFiles//senju/130109_5.TXT)

the current system we have is junk, and impossible to maintain. Ive been looking into other options, but there are so many, and in the time it takes to get to know even one, its hard to know if its a waste of my time, or worth while. 

does anyone have a solid recommendation for plotting /charts software on a website?
Plot to what? PNG? SVG?  In what language is your site? PHP?

---

