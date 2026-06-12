---
title: "HowTo: Update GAIM to Pidgin (Two Easy Steps)"
date: 2007-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Old Pink on 2007-06-14
**Step One: **[Download Pidgin]("http://www.getdeb.net/release.php?id=1307") (from GetDeb, Debain installation file for Debain/Ubuntu)*
**Step Two:** [Download Transition Package]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb") (Install after installing Pidgin to replace GAIM on Ubuntu)

No terminal, no file editing. Just two nice and easy installations! 

**Source: **[http://www.mbhoy.com/14-06-2007/pidgin-201](http://www.mbhoy.com/14-06-2007/pidgin-201)

** ** Updated as of Pidgin 2.1.1 release. This guide now takes you to the latest version ****
** Updated as of [Pidgin 2.1.0]("http://www.mbhoy.com/01-08-2007/pidgin-210") release. Click [here]("http://www.mbhoy.com/01-08-2007/pidgin-210") to check What's New. **

---

### Post by durand on 2007-06-15
cool, thanks :)

---

### Post by ghindo on 2007-06-15
Great and simple tutorial - thanks a bunch!

---

### Post by Nordoelum on 2007-06-16
How to upgrade to the latest version? 2.0.2.

---

### Post by DizzyTech on 2007-06-16
This is a good idea, but you might want to get it from an external repo for the use of updates.

