---
title: "install a tar"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by westcoast01 on 2012-03-23
I want to install Seamonkey 2.8 which comes in a tar file. I'm stuck, here is what I did so far:
open terminal and type mkdir seamonkey2.8 .. enter .. type cd seamonkey2.8 .. enter .. now I am supposed to download the tar file into ~/seamonkey2.8$ .. well I'm stuck! Any help will be greatly appreciated. Thanks in advance, West. P.S. yes version 2.6 (?) is in the software center so please do not go there.

---

### Post by jerome1232 on 2012-03-23
First, open the archive (double click it), extract it somewhere, have a looksie inside to see if there is an INSTALL or README file, maybe it's a precombiled binary, maybe there's a deb package in there.

Report back when you know what is inside the archive.



note: Is there a specific reason you need 2.8? Some blazing new feature that's not in 2.6?

---

### Post by jerome1232 on 2012-03-23
I took the liberty of downloading it to have a look myself, it's a precompiled binary, once you have it extracted, simply double-click the executable inside.

---

### Post by ajgreeny on 2012-03-23
> **jerome1232 said:**
> I took the liberty of downloading it to have a look myself, it's a precombiled binary, once you have it extracted, simply double-click the executable inside.
Yes, it is just like all of the tar archives from mozilla, firefox, thunderbird, etc all are of precompiled binary files that just need a double click.

---

### Post by westcoast01 on 2012-03-23
Thanks all for the quick response, yes I have been looking for an exe. for two days but still unable to locate such. Will give it another go.[ATTACH]214827[/ATTACH]

---

### Post by jerome1232 on 2012-03-23
I'm sorry, I didn't explain it well. exe is for windows, the one that says run-mozila.sh (or maybe seamonkey, that looks like a shell script as well), that's a linux shell script, which probably checks a few things and then runs the linux binary file (aka executable) called seamonkey-bin.


in short, double click the .sh file.

edit: if you wanted to make your own launcher for it, use alacarte (not sure if it's installed by default) to create one, then do a search for your new launcher in the dash and drag it out to your launcher. The launch command will be the full path to that shell script (should work)

---

### Post by westcoast01 on 2012-03-24
TY Jerome 1232 for all the help I really appreciate it. End result, I got what I wanted just not sure how. Ended up deleting all and starting all over. This time when I double clicked the Seamonkey file it loaded. My ultimate goal is to find a browser to use with my Yahoo stuff that has an add-on like "no squint" which I use with FF. Thanks again. West.

---

### Post by missmoondog on 2012-03-24
better yet is why doesn't this browser get updated in the repositroy's faster? 

cripe! the next updated version of this thing will be out before it makes it to them, which really sucks as seamonkey is EASILY the best browser for windows and linux!!

not including seamonkey in the repositories just proves how much of a fanboy based distro ubuntu still is!! if it isn't firefox or chrome, you're forced to use some half baked other browser which either doesn't work at all, or you can't install plugins, or constantly crashes! yes, i know there's opera and that's a very close second place to seamonkey, but even at that, you have to figure out how to install the security key to add to software updates, to install!

epiphany could be an excellent browser for linux, but it's development is slower than molasses! it's hardly made any progress since the very first time i tried ubuntu way back on version 5.04!

---

### Post by jerome1232 on 2012-03-24
> **missmoondog said:**
> better yet is why doesn't this browser get updated in the repositroy's faster? 

cripe! the next updated version of this thing will be out before it makes it to them, which really sucks as seamonkey is EASILY the best browser for windows and linux!!

not including seamonkey in the repositories just proves how much of a fanboy based distro ubuntu still is!! if it isn't firefox or chrome, you're forced to use some half baked other browser which either doesn't work at all, or you can't install plugins, or constantly crashes! yes, i know there's opera and that's a very close second place to seamonkey, but even at that, you have to figure out how to install the security key to add to software updates, to install!

epiphany could be an excellent browser for linux, but it's development is slower than molasses! it's hardly made any progress since the very first time i tried ubuntu way back on version 5.04!

Because each version of Ubuntu has a version freeze on it's packages, the only updates provided are security updates that won't change the user experience, at the End of Life each release should ideally function as it did when it was released, no major ui changes etc...

See these links for some more info
[https://wiki.ubuntu.com/UbuntuDevelopment/ReleaseProcess](https://wiki.ubuntu.com/UbuntuDevelopment/ReleaseProcess)
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

