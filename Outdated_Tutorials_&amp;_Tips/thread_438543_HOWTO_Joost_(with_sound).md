---
title: "HOWTO: Joost (with sound)"
date: 2007-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by mikewitt on 2007-05-09
You need to recompile wine for this to work, and it takes a while. If you're afraid of doing this, you probably want to stop now.

This is for Ubuntu 7.04

First you need to get a few things ready for the install:

first and foremost, download a copy of the most recent Joost program from Joost

open Synaptic, click on "Settings --> Repositories" Click on the "3rd Party Tab" click "Add" at the bottom. In the box that comes up, type this (or copy it):
```
deb-src http://wine.budgetdedicated.com/apt feisty main
```

Click "Ok" and then close the settings window. After the popup that comes up, telling you that you need to hit the "Reload" button, hit the "Reload" button. Close synaptic.

In a console, type:
```
sudo apt-get build-dep wine
```
Now we're going to get the build things. You don't need this step if you've compiled things before:
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
Answer Y to any prompts that come up. (Thanks to foureight84 for suggesting $(uname -r))

Now get some dependencies:
```

sudo apt-get install fakeroot libasound2-dev libaudiofile-dev libesd0-dev libaudio-dev libcapi20-dev liblcms1-dev libcupsys2-dev libsane-dev libhal-dev libdbus-1-dev freeglut3-dev libc6-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libglib1.2-dev libglib2.0-dev libgpg-error-dev libice-dev libieee1284-3-dev libjpeg62-dev libldap2-dev libltdl3-dev libmad0-dev libmng-dev libncurses5-dev libogg-dev libopencdk8-dev libpng12-dev libqt3-mt-dev libsm-dev libusb-dev libvorbis-dev libx11-dev libxcursor-dev libxext-dev libxft-dev libxi-dev libxml2-dev libxmu-dev libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev render-dev unixodbc-dev x-dev zlib1g-dev xlibs-dev libxxf86dga-dev libxxf86vm-dev libjack0.100.0-dev libicu34-dev libungif4-dev libssl-dev
```

Now make a working directory:
```
mkdir wine-src
cd wine-src
```

and get the Wine source:
```
apt-get source wine
```

now cd into the directory that was just created by apt:
```
cd wine-0.9.39~winehq0~ubuntu~7.04
```

and run this command to download the patches necessary to run Joost: (I'm hosting these patches, because they're easire to get this way, rather than from the appdb site)
```
wget http://witt.michael.googlepages.com/patch2.patch http://witt.michael.googlepages.com/patch3.patch http://witt.michael.googlepages.com/patch4.patch http://witt.michael.googlepages.com/patch5.patch http://witt.michael.googlepages.com/patch6.patch http://witt.michael.googlepages.com/patch7.patch http://witt.michael.googlepages.com/patch8.patch
```

now we need to patch using the files we downloaded:
```
patch -p1 < patch2.patch
patch -p1 < patch3.patch
patch -p1 < patch4.patch
patch -p1 < patch5.patch
patch -p1 < patch6.patch
patch -p1 < patch7.patch
patch -p1 < patch8.patch
```

and now that we've patched everything (everything should have gone smoothly) type:
```
dpkg-buildpackage -rfakeroot -uc -b
```
This will take a LONG time (an hour or so)

after it's done, assuming no errors,
```
cd ..
```
and install:
```
sudo dpkg -i wine_0.9.39~winehq0~ubuntu~7.04-1_i386.deb
```

after that's done, type:
```
winecfg
```
Make sure that "Windows XP appears in the dropdown on the first page at the bottom. If it doesn't, select it.
Next click on the audio tab. Make sure that only "OSS Driver" is checked. At the bottom, turn DirectSound Hardware Acceleration to "Emulated" and check the checkbox that says "Driver Emulation"
Now go into the graphics tab, and check "Emulate a virtual desktop" and enter a size of 800x600. Uncheck "Allow the window manager to control windows"
Click "Apply" then "Ok"

**Now to install joost:**
```
cd
cd Desktop
wine JoostSetup-FriendsEdition-0.10.4.exe
```
and follow the prompts

To start Joost type:
```
cd ~/.wine/c_drive/"Program Files"/Joost
```

Then to start joost, type:
```
wine xulrunner/tvprunner.exe application.ini
```
If you don't like all those 'fixme' errors, which mean nothing to most people, run the command like this:
```
WINEDEBUG=fixme-all wine xulrunner/tvprunner.exe application.ini
```

It may take a couple of minutes, but you should eventually see a splash then a login window. Note that if you need to create a username (not an account, but a name associated with an email), you need to do that. When you click OK after doing what it says, you will just see in red letters "true" appear. It will not progress, but this is Ok, joost still got the info. Click Cancel, then type the name you just created.

You should now have Joost up and running. (Troubleshooting section at bottom) :popcorn:


=== METHOD 2 === GIT ===

This is a secondary method, using git to get the latest and greatest wine (which is not dependent upon a repo). We get the latest code (which might be unstable) and patch it. It is also faster when upgrading, as the files that are unchanged do not need to be recompiled.

**[COLOR="Red"]WARNING:[/COLOR] This method uses code snapshots, WHICH MAY BE UNSTABLE. USE AT YOUR OWN RISK.**

