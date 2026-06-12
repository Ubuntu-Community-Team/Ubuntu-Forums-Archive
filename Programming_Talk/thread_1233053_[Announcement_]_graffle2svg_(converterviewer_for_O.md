---
title: "[Announcement ] graffle2svg (converter/viewer for OmniGraffle files)"
date: 2009-08-06
forum: Programming Talk
---

### Post by evymetal on 2009-08-06
(I remember seeing people ask about this on the ubuntu forums before, so I thought I would announce this release here and get feedback)

Project Homepage:
[http://code.google.com/p/graffle2svg/](http://code.google.com/p/graffle2svg/)

graffle2svg is a python application / package for converting .graffle files (created with Omnigraffle [http://www.omnigroup.com/applications/omnigraffle/](http://www.omnigroup.com/applications/omnigraffle/) on OSX ) to .svg files

It's far from finished, and importantly I have focused on being able to understand diagrams like flowcharts correctly, rather than making the converted image look identical to the origional.

(you'll see what I mean if you convert any text!)

It's working well enough for me to open email attachments I get from others in my (Mac based) office - so I'm unlikely to focus on it much, but someone might find it useful.

I'm very open to patches or (specific) bug or feature requests - but patches are better :-)

---

### Post by pbulteel on 2009-12-02
Awesome! I had been looking for something like that and was trying to see if I could write something myself.

I did try it and discovered that OmniGraffle now stores fiiles in a directory instead of a zip file. I also was reading through the forums and they said that they're waiting on Apple to put SVG support into the OS since they use the OS for all the PDF, etc functionality. Well, since they did that in 10.6 when as soon as people start migrating over to Snow Leopard then I'm guessing they'll include native support for SVG.

Anyway, the fact that the graffle is a directory seems to cause problems with your python script. 

I'll leave a msg on the googlecode site and open a bug report. I'll try to help... :)

-P

---

