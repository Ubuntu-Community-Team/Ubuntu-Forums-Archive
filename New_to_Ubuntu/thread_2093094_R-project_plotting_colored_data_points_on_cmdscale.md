---
title: "R-project: plotting colored data points on cmdscale PCoA"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by MalcolmThompson on 2012-12-09
Hello, 

I have been trying to plot a color-coded PCoA plot based on cmdscale with 
the following commands: 

>Data=read.table("Data.txt",row.names=1,header=T,sep="\t") 
>Data 
>Data.pcoa=cmdscale(Data,k=2,eig=T) 
>Data.pcoa 
>ordiplot(Data.pcoa) 

However, I have no idea how to start to color code based on groups by rows (ie. group A, B, C), 
not columns, according to the Data.pcoa file. 

ie. 

Gr1 Gr2 
A 0.5 0.4 
A 0.4 0.5 
A 0.4 0.3 
B 0.2 0.4 
B 0.4 0.2 
C 0.2 0.2 

Also, as you can see, there is no X and Y axis, therefore, I cannot use the standard commands for a biplot.

Any help would be greatly appreciated as I am a beginner (exact commands would be even better). 

Thank you. 

Malcolm Thompson

---

### Post by tgalati4 on 2012-12-09
I like gnuplot for complicated plots.  [http://www.gnuplot.info/](http://www.gnuplot.info/)
It's possible that R-plot uses gnuplot internals for plotting, so poking around the documentation might provide some clues.

---

### Post by MalcolmThompson on 2012-12-09
Thanks for the offer, but I am really new at this and no book can help me at the moment.
 
If you have any ideas, it would be greatly appreciated.
 
Thanks.
 
Malcolm

---

### Post by PGScooter on 2012-12-10
best place to ask is [www.stackoverflow.com](www.stackoverflow.com)
They have a friendly and knowledgeable R user base over there.

---