Step 1:
First, download and install git (note that the version that is in the apt repo for dapper will NOT work; it's too old)
```
sudo apt-get install cogito
```
**NOTE: If you try and download the program "git" from the apt repo, it will cause problems. It is not the same git we need.**

2:
Make and go into the wine-src folder under home.
```
cd
mkdir wine-src
cd wine-src
```

3:
Use git to fetch the latest wine-source, then go into the directory.
```
git clone git://source.winehq.org/git/wine.git wine-git
cd wine-git
```
The git command will take a while. Just go grab something to eat while you wait.

4:
Use wget to download the patches: (As of 0.9.37 patch1.patch is no longer required, however all of the others are.)
```
wget http://witt.michael.googlepages.com/patch2.patch http://witt.michael.googlepages.com/patch3.patch http://witt.michael.googlepages.com/patch4.patch http://witt.michael.googlepages.com/patch5.patch http://witt.michael.googlepages.com/patch6.patch http://witt.michael.googlepages.com/patch7.patch http://witt.michael.googlepages.com/patch8.patch
```

5:
Apply patches:
```
patch -p1 < patch2.patch
patch -p1 < patch3.patch
patch -p1 < patch4.patch
patch -p1 < patch5.patch
patch -p1 < patch6.patch
patch -p1 < patch7.patch
patch -p1 < patch8.patch
```

6:
Commit patches to our branch.
```
git commit -a
```
Vi(m) will come up (which I hate) and you will need to know a few commands.
All command sequences start with a colon (Shift+;). They end when you press enter.
To exit, use "quit" if you've changed something and want to quit without saving, use "quit!"
To save, use the command "write"

For the commits, uncomment the names of all of the first set of files. (they should all end with ".c")

7:
Make wine.
```
./configure
make depend && make
```
This will take a long time.

8:
Uninstall any previous versions of wine
[INDENT]If you used the instructions above, type ```
sudo dpkg remove wine
```
If you used apt to install wine, type ```
sudo apt-get remove wine
```
If you installed from source, cd into that directory, and type ```
sudo make uninstall
```[/INDENT]

9:
Install the new version of wine.
```
sudo make install
```

10:
Check that wine was installed correctly
```
wine --version
```
This should show something like 'wine-0.9.37-g8d159b7'

11:
Continue by using the instructions above to install and run Joost.

**How to use git to update the source (and save a lot of time recompiling):**
1:
Type 
```
git fetch
git rebase origin
```

2:
Run make again:
```
make depend && make
```
This shouldn't take long, as most of the files are unchanged.

3:
Reinstall.
```
sudo make install
```

**[COLOR="Red"][SIZE="5"]Troubleshooting common problems (FAQ):[/SIZE][/COLOR]**
Q) Video doesn't work
A) If you have an nVidia card, try installing the latest beta drivers (for an x86: [http://www.nvidia.com/object/linux_display_ia32_100.14.03.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.03.html"))  (Thanks to georgie for that answer)
 For a tutorial:[http://ubuntuforums.org/showthread.php?t=296933](http://ubuntuforums.org/showthread.php?t=296933)(Thanks Syosoft)
Also, if you use Beryl, set it to metacity, it will run better.
A2) Make sure that "Virtual Desktop" is checked, with a resoulution of 800x600. In more recent versions, unchecking Virtual Desktop (so NONE of the options are checked) sometimes works (and sometimes doesn't). It will play in fulscreen if it works, but can freeze if it doesn't. If it freezes, just hit Ctrl+Alt+Backspace and it will restart GDM (but you'll loose any work you may have done in the background.

Q) Sound doesn't work:
A) In winecfg, under the audio tab, try selecting different drivers; one should work. Also, make sure that "Hardware Acceleration" is set to Emulation, and not any of the other options. Also try checking the box that says "Emulate Sound driver)

Q) It won't start.
A) Go into a console and type 'wine --version' If it says anything less than 0.9.36 (if you've done it recently it should say 0.9.37) then you haven't installed your new wine, or an older version is taking control. Type "sudo apt-get remove wine" and then cd into your wine directory, and and install using the directions above. Then when you type 'wine --version' it should come up with 0.9.37. If it says that and still won't run, make sure you've patched everything (patches 2-8). If it says 'cannot find wine' then just cd into your source directory, and install using the instructions above.

Q) Fonts don't work.
A) Try running this: ```
sudo apt-get install msttcorefonts
``` (Thanks methane)
If that doesn't work, after installing msttcorefonts, run the command: ```
cp /usr/share/fonts/truetype/msttcorefonts/* ~/.wine/drive_c/windows/fonts/
``` (Thanks tetralis)

Q) Should I use sudo when running wine?
A) Never.

Q) What should I do if Joost is using all my CPU?
> **javaJake said:**
> 
If anyone gets stuck with Joost running with this bug, especially after installation, run "killall -KILL tvprunner.exe" - it's the only way you'll get it to close.

For more information, visit these links:
[http://appdb.winehq.org/appview.php?iVersionId=7821](http://appdb.winehq.org/appview.php?iVersionId=7821)
[http://bugs.winehq.org/show_bug.cgi?id=1631](http://bugs.winehq.org/show_bug.cgi?id=1631)

So, to sum up, **this bug is known about already, but cannot be fixed without dramatic patches.**

***** CHANGELOG *****
May 11, 2007: Initaial Revision
May 12, 2007: Added git method, updated to reflect newest version of wine.
May 14, 2007: Added ./configure to git method because of a suggestion. Also added Troubleshooting/FAQ section.
May 16, 2007: Fixed linux-headers section.
May 20, 2007: Added more info to troubleshooting.
May 22, 2007: More info added.
May 24, 2007: Joost has been updated! Brought tutorial up to speed.
May 26, 2007: See message at the top.
June 3, 2007: Changed to reflect Version 0.9.38 of wine.
June 9, 2007: Updated to reflect Joost 0.10.4
June 12, 2007: Added method to get rid of 'fixme' errors.
June 16, 2007: Removed link at top to invites; no more left.
June 18, 2007: Updated to reflect version 0.9.39 of wine in repo.
June 25, 2007: Minor typos corrected; clarified instructions.

---

### Post by Mets on 2007-05-09
can't wait to try this (need to upgrade first), looks awesome, thanks for posting

---

### Post by gorilla_king on 2007-05-09
never heard of joost before. sounds cool. i want to try it. would someone mind sending me an invite [email]thrasher.basher@gmail.com[/email] 
thanks in advance

---

### Post by pingpongboss on 2007-05-10
[IMG]http://i25.photobucket.com/albums/c80/pingpongboss/ImageBot/Screenshot-Winedesktop.png[/IMG]

I keep getting that screen even though I followed your directions on what to set on the Audio page for winecfg.

edit: this is what I get with version 0.9.2
[IMG]http://i25.photobucket.com/albums/c80/pingpongboss/ImageBot/Screenshot-Winedesktop-1.png[/IMG]

---

### Post by KubuntuKilledMe on 2007-05-10
Hi, i could use an invite too, sent to hugo1000 at the gmails.

---

### Post by methane on 2007-05-10
everything worked for me, but the font on the data-entry screen is totally messed up.  Can't even read the buttons.
I'm assuming that this is because I don't have the extra Windows Fonts installed.  I'll try that later.  
Otherwise, thanks!
edit: I'm running Feisty Kubuntu, BTW.

edit: install the fonts like so:
```
sudo apt-get install msttcorefonts
```
and it works for me.

---

### Post by mikewitt on 2007-05-10
Go into winecfg, and under the audio tab, there should be a tree of audio devices. I found mine under "OSS Driver -> Wave In" [IMG]http://ubuntuforums.org/attachment.php?attachmentid=32219&stc=1&d=1178800277[/IMG]

You should find yours under one of the "Wave Out" devices. On two computers, I never found it under ALSA, but it must be there for a reason, so it might be the alsa driver you need. Just uncheck OSS driver, and check the appropriate driver.

---

### Post by dercaS on 2007-05-10
I have trouble compiling
Some time after i've started
```
dpkg-buildpackage -rfakeroot -uc -b
```
I get this:
```
i486-linux-gnu-gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -DWINE_UNICODE_API="" -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -Wall -g -O2 -fno-stack-protector  -o c_949.o c_949.c
c_949.c:9301: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[3]: *** [c_949.o] Error 1
make[3]: Leaving directory `/home/dercas/wine-src/wine-0.9.36~winehq0~ubuntu~7.04/libs/wine'
make[2]: *** [wine] Error 2
make[2]: Leaving directory `/home/dercas/wine-src/wine-0.9.36~winehq0~ubuntu~7.04/libs'
make[1]: *** [libs] Error 2
make[1]: Leaving directory `/home/dercas/wine-src/wine-0.9.36~winehq0~ubuntu~7.04'
make: *** [build-stamp] Error 2
dercas@RSmaster:~/wine-src/wine-0.9.36~winehq0~ubuntu~7.04$
```

What to do? :confused:

---

### Post by andrek on 2007-05-10
Could somebody upload a compiled .deb file?

---

### Post by nkt108 on 2007-05-10
my fonts are also broken when I run Joost... can't read any of the text or buttons

the .deb file is too big to upload, but I could email it to anyone who is having issues compiling their own

mine is for AMD_64 only

---

### Post by darundal on 2007-05-10
Hey, could someone email me an invite? Thx!

---

### Post by nkt108 on 2007-05-10
font issue fixed, just copied all the windows fonts from my windows drive over.
this method of installing wine installs no fonts into the windows/fonts folder

---

### Post by nkt108 on 2007-05-10
get it while it's still there:

[https://joost.com/presents/gigaom-newteevee/](https://joost.com/presents/gigaom-newteevee/)

---

### Post by DoktorSeven on 2007-05-10
[Here's my compiled version](http://doktorseven.miskie.net/files/wine_0.9.36~winehq0~ubuntu~7.04-3_i386.deb) (x86) if someone wants to try it.  **Try at your own risk.**

Title screen and login work for me but all I get is a blank screen while the audio plays...

---

### Post by chr1831 on 2007-05-10
it launches now (WOOT!!!), but it says i have no soundcard and i did everything it said 2 do...

HELP!!!!!!! please and thank you :D

---

### Post by thegreenblob on 2007-05-10
Thanks, got it working :) 

Heres a compiled version for ubuntu 6.10 edgy x86. :) 

[http://www.mediafire.com/?cnzdwrtmayo](http://www.mediafire.com/?cnzdwrtmayo)

Like above use at your own risk.

---

### Post by jkeyes0 on 2007-05-10
It's working for me here, video, sound, everything. The interface is extremely slow (meaning I click, go get coffee, and when I've taken a nap, the UI comes up), but the video and sound play, and I can switch channels and everything seems functional. However, it's a bit jumpy compared to actually running it in Windows, and the sound is... scratchy is about the best way to put it, I think. I've got the sound set to 48000 sample rate and 16 bits per sample, with emulation and driver emulation (I tried all the way up through Full hardware acceleration, and it just became more jumpy and scratchy).

All in all, the best I've had it in Ubuntu, but not quite up to par. I've got a Windows machine running it now (secondary machine, only in existence for running Joost), so I'll probably hold onto that until wine "catches up" as it were, or the Linux version of Joost is released. Excellent progress for an extremely new app, either way. Bravo to the wine devs and those who have worked so hard to make the patches.

---

### Post by gxwalsh on 2007-05-11
I'd love to try this...Can someone send me a Joost invite to greg[at]gregwalsh.com

I've been playing with wine and even got it to work with my GRE software...mostly :) 

Thanks!
Greg

---

### Post by xinix on 2007-05-11
Heh, this is yet another request for an invite.
Thanks

---

### Post by siralphred on 2007-05-11
Anyone that still needs an invite  email me at [email]siralphred@gmail.com[/email]  with title  JOOST INVITE :)

---

### Post by efrincu on 2007-05-11
Excellent post!

Can I please have an invitation too?

Thanks a lot!

---

### Post by mkoby on 2007-05-11
Oh yea! Finally.  Thank you so much.  Someone should seriously buy you a case of your favorite beverage for this.

It is working on my desktop, flawlessly.

---

### Post by alef13 on 2007-05-11
OK, It really works. I followed all the steps and got Joost up and running.
There's only one problem: after running it on the command line, I can see the initial screen, and the 'Connecting' screen as well, but when the sound starts, the screen goes black forever. I'm sure that it's connected because I can hear the sound of the main Joost channel, the Joost Suggest.
I tought this problem was related with beryl, then I disabled it and ran metacity by hand, but I got the same problem.
Some times, after connecting, I can see the menus, but after few seconds it totally disappear and the screen goes black.
Any ideas?

---

### Post by Nukeador on 2007-05-11
It works!

I have only 2 problems:

1- The sound/video it's a bit crappy, faltering.
2- Mi personal info isn't stored so I have to enter my name and age over and over again when I start Joost.

---

### Post by philwhln on 2007-05-11
Almost worked. Joost was telling me it couldn't detect the soundcard, so I tried a few others. EsounD Driver worked the best. But Joost still crashes with this....

fixme:font:GetCharacterPlacementW flags 0x00000008 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 424
Software fallback:ctx->Multisample.Enabled
***************************************************************************
*********************************WARN_ONCE*********************************
File radeon_vtxfmt_a.c function r300MapBuffer line 708
Unknown access type
***************************************************************************

---

### Post by DoktorSeven on 2007-05-11
> **alef13 said:**
> OK, It really works. I followed all the steps and got Joost up and running.
There's only one problem: after running it on the command line, I can see the initial screen, and the 'Connecting' screen as well, but when the sound starts, the screen goes black forever. I'm sure that it's connected because I can hear the sound of the main Joost channel, the Joost Suggest.
I tought this problem was related with beryl, then I disabled it and ran metacity by hand, but I got the same problem.
Some times, after connecting, I can see the menus, but after few seconds it totally disappear and the screen goes black.
Any ideas?

This is exactly the problem I have running it that I mentioned above.  Not sure what the problem is.

---

### Post by pingpongboss on 2007-05-11
wine 0.9.37 source just came out today. Will your directions (and patch files) work for the new version as well?

---

### Post by mikewitt on 2007-05-11
I don't know if it'll work with 0.9.37. I'll try it tonight, and see if it works. (I'll update the tut if it does.)

EDIT:
Ok, after getting on back into Ubuntu (I needed to work with Visual Studio) I found out it's not in the repository yet. It probably will be soon, so I'm testing it now.

ONE MORE TIME:
If you use 0.9.37, DO NOT apply patch1.patch. It won't work (looks like they've added patch to 0.9.37 already). I have yet to find out how this will affect joost (compiling right now), but otherwise it seems the same.

---

### Post by nhandler on 2007-05-12
Well, I've gone through everything but the last step. I now need to get my hands on a joost invite so I can download it. Could anyone send me one (mrcheatr[at]gmail.com)

And is there any way to unapply a patch since patch 1 doesn't work with .9.37?

---

### Post by mikewitt on 2007-05-12
It works with 0.9.37. When that is put in the repository I'll update the instructions. The only difference is that you don't apply patch1.

---

### Post by 3rdalbum on 2007-05-12
I hope this means that the next version of Wine will include the patches you linked to!

---

### Post by mikewitt on 2007-05-12
I'm starting to think that a better way of doing this tutorial would be to use git, because it seems to be easier to maintain patches with git. The other advantage is that wine will always be as up-to-date as we want it; no waiting for repositories to update themselves. Of course the downside is that initial setup takes a bit longer, but updates are much faster; if I do this, I'll leave the old method up as well. 

Right now I'm working on putting the git tutorial together.

---

### Post by nhandler on 2007-05-12
Well either way, I still need to get my hands on a joost invite (mrcheatr[at]gmail.com)

---

### Post by mikewitt on 2007-05-12
I've updated the HOWTO now with a second way to remake wine; through git. The advantages to the second method are speed (it takes less time when you update wine later) and patches are applied more easily; as well as the fact that it is much more up to date. The disadvantage is that the source in the wine git tree may be unstable.

---

### Post by mkoby on 2007-05-12
ok, something is kind of up.

The first time I ran it, it worked flawlessly, the picture and audio were perfect.  Now everytime I run it, the video is slightly jumpy and the audio sounds like it's on a consistant fast forward.  

Pretty annoying.

Anyone else experiencing something similar?  Any fix?

---

### Post by mikewitt on 2007-05-12
I would try rebooting, that might help, because of the way that wine is forced to access the soundcard (depending on which soundcard it is, it locks access; even after unlocking access to other programs it can cause it to be sluggish.)

---

### Post by Aleck79 on 2007-05-13
is anyone else getting the following when trying to add this repository to the synaptic package manager?

"http://wine.budgetdedicated.com/apt/dists/feisty/Release: Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)"

that one if new to me

Thanks guys.

---

### Post by YokoZar on 2007-05-13
> **Aleck79 said:**
> is anyone else getting the following when trying to add this repository to the synaptic package manager?

"http://wine.budgetdedicated.com/apt/dists/feisty/Release: Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)"

that one if new to me

Thanks guys.Hey, I run the repository.  I've seen the error myself.

I'm not sure what is going on at the moment.

---

### Post by YokoZar on 2007-05-13
> **Aleck79 said:**
> is anyone else getting the following when trying to add this repository to the synaptic package manager?

"http://wine.budgetdedicated.com/apt/dists/feisty/Release: Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)"

that one if new to me

Thanks guys.Ok, after some amazing help from shawarma in IRC, everything is right again.  This error should be gone now.

---

### Post by Helskov on 2007-05-13
I have followed this guide and Joost works perfect. :guitar: 

[http://forums.gentoo.org/viewtopic-t-558046-highlight-joost.html](http://forums.gentoo.org/viewtopic-t-558046-highlight-joost.html)

---

### Post by Aleck79 on 2007-05-13
> **YokoZar said:**
> Ok, after some amazing help from shawarma in IRC, everything is right again.  This error should be gone now.

thanks for the reply :)

---

### Post by georgie on 2007-05-13
Hi folks

I initially tried the custom deb for wine posted earlier in the thread. I had the same complaint as some others (sound worked but with a black screen) - running feisty x86 on an AMD 64 box, with nvidia graphics (initially using   stock kernel, and restricted drivers)

So - here's what I did. I don't know which of these steps made it work - YMMV. The custom kernel was something I was doing for another purpose - and, tbh, forgot about this problem, then tried joost and it all worked)

0) followed steps above (wine deb, wincfg as suggested)
1) Built and installed latest 2.6.22-rc1 kernel
2) Installed latest beta of nvidia drivers [http://www.nvidia.com/object/linux_display_ia32_100.14.03.html](http://www.nvidia.com/object/linux_display_ia32_100.14.03.html)
3) Ran joost! Woo-hoo

Regards

Georgie

---

### Post by The Noble on 2007-05-13
I would greatly appreciate an invite as well. Please send to tehnoble(at)gmail(dot)com. Thanks for the guide! Also, what is the bandwidth required for a good viewing experience? I have a 1.5 Mb down/384 Kb up; will this be enough?

---

### Post by mikewitt on 2007-05-13
Did you install your new kernel from kernel.org? Or from another source?

---

### Post by Bastanteroma on 2007-05-13
I got a Joost install dialog, which warned me that I didn't have enough video ram (it sees 0 instead of 128).  I chose to proceed anyway, but the dialog disappeared, leaving just this output in the terminal.

r@r-desktop:~/Desktop$ wine JoostSetup-FriendsEdition-0.10.2.exe
err:ddraw:DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:actctx:ActivateActCtx 0x1622d0 0x34fe64
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library d3d9.dll (which is needed by L"C:\\Program Files\\Joost\\xulrunner\\tvpcsi.dll") not found
r@r-desktop:~/Desktop$ err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library d3d9.dll (which is needed by L"C:\\Program Files\\Joost\\xulrunner\\components\\gkwidget.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library d3d9.dll (which is needed by L"C:\\Program Files\\Joost\\xulrunner\\components\\tvpcsi.dll") not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ddbb958, overlapped 0x7ddbb93c): stub

Any ideas?

EDIT - On a retry the errors were different.  They had to do with OpenGL.  I'm using the nvidia binary driver, installed using Envy.

---

### Post by Bastanteroma on 2007-05-14
Tried again, using the posted binary, but the install window closed, leaving just the green virtual desktop.
This time the 3d worked a little, but it chose to simulate 64mb.  So maybe I need to compile on my system, but with 3d?

r@r-desktop:~/Desktop$ wine JoostSetup-FriendsEdition-0.10.2.exe
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x18b630) : stub, simulating 64MB for now, returning 64MB left
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:actctx:CreateActCtxW 0x34f7d4 00000088
fixme:actctx:ActivateActCtx 0xf00baa 0x34fe64
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ReleaseActCtx 0xf00baa
fixme:actctx:CreateActCtxW 0x34f7d4 00000088
fixme:actctx:ReleaseActCtx 0xf00baa
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x189068)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
r@r-desktop:~/Desktop$ fixme:iphlpapi:NotifyAddrChange (Handle 0x7ca64958, overlapped 0x7ca6493c): stub

---

### Post by Aleck79 on 2007-05-14
to the origional poster: might want to edit your post to make sure users remember that they need to run ./configure before they can "make depend && make" for the git version.

---

### Post by georgie on 2007-05-14
kernel.org  ([http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.22-rc1.gz](http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.22-rc1.gz))

then built kernel the debian way (make oldconfig, make menuconfig, make-kpkg modules-image kernel-image --initrd, dpkg -i *.deb)

Then installed the beta nvidia drivers

---

### Post by Aleck79 on 2007-05-14
> **georgie said:**
> 

Then installed the beta nvidia drivers

yeah same here... it seems that the non-beta drivers don't seem to want to show anything other than a black screen. however, with the beta drivers it all works pretty decent.

Has anyone been able to fullscreen this application without it all getting distorted and screwed up? Seems I can only seem to get it running at 800x600 resolution.

---

### Post by BionicSeahorse on 2007-05-14
> **methane said:**
> install the fonts like so:
```
sudo apt-get install msttcorefonts
```
and it works for me.

I already had the msttcorefonts package installed before I installed Wine/Joost, but this problem still came up. Any other ideas as to how to get readable text in Joost? I am running Feisty/AMD64 on dual monitors BTW.

---

### Post by searayman on 2007-05-14
hey worked great up untill i did this:

wine JoostSetup-FriendsEdition-0.10.2.exe

then a window opened and loaded and i saw liek a percentage clime up and then it just was like striped blue color and froze my whole computer.....

---

### Post by searayman on 2007-05-14
alright so i turned off compiz, andnow i actually got joost to work, then i sign in and everythign and i guesse i see the first navigation page for a few seconds then it goes black and i hear all this music and stuff and its choppy, and just a black screen?

---

### Post by mikewitt on 2007-05-14
What kind of graphics card do you have? If you have an ATi, it's not very well supported, if you have an nVidia, you can go grab the latest beta drivers, and that might help.

---

### Post by searayman on 2007-05-15
i hav envidia and have the latest drivers instaleld already....

---

### Post by Aleck79 on 2007-05-15
> **searayman said:**
> i hav envidia and have the latest drivers instaleld already....

there seems to be an issue with some nvidia cards, however the latest **BETA** drivers seem to fix it, for me at least.

---

### Post by BLTicklemonster on 2007-05-16
Looks like a lot of work. I just started getting in to tunapie and watch neat stuff on desync.com. I'll try this when I get time. Looks interesting.

---

### Post by foureight84 on 2007-05-16
anyone need and invite please pm me.

btw, in the tutorial, installing the linux headers is dependent of the kernel version. a better method is to do:

sudo apt-get install linux-headers-$(uname -r)

---

### Post by foureight84 on 2007-05-16
everything works up to the point where i try to run joost. i get a runtime error 

"R6031 - Attempt to initialize the CRT more than once. This indicates a bug in your application"

This is the error given by tvprunner.exe

---

### Post by ZeroXR on 2007-05-16
I followed the guide and all, I see the Joost splash screen, but on the log-in screen... I can't do anything. There is no blinking icon to input a user name and none of the buttons work when I click on them! Anyone want to help me out with this?

---

### Post by mikewitt on 2007-05-16
What is your setup? That is, the specs of your computer--we can work from there.

---

### Post by ZeroXR on 2007-05-17
Dell XPS m140
Pentium M (Centrino) 1.73 GHz
512mb DDR2 PC2-5300
Intel 915 Series Integrated Graphics Processor

---

### Post by toliman on 2007-05-18
i picked up envy for ATI's latest driver efforts, and i still having a bash at getting "beryl" to do it's magic with my Xpress 200M X700 laptop. week 1 of feisty is going quite well. until then, i thought i try to get some other apps working, photoshop, WoW, premiere and some dvd apps (CFosSpeed or even a heads-up network display would be good too. maybe a sexier gkrellm) 

. i had a look at the GIT repository, and have to say the codebase is just a lot less usable. i could not compile the GIT version, nor was i interested in finding a way to revert the date to one which it would compile. perhaps a linking/dependency bug on my side, no matter. i&#314;l stick with the deb svn + OSS patches copy for now.


are people still offering invites for joost ? i love to see what all the fuss is about. 

if you have the time, send one to [email]hugmyciaalien@gmail.com[/email] and i&#314;l send one along to whomever wants one. (passing forwards or some such)

---

### Post by Jiroo on 2007-05-18
> **Aleck79 said:**
> yeah same here... it seems that the non-beta drivers don't seem to want to show anything other than a black screen. however, with the beta drivers it all works pretty decent.

How can I do this? I tried [this howto]("http://ubuntuforums.org/showthread.php?t=296933"), but with the drivers linked by georgie, and I can't get it work. They are installed, but I have no acceleration... #-o Any clue?

> **toliman said:**
> 
are people still offering invites for joost ? i love to see what all the fuss is about. 
You can invite yourself: [http://joost.com/presents/gigaom-newteevee/]("http://joost.com/presents/gigaom-newteevee/")

---

### Post by capran on 2007-05-18
I followed directions, but having severe issues with Joost. Sound is stuttery/garbled/skipping, and no video at all.

The on-screen interface appeared once for me on my first try, but since it won't at show up at all, and whenever I log-in, I have to re-enter username/pw, and profile, and it immediately starts playing the same audio, but it's all craptastic. 

Ubuntu 7.04, 6800GT using Nvidia drivers acquired with Add/Remove, Creative Xmod USB sound, Intel Pentium D 805 @ 3 GHz, 2GB DDR400.

I tried using Metacity instead of Beryl, no change, as well as various sound settings in winecfg. I noticed sometimes OSS doesn't show a Wave Out, but when it does it shows USBMixer. The other drivers show something else, and don't seem to work. Emulation is on, and sample rate and bit width don't seem to help.

In terminal I get a ***lot*** of these type of messages:
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=1752 < primary_done=5280)

and

fixme:font:GetCharacterPlacementW flags 0x00000132 ignored

The numbers vary.

---

### Post by mikewitt on 2007-05-18
ZeroXR:
I know that Joost used to not work with the 915 chipset; that might be causing it, but I thought they fixed it. I can't seem to find the discussion of that, but the problem is that Joost wants to see a minimum of 512mb of ram, and another 32mb of video memory; the intel chipset uses regular ram as video memory, it just reserves some of it. Usually joost just ends in an error if this is the case, but I think the problem was that it didn't do this all the time; unfortunately I think they fixed it using driver access through a DLL, but wine doesn't use windows drivers, it uses the drivers of the host system.

Basically, I'm trying to say that I think it's your graphics card, and I don't know how to fix it.

---

### Post by tetralis on 2007-05-18
In my case the following font package installation was not enough:
```
sudo apt-get install msttcorefonts
```

However I could fix this by copying the installed mstt-fonts to the my private windows directory.
```
cp /usr/share/fonts/truetype/msttcorefonts/* ~/.wine/drive_c/windows/fonts/
```

---

### Post by tetralis on 2007-05-18
I have the same problem with black video screen after the login, but I can hear the sound.

My Graphic card is Nvidia 440 Go 64. The latest beta driver doesn't support mycard so I got to stick with older driver and a black screen.

At least I tried and I did what I could not run Run Joost on Windows (TM).

B.T.W. I never installed any qt related packages (listed in the HOWTO), I don't know if they had any effect but hey I am i GTK guy.

---

### Post by ZeroXR on 2007-05-18
mikewitt: That's unfortunate, as my desktop machine is in pieces... so definitely a blow to me being on a laptop. =(

---

### Post by Bullio on 2007-05-19
I followed your guide (which was great, btw) and installed everything just fine.  The only change I had to make was where it says "cd .wine/c_drive" I had to enter "cd .wine/drive_c".  For whatever reason mine was setup that way.  Anyway, I'm having the stuttering sound/audio problem as well.  Here are my specs.

Dell Inspiron 9300 (laptop)
1.73 Intel Pentium M
NVIDIA GeForce Go 6800 (driver version 1.0-9755)
Soundblaster Audigy 2 ZS (external sound card)
512mb RAM
Ubuntu 7.04

I do get picture, but the sound and video stutter.  I noticed this in the terminal while running Joost.  I don't know if it means anything (still a little new to the more advanced, technical aspects), but it didn't really look good.
```

fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:imm:ImmReleaseContext (0x1003e, 0x1631a8): stub
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
```
And so on.  Any thoughts?  I hope this is of some help to someone.

---

### Post by HuwSy on 2007-05-19
It doesnt seam to work for me, Iv followed the instructions and patched the version retreived by git and all.  The install sayed i have 0mb video memory but allowed me to continue.  Then running the app i get the following error message:

```
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library d3d9.dll (which is needed by L"C:\\Program Files\\Joost\\xulrunner\\tvpcsi.dll") not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x7de53958, overlapped 0x7de5393c): stub
```

d3d9.dll is in place, but wined3d.dll is nowhere on my system.  As for the whole OSS thing, i dont seam to have any optiuon to use anything else for some reason. Thankfully everything else i use wine for doesnt have a problem with oss. :)

---

### Post by HuwSy on 2007-05-19
btw i have recompiled remade deps and remade to no avail.

---

### Post by javaJake on 2007-05-19
Funny, because I have wined3d over here. I can see it compile as make runs.

If you are _sure_ you are compiling the right thing, do you want me to send you the DLL?

---

### Post by javaJake on 2007-05-19
> **mikewitt said:**
> ZeroXR:
I know that Joost used to not work with the 915 chipset; that might be causing it, but I thought they fixed it. I can't seem to find the discussion of that, but the problem is that Joost wants to see a minimum of 512mb of ram, and another 32mb of video memory; the intel chipset uses regular ram as video memory, it just reserves some of it. Usually joost just ends in an error if this is the case, but I think the problem was that it didn't do this all the time; unfortunately I think they fixed it using driver access through a DLL, but wine doesn't use windows drivers, it uses the drivers of the host system.

Basically, I'm trying to say that I think it's your graphics card, and I don't know how to fix it.

OK, I have this same graphics card as well. On a Dell computer. I've got 768 MB of memory.

This fixed DLL... can't we get it and paste it into wine? I've got an installation of Windows if that is what is needed.

---

### Post by Jiroo on 2007-05-19
> **Bullio said:**
> 
I do get picture, but the sound and video stutter.  I noticed this in the terminal while running Joost.  I don't know if it means anything (still a little new to the more advanced, technical aspects), but it didn't really look good.
```

fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=3230 < primary_done=3232)
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:imm:ImmReleaseContext (0x1003e, 0x1631a8): stub
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
```
And so on.  Any thoughts?  I hope this is of some help to someone.

The same problem here. I also had to change that thing about drive_c. I tried changing the wine config, but nothing changes... Any ideas?

---

### Post by javaJake on 2007-05-19
> **mikewitt said:**
> ZeroXR:
I know that Joost used to not work with the 915 chipset; that might be causing it, but I thought they fixed it. I can't seem to find the discussion of that, but the problem is that Joost wants to see a minimum of 512mb of ram, and another 32mb of video memory; the intel chipset uses regular ram as video memory, it just reserves some of it. Usually joost just ends in an error if this is the case, but I think the problem was that it didn't do this all the time; unfortunately I think they fixed it using driver access through a DLL, but wine doesn't use windows drivers, it uses the drivers of the host system.

Basically, I'm trying to say that I think it's your graphics card, and I don't know how to fix it.

OK, figured out what the problem is exactly, but they have only got bad hacks that solve it right now.

> <killertux> javaJake: problems is basicly that game takes all CPU away from the sounds... so it's priority problem.

This explains why tvprunner.exe and wineserver use up my CPU. I've tried various audio settings, but none seem to work. If anyone gets stuck with Joost running with this bug, especially after installation, run "killall -KILL tvprunner.exe" - it's the only way you'll get it to close.

For more information, visit these links:
[http://appdb.winehq.org/appview.php?iVersionId=7821](http://appdb.winehq.org/appview.php?iVersionId=7821)
[http://bugs.winehq.org/show_bug.cgi?id=1631](http://bugs.winehq.org/show_bug.cgi?id=1631)

So, to sum up, **this bug is known about already, but cannot be fixed without dramatic patches.**

I recommend that mikewitt post this, or a link to the information, on the HOWTO's Troubleshooting section so that we don't get more posts about this.

---

### Post by ZeroXR on 2007-05-19
Agreed there... More insight would very much be appreciated.

---

### Post by javaJake on 2007-05-19
OK, those who are dying to know what's being done to figure this out, I'm having a semi-active conversation with pijalu on the Gentoo forums who hosts another HOWTO on this same subject. His latest idea was here:
[http://forums.gentoo.org/viewtopic-p-4064490.html#4064456](http://forums.gentoo.org/viewtopic-p-4064490.html#4064456)

I'm trying this out now, will let you guys know how it goes.

---

### Post by HuwSy on 2007-05-19
> **javaJake said:**
> do you want me to send you the DLL?

I went and extracted it from the deb package a few pages back.  Possibly should be different but I got joost to load with it none the less.  Far to slow on this putter tho so il be awaiting the linux client currently in development.

---

### Post by javaJake on 2007-05-20
> **javaJake said:**
> OK, those who are dying to know what's being done to figure this out, I'm having a semi-active conversation with pijalu on the Gentoo forums who hosts another HOWTO on this same subject. His latest idea was here:
[http://forums.gentoo.org/viewtopic-p-4064490.html#4064456](http://forums.gentoo.org/viewtopic-p-4064490.html#4064456)

I'm trying this out now, will let you guys know how it goes.

No, this didn't work on my system. I get the same wierd screeching noises for a half of a second, and the same errors, etc., and it still won't run.

I'm personally going to wait at this point.

---

### Post by GoatTuber on 2007-05-22
After a bit of tweaking, I got Joost running somewhat acceptably. 

First I was getting the black screen after you login. This was caused by my NVidia driver, and was fixed by downloading NVidia's beta driver, then switching over to a new terminal window via Ctrl+Alt+F6, killing gdm, and then installing the driver as root.

Then I was getting the stuttering sound/video problem. I ran winecfg and went to the Audio tab, then I set the Default Sample Rate to 48000 and the Default Bits Per Sample to 16. While this isn't really a great fix, it plays smoothly about 95% of the time now. There may be a better way, but it's pretty much working now, and I really need some sleep.

Hope this helps anyone else that's frustrated with the sound problem.

Edit: I just wrote a small launcher script so I don't have to launch it from a terminal anymore. (attached)

---

### Post by Syosoft on 2007-05-22
Updated to the nvidia x86 linux beta drivers as suggested - was getting audio but black screen - it now works as expected. 

Nice little update driver howto: [http://ubuntuforums.org/showthread.php?t=296933](http://ubuntuforums.org/showthread.php?t=296933)

UI is a little slow, audio is a little choppy, CPU usage is pretty acceptable. Overall, it's a lot better than I expected from some of the posts in this thread.

---

### Post by phin on 2007-05-22
i take it i need to make a username under windows? when i click to make a new name it doesn't seem to do anything.

---

### Post by mikewitt on 2007-05-22
Yes and no. I found that even though nothing appeared to happen, the new username took, and I just had to hit cancel, then login with the created credentials. If that doesn't work, then yeah, you'll have to do it on a windows machine.

---

### Post by camerazn on 2007-05-22
I tried the first set of instructions, which worked up until 
dpkg-buildpackage -rfakeroot -uc -b

I deleted everything and tried the second set of instructions. This worked well up until winecfg, When I tried winecfg, the following error was thrown:

```
me@computer:~/wine-src/wine-git$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

Being a noob, and because it worked on the last two errors I encountered, I tried to apt-get X11. No such luck.

Any ideas?

Edit:
I'm running Kubuntu Feisty, but I'm not sure if that matters..

---

### Post by javaJake on 2007-05-22
> **GoatTuber said:**
> While this isn't really a great fix, it plays smoothly about 95% of the time now. There may be a better way, but it's pretty much working now, and I really need some sleep.

Actually, this is one of the fixes mentioned elsewhere (I believe in the Wine AppDB). Also, I got a stutter in my sound every 3 seconds in Windows using Joost, so you may be all set.

---

### Post by javaJake on 2007-05-22
> **camerazn said:**
> I deleted everything and tried the second set of instructions. This worked well up until winecfg, When I tried winecfg, the following error was thrown:

```
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

Being a noob, and because it worked on the last two errors I encountered, I tried to apt-get X11. No such luck.

Any ideas?

Did you run "sudo apt-get build-dep wine"? That is probably what you are missing. In case you didn't know, X11 is the software that manages the graphical part of your computer. It makes the mouse, windows, etc., appear. The X11 drivers are what talk to your video card, and tell it exactly how to display everything on your monitor.

---

### Post by iraubergeek on 2007-05-22
Awesome work! Would anyone mind sending an invite to iraubergeek at gmail dot com?

It is a good day for open source when this stuff works so well.

---

### Post by camerazn on 2007-05-22
> **javaJake said:**
> Did you run "sudo apt-get build-dep wine"? 

It certainly built. Now I just have to figure out why Joost is alternately crashing or unable to find my sound driver.  Thanks!

---

### Post by Jack33 on 2007-05-23
I have been having a real hard time with this on my kubuntu feisty, with intel centrino laptop. Basically I have tried the git method, the compile method, and trying one of the deb's posted here. all results in the same problem. I start wine xulrunner/tvprunner.exe application.ini , joost opens up, then goes to the login screen, i move my mouse and click in the area to place the cursor so i can type my user name. Right when i do click, Joost goes back to its normal loading screen and is frozen. Any help would be greatly appreciated.

Thanks

---

### Post by simone.brunozzi on 2007-05-23
Thanks a lot for this tutorial,
under Feisty everything (slowly) works.

Bye

---

### Post by javaJake on 2007-05-23
> **iraubergeek said:**
> Awesome work! Would anyone mind sending an invite to iraubergeek at gmail dot com?

It is a good day for open source when this stuff works so well.

You can get invites here, straight from Joost!
[http://joost.com/presents/gigaom-newteevee/](http://joost.com/presents/gigaom-newteevee/)

---

### Post by javaJake on 2007-05-23
> **Jack33 said:**
> I have been having a real hard time with this on my kubuntu feisty, with intel centrino laptop. Basically I have tried the git method, the compile method, and trying one of the deb's posted here. all results in the same problem. I start wine xulrunner/tvprunner.exe application.ini , joost opens up, then goes to the login screen, i move my mouse and click in the area to place the cursor so i can type my user name. Right when i do click, Joost goes back to its normal loading screen and is frozen. Any help would be greatly appreciated.

Thanks

Hmmm... this sounds (get it? "sound"s? yuck yuck...) like my problem, however, it _might not_ be related. Just pointing it out as a possibility.
[http://ubuntuforums.org/showthread.php?p=2683922#post2683922](http://ubuntuforums.org/showthread.php?p=2683922#post2683922)

---

### Post by seamuso on 2007-05-24
Joost invites ... [http://www.joost.com/presents/ars-technica/](http://www.joost.com/presents/ars-technica/)

Ars/joost have 10,000 that they are giving away .. first come first serve :p

---

### Post by freeforall079 on 2007-05-24
I am running Joost 0.10.3 on Linux Mint 2.2(Ubuntu edgy core) and it works fine for me.
I had to install the latest drivers from Nvidia( not the beta) to get the video to work. 
I had to install the fonts to read what was on the screen.
I also made a shortcut on my desktop to launch Joost.
Command: wine xulrunner/tvprunner.exe application.ini
Work Path: /home/YOURUSERNAME/.wine/drive_c/Program Files/Joost
For the work path you can right click and Show Hidden Folders when browsing. 

Here is the icon I used.
[http://rapidshare.com/files/33030183/joost.PNG.zip]("http://rapidshare.com/files/33030183/joost.PNG.zip")

To bad we can't run Joost natively yet. :-?
[[IMG]http://farm1.static.flickr.com/208/511317851_03d87cac41.jpg[/IMG]]("http://www.flickr.com/photo_zoom.gne?id=511317851&size=o")

---

### Post by digiplaya on 2007-05-24
Hmm! Why all the success I've been hearing when my system (7.04 feisty with wine 0.9.37-git) doesn't let me fill in login details on the first Joost screen when it launches? The screen (but not my system) is frozen!

I'm thinking either A: font problem since I get those font errors too, or B: X11 driver/display interaction with wine problem.

Anyone know about this? Cause I'd like any input. Remember, I have what I believe to be fully patched git-wine.

Screenshot of what Joost looks like running within Wine:

[IMG]http://i193.photobucket.com/albums/z1/digiplaya/joostunderwine.jpg[/IMG]

Console showing font problem:

[IMG]http://i193.photobucket.com/albums/z1/digiplaya/consoleofwine.jpg[/IMG]

Tom A.

---

### Post by Jack33 on 2007-05-24
digiplaya, i have the exact same problem. I wish i knew how to fix it :( ive installed the msttcorefonts too :(

---

### Post by freeforall079 on 2007-05-24
> **digiplaya said:**
> Hmm! Why all the success I've been hearing when my system (7.04 feisty with wine 0.9.37-git) doesn't let me fill in login details on the first Joost screen when it launches? The screen (but not my system) is frozen!

I'm thinking either A: font problem since I get those font errors too, or B: X11 driver/display interaction with wine problem.

Anyone know about this? Cause I'd like any input. Remember, I have what I believe to be fully patched git-wine.

Screenshot of what Joost looks like running within Wine:

[IMG]http://i193.photobucket.com/albums/z1/digiplaya/joostunderwine.jpg[/IMG]

Console showing font problem:

[IMG]http://i193.photobucket.com/albums/z1/digiplaya/consoleofwine.jpg[/IMG]

Tom A.

I get those error as well but I can type in every text field.
Did you install Joost 0.10.3 on top of Joost 0.10.2?
That is how I did it just ran the installer then it was working.
I had to use the latest Nvidia drivers and type this in console.
sudo apt-get install msttcorefonts
cp /usr/share/fonts/truetype/msttcorefonts/* ~/.wine/drive_c/windows/fonts/

---

### Post by visik7 on 2007-05-25
I got a crash from the joost crash reporting tool
but this after a long time where I see a 800x600 empty Wine Desktop windows
anyone could upload a tested deb of wine patched for joost ?

---

### Post by freeforall079 on 2007-05-25
> **visik7 said:**
> I got a crash from the joost crash reporting tool
but this after a long time where I see a 800x600 empty Wine Desktop windows
anyone could upload a tested deb of wine patched for joost ?

Ubuntu Edgy 6.10
[http://rapidshare.com/files/33164144/wine_0.9.36_winehq0_ubuntu_6.10-1_i386.deb]("http://rapidshare.com/files/33164144/wine_0.9.36_winehq0_ubuntu_6.10-1_i386.deb")
 
Ubuntu Feisty 7.04
[http://rapidshare.com/files/33165145/wine_0.9.36_winehq0_ubuntu_7.04-3_i386.deb]("http://rapidshare.com/files/33165145/wine_0.9.36_winehq0_ubuntu_7.04-3_i386.deb")

I have only tested the Ubuntu Edgy version.
I get the errors above but runs fine no video or audio choppiness.

---

### Post by visik7 on 2007-05-25
> **freeforall079 said:**
> Ubuntu Edgy 6.10
[http://rapidshare.com/files/33164144/wine_0.9.36_winehq0_ubuntu_6.10-1_i386.deb]("http://rapidshare.com/files/33164144/wine_0.9.36_winehq0_ubuntu_6.10-1_i386.deb")
 
Ubuntu Feisty 7.04
[http://rapidshare.com/files/33165145/wine_0.9.36_winehq0_ubuntu_7.04-3_i386.deb]("http://rapidshare.com/files/33165145/wine_0.9.36_winehq0_ubuntu_7.04-3_i386.deb")

I have only tested the Ubuntu Edgy version.
I get the errors above but runs fine no video or audio choppiness.

solved thanks 

there was a problem with wine_doors and this settings they conflicts and preclude joost to run 
maybe is usefull for someone other

---

### Post by aidin on 2007-05-26
BADASS! 

...now does anyone have an invite for me? :( 
i cant do much without that...

--edited--

much appreciated...

--aidin

---

### Post by javaJake on 2007-05-26
> **aidin said:**
> BADASS! 

...now does anyone have an invite for me? :( 
i cant do much without that...

aidinb at gmail


much appreciated...

--aidin

[http://joost.com/presents/gigaom-newteevee/](http://joost.com/presents/gigaom-newteevee/)
Joost and someone else are giving out free invites.

mikewitt, I suggest you add this to your HOWTO so we don't get more of these questions. :)

---

### Post by johnny1978 on 2007-05-26
Hello,

Everything installs fine, but as soon as I try to start joost, i get a runtime error. This was also posted before, but since I haven't been able to find an answer I am posting it again:
the error:

C:\Program Files\Joost\xulrunner\tvprunner.exe

R6031
-Attempt to initialize the CRT more than once.
This indicates a bug in your application.

---

### Post by freeforall079 on 2007-05-27
If Joost 0.10.3 doesn't work for you download Joost 0.10.2.
_Remember to **delete all **of the **Joost** Folders 1st._
[http://rapidshare.com/files/33763874/JoostSetup-FriendsEdition-0.10.2.exe.html]("http://rapidshare.com/files/33763874/JoostSetup-FriendsEdition-0.10.2.exe.html")
/home/USERNAME/.wine/drive_c/windows/profiles/USERNAME/Application Data/
/home/USERNAME/.wine/drive_c/windows/profiles/USERNAME/Local Settings/Application Data/

---

### Post by csulok on 2007-05-29
how do i remove the 272mb -s of unnecesarry files after compiling?
sudo apt-get build-dep wine <- this is the line that downloads and unpacks them.

---

### Post by airtonix on 2007-05-29
hehe this is a xul app but they make you run it in linux under wine...go figure?

---

### Post by JeanJean on 2007-05-31
When I add wine responsity to my kist and I try to update, I've get this error

```
W: GPG error: http://wine.budgetdedicated.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

```

I just ubuntu Fiesty Fawn, how can fix this ?

---

### Post by deadite66 on 2007-05-31
> **JeanJean said:**
> When I add wine responsity to my kist and I try to update, I've get this error

```
W: GPG error: http://wine.budgetdedicated.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

```

I just ubuntu Fiesty Fawn, how can fix this ?

run
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by bwobbones on 2007-05-31
How awesome is that.  Great HOWTO.  Is there any way that you could have a greater screen resolution?  Or maybe even (gasp!) fullscreen?  Sorry if this is a silly question, still new to wine etc...

---

### Post by freeforall079 on 2007-05-31
> **bwobbones said:**
> How awesome is that.  Great HOWTO.  Is there any way that you could have a greater screen resolution?  Or maybe even (gasp!) fullscreen?  Sorry if this is a silly question, still new to wine etc...

I don't think we will get fullscreen until Joost releases a Linux version.
[http://joost.com/forums/p/2007/03/will-there-be-a-joost-client-for-linux/]("http://joost.com/forums/p/2007/03/will-there-be-a-joost-client-for-linux/") 
What's taking them so long though? 
Have they even started?
](*,):confused:

I also have an Icon for Joost. I use this for a shortcut on the desktop.
[http://rapidshare.com/files/34486832/tvp.png]("http://rapidshare.com/files/34486832/tvp.png")

---

### Post by freeforall079 on 2007-06-02
Has anyone gotten this to work under [Wine 0.9.38]("http://www.winehq.org/?announce=0.9.38").
And if so what did you have to do.
Thanks for any Info.

---

### Post by mikewitt on 2007-06-02
It appears that all of the patches are the same. I'm in the process of rebuilding wine using the git method right now. Wine 0.9.38 hasn't hit the repo yet, my guess would be tomorrow (that seems to be their turnaround time, 1-2 days). I'll update the tutorial to reflect changes (if any) when the most recent version hits the repo.

---

### Post by forevertheuni on 2007-06-02
I followed the howto..with ALSA it works ok with sound

---

### Post by javaJake on 2007-06-02
> **freeforall079 said:**
> I don't think we will get fullscreen until Joost releases a Linux version.
[http://joost.com/forums/p/2007/03/will-there-be-a-joost-client-for-linux/]("http://joost.com/forums/p/2007/03/will-there-be-a-joost-client-for-linux/") 
What's taking them so long though? 
Have they even started?
](*,):confused:

I also have an Icon for Joost. I use this for a shortcut on the desktop.
[http://rapidshare.com/files/34486832/tvp.png]("http://rapidshare.com/files/34486832/tvp.png")

I got an e-mail from their tech-support: 

> As a Ubuntu users myself the only thing I can tell you is that we are
working on a Linux version of Joost, can't disclose on how far in
development we are so I can't give you a date for when it will be ready.

*cut information out where he/she linked here...*
 
Please be patient! A Linux version of Joost will be available in the
future..developing it just takes time ..

I can't wait. :)

---

### Post by mikewitt on 2007-06-02
> **mikewitt said:**
> It appears that all of the patches are the same. I'm in the process of rebuilding wine using the git method right now. Wine 0.9.38 hasn't hit the repo yet, my guess would be tomorrow (that seems to be their turnaround time, 1-2 days). I'll update the tutorial to reflect changes (if any) when the most recent version hits the repo.
OK. It does ***_NOT_*** work with Wine 0.9.38. Which kinda sucks. I'll do my best to figure out what's wrong, but i don't entirely know what could be causing it. 

I'll post status updates as I work on it.

---

### Post by mikewitt on 2007-06-02
> **mikewitt said:**
> OK. It does ***_NOT_*** work with Wine 0.9.38. Which kinda sucks. I'll do my best to figure out what's wrong, but i don't entirely know what could be causing it. 

I'll post status updates as I work on it.
I spoke too soon. It still does work, but it takes a LOT longer to start (try 5-6 minutes). Note that I am using a code snapshout though, so it could be a problem with the snapshot, and not the final release of wine. 

Also, the new wine (0.9.38[COLOR="Black"])[/COLOR] has now hit the repo. I'll post results about that in a few hours, when I get the chance to build it.

---

### Post by scyleung on 2007-06-02
When I type > sudo apt-get build-dep wine in the console, it download something 100MB, is this normal?

---

### Post by freeforall079 on 2007-06-02
> **mikewitt said:**
> I spoke too soon. It still does work, but it takes a LOT longer to start (try 5-6 minutes). Note that I am using a code snapshout though, so it could be a problem with the snapshot, and not the final release of wine. 

Also, the new wine (0.9.38[COLOR="Black"])[/COLOR] has now hit the repo. I'll post results about that in a few hours, when I get the chance to build it.
Thanks for the update.
I wonder why it still doesn't work with the original WINE with no compiling. 


> **javaJake said:**
> I got an e-mail from their tech-support: 



I can't wait. :)

I hope this is true. :-k
At Joost the only thing they have said is they will have a Joost for Linux.
I have been there for awhile and no info that they even started to make it yet.
I thought they still didn't decide on how it was going to be installed.
They could at least make page that has the requirements.  8-)

---

### Post by hnic on 2007-06-03
Hello everyone

I just installed Joost and everything went well but when i lauch Joost and it comes up with the Username and password i cant type anything Please help 

Thanks
HNic

---

### Post by mikewitt on 2007-06-03
> **mikewitt said:**
> I spoke too soon. It still does work, but it takes a LOT longer to start (try 5-6 minutes). Note that I am using a code snapshout though, so it could be a problem with the snapshot, and not the final release of wine. 

Also, the new wine (0.9.38[COLOR="Black"])[/COLOR] has now hit the repo. I'll post results about that in a few hours, when I get the chance to build it.
With the version of wine in the repo (0.9.38 ), Joost will run, although it does appear to be slower (than previous versions of wine).

---

### Post by malcam on 2007-06-03
Excellent tutorial. Got it working with stuttering audio. I set the sample rate and bits per sample to maximum, then I turned off vertex/pixel shading in the graphics tab. Now works fairly well, with only slight audio breaks. Hope they release a Linux version soon.

---

### Post by freeforall079 on 2007-06-03
> **mikewitt said:**
> With the version of wine in the repo (0.9.38 ), Joost will run, although it does appear to be slower (than previous versions of wine).

Does this happen every time Joost is opened?
If not it might just be Joost updating Channel Info or adding new channels to your client.
Or it might be that the severs are being updated and some are down at the moment.
So it takes longer to get an answer that your Joost has the correct security key.

Well I compiled the new version of WINE but it comes up with these errors.
wine: creating configuration directory '/home/freeforall/.wine'...
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
wine: '/home/freeforall/.wine' created successfully.

What did I do wrong?
**[SIZE="4"]Update[/SIZE]**
Ok I remove wine and it's directories.
Then I edited my sources.lst and # out everything but the
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
Line and saved my sources.lst
Then I recompiled wine and now it's working.

> **mikewitt said:**
> With the version of wine in the repo (0.9.38 ), Joost will run, although it does appear to be slower (than previous versions of wine).

It doesn't for me I just opened Joost with my shortcut on the desktop and took like 10 secs to load.
Also don't forget to go to **My Joost** --> **Widget Menu** --> **Advanced Settings **and **uncheck Leave on standby** and click _save settings_
Now exit Joost by Clicking **Quit Joost** or the Power Button.

Here is my compiled wine [http://rapidshare.com/files/35118274/wine_0.9.38_winehq0_ubuntu_7.04-1_i386.deb]("http://rapidshare.com/files/35118274/wine_0.9.38_winehq0_ubuntu_7.04-1_i386.deb")
With this script made by GoatTuber [http://rapidshare.com/files/34467945/Joost.sh]("http://rapidshare.com/files/34467945/Joost.sh")
in the /usr/bin/
And this Icon [http://rapidshare.com/files/34486832/tvp.png]("http://rapidshare.com/files/34486832/tvp.png")
I have a shortcut on the desktop with the command of Joost.sh that launches Joost.

I get these errors while exiting.
```
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
fixme:shell:DllCanUnloadNow stub
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

Still runs Joost and has an audio crackling sound like before.

---

### Post by mathiaschulze on 2007-06-05
> **hnic said:**
> Hello everyone

I just installed Joost and everything went well but when i lauch Joost and it comes up with the Username and password i cant type anything Please help 

Thanks
HNic

I have exactly the same problem. In the terminal I get error messages like "fixme:font:GetCharacterPlacementW flags 0x00000132 ignored".

---

### Post by freeforall079 on 2007-06-06
> **mathiaschulze said:**
> I have exactly the same problem. In the terminal I get error messages like "fixme:font:GetCharacterPlacementW flags 0x00000132 ignored".

I get that all the time but I'm able to type in every text field.
I have gotten this with 0.9.36 - 0.9.38 (Joost 0.10.2 - 0.10.3) and still had no problems typing.
Even with Beryl I can type.

---

### Post by Alessiogian on 2007-06-06
Hi,

I have a problem with the pubblic key of the repo.

Can you help me?

---

### Post by freeforall079 on 2007-06-06
> **Alessiogian said:**
> Hi,

I have a problem with the pubblic key of the repo.

Can you help me?
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
Is the command for the key.

---

### Post by Alessiogian on 2007-06-07
> **freeforall079 said:**
> ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
Is the command for the key.

Really Thanks.

But why you don't put it in the guide?

---

### Post by javaJake on 2007-06-07
> **hnic said:**
> Hello everyone

I just installed Joost and everything went well but when i lauch Joost and it comes up with the Username and password i cant type anything Please help 

Thanks
HNic

If your CPU is being used to its max while the window is frozen, see the "Troubleshooting" section of the HOWTO, and go to the question "Q) What should I do if Joost is using all my CPU?". I have the same issue myself.

---

### Post by Swizzler121 on 2007-06-08
> **pingpongboss said:**
> [IMG]http://i25.photobucket.com/albums/c80/pingpongboss/ImageBot/Screenshot-Winedesktop.png[/IMG]

I keep getting that screen even though I followed your directions on what to set on the Audio page for winecfg.

edit: this is what I get with version 0.9.2
[IMG]http://i25.photobucket.com/albums/c80/pingpongboss/ImageBot/Screenshot-Winedesktop-1.png[/IMG]

I'm getting the same error as him, how do i fix it?

---

### Post by freeforall079 on 2007-06-08
> **Swizzler121 said:**
> I'm getting the same error as him, how do i fix it?

Try Alsa driver instead of OSS in winecfg.

---

### Post by Swizzler121 on 2007-06-08
> **freeforall079 said:**
> Try Alsa driver instead of OSS in winecfg.

hmm, tried that, no luck.

this is the errors the terminal puts out:
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored

seems to be something with the fonts, but i'm seeing everything fine, so idk...

---

### Post by bofh80 on 2007-06-11
Hi there,

After waiting and waiting :) then forgetting and rechecking, i noticed you'd updated for the 0.38 code.
i'd already enabled the repository and installed the 0.38 deb availble from fan and got no where....
So i blanked everything and followed your great guide. it really does make things simpler than i thought it would be . . . 

Unfortunatley, i get this :
[ATTACH]35049[/ATTACH]

the console says:

~/.wine/drive_c/Program Files/Joost$ wine xulrunner/tvprunner.exe application.ini 
fixme:iphlpapi:NotifyAddrChange (Handle 0x7baed958, overlapped 0x7baed93c): stub
fixme:keyboard:BlockInput (1): stub
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignoredfixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:font:GetCharacterPlacementW flags 0x00000132 ignoredfixme:shell:DllCanUnloadNow stub

-----------------
And that's it. i've tried joost 10.2 and 10.3 rename my .wine before i ran the guide, and uninstalled wine ;with synaptic choosing complete removal.
I removed the application data settings for joost as well as the othervarious bits after using it's uninstall program, to change versions......i've done all the settings in winecfg as well.

Any help really appreciated . . . .

bofh80 .

---

### Post by mikewitt on 2007-06-11
Could you run Joost this way and then post the output: (It gets rid of all those 'fixme:' errors, and instead only shows true errors)
```
WINEDEBUG=fixme-all wine xulrunner/tvprunner.exe application.ini
```

---

### Post by bofh80 on 2007-06-11
Hi there Mike thanks for the reply.
Unfortunaltey that produced no output at all, the Joost diaglog came up the same as before, but no errors on the command line at all :(
Is there a way to increase the debugging value?
Many thanks for your help/#

edit

i tried with winedbg, and it quite quickly just started doing this:

First chance exception: page fault on read access to 0x01b60020 in 32-bit code (0x00f6f01a).
the memory values appear to change everytime, i'm really not that experienced with winedbg.....
-------------
also i should note that everytime i've installed Wine, (from anywhere it seems) i get this msg :
ldconfig: /usr/lib/libphysfs-1.0.so.1 is not a symbolic link

---

### Post by mikewitt on 2007-06-12
If there's no output when turning fixme errors off, then it's (most likely) a problem with the hardware configuration, or some software thing (within joost, not wine). The command I told you to run just temporarily turns off output of fixme errors, which are (99.9%) non-fatal.

---

### Post by Mirar on 2007-06-14
Excellent guide, thank you.

I seem to have some issues, though. 

The biggest is that Joost doesn't seem to be able to download any video data. I can choose channel and program and everything, but no video ever comes up. Anyone has any idea how to debug that? I don't get much in the way of errors. Maybe someone can show me a netstat over Joost to see if I have all the proper network connections running or give me a hint on how to trace what's going wrong? Or a link to some wine-network-and-sound-testing-software?

The second problem is that I don't get any sounds. Joost never complains about that either (neither OSS nor Alsa gives any complaints; turning off emulation does). But that might follow from the fact I don't get any video either - don't know if it has default sounds that plays anyway...

Joost starts fine within seconds, by the way. No five minute wait. But no video stream, even in hours...

Wine 0.9.38, Joost 10.4.
I would like to try with Joost 10.3, anyone has that somewhere still? 

(Also, 10.4 works fine on a windows computer on the same network.)

/Mirar

[SIZE="1"]wine output:
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cbae958, overlapped 0x7cbae93c): stub
fixme:keyboard:BlockInput (1): stub
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
[...N times...]
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x174ac00) : stub, simulati
ng 64MB for now, returning 64MB left
fixme:font:GetCharacterPlacementW flags 0x00000132 ignored
[...inf times...]
[/SIZE]

---

### Post by NfF on 2007-06-14
> **mikewitt said:**
> You need to recompile wine for this to work, and it takes a while. If you're afraid of doing this, you probably want to stop now.

***_[SIZE="5"][COLOR="Red"]STOP ASKING FOR INVITES![/COLOR] Go here instead: [http://joost.com/presents/gigaom-newteevee/]("http://joost.com/presents/gigaom-newteevee/")[/SIZE]_***

This is for Ubuntu 7.04

First you need to get a few things ready for the install:

first and foremost, download a copy of the most recent Joost program from Joost

open Synaptic, click on "Settings --> Repositories" Click on the "3rd Party Tab" click "Add" at the bottom. In the box that comes up, type this (or copy it):
```
deb-src http://wine.budgetdedicated.com/apt feisty main
```

Click "Ok" and then close the settings window. After the popup that comes up, telling you that you need to hit the "Reload" button, hit the "Reload" button. Close synaptic.

In a console, type:
```
sudo apt-get build-dep wine
```
Now we're going to get the build things. You don't need this step if you've compiled things before:
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
Answer Y to any prompts that come up. (Thanks to foureight84 for suggesting $(uname -r))

Now get some dependencies:
```

sudo apt-get install fakeroot libasound2-dev libaudiofile-dev libesd0-dev libaudio-dev libcapi20-dev liblcms1-dev libcupsys2-dev libsane-dev libhal-dev libdbus-1-dev freeglut3-dev libc6-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libglib1.2-dev libglib2.0-dev libgpg-error-dev libice-dev libieee1284-3-dev libjpeg62-dev libldap2-dev libltdl3-dev libmad0-dev libmng-dev libncurses5-dev libogg-dev libopencdk8-dev libpng12-dev libqt3-mt-dev libsm-dev libusb-dev libvorbis-dev libx11-dev libxcursor-dev libxext-dev libxft-dev libxi-dev libxml2-dev libxmu-dev libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev render-dev unixodbc-dev x-dev zlib1g-dev xlibs-dev libxxf86dga-dev libxxf86vm-dev libjack0.100.0-dev libicu34-dev libungif4-dev libssl-dev
```

Now make a working directory:
```
mkdir wine-src
cd wine-src
```

and get the Wine source:
```
apt-get source wine
```

now cd into the directory that was just created by apt:
```
cd wine-0.9.38~winehq0~ubuntu~7.04
```

and run this command to download the patches necessary to run Joost: (I'm hosting these patches, because they're easire to get this way, rather than from the appdb site)
```
wget http://witt.michael.googlepages.com/patch2.patch http://witt.michael.googlepages.com/patch3.patch http://witt.michael.googlepages.com/patch4.patch http://witt.michael.googlepages.com/patch5.patch http://witt.michael.googlepages.com/patch6.patch http://witt.michael.googlepages.com/patch7.patch http://witt.michael.googlepages.com/patch8.patch
```

now we need to patch using the files we downloaded:
```
patch -p1 < patch2.patch
patch -p1 < patch3.patch
patch -p1 < patch4.patch
patch -p1 < patch5.patch
patch -p1 < patch6.patch
patch -p1 < patch7.patch
patch -p1 < patch8.patch
```

and now that we've patched everything (everything should have gone smoothly) type:
```
dpkg-buildpackage -rfakeroot -uc -b
```
This will take a LONG time (an hour or so)

after it's done, assuming no errors,
```
cd ..
```
and install:
```
sudo dpkg -i wine_0.9.38~winehq0~ubuntu~7.04-1_i386.deb
```

after that's done, type:
```
winecfg
```
Make sure that "Windows XP appears in the dropdown on the first page at the bottom. If it doesn't, select it.
Next click on the audio tab. Make sure that only "OSS Driver" is checked. At the bottom, turn DirectSound Hardware Acceleration to "Emulated" and check the checkbox that says "Driver Emulation"
Now go into the graphics tab, and check "Emulate a virtual desktop" and enter a size of 800x600. Uncheck "Allow the window manager to control windows"
Click "Apply" then "Ok"

**Now to install joost:**
```
cd
cd Desktop
wine JoostSetup-FriendsEdition-0.10.4.exe
```
and follow the prompts

To start Joost type:
```
cd
cd .wine/c_drive
cd "Program Files"
cd Joost
```

Then to start joost, type:
```
wine xulrunner/tvprunner.exe application.ini
```
If you don't like all those 'fixme' errors, which mean nothing to most people, run the command like this:
```
WINEDEBUG=fixme-all wine xulrunner/tvprunner.exe application.ini
```

It may take a couple of minutes, but you should eventually see a splash then a login window. Note that if you need to create a username (not an account, but a name associated with an email), you need to do that. When you click OK after doing what it says, you will just see in red letters "true" appear. It will not progress, but this is Ok, joost still got the info. Click Cancel, then type the name you just created.

You should now have Joost up and running. (Troubleshooting section at bottom) :popcorn:


=== METHOD 2 === GIT ===

This is a secondary method, using git to get the latest and greatest wine (which is not dependent upon a repo). We get the latest code (which might be unstable) and patch it. It is also faster when upgrading, as the files that are unchanged do not need to be recompiled.

**[COLOR="Red"]WARNING:[/COLOR] This method uses code snapshots, WHICH MAY BE UNSTABLE. USE AT YOUR OWN RISK.**

Step 1:
First, download and install git (note that the version that is in the apt repo for dapper will NOT work; it's too old)
```
sudo apt-get install cogito
```
**NOTE: If you try and download the program "git" from the apt repo, it will cause problems. It is not the same git we need.**

2:
Make and go into the wine-src folder under home.
```
cd
mkdir wine-src
cd wine-src
```

3:
Use git to fetch the latest wine-source, then go into the directory.
```
git clone git://source.winehq.org/git/wine.git wine-git
cd wine-git
```
The git command will take a while. Just go grab something to eat while you wait.

4:
Use wget to download the patches: (As of 0.9.37 patch1.patch is no longer required, however all of the others are.)
```
wget http://witt.michael.googlepages.com/patch2.patch http://witt.michael.googlepages.com/patch3.patch http://witt.michael.googlepages.com/patch4.patch http://witt.michael.googlepages.com/patch5.patch http://witt.michael.googlepages.com/patch6.patch http://witt.michael.googlepages.com/patch7.patch http://witt.michael.googlepages.com/patch8.patch
```

5:
Apply patches:
```
patch -p1 < patch2.patch
patch -p1 < patch3.patch
patch -p1 < patch4.patch
patch -p1 < patch5.patch
patch -p1 < patch6.patch
patch -p1 < patch7.patch
patch -p1 < patch8.patch
```

6:
Commit patches to our branch.
```
git commit -a
```
Vi(m) will come up (which I hate) and you will need to know a few commands.
All command sequences start with a colon (Shift+;). They end when you press enter.
To exit, use "quit" if you've changed something and want to quit without saving, use "quit!"
To save, use the command "write"

For the commits, uncomment the names of all of the first set of files. (they should all end with ".c")

7:
Make wine.
```
./configure
make depend && make
```
This will take a long time.

8:
Uninstall any previous versions of wine
[INDENT]If you used the instructions above, type ```
sudo dpkg remove wine
```
If you used apt to install wine, type ```
sudo apt-get remove wine
```
If you installed from source, cd into that directory, and type ```
sudo make uninstall
```[/INDENT]

9:
Install the new version of wine.
```
sudo make install
```

10:
Check that wine was installed correctly
```
wine --version
```
This should show something like 'wine-0.9.37-g8d159b7'

11:
Continue by using the instructions above to install and run Joost.

**How to use git to update the source (and save a lot of time recompiling):**
1:
Type 
```
git fetch
git rebase origin
```

2:
Run make again:
```
make depend && make
```
This shouldn't take long, as most of the files are unchanged.

3:
Reinstall.
```
sudo make install
```

**[COLOR="Red"][SIZE="5"]Troubleshooting common problems (FAQ):[/SIZE][/COLOR]**
Q) Video doesn't work
A) If you have an nVidia card, try installing the latest beta drivers (for an x86: [http://www.nvidia.com/object/linux_display_ia32_100.14.03.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.03.html"))  (Thanks to georgie for that answer)
 For a tutorial:[http://ubuntuforums.org/showthread.php?t=296933](http://ubuntuforums.org/showthread.php?t=296933)(Thanks Syosoft)
Also, if you use Beryl, set it to metacity, it will run better.
A2) Make sure that "Virtual Desktop" is checked, with a resoulution of 800x600. In more recent versions, unchecking Virtual Desktop (so NONE of the options are checked) sometimes works (and sometimes doesn't). It will play in fulscreen if it works, but can freeze if it doesn't. If it freezes, just hit Ctrl+Alt+Backspace and it will restart GDM (but you'll loose any work you may have done in the background.

Q) Sound doesn't work:
A) In winecfg, under the audio tab, try selecting different drivers; one should work. Also, make sure that "Hardware Acceleration" is set to Emulation, and not any of the other options. Also try checking the box that says "Emulate Sound driver)

Q) It won't start.
A) Go into a console and type 'wine --version' If it says anything less than 0.9.36 (if you've done it recently it should say 0.9.37) then you haven't installed your new wine, or an older version is taking control. Type "sudo apt-get remove wine" and then cd into your wine directory, and and install using the directions above. Then when you type 'wine --version' it should come up with 0.9.37. If it says that and still won't run, make sure you've patched everything (patches 2-8). If it says 'cannot find wine' then just cd into your source directory, and install using the instructions above.

Q) Fonts don't work.
A) Try running this: ```
sudo apt-get install msttcorefonts
``` (Thanks methane)
If that doesn't work, after installing msttcorefonts, run the command: ```
cp /usr/share/fonts/truetype/msttcorefonts/* ~/.wine/drive_c/windows/fonts/
``` (Thanks tetralis)

Q) Should I use sudo when running wine?
A) Never.

Q) What should I do if Joost is using all my CPU?


***** CHANGELOG *****
May 11, 2007: Initaial Revision
May 12, 2007: Added git method, updated to reflect newest version of wine.
May 14, 2007: Added ./configure to git method because of a suggestion. Also added Troubleshooting/FAQ section.
May 16, 2007: Fixed linux-headers section.
May 20, 2007: Added more info to troubleshooting.
May 22, 2007: More info added.
May 24, 2007: Joost has been updated! Brought tutorial up to speed.
May 26, 2007: See message at the top.
June 3, 2007: Changed to reflect Version 0.9.38 of wine.
June 9, 2007: Updated to reflect Joost 0.10.4
June 12, 2007: Added method to get rid of 'fixme' errors.


Aah! thx for this guide.

IVE GOT A DEEP DEEP PROBLEM, WHICH IS THINK IS RELATED TO THE HD AND THE LIVE CD
AFTER INSTALLING UBUNTU..I WENT ONLINE ON MY LAPTOP(WINDOWS XP),CUZ THERE IS NO INTERNET ON THE UBUNTU PC. I DOWNLOADED THE NDISWRAPPER, BURNED THE FILE TO THE CD,  AND POP IT IN MY UBUNTU PC.THANKFULLY IT COULD DETECT THE FILE

SO I FOLLOWED THE GUIDE TO INSTALL NDISWRAPPER
AND THIS IS WHAT I TYPED AND THE RESULT

1.sudo su(to become root)
2.then i typed sudo apt-get install ndiswrapper
3.then all it started searching for the file
4.WHAT SHOCKED ME WAS THAT IT COULDNT FIND THE FILE
THE ERROR SAYS-E: couldnt read or find ndiswrapper.BUT IT WAS RIGHT ON MY DESKTOP SITTING INFRONT OF ME.
5.THINKING THAT I MISSED SOMETHING.I POPPED IN MY LIVE CD, AND installed everything.
6. the error msg E:couldnt read or find ndiswrapper.

---

### Post by trippinnik on 2007-06-14
> **NfF said:**
> Aah! thx for this guide.

IVE GOT A DEEP DEEP PROBLEM, WHICH IS THINK IS RELATED TO THE HD AND THE LIVE CD
AFTER INSTALLING UBUNTU..I WENT ONLINE ON MY LAPTOP(WINDOWS XP),CUZ THERE IS NO INTERNET ON THE UBUNTU PC. I DOWNLOADED THE NDISWRAPPER, BURNED THE FILE TO THE CD,  AND POP IT IN MY UBUNTU PC.THANKFULLY IT COULD DETECT THE FILE

SO I FOLLOWED THE GUIDE TO INSTALL NDISWRAPPER
AND THIS IS WHAT I TYPED AND THE RESULT

1.sudo su(to become root)
2.then i typed sudo apt-get install ndiswrapper
3.then all it started searching for the file
4.WHAT SHOCKED ME WAS THAT IT COULDNT FIND THE FILE
THE ERROR SAYS-E: couldnt read or find ndiswrapper.BUT IT WAS RIGHT ON MY DESKTOP SITTING INFRONT OF ME.
5.THINKING THAT I MISSED SOMETHING.I POPPED IN MY LIVE CD, AND installed everything.
6. the error msg E:couldnt read or find ndiswrapper.

This is really off topic.  You should post this somewhere else.

---

### Post by Mirar on 2007-06-15
> **Mirar said:**
> The biggest is that Joost doesn't seem to be able to download any video data. I can choose channel and program and everything, but no video ever comes up.

Thinking this was what you meant with "no video", maybe, perhaps, I upgraded the nVidia driver to the latest beta - no change. I'd really like to hear some ideas... :p
It *feels* like a network problem.

/Mirar

---

### Post by flawedprefect on 2007-06-15
I get a "Runtime Error!

Program C:\Program Files\Joost\xulrunner\tvprunner.exe

R6031
-Attempt to initialize the CRT more than once.
This indicaes a bug in your application

Any thoughts?

THis is when running either of the above commands to initialize Joost.

---

### Post by mikewitt on 2007-06-15
That is completely unrelated, and don't quote the guide, it's really long.

---

### Post by mikewitt on 2007-06-15
If it is a network problem, Wine 0.9.39 might have adressed it (there are supposedly lots of winsock bugfixes). When I said no video, I meant that no video was showing up (which could be any of a number of problems), which is commonly caused by driver issues, however not always.

---

### Post by mikewitt on 2007-06-16
I've finished installing wine 0.9.39 and Joost seems to have stopped working (and this time I think I really mean it).

For me at least, Joost will launch (and faster than it ever has) and I'll see the splash, then the screen goes black, and nothing, eventually erroring out/crashing.

**If ANYONE gets Joost working with 0.9.39, please tell me, either in this forum post, or by PM.**

PS: What's up with the repo? when I run 'apt-get source wine' it grabs wine 0.9.33, not 0.9.38/9. (Note that I normally use the git method, not the repo usually)

---

### Post by Najand on 2007-06-17
Nice. If someone needs invitations, send private messages to me.

---

### Post by crazy25000 on 2007-06-20
Hello, 

I have a joost invite, if you are interested please send me a message.

---

### Post by variableenigma on 2007-06-23
It seems that everything has worked until I get to the very end when I'm trying to actually run Joost. It cannot find my Wine directory. So when I type "cd .wine/c_drive" it says
"bash: cd: .wine/c_drive: No such file or directory".

I'm not sure why this is happening or what I should do about it. I didn't encounter any errors along the way. Any clues would be appreciated!

---

### Post by cohiba on 2007-06-24
> **variableenigma said:**
> So when I type "cd .wine/c_drive" it says "bash: cd: .wine/c_drive: No such file or directory".

My directory is called ~/.wine/drive_c/

---

### Post by javaJake on 2007-06-24
> **variableenigma said:**
> It seems that everything has worked until I get to the very end when I'm trying to actually run Joost. It cannot find my Wine directory. So when I type "cd .wine/c_drive" it says
"bash: cd: .wine/c_drive: No such file or directory".

I'm not sure why this is happening or what I should do about it. I didn't encounter any errors along the way. Any clues would be appreciated!

Run "cd ~/.wine/drive_c" instead. :)

---

### Post by claudiu-eduard on 2007-07-10
I try to open Joost but I got this error : ' Couldn't parse application.ini'
If somebody know what to do please reply.

---

### Post by kungfoomasta on 2007-07-10
> **claudiu-eduard said:**
> I try to open Joost but I got this error : ' Couldn't parse application.ini'
If somebody know what to do please reply.

This happens to me too...I think Joost might be looking in whatever folder you run the command from for application.ini.    I had to do cd .wine/drive_c/Joost  and then do wine xulrunner/tvprunner.exe application.ini

---

### Post by kungfoomasta on 2007-07-10
Joost installed and I can run it, however I can only get to the login screen.  the mouse cursor changes to the text insertion "I" bar, however I can't type anything and the login button is greyed out.  I've tried typing and tabbing just in case I just can't see my input text, but the login button never becomes ungreyed.   Any ideas?

---

### Post by exactt on 2007-07-12
i got wine 0.9.40 from the repo. are the patches still the same for this version? thx

---

### Post by doomster on 2007-07-13
i dunno if it has be posted again in this trhead(to be honest i didnt search)

but reading all the first page posts, i saw tons of peoples asking for 
joost invitations
so, here it is  [ Joost send me invitation plz]("www.joost.com/presents/gigaom-newteevee/")

---

### Post by musikgoat on 2007-07-14
> **mikewitt said:**
> 
and get the Wine source:
```
apt-get source wine
```

now cd into the directory that was just created by apt:
```
cd wine-0.9.39~winehq0~ubuntu~7.04
```

and run this command to download the patches necessary to run Joost: (I'm hosting these patches, because they're easire to get this way, rather than from the appdb site)
```
wget http://witt.michael.googlepages.com/patch2.patch http://witt.michael.googlepages.com/patch3.patch http://witt.michael.googlepages.com/patch4.patch http://witt.michael.googlepages.com/patch5.patch http://witt.michael.googlepages.com/patch6.patch http://witt.michael.googlepages.com/patch7.patch http://witt.michael.googlepages.com/patch8.patch
```

now we need to patch using the files we downloaded:
```
patch -p1 < patch2.patch
patch -p1 < patch3.patch
patch -p1 < patch4.patch
patch -p1 < patch5.patch
patch -p1 < patch6.patch
patch -p1 < patch7.patch
patch -p1 < patch8.patch
```


Ok, so when I ran apt-get source,  I got version 0.9.41
I tried to follow the rest of the steps, but patch[4,5,7].patch failed

this is the example failure of patch7.patch
```
Hunk #1 succeeded at 816 (offset 221 lines).
Hunk #2 FAILED at 870.
Hunk #3 FAILED at 888.
Hunk #4 FAILED at 906.
Hunk #5 FAILED at 944.
Hunk #6 FAILED at 958.

```

I'm running the compile step now, and will see if I get any results.   Does anyone have any suggestions?

---

### Post by quattroman on 2007-07-16
I get this when running
> sudo apt-get update
> W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems


I also get it if I do the refresh in the synaptic after adding the 3rd party repository.

Please advice

Thanks

EDIT: found it in page 11 > wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

---

### Post by quattroman on 2007-07-17
> **musikgoat said:**
> Ok, so when I ran apt-get source,  I got version 0.9.41
I tried to follow the rest of the steps, but patch[4,5,7].patch failed

this is the example failure of patch7.patch
```
Hunk #1 succeeded at 816 (offset 221 lines).
Hunk #2 FAILED at 870.
Hunk #3 FAILED at 888.
Hunk #4 FAILED at 906.
Hunk #5 FAILED at 944.
Hunk #6 FAILED at 958.

```

I'm running the compile step now, and will see if I get any results.   Does anyone have any suggestions?

I got the same right now

Anybody roaming this thread for a solution so I can leave it compiling and go to sleep?

---

### Post by isaacj87 on 2007-07-17
I'm getting this error when trying to run joost

I'm using a deb from this thread...0.9.36
Joost 0.10.2

> fixme:iphlpapi:NotifyAddrChange (Handle 0x78e53958, overlapped 0x78e5393c): stub
fixme:keyboard:BlockInput (1): stub
Signature check failed: C:\Program Files\Joost\chrome\tvp-en-US.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\classic.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\classic.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-ui.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar


---

### Post by quattroman on 2007-07-17
There is something in  Wine version 0.9.41 that will not do patch #7

getting this error
```
Hunk #1 succeeded at 816 (offset 221 lines).
Hunk #2 FAILED at 870.
Hunk #3 FAILED at 888.
Hunk #4 FAILED at 906.
Hunk #5 FAILED at 944.
Hunk #6 FAILED at 958.
```

how do we go with this?

---

### Post by isaacj87 on 2007-07-17
The patches don't work for any version higher than 0.9.39

Compile a lower version with the patches

---

### Post by musikgoat on 2007-07-17
Can you suggest how to get it?   I don't know how to apt-get earlier versions or where to find them.   I would love a suggestion on where to get it.


Thanks greatly,

goat

EDIT:  nevermind,  looking on sourceforge, I found it.
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)
I will try with this!!

---

### Post by musikgoat on 2007-07-17
Ok.  So I cant find this file
wine-0.9.39~winehq0~ubuntu~7.04

and I cant make the debian package with this file
wine-0.9.39.tar.bz2


hmmm,   anyone know where i can find the ubuntu specific 0.9.39 source code?     the arch independant wine wouldn't allow me to package with dpkg.


Thanks for anyones help.

---

### Post by Alendit on 2007-08-05
Hi

I patched 0.9.41 with the patches from winehq.org but I get this error
```
err:module:map_image Could not map section .text, file probably truncated
err:module:import_dll Loading library WMVCore.DLL (which is needed by L"C:\\Programme\\Joost\\xulrunner\\components\\vmk.dll") failed (error c000007b).
```

I copied wmvcore.dll from my win partition to .wine/drive_c/windows/system32, but it didn't help. I also tried to add the library in winecfg wit the same result.

I use newest Joost 0.11.0. I tried also to patch 0.9.37 with the patches from  OP, and got the same issues.

> 
hmmm, anyone know where i can find the ubuntu specific 0.9.39 source code? the arch independant wine wouldn't allow me to package with dpkg.

Use 0.9.39 source from sourceforge.net and run
```
dh_make -e "your@email" -c gpl
```.
Then you will be able to build a package with dpkg-buildpackage.

Alendit

---

### Post by [S|G] on 2007-08-05
> **quattroman said:**
> I got the same right now

Anybody roaming this thread for a solution so I can leave it compiling and go to sleep?

Download wine 9.39 from this address:
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

---

### Post by Oddis on 2007-08-09
Hi,

```
wine: Call from 0x13b99c8 to unimplemented function USER32.dll.RegisterRawInputDevices, aborting

```

Anyone have any idea how to solve this problem??? :confused:](*,)

Wine --version: wine-0.9.36
Joost  --version: 0.11.0

---

### Post by xinix on 2007-08-15
> **Oddis said:**
> Hi,

```
wine: Call from 0x13b99c8 to unimplemented function USER32.dll.RegisterRawInputDevices, aborting

```

Anyone have any idea how to solve this problem??? :confused:](*,)

Wine --version: wine-0.9.36
Joost  --version: 0.11.0

Any solutions?  Joost worked pretty well for me until I upgraded from 0.10.4 to 0.11.0.  Now I get this same error.

---

### Post by Trellmor on 2007-08-19
Hmm, i found a patch for the RegisterRawInputDevices error, and it seems to work. Joost splash screen is appearing, but now this appeared:
[http://www.winehq.org/pipermail/wine-patches/2007-February/036066.html](http://www.winehq.org/pipermail/wine-patches/2007-February/036066.html)

> wine: Call from 0xe3a1f1 to unimplemented function GDI32.dll.GetTextExtentExPointI, aborting

This is actually a known bug that might get fixed sooner or later: [http://bugs.winehq.org/show_bug.cgi?id=8636](http://bugs.winehq.org/show_bug.cgi?id=8636)

I'm currently compiling wine-0.9.39 with these two patches. Hope it works ^^

I also found a different patch for the first error, might be worth a look: [http://www.nabble.com/Stub-for-all-raw-input-functions-t3490344.html](http://www.nabble.com/Stub-for-all-raw-input-functions-t3490344.html)

Hope that hels

Edit: Joost is able to start with these two patches, but I can't login, it is stuck on the login windows, the cpu usage shoots up to 100% and wine freezes.

---

### Post by robertmf on 2007-08-25
Using Feisty and ALSA  .14  I'm getting no system sound/beeps;   no totem dvd sound.  No nothing for sound.  :confused:

---

### Post by javaJake on 2007-08-26
> **robertmf said:**
> Using Feisty and ALSA  .14  I'm getting no system sound/beeps;   no totem dvd sound.  No nothing for sound.  :confused:

If totem does not give you sound, then Joost will not give you sound, and your system as a whole probably will not give you sound.

You need to create a new thread elsewhere and try to get support there. If you get sound with other applications but not Joost, that is a sign that Wine is the issue. Right now, however, it appears that your sound card(s) aren't set up correctly.

---

### Post by computergee on 2007-09-01
Hey guys, I need your help getting this one to run. I compiled and patched wine 0.9.39 to match this guide as closely as possible, and used Joost 0.10.4, also to match the guide. I think I got it installed alright, but when I try to run it I get this:

[email]jimmy@jimmy-desktop:~/.wine[/email]/drive_c/Program Files/Joost$ wine xulrunner/tvprunner.exe application.ini
fixme:iphlpapi:NotifyAddrChange (Handle 0x7c8c1958, overlapped 0x7c8c193c): stub
fixme:keyboard:BlockInput (1): stub
Signature check failed: C:\Program Files\Joost\chrome\tvp-en-US.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\classic.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\classic.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-ui.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-ui.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-ui.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar


Thanks for any help =).

---

### Post by ashishgoel on 2007-09-03
now Joost 0.12.0 is out... any solutions on how to run in Ubuntu???

---

### Post by digiplaya on 2007-09-03
Any solutions for simple "C runtime tried to load more than once" error? Tried it with Wine 0.9.44 non-git plus latest Joost.

Hardware: P4 2.4, 1 GB RAM, 2 120 GB HD's, etc.

I'm not actually running Ubuntu but Sidux (though both is debian based). Hopefully it's under my nose already.

Tom Anderson

:confused:

---

### Post by borimrr on 2007-09-21
After I do "dpkg-buildpackage -rfakeroot -uc -b" i get these few errors at the end:
```
../../tools/wrc/wrc --nostdinc -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_NTSYSTEM_  -foversion.res version.rc
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./ntdll.spec    actctx.o atom.o cdrom.o critsection.o debugbuffer.o debugtools.o directory.o env.o error.o exception.o file.o handletable.o heap.o large_int.o loader.o loadorder.o misc.o nt.o om.o path.o process.o reg.o relay.o resource.o rtl.o rtlbitmap.o rtlstr.o sec.o serial.o server.o signal_i386.o signal_powerpc.o signal_sparc.o signal_x86_64.o string.o sync.o tape.o thread.o threadpool.o time.o version.o virtual.o wcstring.o    relay32.o version.res   -Wl,--image-base,0x7bc00000 -o ntdll.dll.so     ../../libs/port/libwine_port.a  
./ntdll.spec:107: function 'NtAreMappedFilesTheSame' not defined
./ntdll.spec:951: function 'NtAreMappedFilesTheSame' not defined
winegcc: ../../tools/winebuild/winebuild failed.
make[3]: *** [ntdll.dll.so] Error 2
make[3]: Leaving directory `/home/marcos/wine-src/wine-0.9.45~winehq0~ubuntu~7.04/dlls/ntdll'
make[2]: *** [ntdll] Error 2
make[2]: Leaving directory `/home/marcos/wine-src/wine-0.9.45~winehq0~ubuntu~7.04/dlls'
make[1]: *** [dlls] Error 2
make[1]: Leaving directory `/home/marcos/wine-src/wine-0.9.45~winehq0~ubuntu~7.04'
make: *** [build-stamp] Error 2
marcos@marcos-laptop:~/wine-src/wine-0.9.45~winehq0~ubuntu~7.04$

```
Any idea why?

---

### Post by emadde02 on 2007-09-25
I have had some problems installing wine and Joost but I've gotten past them all except for this last one. I'm new with Linux so I may need help understanding any responses.

I have  dell latitude d620 dual booting xp and 7.04-feisty fawn


I have completed everything and the only thing that doesnt work is thecommand to actually open the app
This is everything I get when using the "wine xulrunner/tvprunner.exe application.ini" command:


[email]eric@eric-laptop:~/.wine[/email]/drive_c/Program Files/Joost$ wine xulrunner/tvprunner.exe application.ini
wine: Unhandled page fault on read access to 0x00000000 at address 0x602545 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00602545).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00602545 ESP:0033fbcc EBP:0033ff08 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:0033fc2c EBX:00000000 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000004
Stack dump:
0x0033fbcc:  7b8621d0 00000000 0033ff08 00000000
0x0033fbdc:  0033fbec 00000200 00000000 7b000000
0x0033fbec:  0033fc2c 7b86223e c000007a 0033fc14
0x0033fbfc:  00000000 0033fc1c 7b895d60 0060dbe3
0x0033fc0c:  7bc41e50 0000000e 00180017 0060db3e
0x0033fc1c:  00000000 0033fc2c 7bc10000 7b8ad908
Backtrace:
=>1 0x00602545 in tvprunner (+0x2545) (0x0033ff08)
  2 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  3 0xb7e00897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00602545: movb        0x0(%esi),%al
Modules:
Module  Address                 Debug info      Name (16 modules)
PE      600000-857000   Export          tvprunner
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7efa9000-7efb4000       Deferred        libnss_files.so.2
ELF     7efb4000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c84000-b7c8d000       Deferred        libnss_compat.so.2
ELF     b7c8e000-b7c92000       Deferred        libdl.so.2
ELF     b7c92000-b7dd3000       Deferred        libc.so.6
ELF     b7dd4000-b7deb000       Deferred        libpthread.so.0
ELF     b7df9000-b7f0a000       Export          libwine.so.1
ELF     b7f0c000-b7f27000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Joost\xulrunner\tvprunner.exe
        00000009    0 <==
[email]eric@eric-laptop:~/.wine[/email]/drive_c/Program Files/Joost$ 





thanks for any help you can give me

---

### Post by computergee on 2007-10-02
Anyone get the 1.0beta to work that can give us some instructions on how we can get it to work ourselves :).

---

### Post by ckom on 2007-10-03
> **computergee said:**
> Hey guys, I need your help getting this one to run. I compiled and patched wine 0.9.39 to match this guide as closely as possible, and used Joost 0.10.4, also to match the guide. I think I got it installed alright, but when I try to run it I get this:

[email]jimmy@jimmy-desktop:~/.wine[/email]/drive_c/Program Files/Joost$ wine xulrunner/tvprunner.exe application.ini
fixme:iphlpapi:NotifyAddrChange (Handle 0x7c8c1958, overlapped 0x7c8c193c): stub
fixme:keyboard:BlockInput (1): stub
Signature check failed: C:\Program Files\Joost\chrome\tvp-en-US.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\classic.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\classic.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-ui.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-ui.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\toolkit.jar
Signature check failed: C:\Program Files\Joost\chrome\tvp-ui.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar
Signature check failed: C:\Program Files\Joost\xulrunner\chrome\en-US.jar


Thanks for any help =).

I have gotten this same problem. I've used a patched version of wine as described on this thread, and I've also used the version of wine over at the [gentoo forums]("http://forums.gentoo.org/viewtopic-t-558046.html?sid=9a84f66490b83bddbd4ea6b127a1e59a"). I've tried Joost 0.10.2 and Joost 0.10.4 and the new beta (that doesn't even install without freezing). All in all, i've had absolutely no luck if anyone can offer some insight to this problem it would be much appreciated.

---

### Post by computergee on 2007-10-04
I actually don't get that error with the new 1.0beta, I actually got it to launch!

Now I get get past the "What's Coming Up" screen. A UI pops up, but i can't do anything with it.

---

### Post by Oysterville on 2007-10-05
Using a current Gutsy beta build, running into the following error using the first method during the dpkg-buildpackage part:

```
 virtual.c:2239: error: redefinition of ‘NtAreMappedFilesTheSame’
virtual.c:1851: error: previous definition of ‘NtAreMappedFilesTheSame’ was here
make[3]: *** [virtual.o] Error 1
make[3]: Leaving directory `/home/david/wine-src/wine-0.9.46~winehq0~ubuntu~7.04/dlls/ntdll'
make[2]: *** [ntdll] Error 2
make[2]: Leaving directory `/home/david/wine-src/wine-0.9.46~winehq0~ubuntu~7.04/dlls'
make[1]: *** [dlls] Error 2
make[1]: Leaving directory `/home/david/wine-src/wine-0.9.46~winehq0~ubuntu~7.04'
make: *** [build-stamp] Error 2

```

Can't seem to find any previous mention of the first line of that error in Google.

When I went to apply some of the patches it gave me warnings of "Reversed (or previously applied) patch detected!", so I chose the default each time which was to not apply the patch.  I've forced the patch before and the end result was the same.

Anyone?

---

### Post by stoive on 2007-10-15
new version of wine is out, anyone had any success lately???

---

### Post by somebodies on 2007-10-23
hi all, compiling does take a long time, meanwhile..

I am compiling wine .47 with the patches in Gutsy. Wondering what will happen. 

Errors so far:
xlibs-dev does not exist. I decided to throw it away.
Using the git method doesnt work because it need some opengl library which i cant find, or rather dun know which one to install.
Some patches gave errors, and suddenly..
I get the "virtual.c:2239: error: redefinition of &#8216;NtAreMappedFilesTheSame&#8217;" too

Sigh.. Really googling turns up nothing.

Hm.. Perhaps it's due to patches 2,3 not applied properly. Both of these patches are for NtAreMappedFilesTheSame.

ntdll.dll

Perhaps i will try with .41 later

**Update:**

So far the best way to do things for me is: 

```
sudo apt-get build-dep wine
```

```
sudo apt-get install fakeroot libasound2-dev libaudiofile-dev libesd0-dev libaudio-dev libcapi20-dev liblcms1-dev libcupsys2-dev libsane-dev libhal-dev libdbus-1-dev freeglut3-dev libc6-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libglib1.2-dev libglib2.0-dev libgpg-error-dev libice-dev libieee1284-3-dev libjpeg62-dev libldap2-dev libltdl3-dev libmad0-dev libmng-dev libncurses5-dev libogg-dev libopencdk8-dev libpng12-dev libqt3-mt-dev libsm-dev libusb-dev libvorbis-dev libx11-dev libxcursor-dev libxext-dev libxft-dev libxi-dev libxml2-dev libxmu-dev libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev render-dev unixodbc-dev x-dev zlib1g-dev libxxf86dga-dev libxxf86vm-dev libjack0.100.0-dev libicu34-dev libungif4-dev libssl-dev
```
(xlibs-dev is gone)

Install wine using the git method, along with the patches, answering yes to every error when patching..

I still get the "&#8216;NtAreMappedFilesTheSame" error

**More updates**
ok, now that i read the error properly, its just the patch applied at the wrong place, so there are 2 versions of the same functions at lines 1851 and 2239.

The short answer is to apply the patch and go to the file and manually remove the redundant part.

```
gedit /dlls/ntdll/virtual.c
```

**REMOVE**
```
/***********************************************************************
 *             NtAreMappedFilesTheSame   (NTDLL.@)
 *             ZwAreMappedFilesTheSame   (NTDLL.@)
 */
