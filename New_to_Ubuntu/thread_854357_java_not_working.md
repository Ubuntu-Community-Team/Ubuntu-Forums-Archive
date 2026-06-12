---
title: "java not working"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by carrarin on 2008-07-09
i dloaded the javasdk right. and installed it. it was a bin file so no problems there. 
but i9 cant seem to be able to use the javac command. if i have a file on the desktop, and maneuver the terminal to the desktop and type 
javac teset.java
all i get is an error sying that the comp cant find the javac command .
what else do i need to do.

i dont have the internet, so sudo apt-get is not an option for me

---

### Post by txcrackers on 2008-07-10
The bin is basically a self-extracting archive that extracts right where you put it - and it does **not** place any of the executables in your $PATH, so there's no way to find "javac"

I would strongly recommend using Synaptic to remove *all* Java references, and then re-installing the sun-java6-* packages. (And you can delete your .bin file and the Java6 directory it created when you un-archived it).

---

### Post by rockerphil on 2008-07-10
here's what i'd do, as stated earlier i'd open up synaptic and COMPLETELY remove ALL Java refferences, once that's done run this in terminal

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-bin

and that will install Java for you, hope this helps,

Phil

----------------
Now playing: [SLIPKNOT - Duality](http://www.foxytunes.com/artist/slipknot/track/duality)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

