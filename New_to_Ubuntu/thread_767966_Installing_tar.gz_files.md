---
title: "Installing tar.gz files"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by fullmetalgerbil on 2008-04-26
I'm trying to install Swiftweasel, but it no longer comes as a .deb-now its only available (to my knowledge) as a tar.gz file. Problem is, I have no idea how to install tar.gz files.
Any help would be much appreciated. I know by now I should know how to unpack and install tarballs, but so far I've only installed stuff via synaptic and in .deb form.

---

### Post by warbread on 2008-04-26
Extract the tar.gz file into your /home directory.  Go into terminal and 

```
:-$ cd /home/yourname/swiftfox
```

Hit 'tab' while your typing 'swiftfox' to make sure you get into the right directory.  If there's no .deb in there, you probably have to compile it yourself.  

```

:-$ ./configure
:-$ make
:-$ sudo make install

```

There may be more specific instructions in the README file.  Check through that.  This should be all you need to do, though.

---

### Post by fullmetalgerbil on 2008-04-26
It absolutely did not work. bash did not recognize ./configure among other commands you listed.
Pleeze, somebody just tell me how to install a tar.gz file.

---

### Post by Joeb454 on 2008-04-26
From a terminal run ```
sudo aptitude install build-essential
```

Hope that helps

And we are trying to help yo, please try to be patient :)

---

### Post by eeeandrew on 2008-04-26
Download the file onto your desktop type.

> cd Desktop
then
> tar -zxf swiftweasel.tar.gz
where swiftweasel is the name of the package folder.

next do 
> cd swiftweazel
where swiftweasel is the name of the folder that was created in the last step.

next

> ./configure
make
sudo make install

if theres any errors during this process post them here and we'll show you how to get round them. 

Hope this helps,
Andrew

---

### Post by Meskarune on 2008-04-26
You might have to also install a C compiler. Look up gcc in synaptic and install those packages. :)

---

### Post by Joeb454 on 2008-04-26
They are all included in the build-essential package I mentioned above :)

---

### Post by fullmetalgerbil on 2008-04-26
this is as far as it got
david@david-desktop:~$ cd Desktop
david@david-desktop:~/Desktop$ tar -zxf swiftweasel.tar.gz
tar: swiftweasel.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
david@david-desktop:~/Desktop$ tar -zxf swiftweasel-2.0.0.14_04-17-08_pentium-3.tar.gz
david@david-desktop:~/Desktop$ cd swiftweasel-2.0.0.14_04-17-08_pentium-3.tar.gz
bash: cd: swiftweasel-2.0.0.14_04-17-08_pentium-3.tar.gz: Not a directory
david@david-desktop:~/Desktop$

---

### Post by Joeb454 on 2008-04-26
can you run ```
ls
``` it should tell you what files/folders are in the current directory.

Note that is a lowercase 'L' :)

---

### Post by fullmetalgerbil on 2008-04-26
ls brings up this:
david@david-desktop:~/Desktop$ ls
swiftweasel  swiftweasel-2.0.0.14_04-17-08_pentium-3.tar.gz
david@david-desktop:~/Desktop$ 
I dont know, I installed that build essential package you recommended. I'm probably typing a command wrong or something?

---

### Post by eeeandrew on 2008-04-26
do
> cd Desktop

then

> ls

that should let us see what the correct name to put into the tar command is.

---

### Post by Joeb454 on 2008-04-26
Ok from your last post I see you should get into the directory with ```
cd swiftweasel
```

---

### Post by fullmetalgerbil on 2008-04-26
I think I was already in the Desktop directory, but I typed cd Desktop and got:
david@david-desktop:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory
david@david-desktop:~/Desktop$

---

### Post by eeeandrew on 2008-04-26
ok if I@m reading that output right then it should be

> tar -zxf swiftweasel-2.0.0.14_04-17-08_pentium-3.tar.gz

then 

> cd 

with the name of the folder that was created by the last command.

then > ./configure
make
sudo make install

and yes it was. Apologies, I ended up repeating what someone else had already said to do

---

### Post by fullmetalgerbil on 2008-04-26
Ignore my last post, I just got into the right directorydavid@david-desktop:~/Desktop$ cd swiftweasel
david@david-desktop:~/Desktop/swiftweasel$

---

### Post by Joeb454 on 2008-04-26
ok now try the ./configure etc. :) You may need to install some packages for it to finally complete, but we'll get to that eventually :)

---

### Post by fullmetalgerbil on 2008-04-26
This is as far as I got
david@david-desktop:~/Desktop/swiftweasel$ tar -zxf swiftweasel-2.0.0.14_04-17-08_pentium-3.tar.gz 
tar: swiftweasel-2.0.0.14_04-17-08_pentium-3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
david@david-desktop:~/Desktop/swiftweasel$

---

### Post by eeeandrew on 2008-04-26
you need to run the tar command from the directory the folder your trying to unpackage is in. Not from within the folder itself. in other words. return to the desktop directory and run tar.

---

