---
title: "is this functionality present in gnuplot ?"
date: 2013-01-28
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-28
Hey,
I would like to know if this functionality is present in gnuplot.
Please find attached the screenshot of what I'd like my final graph to look like. I'd like those numbers to be present to tell me under what conditions that value was got. (The arrows are drawn to tell you which numbers I'm asking about)

Basically against each point, I want to write the condition under which that value was got.(more like a comment when viewed later)

Thanks.

PS : Please don't go by numbers alone as my requirement.(I'm saying this because on second thought, it sounds as though a 3-d graph would solve the problem. I'm looking at a comment to be added, say something like, "in morning", "in evening", to tell you when the value was recorded)

---

### Post by tgalati4 on 2013-01-28
Not automatically.  You can write a macro to take values and print them as text labels.  This is from page 58 of the manual:

set_label(x, y, text) \
= sprintf("set label &#8217;%s&#8217; at %f, %f point pt 5", text, x, y)
eval set_label(1., 1., &#8217;one/one&#8217;)
eval set_label(2., 1., &#8217;two/one&#8217;)
eval set_label(1., 2., &#8217;one/two&#8217;)

You could also do a contour plot with labels.  As you said, a 3D plot may be what you need to convey the relationship.

---

### Post by IAMTubby on 2013-01-28
> **tgalati4 said:**
> Not automatically.  You can write a macro to take values and print them as text labels.  This is from page 58 of the manual:

Thanks a lot for the reply. I saw this in the manual on page58.
**36.8 Clabel**


> 
set_label(x, y, text) \
= sprintf("set label &#8217;%s&#8217; at %f, %f point pt 5", text, x, y)
eval set_label(1., 1., &#8217;one/one&#8217;)
eval set_label(2., 1., &#8217;two/one&#8217;)
eval set_label(1., 2., &#8217;one/two&#8217;)

tgalati4, I need some more explanation, would it be possible for you to add it in my .pg file below ? I tried adding but couldn't do it right.
```

#!/usr/bin/gnuplot
reset
set terminal png

set xdata time
set timefmt "%d/%m/%Y %H:%M:%S"
set format x "%H:%M"
set xlabel "time"

set ylabel "total actives"
set yrange [0:31]

set title "M7YC Performance per time"
set key reverse Left outside
set grid

set style data linespoints

plot "test.dat" using 1:3 title "slot 1", \
"" using 1:4 title "slot 2", \
"" using 1:5 title "slot 3", \
"" using 1:6 title "slot 4", \
"" using 1:7 title "slot 5", \
"" using 1:8 title "slot 6", \
"" using 1:9 title "slot 7", \
"" using 1:10 title "slot 8", \
"" using 1:11 title "slot 9", \
"" using 1:12 title "slot 10"
#

```
**For the moment, I'm using the .pg and .dat from** [http://linux.byexamples.com/archives/487/plot-your-graphs-with-command-line-gnuplot/](http://linux.byexamples.com/archives/487/plot-your-graphs-with-command-line-gnuplot/) **You can have a look at the .dat file from this page**




> 
You could also do a contour plot with labels.  As you said, a 3D plot may be what you need to convey the relationship.

I went through contour plot on [http://www.gnuplot.info/demo/contours.html](http://www.gnuplot.info/demo/contours.html). It's a bit like 3-d right ? Sir, I would be more interested in doing it the first method you suggested(using sprintf). That's exactly what I need.

Thanks.

---

### Post by steeldriver on 2013-01-28
I think you can do it like this:

```
$ cat >data <<EOF
A  0  0
"" 1  1
C  2  2
D  3  3
"" 4  4
"" 5  5
EOF

```i.e. make a data file in which one column contains the label strings (I used column 1), with empty strings for any points you don't want to label. Then just

```
gnuplot> plot 'data' using 3:2 w points, '' using 3:2:1 with labels offset 1,1
```

---

### Post by tgalati4 on 2013-01-28
I was going to suggest making a table, which is what *steeldriver* did.  But I have no idea what your values are or what the data represents or what you are trying to convey.  I would need a big picture of what you are trying to convey before I could make suggestions.  Gnuplot has a lot of power, but you need to spend some time with it to become proficient.  I first started using gnuplot in 1987 on HP Irix Unix workstations.  That shows you how long it has been around.

It looks like you are on your way.

---

### Post by IAMTubby on 2013-01-28
> **steeldriver said:**
> 
```
gnuplot> plot 'data' using 3:2 w points, '' using 3:2:1 with labels offset 1,1
```

> **tgalati4 said:**
> I was going to suggest making a table, which is what *steeldriver* did.

steeldriver,tgalati4, wow :D
1. exactly what I needed, I tried understanding what 3:2:1 stands for. Is it x:y:label ?

2. tried deciphering, but couldn't understand what the **' '** stands for in **using 3:2 w points, ''**. Can you please explain that ?

Thanks

---

### Post by steeldriver on 2013-01-28
1. yes that's right

2. afaik it's just a shorthand way to repeat the name of the data file i.e. in this context '' is the same as 'data' (I think of it as 'ditto')

Also note the abbreviations 'u' = using and 'w' = with etc.

I'm *not* a regular gnuplot user so don't take anything I say as gospel though - hopefully tgalati4 will chime in if I've got it wrong

---

### Post by IAMTubby on 2013-01-28
> **steeldriver said:**
> 1. yes that's right
Thanks for the clarification steeldriver. I tried altering the file you gave and am getting expected graphs.

But I have 1 final question.
Don't you think there is no need to mention 3:2:1 since we are already mentioning using 3:2 w points earlier in the line.
I mean it can be confusing for gnuplot if we mention something like**plot 'data' using 3:2 w points, '' using 2:3:1 with labels offset 1,1**. According to me, here, we are asking to plot 3 against 2 initially and later asking to plot 2 against 3. Or are my assumptions incorrect ? :)

> 
2. afaik it's just a shorthand way to repeat the name of the data file i.e. in this context '' is the same as 'data' (I think of it as 'ditto')

okay.

> 
Also note the abbreviations 'u' = using and 'w' = with etc.
Shall note that.

> 
I'm *not* a regular gnuplot user so don't take anything I say as gospel though - hopefully tgalati4 will chime in if I've got it wrong
:) okay

---

### Post by steeldriver on 2013-01-28
They're really 2 separate plot statements (separated by the comma)

```
plot 'data' using 3:2 with points
```THEN (overlay)

```
plot 'data' using 3:2:1 with labels offset 1,1
```Both need the 3:2 because they are the (x,y) coordinates where it should place the points and then the labels

If you run the above 2 commands separately you will see what I mean

---

### Post by IAMTubby on 2013-01-28
> **steeldriver said:**
> They're really 2 separate plot statements (separated by the comma)

```
plot 'data' using 3:2 with points
```THEN (overlay)

```
plot 'data' using 3:2:1 with labels offset 1,1
```Both need the 3:2 because they are the (x,y) coordinates where it should place the points and then the labels

If you run the above 2 commands separately you will see what I mean
oh steeldriver, thanks a lot :)
it's all clear.

thanks tgalati4.

Marking the thread as solved.

---

### Post by tgalati4 on 2013-01-28
gnuplot can take many file formats.  You can separate your data with gum wrappers and gnuplot will still be able to plot it.

In general you will have 1 column with data labels, a second column with X values and a third column with Y values.  So plotting 3:2 w points means plot the third column against the 2 column and use points (as opposed to lines or circles) to show the data.  You can use a massive table with 100 columns and plot many different combinations, all on the same plot.

Look for the gnuplot tutorials on the web and go through them.  You will be an expert in no time.

---

### Post by IAMTubby on 2013-01-29
> **tgalati4 said:**
> So plotting 3:2 w points means plot the third column against the 2 column and use points (as opposed to lines or circles) to show the data.

okay.

> 
Look for the gnuplot tutorials on the web and go through them.  You will be an expert in no time.
ha ha 
thanks tgalati4, I shall do that. :)

---

### Post by IAMTubby on 2013-01-29
> **steeldriver said:**
> gnuplot> plot 'data' using 3:2 w points, '' using 3:2:1 with labels offset 1,1

> **tgalati4 said:**
> 
In general you will have 1 column with data labels, a second column with X values and a third column with Y values.  So plotting 3:2 w points means plot the third column against the 2 column and use points (as opposed to lines or circles) to show the data.

steeldriver, tgalati4
I'm sorry to post again in this thread but I'll make sure I don't stretch this long.

By using steelsriver's code **gnuplot> plot 'data' using 3:2 w points, '' using 3:2:1 with labels offset 1,1**, I have got the label, but only for 1 line in the graph. Why am I not getting for the other two?

Please find attached my files. I have attached the .dat and .pg(gnuplot script file) as .doc because there are limitations on file extensions I can upload. The actual files are name.dat and name.pg

Thanks.

---

### Post by steeldriver on 2013-01-29
You are not changing the y-values for the subsequent label plots - so they are plotting 3 times in the same place (i.e. at the location of the 1st data set)

```
plot "getpminfo.dat" using 2:3 title "System Input Power", '' using 2:3:1 with labels offset 1,1, \
"" using 2:[COLOR=Red]4[/COLOR] title "Peak System Power", '' using 2[COLOR=Red]:3[/COLOR]:1 with labels offset 1,1, \
"" using 2[COLOR=Red]:5[/COLOR] title "Minimum System Power", '' using 2[COLOR=Red]:3[/COLOR]:1 with labels offset 1,1, \
"" using 2[COLOR=Red]:6[/COLOR] title "System Idle Power", '' using 2[COLOR=Red]:3[/COLOR]:1 with labels offset 1,1
```

---

### Post by IAMTubby on 2013-01-29
> **steeldriver said:**
> You are not changing the y-values for the subsequent label plots - so they are plotting 3 times in the same place (i.e. at the location of the 1st data set)

urghhhh steeldriver, :)
thanks a lot. Attaching screesnhot with correct graph and sorry for the trouble. I was so into getting the syntax right that I wasn't looking at the most important detail which is the coordinates.

---

### Post by steeldriver on 2013-01-29
no problem - sometimes these things just need a fresh pair of eyes

---

### Post by IAMTubby on 2013-01-29
> **steeldriver said:**
> no problem - sometimes these things just need a fresh pair of eyes
:)

---

