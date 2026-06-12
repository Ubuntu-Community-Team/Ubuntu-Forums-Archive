---
title: "Having Trouble Compiling Stuff..."
date: 2005-05-11
forum: Packaging and Compiling Programs
---

### Post by steve k on 2005-05-11
Hi,
wow, so i just switched over to Kubuntu Hoary from poking around in Debian for a year and everything works! its amazing!

but: 

i was trying to compile some programs from source just now and it said that i didn't have a suitable c compiler, which is probably not true, i checked and found that gcc was completely installed so i'm guessing it has something to do with how kubuntu decides who or what gets to use that feature.  this was never a problem for me in debian so i'm not really sure how to go about looking to solve this problem.

any help would be appreciated.

---

### Post by az on 2005-05-11
You probably need to install build-essential.

---

### Post by steve k on 2005-05-11
see,
i just tried that but it asked me to insert my cd (it couldn't do it over the network for some reason) and when i did insert the cd it didn't change the picture at all, for some reason it couldn't recognize it...
is there any way of just getting this package through regular apt-sources?

---

### Post by az on 2005-05-11
Remove the cd from your list of repositories and reload.

Either comment it out with a text editor or use synaptic.

sudo nano /etc/apt/sources.list
CTRL-O to save and CTRL-X to exit.

---

### Post by steve k on 2005-05-11
hey,
it seems to be recieving the files now, it's weird how this was never an issue before...it's never asked for the cd and i've apt-got all kinds of stuff up till now.  

thanks for the help!
now that the ./configure command recognizes the compilers it has decided to encounter an X problem:

it tells me that it can't find the X includes and to check my installation for the relevant paths.

where would i look for those? it needs to know where my X repositories are?  it's running within X so i'm assuming there's no way those things aren't there, unless ubuntu is using K-drive or something...
sorry for seeming so dumb about this stuff, i'm just so thrilled at how easy everything has been so far that it's making me a bit lazy.

---

### Post by az on 2005-05-11
When you compile stuff to go with your precompiled binaries, youneed the headers for the binaries.  They are in the developmental packages:

Ex:

xlibs-dev or libgnome-dev

---