NTSTATUS WINAPI NtAreMappedFilesTheSame(PVOID addr1, PVOID addr2)
{
    TRACE("%p %p\n", addr1, addr2);

    return STATUS_NOT_SAME_DEVICE;
}
```

its at one of the two lines, just find it yourself :)
then everything should make properly.
or perhaps someone can edit the patch to make it work properly

lol more errors, now in /wined3d/context.c
I suggest only patches 2,3,8 should be applied.

---

### Post by somebodies on 2007-10-23
forget it, just apply the patches manually. It would save u so much time compared to having errors while compiling.

---

### Post by somebodies on 2007-10-23
ok, i have manually patched all the files, compiling now.

I tried to generate a patch file, its attached as a txt file cos i can only upload it this way.

So far this patch should work with wine 0.9.47 source code, follow the git instructions, instead of applying the 7 patches apply this one. 

My system specs (the important ones)
ATI radeon 9600
Ubuntu 7.10 Gutsy Gibbon 
Compiled in wine 0.9.47 source code

Credits to the original author of these patches (Peter Oberndorfer, Stefan Doesinger) and also mikewitt

I am currently still compiling the source code, dunno whether joost works or not.

Update: fixed a few errors in the patch. Redefinitions again. Smaller file size lol.

Update 2: compiled done, installed joost 1.0 beta, gave me splash screen and this error.

```
wine: Call from 0xd7df53 to unimplemented function GDI32.dll.GetTextExtentExPointI, aborting
```

i guess more patches are needed. Refer to [http://bugs.winehq.org/show_bug.cgi?id=8636](http://bugs.winehq.org/show_bug.cgi?id=8636)

Refer below

---

### Post by wallcrawler78 on 2007-10-23
What would be awesome is to see someone create a joost repo or something that has the wine.deb and a script that can install the deb, download the Joost install file and configure all the other littl crap in one little swooop.  This program is cool enough that I am sure someone out there can make it work easier.

How big is the wine*.deb?  If it was up on bittorrent that would rock!  Ubuntu just keeps getting better and better.  Would love to see Joost on Ubuntu.

---

### Post by somebodies on 2007-10-23
Is it possible to get a .deb with git? how do I do it or find it?

Update:
ok got it. here it is, although be warned that it may still give BadValue (integer parameter out of range for operation) error. Maybe can try using other versions of joost.

Oh, use it at your own risk :)

Pls get the wine dependencies before installing this.

```
sudo apt-get build-dep wine
```

[http://www.fileupyours.com/files/137735/joostwine_git1-1_i386.deb](http://www.fileupyours.com/files/137735/joostwine_git1-1_i386.deb)

---

### Post by somebodies on 2007-10-23
GetTextExtentExPointI error is gone with this patch (merged from bugs.winehq) , but i get this error instead.

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  144 (XFree86-DRI)
  Minor opcode of failed request:  7 ()
  Value in failed request:  0x56
  Serial number of failed request:  948
  Current serial number in output stream:  948

```