You can see either my post [here](http://ubuntuforums.org/showpost.php?p=2722318&postcount=6), or jamyski's post [here](http://ubuntuforums.org/showpost.php?p=2797785&postcount=12) for some Pidgin repos.

---

### Post by srunni on 2007-06-16
The easiest way to do this is to compile from the source code the Pidgin dev's provide at their site. Contrary to popular opinion, it's actually not that hard at all to compile something from source, as long as Ubuntu's package manager has a list of packages that the program is dependent on (in Pidgin's case, we just use Gaim's dependencies, since they are the same program). That way, you can get the newest version of Pidgin, instead of being stuck with an old version, which is what most of the repositories have.
1. You run ```
sudo apt-get build-dep gaim
``` to satisfy all dependencies for compiling Pidgin.
2. You download the source code from [http://www.pidgin.im/](http://www.pidgin.im/)
3. Open a terminal, cd to the directory that contains the Pidgin tarball and do ```
tar xvfj pidgin-*
```
4. cd to the extracted Pidgin folder and run ```
./configure
```
5. Run ```
make
```
6. Run ```
sudo make install
```
7. Now you can launch Pidgin from the command line with ```
pidgin
``` or by doing Alt+F2 and typing in "pidgin"
8. For those of you that want an icon in the GNOME panel/KMenu, copy the pidgin.desktop file from the extracted pidgin archive to /usr/share/applications



You can do this for any software that you want to update, but isn't available in the repositories yet. Unfortunately, compiling code like this without being able to use the build-dep command to satisfy all dependencies can make it nearly impossible to successfully complete, so if there isn't at least an older version of a program available in the repositories to build-dep with, you're going to have a hell of a time getting the configure script to work.

---

### Post by Greeface on 2007-06-22
Hmm, I get dependency problems.  Any suggestions?

EDIT:  Nevermind, I got it going.  Thanks for the howto.

---

### Post by detonish on 2007-06-25
> **srunni said:**
> The easiest way to do this is to compile from the source code the Pidgin dev's provide at their site. Contrary to popular opinion, it's actually not that hard at all to compile something from source, as long as Ubuntu's package manager has a list of packages that the program is dependent on (in Pidgin's case, we just use Gaim's dependencies, since they are the same program). That way, you can get the newest version of Pidgin, instead of being stuck with an old version, which is what most of the repositories have.
1. You run ```
sudo apt-get build-dep gaim
``` to satisfy all dependencies for compiling Pidgin.
2. You download the source code from [http://www.pidgin.im/](http://www.pidgin.im/)
3. Open a terminal, cd to the directory that contains the Pidgin tarball and do ```
tar xvfj pidgin-*
```
4. cd to the extracted Pidgin folder and run ```
./configure
```
5. Run ```
make
```
6. Run ```
sudo make install
```
7. Now you can launch Pidgin from the command line with ```
pidgin
``` or by doing Alt+F2 and typing in "pidgin"
8. For those of you that want an icon in the GNOME panel/KMenu, copy the pidgin.desktop file from the extracted pidgin archive to /usr/share/applications



You can do this for any software that you want to update, but isn't available in the repositories yet. Unfortunately, compiling code like this without being able to use the build-dep command to satisfy all dependencies can make it nearly impossible to successfully complete, so if there isn't at least an older version of a program available in the repositories to build-dep with, you're going to have a hell of a time getting the configure script to work.

Thanks .. worked greatly!

---

### Post by Old Pink on 2007-06-25
> **srunni said:**
> The easiest way to do this is to compile from the source code the Pidgin dev's provide at their site. Contrary to popular opinion, it's actually not that hard at all to compile something from source, as long as Ubuntu's package manager has a list of packages that the program is dependent on (in Pidgin's case, we just use Gaim's dependencies, since they are the same program). That way, you can get the newest version of Pidgin, instead of being stuck with an old version, which is what most of the repositories have.
1. You run ```
sudo apt-get build-dep gaim
``` to satisfy all dependencies for compiling Pidgin.
2. You download the source code from [http://www.pidgin.im/](http://www.pidgin.im/)
3. Open a terminal, cd to the directory that contains the Pidgin tarball and do ```
tar xvfj pidgin-*
```4. cd to the extracted Pidgin folder and run ```
./configure
```5. Run ```
make
```6. Run ```
sudo make install
```7. Now you can launch Pidgin from the command line with ```
pidgin
``` or by doing Alt+F2 and typing in "pidgin"
8. For those of you that want an icon in the GNOME panel/KMenu, copy the pidgin.desktop file from the extracted pidgin archive to /usr/share/applications



You can do this for any software that you want to update, but isn't available in the repositories yet. Unfortunately, compiling code like this without being able to use the build-dep command to satisfy all dependencies can make it nearly impossible to successfully complete, so if there isn't at least an older version of a program available in the repositories to build-dep with, you're going to have a hell of a time getting the configure script to work.

I know how to compile, it's the same as compiling for any application, essentially. 

I was offering an entirely GUI based substitute for those who prefer to avoid terminal. 

As you can see, my tutorial was two steps, yours was seven.

Don't hijack threads.

---

### Post by Depressed Man on 2007-06-25
Now now we´re suppose to be learning and helping each other. It&#347; what makes Ubuntu great. For example, I´m relatively unfamilar with compiling, so I just learned how to compile and now I have the benefit of using your two step method to save myself some time. :D

---

### Post by dseybert on 2007-06-26
> **Old Pink said:**
> **Step One: **[Download Pidgin]("http://www.getdeb.net/release.php?id=955") (from GetDeb, Debain installation file for Debain/Ubuntu)
**Step Two:** [Download Transition Package]("http://www.mfimg.com/files/8/gaim_2.0.1-1%7Efeisty0.1_all.deb") (Install after installing Pidgin to replace GAIM on Ubuntu)

No terminal, no file editing. Just two nice and easy installations! 

**Source: **[http://www.mbhoy.com/14-06-2007/pidgin-201](http://www.mbhoy.com/14-06-2007/pidgin-201)

The transition link isn't working for me.

---

### Post by JFire on 2007-06-26
> **dseybert said:**
> The transition link isn't working for me.

Me either but just follow Srunni's advice and it'll all work out ok.


Give a man a fish and you'll feed him for a day.
Teach a man to fish and you'll feed him for life.

Thanks for the lesson :)

---

### Post by Old Pink on 2007-06-26
> **dseybert said:**
> The transition link isn't working for me.

> **JFire said:**
> Me either

Fixed it. :) 

If you'd clicked the source you would've seen a fix anyway. :)

---

### Post by Tech_gogi on 2007-06-26
Thanks muchly for this..

---

### Post by cyberdork33 on 2007-06-26
getdeb links are not working... wanted to compile anyway... Thanks for the transition package though.

---

### Post by Mismatch on 2007-06-27
I am new to compiling code ... srunni's instructions worked fine .. thx a lot  :D

---

### Post by ballzy on 2007-07-18
If I want Pidgin to replace Gaim, don't I have to uninstall Gaim first?

If so, how do I do this?

I looked in the Synaptic Package Manager and saw that I have "gaim" and "gaim-data" installed.  Should I just mark both of those for "complete removal"? (What's the difference between "removal" and "complete removal"?) And are there more packages that are only used for gaim that should also be removed?

Or does unchecking Gaim in Add/Remove Applications work better? What packages does that remove/completely remove?

Also, is ```
sudo apt-get remove gaim
``` the same as marking "gaim" in Synaptic for "removal" or "complete removal" or neither?

Thanks!

---

### Post by maduranga on 2007-07-27
great.. Pidgin is now working... thx

---

### Post by Sayers on 2007-07-27
I'd rather wait for it to come out in 7.10 but this is a great guide. Shows both ways to do upgrade.

---

### Post by pjalegria on 2007-08-07
Its possible to update to the new Pidgin 2.1?????

---

### Post by rahimveron on 2007-08-13
Thank you now i have Pidgin installed........Thanks shrunni explaining the source compilation and OldPink for those two easy steps!!

---

### Post by PLmatt91 on 2007-08-13
Thanks so much!

---

### Post by nothing4me on 2007-08-14
Thanks. :)
I can confirm this also works on 2.1.0

Worked like a charm!
By the way, thanks for the GetDeb site! :D

---

### Post by giganerd on 2007-08-14
Awesome!  It also worked for me for Pidgin 2.1.0.

---

### Post by Old Pink on 2007-08-23
I'll update the thread with the 2.1.0 information, although 2.1.1 is out now. ;)

---

### Post by Dark Star on 2007-08-23
Thanks but there is another way just add repo. of Pidgin in /etc/apt/sources.list then after the update you Gaim will be transformed in Pidgin :D

---

### Post by Old Pink on 2007-08-23
> **Dark Star said:**
> Thanks but there is another way just add repo. of Pidgin in /etc/apt/sources.list then after the update you Gaim will be transformed in Pidgin :DThere isn't an official Pidgin repository as of yet.

---

### Post by Fonon on 2007-08-23
This is very awesome.  It was very easy, though you might want to explain about the dependancies of the pidgin-data.  It's very easy to fix, but it should still be there.

---

### Post by Dark Star on 2007-08-24
> **Old Pink said:**
> There isn't an official Pidgin repository as of yet.
Just give this a try :) It changed my Gaim into Pidgin latest ver.. ::) I haven't used .deb just changed the repo. and after next update I got Pidgin :D

