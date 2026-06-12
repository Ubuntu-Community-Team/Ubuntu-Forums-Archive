---
title: "Desktop Switcher Icon Gone..."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Matt86 on 2008-10-26
Hi there,

I'm probably about to ask a very stupid question...

I recently installed Kubuntu 8.10, and while playing around with the taskbar I managed to delete the Icon that displays and allows you to switch between open desktops.

As it's not listed as a widget, I'm finding it quite hard to get it back on the taskbar - any suggestions? I realise there are hotkeys for switching between desktops, but I quite like the graphical mode provided by the icon.

Cheers,
Matt

---

### Post by Amarsingh0793 on 2008-10-26
I'm a gnome user, so my knowledge is quite limited :(. I think you right click on the taskbar, and click add widgets and then select "Pager".

Sorry if I'm wrong :)

---

### Post by drs305 on 2008-10-26
In ubuntu it's called 'Workspace Switcher' and you add it via right clicking the panel and selecting 'Add to Panel'. Are you saying that option isn't currently available to you in Kubuntu?

**Added:** If you use compiz, you might need to check the 'General' settings, Desktop Size tab to make sure you have more than 1 desktop 'horizontal virtual size' set.

Also in metacity (gconf-editor, /apps/metacity ) you might check to see if you have "num_workspaces" set to more than 1.

---

### Post by BDNiner on 2008-10-26
That is why i stopped using kde 4.*. I could not find out how to get the desktop switcher back on the taskbar, there are quite a few widgets that i could not figure out how to readd to the taskbar without a reinstall.

---

### Post by Matt86 on 2008-10-28
OK, I've resolved the issue - in KDE4 the widget is indeed called 'Pager' as Amarsingh0793 said. 

Seems like an odd name for the workspace switcher applet..

Thanks all,
Matt

---

