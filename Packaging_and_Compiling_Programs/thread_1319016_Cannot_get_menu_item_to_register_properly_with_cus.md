---
title: "Cannot get menu item to register properly with custom-built .deb"
date: 2009-11-08
forum: Packaging and Compiling Programs
---

### Post by psyke83 on 2009-11-08
Hey folks,

I'm wondering if anybody can lend some assistance. I recently delved into Python (specifically PyGtk) programming in order to create an interface for my PulseAudio Equalizer (bash) script. I've completed the first version of the GUI, which is perfectly functional (but very hacky ;)). 

This is a basic overview of the components that the Equalizer uses:
[LIST]
[*]pulseaudio-equalizer.sh - bash script that does most of the heavy lifting;
[*]pulseaudio-equalizer.py - Python/PyGtk GUI that interfaces with the bash script;
[*]$SOMEPATH/presets/*.preset - these will be text files containing 15 values corresponding to the 15 LADSPA plugin controls, separated by "\n" newlines (because it was the easiest format to parse in Python with my beginner's understanding). The GUI's "Preset" CombBox will populate itself based on the presets available.
[/LIST]

I have looked at the [PackagingFromScratch]("https://wiki.ubuntu.com/PackagingGuide/Complete#Packaging%20from%20Scratch") guide and it doesn't seem relevant to my needs, since a) it expects a vanilla source to work with, and b) I don't require anything to be compiled (since both of the scripts are interpreted).

With that in mind, I grabbed the debian source of "gufw" (why? Because it's small, and appears to be based on Python as well), took a copy of the debian/ directory and hand-edited all the files to suit my needs.

I'm attaching the results (the packed & unpacked source, and built .deb). Note that the .deb file builds without any problems, installs without problems, and the python script, bash script and presets install and work correctly. The only problem is that the menu item is not registering properly.

Any help would be appreciated :)

P.S. If anyone can suggest a better guide that would more suitable to my needs, I'd also be interested in knowing.

---

### Post by SevenMachines on 2009-11-09
your package installs the .desktop to /usr/share/applications which is the right place.the .desktop file doesnt need to register with anything, it should show up instantly in main menu->sound&video. It shows up fine on gnome here in 9.10 so I'm not sure why its not working for you. not much help but the .desktop file is fine!

---

### Post by psyke83 on 2009-11-09
> **SevenMachines said:**
> your package installs the .desktop to /usr/share/applications which is the right place.the .desktop file doesnt need to register with anything, it should show up instantly in main menu->sound&video. It shows up fine on gnome here in 9.10 so I'm not sure why its not working for you. not much help but the .desktop file is fine!

Do you remember if the menu item showed up immediately after installing the .deb package? Sometimes the menu doesn't update new entries until the gnome-panel process restarts (though that doesn't help in my case).

I don't understand why it's not working here...

---

### Post by SevenMachines on 2009-11-10
yes, the menu entry shows up instantly on install/uninstall here.

---