---

### Post by EXCiD3 on 2007-08-24
I like this idea, but what I am wondering is why doesnt pidgin just have a premade debian package?

---

### Post by evaarties on 2007-08-24
> **Dark Star said:**
> Just give this a try :) It changed my Gaim into Pidgin latest ver.. ::) I haven't used .deb just changed the repo. and after next update I got Pidgin :D

Can you tell me which file you changed and what lines you changed into what new lines?

Like 

change

src/gaim

to 

src/pidgin

---

### Post by Old Pink on 2007-08-24
> **Dark Star said:**
> Just give this a try :) It changed my Gaim into Pidgin latest ver.. ::) I haven't used .deb just changed the repo. and after next update I got Pidgin :DI'm not giving anything a try, I'm running latest Pidgin, I know where it came from, and I know where my Gaim has gone.

There are no official Pidgin repositories, you may be using an unofficial repository found on the internet but these can compromise system security and allow practically anything to be installed and run on your computer at your expense. 

You have used a .deb. Repositories use .deb files to provide updates. If you're at the level of expertise where you're unaware of this, I don't recommend third party repositories.

Please avoid any further repository talk in this thread, it's clear they're on different topics.

> **evaarties said:**
> Can you tell me which file you changed and what lines you changed into what new lines?

Like 

change

src/gaim

to 

src/pidginI don't recommend you change file names or the content of files without the experience level required to do so yourself. 

This method takes two steps, one of which is optional, and will be done in 2 minutes. There's no reason to make things harder modifying file names and content, why look for the harder route?

Please avoid discussing your plans for this method in this thread. This thread is for the discussion, appreciation and support of the method in Post #1.