### Post by Joeb454 on 2008-04-26
You don't need to run the tar commands now, you have already done that successfully (congrats ;)) now you will want to run ```
./configure
``` and post back the last few lines of that if it returns an error :)

---

### Post by kansasnoob on 2008-04-26
This is something that also puzzles me to no end.

Can someone point out a "guide for dummies" like me to understand building from targz and/or rpm?

I'd love to get XnView installed properly but I always mess things up.

---

### Post by eeeandrew on 2008-04-26
apologies. Joeb is right. I thought u were still trying to tar it.

---

### Post by fullmetalgerbil on 2008-04-26
This is what I get when trying to run ./configure
david@david-desktop:~/Desktop/swiftweasel$ ./configure
bash: ./configure: No such file or directory
david@david-desktop:~/Desktop/swiftweasel$

---

### Post by Joeb454 on 2008-04-26
:lolflag:

And @kansasnoob, installing from .tar.* files is actually compiling source, and there's no definitive guide for doing it, because you need to install the dependencies.

---

### Post by Joeb454 on 2008-04-26
Ok, it could be similar to the firefox.tar.gz file, try just doing ```
ls
``` again.

If there is a file simply titled "Swiftweasel" without quotes of course, then run ```
./swiftweasel
```

---

### Post by fullmetalgerbil on 2008-04-26
This is what I got from typing ls, but I guess I was still in the swiftweasel directory-should I try just from the desktop directory?
david@david-desktop:~/Desktop/swiftweasel$ ls
browserconfig.properties  libssl3.so
chrome                    libxpcom_compat.so
components                libxpcom_core.so
defaults                  libxpcom.so
dictionaries              libxpistub.so
extensions                LICENSE
firefox                   mozilla-xremote-client
firefox-bin               old-homepage-default.properties
greprefs                  plugins
icons                     README-Swiftweasel
launchers                 readme.txt
LEGAL                     README.txt
libfreebl3.chk            removed-files
libfreebl3.so             res
libmozjs.so               rpref.txt
libnspr4.so               run-mozilla.sh
libnss3.so                searchplugins
libnssckbi.so             swiftweasel
libplc4.so                swiftweasel-bin
libplds4.so               swiftweasel-icon-license.txt
libsmime3.so              updater
libsoftokn3.chk           updater.ini
libsoftokn3.so            xpicleanup
david@david-desktop:~/Desktop/swiftweasel$

---

### Post by eeeandrew on 2008-04-26
Just to confirm. On your desktop is there 2 folders of similar name. One a brown package shaped one and the other one a standard folder?

---

### Post by fullmetalgerbil on 2008-04-26
And thanks for sticking with me on this Joeb:)

---

### Post by Joeb454 on 2008-04-26
hmmm.

I've just kicked myself for not thinking of this before. But isn't Swiftweasel in the repositories? Go to System>Administration>Software Sources, and make sure all repositories except CD and Source Code are enabled.

Then from the terminal run (1 line at a time) ```
sudo aptitude update
sudo aptitude install swiftweasel
```

EDIT: No problem :) I've never used Swiftweasel, but I'll still try :)

---

### Post by fullmetalgerbil on 2008-04-26
Yeah, one brown package and one regular folder-the brown one has the long name the folder is just titled swiftweasel

---

### Post by fullmetalgerbil on 2008-04-26
I ran the commands, it couldn't find a swiftweasel package. I'm about to give up and just put up with Firefox crashing all the time.

---

### Post by eeeandrew on 2008-04-26
The reason I asked about the folders was to make sure your trying the right one. so do cd followed by the name of the regular looking folder. then
> ./configure
make
sudo make install

each on their own line.

Any luck?

---

### Post by Joeb454 on 2008-04-26
Sorry to hear that :( I've found Firefox 3 to be far better than 2.

You could always switch to Opera if you are running the x86 (32 bit) system.

---

### Post by fullmetalgerbil on 2008-04-26
No luck at all. All I keep getting when I enter ./configure is this:david@david-desktop:~/Desktop/swiftweasel$ cd swiftweasel
bash: cd: swiftweasel: Not a directory
david@david-desktop:~/Desktop/swiftweasel$ ./configure
bash: ./configure: No such file or directory
david@david-desktop:~/Desktop/swiftweasel$ ./configure
This has happened all of about half a dozen times.

---

### Post by eeeandrew on 2008-04-26
try > make from the swiftweasel directory?
then > sudo make install

Other than that I@m out of ideas.
Sorry.

---

### Post by fullmetalgerbil on 2008-04-26
Yeah, Firefox 3 is a little better-its only crashed on me once since I installed it yesterday. I've tried Opera and didn't much like it though.
The thing I cant figure out is why the hell my ./configure command does not work.

---

### Post by Absorbed on 2008-04-26
> **fullmetalgerbil said:**
> I ran the commands, it couldn't find a swiftweasel package. I'm about to give up and just put up with Firefox crashing all the time.

As I understand it, you need to type the following:
```
david@david-desktop:~/Desktop/swiftweasel$ ./swiftweasel
```

However, it would be much easier to let Ubuntu install swiftweasel automatically using "Add/Remove..." in the Applications menu on the top left. After it's installed, it should appear in the Internet submenu of the Application menu.

Edit: Okay, ignore me -- swiftweasel isn't in my Add/Remove. However you could try a different browser like Epiphany.

---

### Post by fullmetalgerbil on 2008-04-26
I give up.
david@david-desktop:~/Desktop/swiftweasel$ cd Desktop
bash: cd: Desktop: No such file or directory
david@david-desktop:~/Desktop/swiftweasel$ cd swiftweasel
bash: cd: swiftweasel: Not a directory
david@david-desktop:~/Desktop/swiftweasel$ ./configure
bash: ./configure: No such file or directory
david@david-desktop:~/Desktop/swiftweasel$ ./configure
bash: ./configure: No such file or directory
david@david-desktop:~/Desktop/swiftweasel$ make
make: *** No targets specified and no makefile found.  Stop.
david@david-desktop:~/Desktop/swiftweasel$ sudo make install
[sudo] password for david: 
make: *** No rule to make target `install'.  Stop.
david@david-desktop:~/Desktop/swiftweasel$ david@david-desktop:~/Desktop/swiftweasel$ ./swiftweasel
bash: david@david-desktop:~/Desktop/swiftweasel$: No such file or directory
david@david-desktop:~/Desktop/swiftweasel$