Tried googling, nothing turns up. Any ideas?
Anyone can try it and tell me if it works?

It is a bit beyond me

---

### Post by Caharin on 2007-10-23
im compiling wine 9.47 with your patch somebodies.  I'm gunna try to install joost0.102 to see if I can get it to work.  so far I have not had anything successfully compile until your your patch from wine 9.36-9.47.  Now it's actually compiling so I'll see in a few mins if joost.102 will run.

compiled wine installed fine.
joost 0.102 installed.  when the program ran it gave me the error that the CRT was initialized twice :(

---

### Post by somebodies on 2007-10-23
yay im so happy someone tried. :)

which one did u use? i think you used the one without patch 4,5,6,7

anyway, try this deb file.

rmb to remove the source wine.

[http://www.fileupyours.com/files/137735/joostwine_git1-1_i386.deb](http://www.fileupyours.com/files/137735/joostwine_git1-1_i386.deb)

---

### Post by stoive on 2007-10-24
i tried your .deb and it worked up till the splash screen..
then wine had a heap of fixme errors and ends with

> err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
err:d3d:CreateContext SetPixelFormat failed on HDC=0x390 for iPixelFormat=1
err:d3d:IWineD3DSwapChainImpl_CreateContextForThread Failed to create a new context for the swapchain
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"


and in the wine virtual desktop an error "R6034 An application has made an attempt to load the C runtime library incorrectly"

---

### Post by somebodies on 2007-10-24
> **stoive said:**
> i tried your .deb and it worked up till the splash screen..
then wine had a heap of fixme errors and ends with



and in the wine virtual desktop an error "R6034 An application has made an attempt to load the C runtime library incorrectly"

I am not very sure, currently i get the splash screen too and the fatal error called badvalue

Did u do these?

```
sudo apt-get build-dep wine
```

```
sudo apt-get install fakeroot libasound2-dev libaudiofile-dev libesd0-dev libaudio-dev libcapi20-dev liblcms1-dev libcupsys2-dev libsane-dev libhal-dev libdbus-1-dev freeglut3-dev libc6-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libglib1.2-dev libglib2.0-dev libgpg-error-dev libice-dev libieee1284-3-dev libjpeg62-dev libldap2-dev libltdl3-dev libmad0-dev libmng-dev libncurses5-dev libogg-dev libopencdk8-dev libpng12-dev libqt3-mt-dev libsm-dev libusb-dev libvorbis-dev libx11-dev libxcursor-dev libxext-dev libxft-dev libxi-dev libxml2-dev libxmu-dev libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev render-dev unixodbc-dev x-dev zlib1g-dev xlibs-dev libxxf86dga-dev libxxf86vm-dev libjack0.100.0-dev libicu34-dev libungif4-dev libssl-dev
```

Okok, i think i see the code. Sorry im blind

---

### Post by stoive on 2007-10-24
> 0 upgraded, 0 newly installed, 0 to remove and 140 not upgraded.

 on both of them

---

### Post by somebodies on 2007-10-24
[.DEB file]("http://www.fileupyours.com/files/137735/joostwine_git1-2_i386.deb")

[Patch]("http://www.fileupyours.com/files/137735/patch.txt")

Sigh, i have work to do, maybe we should wait for the native version.

Somehow i have a feeling joost doesn't need wine to run.

---

### Post by Caharin on 2007-10-24
thanks for the .deb man. that was way cool of you.
I got it to install and then it said it had an error, so I clicked restart joost and it actually got to what looked like a credits page.  Then it showed dialog box that joost normally makes but the font was all gibberish.  I have the ms fonts installed but I don't think thats what the problem is.  Are there plans for a native version of Joost?

---

### Post by somebodies on 2007-10-25
> **Caharin said:**
> thanks for the .deb man. that was way cool of you.
I got it to install and then it said it had an error, so I clicked restart joost and it actually got to what looked like a credits page.  Then it showed dialog box that joost normally makes but the font was all gibberish.  I have the ms fonts installed but I don't think thats what the problem is.  Are there plans for a native version of Joost?

The credits page is the splash screen.

hm, i got the other screen too for one of the versions of joost. Wonder what it is trying to say.

Have u tried any other versions?

---

### Post by tuxtail on 2007-10-25
I'm trying to get JoostSetup-Beta-1.0.2.exe to run, since I don't know what the friendly version is, or where to get it ;)

