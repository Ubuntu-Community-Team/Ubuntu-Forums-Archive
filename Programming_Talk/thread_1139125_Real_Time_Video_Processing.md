---
title: "Real Time Video Processing"
date: 2009-04-26
forum: Programming Talk
---

### Post by Novemberox on 2009-04-26
Hi there,

I'm about to create that would be operating on video, format doesn't matter. First of all I need information, how can I open video file and play in window, I don't really know which libraries should I use. My first guess was revel lib, but I'm not quite sure where to start. This program function is to find road lines from movie like this: [http://www.dailymotion.pl/video/x5ut86_formula-1-camera-car-giro-gp-di-spa_auto](http://www.dailymotion.pl/video/x5ut86_formula-1-camera-car-giro-gp-di-spa_auto)

My goals are:
- create window with original movie
- create second window displaying movie/image after processing

What I need, or I think I need:
- library that provides:
opening video file
playing it
getting information about each pixel. I mean that, I would like to have aces to position X,Y and it's value (maybe I will operate on images that will be created from movie)
- create detection function
I would like to find straight lines

Kind of processing I would like to do:
- simple convolution (some edge filters)
- threshold
- maybe sth else

Can you tell me how should I start working on this project. Any advice will be very useful. What libraries should I use? Did I forget about something?

Thanks in advance.


PS I hope it's right place for this topic and sorry for my poor English.

---

### Post by eye208 on 2009-04-27
Check out the [GStreamer](http://www.gstreamer.net/) multimedia framework. For an example that uses GStreamer for realtime video processing, take a look at [Cheese](http://projects.gnome.org/cheese/).

---

