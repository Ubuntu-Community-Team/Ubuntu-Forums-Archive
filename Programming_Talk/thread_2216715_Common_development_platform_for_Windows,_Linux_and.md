---
title: "Common development platform for Windows, Linux and Mac"
date: 2014-04-13
forum: Programming Talk
---

### Post by zobayer1 on 2014-04-13
Hello everyone, I was hoping to get some suggestions about building an application that will work in all the three major platforms without much modification. The application will sound / microphone / webcam / screen etc. I know Java (and Java EE), a little python. Not really good with HTML5+Js, but I am open to any other platform that will help me to build this app. By common platform, I mean I can generate executable programs differently for each os, but it will be easier if the main codebase remains the same. As for platform independence, I presume Python or Java will be a better choice. Help me to get the right direction.

Thanks in advance.

---

### Post by ssam on 2014-04-14
For AV stuff I'd look at gstreamer which is very common on Linux, and available for win and mac. It is used in a lot of projects [http://gstreamer.freedesktop.org/apps/](http://gstreamer.freedesktop.org/apps/)

I looks like the java bindings are not kept up to date ( [http://code.google.com/p/gstreamer-java/](http://code.google.com/p/gstreamer-java/) ), its commonly used with C or python.

---

