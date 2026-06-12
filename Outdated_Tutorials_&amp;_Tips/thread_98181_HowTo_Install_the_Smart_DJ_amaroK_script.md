---
title: "HowTo: Install the Smart DJ amaroK script"
date: 2005-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by db0 on 2005-12-02
This is a step-by-step guide for installing the [Smart DJ]](http://www.kde-apps.org/content/show.php?content=31509) script for [amaroK](http://amarok.kde.org) on Ubuntu Breezy 5.10. I'm doing this because installing this script is not as intuitive as the rest and until a more automated process is made I hope to help someone else to use it.

First of all, you'll need to install some packages

Download the latest versions of these programs in your homedir
[LIST]
[*][http://rudd-o.com/wp-content/projects/files/python-extattr/](http://rudd-o.com/wp-content/projects/files/python-extattr/)
[*][http://rudd-o.com/wp-content/projects/files/songanalysis/](http://rudd-o.com/wp-content/projects/files/songanalysis/)
[*][http://rudd-o.com/wp-content/projects/files/python-commandsplus/](http://rudd-o.com/wp-content/projects/files/python-commandsplus/)
[*][http://rudd-o.com/wp-content/projects/files/python-amarok/](http://rudd-o.com/wp-content/projects/files/python-amarok/)
[*][http://rudd-o.com/wp-content/projects/files/python-Observable/](http://rudd-o.com/wp-content/projects/files/python-Observable/)
[/LIST]
Now get some packages you'll need *
```
$ sudo apt-get install python-qt3 python2.4-dev vorbis-tools attr mpg321 binutils gcc make gsl-bin libgsl0-dev libvorbis-dev
```

(* some packages are used when you will process mp3 or ogg. If you don't use this format you may skip that package. mp3: mpg321, ogg: vorbis-tools - libvorbis-dev)
(* make, binutils and gcc are required because you have to compile a package from source. If songanalysis comes in a package in a later time they will not be necessary)


Start installing the packages your downloaded
```

$ tar -xvf python-commandsplus-0.2.3.tar.gz
$ tar -xvf python-extattr-0.1.3.tar.gz
$ tar -xvf songanalysis-0.4.0.tar.gz 
$ tar -xvf python-Observable-0.1.0.tar.gz
$ tar -xvf python-amarok-0.1.0.tar.gz
$ cd python-commandsplus-0.2.3
$ sudo python setup.py install
$ cd ..
$ cd python-extattr-0.1.3
$ sudo python setup.py install
$ cd ..
$ cd python-Observable-0.1.0
$ sudo python setup.py install
$ cd ..
$ cd python-amarok-0.1.0
$ sudo python setup.py install
$ cd ..
$ cd songanalysis-0.4.0 
$ ./configure
$ make
$ sudo make install
$ cd ..
```


If you wish, enable extended attributes on the volume where you store your mp3/ogg files (see the SmartDJ script README)

If you use vorbis files, create a symlink for ogg321. 
```
$ cd /usr/bin/
$ sudo ln -s ogg123 ogg321
```

Now use amaroK's script manager to install the latest Smart DJ script.
Hopefully all is fine and you should be able to start the script.

*Note: *Before running this script I used mp32ogg to encode all my collection into the vorbis format. For some reason the Script would halt on some .mp3 files.

*Disclaimer.* I do not claim that this will work every time and I may have forgotten something because I did this a while ago. If you find something wrong or missing please let me know so that I can update the guide.

*EDIT:* Added some new dependencies and changed the links to the new versions.

*EDIT:* Added the python2.4-dev package to the dependencies since some people needed it.

---

### Post by db0 on 2005-12-05
Added this HowTo to the wiki. [Check it out](https://wiki.ubuntu.com/SmartDJHowTo)

---

### Post by arnieboy on 2005-12-05
aaah.. finally its here :) good job db0!

---

### Post by Caboto on 2005-12-05
[QUOTE=db0][...]
*Note: *Before running this script I used mp32ogg to encode all my collection into the vorbis format. For some reason the Script would halt on some .mp3 files.
[...][/QUOTE]
By "halt" you mean really "halt", do you? I've followed your How-To (btw. you should update the tar/cd commands as well eg. amarok-0.1.0 -> python-amarok-0.1.0 and so on) and was a little astonished, that it took that long for analyzing songs. I've got around 4500 mp3 songs and after 1 hour of nearly 80-100% CPU it has only 100 songs analyzed. :(
Does it really take so long or is something wrong with my installation of SmartDJ/Amarok?

---

### Post by db0 on 2005-12-05
No, it really takes that long. Each song analysis takes about 20-50 secs (it's pretty deep).

When I said it halted I mean it was stuck analyzing one single song for an hour or so.  I could stop the script but as soon as I started it again it stuck on the same song.
In the end had to take those two bad mp3s outside the collection (they wouldn't convert to ogg either).

All in all the analysis took me a few days but now I'm using the prog normally (although it isn't fully integrated with amarok-svn yet).

---

### Post by Caboto on 2005-12-05
Okay. That makes sense. But I gotta ask this last question: "Is it worth the wait?" 
I mean, are the suggestions really good? I can't imagine how a machine could analyze my songs and find similar tracks based on the statistics for me...

---

### Post by db0 on 2005-12-05
I'm still checking things out. Among bugs and crashes I've finally made it work in a pretty stable state and right now I'm trying to tweak the slider in order to bring in suggestions I agree with. I haven't had much luck yet and the documentation of the script is still a bit lacking. 
There are some features within that I still don't know what they do. 
In any case, it's below my expectations but it **is** a step in the right direction

---

### Post by Jakobo.C on 2006-01-03
Thank you for writing this HowTo. When I want to install the smart dj-script, I get the following error.
I've installed all packages you mentioned.

```

jakobo@hinterwelt:~/Desktop/smartDJ/python-commandsplus-0.2.3$ sudo python setup.py install
Password:
running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)
jakobo@hinterwelt:~/Desktop/smartDJ/python-commandsplus-0.2.3$

```

When I looked in the /usr/lib/python2.4/ -folder, I noticed that I've no config-folder in there.
Is there a python-package missing? (Something like a -dev?) If yes, which package does install the needed file(s)?

Would be very thnakfull for help, because I realy would like to give smart dj a try.

Jakobo

---

### Post by db0 on 2006-01-03
I don't think so. As far as I remember, I didn't need to install a -dev package but I may be mistaken. Try reinstalling the python package in case there is some error with your installation. 
I'm at work now and I can't check which packages or version I have install. As soon as I get home I'll let you know

---

### Post by Rev. Nathan on 2006-01-09
I really wish to do this, but those links are not working. If you need hosting, I do have a web site I do not mind hosting them on...

---

### Post by db0 on 2006-01-09
They're not mine. 

It seems the developer changed his site's layout. I've edited my post to reflect this.

---

### Post by Rev. Nathan on 2006-01-10
Rats, I'm getting the same error as Jakobo.C.

Download the .tar.gz stuff, right? We must be missing a package or something.

---

### Post by Rev. Nathan on 2006-01-17
Any help on this?

---

### Post by grte on 2006-02-10
I've also got the same problem as Jakobo.C.

Anyone have any ideas?

---

### Post by db0 on 2006-02-10
Try installing the python2.4-dev package

---

### Post by Rev. Nathan on 2006-02-10
Alright! It installed no problems, and the tutorial simplified the process indeed. Good stuff, thanks! :D

Pretty sick stuff :D

---

### Post by db0 on 2006-02-11
Ok, I'm confused is it good stuff or sick stuff? :P

---

### Post by Rev. Nathan on 2006-02-11
Haven't quite been able to confirm that yet. The script's GUI is pretty gross looking, although that really shouldn't be anything to bitch about. It does use all of your CPU power to update, and it will take all weekend and maybe longer to go through my entire collection (slightly over 40GB?). I'm going to wait to give some more input.

But what I meant to say in my original post, I needed python2.4-dev to install. Went smoothly after that!

---

### Post by SirKillalot on 2006-02-27
thank you, finally it works for me!

---

### Post by yugo on 2006-09-24
Thank you for your how to, but it doesn't work for me.
Here is the error log:
```

amarok: [ScriptManager] Running script: /home/hugo/.kde/share/apps/amarok/scripts/Smart DJ/Smart DJ
amarok: [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok: [CollectionDB] [ERROR!] near "show": syntax error
amarok: [CollectionDB] [ERROR!] on query: show tables;
amarok: [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok: [CollectionDB] [ERROR!] near "show": syntax error
amarok: [CollectionDB] [ERROR!] on query: show tables;
amarok: [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok: [CollectionDB] [ERROR!] table analysis already exists
amarok: [CollectionDB] [ERROR!] on query: CREATE TABLE analysis (  url varchar(255) NOT NULL default '',  volume_diff float default NULL,  freq0 float default NULL,  freq1 float default NULL,  freq2 float default NULL,  freq3 float default NULL,  freq4 float default NULL,  freq5 float default NULL,  freq6 float default NULL,  freq7 float default NULL,  freq8 float default NULL,  freq9 float default NULL,  freq10 float default NULL,  freq11 float default NULL,  freq12 float default NULL,  freq13 float default NULL,  freq14 float default NULL,  freq15 float default NULL,  freq16 float default NULL,  freq17 float default NULL,  freq18 float default NULL,  freq19 float default NULL,  freq20 float default NULL,  freq21 float default NULL,  freq22 float default NULL,  freq23 float default NULL,  freq24 float default NULL,  freq25 float default NULL,  freq26 float default NULL,  freq27 float default NULL,  freq28 float default NULL,  freq29 float default NULL,  bpm float default NULL,  interface_used varchar(4) NOT NULL default '',  PRIMARY KEY  (url) );

```
I could try an other database, but I you have any idea before, it could be fine.
Also, the analyse took only about 10min for 30GB. Was something going wrong?

---

### Post by zodwallop on 2006-09-25
I'm having difficulties getting it to work as well.

I followed the directions in the original post (one of the packages has been updated) and everything seemed to install ok.  Amarok recognized and seemed to install the script without problem.  

But when I try to run the script, my processor goes to 100% for about 10 seconds and then goes back to normal.  The "Configure" option is only available for about a second after I press the "Run" button, then it greys out again.  

Does it create a log anywhere so let me know what kind of problems it's running into?  I haven't been able to dig up very much documentation for the script.  Thanks!

---

### Post by yugo on 2006-10-03
to get a log, just run amarok from bash.

---

### Post by DamianABBA on 2006-12-01
Hello Zodwallop! I'm having that same problem.
Could you solve it?

Thanks.

---

### Post by alphablue52 on 2007-01-31
No solution from me, but some more details on my errors:

Compiling and installing worked without errors, songanalysis works fine from the command line:
```
Analyzing (02) Deep Purple - Black Night.ogg 
 Volume diff: 3.237317 
 Frequencies: 0.156130 0.084804 0.074623 0.061431 0.048010 0.041924 0.039883 0.035930 0.031068 0.027161 0.041972 0.071816 0.047932 0.045936 0.048449 0.048606 0.059992 0.073814 0.116524 0.150012 0.141035 0.131596 0.124738 0.091114 0.081577 0.059915 0.035027 0.023059 0.018136 0.034998 
 BPM: 133.933995 
 Analysis took 12 seconds 
```

Also, SmartDJ scanns files in Amarok and detects the BPM (available from right mouse click > SmartDJ > Edit tempo). But it isn't shown in the Amarok coloum "BPM".
The problem is that "Find tracks similar to selection" doesn't find anything. And if I try to enable AutoDJ, the SmartDJ script crashes. The only way to reanimate it is to delete the file ~/.smartdj.conf.

There are some suspicious lines in the .smartdj.log file:
```
DEBUG:ContextBrowserUpdater: Context browser monitor started 
 DEBUG:amaroK Proxy: tf2bool: 0 <type 'int'> 
 DEBUG:amaroK Proxy: calling DCOP method: amarok.player.dynamicModeStatus() 
 DEBUG:ContextBrowserUpdater: file is not current context browser, ignoring 
 DEBUG:amaroK Proxy: tf2bool: 0 <type 'int'> 
 DEBUG:amaroK Proxy: calling DCOP method: amarok.player.enableRandomMode(False) 
 DEBUG:amaroK Proxy: calling DCOP method: amarok.player.enableDynamicMode(False) 
 DEBUG:SuperDynamicModeMonitor: Aborting because amaroK is unexpectedly gone: DCOP: Unknown method. 
 DEBUG:root: ending user interface 
 DEBUG:PyQt UI: Disabling UI
```

But I have no idea what that means.

I also tried deleting all amarok stuff from ~/.kde and used only one english album with ogg files with the same result.
So the error seams to be in the python scripts and extensions, not with ut8 encoding nor mp3.

I am using Kubuntu 6.10 with KDE 3.5.5, Amarok 1.4.3 and python 2.4.3-11ubuntu3.
SmartDJ (0.6), the python extra stuff and songanalysis (0.4.0) are from the author's website.

Thanks for any help,
AB.

---

### Post by alphablue52 on 2007-01-31
note by:

running amarok from the command line doen't give any information, but SmartDJ has a log file in your home directory called ".smartdj.log" But it has an enormous size, because every file scan seemed to be logged.

Could you please try to delete your .smartdj.conf and see if you get the same results?

---

### Post by alphablue52 on 2007-02-18
Well, I've installed a fresh (K)Ubuntu 6.10 Edgy Edge from CD, did an apt-get upgrade and tried to get SmartDJ working with the same result.

Who got SmartDJ running on Ubuntu Edgy Egde? Could you please post your installed python packages (incl. versions)?

Thanks a lot!

---

### Post by frankhdz on 2009-02-19
Trying to install this in ubuntu 8.10 
When trying to install songanalysis I get this error

configure:2163: error: C compiler cannot create executables
See `config.log' for more details.

Anyone have any suggestions on how to get passed this? Every other step worked perfect except this one.

---

