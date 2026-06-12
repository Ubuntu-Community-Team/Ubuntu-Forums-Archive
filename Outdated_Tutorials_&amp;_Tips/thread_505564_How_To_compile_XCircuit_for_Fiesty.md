---
title: "How To compile XCircuit for Fiesty"
date: 2007-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by drlock on 2007-07-20
I was very sad when Ubuntu removed XCircuit from the repositories, because I use XCircuit nearly every day.  So I went looking for some other way to get it installed on my system.  I wanted to publish my results here, so that others who also need XCircuit can continue to use it.

I have not been able to find any good .deb for xcircuit (if anyone finds one please let me know.), so I had to compile it from source.  Here are the steps to compile and install the latest version of XCircuit.  I have tested these steps on a Ubuntu 64 bit machine and an XUbuntu 32bit machine.  Both were recently upgraded to Fiesty

First, you need the general C compiler tools:
```
sudo apt-get install build-essential automake1.9
```
You may already have them installed, but it will not hurt to run the command anyway just to make sure.

Next, XCircuit needs some TCL &TK header/library files to compile
```
sudo apt-get install tcl8.4-dev tk8.4-dev
```
This will also pull in a number of dependencies, which is fine, you need some of them too.

Now, you need the latest XCircuit source code.  You can download it from here: [http://opencircuitdesign.com/xcircuit/](http://opencircuitdesign.com/xcircuit/)
At the time of this writing the latest version was 3.6.109, so I just ran:
```
wget http://opencircuitdesign.com/xcircuit/archive/xcircuit-3.6.109.tgz
```

Now uncompress the archive and change to the new directory:
```
tar -xzf xcircuit-3.6.109.tgz
cd xcircuit-3.6.109 
```

The code first needs to be configured to your system.  On my machine it could not find the TCL libraries so I had to provide the path explicitly.
```
./configure --with-tcl=/usr/lib/tcl8.4/
```
After this runs, scan the output for any warnings or errors.

You should now be ready to compile XCircuit:
```
make
```
Again check the output for any errors.  If there were errors they should be near the end of the output.

Finally, you are ready to install XCircuit:
```
sudo make install
```

That is it, you should now be able to run it:
```
xcircuit
```
and start drawing beautiful schematics.

Once XCircuit is compiled and running, you no longer need all those headers and libraries, if you like, you can remove them:
```
sudo apt-get remove tcl8.4-dev tk8.4-dev
```
```
sudo apt-get autoremove
```
The second command removes all the dependencies that tk8.4-dev pulled in.

Misc. Notes:
[LIST]
[*] There are some good tutorials for learning XCircuit here: [http://opencircuitdesign.com/xcircuit/](http://opencircuitdesign.com/xcircuit/)
It is a rather odd program to learn at first, but once you get the hang of it you can be very productive.
[*] As a bonus HOW TO, the PostScript files that XCircuit produces can easily be converted to PNG's using ImageMagick.
[LIST=1]
[*] Make sure you have it installed
```
sudo apt-get install imagemagick
```
[*] Now you can convert any PostScript file to PNG with:
```
convert -density 150 xcircuit_file.ps tmp.png
```
Where 'xcircuit_file.ps' is the postscript file to produce and 'tmp.png' is the output PNG (if there are multiple pages you will get a set of tmp-0.png, tmp-1.png, etc.)
The '-density 150' argument sets the PNG resolution to 150 dpi, which usually looks decent in print.
[/LIST]
[/LIST]

---

### Post by frodon on 2007-07-23
Don't forget to request a package for gutsy gibbon ;) :
[http://ubuntuforums.org/showthread.php?t=414355](http://ubuntuforums.org/showthread.php?t=414355)

---

### Post by drlock on 2007-07-23
Thanks frodon, I could not find any prior requests for it, so I have added the request: [https://bugs.launchpad.net/ubuntu/+bug/127730](https://bugs.launchpad.net/ubuntu/+bug/127730)

---

