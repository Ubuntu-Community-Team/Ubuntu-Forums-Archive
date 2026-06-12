---
title: "Help! Gnuplot problem"
date: 2011-07-08
forum: Programming Talk
---

### Post by kelvin490 on 2011-07-08
How can I save the plotted image plotted by gnuplot, in the format of GIF or JPEG? I plotted a picture then do something as follows:
 
gnuplot> set terminal jpeg
Terminal type set to 'jpeg'
Options are 'nocrop font /usr/share/fonts/truetype/ttf-liberation/LiberationSans-Regular.ttf 12 '
 
then I want to save it as finplot.jpeg, but it comes out:
 
gnuplot> set output finplot.jpeg
         undefined variable: finplot

What's the problem? Please help.

---

### Post by krazyd on 2011-07-08
You need quotes around the filename.

I usually save plots as PNG because it is lossless, usually smaller than jpg (for plot images) and more portable than gif.

Using pngcairo seems to give the best results:
```

set term pngcairo size 800,600 enhanced
set output "plot.png"
```

See the documentation for more help regarding the options above.

---

### Post by kelvin490 on 2011-07-08
> **krazyd said:**
> You need quotes around the filename.
 
I usually save plots as PNG because it is lossless, usually smaller than jpg (for plot images) and more portable than gif.
 
Using pngcairo seems to give the best results:
```

set term pngcairo size 800,600 enhanced
set output "plot.png"
```
 
See the documentation for more help regarding the options above.
 
 
Thanks, but when I tried this I got some errors:
 
gnuplot> set term pngcairo size 800,600 enhanced
                  ^
         unknown or ambiguous terminal type; type just 'set terminal' for a list
 
What is that?

---