It installs, no problem.

Running "wine xulrunner/tvprunner.exe application.ini" from the installation directory gives me the 800x600 virtual desktop and a splash screen. After a small amount of time, I get:

```
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33ef98, uiNumDevices=1, cbSize=12) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33ef94, uiNumDevices=1, cbSize=12) stub!
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
err:d3d:CreateContext SetPixelFormat failed on HDC=0x390 for iPixelFormat=1
err:d3d:IWineD3DSwapChainImpl_CreateContextForThread Failed to create a new context for the swapchain
```

Now Joost comes up, saying it crashed, and want's to send a crash report...

I can't seem to get past this...

Anyone?

Thx
TuxTail

---

### Post by somebodies on 2007-10-25
> **tuxtail said:**
> I'm trying to get JoostSetup-Beta-1.0.2.exe to run, since I don't know what the friendly version is, or where to get it ;)

It installs, no problem.

Running "wine xulrunner/tvprunner.exe application.ini" from the installation directory gives me the 800x600 virtual desktop and a splash screen. After a small amount of time, I get:

```
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33ef98, uiNumDevices=1, cbSize=12) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33ef94, uiNumDevices=1, cbSize=12) stub!
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
err:d3d:CreateContext SetPixelFormat failed on HDC=0x390 for iPixelFormat=1
err:d3d:IWineD3DSwapChainImpl_CreateContextForThread Failed to create a new context for the swapchain
```

