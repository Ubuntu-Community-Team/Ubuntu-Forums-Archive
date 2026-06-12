---
title: "Kinda screwed up &gt;.&lt;"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by LeftNut on 2008-10-12
I've been trying to install the compiz-fusion plugins like atlantis and etc. so i read one guide and tried to install compiz-git on hardy but to my dismay i kind of bunked my system. i lost all to tops of my programs with the move/max/close is and lost all my desktop views. i managed to almost reverse this by going through the synaptic manager but i get this error when trying to reinstall fusion: E: fusion-icon: subprocess post-installation script returned error exit status 1

i did uninstall compiz-git and thats the message i get when i try and reinstall fusion. i got the tops back and a 2 desktop cube but it wont apply the 4 sided cube when i add more desktops buy going to the properties of the workspace switcher. if theres a way to get the system back to norm without reinstalling ubuntu it would be great.


Thanks for any help!
Gary

---

### Post by jamesrl on 2008-10-12
When you lost the tops of your programs, you probably just had to get to a terminal (Alt-F2 gnome-terminal) and run 

```
metacity --replace &
```

When you get the error message, does it say anything more detailed when you click on Details in synaptic?  I would guess you need to remove some directories before it can uninstall properly.

---

### Post by earthpigg on 2008-10-12
> **LeftNut said:**
> **i lost all to tops of my programs with the move/max/close is **

did you disable the plugin "window decorations"? that happened to me, and re-enabling that plugin fixed it...

---

### Post by LeftNut on 2008-10-12
> **jamesrl said:**
> When you lost the tops of your programs, you probably just had to get to a terminal (Alt-F2 gnome-terminal) and run 

```
metacity --replace &
```

When you get the error message, does it say anything more detailed when you click on Details in synaptic?  I would guess you need to remove some directories before it can uninstall properly.

i completely uninstalled successful. but when i try and reinstall fusion i get the error stated but now i got 4 desktops and the expo and the cube will not load >.< 

just to clarify for every1 i got the tops of the windows back when i uninstalled compiz-git. now my problem is gettin compiz-fusion to load back into the system.

so if someone could explain to me how to completely remove all of compiz and completely reinstall it i think this might fix the problem =]? or maybe im wrong but i'm really trying to avoid reinstalling hardy because it took me like 3 days to get my desktop to a point were i like it. but if thats wats needed ill just reboot it =\

thanks for the help so far,
Gary

---

### Post by hyper_ch on 2008-10-12
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

