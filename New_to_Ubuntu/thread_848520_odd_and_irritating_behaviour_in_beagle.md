---
title: "odd and irritating behaviour in beagle"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-07-03
i recently switched from tracker (which is awful) to beagle (which is great!)

however, i have found some odd and very irritating things that beagle does. I am currently making a cookbook for my school. I have had two lemonade recipes donated for the book. when i search lemonade i get a bunch of recipes which beagle claims to be lemonade, but which quite clearly arent, and have no mention of lemonade in them (image 1).

also, say when i search for Middle East (a chapter with this name) i get what is shown in image 2. The highlighted one is the actual document, although it displays some random extract as the title (this happens very often). The 'NEEDS A REAL TITLE' things are very odd- they are both also chapters, but have not got what is displayed as the title, or anywhere in the text. very confusing and very annoying!

thanks for all your help!

---

### Post by dbera on 2008-07-03
To check how lemonade was matched, run this from a terminal
$ beagle-query --verbose lemonade > results.txt
Then open results.txt, find the entry for the file you are interested in and it will show you where lemonade occurs in the file.

Regarding the weird titles, I think those are automatic document-title set by MS-Office/OpenOffice/Adobe if you haven't set an explicit title. If you have a suggestion, drop by at the beagle IRC channel at [http://embed.mibbit.com/?server=irc.gimp.net&channel=%23dashboard](http://embed.mibbit.com/?server=irc.gimp.net&channel=%23dashboard)

---

### Post by benji.ijneb on 2008-07-03
ah. i've worked out what it is! Beagel displays the 'title' of the document, not the document's actual name.

would there be any way of getting beagle to display the name of the file in stead of it's 'title' (what ever that is) EDIT: the title is what you choose under File; Properties; Description; Title in OOo. Perhaps in word documents this is not always saved properly... 

failing that, is there a script which i could use that would make the title of every document (odt, doc, etc.) the same as it's file name. (I'm new to all this, so i couldn't write anything like that!)

thanks for all you help so far!

---

### Post by dbera on 2008-07-03
I dont know any easy way to change titles of document files. Also I dont think there is any way in beagle-search to display the file name, at least not currently.

---

### Post by benji.ijneb on 2008-07-04
would it not be possible to write some kind of crazy script that would do the trick?

---

### Post by dbera on 2008-07-04
> **benji.ijneb said:**
> would it not be possible to write some kind of crazy script that would do the trick?

Beagle-search - no. odt files ... maybe - you can look around the web and ask odt experts.

---

