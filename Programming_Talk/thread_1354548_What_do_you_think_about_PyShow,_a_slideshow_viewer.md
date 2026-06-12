---
title: "What do you think about PyShow, a slideshow viewer I wrote in Python?"
date: 2009-12-14
forum: Programming Talk
---

### Post by Jekshadow on 2009-12-14
For my Social Issues final this year, my assignment was to create a project describing a book we had read over the semester. I created a website with descriptions of the characters, pictures and clips from the different movies made about my book, a timeline of the plot and some other stuff, but I was bored, and so I thought that a desktop slideshow app might boost my grade a few points. I had just started learning Python (yesterday at about midnight), and I thought I would try to make something actually useful with it. This is where I came up with PyShow. 

URL: [https://launchpad.net/pyshow](https://launchpad.net/pyshow)

Features:
[LIST]
[*]Loads captions (names) from config file
[*]Loads slideshow name from config file
[*]Open Source (GPL v3)
[*]Simple, Lightweight (4.2kb for the script)
[/LIST]

What I still need to do:
[LIST]
[*]Create an app to automatically create zipped PyShows, ready for viewing
[*]Fullscreen Mode
[*]Fix button width issues, the button layout is kind of hacked together
[*]Make it keep aspect ratios when resizing images
[/LIST]

---

### Post by G|N| on 2009-12-14
I did not test it but it seems a very nice project! I was planning on writing the same thing but your code seems good enough for me to use :)

ps:
```
self.window.fullscreen()
```
will open the window fullscreen

---

### Post by Jekshadow on 2009-12-14
> **G|N| said:**
> I did not test it but it seems a very nice project! I was planning on writing the same thing but your code seems good enough for me to use :)

ps:
```
self.window.fullscreen()
```
will open the window fullscreen


I was planning on changing a few things when it becomes full screen, such as having the buttons be translucent, and making the image fill the entire screen, but thanks for the tip.

If you are planning to use it, I recommend pulling the source via bazaar from the 0.1 series I put up, as the trunk will most likely become unstable when I am working on some new features, and fixing up some problems with 0.1, such as button sizing and image scaling.

---

