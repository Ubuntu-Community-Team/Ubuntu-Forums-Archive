---
title: "Installing themes for Pidgin...."
date: 2008-10-27
forum: New to Ubuntu
---

### Post by MrPatton84 on 2008-10-27
Hey everybody, 

I'm struggling to install new themes for Pidgin, which is annoying as I'm sure it should be really easy. 

I read this on the [Lifehacker]("http://lifehacker.com/356291/ten-must+have-plug+ins-to-power-up-pidgin") website...


Theme Pidgin with the GTK Theme Selector or GTK+ Theme Control
Pidgin runs on both Windows and Linux using the GTK graphical environment, so theming Pidgin is as easy as using GTK's built-in theming tools. Here's how it works on Windows.

First, you probably want to find a good-looking theme. A good place to start is at the Gnome Application Themes, where you can browse tons of GTK themes (like this one I'm using).

Found one? Download it and extract the contents to C:\Program Files\Common Files\GTK\2.0\share\themes (there should already be a few themes in there to give you an idea of what the results should look like). Now you just need to fire up the Gnome Theme Selector (it should be in your Start menu) and pick the theme you just installed.

Alternately, you could install the Pidgin GTK+ Theme Control plug-in, which allows you to adjust Pidgin's look directly from Pidgin.


Still no luck. Thanks in advance for everyone's help. 

Chris

---

### Post by fLuX23 on 2009-07-19
Hey how's it going.  I realize its a little late but just in case anyone else stumbles in here looking for the same answer.  In order to change the pidgin theme, you have to specify with a command with the following syntax:


GTK2_RC_FILES=/usr/share/themes/NameOfTheme/gtk-2.0/gtkrc pidgin


Hope this helps, I've only been using Linux for a year so if any of you more experienced users knows an alternative I'd like to know myself. =D

---

