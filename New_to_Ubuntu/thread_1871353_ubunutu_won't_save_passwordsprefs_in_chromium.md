---
title: "ubunutu won't save passwords/prefs in chromium"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by d_stroyer on 2011-10-28
i installed chromium afer i got ubuntu because i'm not a fan of firefox. everytime it starts up, it asks if i want to make it my default browser and i click yes. also, i choose the option to save passwords when it asks. then, when i restart my chromium it gives me the same prompts and does not remember my choices. any ideas on what's wrong? thanks.

---

### Post by wolfen69 on 2011-10-28
Sounds like your config may be screwed up. If you don't mind starting over (settings) with chromium, just go into /home/user/.config and delete the chromium folder. Restart chromium, and a new config file will be generated.

---

### Post by d_stroyer on 2011-11-07
ok..umm i'm pretty much new to linux. i understand what you are telling me to do but how do i get to that? if i click on my home folder there is nothing that says user? please dumb it down for me a little? thanks.

---

### Post by trivialpackets on 2011-11-07
I don't use chromium, but I believe what he is suggesting is that you close Chromium, open a Terminal, and type in the following:

rm -rf ~/.config/chromium

---

### Post by trivialpackets on 2011-11-07
Alternatively, you can do the following if the command line isn't your thing.
 1) close chromium
 2) Open your home folder
 3) Press Ctrl+H to show the hidden folders
 4) Double click on the .config folder that appears (the . before the name indicates that it's a hidden folder!)
 5) Delete the chromium folder
 6) Restart Chromium.

I would also go into your home folder again and do the Ctrl+H again to hide the hidden folders if you go this route.  Best of luck and let us know how it goes!

---

