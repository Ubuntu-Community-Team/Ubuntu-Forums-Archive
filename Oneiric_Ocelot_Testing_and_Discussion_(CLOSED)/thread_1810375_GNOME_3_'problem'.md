---
title: "GNOME 3 'problem'"
date: 2011-07-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by miasmablk on 2011-07-22
i just installed Gnome 3 /gnome shell on my 11.04 system and i've  encountered a bit of an annoyance. I would like to disable the feature  which shows all shows all open windows in a work space when ever you  hover your mouse over 'activities', i think it's called hot corner? the  only documentation I've found slightly related to this is how to disable  the 'ripple effect' when hovering over the hot corner which isn't what i  want. Is there a setting I've missed in gconf or possibly an extension  for this? my screen resolution is only 1366x768 so keep hitting this by  accident and it's become very annoying I would just like to use the  super key for this function if possible.

---

### Post by cecilpierce on 2011-07-23
I have the same problem with Unity side bar when trying to close a window, very aggravating.

But with G3 I added an extension called acctivitiesbutton I think but you can try others and see which ones you like. 

[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

---

### Post by miasmablk on 2011-07-23
nevermind i've found an extension to correct the problem.

---

### Post by cecilpierce on 2011-07-23
where did you find it, whats it called ?

---

### Post by miasmablk on 2011-07-23
Here's how to turn off the irritating 'hot corner' feature in gnome 3 / shell:


```
cd ~/.local/share/gnome-shell/extensions
``````
mkdir activitieshotspotdisabler@harmus.gmail.com
``````
cd activitieshotspotdisabler@harmus.gmail.com
``````
wget _[https://raw.github.com/hermanus/gnome-shell-extensions/master/Gnome-shell-activities-hotspot-disabler/extension.js](https://raw.github.com/hermanus/gnome-shell-extensions/master/Gnome-shell-activities-hotspot-disabler/extension.js)_
``````
wget _https://raw.github.com/hermanus/gnome-shell-extensions/master/Gnome-shell-activities-hotspot-disabler/metadata.json_
```Press ALT+F2 , type 'r' and press enter.  Gnome Shell will restart and the      hot corner feature will leave you in peace.

---

### Post by MARP1961 on 2011-07-26
I followed these instructions and the extension appears but seems to be switched off. In the Gnome Tweak Tool it is 'greyed out' and cannot be selected.

---

### Post by MARP1961 on 2011-07-26
After a bit more searching I found out this works:
```

```[http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button](http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button)

---

### Post by miasmablk on 2011-07-27
> **MARP1961 said:**
> After a bit more searching I found out this works:
[http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button](http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button)

Strange, as this link provides the same extension. "hermanus hotspot disabler"

---

### Post by MARP1961 on 2011-07-27
Yes, I know it does; but for some reason I can't get this to work. What did work is following advice given on the second answer on the page. Just a quick edit of the file **/usr/share/gnome-shell/js/ui/panel.js**. I know I needed to issue the command **gksudo nautilus** first before I could save changes made to this file. Although I don't fully understand how this all works, the instructions are good and clear and once I found the relevant line was able to make the change. 

Apparently, updates might reverse what I have done. We'll have to wait and see if this fix lasts.

---

