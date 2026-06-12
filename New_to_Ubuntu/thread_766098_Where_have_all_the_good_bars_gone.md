---
title: "Where have all the good bars gone?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Kamir_Amar on 2008-04-25
Long time reader first time poster??

well not long time but after tonight it seems to be.

Just did a fresh install of 8.04 and everything was super duper... I even got all my stuff installed and reset up (bookmarks, XChat tweaks, so on)...

Then I figure hey lets make it look pretty... I went from cool and useful to a brick...

I installed emerald, compiz-fusion-bcop(?), compiz-manager-****(i forget the whole title). chose what pretties I wanted but left mostly defualts and that was it. 

I restart I come back to nothing but a picture... no top or bottom bars, nothing to clicky, pushing any keyboard commands turns up squat (tried alt+F2...nothing....Ctrl+Alt+F2...something)

I am at a total loss. Anything I have read in here has left me high and dry because I can not seem to access anything to do anything.

SO now I humble myself upon the good people of this land to please HELP ME!!!!

_Kamir(sometimes I feel like a noob)Amar

EDIT: Video card is NVidia 6150(?) it comes onboard with the Dell 531s

---

### Post by exactopposite on 2008-04-25
try ```
emerald --replace
```

---

### Post by Perfect Storm on 2008-04-25
and/or install compiz-icon. There you can control everything (plus reload and set what to use which will solve your problem).

---

### Post by Kamir_Amar on 2008-04-25
Well here is what is going on....

emerald --replace it just hangs there (this is done in the failsafe terminal) it doesn't freeze it just drops to the next line and blnks at me.

(also did it as sudo emerald --replace)

sudo apt-get install compiz-icon ... ... ... package can not be found or does not exist (not in those exact words)

I also tried for the ccsm but FAIL ....

(;_;) <--- me sad faced....

---

### Post by Perfect Storm on 2008-04-25
sorry, it's **fusion-icon** I always mix it the two words up.

---

### Post by Kamir_Amar on 2008-04-25
Sadly I shall soon be known as:

Kamir(FAIL)Amar

I installed it and ran it and it spit out a small set of stuff and then just sat there blinking at me.

```
*Detected Session: unknown
*Searching for installed applications
*NVIDIA on Xorg detected exporting: __GL_YIELD=NOTHING
*Using the GTK interface
*Starting Compiz:
executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp compiz.real 
(video) - WARN: No 8 bit GLX pixmap format, disabling YV12 image format.

Couldn't find a perfect decorator; trying all decorators.
Starting emerald
[]<---blinking box

```

So again I am at a loss...

I am tryin to do anything to not have to reinstall and reset up everything... I am sure you can understand...

Kamir]LIAF[Amar

---

### Post by Perfect Storm on 2008-04-25
is the nvidia driver installed, have you tested it by running some 3D apps/games?

---

