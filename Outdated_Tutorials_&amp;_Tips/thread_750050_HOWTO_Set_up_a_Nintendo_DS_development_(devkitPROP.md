---
title: "HOWTO: Set up a Nintendo DS development (devkitPRO/PAlib) environment"
date: 2008-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by louman on 2008-04-09
[b]
[COLOR="Red"]
IMPORTANT: THIS HOWTO IS OUT OF DATE. IT IS BEING KEPT FOR ARCHIVAL PURPOSES ONLY.
[/COLOR]
For the up-to-date howto and script, [click here]("http://lmn.mooo.com/projects/devkitpro-sh").
[/b]



[COLOR="Sienna"]**Special thanks to ndsgr, this HOWTO is adapted from his ([http://blog.dev-scene.com/ndsgr/devkitarm-in-ubuntu-edgy](http://blog.dev-scene.com/ndsgr/devkitarm-in-ubuntu-edgy))**[/COLOR]

**This HOWTO [COLOR="Red"]is[/COLOR] for:**
-Those who want to quickly install the build tools and libraries necessary to begin **Nintendo DS homebrew development**.

**This HOWTO is [COLOR="Red"]not[/COLOR] for:**
-Those who want to quickly install the build tools and libraries necessary to begin **Wii homebrew development**.
-Those who want to learn how to set up a particular IDE for DS development (if you know of any such guide, please let me know about it!).

While there are a few decent guides for developing DS homebrew software with Linux out there, few make the installation process simple so you can just get to the fun stuff. I've written a script and this short HOWTO to get you started quickly.

The script will download and install the following into a directory called "devkitpro" in your home directory:
[LIST]
[*][devkitARM, libnds, libfat and dswifi](http://www.devkitpro.org/)
[*][PAlib](http://www.palib-dev.com/)
[*][NO$GBA](http://nocash.emubase.de/gba.htm)
[*][uLibrary](http://brunni.dev-fr.org/index.php?page=ndssoft_ulib)
[/LIST]

With the use of my script, the installation process should be relatively painless. Emphasis on *should*.
When it isn't, please report the errors/problems/annoyances to me via email (see the top of attached script for my email address).
The script generates a log file with the name "devkitpro-install.log" in the current directory; please send me this file if you encounter any problems.

**Requirements**
Some packages you may not already have will be required (let me know if you discover that I'm missing something):
```
$ sudo apt-get update
$ sudo apt-get install wine p7zip unzip unrar
```
--

**If you are updating or reinstalling devkitpro, I would recommend uninstalling before following these steps.**

1) Download the attached script and make sure you can execute it:
```
$ chmod a+x devkitpro.sh
```

2) Run the script:
```
$ ./devkitpro.sh
```
If the script completes without any issues, you will see this text, followed by several other lines:
```

-> devkitPRO installed successfully!

```
Again, in the event that this fails, email me the file "devkitpro-install.log" and a description of what happened, if possible.

3) Back up your original ~/.bashrc file:
```
$ cp ~/.bashrc ~/.bashrc.backup
```

4) As the script will tell you once it has finished, add the lines to the end of your .bashrc file (be sure to back it up first):
(**NOTE**: if you modify the script because you want to install the files somewhere other than ~/devkitpro, you should copy the lines from the script's output. Otherwise, the following default lines will suffice.)
```
export DEVKITPRO=/home/louman/devkitpro **# change this to reflect your home directory**
export DEVKITARM=$DEVKITPRO/devkitARM
export PAPATH=$DEVKITPRO/PAlib/lib
export NOCASHGBA=$DEVKITPRO/nocashgba
alias nds="wine $NOCASHGBA/NO\\\$GBA.EXE"
```

5) Load these new settings like so:
```
$ source ~/.bashrc
```

6) Compile an example DS program and run it with the emulator to see if everything is set up properly:
```
$ cd $DEVKITPRO/uLibrary/Examples/Example06
$ make
$ nds Example06.nds
```

**That's it!** Now look through some of the libnds, uLibrary, and PAlib examples, and read some tutorials:
[b][LIST]
[*]$DEVKITPRO/libnds/examples
[*]$DEVKITPRO/uLibrary/Examples
[*]$DEVKITPRO/PAlib/examples
[*][http://www.dev-scene.com/NDS/Tutorials](http://www.dev-scene.com/NDS/Tutorials)
[*][http://palib-dev.com/wiki/doku.php](http://palib-dev.com/wiki/doku.php)
[*]**Google is your friend ;)**
[/LIST][/b]

**[COLOR="Red"]To Uninstall[/COLOR]**
1) Remove the devkitPRO directory:
```
$ rm -r $DEVKITPRO
```

2) Clean up downloaded files:
```
$ rm -r ~/.devkitpro_cache
```

3) **(Optional)** Recover your original ~/.bashrc file
```
$ cp ~/.bashrc.backup ~/.bashrc
```

---

### Post by GumbyX on 2008-05-26
Its nice to see someone post a how-to for NDS development. One problem though: The script file you listed ends at a dead link. Any way you can fix it, or just list the contents/steps the script takes?

---

### Post by louman on 2008-06-01
Bah! I should have known. Sorry about that!
The link is fixed (I moved home from school for the summer).
I appreciate any feedback.

---

### Post by koepkeb on 2008-06-06
That was a great howto for a beginner (like me). 

One thing that I noticed..in gutsy gibbon's synaptic I had 2 choices for 7zr (I hadn't had it installed yet) one ended with '.full' and the other not.  Installing the non '.full' worked (either that or having both installed).

