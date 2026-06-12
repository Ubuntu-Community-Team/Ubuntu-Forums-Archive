---
title: "disk cleanup?"
date: 2008-08-16
forum: Philippine Team
---

### Post by ache109 on 2008-08-16
Guys tulong naman,

pano ba mag disk cleanup dun sa  hard drive ko? nag dlete nako ng files thru synaptic and add/remove programs... nasa mga codec kaya na nainstall ko nasa loob looban kaya ndi sakop ng synaptic?? Kasi last month eh mahigit 20 GB pa ang free space nya ngaun 9 GB nalang. Cairodock at GTK themes lang ang ininstall ko. Ininstall ko rn ung mythtv pero tinanggal ko rin kasi ndi compatible. Dinelete ko narin virtual box ko kasi nd ko naman gamit windows..

Thanks,
Ache109

At kung meron kaung kelangan para malaman ang sanhi just reply to this

t.Y!

---

### Post by loell on 2008-08-16
di mo na yan kailangan. :D

---

### Post by king leoric on 2008-08-16
> **ache109 said:**
> Guys tulong naman,

pano ba mag disk cleanup dun sa  hard drive ko? nag dlete nako ng files thru synaptic and add/remove programs... nasa mga codec kaya na nainstall ko nasa loob looban kaya ndi sakop ng synaptic?? Kasi last month eh mahigit 20 GB pa ang free space nya ngaun 9 GB nalang. Cairodock at GTK themes lang ang ininstall ko. Ininstall ko rn ung mythtv pero tinanggal ko rin kasi ndi compatible. Dinelete ko narin virtual box ko kasi nd ko naman gamit windows..

Thanks,
Ache109

At kung meron kaung kelangan para malaman ang sanhi just reply to this

t.Y!

Try mo this..

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by ch1c0dj on 2008-08-16
Posible na marami ka na na download na updates
Check mo ung laman nito > /var/cache/apt/archives dito kasi mapunpunta ung mga downloaded files na kailangan sa during pag updates o pag iinstall ng package from online sources eh. Pwede mo erase or cd write kung gusto mo gamitin sa pang update/install sa ubuntu offline.

Or baka sa mga program mo na nag create ng temp files, tapos hindi na remove after na i-close na ung program. halos 11G kasi ung biglang na consume sa disk space mo masyado malaki. usual suspect dyan is ung mga apps na kailangan ng malaki memory tulad ng graphics/office apps. check mo sa mga settings ng apps na gamit mo kung nag cre-create ng temp files for faster performance.

(OT: my first 1 hundred post:)

---

### Post by killer_d76 on 2008-08-16
wow.. great info and nice timing!.. i have the issue here, and i'm a bit space concious as well, i have given 60GB partition for Ubuntu out of 80Gig on my laftaf :)and now i have 25GB left!.. looks like it's time to do some clean-up here! ;)

---

### Post by the yawner on 2008-08-17
Clean your /var/cache/apt/archives directory.
> sudo apt-get clean

---

### Post by drboontu on 2008-08-17
Hi,

Run these in a terminal to show the largest 50 files in your user directory.
Use the second one if you have a large directory (much faster).
They will also create a file ~/bigfile.list

$ find . -type f -exec ls -s {} \; | sort -n -r | head -50 | cat -n | tee ~/bigfile.list

$ time find . -type f -print0 | xargs --null du -s | sort -n -r | head -50 | cat -n | tee ~/bigfile.list

Cheers,

---

