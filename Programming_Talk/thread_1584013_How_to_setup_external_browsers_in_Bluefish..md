---
title: "How to setup external browsers in Bluefish."
date: 2010-09-28
forum: Programming Talk
---

### Post by MasterNetra on 2010-09-28
This is of course not a personal help thread, A little bit ago I was having issues with setting up the external browsers. Figured out all I needed to do is supply the basic command plus "%s" that was it.

So for people getting started with Bluefish, you go to Edit > Preferences (At the bottom of the edit menu, you might have to maximize bluefish)

Next select External Programs. And under Browsers adjust Mozilla & Opera's command so that it reads:

```

(Mozilla):
firefox "%s" 

(Opera): 
opera "%s"


```

Also you can do:
```

(Mozilla):
/usr/bin/firefox "%s"

(Opera)
/usr/bin/opera "%s"

```

but why do more work when you don't have to right?

---Feel free to remove the rest if you want.

To add other browsers, first click "add" (obviously),

Double click the new entries label and give it the browsers name (or whatever you want to call it, thats name it will appear as in the external menu).

Then enter your browser's basic command then space and add "%s"

Then of course hit apply or ok.

Here is a quick list of browsers and their appropriate commands for the less active. :P

```

(Mozilla Firefox): firefox "%s"

(IceCat): icecat "%s"

(Google Chrome): google-chrome "%s"

(Chromium): chromium-browser "%s"

(Opera): opera "%s"

(Midori): midori "%s"


```

Hope this is helpful to people. 

Tested on Ubuntu (Lucid) + Bluefish - Verison: 1.0.7

---

### Post by Prescilla on 2011-07-26
Can you help me how to set up bluefish so that every time I click the View in browser button all HTML files will open in Chromium? Right now the default browser is Firefox. I really need to open all HTML files (written in Bluefish) in Google Chromium. Thank you!

---

### Post by aaawelder on 2011-12-31
I gave a try to all of the above with no success. I did not get the Chromium browser functioning correctly until I modified the "Command" to read:

chromium-browser '%p'&

now my hypertext documents display as they should, in a new tab, in "Chromium".

---

