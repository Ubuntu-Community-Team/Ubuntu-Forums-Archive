---
title: "single click to open instead of double click"
date: 2018-06-07
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-07
there used to be setting in old gnome that you could open files or folders or apps with single click.  also you could bypass trash for complete deltion.  is this possible in new ubuntu?

---

### Post by Frogs Hair on 2018-06-07
Check in file manger Preferences > Behavior

---

### Post by bodhin2 on 2018-06-07
sorry but i have there is no menu or preferncces in my installs.  that is why i asked.  I do not see it anywhere.  strange eh?

---

### Post by Frogs Hair on 2018-06-07
There should be an icon opposite of the window buttons with a drop down menu.

---

### Post by bodhin2 on 2018-06-07
i do not have that!!!  maybe i can get a pic.  having issues on install on my wife;s laptop at the moment.  that is really strange that is why i asked.  thanks

trying to get a pic here.

---

### Post by Frogs Hair on 2018-06-07
I'm still running an upgrade from 17.10 to 18.04 since beta 1 , but have the current version of Files/Nautilus. Do you see anything different with the default theme ?

---

### Post by bodhin2 on 2018-06-07
i am sorry - i cannot answer that.  this is 18.04 ubuntu reg flavor as such.  see my questions are not that stupid when i do not see what i am used to since i have used linux pretty much other than enlightenment and even then i think that was possible - i am 99% certain

---

### Post by Frogs Hair on 2018-06-07
I too have 18.04 . Switch to the default theme and see if anything changes on the title bar in the file manager.

---

### Post by bodhin2 on 2018-06-07
ok not sure what it was though.  will try - thank you.  even before i tweaked the theme it was not therethat i remeber.

did adwaitha deafult in my menu and nothing.....

---

### Post by wildmanne39 on 2018-06-07
I had the same issue on a fresh install but not when I upgraded from 17.10 to 18.04, here is how to solve it.

[https://ubuntuforums.org/showthread.php?t=2388106](https://ubuntuforums.org/showthread.php?t=2388106)

I had to log out and back in for it to work.

---

### Post by Frogs Hair on 2018-06-07
I've installed the same theme as you and still see the menu .:confused:

---

### Post by bodhin2 on 2018-06-07
FH - i just installed on my wifes and haven't tweaked anything with another burned dvd - and all 3 laptops are the same.   weird eh??????

---

### Post by Frogs Hair on 2018-06-08
I probably have an old configuration due to the fact I upgraded. I thought I might try a clean installation this weekend , but nothing is broken.

---

### Post by bodhin2 on 2018-06-08
Thanks again for all of your help.  as i said.  i know there used to be in preferences a way to tweak some stuff.  like trash and clicks....  but when i saw this layout - i had to ask.  weird eh????  Have a great weekend!

---

### Post by tea for one on 2018-06-08
> **bodhin2 said:**
> Thanks again for all of your help.  as i said.  i know there used to be in preferences a way to tweak some stuff.  like trash and clicks....  but when i saw this layout - i had to ask.  weird eh????  Have a great weekend!

Preferences on some Gnome applications (i.e. Nautilus, Gnome Calculator, Terminal to name but three) can be accessed by right click on the application icon on the top bar.

However, I have noticed that some older Gnome extensions prevent the user from opening the menu with a right click.

I use Taskbar version 57 and this extension now supports the right click access to menus, help, preferences etc.

Best wishes

---

### Post by bodhin2 on 2018-06-08
thanks but doesn't work or is not possible!  :-(

---

### Post by deadflowr on 2018-06-08
Another option is dconf/gsettings can do the change.
From a graphical way install dconf editor and go to org > gnome > nautilus > preferences and click on click-policy
Turn off Use default value.
Then click on custom value and select single.
Then click Apply on the bottom right corner.
It should reset it automatically to single click.

Or from the command line
```
gsettings set org.gnome.nautilus.preferences click-policy single
```


Also, you do not have a Title name in the top panel for Files? (the gnome-shell panel, not the Files program panel)
That's usually there and clickable for the menu.

---

### Post by Frogs Hair on 2018-06-08
On my 25 minute old clean installation of 18.04 the preferences for files shows in the app indicator on the top panel. Single click and trash options are in the behavior settings.

---

### Post by bodhin2 on 2018-06-08
pardon my expression but DAMN - never never thought to try that.   it is there.  thank you so much for your persistence to help.  I never would have thought to click on that aspect!....  makes me laugh!   Out Loud Too!!!!! hoe stupid.

thannk you yet again my friend!!!!!!  does not have a delete without going to trash but the single click helps so much! HABIT!!!!!!!!!!!

i am most appreciative.   was planning on commenting a bit more in near future about the positive help and people on the current forums as opposed to the original ones.....


p.s. when i clicked on apps it just said quit so i tried but never the file manager.

---

### Post by danthonyd on 2018-06-08
Try thr mouse settings.

---

### Post by cheapodonuts on 2018-08-26
I'm using Gnome Flashback and I see a tiny file cabinet in the top left corner of my Home file, that gives me the drop down menu.

---

