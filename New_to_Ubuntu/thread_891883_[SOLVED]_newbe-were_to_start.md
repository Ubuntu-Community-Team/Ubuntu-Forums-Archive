---
title: "[SOLVED] newbe-were to start?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Homelinux on 2008-08-16
Hey guys I am new and really do not know were to start with this. A friend told me about Ubuntu and gave me his Ubuntu 8.04 LTS Desktop Edition CD. I have an older dell so it put it on there, was really easy to install and it is really cool. I am into audio and video stuff and so he told me to look up Ubuntu Studio. I downloaded it and it is awesome, Just a little over wellming so my problem is:

A) the _open movie editor_ opens but it shoots a bunch of small black lines across the desktop and then opens with everything working except the part where you see you movie, it is blank and you can see the desktop through there.

B) I looked through the synaptic and i can not find packages with audio and sound, loops for mixing up your own music, is there? or is there free sites to get those for Linux esp those that will work with Ubuntu.

Well I am really sorry this is so long and hopefully will not be this long any more.

---

### Post by Sealbhach on 2008-08-16
Hi, there are at least two music creation packages available in the Ubuntu repositories:

Rosegarden

Ardour

try them both - see which one is best for your needs.

You can install them through the terminal, it's simpler. Just open up a terminal and type:

```

sudo apt-get install rosegarden ardour
```

I've just looked on the web now and it seems Ardour already comes with Unbuntu Studio...!

I don't know what that problem with the movie player is. A good application I've discovered is Elisa Media Center - try it out.

If you can follow this, it should sort out most of your media playing problems:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


Hope this helps!

.

---

### Post by starcannon on 2008-08-16
Lets start out by finding out if your video card is functioning properly.

open a terminal Applications->Accessories->Terminal
and put in the following code:
```
glxinfo | grep direct
```

If it does not report
"direct rendering: Yes"

then it is possible your issues may be fixed by enabling it.

GL and Welcome to Ubuntu!

---

### Post by Homelinux on 2008-08-16
> **starcannon said:**
> Lets start out by finding out if your video card is functioning properly.

open a terminal Applications->Accessories->Terminal
and put in the following code:
```
glxinfo | grep direct
```

If it does not report
"direct rendering: Yes"

then it is possible your issues may be fixed by enabling it.

GL and Welcome to Ubuntu!

 did what you said and it came back "direct rendering: Yes"
 how do i enable it? and i think may graphics card is a legacy something or other or uses legacy something. anyway thanks for the welcome.

---

### Post by Sealbhach on 2008-08-17
> **Homelinux said:**
> did what you said and it came back "direct rendering: Yes"
 how do i enable it? and i think may graphics card is a legacy something or other or uses legacy something. anyway thanks for the welcome.

If it says "yes" then it is enabled, so nothing more to do there.


.

---

