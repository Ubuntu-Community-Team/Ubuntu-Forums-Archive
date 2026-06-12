---
title: "Setting up the OpenGL GLUT stuff"
date: 2007-01-25
forum: Programming Talk
---

### Post by .alpeffers. on 2007-01-25
Okay, so my prof for my OpenGL class told me to look to his webpage for a how-to for installing the OpenGL libraries.

it was done for Fedora Core 1, and failed on me.

What do i need to set it up, and get it working.

I tried to follow the direcitons that came with the tar'ed files, however no different.

So any and all help would be appreciated.

Thanks.

PS, I think mainly it is a problem with the path, as its a re-occuring error/warning, but idunno, never hadta do anything like this before.

---

### Post by Wybiral on 2007-01-25
Well, in debian you just need the mesagl dev files, and the freeglut dev files. You can get them from synaptic.

What was the error btw?

---

### Post by Grey on 2007-01-25
sudo apt-get install freeglut3-dev build-essential

that command, when entered from the terminal should get you up and running.

---

### Post by .alpeffers. on 2007-01-25
okay I reran the make file... two times now, first time i had the output separated into two files, the errors, and the output, then the second time I combine the two into one file.


unfortunately the text file is too large to post... I'll get em online in a sec though

which would you rather see?

*scuttles away to ftp client*

---

### Post by Grey on 2007-01-25
you can attach files to your posts, you know?  :)  Just click manage attachments at the bottom.

---

### Post by .alpeffers. on 2007-01-25
i would if they didn't have a size limit on the attachments...

[http://people.uleth.ca/~al.peffers/mkmkfiles.imake.output.txt]("http://people.uleth.ca/~al.peffers/mkmkfiles.imake.output.txt")
[http://people.uleth.ca/~al.peffers/mkmkfiles.imake.errors.txt]("http://people.uleth.ca/~al.peffers/mkmkfiles.imake.errors.txt")
[http://people.uleth.ca/~al.peffers/mkmkfiles.imake.combined.txt]("http://people.uleth.ca/~al.peffers/mkmkfiles.imake.combined.txt")

did the apt-get stuff... but i don't think thats all i need...

also i've posted on gamedev's forums...

time to get some sample code to try and see if it compiles...

---

