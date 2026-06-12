---
title: "Draw Bar Graph by using GNUPlot"
date: 2013-02-07
forum: Programming Talk
---

### Post by tzeronone on 2013-02-07
For example, I have a file called "data.txt". And the content is:
[HTML]Iker_Casillas 31
Sergio_Ramos 26
Karim_Benzema 25[/HTML]I would like to plot the data into a bar graph. So far, here is my code:
[HTML]set boxwidth 1 relative
set style data histograms
set style fill solid 1.0 border -1
set datafile separator " "
plot '0/0_0.0.txt' using 2:xticlabels(1) notitle
set terminal jpeg truecolor font small size 600,500
set output 'try.jpeg'
replot[/HTML]However, due to the length of the name, it will overlapped with each other. Any idea how to solve this? And I would like to add value label on top of each bar. Any help? Thank you.

---

