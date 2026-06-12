---
title: "Help me with JavaScript in a simple Firefox extension please."
date: 2011-07-18
forum: Programming Talk
---

### Post by Stochastic on 2011-07-18
I'm trying to create a simple extension for my firefox so that I can simplify a task into one click rather than the current ten or so steps it takes.  I've read a tutorial or two on how to build an extension and now I just need to get the js files written (I could get this done with a bunch of research, but maybe someone out there can throw it down for me).

Essentially, I want the script to look at the source code for the current website, find the string ```
onclick="playSong
``` follow along that same line until the url (ending in .mp3) is found, then download that mp3 to the current downloads directory.

Anyone want to help me out either with a link to the right source code to look into, or with the given js that I need?  Thanks.

---

### Post by cipherboy_loc on 2011-07-18
If you have figured out how to do the downloading of the page, and stored it in a variable, I would recommend using REGEXes to search for the line. Personally, I would take all the output, and split it into an array by lines, then parse all the elements for that text, and store results in another array. Then you can extract the path name(s) from that array (or you could use a single variable and take only the first instance).

EDIT:

If you haven't figured it out, I would look and see if you can download the pages via jquery. I don't know how it would function in a add-on, but I think it won't allow you to download pages for external sites when added to a web site.



Cipherboy

---

### Post by An Sanct on 2011-07-18
[This]("https://addons.mozilla.org/en-US/firefox/addon/highlightall/") might be of interest to you...

---