Thank you for your work!

---

### Post by louman on 2008-06-06
Thanks for the feedback; I've updated the guide accordingly.

---

### Post by Skatertjah on 2008-06-22
Thanks a lot for the installing guide, it helped me out a lot since I've been looking for something like this for ages.

Just one question: What do you use for gfx and sfx? I've tried using the linux PAGfx and Audacity but I couldn't get the right results with either of them.
Thanks in advance.

---

### Post by louman on 2008-07-12
Regarding graphics/sound:
I actually haven't had much time to play with these tools, ironically. Try looking at some examples (located in $DEVKITPRO/libnds/examples, $DEVKITPRO/PAlibExamples and $DEVKITPRO/uLibrary/Examples) and open their data with the Gimp/Audacity to see the details of their format so you can save your files as that particular format later on.

---

### Post by Abras on 2008-07-21
Thanks, it worked great! And yes, it does work on hardy (you said it probably would but I just wanted to confirm it) 

It's obvious to me that a good deal of care went into writing this guide so great work. I wish the internet was full of guides as helpful as this one.

btw, one little hiccup. The script installed no$gba in ~/devkitpro/**nocashgba/** which caused an error when I tried to run the sample program. So all I did was change the directory's name to "no**$**gba." It's silly, but you may want to look into it.

OK, time for some fun...

---

### Post by louman on 2008-07-24
Again, thanks for the feedback; I appreciate your appreciation!

Yes, I changed it to "nocashgba" the last time I updated the script because there were a few problems outputting the proper escaped path name at the end of the script.
I've updated the guide accordingly. :)

Tonight after work I'll probably be updating the script to include the latest versions of all the software packages it installs; chances are there are some updates by now.

---

### Post by randomusername on 2008-07-26
Thanks for this, I just picked up a DS & have been looking forward to messing around writing some code for it. :)

One thing though - the install script requires unrar along with 7zr and unzip, but it is not listed in your instructions.

---

### Post by schmede on 2008-08-10
thank you so much!
works really fine, though i had to go back to ubuntu gutsy to make it work. (had hardy on my disk before and had several other issues with it)

---

### Post by plumbium on 2008-08-12
Thanks!  It worked great.  This is nice because I was having trouble setting up devkitARM and PAlib on linux, which was one of the few things that I still use windows for.

---

### Post by bloeper on 2008-08-13
i tried to run the script on Ubuntu 8.04 but i get some errors.. To name them:
[php]
./devkitpro.sh: line 162: $LOGFILE: ambiguous redirect
mkdir: cannot create directory `/home/tom/devkitpro/libnds/include/ulib': No such file or directory
./devkitpro.sh: line 44: $LOGFILE: ambiguous redirect
->ERROR: Could not create directory: /home/tom/devkitpro/libnds/include/ulib
[/php]
The complete output of the script:
[PHP]
./devkitpro.sh: line 100: $LOGFILE: ambiguous redirect

./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> Building directory tree...
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/.devkitpro_cache: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro/libnds: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro/libnds/examples: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro/nocashgba: directory already exists.
./devkitpro.sh: line 115: $LOGFILE: ambiguous redirect

./devkitpro.sh: line 118: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> Downloading files...
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: devkitARM_r23-i686-linux.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: PALib_CommunityUpdate_BETA-080203.7z
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: libnds-20071023.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: nds-examples-20080427.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: uLibrary.rar
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: libfat-nds-20070127.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: dswifi-0.3.4.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: no$gba-w.zip

./devkitpro.sh: line 130: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> Extracting archives...
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...devkitARM
./devkitpro.sh: line 134: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...PAlib
./devkitpro.sh: line 138: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...libnds
./devkitpro.sh: line 142: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...libnds_examples
./devkitpro.sh: line 146: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...libfat
./devkitpro.sh: line 150: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...dswifi
./devkitpro.sh: line 154: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...NO$GBA
./devkitpro.sh: line 158: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...uLibrary
./devkitpro.sh: line 162: $LOGFILE: ambiguous redirect
mkdir: cannot create directory `/home/tom/devkitpro/libnds/include/ulib': No such file or directory
./devkitpro.sh: line 44: $LOGFILE: ambiguous redirect
->ERROR: Could not create directory: /home/tom/devkitpro/libnds/include/ulib

[/PHP]

but i can't find the error, hope that somebody can help me.

Greetings,

Tom

---

### Post by booyaadotorg on 2008-08-17
gah 3rd attempt to lavish praise on you mate! this script worked a charm! thanks again!

---

### Post by zine92 on 2008-12-29
i did not have a .bashrc even though i am using a bash shell.

---

### Post by edhaker13 on 2009-03-25
> **bloeper said:**
> i tried to run the script on Ubuntu 8.04 but i get some errors.. To name them:
[php]
./devkitpro.sh: line 162: $LOGFILE: ambiguous redirect
mkdir: cannot create directory `/home/tom/devkitpro/libnds/include/ulib': No such file or directory
./devkitpro.sh: line 44: $LOGFILE: ambiguous redirect
->ERROR: Could not create directory: /home/tom/devkitpro/libnds/include/ulib
[/php]
The complete output of the script:
[PHP]
./devkitpro.sh: line 100: $LOGFILE: ambiguous redirect

./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> Building directory tree...
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/.devkitpro_cache: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro/libnds: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro/libnds/examples: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro: directory already exists.
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> /home/tom/devkitpro/nocashgba: directory already exists.
./devkitpro.sh: line 115: $LOGFILE: ambiguous redirect

./devkitpro.sh: line 118: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> Downloading files...
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: devkitARM_r23-i686-linux.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: PALib_CommunityUpdate_BETA-080203.7z
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: libnds-20071023.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: nds-examples-20080427.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: uLibrary.rar
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: libfat-nds-20070127.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: dswifi-0.3.4.tar.bz2
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> File already exists, not downloading: no$gba-w.zip

./devkitpro.sh: line 130: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> Extracting archives...
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...devkitARM
./devkitpro.sh: line 134: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...PAlib
./devkitpro.sh: line 138: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...libnds
./devkitpro.sh: line 142: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...libnds_examples
./devkitpro.sh: line 146: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...libfat
./devkitpro.sh: line 150: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...dswifi
./devkitpro.sh: line 154: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...NO$GBA
./devkitpro.sh: line 158: $LOGFILE: ambiguous redirect
./devkitpro.sh: line 36: $LOGFILE: ambiguous redirect
-> ...uLibrary
./devkitpro.sh: line 162: $LOGFILE: ambiguous redirect
mkdir: cannot create directory `/home/tom/devkitpro/libnds/include/ulib': No such file or directory
./devkitpro.sh: line 44: $LOGFILE: ambiguous redirect
->ERROR: Could not create directory: /home/tom/devkitpro/libnds/include/ulib

[/PHP]

but i can't find the error, hope that somebody can help me.

Greetings,

Tom
I had a similar problem its said this ```
cp: no se puede efectuar `stat' sobre «/home/edhaker13/devkitpro/uLibrary/Install/*h»: No existe el fichero ó directorio
```
which is that the dir doesnt exst i look it a bit and the problem is the file ulibrary.rar doesnt exist anymore so it doesnt unrar it what i did was find the in in the terminal and paste it in my browser it redirectd me saying the file doesnt exist similar file ulibrary-1.12.**7z**,download and unzip in devkitpro removing -1.12 from the name and run the script again.hope is what you need
P.D:you should change this in the script
P.D2:i made the changes in the script if anyone wants it :KS

---

### Post by SigmaSanti on 2009-04-15
I have the same problem, but the new file provided is identical to the old one.

---

### Post by blueminder on 2010-01-25
I hate to resurrect dead threads, but I figure I would update this with an updated script for those who are still interested in NDS/GBA development.

I just changed the script for it to download the newest versions of the software and placed it all in a .dev directory in your home so that way it's out of the way.

I tested this on my Debian Squeeze system, though it should work just fine no matter what you use.

---

### Post by RBTR on 2010-01-26
Wow. What luck. I was actually in the middle of editing the script to do that. Thanks a lot.

*goes to look at script*

---

### Post by SigmaSanti on 2010-01-26
Haven't looked at the script, but thanks.

---

### Post by ButaneMage on 2010-05-03
I have updated the script to work for me on 10.04.  Updated script is attached.

Edit: Actually doesn't work with uLibrary :\ Or PAlib for that matter.  Hmmm I did have this working at one time...

---

### Post by SigmaSanti on 2010-05-03
Beautiful, it works perfectly for libnds, and is better than the original. Just note that it puts devkitpro in the .dev directory. Thanks for updating the script, you saved me a lot of time searching for files across the Internet.

---

### Post by seanpd on 2010-05-27
=d>

---

### Post by louman on 2010-06-01
> **ButaneMage said:**
> I have updated the script to work for me on 10.04.  Updated script is attached.

Edit: Actually doesn't work with uLibrary :\ Or PAlib for that matter.  Hmmm I did have this working at one time...

Thanks for those intermittent updates while I disappeared from the forums for a while.

Anyway, I've done another big update to the original script (which can be grabbed from the original post now) that fix all the issues with PAlib and uLibrary that were present when you made that edit.

I don't check the forums here much anymore since I've moved to ArchLinux, so if you have any issues please email me. (My email address is included at the top of the script.)

---

### Post by aczid on 2011-02-14
I've updated the script again to use all the latest versions and added maxmod and libfilesystem.

You can find the script here [https://gist.github.com/825995](https://gist.github.com/825995)

---

