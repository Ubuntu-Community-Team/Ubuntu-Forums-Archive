---
title: "Problems installing Comical 0.8 and Comix"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by erans on 2008-07-08
Hello,

New to the forums and the OS (I've been meaning to try Linux for a long time). I like it so far except I'm getting frustrated trying to install a comic book viewer!

I've installed Comix via the package manager. The problem is the program won't start. I'll get a new entry on my taskbar that reads "Starting Comix," but it'll disappear after a while. 

So I tried the other comic book viewer (Comical). I downloaded the source and tried to make the file and got these errors: 

```
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
../Comical Icons/comical.xpm:262: warning: deprecated conversion from string constant to ‘char*’
ComicalApp.cpp: In member function ‘virtual bool ComicalApp::OnInit()’:
ComicalApp.cpp:63: error: invalid use of incomplete type ‘struct wxIcon’
/usr/include/wx-2.8/wx/gdicmn.h:35: error: forward declaration of ‘struct wxIcon’
make[1]: *** [ComicalApp.o] Error 1
make[1]: Leaving directory `/home/shayan/comical-0.8/src'
make: *** [src/ComicalApp.o] Error 2

```

I'm pretty sure I have all of the required libraries for both of these programs. I just can't figure this out as this is the 9th hour of my Linux experience. 

Any help would be appreciated. If you need me to give more information, I'd be happy to do so. Thanks.

---

### Post by st33med on 2008-07-08
Boy, you are sure getting down and dirty into Linux compiling already!
You will need to get build-essential from the repositories.
```
sudo apt-get install build-essential
```

There also maybe a chance that other packages are needed. Check the Comical installation instructions for what you need.

---

### Post by erans on 2008-07-08
Thanks for the response. I did install the essential packages already (I spent about an hour and a half trying to figure out how to install XMMS, haha). 

Comical lists wxWidgets as a requirement as well as gcc3.3. According to the package manager, I have gcc installed but gcc3.3 is a separate entry underneath and it is not installed, so I'll install it and give it a go (though I'm not sure if this will make a difference) and report back.

---

### Post by erans on 2008-07-08
Installed gcc3.3, no dice. :(

---

### Post by st33med on 2008-07-08
```
sudo apt-get install wx-common
```
That would be my best guess...

---

### Post by erans on 2008-07-08
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wx-common is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Still nothing. :\

Is it possible that I sabotaged myself during my learning process?

---

### Post by dwn99 on 2008-07-09
hey,  I use comix.  It's a good program.

are you trying to open .cbr files (as in .rar)?

do .cbz files work?  (as in .zip)


If it's a rar thing, you have to install rar and unrar.  I think all you have to do is something like: sudo apt-get install rar unrar

Then see if that works.  You don't have to compile from source.  Hope that works.

---

### Post by jamvegan on 2008-07-09
For what it's worth, the errors you posted do not appear to be dependency problems.  They look like problems in the actual source code you are trying to compile.

---

### Post by erans on 2008-07-09
> **dwn99 said:**
> hey,  I use comix.  It's a good program.

are you trying to open .cbr files (as in .rar)?

do .cbz files work?  (as in .zip)


If it's a rar thing, you have to install rar and unrar.  I think all you have to do is something like: sudo apt-get install rar unrar

Then see if that works.  You don't have to compile from source.  Hope that works.

My problem with Comix is that the program won't even start up. :\

It goes to "Starting Comix" and then closes itself after 10 seconds or so. Any idea what this could be? I'm getting the same problem with Ubuntu Chess for some reason.

---

### Post by lamego on 2008-07-09
Please run "comix" from the terminal and check for any error message.

---

### Post by dwn99 on 2008-07-09
> **erans said:**
> My problem with Comix is that the program won't even start up. :\

It goes to "Starting Comix" and then closes itself after 10 seconds or so. Any idea what this could be? I'm getting the same problem with Ubuntu Chess for some reason.


I can't remember for sure, but I feel like I had that problem before, and for some reason, I think it was fixed after I had installed unrar and rar (I just don't remember).  I do agree with your/my previous logic that it should start and open .zip files and fail on .rar files, but maybe it is checking for prerequisites first or something.

Considering you will need rar and unrar whenever you do get any comic reader to open, how about you double check to ensure they are installed?  And see if that helps.  If they are already installed or if that doesn't fix things, then no harm done.
I think the command from terminal is just:
sudo apt-get install rar unrar

---

### Post by erans on 2008-07-09
```
PyGTK version 2.8.0 or higher is required to run Comix.
No version of PyGTK was found on your system.

```

Only python-gtk 2.12 is installed on my system, according to synaptic. :(

---

### Post by 9paros on 2008-07-31
Feeling myself a fool since installed ubuntu; just like a 5 years old at the 8' Math class. How to install an jpegtran executable? Lossless JPEG rotation will not be availiable it shows.

---

### Post by Dr_Willis on 2008-08-05
There does seem to be some issues with Compiling Comical 0.8  - However version 0.7  does compile.

I have not had your issues with the other comic book readers in the repos.

Looking into the .8 issue further. Good luck.
:-\"

---

### Post by pormogo on 2008-08-09
I started using comix a few days ago and I love the flexibility it gives you when reading comics. However something seems to be wrong in that it doesn't correctly read cbr or cbz files. When I open a cbz or cbr file with comix it displays the cover and maybe the first 1-2 images in the cbz/r, but that's it. In order to read the comics I have to unpack the archives, which almost defeasts the point of using the application.

I tried adding various cbr/z's to the library. If I highlight an item added to the library it shows the correct pagecount, however it only displays 1-3 images...

---

### Post by pablokal on 2009-05-15
You can find a solution to install Comical (for me in Hardy at least) here:
[http://ubuntuforums.org/showthread.php?t=759400](http://ubuntuforums.org/showthread.php?t=759400)

Worked for me excellently, no problems with cbr's. [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

