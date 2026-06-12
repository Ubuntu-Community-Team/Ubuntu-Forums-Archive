---
title: "football manager 8 in wine-black screen, working upon closing the window"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by bovier on 2008-08-07
Hi

I installed football manager 8 on my laptop with hardy heron using wine.
When I try to run it (using a no cd crack), it will work for a few screens, which is followed by a black screen. Nothing happens in the black screen, but I can move my mouse. However, when I close the wine window, football manager suddenly works again, bringing me to the first menu; the problem is that it will almost immediately close itself down after you do anything.

I looked around a little, and saw some people writing that I should disable compiz, i tried by " metacity --replace " but it did not change anything. 

what could be the problem:confused:

---

### Post by Tatty on 2008-08-07
To disable compiz in hardy all you need to do is System->Preferences->Appearance, then switch to the Visual Effects tab and select "None"

---

### Post by Catalyst2Death on 2008-08-07
If your already using metacity you don't need to replace your window manager... You can do this with the gui by going to System>Preferences>Appearance and on the Effects tab select no desktop effects.  Try running it again... If it still doesn't work, then try these registry commands:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Read through and pick accordingly, I'm not sure about which are appropriate for you so maybe you should check out the appdb page here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9479](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9479)

Wine is difficult to run, and I've never had good luck with it.  Maybe you'll have a different experience.  My advice would be to look for an open source alternative, and then come back to wine as a last resort.

---

### Post by bovier on 2008-08-07
> **Catalyst2Death said:**
> If your already using metacity you don't need to replace your window manager... You can do this with the gui by going to System>Preferences>Appearance and on the Effects tab select no desktop effects.  Try running it again... If it still doesn't work, then try these registry commands:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Read through and pick accordingly, I'm not sure about which are appropriate for you so maybe you should check out the appdb page here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9479](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9479)

Wine is difficult to run, and I've never had good luck with it.  Maybe you'll have a different experience.  My advice would be to look for an open source alternative, and then come back to wine as a last resort.

thanks for the tips with the visual effects...
are there alternatives for wine???:confused:

I will check the website. But I do think it is strange that everything will start to look as if it is working nicely after i close wine; it is just unfortunate that the game itself will also quickly close

---

### Post by Catalyst2Death on 2008-08-08
Wine is the only implementation of the windows api in Linux.  So no there aren't alternatives to wine.  There may however be open source alternatives to football manager 8.  I don't know what the program is or does, but you may want to google "football manager 8 alternatives Linux" or replace Linux with open source or Ubuntu or foss etc.

Wine is a program that takes windows commands and language and translates them to something that linux can understand.  So if you close wine, you'll kill the windows program that you were running.  Wine acts as an interface between the windows program and Linux.  Its difficult to tell you exactly what to try without knowing more about the program.

---

### Post by bovier on 2008-08-08
I don't know what happened, but after starting it again using the terminal, it worked (on the second try). 
Strange, no? that it is working under the terminal and not by simply clicking it in nautilus... anyway, thanks!

---

