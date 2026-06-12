---
title: "Anjuta requirements?"
date: 2005-05-14
forum: Programming Talk
---

### Post by NoTiG on 2005-05-14
Hey.. just wondering if anyone knows... I am just trying to create a project but during the automake ..... First it told me i was missing automake .. so i got automake from synaptic... then it told me i was missing glade! . so i got glade 2.. then it was i was missing "libtool" .. so i got lib tool . Now it quits and says:

intl/Makefile.in' not found
./ABOUT-NLS not found
./intl does not exist
(probably missing development files)

so... im guessing i am missing another package?? does anyone know what package has the appropriate dev files.. ???

---

### Post by NoTiG on 2005-05-14
just an update... I unchecked support for gettext... and that problem went away... even though i checked synaptic and i already have gettext installed....

but on to the next one... now it says

"no package libgnomeui-2.0 found" .. its not in synaptic either.. at least with the repositories i currently have. and it says "perhaps you should add the directory containing libgnomeui-2.0.pc

---

### Post by Dogmeat on 2005-05-14
hello, i installed anjuta yesterday too, here's the packages i got:

```
sudo apt-get install libgnomeui-dev cvs indent ctags devhelp gnome-devel libgtk2.0-dev libgtkmm2.0-dev libgnome2-dev libgnomemm2.0-dev devhelp-books anjuta autogen automake glade-gnome-2 gnome-devel libtool
```

I did the anjuta tutorial and it worked flawlessly (although apparently its for an earlier version) Also it missed a little bit on how to configure the GtkEntry but it's intuitive to do if you configured the buttons.

btw don't try to compile your first gnome project as is, you need to build the GUI first (again, do the tutorial) or you'll get a bunch of errors starting with "can't find <gnome.h>" etc. Let me know if it works for you!  :smile:

---

### Post by NoTiG on 2005-05-14
hey thanks! . i had most of those.. except autogen, ctags, cvs .... but the one that made it all work was libgnomeui-dev . 

I did have one problem though........ everything installed EXCEPT gnome-devel. I ran auto make on the template project program and everything worked... so i guess gnome-devel is not crucial ? but when i try to install it ... it says "broken package.. requires gnome.core.devel" .. which is NOT in synaptic. Is gnome.core.devel necessary ? Would you mind telling me what repository has gnome.core.devel ??? please :P 

THere is also something else... i created a couple of projects and when it failed to automake them.. i closed them. and now they show up .. when i go to "open projects" .. and it says they're in my ~/Projects folder , BUT there is nothing in that folder! . so when i try to open them....... to delete them it doesnt work. its like they are now broken links.

---

### Post by Dogmeat on 2005-05-14
I think apt-get automatically installed gnome-core-devel on my system, you probably didn't add the extra repositories go [here](http://www.ubuntuguide.org/#extrarepositories), follow the instructions and try again! What kind of project are you creating? I only tested the Gnome Project kind so far in C, other kinds may need other packages i haven't tried them yet...

---

### Post by Raven-sb on 2005-05-24
[QUOTE=Dogmeat]I think apt-get automatically installed gnome-core-devel on my system, you probably didn't add the extra repositories go [here]("http://www.ubuntuguide.org/#extrarepositories"), follow the instructions and try again! What kind of project are you creating? I only tested the Gnome Project kind so far in C, other kinds may need other packages i haven't tried them yet...[/QUOTE]

According to other forum posts there is a problem with installing smeg (Gnome Menu Editor) and gnome-devel; in that once you have installed smeg, apt refuses to install gnome-devel and gnome-core-devel.  Unfortunately no one seems to know how to fix this which is really annoying.  I've even tried uninstalling smeg, but come up with error messages that refuse to allow  me to uninstall it. ](*,) 

I'll be keeping a close eye on this as I really want to install anjuta.

*sighs*

Raven

---

### Post by Dogmeat on 2005-05-25
Yes i installed anjuta before smeg, so that must be it..  I installed smeg from from apt-get but didn't like it as i couldn't create my own menu bar (only submenus) and I removed it with apt-get (without erros IIRC). I saw a post recently that said 0.6 was out and it had that ability so I'd like to install it! But I don't wanna break anjuta, so please let me know which version of smeg is problematic, thanks!  ;-)

---

### Post by Raven-sb on 2005-05-25
Hi Dogmeat,

Well it seems that I was mistaken in my last post. It's not that smeg is incompatible with Anjuta, but rather that the liabaries that Anjuta needs (i.e gnome-devel) have been removed from the repositries and replaced with the liabaries that smeg needs.  

I found this out after doing a reinstall of Ubuntu and then attempting to apt-get anjuta. *sighs* So I'm thinking of installing Kbuntu and getting KDevelop, which is not what I wanted to do. ](*,)

On the plus side (there has to be one *smiles*) smeg 0.6 is a very good program, much better then smeg 0.5  Congrats on having a working copy of Anjuta, if I were you I wouldn't touch smeg on the basis that it may cripple Anjuta, but thats just me, YMMV.

Regards,

Raven

---

### Post by jdong on 2005-05-25
> **Raven-sb]According to other forum posts there is a problem with installing smeg (Gnome Menu Editor) and gnome-devel said:**
> (*,) 
 
I'll be keeping a close eye on this as I really want to install anjuta.
 
*sighs*
 
Raven
 
Yeah, this is unfortunately a Smeg problem. Travis (Amaranth) has new versions of libgnome-menu0 (because the ones shipping with Hoary were defunct), but unfortunately they don't work with the Hoary gnome-devel.
 
 
Hopefully, he'll resolve these issues soon.

---

### Post by jdong on 2005-05-25
UPDATE: 
 
[http://ubuntuforums.org/showthread.php?p=187022]("http://ubuntuforums.org/showthread.php?p=187022")
 
See the above thread for a command to remove smeg AND roll back the gnome-menu changes, so gnome-devel will install :)
 
This WILL remove smeg.

---

### Post by Raven-sb on 2005-05-25
Thanks Jdong, this is wonderful news (well for Anjuta users anyway sorry about smeg!)

Raven:-)

---

