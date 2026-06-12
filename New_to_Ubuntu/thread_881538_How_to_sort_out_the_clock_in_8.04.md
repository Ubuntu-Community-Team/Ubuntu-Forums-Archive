---
title: "How to sort out the clock in 8.04"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by NeoEIRE on 2008-08-06
hi,
firstly i must say, i am loving the new ubuntu and finding all the little improvements GREAT!

but its still missing a decent clock for the panel...
the digital black font one is just useless...
with kubuntu, u had a nice anologe clock which isnt here or in ubuntu 7.04.
so i use "Macslow's Cairo-clock" which i love because u can change it in many ways to suit ur tastes... but its a workspace clock...

so where can i get the same thing for the panel? or 
how can i attach it to the panel...? or even, 
make the workspace clock, always run and start up when i start my pc....?

thanks and i must say keep up the great work ubuntu... :guitar:
(i can finally play call of duty:lolflag:)
shane

---

### Post by northern lights on 2008-08-06
Both common docks (cairo-dock, awn) come with a clock plug-in, I think.

Navigate to "System > Administration > Software Sources". Enable all
repositories but 'proposed' and 'backports'.

For cairo-dock, run ```
gksu gedit /etc/apt/source.list
```and append the file by```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```Then add the necessary public key and install cairo-dock via```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install cairo-dock cairo-dock-plug-ins
```

For AWN, run ```
sudo apt-get update && sudo apt-get install avant-window-navigator
```

---

### Post by NeoEIRE on 2008-08-06
> **northern lights said:**
> Both common docks (cairo-dock, awn) come with a clock plug-in, I think.

Navigate to "System > Administration > Software Sources". Enable all
repositories but 'proposed' and 'backports'.

For cairo-dock, run ```
gksu gedit /etc/apt/source.list
```and append the file by```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```Then add the necessary public key and install cairo-dock via```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install cairo-dock cairo-dock-plug-ins
```

For AWN, run ```
sudo apt-get update && sudo apt-get install avant-window-navigator
```



not sure what u mean by apend sourse file... its just blank file? and what does this do? its already installed to?

plus whats AWN?

---

### Post by forger on 2008-08-06
> **NeoEIRE said:**
> 
not sure what u mean by apend sourse file...
He meant edit and add that "deb ..." line inside the /etc/apt/sources.list file
You can do that by executing gedit (gnome text editor) with admin privileges:
```
gksu gedit /etc/apt/sources.list
```

> **NeoEIRE said:**
> 
plus whats AWN?
If you'd check the command they gave, you would see that they're the initials for **A**vant **W**indow **N**avigator :)

---

### Post by NeoEIRE on 2008-08-06
ok thanks, i'll try that


after i append, and added the nessesary public keys and install cairo-dock bits

i got this message... this is the end bit...

Fetched 619kB in 1s (364kB/s)                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cairo-dock


added AWN bit too...


what do i do now... (looked in adding panel window and theres no extra icons, or options)
i admit the AWL is kool looking but its not what i wanted to do? just want a decent usable clock on my panel...

---

### Post by northern lights on 2008-08-06
> **NeoEIRE said:**
> after i append, and added the nessesary public keys and install cairo-dock bits

Fetched 619kB in 1s (364kB/s)                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cairo-dock
Append > Add key > Update > Install --> You must have neglected or failed to execute one step.

As for not wanting a dock:
Didn't quite get you right.
However, something the size of 'Mac Slow's Cairo Clock' (Never used it, seen pictures) in the panel? How's that supposed to work? How large is your panel?

---

### Post by fabounet on 2008-08-06
don't forget to run "sudo apt-get update" after modifying your source.list

by the way it should be possible to do it in Synaptic directly ("add a tierce party" or something like that)

In Cairo-Dock you can even detach the clock applet from the dock, to make it run like the Cairo-Clock, directly on the desktop.
Plus in 1.6.2 you can run many clocks, useful if you have familly in some foreign coutries ;-)

---

### Post by northern lights on 2008-08-06
> **fabounet said:**
> by the way it should be possible to do it in Synaptic directly ("add a tierce party" or something like that)It is true that the cairo repository will appear under 'Third Party Software', yet by default that will only show Canonical's partner repositories.

---

### Post by NeoEIRE on 2008-08-06
> **northern lights said:**
> Append > Add key > Update > Install --> You must have neglected or failed to execute one step.

As for not wanting a dock:
Didn't quite get you right.
However, something the size of 'Mac Slow's Cairo Clock' (Never used it, seen pictures) in the panel? How's that supposed to work? How large is your panel?

u can custom the size to anything but 75x75-100x100 perfect... and there is a similar thing for kubuntu... dont really care if its this cairo thing, that was just an example of what i am looking for, plus i just installed it and it looks better than the standard digital clock(i have a see-through panel so black font annoying in panel as u cant see it)... as long as its an anologe clock with a white face so i can easly read the time...

this system is my tv/entertament/radio on sitting room wall(40" lcd) so as u can guess, it would be handy...

---

### Post by NeoEIRE on 2008-08-06
basically if u have ever seen kubuntu, it comes standard... u can choice what type...

but i cant do that on ubuntu which makes no sense...

---

### Post by NeoEIRE on 2008-08-06
> **fabounet said:**
> don't forget to run "sudo apt-get update" after modifying your source.list

by the way it should be possible to do it in Synaptic directly ("add a tierce party" or something like that)

In Cairo-Dock you can even detach the clock applet from the dock, to make it run like the Cairo-Clock, directly on the desktop.
Plus in 1.6.2 you can run many clocks, useful if you have familly in some foreign coutries ;-)


thats what i mean... i have the clock installed... done all the stuff above but no docking... as im not an ubuntu wiz, can u tell me how u got it to drag to the panel... and even back again... the muti-clock thing will be handy too

---

### Post by northern lights on 2008-08-06
Install cairo-dock as described above.

Add a custom launcher to the panel and let it execut 'cairo-dock'. If you want to use it permanently, add it to "System > Preferences > Sessions > Startup Tab"

---

