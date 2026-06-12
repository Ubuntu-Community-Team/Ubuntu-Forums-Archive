---
title: "UML For Gnome"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by aprilmot on 2008-10-12
Hello All,
I am currently looking for a UML Designer Program for ubuntu Gnome .  I have installed BOUML, Project Control and Project Synchro.  I hope these programs are ment for KDE and not gnome.  I am using gnome and wish to continue the same.  When I try to open these programs there are asking to set some environmental variables.  I dont know how to set environmental variables in Ubuntu gnome. I think probably thats only possible in KDE?? Is there any other UML Designer Tool for Gnome.

Thank you in Advance.

---

### Post by Nepherte on 2008-10-12
What environmental variables does he ask for? Can you give the complete (error?) message.

---

### Post by aprilmot on 2008-10-12
> **Nepherte said:**
> What environmental variables does he ask for? Can you give the complete (error?) message.

Please find the error attached.

---

### Post by SeanHodges on 2008-10-12
I'm not familiar with BOUML, and after a quick Google I can't even find Project Control/Project Sychro. If you continue to have trouble with BOUML you might want to try Umbrello, which IMO is a very good cross-platform UML modeller:

[http://uml.sourceforge.net/screen.php](http://uml.sourceforge.net/screen.php)

It's in the repositories, just install it from Synaptic.

---

### Post by bruno_pages on 2008-10-13
Hi,

Bouml is not associated to Kde or Gnome, it uses Qt and is able to run under any Linux, Unix, MacOS X and Windows. I reference packages I know in the [download]("http://bouml.free.fr/download.html") page

you try to use an old release of Bouml, now you don't have to define environment variables like BOUML_ID, all can be defined through the "environment dialog" under Bouml itself

if you really want to use your old release you just have to define the BOUML_ID variable :
[LIST]
[*]to define an environment variable under Linux (t)csh, place the following line in your .cshrc : setenv <var> <value>
[*]to defined an environment under Linux bash, place the following line in your .bashrc : export <var>=<value>
[/LIST]
in this case <var> is BOUML_ID and <value> can be 2 (supposing this value is not already used by an other user working with you)

however I encourage you to use a recent release, for instance the last one. An Ubuntu package is made by [Arakhne]("http://www.arakhne.org/bouml") (also referenced in the [download]("http://bouml.free.fr/download.html") page).

Independently of the use of the Arakhne package you can also 'awake' Ubuntu asking them to upgrade their Bouml packages ;)

Best regards and happy modeling

Bruno

---

### Post by SeanHodges on 2008-10-13
You know you're in good hands when the developer of an application takes the time to register on a forum, just to answer a user in peril :)

EDIT: Next release of Ubuntu (end of this month) will include Bouml 4.4 (which has BOUML_ID fix), for now though you may be better off getting the latest release from upstream as bruno_pages suggested.

---

### Post by leg on 2008-10-13
Just in case you still want to try something else you could look at Gaphor.

---

### Post by pvarney on 2010-10-13
It's an old thread, but I came here and tried all of these.  Ended up finding Dia in the repos, it's the one I stuck with.

---

