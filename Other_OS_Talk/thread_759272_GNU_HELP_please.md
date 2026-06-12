---
title: "GNU? HELP please"
date: 2008-04-18
forum: Other OS Talk
---

### Post by Thundera on 2008-04-18
So I am making my own distro as you know based from a stripped down version of goBuntu, and on source foorge it said pick a license.

My Understanding is GNU is free software, but not open source, which means people are not allowed to edit it.

Can I do this? Or since its goBuntu or a linux distro or watever do I need to make it GLPL for opensource?


MY MAIN QUESTION IS:
With my Distro I am making from gobuntu can I make it a free closed source? (which i think is GNU)

---

### Post by smartboyathome on 2008-04-18
GNU is very much open source. You would need to choose LGPL to include non-free stuff. Since you live in the U.S., I would be wary what you include, since the patent vendors could come after you for including, ie flashplugin-nonfree or sunjava.

---

### Post by Thundera on 2008-04-18
I will do open source GNU than I guess....

---

### Post by smartboyathome on 2008-04-18
> **Thundera said:**
> I will do open source GNU than I guess....

Do LGPL, not GNU. It is more suited for this, since I read your other post.

---

### Post by Thundera on 2008-04-18
But on Source Forge, it says you must be opensource.

So this is open source and free, so which do I choose, lgpl now?

---

### Post by smartboyathome on 2008-04-18
lgpl is open source, but allows closed source. I wouldn't use SourceForge for your distro, though, since it has a limited file size which won't accomidate the image.

---

### Post by Thundera on 2008-04-18
Well being 13, I have no credit, parents just do not care, and I need to do everything freely, any recommendations?
(And no I am not a nerd, I am a skater, but I am currently injured and have nothing else to do....)

So I am thinking I do Opensource LGPL (Sourcefogre has that option)

---

### Post by smartboyathome on 2008-04-18
You will have to find someone who has a server which will donate space bandwidth to you. Thats my only suggestion, as Sourceforge only works for smaller distros.

---

### Post by Thundera on 2008-04-18
I have one host, which I would get 300gigs space 600gigs bandwidth, should I go with that?
I am really going to need someone more knowledgable about distro's to help me in the future when I am just about ready.

---

### Post by SunnyRabbiera on 2008-04-18
> **smartboyathome said:**
> GNU is very much open source. You would need to choose LGPL to include non-free stuff. Since you live in the U.S., I would be wary what you include, since the patent vendors could come after you for including, ie flashplugin-nonfree or sunjava.

well technically you can redistribute both java and flash with your distro as long as its non profit, heck MP3 support out of the box is fairly legal as long as its not commercial.
But if you did create a commercial distro some of the money made for it will have to go to companies like adobe and such.

---

### Post by Thundera on 2008-04-19
It is totaly free and always will be. So as long as it is always totaly free, GNU is what I should pick?
(I am very newbish, I just want to learn and try my hardest to build this since I have nothing else to do.)
And how do I implement the license in the os itself? Do I just create a folder inside the OS and call it GNU and have the GNU documents in it or what?

---

### Post by SunnyRabbiera on 2008-04-19
Its your choice in the end, however you can still use some stuff for free like Java as there is nothing really restricting it these days as java is becoming more open sourced.
You could also put things like gnash, helix player and even MP3 support out of the box as lately the MP3 license has become more open friendly, there are some countries where its implementation is still shaky but its getting better.

---

### Post by Thundera on 2008-04-19
Than it'll stay GNU. I am done thanks guys.

As for putting the license in how do I do that?

---

### Post by SunnyRabbiera on 2008-04-19
you can just copy it from the official GPL website:
[http://www.gnu.org/licenses/gpl.html]("http://www.gnu.org/licenses/gpl.html")

depending on how open you want it to be the gpl2 might be the better (as the GPL3 has a lot of legal mumbo jumbo)

---

### Post by Thundera on 2008-04-19
I mean once I copy it where do I place it inside of my distro?
Anyways I gotta go, night guys, bye and thanks! Ill check up tommorrow!

---

### Post by smartboyathome on 2008-04-19
The GPL does not allow non-free content, the LGPL does.

---

### Post by schnauzer93 on 2008-04-19
> **Thundera said:**
> I mean once I copy it where do I place it inside of my distro?
Anyways I gotta go, night guys, bye and thanks! Ill check up tommorrow!

Maybe create a text file named "license.txt" and put it in the root directory of the CD?

---

