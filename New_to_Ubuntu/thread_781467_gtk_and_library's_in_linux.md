---
title: "gtk and library's in linux"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-05-04
Hello forum people,

Please can you advise me of whether or not my understanfing of Linux is correct.

Is it correct to say that the GTK library....is basically

gnomeTkde.............GTK....library's

in other words...when you get most ditro's they already have this library core included....right?......because often the desktop of the distro uses those library's...(say a gnome desktop based distro)

if you further download and install an extra feature.... like the KDE desktop..... then doing so simply calls things from those GTK library's....a kde desktop linking shell of calls...

i understand that there is a...... KDE core library....and a Gnome core library....

i wondered if these CORES are allready wrapped up inside the GTK library's that come ready included in many distro's...

thanks

Vince.

---

### Post by luisromangz on 2008-05-04
GTK stands for Gimp Tool Kit. It is the widget library used to draw buttons and texboxes (entries in GTK terminology) in some applications, like Gimp, Inkscape, Pidging and all of Gnome apps. GTK is a C library, but there are many wrapers gtkmm for C++, pygtk for python, etc.

GTK is currently maintained by the Gnome project, but that doesn't mean that it is just used in Gnome nor in Linux as it is a multiplataform library. For example, you have Windows versions of Pidgin and Gimp, which use GTK for Windows. Also, Xfce uses GTK, and is a different desktop environment from Gnome.

KDE uses its own libraries, which are built on Qt, which is actually more a framework than a library. Qt is written in C++ (and have many wrappers for other languages, too), and doesn't share any code with GTK, so no "cores wrapped inside anything" ;)

Of course, Gnome based distros, like Ubuntu, include GTK because is a requirement for Gnome, and KDE distros, like Kubuntu, include Qt by default because is a requirement for KDE, but both toolkits/frameworks, can exist simultaneously in the same machine, and in fact do in some (at least mine).

---

### Post by vinceUUUU on 2008-05-04
Hello

i see...

my ideas were miles out then....

although it makes sense what you say about distro's and GTK and Qt with KDE

i was just wondering about gnome and KDE in general....basically a lot linux tools seam to always require gnome....

so this in turn means you must have gnome on your system right?

many distros that i download and try don't use gnome desktop....

so would it be correct to say that if i do some apititude commands and install gnome-core and kde-core....then all linux tools that require them will always find them?

or do i actually need to install the proper gnome-desktop (metapackage)...and kde-desktop package ....and also install the core's aswell?

i can boot into various sessions right?....gnome DE...kde DE....maybe fluxbox

thanks

Vince.

---

### Post by SunnyRabbiera on 2008-05-04
you really dont need gnome to use gnome apps, just the base gtk libraries and whatever is needed for said gnome app.
I have used many distros that have used KDE but used gtk apps like synaptic, pidgin, the gimp, etc.
Its very possible to have a hybrid system without installing a full desktop, I know I mix KDE applications with gnome ones but without any real issues.

---

### Post by luisromangz on 2008-05-05
If an app doesn't use the Gnome libs, but just GTK ones, then it isn't a Gnome app. For example, neither Synaptic, Pidgin nor Gimp are Gnome apps, just GTK ones.

---

### Post by vinceUUUU on 2008-05-05
Hell luis,

thankyou for replying...

sorry for labouring this point...

so do most distro's already come with GTK installed?....

sometimes when i find a good linux tool, it often says "required gnome" next to it...

so i guess my best bet is to install both GTK lib and gnome...(not gnome-core or gnome-desktop or anything like that...just install GNOME)

and also install kde...

currently i am trying a good distro called ARCH linux...very fast...

thanks

Vince.

---

