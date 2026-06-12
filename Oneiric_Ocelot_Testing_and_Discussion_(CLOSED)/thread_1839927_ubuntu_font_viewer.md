---
title: "ubuntu font viewer"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tadcan on 2011-09-06
Tried to install a .ttf font, but get a message saying their is no program to view the file. Google doesn't seem to be a help. Just instructions on how to do a manual install. Installed the restricted package, but that didn't help. What program is used to view fonts?

---

### Post by lucazade on 2011-09-06
> **tadcan said:**
> Tried to install a .ttf font, but get a message saying their is no program to view the file. Google doesn't seem to be a help. Just instructions on how to do a manual install. Installed the restricted package, but that didn't help. What program is used to view fonts?

to install new fonts simply create a folder in your home called .fonts and copy .ttf files inside it.
to view font install gnome-specimen.. don't know if there is anything better, anyway this does the job.

---

### Post by coffeecat on 2011-09-06
This is interesting. I can confirm what the OP is reporting. If I double-click on a ttf file in Oneiric to try to install it, I get a "no application to view this file" message. In Natty and before a window opens up with a preview of the font and an "Install font" button. The name of the app associated with ttf files in Natty is "Font Viewer" but I can't find the name of the package that provides this. Anyone know what this might be? Is this another casualty of the switch to gnome3?

---

### Post by tadcan on 2011-09-06
Thanks. That seems to need a restart to work. Then I noticed the check online, which gives the option of Kfont viewer and font forge. Will give them a go as well.

---

### Post by fjgaude on 2011-09-06
This is the way it is for now: drag any font you wish to install into the .**fonts** file. Simply create it in Home directory if it isn't there. Then after you have installed **Specimen Font Previewer** you can see what that font looks like.

I'm sure as things settle down Oneiric will be at least as good as Natty is, regarding fonts.

Folks like **Font Manager**, but I've not used it much. I did install it along with other font handling software. All good, but I don't use much of these things.

---

### Post by tadcan on 2011-09-06
Set up .fonts folder which worked. Kfont works, font forge crashes and specimen font previewer isn't associated with .ttf and not available in the list of options to open the file.

---

### Post by coffeecat on 2011-09-06
> **coffeecat said:**
>  The name of the app associated with ttf files in Natty is "Font Viewer" but I can't find the name of the package that provides this. Anyone know what this might be? Is this another casualty of the switch to gnome3?

Well, as everyone seems to be focussed on how to install fonts in Oneiric (which is fair enough) rather than wonder why the perfectly good functionality built into Natty has disappeared, I'll have a conversation with myself. :p

If you run "gnome-font-viewer /path/to/filename.ttf" in a terminal in Natty you get the font viewer. But I still can't find out which package this is included in. Running "man gnome-font-viewer" gives "No manual entry for gnome-font-viewer".

**EDIT**: Found it!

[http://packages.ubuntu.com/search?searchon=contents&keywords=gnome-font-viewer&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=gnome-font-viewer&mode=exactfilename&suite=natty&arch=any)

It comes with gnome-control-center. So I guess it's a casualty of the change to gnome 3.

---

### Post by lucazade on 2011-09-06
> **coffeecat said:**
> Well, as everyone seems to be focussed on how to install fonts in Oneiric (which is fair enough) rather than wonder why the perfectly good functionality built into Natty has disappeared, I'll have a conversation with myself. :p

If you run "gnome-font-viewer /path/to/filename.ttf" in a terminal in Natty you get the font viewer. But I still can't find out which package this is included in. Running "man gnome-font-viewer" gives "No manual entry for gnome-font-viewer".

**EDIT**: Found it!

[http://packages.ubuntu.com/search?searchon=contents&keywords=gnome-font-viewer&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=gnome-font-viewer&mode=exactfilename&suite=natty&arch=any)

It comes with gnome-control-center. So I guess it's a casualty of the change to gnome 3.

ah, nice find!
yes, we were focused on manual fixes :) 
far better in a working nautilus with font support.

---

### Post by tadcan on 2011-09-06
Good find, I was presuming, wrongly it seems that the font viewer would come later. Could this be viewed as a bug, feature request?

---

### Post by coffeecat on 2011-09-06
> **tadcan said:**
> Could this be viewed as a bug, feature request?

Yes, and I've made another find.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/839407](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/839407)

I've done a me-too. I haven't tried the workaround suggested there yet - too late here - but perhaps someone else will have by the time I log in again in the morning. :wink:

---

### Post by tadcan on 2011-09-06
Me to'd this as well. I encourage others to do so as well, this should be default for a modern OS.

---

### Post by jbicha on 2011-09-23
This has been fixed now. Just install gnome-font-viewer.

---

### Post by dino99 on 2011-09-23
> **jbicha said:**
> This has been fixed now. Just install gnome-font-viewer.

fixed ? have watched some latest packages upgrades comments talking about gnome-font-viewer included by these packages, but none have installed it: very confusing.

---

### Post by jbicha on 2011-09-23
Ah, it's still not included by default...

Well, it's partially "fixed" then. :-)

---

