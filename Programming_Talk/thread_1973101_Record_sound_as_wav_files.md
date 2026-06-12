---
title: "Record sound as wav files"
date: 2012-05-04
forum: Programming Talk
---

### Post by forsubhi on 2012-05-04
I want to develop program to record sounds from microphone and save them as wav file to use them with sphinxtrain (tool for voice recognition ) , I want to develop program with java 

I need help to choose best library of java and take benefit from jdk 7 if possible 

I see media library , is it the best library and , how could I use it ?

is there any existing simple code to do that ? 

I want to draw spectrogram if possible .

---

### Post by malikinam on 2012-05-04
i have a drawing which will help you in you goals do you want to get it and that is absolutely free.


[long island real estate](http://www.therealestateone.com/long-island-real-estate/) | [allegheny county real estate](http://www.therealestateone.com/allegheny-county-real-estate/)

---

### Post by 11jmb on 2012-05-04
For capturing with a microphone, java has a library for that.
[http://docs.oracle.com/javase/tutorial/sound/capturing.html](http://docs.oracle.com/javase/tutorial/sound/capturing.html)

For writing to a .wav file, I'm not sure. I haven't done that. That may be something simple to homebrew if you want to go that route. Depends on how simple the .wav standard is.

For writing a spectrogram, again I don't know about any libraries. a quick solution would be to use fftw with JNI. Then you can assign a color scale to the FFT values and draw your FFT bins as rectangles on a panel fairly easily.

caveat for the last two: homebrew solutions like that are not the best choice unless 1) you're doing it as a learning exercise or 2) you can't find a good library that you can apply to your task.

no need to re-invent the wheel.

---

