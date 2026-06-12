---
title: "avant-window-navigator"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Carlien on 2008-08-13
Hi

i'm experiencing some problems with my ubuntu system (Ubuntu 7.10)

first of all, my avant-window-navigator acts weird, there are vertical white stripes where the 'show desktop' button and the 'quit' button are supposed to be... does anyone know how to solve this? i already tried to re-install it, but it just won't work...

then i have another problem... sometimes programs such as mozilla, rhythmbox just close out of nowhere... my x server is not even running slow or freezing but these programs just seem to close... 

can anyone help me?

---

### Post by blazercist on 2008-08-13
its because you cant have the applets in the regular panel AND awn, you need to remove the show desktop and quit applets from your panel.

---

### Post by moonbeam on 2008-08-14
> **blazercist said:**
> its because you cant have the applets in the regular panel AND awn, you need to remove the show desktop and quit applets from your panel.

Actually that would not be the case.  The ONLY applet that would apply to is systray applets (there can only be one systray) but no others.

When dealing with white lines I'd suggest starting at the following URL.  Normally it's one of three things in order of likelihood... missing python dependencies, two different version of awn, or a version of core that is incompatible with the installed version of extras.   It's almost certainly the first one though...

[http://wiki.awn-project.org/FAQ#Why_does_my_bar_have_one_or_more_thin.2C_vertical.2C_white_lines_that_extend_beyond_the_dock.3F](http://wiki.awn-project.org/FAQ#Why_does_my_bar_have_one_or_more_thin.2C_vertical.2C_white_lines_that_extend_beyond_the_dock.3F)

---

### Post by vikramaditya on 2008-08-14
If **moonbeam**'s excellent suggestion doesn't get things sorted out, you might consider trying cairo dock.  I personally prefer it to AWN.

---

### Post by petedct on 2008-08-14
> **Carlien said:**
> Hi

i'm experiencing some problems with my ubuntu system (Ubuntu 7.10)

first of all, my avant-window-navigator acts weird, there are vertical white stripes where the 'show desktop' button and the 'quit' button are supposed to be... does anyone know how to solve this? i already tried to re-install it, but it just won't work...

then i have another problem... sometimes programs such as mozilla, rhythmbox just close out of nowhere... my x server is not even running slow or freezing but these programs just seem to close... 

can anyone help me?

I've experienced those white lines too. Frequently after an AWN update. What fixed them was to delete the applet from the dock and then add it back in.

---

### Post by Paqman on 2008-08-14
> **petedct said:**
> What fixed them was to delete the applet from the dock and then add it back in.

Same problem, same solution for me too. Presumably there's a conflict between the stored user data and the updated version of the applet. Smack on the hand for the AWN devs ;)

---