---

### Post by Joeb454 on 2008-04-26
Swiftweasel 2.0.0.13 is available as a .deb from sourceforge, why not install that and then update it to 2.0.0.14 through the actually application?

[Link to SourceForge DL Page]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717")

---

### Post by GavinZac on 2008-04-26
Not to sound blunt, but what the guys are telling you is the standard compilation procedure. Swiftweasal might not neccessarily follow that exact procedure. I'd recommend reading the SW website or the included README file.

Also, I'd try to fix Firefox, rather than switch browsers.

---

### Post by Joeb454 on 2008-04-26
I thought of that GavinZac - That's why I asked the OP to do an ls in the directory, seeing as there was no configure file then I abandoned that approach. You would have seen this on the 2nd or 3rd page I believe

---

### Post by fullmetalgerbil on 2008-04-26
Yeah, I just d/l'd and installed the older .deb. The whole thing though wasn't just getting the browser-I wanted to learn how to install tar.gz packages in general. 
The thing that kills me is all y'all told me the standard installation procedure-but bash wasn't recognizing commands like ./configure, make and install. I'm really trying to learn this stuff, however I dont know what the farg the problem is with my system that it wont recognize the commands.
Anyways thanks to everybody who helped me with this. Now its time to relax and enjoy a cup of beans....

---

### Post by Joeb454 on 2008-04-26
:lolflag:

I would be quite happy to walk you through compiling something, however the ls told me that Swiftweasel didn't have the configure file needed to compile (or autoconf file).

I'm glad you got Swiftweasel however. If you want to compile something let me know and I'll try and walk you through it...

Now off to see if Conky compiles on Hardy, it wouldn't in the Beta :(

---

### Post by Absorbed on 2008-04-26
> **fullmetalgerbil said:**
> 
david@david-desktop:~/Desktop/swiftweasel$ david@david-desktop:~/Desktop/swiftweasel$ ./swiftweasel

You don't type in the whole "david@david-desktop:~/Desktop/swiftweasel$ ./swiftweasel"; you just type "./swiftweasel" without the quotes.

---

### Post by Meskarune on 2008-04-26
You could also check out kazehakase browser. Its gecko based but very small and fast. You can find it in add/remove

---

### Post by warbread on 2008-04-26
[Click on this link]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717").

Follow the instructions on the image.  Just to clarify, there are .deb files on Sourceforge.net.  When you download this file, tell your browser to open it instead of saving it to the hard drive.  No need to decompress, find the directory or compile.

Don't forget to hit the thank you button!

---

### Post by Joeb454 on 2008-04-26
If you read above, I already told the OP about this, and (s)he followed my advice :)

Also don't ask for thanks ;) If the OP finds your post genuinely helpful, they will thank you for it.

I only have thanks mentioned in my sig because they were re-implemented a couple of days ago. It will be gone on Monday

---

### Post by warbread on 2008-04-27
> **Joeb454 said:**
> If you read above, I already told the OP about this, and (s)he followed my advice :)

Also don't ask for thanks ;) If the OP finds your post genuinely helpful, they will thank you for it.



That's not necessarily true, though the statement was more tongue-in-cheek than advice.  

And no, I didn't read.  I responded directly from email.  My bad for typing right after waking.

---

### Post by Joeb454 on 2008-04-27
:lolflag:

I know :) I just didn't want the mod's to tell you off either ;) And I've done the same before (posted just after waking). Don't worry about it ;)

---

### Post by sailor2001 on 2008-04-27
I was under the impression that swift weasel is not being supported or has changed name.. seamonkey is probably what you want now. (repositories)

---

### Post by Joeb454 on 2008-04-27
Swiftweasel looks like it is still being updated following the latest releases of Firefox 2.

I.e. if you look on the sourceforge page there is Swiftweasel 2.0.0.14 which I believe is the latest Stable release of Firefox

---

