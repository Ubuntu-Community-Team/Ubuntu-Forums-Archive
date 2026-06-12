---
title: "how to organize desktop launchers"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by beew on 2011-10-12
Hi,

It seems that with gnome 3 (not gnome shell, but the underlying DE) the desktop launchers are all over the places. I would like to organize them so that, for example, Synaptic goes to "System" instead of "other" (it seems that most things not installed by default go to "other") The "Main menu" (alarte) doesn't work with gnome 3 anymore apparently. I am wondering if there is a way to do it (there should be something like alarte to do it easily if they want the new ui to be user friendly)


Also ccsm should also appear in the system settings menu like in Natty.

Is there a way to do this? Thanks.

---

### Post by mc4man on 2011-10-12
What session are you using
alacarte does work though only seems useful in the gnome fallback session 
(I guess could be used to create custom launchers in unity* or Gs

---

### Post by beew on 2011-10-12
> **mc4man said:**
> What session are you using
alacarte does work though only seems useful in the gnome fallback session 
(I guess could be used to create custom launchers in unity* or Gs
  Unity 3d. I wouldn't want to use the "fall back" if my hardware can run full 3d unity. 

In GS it didn't work last time I tried.

---

### Post by beew on 2011-10-13
I tried with alacarte. Changing the categories in the Main Menu doesn't always make changes that correspond to the arrangement in the dash. For example, I add synaptic to system tools, and it does show up in system in the dash, but I added the Main Menu and CCSM to system  tools and they don't show up in the system in the dash.

Also, I don't know how to add something to the "system settings" menu (under the user name icon) I think ccsm should be there like in Natty, for example.

Thanks.

---

### Post by mc4man on 2011-10-13
The only use I see for alacarte in unity*/Gs is an alternate way to create custom launchers. Really not of much or any value otherwise.

By default synaptic should be visible in the apps lens > System, is here (screen

As far as ccsm it shows in the app lens > Customization which makes sense.(screen 2

All you are doing with alacarte is creating alacarte-made .desktops in ~/.local/share/applications which will show up in the dash but don't reflect any actual change to the orig. .desktop

I'm not really up on what the dash does to determine 'placement of installed apps, I'd think the Category= line in the .desktop plays a part though I'm not sure altering that after the fact will matter (after an app is installed), though copy a .desktop to ~/.local/share/applications with changes may

ATm the dash seems to do ok with placement though there are certainly some 'oddities' and or inappropriate placements.

---

### Post by beew on 2011-10-13
Thanks for the reply. 

Now is there anyway to put ccsm in the system settings menu?

---

### Post by mc4man on 2011-10-13
> **beew said:**
> Thanks for the reply. 

Now is there anyway to put ccsm in the system settings menu?

Note that I don't particularly use the apps lens for commonly used apps - prefer to create category based launcher icons/quicklists
In this case you could alter by adjusting ccsm.desktop

Change in the Category= line the  Settings to System

---

