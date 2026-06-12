---
title: "How to add plugins to Audacity in Ubuntu Studio"
date: 2016-01-28
forum: New to Ubuntu
---

### Post by stephen376 on 2016-01-28
Hey Community, Hope you're all very well. Been using Linux on and off for years still class myself very much as a beginner. Anyway to my question: I want to know how to add plugins to Audacity on Ubuntu Studio. Please go easy on me with the instructions as I could get lost easily. Thanks in advance guys!

---

### Post by ajgreeny on 2016-01-28
Look for the various ladspa plugins in software-centre or synaptic and install them in the usual way.
I have the **swh-plugins** and **tap-plugins** installed and that gives me all I need, but there are others available so have a look and try them.

You access the plugins from the Effects menu item in Audacity, as you probably know already.

---

### Post by stephen376 on 2016-01-29
Thank you very much for your help so far. I noticed i already have those plugins installed via software centre. I have downloaded the following plug in to my downloads folder: 

[http://theaudacitytopodcast.com/chriss-dynamic-compressor-plugin-for-audacity/](http://theaudacitytopodcast.com/chriss-dynamic-compressor-plugin-for-audacity/) 

How can i make it active, usable in the effects bar. 

I realise this is straight forward on mac or windows as in you just put it in the plug ins folder for audacity but in linux it seems much trickier.

I should mention I know how to use Audacity to edit on Mac or windows. I just don't know how to add third party plugins using linux. Thanks.

---

### Post by jim_deadlock on 2016-01-29
There is a "How to install" section right there on the page you linked (including Linux).

---

### Post by howefield on 2016-01-29
Assuming that you have download the zip file and extracted to the Downloads folder :-

Open a terminal and use the following command to create a folder within your /home folder.

```
mkdir -p ~/.audacity-files/plug-ins
```

then, move the compress.ny file into the new folder with..

```
cp ~/Downloads/compress.ny ~/.audacity-files/plug-ins
```

Finally enable the plugin in Audacity by starting (or restart if already open)  Audacity > Effect menu > Add / Remove Plugins > Find “compress” and select it (easy to find if you click on the New radial filter button) > Click Enable and then OK.

---

### Post by stephen376 on 2016-01-31
You're a legend Howes, thank you very much got it working now. Much easier than i expected. Looking forward to editing full time in linux now ;)

---

### Post by howefield on 2016-01-31
Cool, well done.

Happy editing :)

---

