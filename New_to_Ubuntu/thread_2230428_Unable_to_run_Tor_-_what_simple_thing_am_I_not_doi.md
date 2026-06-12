---
title: "Unable to run Tor - what simple thing am I not doing?"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by verymadpip on 2014-06-19
Hi everybody.
I'm trying to launch Tor from "start-tor-browser" script in the folder I've extracted from the browser bundle tarball which I downloaded from the Tor website. (Hope I've got the correct terminology in that sentence...........)

I'm running Ubuntu 14.04 64 bit, with the 64 bit browser bundle.

I have the script set to execute in the permissions tab, but all that happens when I double click it is a gedit window opens, showing me the text of the script itself (I assume that's what it is anyway).
This behaviour occurs with & without execute being set.

I'm sure I'm missing something incredibly simple, I just can't put my finger on it.
Anybody have any ideas?

---

### Post by open2reason on 2014-06-19
I too am suffering from that problem even though I was a satisified user when running Tor under Ubuntu12.04lts and sometimes find myself resorting to [https://tails.boum.org/](https://tails.boum.org/) when I would have reached for Tor.

---

### Post by avesummathat on 2014-06-19
Open preferences in Nautilus (Edit > Preferences)
Then go to the to "Behaviour" tab.
Change "Executable text files" to either "run... when opened", or "Ask each time" - I have it on ask each time, as sometimes I want to open it in gedit, and sometimes I want it to run...

Alternatively, run it in a terminal by typing 
```
./start-tor-browser
```

---

### Post by open2reason on 2014-06-19
Many thanks for your help, I fear my memory must be fading. Thanks again.

---

### Post by Nobody Nessie on 2014-06-19
Right click the start-tor-browser file and set its permission to "execute as a program" (or something like that). 

You can create a shortcut somewhere in your applications launcher with the following command :

```
yourownpath/tor-browser_en-US/start-tor-browser start
```

Or type directly in your terminal :

```
yourownpath/tor-browser_en-US/start-tor-browser start
```

---

### Post by verymadpip on 2014-06-19
Hi again!

avesummathat: that's ther chappie I was looking for!!!  Couldn't work out why I no longer had that option pop up or even where I was supposed to be looking for it.
Sometimes my density astounds me.

(I did get tor running by dragging & dropping the script file into a terminal.  For me that is a less than pleasing state of affairs, however).

---

