---
title: "Synaptic not showing installed packages"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MadNachos on 2011-09-19
Since I upgraded to Oneiric I have noticed that Synaptic does not show all installed packages when filtering. I have checked the filter settings and also removed the Synaptic config files but I cant fix the problem. A good example is a search for 'lame' does not show lame or the lame libs that show up via "dpkg --get-selections | grep lame" in Synaptic. Same for other packages such as Thunderbird. Anyone seen this?

---

### Post by sammiev on 2011-09-19
> **MadNachos said:**
> Since I upgraded to Oneiric I have noticed that Synaptic does not show all installed packages when filtering. I have checked the filter settings and also removed the Synaptic config files but I cant fix the problem. A good example is a search for 'lame' does not show lame or the lame libs that show up via "dpkg --get-selections | grep lame" in Synaptic. Same for other packages such as Thunderbird. Anyone seen this?

Just checked that myself and your correct.

---

### Post by mc4man on 2011-09-20
works fine here - are you using "Description and Name" in search?

---

### Post by MadNachos on 2011-09-20
> **mc4man said:**
> works fine here - are you using "Description and Name" in search?

Using the 'search' button works OK it seems but using the 'quick filter' box does not provide valid results.

---

### Post by seeker5528 on 2011-09-21
> **MadNachos said:**
> Using the 'search' button works OK it seems but using the 'quick filter' box does not provide valid results.

What it shows is relative to what you have selected on the left.

Using 'lame' as an example....

If you have 'status' and 'all' or 'status' and 'installed' selected in the left pane, then using lame in the 'quick filter' box should either display lame and all related apps or only show lame if it is installed and related apps that are installed.

If 'status' and 'installed (manual)' are selected, you would only see lame and/or related apps that you specifically chose to install as opposed to packages that were pulled in when you chose to install something else that had a depends/recommends on them.

Later, Seeker

---

### Post by MadNachos on 2011-09-21
> **seeker5528 said:**
> What it shows is relative to what you have selected on the left.

Using 'lame' as an example....

If you have 'status' and 'all' or 'status' and 'installed' selected in the left pane, then using lame in the 'quick filter' box should either display lame and all related apps or only show lame if it is installed and related apps that are installed.

If 'status' and 'installed (manual)' are selected, you would only see lame and/or related apps that you specifically chose to install as opposed to packages that were pulled in when you chose to install something else that had a depends/recommends on them.

Later, Seeker

Right, but its not doing that. If I select 'status' on the bottom left and 'All' or any of the other options (installed, not installed, etc) 'lame' wont show up using the 'Quick Filter' box, only a search using the 'Search' button provides the proper results.

---

### Post by seeker5528 on 2011-09-21
The only thing I can think of off the top of my head is.....

Do you have apt-xapian-index installed?

EDIT:

If it is installed you might open a terminal and type ```
sudo /usr/share/apt-xapian-index/update-apt-xapian-index-dbus
``` to see if that makes a difference.

Later, Seeker

---

### Post by ClyN3il on 2011-09-26
I've been having this same problem.

Example: "All" is selected on the left. When I type "unity" in the quick filter box, all that appears is firefox-globalmenu. It filters out unity and all the other packages that have "unity" in their package names, even though I can find them by leaving the quick filter box empty and scrolling through the list alphabetically.

Is quick filter now only filtering by package description and not by package name? And if so, why? 

Since running sudo update-apt-xapian-index in an attempt to fix this, I've been getting some apt-xapian-index crashes.

And just now Synaptic crashed while attempting to update.

---

### Post by ventrical on 2011-09-26
All working fine here for now...
Intel Desktop Motherboard/2.66GHz Intel Pentium 4 Dual Core.nVidia GEForce218/512MB/500GBSATA/[COLOR=Blue]Affirmion Vector Analog Generator/[/COLOR]

---

### Post by seeker5528 on 2011-09-26
> **ClyN3il said:**
> Since running sudo update-apt-xapian-index in an attempt to fix this, I've been getting some apt-xapian-index crashes.

And just now Synaptic crashed while attempting to update.

If you still get crashes happening, I would purge and re-install....

```
sudo dpkg --purge --force-depends apt-xapian-index synaptic
sudo apt-get install apt-xapian-index synaptic
```

Later, Seeker

---

