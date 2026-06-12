---
title: "Is C/C++ really that good for Image decoding?"
date: 2010-01-12
forum: Programming Talk
---

### Post by kahumba on 2010-01-12
Folks can anyone give an example of any Java library that would be close as good as those written in C/C++ ?

I'm writing a Java file browser to scratch several itches I can't stand in browsers like Nautilus and Thunar: their user interface and very slow to list (large) directories. And while it delivers crazy speed I'm nowhere near providing a decent implementation of "icon view" where I have to create snapshots of images so I had to limit to max 70KB the size of previewable images (as seen on icon_view.png). I _am_ using source subsampling to read "between the lines" if the image is bigger than the cell's size, but while it helps, it doesn't help enough.

Am I doomed with Java to stay at this image size limit?

ps: By speed I mean that both Nautilus and Thunar take like 6-8 seconds (which is frustrating a lot) to list dirs like /usr/bin or /usr/lib if visited for 1st time since reboot, when trying 2nd time the speed is faster cause the data is cached. My file browser lists those directories in about 0.1 seconds the _1st_ time while not sacrificing bells and whistles. So my computer feels *a lot* faster, except the "images preview issue".

---

### Post by PaulM1985 on 2010-01-12
You could use Java's BufferedImage class to store the image and use ImageIO.Read(File aFile) to get the images.  Create a class for an Icon which extends JPanel.  Override the paint() method and use drawImage() in the Graphics class. There is a call for drawImage() which will complete all scaling for you.  

Then you can either paint text or add labels for the file names.

Hope this is of some help.

Paul

---

