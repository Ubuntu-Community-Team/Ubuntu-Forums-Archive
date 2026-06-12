---
title: "No &quot;screen&quot; choice in Desktop &gt; Gnome"
date: 2005-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Rusty Age on 2005-08-04
Hi everyone:

I posted elsewhere that I'm unable to take my display resolution up beyond 640*480 in Ubunto Hoary 5.04. I followed many instructions to include my Horiz and Vert refresh rates in the xorg.conf file. This still doesn't work and I'm still stuck with 640*480. :-? 

I read in another forum that one could try and change the screen resolution by going to Desktop > Gnome > Screen (and I quote the entire message below:)

[INDENT]*Ubuntu is using Gnome so I believe you can fire up the Configuration Editor (gconf-editor in terminal) and browse to "desktop>gnome>screen>default>0" and change the key "resolution" to whatever you want (1024x768 for example)*[/INDENT]

Unfortunately, I don't see the Screen > default > 0 options in my desktop > gnome Config editor. How do I enable this?  ](*,) 

Many thanks for your help.

Regards,
Russel

---

### Post by autocrosser on 2005-08-04
I tried that path & it is not there on my system--I normally edit my xorg.conf directly--It would help if you could post your .conf so we can see what is wrong with it---

Also-have you enabled the extra repositories?  I know that there is a RandR applet available for switch on the fly--shows up in Add to Panel>Display Geometry Switcher  if it is installed. You will most likely need to get your .conf sorted out before you can use  it----

---

### Post by maqi on 2005-08-04
Well, this doesn't look much like a HOW TO to me  [-X  Have a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=22348).

Perhaps repost your question in a HELP forum and include some system information like gfx card make/model, gfx driver, error messages, etc. You might actually get a useful answer. You certainly won't from your question as phrased.

Have a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=24557) to enable the RandR function via your xorg.conf. You should not need to install anything.

You could also try [this page](http://www.ubuntuforums.org/search.php?)  as you are not the first person who's had this problem :-P 

Good luck  :smile:

maqi

---

### Post by Rusty Age on 2005-08-04
Many thanks for your posts, guys, and the links too. Will check them out. Sorry for the wrong post .. but I'm a total novice at Ubuntu - a total of 36 hours, to be precise :-(
Regards
Russel

---

