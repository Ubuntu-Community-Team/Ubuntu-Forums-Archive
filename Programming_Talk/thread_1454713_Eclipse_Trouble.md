---
title: "Eclipse Trouble"
date: 2010-04-15
forum: Programming Talk
---

### Post by Vistz on 2010-04-15
I downloaded Eclipse through the "Ubuntu Software Center". When I go to File>>New, the only options I get are: Project, Folder, File, Untitled Text File, and Other. This happens even after I create a new project. I've checked Synaptic and confirmed that I have the JRE/fonts installed.

---

### Post by km0r3 on 2010-04-15
Screenshot?

---

### Post by Vistz on 2010-04-15
[IMG]http://i592.photobucket.com/albums/tt7/icer_kingz/Eclipse.png[/IMG]

The same thing appears when I go to File>>New

---

### Post by GregBrannon on 2010-04-15
Sorry to be dense, but what are you trying to do?

---

### Post by Vistz on 2010-04-15
I'm trying to create a class. Instead of the options shown, there should be about 10-12 other options: "Package", "Class", "Interface", etc..

---

### Post by Vistz on 2010-04-15
*Update

I got it to work by running this

```
sudo apt-get install eclipse-jdt eclipse-plugin-cvs eclipse-pde
```

---

