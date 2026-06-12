---
title: "using python to disply many charts as .png files"
date: 2008-11-07
forum: Programming Talk
---

### Post by glok_twen on 2008-11-07
i am using some python libraries, scipy and pylab, in creating a simple console app that makes a bunch of different graphs. right now i save each plot off to a .png file. it's a fantastically easy to use solution to create all these graphs. 

however, i'm out of ideas on how i might display these dozens of charts in a way that's easy to use. ideally it would be a forms app that would let me click through all different criteria, select a group of the .png's, then page through them. but i've never been good at coding event-based gui stuff. so i'm looking for other ideas that are easier to code.

one thing is to spit them all out to some sort of open office file then be able to page through them. sounds clunky though.

or, spit them out into an html file with links and labels then surf through them. i have to say that even 29 years after learning to code i have _never_ created an html page programmatically so i have no idea how cumbersome it is and how hard to learn.

what do you recommend? what other ideas would you have on how i could do this?

---

### Post by geirha on 2008-11-07
How about putting the png-files in a directory, then pass that directory to an external program for viewing images, like gthumb or f-spot or something?

---

