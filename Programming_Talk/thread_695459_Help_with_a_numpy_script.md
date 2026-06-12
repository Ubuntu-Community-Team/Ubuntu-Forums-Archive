---
title: "Help with a numpy script"
date: 2008-02-13
forum: Programming Talk
---

### Post by aquavitae on 2008-02-13
I've been asked at work to write a script to do some calculations.  The input is a text file containing records of the levels in a river i.e. time - value. I need to do a fast fourier transform on it, which means first tweaking the data into equal time steps.  I don't know much about the statistics behind it all, bu apparently the time step I should achieve is the peak in the histogram of the times.  At the moment my program looks like this (pseudocode)
```

times, values = extract values from file # i.e. [time0, time1], [value01, value1]
histogram = homemade_histogram_function(times)
time_step = peak(histogram)
new_times, newvalues = interpolate(times, values, time_step)
output = numpy.fft(newvalues)

```
The main problem with this is the size of the input data - an average input file is about 200Mb and contains millions of rows of data, that means each loop is run a few million times, and it takes about a day to run.

My first question is, is it necessary to do the histogram, or is there a quicker way of estimating the time_step without much impact on the fft?

The second question is, if I do need to calculate the peak of the histogram, whats the fastest way of doing it in python (using numpy).  I don't really want to have to do this in C to get the speed!

---

### Post by dwblas on 2008-02-13
Your problem is beyond me.  I just wanted to be sure that you knew about SciPy.  Check the fourier links here
[http://wiki.python.org/moin/NumericAndScientific/Libraries](http://wiki.python.org/moin/NumericAndScientific/Libraries)

---

### Post by aquavitae on 2008-02-14
Yes, I do know about scipy.  The fourier part is not really the problem - its the rest of the analysis thats slowing things down.  I've found a couple of places to improve the speed, but I think I might end up writing bits of it in C.

---

### Post by jeremytaylor on 2008-02-14
If this histogram step is the one slowing you down have you tried using the scipy.histogram function as it may be faster than your homegrown one?

An  other option might be to explore USFFT (unequally spaced fft), this isn't something I've ever used but there is  plenty of literature on the topic. You can also investigate non fft approaches, see for example [http://adsabs.harvard.edu/abs/1975Ap&SS..36..137D](http://adsabs.harvard.edu/abs/1975Ap&SS..36..137D)

If you are looking to do something like power spectrum estimation with your transformed data then there a fair few methods around that circumvent the need for FFTs, maximum likelihood methods are pretty prevalent. 

Jeremy

---

### Post by aquavitae on 2008-02-14
Thanks, I'll have a look at USFFT. I'm not sure exactly what the information is to be used for - I think its just plotted to a graph (freq - energy) to as long as that is the output it doesn't matter how I get there.

I tried numpy.histogram (I think its the same function as scipy uses, but I'm not sure) and it does speed things up quite a bit.  When I looked at the source I saw why mine was slow by comparison.  Now the slow part seems to be interpreting the input file - its basically csv, but has a lot of unnecessary data, and I need to convert 'yyy/mm/dd hh:mm:ss microseconds' to a number... thats a bit of a bottleneck, but I haven't really looked for better options yet.

---

