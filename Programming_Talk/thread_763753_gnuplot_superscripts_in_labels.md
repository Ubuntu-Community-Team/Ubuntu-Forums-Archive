---
title: "gnuplot superscripts in labels"
date: 2008-04-23
forum: Programming Talk
---

### Post by Claus7 on 2008-04-23
Hello,

I 'm trying in 7.10 to use superscripts in axis labels while using gnuplot. My effort up to now was the following :
[LIST]
[*]set terminal png enhanced
[*]set terminal postscript enhanced
[*]set terminal postscript eps enhanced
[/LIST]
in combination to:
set xlabel "x^1"
plot ...

If I type this I get no results at all. Either my terminal will show "weird characters" or it will show data without creating the plot. Has anyone faced the same problem?

Regards!

---

### Post by Zugzwang on 2008-04-23
> **Claus7 said:**
> If I type this I get no results at all. Either my terminal will show "weird characters" or it will show data without creating the plot. Has anyone faced the same problem?


I assume that you know that when setting the terminal type to postscript, you will only get a postscript output of the plot but nothing will be drawn on the screen or whatsoever. The same holds for PNG. You need to redirect your output to a file: ```
set output '/tmp/test.png'
``` You can then view the file using your favourite programs for doing so.

As fas as your superscripts are concerned: Look at the details of the respective terminal type if they are supported. You might try one of the TeX output drivers which allow you to use TeX code as labels.

---

### Post by Claus7 on 2008-04-25
Hello,

1) Every time I type the plot command inside gnuplot I get a preview of my plot in a new window.

2) I have installed many tex packages from synaptic, yet to no avail as far as _png_ files from gnuplot are concerned. Maybe you propose to install something else?

3)If I type inside gnuplot :
```
set term postscript enhanced color
set output "colorindex.ps"
set xlabel "x^{15}"
plot "myplot" u 1:2
```
and then exit and type:
```
convert colorindex.ps ./colorindex.png
```
I get the output in png and the label as it should be, yet with the exception that the resolution is not as good as cretaing a png file from gnuplot. I have tried to set both the size for postscirpt files inside gnuplot or via the convert command, yet to no avail.

4)If I do :
```
gnuplot> set term png enhanced
Terminal type set to 'png'
Options are 'nocrop enhanced medium size 640,480 '
gnuplot> set output "colorindex.png"
gnuplot> set xlabel "x^{15}"
gnuplot>  plot "myplot" u 1:2
gdImageStringFT: Could not find/open font
gdImageStringFT: Could not find/open font
gdImageStringFT: Could not find/open font
gdImageStringFT: Could not find/open font
gnuplot>

```

Searching further about the error it seems that gnuplot cannot find a font that is needed. In order for gnuplot to find the font the environmental variable GDFONTPATH should be able to look where the fonts are installed.

Links for further notice:
[LIST]
[*][http://t16web.lanl.gov/Kawano/gnuplot/label-e.html](http://t16web.lanl.gov/Kawano/gnuplot/label-e.html)
[*][http://www.groupsrv.com/computers/about265948.html](http://www.groupsrv.com/computers/about265948.html)
[*][http://www.nabble.com/Re:-Can-gnuplot-do-this--p14343954.html](http://www.nabble.com/Re:-Can-gnuplot-do-this--p14343954.html)
[*][COLOR="Purple"]http://objectmix.com/graphics/139280-png-enhanced-font.html[/COLOR]
[*][COLOR="#800080"]http://search.cpan.org/~ilyaz/Term-Gnuplot-0.90380905/GnuplotTerminals.pod[/COLOR]
[*][COLOR="#ff8c00"]http://www.nabble.com/Re:-A-problem-with-fonts-and-or-printing-PNG-files--p15798292.html[/COLOR]
[/LIST]
Regards!

---

### Post by Claus7 on 2009-04-29
Hello,

this is a how to based on here (in hellenic language):
[http://www.linuxformat.gr/?q=forum/%CF%80%CF%81%CF%8C%CE%B2%CE%BB%CE%B7%CE%BC%CE%B1-%CE%BC%CE%B5-%CE%B5%CE%BB%CE%BB%CE%B7%CE%BD%CE%B9%CE%BA%CE%AC-%CF%83%CF%84%CE%BF-gnuplot-%CE%BB%CF%8D%CE%B8%CE%B7%CE%BA%CE%B5](http://www.linuxformat.gr/?q=forum/%CF%80%CF%81%CF%8C%CE%B2%CE%BB%CE%B7%CE%BC%CE%B1-%CE%BC%CE%B5-%CE%B5%CE%BB%CE%BB%CE%B7%CE%BD%CE%B9%CE%BA%CE%AC-%CF%83%CF%84%CE%BF-gnuplot-%CE%BB%CF%8D%CE%B8%CE%B7%CE%BA%CE%B5)

which allows to choose the fonts we want to use in gnuplot labels and also to extract a plot with multiple sub-plots in a display file.

(the process took place in gutsy gibbon, I think that it will work in most linux boxes)
So the commands are the following:
(after you have typed gnuplot)

```
p "file1" u 1:2 w l linewidth 4 lt 2
replot "file2" u 1:2 w l linewidth 4 lt 1
f(x)=0
replot f(x) w l linewidth 4 lt 3
```

remarks:
i)the linewidth shows "how big" the line will be
ii)the lt #, where # is a number, gives the color of the line, [http://nucl.sci.hokudai.ac.jp/~ohnishi/Lib/gnuplot.html](http://nucl.sci.hokudai.ac.jp/~ohnishi/Lib/gnuplot.html)
iii)with replot we plot a second plot to the same plot (hope this was clear)
iv)with f(x)=#, where # is a number, we plot a line parallel to the x axis

Now, in order to save the above "project" to a png file it suffices to type:

```
set term png enhanced
set output "name_of_file.png"
replot
```

If you want to have hellenic, or some other fonts in your labels, you have to type the path of the fonts that you want to use:

```
set term png enhanced font "/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf"
set xlabel "write something &#947;&#961;&#940;&#968;&#949; &#954;&#940;&#964;&#953;"
set ylabel "write something"
set output "name_of_file.png" (*) -> see below
replot
```

If the font path does not complain with errors, then propably you have chosen it correctly, and it will display the fonts you want.

Every time someone makes a change and wants to save that change to the "name_of_file.png", someone should retype the (*) command first, then give the changes (for example set another xlabel) and finaly replot.

SOLUTION TO THE THREAD:
The choice of the right type of font is vital so as gnuplot to display correctly not only the letters someone wants, but also other things as the superscripts in labels. For example the:
set xlabel "x^{15}"
works very nice with the font type I used in here.

EDIT: If someone wants to remove the legends from a graph (the explanatory remarks which say on which color belongs which plot) the command:
set nokey
would suffice

Regards!

---

