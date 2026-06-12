---
title: "Need help picking a language to programy may little app in : )"
date: 2007-11-03
forum: Programming Talk
---

### Post by thenetduck on 2007-11-03
Hello once again my good programming friends.

I have an idea for a program that I would like to hack up don't know what language to use. I am developing it for Linux .deb base (Ubuntu of course) but would to be able to make Windows/Mac versions for it in the future as well. 

When you install the app, I want the user to be able to right click on a folder in their director and select an option that I set. This would then enable my app on that folder. 

My first thoughts are C++ because it would be a bit faster than Python (I think right?) but don't know what will be easier to create a right click on a folder action with. 

So, does anyone know what would work best in this situation? 

Thanks a bunch

The Net Duck

---

### Post by slavik on 2007-11-03
umm, nautilus has an API that you can use with Python to create actions ... kind of "Open Terminal Here" type of context option ...

---

### Post by thenetduck on 2007-11-03
> **slavik said:**
> umm, nautilus has an API that you can use with Python to create actions ... kind of "Open Terminal Here" type of context option ...

Yes, I want it to work like Open Terminal Here... man I love that app, so small but soo good. 

I wonder if the best thing for me to do is to check out the Nautilus Dev site to see if they have anything that plays nice with C++. or good docs at least.  

The Net Duck

---

### Post by Wybiral on 2007-11-03
You never mentioned what the actual software was going to do. I'm pretty sure you need Python to create plugins for nautilus, so Python is definitely a good option for the entire application. If it does end up requiring more speed you can write the cpu-critical modules in C and still use Python for the majority of it.

---

### Post by thenetduck on 2007-11-03
> **Wybiral said:**
> You never mentioned what the actual software was going to do. I'm pretty sure you need Python to create plugins for nautilus, so Python is definitely a good option for the entire application. If it does end up requiring more speed you can write the cpu-critical modules in C and still use Python for the majority of it.

Thanks. I don't have the all mighty experience quit yet so didn't realize you could do that, but then again, I guess anything is possible. 

The app is basically like a small version of Time Machine (the app they have on the Macs these days). No giant back ups. etc. To be honest, it's my first app that I think I can really do, so am obviously going to make it open source, just want to lay out a skeleton. 

I think I am going to go with Python then run things in C like you suggested if I need something that can crunch things. 

Thanks
The Net Duck

---

### Post by Wybiral on 2007-11-03
Yeah, writing modules for Python in C is pretty simple if you're familiar with C. Luckily Python has a plethora of modules available for you to begin with, so you may be able to find everything you're looking for. It certainly has file handling / database / compression modules like you'll need for this project. Good luck!

---

### Post by ghostdog74 on 2007-11-03
> **thenetduck said:**
> 
The app is basically like a small version of Time Machine (the app they have on the Macs these days). 
there's something similar already started , see [here]("https://launchpad.net/timevault/+download")

---

### Post by slavik on 2007-11-03
just use ext3cow :)

---