The latest version of Pidgin is now available on GetDeb: [http://www.getdeb.net/release.php?id=1307](http://www.getdeb.net/release.php?id=1307) (2.1.1) then use [this link](http://mbhoy.com/?s=Pidgin) to locate and install the transition package (not version dependant, will work with any Pidgin version) and you're sorted. No file changing. No shady repositories. No terminal. 2 minutes of clicking.

---

### Post by Project_2501 on 2007-08-25
> **srunni said:**
> The easiest way to do this is to compile from the source code the Pidgin dev's provide at their site. Contrary to popular opinion, it's actually not that hard at all to compile something from source, as long as Ubuntu's package manager has a list of packages that the program is dependent on (in Pidgin's case, we just use Gaim's dependencies, since they are the same program). That way, you can get the newest version of Pidgin, instead of being stuck with an old version, which is what most of the repositories have.
1. You run ```
sudo apt-get build-dep gaim
``` to satisfy all dependencies for compiling Pidgin.
2. You download the source code from [http://www.pidgin.im/](http://www.pidgin.im/)
3. Open a terminal, cd to the directory that contains the Pidgin tarball and do ```
tar xvfj pidgin-*
```
4. cd to the extracted Pidgin folder and run ```
./configure
```
5. Run ```
make
```
6. Run ```
sudo make install
```
7. Now you can launch Pidgin from the command line with ```
pidgin
``` or by doing Alt+F2 and typing in "pidgin"
8. For those of you that want an icon in the GNOME panel/KMenu, copy the pidgin.desktop file from the extracted pidgin archive to /usr/share/applications



You can do this for any software that you want to update, but isn't available in the repositories yet. Unfortunately, compiling code like this without being able to use the build-dep command to satisfy all dependencies can make it nearly impossible to successfully complete, so if there isn't at least an older version of a program available in the repositories to build-dep with, you're going to have a hell of a time getting the configure script to work.

Thanks for this Sunni!!!!!!!!!!

---

### Post by darclaird on 2007-08-25
Thanks for the clea concise howto guys, worked first time round with 2.1.1 on a fairly fresh 7.04 install

Keep up the good word

-- J

---

### Post by Pikestaff on 2007-08-25
> **srunni said:**
> The easiest way to do this is to compile from the source code the Pidgin dev's provide at their site. Contrary to popular opinion, it's actually not that hard at all to compile something from source, as long as Ubuntu's package manager has a list of packages that the program is dependent on (in Pidgin's case, we just use Gaim's dependencies, since they are the same program). That way, you can get the newest version of Pidgin, instead of being stuck with an old version, which is what most of the repositories have.
1. You run ```
sudo apt-get build-dep gaim
``` to satisfy all dependencies for compiling Pidgin.
2. You download the source code from [http://www.pidgin.im/](http://www.pidgin.im/)
3. Open a terminal, cd to the directory that contains the Pidgin tarball and do ```
tar xvfj pidgin-*
```
4. cd to the extracted Pidgin folder and run ```
./configure
```
5. Run ```
make
```
6. Run ```
sudo make install
```
7. Now you can launch Pidgin from the command line with ```
pidgin
``` or by doing Alt+F2 and typing in "pidgin"
8. For those of you that want an icon in the GNOME panel/KMenu, copy the pidgin.desktop file from the extracted pidgin archive to /usr/share/applications



You can do this for any software that you want to update, but isn't available in the repositories yet. Unfortunately, compiling code like this without being able to use the build-dep command to satisfy all dependencies can make it nearly impossible to successfully complete, so if there isn't at least an older version of a program available in the repositories to build-dep with, you're going to have a hell of a time getting the configure script to work.

Thanks, the packages in the first post didn't work for me (maybe because I'm using Dapper and not Feisty?) but this did, thanks :)

Although actually I have a problem now where Pidgin only runs when I type it into the terminal... I can't get it to run by clicking the .desktop icon or going into the menu and clicking on it.  It appears to be loading, but it doesn't do anything.  Tips?

---

### Post by Dark Star on 2007-08-26
> **Old Pink said:**
> I'm not giving anything a try, I'm running latest Pidgin, I know where it came from, and I know where my Gaim has gone.

There are no official Pidgin repositories, you may be using an unofficial repository found on the internet but these can compromise system security and allow practically anything to be installed and run on your computer at your expense. 

You have used a .deb. Repositories use .deb files to provide updates. If you're at the level of expertise where you're unaware of this, I don't recommend third party repositories.

Please avoid any further repository talk in this thread, it's clear they're on different topics.

I don't recommend you change file names or the content of files without the experience level required to do so yourself. 

This method takes two steps, one of which is optional, and will be done in 2 minutes. There's no reason to make things harder modifying file names and content, why look for the harder route?

Please avoid discussing your plans for this method in this thread. This thread is for the discussion, appreciation and support of the method in Post #1.


Ok boss :lolflag: As you say thanks for guide though :D

---

### Post by pedja_portugalac on 2007-09-08
> **Old Pink said:**
> **Step One: **[Download Pidgin]("http://www.getdeb.net/release.php?id=1307") (from GetDeb, Debain installation file for Debain/Ubuntu)*
**Step Two:** [Download Transition Package]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb") (Install after installing Pidgin to replace GAIM on Ubuntu)

No terminal, no file editing. Just two nice and easy installations! 

**Source: **[http://www.mbhoy.com/14-06-2007/pidgin-201](http://www.mbhoy.com/14-06-2007/pidgin-201)

** ** Updated as of Pidgin 2.1.1 release. This guide now takes you to the latest version ****
** Updated as of [Pidgin 2.1.0]("http://www.mbhoy.com/01-08-2007/pidgin-210") release. Click [here]("http://www.mbhoy.com/01-08-2007/pidgin-210") to check What's New. **

Very nice. Thank You.
PS. Before today i couldn't even use Gaim because i have a firestarter firewall manager and it simply didn't work. Now I can use all my IM accounts with no pain. Thanks ones again.:)

---

### Post by defe007 on 2007-09-11
Thanks alot, this worked like a charm!

---

### Post by chrux on 2007-09-13
I'm pretty sure I can delete the .tar files after installing, but can I del the folder it has created? or perhaps move it, cuz its current on my desktop

---

### Post by pedja_portugalac on 2007-09-15
What .tar files? Do you meen .deb files? I don't understand how could those debian packages create folders on your desktop? If you have followed instructions and order of installation it shouldn't happen.

---

### Post by maniac_X on 2007-09-16
> **Old Pink said:**
> 
Please avoid discussing your plans for this method in this thread. This thread is for the discussion, appreciation and support of the method in Post #1.


Wow! I had to do a double-take. For a minute there I thought I had accidently logged into some M$ forum with discussion  that there's only 1 way to do things.

Thanks :KS**srunni**:KS! Learning new things is sometimes better than taking the easiest road. :)

