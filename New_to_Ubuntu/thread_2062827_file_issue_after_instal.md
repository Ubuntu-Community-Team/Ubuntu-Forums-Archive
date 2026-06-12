---
title: "file issue after instal"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by TFSinclair on 2012-09-25
Please help. (this seems to be a consistent theme with me (sigh).
I installed a weather program using " sudo apt-get install indicator-weather" in Terminal in Ubuntu 12.04.  
When prompted, I entered my password and watched Terminal get and install the package. I can find it in both the "Downloads" and in "Files" but the package is not on my desktop nor is it functioning.
How might I resolve this issue and get the weather indicator to function?

---

### Post by Bashing-om on 2012-09-25
TFSinclair;

 I also had a similar experience, come to find out the data is from google, and google no longer supports the application//yahoo has the functionality however, some advise the info is not regularly updated. - I too do miss the weather applet in 12.04--

to remove:
```
sudo apt-get --purge remove indicator-weather
```open to replacement suggestions <==BDQ

---

### Post by newb85 on 2012-09-25
What Bashing-om says is correct, though in my experience, the data from Yahoo is updated frequently enough for my needs.

I think the OP's question, though, is how to start it up the first time.  You could search for indicator-weather in the Dash, you could hit Alt+F2 and run indicator-weather, or you could grab a terminal and

```
indicator-weather & exit
```

The app should appear in your system tray, although it won't show any information until you set your preferences, including your location.  ;)

---

### Post by Bashing-om on 2012-09-25
thank you newb85 ..me jumping to quick to conclusions. Sheeeshh.

[INDENT]glad someone is watching over my shoulder ==>BDQ

[/INDENT]

---

### Post by TFSinclair on 2012-09-26
I had to uninstal the bloody package.  Got it up and installed and had the same issues as before.
Thanks for the help. both of you!
TFSinsclair

---

