---
title: "Finding the right program language for downloading and displaying images"
date: 2011-11-23
forum: Programming Talk
---

### Post by DesignXpress on 2011-11-23
I'm working on a BeagleBoard with on it Ubuntu 11.10 (a minimal install, that has (had) no X installed). The target is to get the device to download an XML file, interpret the file and download images contained. Then the device should display each image alike a photoframe untill the XML on the server changes.

I'd like to write it myself (unless a ready to use program exists and would work without a desktop environment). But up until today I didn't get anywhere on the decision which program language to use.

This morning I wrote some Python scripts that display an image on the screen (using pygame to get the image to display). I also downloaded some files, so although it will take me quite some work I'd get this running in Python (probably).

But is Python right for me? It is just the first one I got things done with.

The target is to have the device boot up and automatically run the script/program as long as it receives no other user input. It must be able to detect the internet is up and possibly try to fix if it isn't.

Or am I better of looking at another language instead. So far (few hours) Python has been easy to understand, comming from PHP and Pascal as previous languages...

I did already look at the topics at the top of this section, and they are nice resources to discover the different languages, but it is not very clear if they will get me there, or if any of those can be recommended given the limited resources but also limited functionality needed (internet (wifi), xml parsing and display of images)

---

