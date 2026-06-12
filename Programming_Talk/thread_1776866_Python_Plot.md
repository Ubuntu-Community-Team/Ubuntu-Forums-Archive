---
title: "Python Plot"
date: 2011-06-06
forum: Programming Talk
---

### Post by Mosabama on 2011-06-06
Any body knows what library is used for plotting the ubuntu system monitor cpu and memory usage? and if that available for python ?

if not, can you tell me whats the best to use with python and give me a link for a simple tutorial for that.

its that I am not sure which one to use specially that I have no experience in this.

Thanks

---

### Post by lavinog on 2011-06-07
I believe it uses cairo.
There is a python module for it:
[http://cairographics.org/pycairo/](http://cairographics.org/pycairo/)

---

### Post by Mosabama on 2011-06-09
Thanks .. but I couldn't understand it, and I didnt find any example like the one in the ubuntu system monitor :( I tried to download the source and understand it but no luck. I am not that much experienced in this as I am really new.

I tried Matplotlib but it takes alot of processing when the plotting is live. it really kills the laptop. 

I would appreciate it if some one can make me a simple example specially with the one used in system monitor as it looks really good and takes no processing power at all.

Thanks again

---

### Post by tbastian on 2011-06-09
I had to do some plotting last year in C, so I did some searching around. I ended up having to write my own library since I could not find anything that fit my application well. (I'm not sure whats available for python)

That being said: Cairo is not a plotting library per-se, but rather a drawing library which can be used to create plots, and if you're looking for a super simple application, it wouldn't be that difficult.

---

### Post by Mosabama on 2011-06-09
I have read about Cairoplot .. but I dont know if this can be integrated with wx. I searched for example but did not find any.

---

### Post by cgroza on 2011-06-09
I think wxWidgets has a plot class.

---