---

### Post by purplenite on 2007-09-16
I tried compiling from source, but when I attempt to run pidgin, I get the following: "pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory"

I followed srunni's instructions for compilation exactly. Any suggestions?

---

### Post by kditty on 2007-09-16
> **Old Pink said:**
> **Step One: **[Download Pidgin]("http://www.getdeb.net/release.php?id=1307") (from GetDeb, Debain installation file for Debain/Ubuntu)*
**Step Two:** [Download Transition Package]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb") (Install after installing Pidgin to replace GAIM on Ubuntu)

No terminal, no file editing. Just two nice and easy installations! 

**Source: **[http://www.mbhoy.com/14-06-2007/pidgin-201](http://www.mbhoy.com/14-06-2007/pidgin-201)

** ** Updated as of Pidgin 2.1.1 release. This guide now takes you to the latest version ****
** Updated as of [Pidgin 2.1.0]("http://www.mbhoy.com/01-08-2007/pidgin-210") release. Click [here]("http://www.mbhoy.com/01-08-2007/pidgin-210") to check What's New. **

when i try this method, i get "error: dependancy is not satisfiable: pidgin-data" and "error: dependancy is not satisfiable: pidgin"

---

### Post by purplenite on 2007-09-16
> **purplenite said:**
> I tried compiling from source, but when I attempt to run pidgin, I get the following: "pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory"

I followed srunni's instructions for compilation exactly. Any suggestions?


I just fixed this problem. If anyone else runs in to this, you need to fix a symbolic link first:
```
sudo ln -s /usr/local/lib/libpurple.so.0 /usr/lib
```

---

### Post by spetras73 on 2007-09-16
hi, after I installed the pidgin-data package I'm getting "Error: Dependency is not satisfiable: libatk1.0-0"

I have the libatk1.0-0 on my system, it is the latest version (verified thru apt-get).

any ideas?  thanks so much.

---

### Post by olieviya on 2007-09-17
Just curious does anybody know why the official pidgin website doesn't offer a .deb? [http://www.pidgin.im/download/]("http://www.pidgin.im/download/")

---

### Post by ruggrat on 2007-09-17
> **olieviya said:**
> Just curious does anybody know why the official pidgin website doesn't offer a .deb? [http://www.pidgin.im/download/]("http://www.pidgin.im/download/")

As they say on their site: ["WhyPackagesExist']("http://developer.pidgin.im/wiki/WhyPackagesExist"):

"As the upstream authors, our primary distribution method is naturally the source itself in tar.gz and tar.bz2 form. Our responsibility ends when we release the tarball.

As a convenience, an extra, we provide binary installers where we have developers able and willing to do so. We have developers with a significant number of Red Hat and Fedora machines or chroot environments, thus we provide various RPM packages.

While we have a few developers using Debian systems, the Debian package maintainers have historically worked closely with us and provided timely updates to the official packages. There has been no need on our part to create packages for Debian unstable, and no desire on our part to try to backport packages to Debian testing or stable. The situation with Ubuntu is the same. "

They think they will do more harm than good, so it's better off to let us just compile it?

---

### Post by MerlinsLair on 2007-09-17
Thanks for all the help on this guys! Got things sorted and working just fine with the 2-step method. Glad to learn more about this great OS everyday whether it be by compiling or a step x step method.

Thanks again!

---

### Post by moopoo on 2007-09-17
PLEASE FORGET THE STUFF I WROTE BELOW. I crashed into this thread without knowing, that getdeb was mentioned in post #1!
Sorry guys, can't find the delete button.

***********************************************************************************************
Uhhmmm, I don't know if this was mentioned before ...

but where you looking for [this]("http://www.getdeb.net/app.php?name=Pidgin")?
please scroll down to choose between 32 and 64bit.

getdeb is a great source for debs.

yours,
m00p00

---

### Post by gOLdenHaWK3D on 2007-09-18
> **Old Pink said:**
> **Step One: **[Download Pidgin]("http://www.getdeb.net/release.php?id=1307") (from GetDeb, Debain installation file for Debain/Ubuntu)*
**Step Two:** [Download Transition Package]("http://www.mbhoy.com/wp-content/uploads/mfimg/gaim_2.0.1-1%7Efeisty0.1_all.deb") (Install after installing Pidgin to replace GAIM on Ubuntu)

No terminal, no file editing. Just two nice and easy installations! 

**Source: **[http://www.mbhoy.com/14-06-2007/pidgin-201](http://www.mbhoy.com/14-06-2007/pidgin-201)

** ** Updated as of Pidgin 2.1.1 release. This guide now takes you to the latest version ****
** Updated as of [Pidgin 2.1.0]("http://www.mbhoy.com/01-08-2007/pidgin-210") release. Click [here]("http://www.mbhoy.com/01-08-2007/pidgin-210") to check What's New. **

Thanks a ton!
It worked perfectly. :)

:guitar:

---

### Post by bluvy on 2007-09-18
> **srunni said:**
> The easiest way to do this is to compile from the source code the Pidgin dev's provide at their site. Contrary to popular opinion, it's actually not that hard at all to compile something from source, as long as Ubuntu's package manager has a list of packages that the program is dependent on (in Pidgin's case, we just use Gaim's dependencies, since they are the same program). That way, you can get the newest version of Pidgin, instead of being stuck with an old version, which is what most of the repositories have.
1. You run ```
sudo apt-get build-dep gaim
``` to satisfy all dependencies for compiling Pidgin.
2. You download the source code from [http://www.pidgin.im/](http://www.pidgin.im/)
3. Open a terminal, cd to the directory that contains the Pidgin tarball and do ```
tar xvfj pidgin-*
```
4. cd to the extracted Pidgin folder and run ```
./configure
```
5. Run ```
make
```
6. Run ```
sudo make install
```
7. Now you can launch Pidgin from the command line with ```
pidgin
``` or by doing Alt+F2 and typing in "pidgin"
8. For those of you that want an icon in the GNOME panel/KMenu, copy the pidgin.desktop file from the extracted pidgin archive to /usr/share/applications



You can do this for any software that you want to update, but isn't available in the repositories yet. Unfortunately, compiling code like this without being able to use the build-dep command to satisfy all dependencies can make it nearly impossible to successfully complete, so if there isn't at least an older version of a program available in the repositories to build-dep with, you're going to have a hell of a time getting the configure script to work.

Everything seems to be going fine until I get to step 5 and type:

make

the terminal says:

make: *** No targets specified and no makefile found.  Stop.

What am I doing wrong?

---

### Post by superpenguin79 on 2007-09-19
Thanks for the tips, works great, just wish it would support Skype and I'd be all set... :)

---

### Post by fINTiP on 2008-04-13
I am having the same problem as Bluvy. I get the same response.

Also, after step one, I get:

```
E: Could not open file /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_edgy_free_source_Sources - open (2 No such file or directory)
```

I'm running a fresh install of Edgy...

Bonvolu help?

Dankon,

.L

---

