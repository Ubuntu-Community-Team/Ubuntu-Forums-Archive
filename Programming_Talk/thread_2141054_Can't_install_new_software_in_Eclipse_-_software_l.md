---
title: "Can't install new software in Eclipse - software list empty"
date: 2013-05-01
forum: Programming Talk
---

### Post by YBthebest on 2013-05-01
Hi guys, 
I've got Ubuntu 12.4 first of all.
I'm using Eclipse Indigo 3.7 (but I've had this bug with every Eclipse version tried, which means a lot, and the most recent ones too), and I've got a problem: when I go to "Install new Software" and I select a site from the available sites (whatever site, even "All Available Sites"), nothing happens. Literally. No software appears to be installed. I've found this exact bug pretty much nowhere on the internet or the solutions haven't worked for me.

I really need to install the PDT (php support) for Eclipse.

Thanks a lot.

---

### Post by Warren Hill on 2013-05-01
First you need to tell it what site.  "All Available Sites" means all the sites it knows about, not all sites that exist somewhere.

From the "Help" menu select install new software.  Click Add to add a new site.

The site you want for Indigo is

Indigo Update Site 
[http://download.eclipse.org/releases/indigo/](http://download.eclipse.org/releases/indigo/)

It will think for a bit and download a list of software available on that sitw

Expand "Programming Languages" and you should find PHP Development Tools (PDT) listed

You can now install.

If this fixed your problem don't forget to mark the thread solved.

---

### Post by YBthebest on 2013-05-02
Thanks for your help.

I wasn't clear in my first post. I already have a lot of differents websites in the list, including this one (Indigo Update). And even when I select that one, nothing happens.

I really don't understand.
Thanks again.

---

### Post by lkrnac on 2014-01-29
Same problem here. 
It seems to be some rendering problem, beacause when I click "Select all", "xx items selected" appear next to "Unselect all" button.
Any thoughts? 
This is pretty annoying

---

### Post by lkrnac on 2014-01-29
Problem now solved.
I deleted workspace (.metadata) and created new one

---

