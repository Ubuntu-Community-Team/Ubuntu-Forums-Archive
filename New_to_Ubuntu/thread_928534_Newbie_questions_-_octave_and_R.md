---
title: "Newbie questions - octave and R"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Ippiki_Okami on 2008-09-24
Hey everybody
ive just set up a dual boot with ubuntu and vista and must say how smooth the whole thing went! Im already only using vista when absolutely necessary!

However ive had a bit of trouble with the following and was wondering if any one can help:

--i downloaded gnuoctave via the repositries and its seems to work fine in the terminal initially. I can define variables etc... however if i go plot a function i get the following error:

```
octave:1> x = linspace(0, 2*pi, 100);
octave:2> y = sin(x);
octave:3> plot(x, y);
sh: gnuplot: not found
sh: gnuplot: not found
error: compare_versions: version numbers must be a single row
error: evaluating if command near line 78, column 3
error: called from `compare_versions' in file `/usr/share/octave/3.0.0/m/miscellaneous/compare_versions.m'
error: if: error evaluating conditional expression
error: evaluating if command near line 209, column 5
error: evaluating if command near line 206, column 3
error: called from `drawnow:enhanced_term' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'
error: evaluating assignment expression near line 169, column 14
error: evaluating if command near line 138, column 3
error: called from `drawnow:init_plot_stream' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'
error: evaluating assignment expression near line 125, column 14
error: evaluating if command near line 117, column 3
error: called from `drawnow:open_gnuplot_stream' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'
error: evaluating if command near line 78, column 8
error: evaluating if command near line 77, column 6
error: evaluating if command near line 74, column 4
error: evaluating if command near line 72, column 2
error: evaluating for command near line 71, column 7
error: evaluating if command near line 45, column 5
error: called from `drawnow' in file `/usr/share/octave/3.0.0/m/plot/drawnow.m'

```

does this mean its as simple as installing gnuplot? 

--also does anyone know of any good tutorials on how to install the R statistics package? i can only seem to find a GUI version in the repos...

--another thing ive noticed is that if i have firefox open at the same time as the terminal, and close the terminal then firefox will automatically close.. is this just a setting ive changed inadvertently or something?

Thanks heaps
Okami

---

### Post by prshah on 2008-09-24
> **Ippiki_Okami said:**
> 
does this mean its as simple as installing gnuplot? 

--another thing ive noticed is that if i have firefox open at the same time as the terminal, and close the terminal then firefox will automatically close.. is this just a setting ive changed inadvertently or something?



a) (installing gnuplot) yes, that should do it.
b) The process started in the terminal is a "child" to the terminal; close the terminal and the process is closed (terminated/killed) as well.

---

