---
title: "Recursivly rename folders removing characters as required"
date: 2016-04-17
forum: Programming Talk
---

### Post by peter_brickles on 2016-04-17
HI guys here's hoping some on pout the can help 

I have a large library of epub and mobi file creates some what by calibre.

Output  of tree listing below 

 > 
&#9474;** &#9500;&#9472;&#9472; Paddy Whacked_ The Untold Story of the Irish American Gangster (581)
&#9474;** &#9474;** &#9500;&#9472;&#9472; cover.jpg
&#9474;** &#9474;** &#9500;&#9472;&#9472; metadata.opf
&#9474;** &#9474;** &#9492;&#9472;&#9472; Paddy Whacked_ The Untold Story of the Iri - T. J. English.mobi
&#9474;** &#9492;&#9472;&#9472; The Savage City_ Race, Murder, and a Generation on the Edge (619)
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; metadata.opf
&#9474;**     &#9492;&#9472;&#9472; The Savage City_ Race, Murder, and a Gener - T. J. English.mobi
&#9500;&#9472;&#9472; Tom Philbin
&#9474;** &#9492;&#9472;&#9472; Killer Book of Cold Cases_ Incredible Stories, Facts, and Trivia From the Most Baffling True Cr (570)
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; Killer Book of Cold Cases_ Incredible Stor - Tom Philbin.epub
&#9474;**     &#9500;&#9472;&#9472; Killer Book of Cold Cases_ Incredible Stor - Tom Philbin.mobi
&#9474;**     &#9492;&#9472;&#9472; metadata.opf
&#9500;&#9472;&#9472; Tony Bennett
&#9474;** &#9492;&#9472;&#9472; The Good Life (789)
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; metadata.opf
&#9474;**     &#9500;&#9472;&#9472; The Good Life - Tony Bennett.epub
&#9474;**     &#9492;&#9472;&#9472; The Good Life - Tony Bennett.mobi
&#9500;&#9472;&#9472; Trevor Marriott
&#9474;** &#9492;&#9472;&#9472; The Evil Within - a Top Murder Squad Detective Reveals the Chilling True Stories of the World's (572)
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; metadata.opf
&#9474;**     &#9500;&#9472;&#9472; The Evil Within - a Top Murder Squad Detec - Trevor Marriott.epub
&#9474;**     &#9492;&#9472;&#9472; The Evil Within - a Top Murder Squad Detec - Trevor Marriott.mobi
&#9500;&#9472;&#9472; Troy Denning
&#9474;** &#9500;&#9472;&#9472; Book 1 - A Forest Apart (737)
&#9474;** &#9474;** &#9500;&#9472;&#9472; Book 1 - A Forest Apart - Troy Denning.epub
&#9474;** &#9474;** &#9500;&#9472;&#9472; Book 1 - A Forest Apart - Troy Denning.mobi
&#9474;** &#9474;** &#9500;&#9472;&#9472; cover.jpg



I would like to recursively rename the directories  removing the brackets and numbers 

> 
&#9474;** &#9500;&#9472;&#9472; Paddy Whacked_ The Untold Story of the Irish American Gangster
&#9474;** &#9474;** &#9500;&#9472;&#9472; cover.jpg
&#9474;** &#9474;** &#9500;&#9472;&#9472; metadata.opf
&#9474;** &#9474;** &#9492;&#9472;&#9472; Paddy Whacked_ The Untold Story of the Iri - T. J. English.mobi
&#9474;** &#9492;&#9472;&#9472; The Savage City_ Race, Murder, and a Generation on the Edge
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; metadata.opf
&#9474;**     &#9492;&#9472;&#9472; The Savage City_ Race, Murder, and a Gener - T. J. English.mobi
&#9500;&#9472;&#9472; Tom Philbin
&#9474;** &#9492;&#9472;&#9472; Killer Book of Cold Cases_ Incredible Stories, Facts, and Trivia From the Most Baffling True Cr 
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; Killer Book of Cold Cases_ Incredible Stor - Tom Philbin.epub
&#9474;**     &#9500;&#9472;&#9472; Killer Book of Cold Cases_ Incredible Stor - Tom Philbin.mobi
&#9474;**     &#9492;&#9472;&#9472; metadata.opf
&#9500;&#9472;&#9472; Tony Bennett
&#9474;** &#9492;&#9472;&#9472; The Good Life
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; metadata.opf
&#9474;**     &#9500;&#9472;&#9472; The Good Life - Tony Bennett.epub
&#9474;**     &#9492;&#9472;&#9472; The Good Life - Tony Bennett.mobi
&#9500;&#9472;&#9472; Trevor Marriott
&#9474;** &#9492;&#9472;&#9472; The Evil Within - a Top Murder Squad Detective Reveals the Chilling True Stories of the World's
&#9474;**     &#9500;&#9472;&#9472; cover.jpg
&#9474;**     &#9500;&#9472;&#9472; metadata.opf
&#9474;**     &#9500;&#9472;&#9472; The Evil Within - a Top Murder Squad Detec - Trevor Marriott.epub
&#9474;**     &#9492;&#9472;&#9472; The Evil Within - a Top Murder Squad Detec - Trevor Marriott.mobi
&#9500;&#9472;&#9472; Troy Denning
&#9474;** &#9500;&#9472;&#9472; Book 1 - A Forest Apart
&#9474;** &#9474;** &#9500;&#9472;&#9472; Book 1 - A Forest Apart - Troy Denning.epub
&#9474;** &#9474;** &#9500;&#9472;&#9472; Book 1 - A Forest Apart - Troy Denning.mobi
&#9474;** &#9474;** &#9500;&#9472;&#9472; cover.jpg



I have been scratching my head over this one all day so any help would be gratefully appreciated

---

### Post by peter_brickles on 2016-04-17
solved this on with a little help from another forum if any one ever needs the solution 

> find . -type d -name "*([0-9]*)" | while read FN; do mv "$FN" "${FN%([0-9]*)}"; done

---

### Post by Bucky Ball on 2016-04-17
Thanks for sharing. ;)

It would be even more helpful if you mark the thread as solved. See the first link in my signature at the bottom of this post for how.

---

