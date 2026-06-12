---
title: "pointers on how to make a CL program more GUI"
date: 2008-05-06
forum: Programming Talk
---

### Post by nikopol on 2008-05-06
Though I've used Linux for a decade now, I've never been much of a programmer but the recent issue I've had has made try to grapple a bit more with it.

Here's my problem: I use [unpackmp4](http://www.xmixdrix.com/tools/unpackmp4.html) which is a java CL program.
It's pretty good but a bit of a pain to type in all the files for it do its business. 
eg Java -jar unpackmp4 /where/i/put/filename.avi /elsewhere/outputToThisFilename.avi

What would be the best way to get a drag drop folder on my desktop which will just run the program and automagically create the new files appending it with a new name (say FIXED)? 

Is bash the way forward here? Any pointers as to websites I should be looking at?

(oh and it's not my homework in case you're wondering! :) )

---

### Post by Mickeysofine1972 on 2008-05-06
Well you could write a shell command to runn that command but with all the options included so you only have to write them once. 

Or, you could use a higher level languge to make a gui that will be able to do the file selection and spawn the command in a 'xterm -e command'.

Or you could get the source and build a gui that uses its functions to do that itself!

Thats in order of complexity too. :lolflag:

Mike

---

### Post by nikopol on 2008-05-16
thanks for the input - not so simple then eh? 
I may just put up with the typing all the information each time. I was wondering if it was a simple enough thing to mash up but I think it'll take me a lot longer than the typing :)

---

