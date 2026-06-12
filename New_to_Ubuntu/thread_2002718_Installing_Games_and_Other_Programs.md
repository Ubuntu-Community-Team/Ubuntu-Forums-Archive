---
title: "Installing Games and Other Programs"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Sequoia Bird on 2012-06-13
I found some open source games on the internet that I want to install. I think both are available in the Ubuntu Software Center, but I don't think either are the latest versions. I can find the latest versions on the internet, I just don't know how to get them onto my computer and running (preferably from the launcher or Dash Home. I have Ubuntu 12.04 64bit on a dell inspiron 1564. 

The first is Minetest. I installed the version from Ubuntu Software Center, but I couldn't connect to any servers which I assume is a result of the older version. 
[http://minetest.net/download.php](http://minetest.net/download.php)

The second is Simutrans. I installed it once before and got it running (I don't remember how I did it though), but I had to navigate to the .exe file to use it, I couldn't figure out how to give it an icon in the launcher. 
[http://www.simutrans.com/paksets.htm](http://www.simutrans.com/paksets.htm)
(I want the pak64.Contrast pakset, which I couldn't figure out how to install)

So, how do I do it? I'm sure this question has been answered thousands of times before, if someone knows of an in-depth tutorial. 

Thanks,
Dylan

---

### Post by mastablasta on 2012-06-13
linux does not use .exe files (though you can run them in Wine).
 
if oyu want to install from internet then you need to use .tar.gz file or .deb file (if the deb file was made for Ubuntu). instructions for tar.gz file instalation are usually found inside the file after you extract it.
 
you can also try to find and then add a PPA of the game's latest version. that should keep it at the latest version via regular software updates.

---

### Post by afixane on 2012-06-13
If the available format is .tar.gz , you need to compile :P
If .deb, just double click, it will open Software centre, and then click install

BTW, everything in software centre isn't the latest version, but "the most stable" version.

---

### Post by Sequoia Bird on 2012-06-13
Alright, thanks for the pointers! I will find a tutorial for compiling the tar.gz files.

---

### Post by Sequoia Bird on 2012-06-13
> octopus@octopus-Inspiron-1564:~$ cd Source
octopus@octopus-Inspiron-1564:~/Source$ ls
simulinux-111-2-2.zip  simupak64-111-2.zip  simutrans
octopus@octopus-Inspiron-1564:~/Source$ cd simutrans
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ls
change_request.txt  font         music               readme.txt  text
config              history.txt  pak                 simutrans   thanks.txt
copyright.txt       license.txt  problem_report.txt  skin
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ./configure
bash: ./configure: No such file or directory
octopus@octopus-Inspiron-1564:~/Source/simutrans$ 
Now what?

They were .zip files instead of .tar.gz files (first two items listed on line 3). I unzipped both of them which created the "simutrans" folder, also in line 3.

---

### Post by Frogs Hair on 2012-06-13
Tar.gz files often include instructions in the form of read me file found when the package is extracted.

---

### Post by drmrgd on 2012-06-13
> **Sequoia Bird said:**
> Now what?

First, it would be better to use the Code tags rather than the Quote tags as the Code tags will format things a little more easy to read.

Next, to be sure you're doing it right, I would consult the readme.txt file that seems to be inside the tarball that you downloaded.  I can't seem to figure out which one you downloaded, and so I can't really tell you exactly how to compile it.  However, there does appear to be a file in there called "config" not "configure", which might be what you want.

---

### Post by Sequoia Bird on 2012-06-13
This is the only relevant information in the readme.txt file in the simutrans folder.

```
The most common error is the attempt to start the program without
installing a graphics set. This is not possible!

*** PLEASE MAKE SURE TO HAVE INSTALLED A PAK-SET TOO! ***

Simutrans cannot start without the graphics in the pak set!


```The "pak" folder that I downloaded says "bash: cd: pak: Permission denied" when I try to open it. 

The other files in the simutrans folder are:
```
change_request.txt  font         music               readme.txt  text
config              history.txt  pak                 simutrans   thanks.txt
copyright.txt       license.txt  problem_report.txt  skin
```Not sure this is what you meant, but I tried this:
```
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ./config
bash: ./config: Is a directory
```

Thanks for the code tip, drmrgd.

---

### Post by drmrgd on 2012-06-13
> **Sequoia Bird said:**
> This is the only relevant information in the readme.txt file in the simutrans folder.

```
The most common error is the attempt to start the program without
installing a graphics set. This is not possible!

*** PLEASE MAKE SURE TO HAVE INSTALLED A PAK-SET TOO! ***

Simutrans cannot start without the graphics in the pak set!


```
The "pak" folder that I downloaded says "bash: cd: pak: Permission denied" when I try to open it. 

The other files in the simutrans folder are:
```
change_request.txt  font         music               readme.txt  text
config              history.txt  pak                 simutrans   thanks.txt
copyright.txt       license.txt  problem_report.txt  skin
```

Not sure this is what you meant, but I tried this:
```
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ./config
bash: ./config: Is a directory
```

OK, I figured out the one you downloaded and checked into it.  It looks like when I unzip the simullinux-111-2-2.zip folder it creates what you posted above.  Then, I downloaded and unzipped simupak64-111-2.zip since the readme said that I need to have 1 pak file installed.  That automatically unzipped into the pak folder that was located in the unzipped simutrans folder, and I too had a permission denied error accessing the folder.  

Inside the simultrans folder is the binary executable file called simutrans.  So, in order to launch the game, there is no need to compile anything.  You simply need to execute the game script by typing 

```
./simutrans
```

Which seems to launch the game fine.  I didn't go any further than that, but it seems like it should work OK from there.

---

### Post by Sequoia Bird on 2012-06-13
Whoa, thanks for checking that out, drmrgd.

I just tried this:
```
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ls
change_request.txt  font         music               readme.txt  text
config              history.txt  pak                 simutrans   thanks.txt
copyright.txt       license.txt  problem_report.txt  skin
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ./simutrans
./simutrans: error while loading shared libraries: libbz2.so.1.0: cannot open shared object file: No such file or directory

```No avail! :(

I'll try it again from step one to see if it'll work. Nope, no luck. I tried a different pak too, same result.

---

### Post by drmrgd on 2012-06-13
> **Sequoia Bird said:**
> Whoa, thanks for checking that out, drmrgd.

I just tried this:
```
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ls
change_request.txt  font         music               readme.txt  text
config              history.txt  pak                 simutrans   thanks.txt
copyright.txt       license.txt  problem_report.txt  skin
octopus@octopus-Inspiron-1564:~/Source/simutrans$ ./simutrans
./simutrans: error while loading shared libraries: libbz2.so.1.0: cannot open shared object file: No such file or directory

```No avail! :(

I'll try it again from step one to see if it'll work. Nope, no luck. I tried a different pak too, same result.

Seems like you're missing the libbz2-1.0 library somehow (it might be related to 64-bit architecture vs 32-bit that I have).  You can first check to see that it's there and is symlinked correctly (I think this sometimes causes problems) by running:

```
locate libbz2.so.1
```

If you don't get a result, then it's not installed on your system, and you can install it by running:

```
sudo apt-get install libbz2-1.0
```

If you do get a result, then change directory to where it points (on my system that's /lib/i386-linux-gnu/) and have a look to see if you see a similar structure:

```
lrwxrwxrwx 1 root root    15 Dec 15 01:09 libbz2.so.1 -> libbz2.so.1.0.4
lrwxrwxrwx 1 root root    15 Dec 15 01:08 libbz2.so.1.0 -> libbz2.so.1.0.4
-rw-r--r-- 1 root root 65996 Dec 15 01:09 libbz2.so.1.0.4

```

Essentially you'll want libbz2.so.1 and libbz2.so.1.0 to point to the latest version of the library.  If it does not, then you'll just need to run:

```
ln -s <target> <link_name>
``` 

I'm not sure the structure you have, so I'm not sure the versions I have are the same as yours and the link I post will be correct.  It might be better if you run:

```
ls -l libbz*
```

in that directory just so we can see what you have going on. But, I believe you want something like:

```
sudo ln -s libbz2.so.1.0.4 libbz2.so.1.0
```

I'm offline for the rest of the night.  Hopefully, this will help and if not someone else might be able to pick it up from here for you.

---

### Post by Sequoia Bird on 2012-06-13
Excellent, thank you. I got Minetest v0.4 working now (it was a .deb, piece of cake), and I'll continue trying to work it out after a break of pixel-mining.

---

### Post by Sequoia Bird on 2012-06-14
I did get a result:

```
octopus@octopus-Inspiron-1564:/lib/x86_64-linux-gnu$ ls -l libbz*
lrwxrwxrwx 1 root root    15 May  3 21:55 libbz2.so.1 -> libbz2.so.1.0.4
lrwxrwxrwx 1 root root    15 May  3 21:55 libbz2.so.1.0 -> libbz2.so.1.0.4
-rw-r--r-- 1 root root 66784 Dec 14 22:11 libbz2.so.1.0.4
```In the list of files, libbz2.so.1 and libbz2.so.1.0 are light blue and bold, while libbz.so.1.0.4 is white. I don't know if that's relevant.

```
octopus@octopus-Inspiron-1564:/lib/x86_64-linux-gnu$ sudo ln -s libbz2.so.1.0.4 libbz2.so.1.0
ln: failed to create symbolic link `libbz2.so.1.0': File exists

```

---

### Post by drmrgd on 2012-06-14
Hmmmm...well, I'll be honest...you have me a little baffled at this point.  It does look like you have the correct library, and it does look like you have the same symbolic links as I do, which help a few programs access the library correctly (i.e. the correct library is libbz2.so.1.0.4, but no matter if the program calls for it by name or by libbz.so.1 or libbz.so.1.0, it'll still use the right one). 

My suspicion is that this might have something to do with 64-bit architecture vs 32-bit, which is what I'm running.  It could be that you need something else to make it work (ia32-libs?), but that's a little outside my knowledge base.  I would have suspected something more like "wrong ELF" type or something as the error if this were the case, but I'm not entirely sure.    

Let's see if anyone has a better suggestion.  You might also post to the simutrans forums as I see they have a few posts on there about similar issues (although they seem to have walked the same path as you and I with better success!).

---

### Post by Sequoia Bird on 2012-06-14
Alright, it's okay. Thanks again for the help!

I can play the older, stable version for now; it's in the Software Centre.

---