Now Joost comes up, saying it crashed, and want's to send a crash report...

I can't seem to get past this...

Anyone?

Thx
TuxTail

At least for u joost wants to send a crash report.

Im sorry, cant help u. I think most ppl who installs and run will get this problem.

Has to do with the original patches 4 and 7, onscreen and offscreen rendering. I cant get past editing context.c, as in the codes in these 2 patches seem to contradict each other. One says add in this part, and the other says take it out.

Anyone can help me on this? or do I have to ask the author? Pls, thanks

For the moment pls hold on. I am really unsure of what to do.

---

### Post by tuxtail on 2007-10-25
I did this:

sudo apt-get source wine
cd wine-*
patch -p1 mbs_joost.1.patch
dpkg-buildpackage -rfakeroot -uc -b

installed the deb with dpkg

The patch file is here: [http://tuxtail.org/mbs_joost.1.patch](http://tuxtail.org/mbs_joost.1.patch)
and is a collected patch of what I found here on this thread.. and maybe some more stuff... don't remember...

But gets me stumped...

I'm using Kubuntu Gutsy btw

/tuxtail

---

### Post by somebodies on 2007-10-25
okok im gonna try it

Edit:
ok got it, for lazy ppl, hope this works for you
[http://www.fileupyours.com/files/137735/joostwine_gittuxtail1-3_i386.deb](http://www.fileupyours.com/files/137735/joostwine_gittuxtail1-3_i386.deb)

I still get this error message, I think its only limited to my computer

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  144 (XFree86-DRI)
  Minor opcode of failed request:  7 ()
  Value in failed request:  0x56
  Serial number of failed request:  954
  Current serial number in output stream:  954

```

---

### Post by somebodies on 2007-10-26
Ok this is the farthest i get so far, I see the login screen!! Even though i do get
```
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1

```

I used **kumbayo**, a fork of wine. Ok, a wine fork. A fork in the wine. :)
[http://repo.or.cz/w/wine/kumbayo.git](http://repo.or.cz/w/wine/kumbayo.git)

Anyway, after it gives the login screen, it crashes.

After a while, it gives me this

```
err:ntdll:RtlpWaitForCriticalSection section 0x1d56e4 "dsound.c: DirectSoundDevice.mixlock" wait timed out in thread 002a, blocked by 001f, retrying (60 sec)
```

and a lot of times of
```
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=28576, mixpos=760/49392 (828/53760), primary_mixpos=51008, writepos=22432, mixlen=20448

```

ok its a known bug [http://bugs.winehq.org/show_bug.cgi?id=1631](http://bugs.winehq.org/show_bug.cgi?id=1631)

---

### Post by divadotrebla on 2007-10-29
I want to install joost. (first time =P)
Did anyone get this working on Gutsy?

---

### Post by tuaranoi on 2007-10-31
i tried to patch the patch2.patch, from patch4-7, there were some errors...

---

### Post by somebodies on 2007-11-01
Anyone tried compiling kumbayo and running joost?

---

### Post by h2z on 2007-11-23
> **tuxtail said:**
> I did this:

sudo apt-get source wine
cd wine-*
patch -p1 mbs_joost.1.patch
dpkg-buildpackage -rfakeroot -uc -b

installed the deb with dpkg

The patch file is here: [http://tuxtail.org/mbs_joost.1.patch](http://tuxtail.org/mbs_joost.1.patch)
and is a collected patch of what I found here on this thread.. and maybe some more stuff... don't remember...
/tuxtail


I've done the same thing (0.9.49) but when I try running Joost (Beta 1.0.2) I only get to see the splash screen for a few seconds before the Joost Crash Reporter shows up. Is there a way to fix this?

```

err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
err:d3d:CreateContext SetPixelFormat failed on HDC=0x378 for iPixelFormat=1
err:d3d:IWineD3DSwapChainImpl_CreateContextForThread Failed to create a new context for the swapchain

```


EDIT: Vid card is ATI X1600pro (8.42.3 driver), wine is set to emulate 800x600 desktop (tried with and without Hardware Accel and Shaders).

---

### Post by somebodies on 2007-11-25
seriously, i have higher hopes with kumbayo

---

### Post by shytuzsaylaw on 2007-12-09
Shame about Joost. Tried installing Joost Beta 1.03, using the latest version of wine. Repository details for all Ubuntu versions are available on WineHQ website.

Reports Error: " R6031 -Attempt to initialise CRT more than once. This indicates a bug in your application." 

In fairness, even some microsoft users get this message, depending on their hardware configuration.

If anyone has any ideas, involving solutions though, they would be gratefully appreciated.

---

### Post by Caharin on 2007-12-13
I'm getting the same error on 1.0.3 and wine 9.50, though that was the same error I've been getting since 1.0.1.  There are a couple of threads on Joost's website petitioning for them to make a native linux version.  It may be more beneficial to add your voice too.  Last I checked there were 3031 posts requesting a native version.

---

### Post by divadotrebla on 2007-12-30
> **shytuzsaylaw said:**
> Shame about Joost. Tried installing Joost Beta 1.03, using the latest version of wine. Repository details for all Ubuntu versions are available on WineHQ website.

Reports Error: " R6031 -Attempt to initialise CRT more than once. This indicates a bug in your application." 

In fairness, even some microsoft users get this message, depending on their hardware configuration.

If anyone has any ideas, involving solutions though, they would be gratefully appreciated.


I got these one too =S

Anyone could run Joost on Gutsy?

---

### Post by JoshuaRL on 2007-12-31
Has anyone tried Mac-on-Linux?  [http://mac-on-linux.sourceforge.net/](http://mac-on-linux.sourceforge.net/)

Do you think it would be easier to run Joost through that because it's UNIX based?

Just a thought.

---

### Post by lithorus on 2008-01-16
> **JoshuaRL said:**
> Has anyone tried Mac-on-Linux?  [http://mac-on-linux.sourceforge.net/](http://mac-on-linux.sourceforge.net/)

Do you think it would be easier to run Joost through that because it's UNIX based?

Just a thought.

The mac-on-linux is only for PPC

---

### Post by motin on 2008-02-06
> **shytuzsaylaw said:**
> Shame about Joost. Tried installing Joost Beta 1.03, using the latest version of wine. Repository details for all Ubuntu versions are available on WineHQ website.

Reports Error: " R6031 -Attempt to initialise CRT more than once. This indicates a bug in your application." 

In fairness, even some microsoft users get this message, depending on their hardware configuration.

If anyone has any ideas, involving solutions though, they would be gratefully appreciated.

I too get this...

---

### Post by xodeus on 2008-03-04
Is anyone working on a workaround for 7.10 and the latest publics beta of joost?

---

### Post by TheLimpKid on 2008-05-18
Can't we just make our own version better?

Here is some documentation:
[http://dev.joost.com/](http://dev.joost.com/)

I'd love to help, although I'm not that good at programming.

---

### Post by javaJake on 2008-05-24
Augh, you got me all excited. I was going to look and see what I could do, but the only developer stuff they posted up there was for Joost Widgets (which run within Joost). Dangit. :(

---

### Post by eeclark on 2008-07-04
Use Miro

[http://blog.linuxoss.com/2007/11/miro-open-source-alternative-to-joost-and-much-more/](http://blog.linuxoss.com/2007/11/miro-open-source-alternative-to-joost-and-much-more/)

Support Open Source

---

### Post by x58 on 2008-12-09
Joost don't have anymore it's own Player. Now go to [www.joost.com](www.joost.com) and playing everything from website. Very, very good quality.Problem resolved

---

