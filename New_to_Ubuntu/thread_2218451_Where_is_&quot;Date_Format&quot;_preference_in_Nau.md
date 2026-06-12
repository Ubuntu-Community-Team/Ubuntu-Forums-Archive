---
title: "Where is &quot;Date Format&quot; preference in Nautilus 14.04 settings?"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by genejohnson55 on 2014-04-20
Does anyone else hate Nautilus?

I was a Nautilus fan (ubuntu 12.04) until I installed 14.04. Nautilus in 14.04 SUCKS! What the heck has gnome done to their file browser. There used to be a "Date Format" option setting at nautilus > edit > preferences > display = format: 2014-04-20 time. Did gnome remove this? Why?????

Since Nautilus has become a total piece of garbage in 14.04. Is anyone else installing a diff file browser? which one? How do you do this. Is it possible to uninstal the total piece of crap that is Nautilus in 14.04?

Any chance I can make 14.04 nautilus look like the 12.04 nautilus? pics below:


** here's a screenshot of Nautilus in 12.04:**
 [IMG]http://i.imgur.com/waTDf8v.png[/IMG]





** here's a screenshot of Nautilus in 14.04:**
 [IMG]http://i.imgur.com/YcrL35a.png[/IMG]



Now why can I get nautilus to show International Time format in 12.04 but not 14.04? (i'm using same language region in both).

also, why does the date not show in 14.04?

---

### Post by deadflowr on 2014-04-20
Don't care about any of that myself, but if you want an old looky file manager, then maybe look into installing nemo to replace nautilus.
Here's one way
[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

Not the greatest answer, but something anyway.

---

### Post by Paulgirardin on 2014-04-20
Nemo is in the repos now - install via software center

---

### Post by Vaphell on 2014-04-20
> Did gnome remove this? Why?????

no sense in trying to understand the madness. Seriously, it's ridiculous.
according to this
[http://askubuntu.com/questions/149890/how-to-change-the-date-format-in-nautilus-list-columns](http://askubuntu.com/questions/149890/how-to-change-the-date-format-in-nautilus-list-columns)
Nautilus used to have a dconf setting for that (locale/iso/informal). I looked for it in dconf... aaaaaand it's gone, totally. No idea if it's hardcoded now or buried in some obscure configs of nautilus that are not exposed in dconf.

You can change the date format for the ubuntu date indicator in the corner (dconf exposes a custom setting where you can do anything with date beyond the guified defaults) but gnome3 anything = no dice.

---

### Post by genejohnson55 on 2014-04-20
yeah, I'm running a custom date format via dcon-editor for the upper right corner of the top-panel but this custom format does not populate to anything else. What makes matters worse is that I'm using the language region en_DK locale. But all my date formats are still in the stupid American format where they put everything backwards. 

It's def time for a new file browser. nautilus has been ruined. gnome also got rid of a great feature for nautilus: org.gnome.nautilus.preferences.show-advanced-permissions

this was also a great feature. and it is no more.

---

