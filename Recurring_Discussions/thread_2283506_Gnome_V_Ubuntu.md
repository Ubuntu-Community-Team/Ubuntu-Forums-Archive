---
title: "Gnome V Ubuntu"
date: 2015-06-22
forum: Recurring Discussions
---

### Post by anbu-s on 2015-06-22
I was using Gnome Ubuntu 14.04.02 LTS - thought i'll upgrade to the latest 15.04 and did an upgrade via terminal. After the upgrade it will not login - every time i put my password in it will go blank.

Then I thought i'll try the standard Ubuntu 15.04 - and installed it from scratch and tried it. Within 3 hours, I was longing for the gnome feature paritucaly the window spread and how smooth the operations were with Gnome, like the unity bar etc. - may be its because I'm used to Gnome. Kept the ubuntu for a day but wasn't happy and went back to a fresh install of Gnome 15.04 and then did a full restore from the back up. 

Now i'm back to my beloved Gnome!!
Is it just me or people who use Gnome don't like the standard Ubuntu??

---

### Post by slickymaster on 2015-06-22
Not a support request

*Moved to the ***Recurring Discussions*** sub-forum*

---

### Post by LastDino on 2015-06-22
I've experienced and was introduced to Ubuntu through gnome, but I've no problems with Unity and that is what's my main OS. So...

But everyone has their own preferences.

---

### Post by anbu-s on 2015-06-22
What i was missing it the abiilty to see all opened windows when i move my cursor to the top left corner in Gnome. The hotspots feature in ubuntu does this - but its a hit and miss and every time i reboot the machine it doesn't work, until i go back to tweak tools and disable and enable hotspots again. Also Gnome give you all windows and the opened workspaces in one shot. In general, I feel all standard operations are smoother in gnome

---

### Post by Copper Bezel on 2015-06-24
Yeah, there's a problem on some video cards with Compiz registering hot corners and / or screen edges. I've also had machines that performed better under Gnome and under Unity for similar card compatibility reasons. But generally, I've had the upper left corner set to window spread in Compiz since, like, 2010. I really don't like using Unity without it. 

I do think that Gnome is prettier between the two, but that Unity is more featureful by a fair margin, with the lenses and more complete dock functionality. The things that are configurable, I tend to configure - I don't like the application-based Alt+Tab on either and use workspace-sorted coverflow clones instead. (And it's not like I'm using the default theme, either, so the aesthetic difference is pretty minor for me. I do dislike Ambiance, mostly because the gray toolbars on GTK2 apps look really, really bad against the charcoal (or buttery gold, for Radiance) titlebars.)

---

### Post by monkeybrain20122 on 2015-06-24
> **anbu-s said:**
> What i was missing it the abiilty to see all opened windows when i move my cursor to the top left corner in Gnome. The hotspots feature in ubuntu does this - but its a hit and miss and every time i reboot the machine it doesn't work, until i go back to tweak tools and disable and enable hotspots again. Also Gnome give you all windows and the opened workspaces in one shot. In general, I feel all standard operations are smoother in gnome

Here is a workaround. Make a script called scalefix.sh, for example.

```
#!/bin/bash
#fix scale hot corner
sleep 6
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"Disabled"'
sleep 1
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"TopLeft"'
exit 0
```

Put it somewhere. e.g Create a Scripts folder in your home and put it inside. make it executable (right click, Properties, allow to execute file as program, or chmod +x from terminal) Add it to your Startup Applications. You can adjust the sleep on first line, so if it takes you longer to login to the desktop at start, put something like 10 or 15. Idea is you want to run the script right when you log into the desktop. If it takes a long time between login screen and desktop you have to put something larger to delay running the script.  The effect of the script is basically the same as opening ccsm to disable and then enable the hot corner but it does this automatically at login.

---

### Post by Copper Bezel on 2015-06-24
I actually have other settings like that - for instance, one trackpad setting that refuses to stay set on login, but persists through suspend and the like - that I just made a script for. I made a shortcut to the script in my home folder and run it after logging in. It's a bit of a pain, but not so much as going and setting those things manually or trying to estimate how long to sleep the script when the total login process might take five seconds or thirty depending on whether it's a fresh boot and just what is in memory at the moment.

---

