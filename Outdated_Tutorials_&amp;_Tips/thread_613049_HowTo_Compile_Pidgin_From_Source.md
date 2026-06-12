---
title: "HowTo: Compile Pidgin From Source"
date: 2007-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by trusatori on 2007-11-14
I've trolled these forums for awhile now, enjoying the plethora of information and experienced users, but being that this is my first post / tutorial, please bear with me ;].  Because the repos have yet to be updated with the latest version of Pidgin and the release seems to fix some memory leaks that have plagued the little bird for awhile now, I figured a concise set of instructions on how to do this would be appropriate.  I've noticed a few people compiling new versions but while unknowingly keeping the old libpurple, which may or may not be a good thing, and this tutorial will make use of the most up-to-date version.

Note: I realize that I simply could've posted a deb for most of this, but compiling from source is a handy skill that many have yet to learn or feel comfortable with. It allows one to liberate themselves of practices such as "deb begging" or adding a new (possibly insecure) repo to download one app.  This guide is also fairly Gutsy specific, but should be easily modified to just about any other release.

Other handy information regarding compiling Pidgin can be found [here]("https://help.ubuntu.com/community/Pidgin").

**Current Version: 2.4.1 [[ChangeLog]("http://developer.pidgin.im/wiki/ChangeLog") / [Download]("http://pidgin.im/download/source/")]**

**1) Remove old Pidgin et. al.**

Open a terminal and type / copy-and-paste the following:
```
sudo aptitude purge pidgin pidgin-data libpurple0
```
Do not fear, as this will not remove your pidgin settings, logs, accounts, aways, etc.

**2) Prepare to compile Pidgin**

Click on the main menu and select "System->Administration->Software Sources".  Make sure the box next to "Source code" is checked.

Open a terminal and type / copy-and-paste the following:
```
sudo aptitude update && sudo aptitude install build-essential checkinstall
```
This will install the necessary tools to compile anything, if you haven't already done so.

Open a terminal and type / copy-and-paste the following:
```
sudo apt-get build-dep pidgin
```
Allow it to download and install the plethora of packages that are required to compile Pidgin.

**3) Download and compile Pidgin**

The pidgin source can be found at [pidgin.im]("http://www.pidgin.im") or directly by clicking [here]("http://sourceforge.net/project/downloading.php?groupname=pidgin&filename=pidgin-2.4.1.tar.bz2&use_mirror=internap").
Extract the archive either by right-clicking on it and clicking "extract here" or by running the following command in terminal:
```
tar -jxvf pidgin-2.4.1.tar.bz2
```

Get into your newly created directory:
```
cd pidgin-2.4.1/
```

Get compiling!  Retrieve a beer and/or cup of tea as, depending on the speed of your computer, the 'make' command may take some time.
```
./configure --prefix=/usr --enable-gnutls=yes
make
sudo checkinstall
```
(For those interested, the '--enable-gnutls=yes' is required for Google Talk and MSN support.)

Enjoy watching the waterfall of text for a bit.  When presented with a series of questions after running 'sudo checkinstall' simply press enter to accept the defaults.

***Important Note*** Sometimes, for reasons I don't fully understand, checkinstall will seemingly stop doing its business at "Installing Debian Package."  In the event that this happens, simply press enter to accept whatever dialog is appearing and checkinstall is hiding from you.  I believe it's asking if you want to overwrite an old file leftover from the old install (and therefore answering yes is the way to go), but can anyone confirm this?

After more text floods the screen, you should have Pidgin compiled and installed.  Try running it by typing 'pidgin'.

**4) Other Notes**
If when trying to run Pidgin, you receive the error:
```
pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory
```
Try running these two commands in terminal:
```
sudo ln -s /usr/local/lib/libpurple.so /usr/lib/
sudo ln -s /usr/local/lib/libpurple.so.0 /usr/lib/
```
The error is caused by Pidgin looking for its libraries in the wrong place (likely due to the omission of '--prefix=/usr' from configure).  The previous two commands link where it thinks they are to where they actually are.  You should now be able to run Pidgin successfully!

You can run a
```
sudo rm -rf pidgin-2.4.1/
```
to get rid of your source directory but make **SURE** you're removing the directory and not anything else as a 'rm -rf' can be a nasty one if used carelessly.

Also, because of an inconsistency in version naming, update-manager or your other package managers may attempt to "upgrade" you back down to the old version that's in the repos, thinking that it's newer.  To get this to stop happening, open Synaptic and search for pidgin, pidgin-data, and libpurple0 (you'll have to do this one by one as it resets your search after each).  After searching for each, highlight it and click on 'Package->Lock Version' up top.  This will keep update-manager from touching it and constantly suggesting an update.

The following command will remove Pidgin at anytime (since you were smart and used 'checkinstall'):
```
sudo aptitude remove pidgin
```

Enjoy having fewer memory leaks and be sure to post any suggestions / questions \m/ ;]

**ChangeLog**
*11/21/07* - added  '--prefix=/usr' option to the ./configure command (suggested by ImpressMe)
*11/28/07* - Updated to reflect the release of 2.3.0 (thanks to goldencako for testing) and added a link to the Pidgin tutorial provided by the Ubuntu Documentation Project (thanks to Rippie).  Also added the '--enable-gnutls=yes' ./configure option to enable support for MSN and Google Talk.
*12/8/07* - Fixed a small typo (thanks to Chonnawonga!) and updated the guide to reflect the release of 2.3.1.
*12/28/07* - Made the "important note" more obvious :P~
*3/3/08* - Updated to reflect the release of 2.4.0 (thanks to mafsi for testing).
*4/3/08* - Updated to reflect the release of 2.4.1 and added the "Software Sources" step (thanks to h2z!).

---

### Post by ImpressMe on 2007-11-15
Question:

```
 
sudo ln -s /usr/local/lib/libpurple.so /usr/lib/
sudo ln -s /usr/local/lib/libpurple.so.0 /usr/lib/ 
```

Will these links survive the uninstall and be a problem, if I install Pidgin from the official repositories later?

---

### Post by ImpressMe on 2007-11-15
How do I uninstall all of the files installed by:

sudo apt-get build-dep pidgin

---

### Post by trusatori on 2007-11-15
> **ImpressMe said:**
> Question:

```
 
sudo ln -s /usr/local/lib/libpurple.so /usr/lib/
sudo ln -s /usr/local/lib/libpurple.so.0 /usr/lib/ 
```

Will these links survive the uninstall and be a problem, if I install Pidgin from the official repositories later?

The links will likely survive the package being uninstalled.  

Although I'm not 100% certain, when installing a future release of Pidgin from the repos, apt is likely going to ask if you want to overwrite them or it may just do it automatically since they're only links.  In any event, if you decide to uninstall this version, the symlinks can simply and safely be rm'd from /usr/lib/ before installing the new version or if an error results during install.

Keeping the build dependencies is not going to hurt anything (except maybe use up a bit of disk space) and they'll be needed again anyway in the event that you compile another version of Pidgin.  However, if you really want the build dependencies gone, 'gtkorphan' is your friend.
```
sudo aptitude install gtkorphan
```
It will allow you to find and remove all orphaned packages.  To my knowledge, that's the only way to accomplish what you asked, as apt doesn't seem to have this functionality built-in.

---

### Post by ImpressMe on 2007-11-15
[COLOR=Black]Thx[/COLOR] ;)

---

### Post by Elmeromero on 2007-11-16
Excellent! Your instructions worked perfectly!
I'm recently installed Gusty and wanted to upgrade into Pidgin 2.2.2 because that version supports MSNP14 which includes displaying status messages that are displayed with the each buddy in MSN. However the status messages are not displayed in Pidgin and in fact the MSNP14 protocol was already implemented in version 2.2.1.
Has anyone here been able to see status messages of MSN buddies in Pidgin, and if so does it require some configuration?

---

### Post by bundo on 2007-11-16
config option is
[COLOR="Red"]configure --prefix=/usr 
[/COLOR]
No Need Symlink link

---

### Post by ImpressMe on 2007-11-16
> **Elmeromero said:**
> Excellent! Your instructions worked perfectly!
I'm recently installed Gusty and wanted to upgrade into Pidgin 2.2.2 because that version supports MSNP14 which includes displaying status messages that are displayed with the each buddy in MSN. However the status messages are not displayed in Pidgin and in fact the MSNP14 protocol was already implemented in version 2.2.1.
Has anyone here been able to see status messages of MSN buddies in Pidgin, and if so does it require some configuration?

Are you *sure* that it supports MSNP14? I can see comments from Yahoo contacts and what not, but not from MSN. Apparently MSNP14 code was completed a long time ago, but I am not sure that it is integrated into 2.2.1 or 2.2.2.

It should work out of the box, but lets see what 2.2.3 will bring us. I got tired of reading page long tickets.

And please upgrade the HOW-TO with config option [COLOR=Black]--prefix=/usr, _[trusatori.]("http://ubuntuforums.org/member.php?u=287317")_[/COLOR]

---

### Post by trusatori on 2007-11-16
Thanks for the input, friends, and the guide has been updated.

The reason I didn't include it in the original is because I personally prefer to keep my repo installed stuff (/usr/) separate from my compiled stuff (/usr/local/) because I find that occasionally, checkinstall will mess something up and talk about overwriting and removing things I don't want to when I go to remove a package.  Due to this, I like to be on the safe side and keep things separate, but I agree that it is a more straight-forward approach, especially to the new user, to have everything in /usr/ ;].

As for the msn protocol, I'm not an msn user and therefore didn't notice the issue, but I'll look into it and see if I can be of any help.

---

### Post by ImpressMe on 2007-11-16
I didn't see this msnp14 support in 2.2.1 from this official Ubuntu repos neither in the 2.2.2 I found in another repository, so I simple believe that it has not yet found its way into Pidgin.

---

### Post by survient on 2007-11-22
I'm compiling this and I'm almost 100% of the way, here's my final output after the ./config:
pidgin 2.2.2

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : bonjour gg irc jabber msn myspace novell oscar qq sametime silc simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification...... : yes
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.

Cyrus SASL support and Tk support are really the only two things bugging me, it's saying Mono and Network Manager support are either experimental or buggy(should I enable these?). Should I get support for cyrus and tk? if so, how? otherwise I think everything looks good.

---

### Post by trusatori on 2007-11-22
It really depends strictly on if you want / need these features.  The default compile will work just fine for pretty much everyone.  Google around for what these features actually are (I'm not familiar with them and haven't read any Pidgin tutorials talking about them in the past) and if you wish to have them enabled, install the corresponding "-dev" package from Synaptic and enable the feature by appending "--enable-cyrus-sasl" or whatever to your "./configure" line.

Frankly, if you don't know what these features are at first glance, the chances are you don't want / need them, as the "sudo apt-get build-dep pidgin" command installs / enables all of the features of a typical Pidgin setup.

But that's just my two cents ;]

---

### Post by Chonnawonga on 2007-11-22
Thanks for the how-to! Fantastic! I am enjoying it already.

Quick question: now that I've told Synaptic to leave Pidgin the heck alone, it won't let me install guifications (of course). So, should I try compiling that from source too, or do you know if there's a deb somewhere? The only one I could find with a quick search is this: [http://packages.debian.org/sid/gaim-guifications/all/download]("http://packages.debian.org/sid/gaim-guifications/all/download") but I don't know if that's a good idea or not, seeing as I'm a bit of a newbie.

Thank you!

---

### Post by survient on 2007-11-22
I can't get it to kick on either, but libnotify is working.

---

### Post by koolkatkiwi on 2007-11-23
> **survient said:**
> I'm compiling this and I'm almost 100% of the way, here's my final output after the ./config:
pidgin 2.2.2

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : bonjour gg irc jabber msn myspace novell oscar qq sametime silc simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification...... : yes
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.



Hi. Thanks, trusatori, for this great tutorial. It was very scary for me, seeing all those pages and pages of things happening. I'm a very rank newbie, and I should have stayed in the Absolute Beginners Forum, I guess, and not tried to do anything like this. I searched for an update for Pidgin, and found this thread - it looked straightforward, so I thought maybe I could do it.

Pidgin has installed alright, but it's in the wrong directory! I wish I had seen any messages like the one quoted here, especially "Pidgin will be installed in /usr/local/bin." It didn't show me where it would be installed, or anyway I didn't see it.

At Step 3, it says: "3) Download and compile Pidgin - Extract the archive either by right-clicking on it and clicking "extract here" or by running the following command in terminal: tar -jxvf pidgin-2.2.2". So I did that, but it didn't put it into the right directory - instead it installed into my /home directory, where I had downloaded it.

What should I do now, do the whole process again, uninstalling Pidgin, and then re-installing it again in the right directory? Or is there an easier way of doing it? Should I remove it using "dpkg -r pidgin" as it says to do? This is the message I got:


**********************************************************************

 Done. The new package has been installed and saved to

 /home/kath/pidgin-2.2.2/pidgin_2.2.2-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r pidgin

**********************************************************************

Any advice would be great, and sorry to be so dumb.

Cheers,
Kath.

---

### Post by trusatori on 2007-11-23
> **Chonnawonga said:**
> Thanks for the how-to! Fantastic! I am enjoying it already.

Quick question: now that I've told Synaptic to leave Pidgin the heck alone, it won't let me install guifications (of course). So, should I try compiling that from source too, or do you know if there's a deb somewhere? The only one I could find with a quick search is this: [http://packages.debian.org/sid/gaim-guifications/all/download]("http://packages.debian.org/sid/gaim-guifications/all/download") but I don't know if that's a good idea or not, seeing as I'm a bit of a newbie.

Thank you!

Chonna:
I just played around with it and found out that it's easiest to get this working by compiling Guifications yourself.  The source can be found [here]("http://downloads.guifications.org/plugins//Guifications2/pidgin-guifications-2.14.tar.bz2").  Once you extract and cd into the folder...
```

./configure --prefix=/usr
make
sudo checkinstall
```
(Leave out the --prefix=/usr part ONLY if you didn't use it during the compile of Pidgin [and used the ln-s fix instead].  If you did follow the original tutorial verbatim, however, copy and paste the above commands).

Just like you did when compiling Pidgin and it should show up under Tools->Plugins in Pidgin.  Let me know how that works for you.
> **koolkatkiwi said:**
> Hi. Thanks, trusatori, for this great tutorial. It was very scary for me, seeing all those pages and pages of things happening. I'm a very rank newbie, and I should have stayed in the Absolute Beginners Forum, I guess, and not tried to do anything like this. I searched for an update for Pidgin, and found this thread - it looked straightforward, so I thought maybe I could do it.

Pidgin has installed alright, but it's in the wrong directory! I wish I had seen any messages like the one quoted here, especially "Pidgin will be installed in /usr/local/bin." It didn't show me where it would be installed, or anyway I didn't see it.

At Step 3, it says: "3) Download and compile Pidgin - Extract the archive either by right-clicking on it and clicking "extract here" or by running the following command in terminal: tar -jxvf pidgin-2.2.2". So I did that, but it didn't put it into the right directory - instead it installed into my /home directory, where I had downloaded it.

What should I do now, do the whole process again, uninstalling Pidgin, and then re-installing it again in the right directory? Or is there an easier way of doing it? Should I remove it using "dpkg -r pidgin" as it says to do? This is the message I got:


**********************************************************************

 Done. The new package has been installed and saved to

 /home/kath/pidgin-2.2.2/pidgin_2.2.2-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r pidgin

**********************************************************************

Any advice would be great, and sorry to be so dumb.

Cheers,
Kath.

Kath:
The "/home/kath/pidgin-2.2.2/pidgin_2.2.2-1_i386.deb" file that was created is  made by the installer and can be used to install Pidgin again without going through all the compile jazz again and frankly, after all is installed and working, you can delete that whole "pidgin_2.2.2" folder from your home directory as it won't be used at all once all is set.

What happens when you type 'pidgin' at the command line?  The app should just run.  If nothing happens, try running 'which pidgin' to see if / where Pidgin is installed.  If nothing results, I'd suggest running the "sudo dpkg -r pidgin" command to remove what you have and try again.  Don't let it scare you!  Post your questions here and you'll get it installed in no time. ;]

---

### Post by Photon on 2007-11-24
Thanks for the guide :) i compiled pidgin without the necessary packages (didnt do the apt-get build-dep step) was able to connect to yahoo, but not gtalk. Now i know to do things the right way :)

---

### Post by user1234 on 2007-11-24
> **trusatori said:**
> 
Open a terminal and type / copy-and-paste the following:
```
sudo apt-get build-dep pidgin
```
Allow it to download and install the plethora of packages that are required to compile Pidgin.

Having trouble here:
```
sudo apt-get build-dep pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_gutsy_free_source_Sources - open (2 No such file or directory)
```

---

### Post by koolkatkiwi on 2007-11-24
> **trusatori said:**
> 
Kath:
The "/home/kath/pidgin-2.2.2/pidgin_2.2.2-1_i386.deb" file that was created is  made by the installer and can be used to install Pidgin again without going through all the compile jazz again and frankly, after all is installed and working, you can delete that whole "pidgin_2.2.2" folder from your home directory as it won't be used at all once all is set.

What happens when you type 'pidgin' at the command line?  The app should just run.  If nothing happens, try running 'which pidgin' to see if / where Pidgin is installed.  If nothing results, I'd suggest running the "sudo dpkg -r pidgin" command to remove what you have and try again.  Don't let it scare you!  Post your questions here and you'll get it installed in no time. ;]

Thanks for that, Michael. I guess I didn't mess up too badly! Yes, it starts from the CLI and it did install into the correct folder - /usr/bin/pidgin, and it starts when I click on the icon (but the icon isn't right - see below). I don't know if it works as it should, because I've never used Pidgin or any IM before. I want to use it for voice over internet.

BUT - the thing is, all the icons for things such as "available" "chatty" "away" "extended away" "do not disturb" etc. have disappeared and now appear as a box with a red "x" in them. The main logo, the little bird, has also disappeared, and there is just a generic square there. When you have the program running, the icon on the top bar is also a square with a red "x". How can I get the icons back? I feel there might be something else wrong, too, if those are missing.

Cheers,
Kath:KS

---

### Post by koolkatkiwi on 2007-11-24
Hmmm . . . Survient said he saw the message: "Pidgin will be installed in /usr/local/bin."

Now, mine was installed into just /usr/bin/pidgin. Could it be that it's in the wrong directory, and so the path to the icons has been lost? Just an idea.

Cheers,
Kath:KS

---

### Post by koolkatkiwi on 2007-11-24
Michael, I "locked version" on those three files you said to, but it doesn't make any difference to the Synaptic Package Manager. I keep getting the message:

"Software index is broken. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

When I do this in the terminal, of course it wants to get back the previous version of Pidgin. 

What should I do?

Cheers,
Kath:KS

---

### Post by trusatori on 2007-11-25
> **user1234 said:**
> Having trouble here:
```
sudo apt-get build-dep pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_gutsy_free_source_Sources - open (2 No such file or directory)
```

Can you run any apt-get command, i.e 'sudo apt-get update' or 'sudo apt-get upgrade'?  If you can, I am really going to be left scratching my head.

If you can't, it looks like it may have something to do with Medibuntu's repository, so if you have added it to your '/etc/apt/sources.list', comment out the entry and try again.

Kath:
The icon issue is indeed very odd.  I have done many of these exact compiles and the only icon issue I've ever experienced was a temporarily disappearing icon for the program itself in the main menu and I'm not quite sure what causes that.  If a restart / re-login isn't fixing things for you, I'm going to have to  research around a bit and see what may cause that.

If you've got the time on your hands and feel like playing a bit, you may want to run through the tutorial again, starting with the very first "purge..." command just to make sure everything is kosher is that department.

And regarding your installation location: your /usr/bin/ is actually preferable to /usr/local/bin, and I've done installs into both and haven't experienced your icon issue, so I think you're a-okay in that department.

---

### Post by trusatori on 2007-11-25
> **koolkatkiwi said:**
> Michael, I "locked version" on those three files you said to, but it doesn't make any difference to the Synaptic Package Manager. I keep getting the message:

"Software index is broken. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

When I do this in the terminal, of course it wants to get back the previous version of Pidgin. 

What should I do?

Cheers,
Kath:KS

Hmmm, seems like something has made your packages upset and they tend to be a bit sensitive, so just about anything could've caused it.  My recommendation is this: Unlock the Pidgin files (pidgin, pidgin-data, libpurple0) if Synaptic will allow you to and run the suggested '"sudo apt-get install -f" in terminal, allowing it to do whatever it wants to do (including removing Pidgin) to get your packages back in order.  After that (hopefully successful) operation, run through the tutorial again to get the new Pidgin back in there.  Hopefully this will simultaneously please the package gods and allow you to get your icons back all in one big move.  Let me know how it goes and how else I can advise.

---

### Post by desperado666 on 2007-11-25
Anyone had success compiling pidgin 2.2.2. on feisty ? 
I have errors about /usr/bin/stripe which is already installed and cant be overwritten.

---

### Post by Chonnawonga on 2007-11-25
trusatori,

The guifications compile worked like a charm, same as the pidgin compile. Thank you! I didn't even have to re-load my old guifications settings, which is pretty sweet.

Tell me, what does the "--prefix=/usr" option do?

Thanks!!

---

### Post by trusatori on 2007-11-25
> **desperado666 said:**
> Anyone had success compiling pidgin 2.2.2. on feisty ? 
I have errors about /usr/bin/stripe which is already installed and cant be overwritten.

I haven't tried to compile on Feisty, so hopefully someone who has will drop by and be able to lend some assistance.

[QUOTE=Chonnawonga]trusatori,

The guifications compile worked like a charm, same as the pidgin compile. Thank you! I didn't even have to re-load my old guifications settings, which is pretty sweet.

Tell me, what does the "--prefix=/usr" option do?

Thanks!![/QUOTE]

Glad to hear it went well!  The --prefix option simply sets things up so the app is installed into /usr/bin (where most apps are installed by default in Ubuntu) as opposed to the traditional /usr/local/bin (historically used for single-user installs).

---

### Post by desperado666 on 2007-11-26
In Order to compile MSN and Google Talk Support you need following packages for feisty

libgnutls-dev

and you have to compile with this option

```
./configure --enable-gnutls=yes 

```

to enable SSL Support

More here
[https://help.ubuntu.com/community/Pidgin](https://help.ubuntu.com/community/Pidgin)

I had to compile pidgin with dh_make. Maybe you can describe this option to compile pidgin successfully.

---

### Post by qbox on 2007-11-26
hmm I have more problems with new version.
I cant see pictures, animation pictures in conversations I cant send smiles and stuff like that

EDIT:
cool I du 
sudo apt-get update
and Im on the version 2.2.1 again.

---

### Post by Rippie on 2007-11-28
Hello guys....

Im gonna try compile Pidgin 2.3 later when i get home, and im going to follow this guide here, i think you all should try it and lets take it from there.


1 Step: Close pidgin
2 Step: Remove pidgin with sudo apt-get remove pidgin
3 Step: Follow this guide [https://help.ubuntu.com/community/Pidgin](https://help.ubuntu.com/community/Pidgin)

I will post in here how it all turns out later when back from work..

---

### Post by Rippie on 2007-11-28
Yeah !! got Pidgin 2.3 to work !!

---

### Post by goldencako on 2007-11-28
Thanks for the post. I used it to update to 2.30. Cheers!

---

### Post by trusatori on 2007-11-28
I've updated the guide to reflect the new release.  Thanks to goldencako for testing it out! ;]

---

### Post by desperado666 on 2007-11-30
compilation works with feisty and pidgin 2.3 (compiled with dh_make)

---

### Post by qbox on 2007-11-30
qbox@qbox:~/Desktop/pidgin-2.3.0$ ./configure --prefix=/usr --enable-gnutls=yes
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
qbox@qbox:~/Desktop/pidgin-2.3.0$

EDIT:
its fine now. I need sudo command

EDIT:
when I install new version of pidgin I receive security update alert. if I do this update Im back to older version.
What to do.

---

### Post by qbox on 2007-11-30
Thats IT IM TIRED from pidgin. When someone try to write me I didnt receive nothing.
[www.meebo.com](www.meebo.com) from now on.

---

### Post by trusatori on 2007-11-30
> **qbox said:**
> qbox@qbox:~/Desktop/pidgin-2.3.0$ ./configure --prefix=/usr --enable-gnutls=yes
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
qbox@qbox:~/Desktop/pidgin-2.3.0$

EDIT:
its fine now. I need sudo command

EDIT:
when I install new version of pidgin I receive security update alert. if I do this update Im back to older version.
What to do.

Take a look at the bottom of the guide, under "Other Notes."  There are instructions on how to get update-manager to stop "upgrading" you back to the old version.  As for you not receiving messages from other people, I'm a bit stumped as I've never heard that happening to anyone (at least, for any reason that wasn't network related).

---

### Post by Chonnawonga on 2007-12-06
trusatori,

I think there may be a small error in the updated guide (2.3.0). You have this:
```
tar -jxvf pidgin-2.3.0
```
...but that doesn't work, because there's nothing with that name. Should it be this?
```
tar -jxvf pidgin-2.3.0.tar.bz2
```
Or perhaps this?
```
tar -jxvf pidgin-2.3.0*
```

But then, n00b that I am, it's entirely possible that I've missed something.

---

### Post by marianlibrarian on 2007-12-06
I sure wish just once I could follow installation instructions in Ubuntu and it would work... (sigh)

Here goes:
At the following command:
sudo apt-get build-dep pidgin
I get the following response:
> librarian@ubuntuserver:~$ sudo apt-get build-dep pidgin
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for pidgin

I downloaded the package from: [http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)

I can unzip or unpack it to some mysterious place on the hard drive and I don't have a clue how to make it be an application that is usuable. 

so what do I do now?? I have this installed on my windows xp machine in about 3 minutes. I have been struggling with ubuntu's install for well over an hour. Unfortunately this is a work machine for a library and I don't have an hour to spare for this kind of head ache. 

Isn't there a manual somewhere that has these standard - used alot kind of applications in something like alphabetical order that I could just go to and read and do it and it works???

Better yet, WHY DOESN'T PIDGIN HAVE INSTRUCTIONS ON HOW TO INSTALL THEIR SOFTWARE????

---

### Post by Chonnawonga on 2007-12-06
Hi marian,

I understand your frustration. Terminal stuff can be a real pain in the @$$, especially for those (like me) who are more comfortable in a graphic environment.

Have you tried installing the version of Pidgin that's available through the Applications menu, under Add/Remove? There's really nothing wrong with that: the folks on this thread are just trying to use the newest and latest, for whatever reason.

Regards,
Chonnawonga

---

### Post by Gourgi on 2007-12-07
great straight-through guide !
man you :guitar:
:)
i just installed pidgin 2.3.0 in hardy tribe1 without problems 
yeah , that's right ... **hardy 8.04** ! it is my experiment-install :lolflag:

now i have the .deb package to install to my primary gutsy installation
thanks again ! :)

---

### Post by trusatori on 2007-12-07
Chonna:
Absolutely correct sir!  Good eye and thanks for the heads up!

---

### Post by marianlibrarian on 2007-12-10
I went to my applications "add/remove" - pidgen isn't there but GAIM is and it is already installed.... I am trying now to logon with it but it doesn't seem to work for an aol account. oh well, i have wasted too much time on this now. 

It is the little things that make it so frustrating. There are so many versions of Ubuntu and I am not with the newest. I am hanging on to Dapper Drake because it has the longest support time. I also take care of nine ubuntu machines. I make sure they are updated on a weekly basis. I am one lonely rural librarian, who doesn't have time to "experiment". I just need it to do what I need it to do. 

Right now, I have given up on pidgen or what used to be GAIM. Just like I have given up on several other programs. Maybe someday I will have the luxury of time and can experiment with Ubuntu. It sounds like fun.

---

### Post by Chonnawonga on 2007-12-10
Marian,

I'm sorry you're having so much difficulty. Staying with Dapper Drake has its merits: it's highly stable. The trade-off is that you don't get the latest software. The next long-term-support release is in April: that might be a good time to update your machines so that they have the latest software, including the whatever version of Pidgin is current at that time.

I hope you can hang on until then!

---

### Post by IeU on 2007-12-10
for some reason, it is not working for me . . .

```

pidgin 2.3.1

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : bonjour gg irc jabber msnp9 myspace novell oscar qq sametime simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification...... : yes
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : yes

Print debugging messages...... : no

Pidgin will be installed in /usr/bin.

configure complete, now type 'make'

felipe@felipe-desktop:~/Linux Donwloads/pidgin-2.3.1$ 

```

the end of "make" . . .
```

mv -f .deps/libxmpp.Tpo .deps/libxmpp.Plo
/bin/bash ../../../libtool --silent --tag=CC   --mode=link gcc  -g -g -O2 -module -avoid-version  -o libxmpp.la -rpath /usr/lib/purple-2 libxmpp.lo libjabber.la -lnsl -lresolv 
libtool: link: warning: `/usr/lib64/libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libxml2.la' seems to be moved
/bin/sed: can't read Donwloads/pidgin-2.3.1/libpurple/protocols/jabber/libjabber.la: No such file or directory
libtool: link: `Donwloads/pidgin-2.3.1/libpurple/protocols/jabber/libjabber.la' is not a valid libtool archive
make[5]: *** [libxmpp.la] Error 1
make[5]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple/protocols/jabber'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple/protocols'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1'
make: *** [all] Error 2
felipe@felipe-desktop:~/Linux Donwloads/pidgin-2.3.1$ 
```

what is going wrong ?

---

### Post by IeU on 2007-12-11
bump :)

---

### Post by Gourgi on 2007-12-11
> **IeU said:**
> bump :)

after i succesfully installed 2.3.0 @ hardy (see few posts back) , i also successfully installed 2.3.1 to gutsy.
i just followed the first post !
i don't think i can help you.
maybe unistall and clean dependencies and start over again ?

---

### Post by marianlibrarian on 2007-12-11
>  		Marian,

I'm sorry you're having so much difficulty. Staying with Dapper Drake has its merits: it's highly stable. The trade-off is that you don't get the latest software. The next long-term-support release is in April: that might be a good time to update your machines so that they have the latest software, including the whatever version of Pidgin is current at that time.

I hope you can hang on until then!

I am going to wait. Patience has its positive side - somewhere around here.  I used to use GAIM in windows years ago and really liked it. I still like 6.06 because as much as I wish, I don't have time to "play" with an operating system. The learning curve is just too steep for me.

---

### Post by IeU on 2007-12-11
i am waiting too, but would like to solve my problem posted above :)

---

### Post by trusatori on 2007-12-11
> **IeU said:**
> i am waiting too, but would like to solve my problem posted above :)

Are you running 64 bit Ubuntu?  I'm thinking that may have something to do with it but I don't have any experience with compiling in 64 bit land.  Hopefully someone will come by who does.

In the mean time, you may want to grab the 64 bit deb for 2.3.0 from [here]("http://www.getdeb.net/app.php?name=Pidgin").

---

### Post by IeU on 2007-12-11
> **trusatori said:**
> Are you running 64 bit Ubuntu?  I'm thinking that may have something to do with it but I don't have any experience with compiling in 64 bit land.  Hopefully someone will come by who does.

In the mean time, you may want to grab the 64 bit deb for 2.3.0 from [here]("http://www.getdeb.net/app.php?name=Pidgin").

thanks mate

---

### Post by Gourgi on 2007-12-11
> **trusatori said:**
> Are you running 64 bit Ubuntu?  I'm thinking that may have something to do with it but I don't have any experience with compiling in 64 bit land.  Hopefully someone will come by who does.

i forgot to say that i do use AMD64 in both 7.10 & 8.04 ubuntu and still had no problem at compiling !

---

### Post by nukturnal on 2007-12-12
After going through enough compilation drama for two days, I realized the compilation and configuration process was all ok except when it comes to issuing the ultimate "make install" command. I decided to try "sudo make install" and at last pidgin installation successfully completed. 

Hope it helps somebody out

---

### Post by Gourgi on 2007-12-12
> **nukturnal said:**
> After going through enough compilation drama for two days, I realized the compilation and configuration process was all ok except when it comes to issuing the ultimate "make install" command. I decided to try "sudo make install" and at last pidgin installation successfully completed. 

Hope it helps somebody out

using sudo is clearly mentioned in the first post
i propose you always use sudo when you type ```
sudo make install
```
maybe you should try 
```
sudo checkinstall
``` instead 
it will give you a .deb package and automatically install th package and if you want to uninstall it you can doing via synaptic ;)

---

### Post by trusatori on 2007-12-12
> **Gourgi said:**
> using sudo is clearly mentioned in the first post
i propose you always use sudo when you type ```
sudo make install
```
maybe you should try 
```
sudo checkinstall
``` instead 
it will give you a .deb package and automatically install th package and if you want to uninstall it you can doing via synaptic ;)

+1 ;]

---

### Post by abzolutxero on 2007-12-15
> **marianlibrarian said:**
> I sure wish just once I could follow installation instructions in Ubuntu and it would work... (sigh)

Here goes:
At the following command:
sudo apt-get build-dep pidgin
I get the following response:


I downloaded the package from: [http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)

I can unzip or unpack it to some mysterious place on the hard drive and I don't have a clue how to make it be an application that is usuable. 

so what do I do now?? I have this installed on my windows xp machine in about 3 minutes. I have been struggling with ubuntu's install for well over an hour. Unfortunately this is a work machine for a library and I don't have an hour to spare for this kind of head ache. 

Isn't there a manual somewhere that has these standard - used alot kind of applications in something like alphabetical order that I could just go to and read and do it and it works???

Better yet, WHY DOESN'T PIDGIN HAVE INSTRUCTIONS ON HOW TO INSTALL THEIR SOFTWARE????

i got the same error, "E: Unable to find a source package for pidgin"

i manually added some dependencies based on the the installation instructions on ubuntu.com, but there were 3 that were unable to be resolved.  

is this a problem?

---

### Post by survient on 2007-12-15
what is the benefit of 2.3 anyway?

---

### Post by Bunnykun on 2007-12-15
> **IeU said:**
> for some reason, it is not working for me . . .

```

pidgin 2.3.1

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : bonjour gg irc jabber msnp9 myspace novell oscar qq sametime simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification...... : yes
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : yes

Print debugging messages...... : no

Pidgin will be installed in /usr/bin.

configure complete, now type 'make'

felipe@felipe-desktop:~/Linux Donwloads/pidgin-2.3.1$ 

```

the end of "make" . . .
```

mv -f .deps/libxmpp.Tpo .deps/libxmpp.Plo
/bin/bash ../../../libtool --silent --tag=CC   --mode=link gcc  -g -g -O2 -module -avoid-version  -o libxmpp.la -rpath /usr/lib/purple-2 libxmpp.lo libjabber.la -lnsl -lresolv 
libtool: link: warning: `/usr/lib64/libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib64/libxml2.la' seems to be moved
/bin/sed: can't read Donwloads/pidgin-2.3.1/libpurple/protocols/jabber/libjabber.la: No such file or directory
libtool: link: `Donwloads/pidgin-2.3.1/libpurple/protocols/jabber/libjabber.la' is not a valid libtool archive
make[5]: *** [libxmpp.la] Error 1
make[5]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple/protocols/jabber'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple/protocols'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/felipe/Linux Donwloads/pidgin-2.3.1'
make: *** [all] Error 2
felipe@felipe-desktop:~/Linux Donwloads/pidgin-2.3.1$ 
```

what is going wrong ?


I had this same issue, and even went through a linux reinstall (with it's own host of problems) before returning to the exact same problem.

It turns out the problem was that my path to the root of the source had spaces.  I had it in /home/program sources/pidgin/pidgin-2.3.1  .  Changing it to /home/sources/pidgin/pidgin-2.3.1 allowed installation with no problems. 

I'm a growing linux newbie, so I don't know if this is a typical consideration of compiling source, or if it just an issue unique with this particular installation, but I now know to just avoid it in the future

---

### Post by trusatori on 2007-12-16
> **survient said:**
> what is the benefit of 2.3 anyway?

Check out the change log which can either be found on the pidgin site or via the link on the tutorial to see exactly what's fresh in each release.

And Bunny, that's a really interesting issue / fix, and I'm sure it can probably help out more than a few people.

---

### Post by bfoos on 2007-12-19
Can someone here please explain what is wrong here? I followed the directions in the first post, compiled and installed 2.3.1 from source. Everything went swimmingly. Now after the big samba and kernel update this morning, all I get upon attempting to launch pidgin is...

```
symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error
```

There is virtually no information out there regarding this issue and I'm at a loss. I tried reverting to pidging 2.2.1 and while that version will launch, there are no protocols present. Any advise would be appreciated.

---

### Post by trusatori on 2007-12-20
> **bfoos said:**
> Can someone here please explain what is wrong here? I followed the directions in the first post, compiled and installed 2.3.1 from source. Everything went swimmingly. Now after the big samba and kernel update this morning, all I get upon attempting to launch pidgin is...

```
symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error
```

There is virtually no information out there regarding this issue and I'm at a loss. I tried reverting to pidging 2.2.1 and while that version will launch, there are no protocols present. Any advise would be appreciated.

Hm, I've done the samba / kernel upgrades on multiple computers, all of which were also running 2.3.1 prior to the upgrade and have not experienced this yet.  I'm going to have to look into this...

---

### Post by bfoos on 2007-12-20
> **trusatori said:**
> Hm, I've done the samba / kernel upgrades on multiple computers, all of which were also running 2.3.1 prior to the upgrade and have not experienced this yet.  I'm going to have to look into this...
I honestly have no clue why it happened. I can't say for sure it was any of the updates that got pushed through yesterday, it just happened that after I installed them and rebooted, Pidgin no longer worked. I suspect it had something to do with all of the messing around with libpurple I did when I first tried compiling 2.3.0.

Anyway, I was able to launch 2.3.1 after removing it's config files from my .purple directory. However, I was unable to sort whatever issue was causing the protocol list to be empty. I wanted to start fresh with my home directory on it's own partition anyway, so I just reinstalled Gutsy.

---

### Post by timephoenix on 2007-12-21
Hey folks. I'm trying and failing to compile Pidgin on Feisty. When running make, here's what I get:

libtool: install: warning: relinking `libxmpp.la'
/bin/bash: ../../../libtool: No such file or directory
libtool: install: error: relink `libxmpp.la' with the above command before installing it
make[5]: *** [install-pkgLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple/protocols/jabber'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple/protocols/jabber'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple/protocols'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.


Any help is appreciated.

---

### Post by trusatori on 2007-12-21
> **timephoenix said:**
> Hey folks. I'm trying and failing to compile Pidgin on Feisty. When running make, here's what I get:

libtool: install: warning: relinking `libxmpp.la'
/bin/bash: ../../../libtool: No such file or directory
libtool: install: error: relink `libxmpp.la' with the above command before installing it
make[5]: *** [install-pkgLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple/protocols/jabber'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple/protocols/jabber'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple/protocols'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/josh/Install/pidgin-2.3.1/libpurple'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.


Any help is appreciated.

The key to compiling on Feisty is the use of dh_make.  Hopefully someone with Feisty compiling experience can shed some light on the procedure for you.

---

### Post by unityofsaints on 2007-12-22
Great guide, worked a charm, thx!

---

### Post by Knowles on 2007-12-22
> **bfoos said:**
> Can someone here please explain what is wrong here? I followed the directions in the first post, compiled and installed 2.3.1 from source. Everything went swimmingly. Now after the big samba and kernel update this morning, all I get upon attempting to launch pidgin is...

```
symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error
```

There is virtually no information out there regarding this issue and I'm at a loss. I tried reverting to pidging 2.2.1 and while that version will launch, there are no protocols present. Any advise would be appreciated.

When you install gutsy it install pidgin by default however if you simply remove pidgin such as

```
apt-get remove pidgin
```

some bits still remain, in my case it was the library libpurple0, for some reason this main library of pidgin was still present

```
apt-get purge libpurple*
```

removed the file and now my pidgin compiled by source works,

---

### Post by bfoos on 2007-12-23
I had tried purging libpurple0. However, it made absolutely no difference. The protocol list was still unpopulated. As I said above. I couldn't figure out any way to rectify the issue, so I just wound up reinstalling Gutsy. I have Pidgin 2.3.1 compiled from source and installed now.

---

### Post by kr0n1x on 2007-12-24
Thanks it worked perfectly in Fluxbuntu :)

---

### Post by BattlePanic on 2007-12-27
I just attempted this howto on Gutsy Gibbon and it worked great.  I'd never compiled and installed from source before so I learned a few new things on this howto.  Thanks for all your work.

The only snag I ran into was when I was removing pidgin, pidgin-data, and libpurple0.  APT gave some complaints about the 'gaim' package being installed and as a result, it wanted to remove the 'ubuntu-desktop' package among other things.  This didn't sound right, so I removed the gaim package via synaptic since this package was described as being merely transitional and nonessential.  I tried to remove pidgin once more and APT had no complaints with the gaim package now removed.

---

### Post by BattlePanic on 2007-12-27
One other thing,

I just fired up Synaptic so that I could lock the pidgin, pidgin-data, and libpurple0 packages as described in the howto.  After searching for all three, Synaptic tells me that only the pidgin package is installed.  Did I somehow how skip installing pidgin-data and libpurple0?  Pidgin seems to work so I'm assuming all three packages must installed somewhere on my system.  Why is Synaptic telling me otherwise?

---

### Post by Luis Macias on 2007-12-27
Hi, thanks for the guide, i just have one problem, in the terminal i had "installing debian package" for about 1 hour, so i close it, but i can open pidgin correctly, the thing is i dont have the icon... so this means its not installed correctly?? Thansk a lot for the post!

---

### Post by BattlePanic on 2007-12-27
Luis Macias,

While checkinstall was running I noticed the same problem at "Installing Debian Package"  According to trusatori in his original post:

> **trusatori said:**
> Note: Sometimes, for reasons I don't fully understand, checkinstall will seemingly stop doing its business at "Installing Debian Package." In the event that this happens, simply press enter to accept whatever dialog is appearing and checkinstall is hiding from you. I believe it's asking if you want to overwrite an old file leftover from the old install (and therefore answering yes is the way to go), but can anyone confirm this?

After more text floods the screen, you should have Pidgin compiled and installed. Try running it by typing 'pidgin'.

So you may try removing pidgin and redoing the compile and install, and just press enter when you get to that stage.  Hope this helps.

---

### Post by BattlePanic on 2007-12-27
I just noticed that the GNOME menu item for pidgin, normally located under Applications -> Internet -> Pidgin Internet Messenger, is missing it's associated icon (the little purple pigeon).

Is this normal?  Do I have to reconfigure my GNOME menu and specify pidgin's associated icon or should I expect this to be done automatically for me?  Is there a usual place where a program's associated icons are stored?

---

### Post by Luis Macias on 2007-12-28
Thanks, i think i will leave it like this, because it works perfectly, is only the icon, so i justed added an icon. Thanks for your reply

---

### Post by trusatori on 2007-12-28
> **BattlePanic said:**
> One other thing,

I just fired up Synaptic so that I could lock the pidgin, pidgin-data, and libpurple0 packages as described in the howto.  After searching for all three, Synaptic tells me that only the pidgin package is installed.  Did I somehow how skip installing pidgin-data and libpurple0?  Pidgin seems to work so I'm assuming all three packages must installed somewhere on my system.  Why is Synaptic telling me otherwise?

If Pidgin is running okay on your system, you can rest assured that you have the necessary packages installed.  It's possible that due to your configuration the other two packages got consolidated into your pidgin package, which is fine, as long as all works well.

> **BattlePanic said:**
> I just noticed that the GNOME menu item for pidgin, normally located under Applications -> Internet -> Pidgin Internet Messenger, is missing it's associated icon (the little purple pigeon).

Is this normal?  Do I have to reconfigure my GNOME menu and specify pidgin's associated icon or should I expect this to be done automatically for me?  Is there a usual place where a program's associated icons are stored?

I find that this happens sometimes after a compile and install and I noticed that it usually fixes itself after a reboot or two.  Not real sure what causes it ;\.

---

### Post by Ownager on 2007-12-28
3) Download and compile Pidgin

The pidgin source can be found at pidgin.im or directly by clicking here.
Extract the archive either by right-clicking on it and clicking "extract here" or by running the following command in terminal:
Code:

tar -jxvf pidgin-2.3.1.tar.bz2

Get into your newly created directory:
Code:

cd pidgin-2.3.1/

Get compiling! Retrieve a beer and/or cup of tea as, depending on the speed of your computer, the 'make' command may take some time.
Code:

./configure --prefix=/usr --enable-gnutls=yes
make
sudo checkinstall

(For those interested, the '--enable-gnutls=yes' is required for Google Talk and MSN support.)

Enjoy watching the waterfall of text for a bit. When presented with a series of questions after running 'sudo checkinstall' simply press enter to accept the defaults.

*Important Note* Sometimes, for reasons I don't fully understand, checkinstall will seemingly stop doing its business at "Installing Debian Package." In the event that this happens, simply press enter to accept whatever dialog is appearing and checkinstall is hiding from you. I believe it's asking if you want to overwrite an old file leftover from the old install (and therefore answering yes is the way to go), but can anyone confirm this?

After more text floods the screen, you should have Pidgin compiled and installed. Try running it by typing 'pidgin'.
-------------------------------------------------------------------------------


I don't really understand this very well. I already downloaded pidgin 2.3.1.

I extracted it into desktop....

What's up with ./configure --prefix=/usr --enable-gnutls=yes make sudo checkinstall
? 

I don't really understand this. I tried that in terminal. It doesn't work. Where can I compile it? Where can I type this? Do I still have to type in terminal? You should have said something more about this one.

---

### Post by BattlePanic on 2007-12-29
> **Ownager said:**
> 
What's up with ./configure --prefix=/usr --enable-gnutls=yes make sudo checkinstall
? 

I don't really understand this.

Those are actually three separate commands.  I think your problem may be that you're trying to type them in all on one line.  If you had no problems up to that point, you're doing well and are not far off.  

Before we you get you back on track, to make things a bit more clear, wherever you see <ENTER> written in my code examples, type the "Enter" key instead.

If you've already extracted the pidgin source code to a directory on your Desktop, open up a terminal window and switch to that directory by entering the following:

```
cd ~/Desktop/<name_of_pidgin_directory><ENTER>
```

just make sure to replace <name_of_pidgin_directory> with whatever the directory containing the pidgin source code is named.

Now type the following commands, remembering that <ENTER> actually means press the "Enter" key:

```

./configure --prefix=/usr --enable-gnutls=yes<ENTER>
make<ENTER>
sudo checkinstall<ENTER>

```

Also note that your computer will have to do some work between each of these commands.  Wait for each command to finish executing and return you to the prompt before entering the next command.  Refer to the original howto where you left off and hopefully you'll have pidgin up and running.

---

### Post by BattlePanic on 2007-12-29
> **BattlePanic said:**
> I just noticed that the GNOME menu item for pidgin, normally located under Applications -> Internet -> Pidgin Internet Messenger, is missing it's associated icon (the little purple pigeon).


Curiously, the icon just returned after I used gnome-app-install (under Applications -> Add/Remove) to install an unrelated program.  It appears that while doing this, gnome-app-install also restored my pidgin icon.  I'm not not 100% sure on this but it looks to be the case.

---

### Post by Arwen on 2007-12-29
HELLO!
I get an error when it executes "sudo checkinstall'':

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: y

logfile:

(Reading database ... ......)
Extracting pidgin (from .../pidgin_2.3.1-1_i386.deb) ...
dpkg: pidgin: warning - file `etc/gconf' is not common file or link (
= `/etc/gconf')
dpkg: pidgin: warning - file`etc/gconf/gconf.xml.defaults' is not common file or link
 (= `/etc/gconf/gconf.xml.defaults')
dpkg: error in processing /home/felicia/PIDGIN/pidgin-2.3.1/pidgin_2.3.1-1_i386.deb (--
install):
trying to replace  `/usr/bin/strip', that is also in package binutils
dpkg-deb: the subprocess paste was killed from signal (Broken pipe)
Errors occured during processing:
 /home/felicia/PIDGIN/pidgin-2.3.1/pidgin_2.3.1-1_i386.deb

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


*****I translated logfile in english,I think it's still clear about the errors I get.

Thanx for any help!

---

### Post by Sharpeee on 2007-12-29
I've got the same error as Arwen when running 'checkinstall':

(Reading database ... 110228 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.3.1-1_i386.deb) ...
dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain file or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing pidgin_2.3.1-1_i386.deb (--install):
 trying to overwrite `/usr/bin/ld', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 pidgin_2.3.1-1_i386.deb

---

### Post by isaacj87 on 2008-01-02
> **Sharpeee said:**
> I've got the same error as Arwen when running 'checkinstall':

(Reading database ... 110228 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.3.1-1_i386.deb) ...
dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain file or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing pidgin_2.3.1-1_i386.deb (--install):
 trying to overwrite `/usr/bin/ld', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 pidgin_2.3.1-1_i386.deb

I noticed you are running Feisty...I can confirm that the majority of the tutorial does work with Feisty, but there are a few things that didn't...

I had to use this guide as well...
[http://help.ubuntu.com/community/Pidgin]("http://help.ubuntu.com/community/Pidgin")

But to answer your question, I found another tutorial that had this for checkinstall...
```
sudo checkinstall –exclude=/etc/gconf,/usr/bin,/usr/lib
```

Seems like it could solve your problem. I haven't tried it yet as I don't like checkinstall. But you could could give it a try. :)

---

### Post by kevdog on 2008-01-02
I gave up on the checkinstall and just went with the old sudo make install.  Sure its outside the apt system, but I have managed to survive w/o a problem with Edgy->Feisty->Gutsy w/o a problem.  I think with Hardy I am going to start over.

---

### Post by isaacj87 on 2008-01-03
> **kevdog said:**
> I gave up on the checkinstall and just went with the old sudo make install.  Sure its outside the apt system, but I have managed to survive w/o a problem with Edgy->Feisty->Gutsy w/o a problem.  I think with Hardy I am going to start over.

That's what I had to do...good ol' "sudo make install"

I don't like checkinstall anyways :)

---

### Post by Daniel15 on 2008-01-03
Any idea how to obtain/compile the MSNP13 branch of Pidgin? This is an updated branch of Pidgin that supports a newer version of the MSN protocol (including personal messages, offline messaging, etc.), but I can't find  where to get the new code from. Any idea? :P

---

### Post by z|x on 2008-01-19
I followed the commands exactly as mentioned above, but I still receive the error "No TLS/SSL support found.

---

### Post by MilitantPotato on 2008-01-21
I followed the guide, everything is fine untill i run sudo checkinstall

It errors with:

> *************************************

*** Warning: The package version "%pidginver" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

so I enter 2.3.1:tater1 and it continues.

It gets to the package info and it's all messed up.
> This package will be built according to these values:

0 -  Maintainer: [ root@home1 ]
1 -  Summary: [ A GTK+ based multiprotocol instant messaging client
Development headers, documentation, and libraries for Pidgin
libpurple library for IM clients like Pidgin and Finch
Development headers, documentation, and libraries for libpurple
Bonjour plugin for Pidgin
Lotus Sametime plugin for Pidgin using the Meanwhile library
Mono .NET plugin support for Pidgin
A text-based user interface for Pidgin
Headers etc. for finch stuffs ]
2 -  Name:    [ pidgin ]
3 -  Version: [ 2.3.1:tater1 ]
4 -  Release: [ 0%{?beta ]
5 -  License: [ GPL ]
6 -  Group:   [ Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet
Applications/Internet ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ pidgin ]
9 -  Alternate source location: [  ]
10 - Requires: [ gconf2
gconf2
gconf2
GConf2
GConf2
GConf2
perl
libpurple = %{version}
pidgin = %{version}, libpurple-devel = %{version}
gtk2-devel
pkgconfig
libpurple = %{version}
pkgconfig
libpurple >= %{apiver}
libpurple >= %{apiver}
libpurple >= %{apiver}
libpurple = %{version}
finch = %{version}, libpurple-devel = %{version}
ncurses-devel
pkgconfig ]

Enter a number to change any of them or press ENTER to continue:



I've no idea what to do at this point since it fails to make a debian due to the settings above.

---

### Post by aaronfromchina on 2008-01-23
Very good guide.

I successfully compile and install pidgin 2.3.1 by following the instruction.

Thanks very much!

---

### Post by yizuman on 2008-02-10
> **trusatori said:**
> Also, because of an inconsistency in version naming, update-manager or your other package managers may attempt to "upgrade" you back down to the old version that's in the repos, thinking that it's newer. To get this to stop happening, open Synaptic and search for pidgin, pidgin-data, and libpurple0 (you'll have to do this one by one as it resets your search after each). After searching for each, highlight it and click on 'Package->Lock Version' up top. This will keep update-manager from touching it and constantly suggesting an update.

I've tried locking them as discribed, the "package" tab is ghosted and won't let me do anything. What am I doing wrong?

Everything worked perfectly as mentioned on page 1 of this thread though.

Yiz

---

### Post by trusatori on 2008-02-10
> **yizuman said:**
> I've tried locking them as discribed, the "package" tab is ghosted and won't let me do anything. What am I doing wrong?

Everything worked perfectly as mentioned on page 1 of this thread though.

Yiz

Hm, my "package" is never grayed out for me up top on the menu bar.  This may sound ridiculous, but are you sure you're highlighting the package before trying to click it?  Otherwise, I'm truly stumped.

---

### Post by BattlePanic on 2008-02-21
I completed this HOWTO a while back.  Now I want to install the pidgin-guifications package using the Synaptic Package Manager.  When I mark pidgin-guifications for installation I get an error stating there there were unresolvable dependencies:

> Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

pidgin-guifications:
Depends: pidgin(>=1:2.0) but 2.3.1-1 is to be installed

I'm guessing this has to do with the "1:" prefix in the required pidgin version.  I'm not sure what this means though.  This error message doesn't quite make sense either.  It says that 2.3.1-1 is to be installed but, in fact, it already is installed.  I'm not familiar with dependencies or version numbering.  Can anyone tell me of a fix to my current problem?

---

### Post by kevdog on 2008-02-22
> **z|x said:**
> I followed the commands exactly as mentioned above, but I still receive the error "No TLS/SSL support found.

Try this 

sudo aptitude install libnss3-dev

You are then going to have to reconfigure and recompile.  During the process where you type 

./configure -- Look at the messages in the very first part.  It should tell you if there is SSL/TLS support.

---

### Post by Oldsoldier2003 on 2008-02-24
When following the tutorial purging pidgin caused the removal of Ubuntu-desktop. I am aware that this is a dummy package, and reinstalling it would be necessary to ensure a proper upgrade from Gutsy 7.10 in the future...

My question is this:
Since reinstalling Ubuntu-desktop would reinstall a lot of the stuff i painstakingly trimmed from my system, will ** NOT** reinstalling Ubuntu-desktop create ant issues for the normal operation and updates of my system? (I suspect not, but I'm a little paranoid )

I would also like to thank trusatori for taking the time to post this tutorial it was very helpful, because as a newbie to compiling apps I didn't think about the configure options, he saved me a couple recompiles :)

---

### Post by h2z on 2008-02-27
```

stefan@stefan-ubuntu:~$ sudo apt-get build-dep pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for pidgin

```

This is what I get when trying to build the dependencies for pidgin, any suggestions :confused:



EDIT: After reading the official Pidgin FAQ on their main site, all that is needed to make this work is **enable "Source Code"** in the Software Sources screen (System->Admin->Software Sources).

---

### Post by mdkaneda55 on 2008-03-02
love the guide. =) but i just got done reading thru pages & pages of people's issues... just wanted to point out that if anyone gets fed up w/ the compiling process, there's always getdeb.. 

[http://getdeb.net/comment.php?rel_id=2259](http://getdeb.net/comment.php?rel_id=2259)

of course some of their packages have 'issues'.. but most all work well. i do recommend compiling though, but for those who don't understand the concept & get frustrated, theres always an easier route =)

---

### Post by trusatori on 2008-03-02
BattlePanic:

> **trusatori said:**
> Chonna:
I just played around with it and found out that it's easiest to get this working by compiling Guifications yourself.  The source can be found [here]("http://downloads.guifications.org/plugins//Guifications2/pidgin-guifications-2.14.tar.bz2").  Once you extract and cd into the folder...
```

./configure --prefix=/usr
make
sudo checkinstall
```
(Leave out the --prefix=/usr part ONLY if you didn't use it during the compile of Pidgin [and used the ln-s fix instead].  If you did follow the original tutorial verbatim, however, copy and paste the above commands).

Just like you did when compiling Pidgin and it should show up under Tools->Plugins in Pidgin.  Let me know how that works for you.


Oldsoldier:
Solid question.  I imagine it shouldn't give you any trouble at all, since what it will be comparing are the actual package versions during a dist-upgrade and not the dummy packages, so I'm thinking you're in the clear.  Do report back if it does oddly present an issue and I'll gladly do what I can to help ;].

h2z:
For some reason, it never hit me that enabling those was a necessary step.  I'll add it to the guide and certainly give you credit.

---

### Post by mafsi on 2008-03-03
followed the instruction and succeded to install pidgin 2.4.0

i have an amendament although.

when i tried:

```

make
sudo checkinstall

```

i had erros so i imput
[B]
sudo make[/B]

insted of "make"

---

### Post by trusatori on 2008-03-03
> **mafsi said:**
> followed the instruction and succeded to install pidgin 2.4.0

i have an amendament although.

when i tried:

```

make
sudo checkinstall

```

i had erros so i imput
[B]
sudo make[/B]

insted of "make"

Hmm, I had no problems installing 2.4.0 with a 'make' instead of a 'sudo make', but YMMV.  Thanks for testing it out ;]

---

### Post by sandgroper3 on 2008-03-05
I have been successful with the compilation and installation of Pidgin on both Kubuntu and Ubuntu 7.10 using the above procedure.

However, users should be warned that if they allow the update managers in both Kubuntu and Ubuntu to 'update' libpurple, pidgin, and pidgin data, their pidgin installation will be broken.

I suspect that dpkg or apt configuration is required to prevent update acting on the new version of pidgin.

I am still attempting to figure out how to do this (ie prevent update managers from acting on the newly installed pidgin).

Can anyone shed some light on this?

Thanks :)

---

### Post by sandgroper3 on 2008-03-05
Thank you Trusatori for this most enlightening learning experience. Indeed the changes required to pevent 'unwanted updates' are there in 'Other Notes'.

Thanks again, I am really enjoying the new pidgin.:) :) :)

---

### Post by sandgroper3 on 2008-03-07
> **marianlibrarian said:**
> I sure wish just once I could follow installation instructions in Ubuntu and it would work... (sigh)

Here goes:
At the following command:
sudo apt-get build-dep pidgin
I get the following response:


I downloaded the package from: [http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)

I can unzip or unpack it to some mysterious place on the hard drive and I don't have a clue how to make it be an application that is usuable. 

so what do I do now?? I have this installed on my windows xp machine in about 3 minutes. I have been struggling with ubuntu's install for well over an hour. Unfortunately this is a work machine for a library and I don't have an hour to spare for this kind of head ache. 

Isn't there a manual somewhere that has these standard - used alot kind of applications in something like alphabetical order that I could just go to and read and do it and it works???

Better yet, WHY DOESN'T PIDGIN HAVE INSTRUCTIONS ON HOW TO INSTALL THEIR SOFTWARE????

If you're getting this message when you are attempting to get pidgin dependencies it makes me think that you do not have the necessary repositories. I would suggest that you look at the following web site (in particular, the section called: *Extra Repositories* )for guidance with regard to repositories:
[INDENT][http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)[/INDENT]

Good luck. :)

---

### Post by yizuman on 2008-07-02
Getting an error...

new version is out... 2.4.3

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lo lt mk my_MM nb ne nl nn oc pa pl pt_BR pt ps ro ru si sk sl sq sr sr@latin sv ta te th tr uk ur vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for fileno()... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for GTK... yes
checking for PANGO... yes
checking for X11... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... yes
checking for SmcSaveYourselfDone in -lSM... yes
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
checking for X11/SM/SMlib.h... yes
checking for STARTUP_NOTIFICATION... yes
checking for GTKSPELL... yes
checking for initscr in -lncursesw... yes
checking for update_panels in -lpanelw... yes
checking /usr/include/ncursesw/ncurses.h usability... yes
checking /usr/include/ncursesw/ncurses.h presence... yes
checking for /usr/include/ncursesw/ncurses.h... yes
checking if /usr/include/ncursesw/ncurses.h supports wide characters... yes
checking for LIBXML... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for GSTREAMER... yes
checking for gst_registry_fork_set_enabled in -lgstreamer-0.10... yes
checking for MEANWHILE... yes
checking for AVAHI... yes
checking avahi-client/client.h usability... yes
checking avahi-client/client.h presence... yes
checking for avahi-client/client.h... yes
checking avahi-glib/glib-malloc.h usability... yes
checking avahi-glib/glib-malloc.h presence... yes
checking for avahi-glib/glib-malloc.h... yes
checking for avahi_client_new in -lavahi-client... yes
checking for SILC... no
checking for SILC... no
checking for SILC... no
checking for GADU... yes
checking for libgadu GPL compatibility... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for -Waggregate-return option to gcc... yes
checking for -Wcast-align option to gcc... yes
checking for -Wdeclaration-after-statement option to gcc... yes
checking for -Wendif-labels option to gcc... yes
checking for -Werror-implicit-function-declaration option to gcc... yes
checking for -Wextra -Wno-sign-compare -Wno-unused-parameter option to gcc... yes
checking for -Winit-self option to gcc... yes
checking for -Wmissing-declarations option to gcc... yes
checking for -Wmissing-noreturn option to gcc... yes
checking for -Wmissing-prototypes option to gcc... yes
checking for -Wnested-externs option to gcc... yes
checking for -Wpointer-arith option to gcc... yes
checking for -Wundef option to gcc... yes
checking for FORTIFY_SOURCE support... yes
checking for pidgin... no
checking for dbus-binding-tool... yes
checking for DBUS... yes
checking for NETWORKMANAGER... no
configure: error:
NetworkManager development headers not found.
Use --disable-nm if you do not need NetworkManager support.


```

What to do?

---

### Post by jocko on 2008-07-02
> **yizuman said:**
> Getting an error...

new version is out... 2.4.3

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lo lt mk my_MM nb ne nl nn oc pa pl pt_BR pt ps ro ru si sk sl sq sr sr@latin sv ta te th tr uk ur vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for fileno()... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for GTK... yes
checking for PANGO... yes
checking for X11... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... yes
checking for SmcSaveYourselfDone in -lSM... yes
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
checking for X11/SM/SMlib.h... yes
checking for STARTUP_NOTIFICATION... yes
checking for GTKSPELL... yes
checking for initscr in -lncursesw... yes
checking for update_panels in -lpanelw... yes
checking /usr/include/ncursesw/ncurses.h usability... yes
checking /usr/include/ncursesw/ncurses.h presence... yes
checking for /usr/include/ncursesw/ncurses.h... yes
checking if /usr/include/ncursesw/ncurses.h supports wide characters... yes
checking for LIBXML... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for GSTREAMER... yes
checking for gst_registry_fork_set_enabled in -lgstreamer-0.10... yes
checking for MEANWHILE... yes
checking for AVAHI... yes
checking avahi-client/client.h usability... yes
checking avahi-client/client.h presence... yes
checking for avahi-client/client.h... yes
checking avahi-glib/glib-malloc.h usability... yes
checking avahi-glib/glib-malloc.h presence... yes
checking for avahi-glib/glib-malloc.h... yes
checking for avahi_client_new in -lavahi-client... yes
checking for SILC... no
checking for SILC... no
checking for SILC... no
checking for GADU... yes
checking for libgadu GPL compatibility... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for -Waggregate-return option to gcc... yes
checking for -Wcast-align option to gcc... yes
checking for -Wdeclaration-after-statement option to gcc... yes
checking for -Wendif-labels option to gcc... yes
checking for -Werror-implicit-function-declaration option to gcc... yes
checking for -Wextra -Wno-sign-compare -Wno-unused-parameter option to gcc... yes
checking for -Winit-self option to gcc... yes
checking for -Wmissing-declarations option to gcc... yes
checking for -Wmissing-noreturn option to gcc... yes
checking for -Wmissing-prototypes option to gcc... yes
checking for -Wnested-externs option to gcc... yes
checking for -Wpointer-arith option to gcc... yes
checking for -Wundef option to gcc... yes
checking for FORTIFY_SOURCE support... yes
checking for pidgin... no
checking for dbus-binding-tool... yes
checking for DBUS... yes
checking for NETWORKMANAGER... no
configure: error:
NetworkManager development headers not found.
Use --disable-nm if you do not need NetworkManager support.


```What to do?

Try to do either what it tells you to do:```
./configure --disable-nm
make
sudo make install
```Or install network-manager-dev and try again:```
sudo apt-get install networkmanager-dev
./configure
make
sudo make install
```

---

### Post by goatse1 on 2008-07-02
compile pidgin 2.4.3 on hardy 

```

sudo apt-get install libgtk2.0-dev libxcb-screensaver0-dev libxss-dev libstartup-notification0-dev gtk gtk libgtkspell-dev libxml2-dev GStreamer libgstreamer0.10-dev avahi libavahi-common-dev libavahi-client-dev libavahi-core-dev libavahi-ui-dev libdbus-1-dev libdbus-glib-1-dev network-manager-dev libperl-dev libgnutls-dev tcl-dev tk-dev

./configure 
make
sudo make install

```
with a lot of luck and the help of god this might work for you.

---

### Post by defcon3 on 2008-07-02
Could someone tell me why is this necessary in the distro known for user-friendliness?! Pidgin 2.4.1 does NOT want to connect to ICQ. Old version. Period! 

How is it noone has brought this 2.4.3 to the repositories yet? Do we not all communicate online? Is Pidgin not a tool of daily use? I am banging my drums, explaining how cool this is compared to Windows and today alone I received calls from all friends, where I put ubuntu as desktop replacement...

Do you have an idea how it feels to advocate something and then spend one full day explaining everything will be alright?!

Speechless, this is what I am!

---

### Post by IsPoLiN on 2008-07-02
UPDATE: You have to remove pidgin 2.4.1 before (or after) installing 2.4.3 using the method below.
Script to remove pidgin 2.4.1 :
```

sudo apt-get remove pidgin

```
---------------------------------------

That didn't work for me. Goatse1 must have had gettext and meanwhile-dev installed on his system already. Here's a more complete script.

```

sudo apt-get install libgtk2.0-dev libxcb-screensaver0-dev libxss-dev libstartup-notification0-dev libgtkspell-dev libxml2-dev libgstreamer0.10-dev libavahi-common-dev libavahi-client-dev libavahi-core-dev libavahi-ui-dev libdbus-1-dev libdbus-glib-1-dev network-manager-dev libperl-dev libgnutls-dev tcl-dev tk-dev libmeanwhile-dev gettext
cd
wget http://downloads.sourceforge.net/pidgin/pidgin-2.4.3.tar.bz2;
tar svjf pidgin-2.4.3.tar.bz2
cd pidgin-2.4.3
./configure
make
make install
make clean

```

If this doesn't work for you, look at the error you get after you run './configure'
That will usually tell you what dependency you are missing. After you install that dependency, run './configure' again. (you may have to go through this process a few times). 
If './configure' returns 
"configure complete, now type 'make'"
as the last line, you can proceed to the next step ('make').

> **goatse1 said:**
> compile pidgin 2.4.3 on hardy 

```

sudo apt-get install libgtk2.0-dev libxcb-screensaver0-dev libxss-dev libstartup-notification0-dev gtk gtk libgtkspell-dev libxml2-dev GStreamer libgstreamer0.10-dev avahi libavahi-common-dev libavahi-client-dev libavahi-core-dev libavahi-ui-dev libdbus-1-dev libdbus-glib-1-dev network-manager-dev libperl-dev libgnutls-dev tcl-dev tk-dev

./configure 
make
sudo make install

```
with a lot of luck and the help of god this might work for you.

---

### Post by jocko on 2008-07-02
> **defcon3 said:**
> Could someone tell me why is this necessary in the distro known for user-friendliness?! Pidgin 2.4.1 does NOT want to connect to ICQ. Old version. Period!
I'm sure this will be fixed by an updated libpurple package soon.

> **defcon3 said:**
> How is it noone has brought this 2.4.3 to the repositories yet?
2.4.3 will probably never be added to the hardy repos. New versions are almost never added to an already released ubuntu release (unless if it is to update a beta version to a final version).
And it was only released yesterday, so even if it were to be added to the repos you should really learn to be patient and quit complaining. Debianizing, compiling and testing new packages takes time.
I'm sure you will see 2.4.3 in intrepid ibex (september), and you may even find hardy/gutsy versions on [getdeb.net]("http://www.getdeb.net/") soon if someone makes the package.

Edit: There are 2.4.3 packages for hardy out on getdeb.net already (both 32 and 64 bits).

---

### Post by pafffkata on 2008-07-02
After a bit struggling with the ./configure command, I finally managed to get a working configure file after installing the network-manager-dev package and managed to install Pidgin 2.4.3, but now when I try starting the program I get the following error:

pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

Can someone please help me out with this?

Distro is 7.10

---

### Post by IsPoLiN on 2008-07-02
Hmn... i believe libpurple is supposed to compile with pidgin. Did you:
a) remove the old version of pidgin before running "make install" on the new one?
b) get ./configure to work without forcing it to skip something that libpurple required?
c) try running
```

updatedb
locate libpurple.so

```
to see if it got put in the wrong place somehow?

I'm afraid i can't help you much as I'm running 8.04 and don't have virtualization software installed to try 7.10

> **pafffkata said:**
> After a bit struggling with the ./configure command, I finally managed to get a working configure file after installing the network-manager-dev package and managed to install Pidgin 2.4.3, but now when I try starting the program I get the following error:

pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

Can someone please help me out with this?

Distro is 7.10

---

### Post by Loranga on 2008-07-03
How do I activate SILC support when compiling from source?

I have tried both using the libsilc deb packages and by using silc from source. The configure script picks up SILC in both cases. ./configure --prefix=/usr --disable-nm --disable-perl --disable-tcl
Any problems with disabling perl and tcl perhaps?


When I run pidgin with the --debug flag and quit pidgin I get this information, which probably means SILC is never loaded during startup
```
(16:55:56) plugins: Unloading plugin AIM
(16:55:56) plugins: Unloading plugin Bonjour
(16:55:56) plugins: Unloading plugin GNUTLS
(16:55:56) certificate: CertificateScheme x509 unregistered
(16:55:56) plugins: Unloading plugin Gadu-Gadu
(16:55:56) plugins: Unloading plugin GroupWise
(16:55:56) plugins: Unloading plugin ICQ
(16:55:56) plugins: Unloading plugin IRC
(16:55:56) plugins: Unloading plugin MSN
(16:55:56) plugins: Unloading plugin MySpaceIM
(16:55:56) plugins: Unloading plugin Off-the-Record Messaging
(16:55:56) imgstore: retrieved image id 1
(16:55:56) imgstore: retrieved image id 2
(16:55:56) imgstore: retrieved image id 3
(16:55:56) imgstore: retrieved image id 4
(16:55:56) plugins: Unloading plugin QQ
(16:55:56) plugins: Unloading plugin SIMPLE
(16:55:56) plugins: Unloading plugin SSL
(16:55:56) plugins: Unloading plugin Sametime
(16:55:56) plugins: Unloading plugin XMPP
(16:55:56) plugins: Unloading plugin Yahoo
(16:55:56) plugins: Unloading plugin Zephyr

```

The installed libraries are called /usr/lib/purple-2/libsilcpurple.la and
/usr/lib/purple-2/libsilcpurple.so

Is that how it should be?

---

### Post by kevdog on 2008-07-03
What ever happened to just installing the dependencies (is not totally inclusive however contains the core dependencies) like this:

sudo apt-get build-dep pidgin

---

### Post by sjpritch25 on 2008-08-04
> **pafffkata said:**
> After a bit struggling with the ./configure command, I finally managed to get a working configure file after installing the network-manager-dev package and managed to install Pidgin 2.4.3, but now when I try starting the program I get the following error:

pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory

Can someone please help me out with this?

Distro is 7.10




```
ln -s /usr/local/lib/libpurple.so /usr/lib/
ln -s /usr/local/lib/libpurple.so.0 /usr/lib/
```

Those two commands worked for me.   

check install didn't work for me either.  I had to use **sudo make install**

---

### Post by runesvend on 2008-12-07
Thanks for the How To. It works perfectly all the way up to the *checkinstall* command where I get this strange error:

```

[...]

test -z "/usr/share" || mkdir -p -- "/usr/share"
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/16x16/apps/pidgin.png' '/usr/share/icons/hicolor/16x16/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/16x16/apps/_inst.18639_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/22x22/apps/pidgin.png' '/usr/share/icons/hicolor/22x22/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/22x22/apps/_inst.18648_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/24x24/apps/pidgin.png' '/usr/share/icons/hicolor/24x24/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/24x24/apps/_inst.18657_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/32x32/apps/pidgin.png' '/usr/share/icons/hicolor/32x32/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/32x32/apps/_inst.18666_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/48x48/apps/pidgin.png' '/usr/share/icons/hicolor/48x48/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/48x48/apps/_inst.18675_': No such file or directory
make[4]: *** [install-nobase_dist_pidginiconsDATA] Error 1
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```


This is all the text I get from running the command, not sure if it's relevant though:

```
Making install in oscar
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/oscar'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/oscar'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/purple-2" || mkdir -p -- "/usr/lib/purple-2"
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'liboscar.la' '/usr/lib/purple-2/liboscar.la'
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'libaim.la' '/usr/lib/purple-2/libaim.la'
libtool: install: warning: relinking `libaim.la'
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'libicq.la' '/usr/lib/purple-2/libicq.la'
libtool: install: warning: relinking `libicq.la'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/oscar'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/oscar'
Making install in qq
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/qq'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/qq'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/purple-2" || mkdir -p -- "/usr/lib/purple-2"
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'libqq.la' '/usr/lib/purple-2/libqq.la'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/qq'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/qq'
Making install in sametime
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/sametime'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/sametime'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/purple-2" || mkdir -p -- "/usr/lib/purple-2"
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'libsametime.la' '/usr/lib/purple-2/libsametime.la'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/sametime'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/sametime'
Making install in simple
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/simple'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/simple'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/purple-2" || mkdir -p -- "/usr/lib/purple-2"
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'libsimple.la' '/usr/lib/purple-2/libsimple.la'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/simple'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/simple'
Making install in yahoo
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/yahoo'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/yahoo'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/purple-2" || mkdir -p -- "/usr/lib/purple-2"
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'libyahoo.la' '/usr/lib/purple-2/libyahoo.la'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/yahoo'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/yahoo'
Making install in zephyr
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/zephyr'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/zephyr'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/purple-2" || mkdir -p -- "/usr/lib/purple-2"
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'libzephyr.la' '/usr/lib/purple-2/libzephyr.la'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/zephyr'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols/zephyr'
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/protocols'
Making install in tests
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/tests'
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/tests'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/tests'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/tests'
Making install in .
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple'
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../libtool --silent --mode=install /usr/bin/install -c  'libpurple.la' '/usr/lib/libpurple.la'
 /bin/bash ../libtool --silent --mode=install /usr/bin/install -c  'libpurple-client.la' '/usr/lib/libpurple-client.la'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../libtool --silent --mode=install /usr/bin/install -c 'purple-client-example' '/usr/bin/purple-client-example'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
 /usr/bin/install -c 'purple-remote' '/usr/bin/purple-remote'
 /usr/bin/install -c 'purple-send' '/usr/bin/purple-send'
 /usr/bin/install -c 'purple-send-async' '/usr/bin/purple-send-async'
 /usr/bin/install -c 'purple-url-handler' '/usr/bin/purple-url-handler'
test -z "/usr/include/libpurple" || mkdir -p -- "/usr/include/libpurple"
 /usr/bin/install -c -m 644 'account.h' '/usr/include/libpurple/account.h'
 /usr/bin/install -c -m 644 'accountopt.h' '/usr/include/libpurple/accountopt.h'
 /usr/bin/install -c -m 644 'blist.h' '/usr/include/libpurple/blist.h'
 /usr/bin/install -c -m 644 'buddyicon.h' '/usr/include/libpurple/buddyicon.h'
 /usr/bin/install -c -m 644 'certificate.h' '/usr/include/libpurple/certificate.h'
 /usr/bin/install -c -m 644 'cipher.h' '/usr/include/libpurple/cipher.h'
 /usr/bin/install -c -m 644 'circbuffer.h' '/usr/include/libpurple/circbuffer.h'
 /usr/bin/install -c -m 644 'cmds.h' '/usr/include/libpurple/cmds.h'
 /usr/bin/install -c -m 644 'connection.h' '/usr/include/libpurple/connection.h'
 /usr/bin/install -c -m 644 'conversation.h' '/usr/include/libpurple/conversation.h'
 /usr/bin/install -c -m 644 'core.h' '/usr/include/libpurple/core.h'
 /usr/bin/install -c -m 644 'dbus-maybe.h' '/usr/include/libpurple/dbus-maybe.h'
 /usr/bin/install -c -m 644 'debug.h' '/usr/include/libpurple/debug.h'
 /usr/bin/install -c -m 644 'desktopitem.h' '/usr/include/libpurple/desktopitem.h'
 /usr/bin/install -c -m 644 'eventloop.h' '/usr/include/libpurple/eventloop.h'
 /usr/bin/install -c -m 644 'ft.h' '/usr/include/libpurple/ft.h'
 /usr/bin/install -c -m 644 'gaim-compat.h' '/usr/include/libpurple/gaim-compat.h'
 /usr/bin/install -c -m 644 'idle.h' '/usr/include/libpurple/idle.h'
 /usr/bin/install -c -m 644 'imgstore.h' '/usr/include/libpurple/imgstore.h'
 /usr/bin/install -c -m 644 'log.h' '/usr/include/libpurple/log.h'
 /usr/bin/install -c -m 644 'mime.h' '/usr/include/libpurple/mime.h'
 /usr/bin/install -c -m 644 'nat-pmp.h' '/usr/include/libpurple/nat-pmp.h'
 /usr/bin/install -c -m 644 'network.h' '/usr/include/libpurple/network.h'
 /usr/bin/install -c -m 644 'notify.h' '/usr/include/libpurple/notify.h'
 /usr/bin/install -c -m 644 'ntlm.h' '/usr/include/libpurple/ntlm.h'
 /usr/bin/install -c -m 644 'plugin.h' '/usr/include/libpurple/plugin.h'
 /usr/bin/install -c -m 644 'pluginpref.h' '/usr/include/libpurple/pluginpref.h'
 /usr/bin/install -c -m 644 'pounce.h' '/usr/include/libpurple/pounce.h'
 /usr/bin/install -c -m 644 'prefs.h' '/usr/include/libpurple/prefs.h'
 /usr/bin/install -c -m 644 'privacy.h' '/usr/include/libpurple/privacy.h'
 /usr/bin/install -c -m 644 'proxy.h' '/usr/include/libpurple/proxy.h'
 /usr/bin/install -c -m 644 'prpl.h' '/usr/include/libpurple/prpl.h'
 /usr/bin/install -c -m 644 'request.h' '/usr/include/libpurple/request.h'
 /usr/bin/install -c -m 644 'roomlist.h' '/usr/include/libpurple/roomlist.h'
 /usr/bin/install -c -m 644 'savedstatuses.h' '/usr/include/libpurple/savedstatuses.h'
 /usr/bin/install -c -m 644 'server.h' '/usr/include/libpurple/server.h'
 /usr/bin/install -c -m 644 'signals.h' '/usr/include/libpurple/signals.h'
 /usr/bin/install -c -m 644 'smiley.h' '/usr/include/libpurple/smiley.h'
 /usr/bin/install -c -m 644 'dnsquery.h' '/usr/include/libpurple/dnsquery.h'
 /usr/bin/install -c -m 644 'dnssrv.h' '/usr/include/libpurple/dnssrv.h'
 /usr/bin/install -c -m 644 'status.h' '/usr/include/libpurple/status.h'
 /usr/bin/install -c -m 644 'stringref.h' '/usr/include/libpurple/stringref.h'
 /usr/bin/install -c -m 644 'stun.h' '/usr/include/libpurple/stun.h'
 /usr/bin/install -c -m 644 'sound.h' '/usr/include/libpurple/sound.h'
 /usr/bin/install -c -m 644 'sslconn.h' '/usr/include/libpurple/sslconn.h'
 /usr/bin/install -c -m 644 'upnp.h' '/usr/include/libpurple/upnp.h'
 /usr/bin/install -c -m 644 'util.h' '/usr/include/libpurple/util.h'
 /usr/bin/install -c -m 644 'value.h' '/usr/include/libpurple/value.h'
 /usr/bin/install -c -m 644 'xmlnode.h' '/usr/include/libpurple/xmlnode.h'
 /usr/bin/install -c -m 644 'whiteboard.h' '/usr/include/libpurple/whiteboard.h'
 /usr/bin/install -c -m 644 'purple.h' '/usr/include/libpurple/purple.h'
 /usr/bin/install -c -m 644 'version.h' '/usr/include/libpurple/version.h'
 /usr/bin/install -c -m 644 'dbus-bindings.h' '/usr/include/libpurple/dbus-bindings.h'
 /usr/bin/install -c -m 644 'dbus-purple.h' '/usr/include/libpurple/dbus-purple.h'
 /usr/bin/install -c -m 644 'dbus-server.h' '/usr/include/libpurple/dbus-server.h'
 /usr/bin/install -c -m 644 'dbus-useful.h' '/usr/include/libpurple/dbus-useful.h'
 /usr/bin/install -c -m 644 'dbus-define-api.h' '/usr/include/libpurple/dbus-define-api.h'
 /usr/bin/install -c -m 644 'dbus-types.h' '/usr/include/libpurple/dbus-types.h'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'purple.pc' '/usr/lib/pkgconfig/purple.pc'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple'
Making install in example
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/example'
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/example'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/example'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple/example'
make[2]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple'
make[1]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/libpurple'
Making install in doc
make[1]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/doc'
make[2]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './pidgin.1' '/usr/share/man/man1/pidgin.1'
 /usr/bin/install -c -m 644 './finch.1' '/usr/share/man/man1/finch.1'
make[2]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/doc'
make[1]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/doc'
Making install in finch
make[1]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch'
Making install in libgnt
make[2]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
make  install-recursive
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
Making install in .
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c  'libgnt.la' '/usr/lib/libgnt.la'
test -z "/usr/include/gnt" || mkdir -p -- "/usr/include/gnt"
 /usr/bin/install -c -m 644 'gntwidget.h' '/usr/include/gnt/gntwidget.h'
 /usr/bin/install -c -m 644 'gntbindable.h' '/usr/include/gnt/gntbindable.h'
 /usr/bin/install -c -m 644 'gntbox.h' '/usr/include/gnt/gntbox.h'
 /usr/bin/install -c -m 644 'gntbutton.h' '/usr/include/gnt/gntbutton.h'
 /usr/bin/install -c -m 644 'gntcheckbox.h' '/usr/include/gnt/gntcheckbox.h'
 /usr/bin/install -c -m 644 'gntclipboard.h' '/usr/include/gnt/gntclipboard.h'
 /usr/bin/install -c -m 644 'gntcolors.h' '/usr/include/gnt/gntcolors.h'
 /usr/bin/install -c -m 644 'gntcombobox.h' '/usr/include/gnt/gntcombobox.h'
 /usr/bin/install -c -m 644 'gntentry.h' '/usr/include/gnt/gntentry.h'
 /usr/bin/install -c -m 644 'gntfilesel.h' '/usr/include/gnt/gntfilesel.h'
 /usr/bin/install -c -m 644 'gntkeys.h' '/usr/include/gnt/gntkeys.h'
 /usr/bin/install -c -m 644 'gntlabel.h' '/usr/include/gnt/gntlabel.h'
 /usr/bin/install -c -m 644 'gntline.h' '/usr/include/gnt/gntline.h'
 /usr/bin/install -c -m 644 'gntmarshal.h' '/usr/include/gnt/gntmarshal.h'
 /usr/bin/install -c -m 644 'gntmenu.h' '/usr/include/gnt/gntmenu.h'
 /usr/bin/install -c -m 644 'gntmenuitem.h' '/usr/include/gnt/gntmenuitem.h'
 /usr/bin/install -c -m 644 'gntmenuitemcheck.h' '/usr/include/gnt/gntmenuitemcheck.h'
 /usr/bin/install -c -m 644 'gntslider.h' '/usr/include/gnt/gntslider.h'
 /usr/bin/install -c -m 644 'gntstyle.h' '/usr/include/gnt/gntstyle.h'
 /usr/bin/install -c -m 644 'gnttextview.h' '/usr/include/gnt/gnttextview.h'
 /usr/bin/install -c -m 644 'gnttree.h' '/usr/include/gnt/gnttree.h'
 /usr/bin/install -c -m 644 'gntutils.h' '/usr/include/gnt/gntutils.h'
 /usr/bin/install -c -m 644 'gntwindow.h' '/usr/include/gnt/gntwindow.h'
 /usr/bin/install -c -m 644 'gntwm.h' '/usr/include/gnt/gntwm.h'
 /usr/bin/install -c -m 644 'gntws.h' '/usr/include/gnt/gntws.h'
 /usr/bin/install -c -m 644 'gnt.h' '/usr/include/gnt/gnt.h'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'gnt.pc' '/usr/lib/pkgconfig/gnt.pc'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
Making install in wms
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt/wms'
make[5]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt/wms'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/gnt" || mkdir -p -- "/usr/lib/gnt"
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  'irssi.la' '/usr/lib/gnt/irssi.la'
libtool: install: warning: relinking `irssi.la'
 /bin/bash ../../../libtool --silent --mode=install /usr/bin/install -c  's.la' '/usr/lib/gnt/s.la'
libtool: install: warning: relinking `s.la'
make[5]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt/wms'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt/wms'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
make[2]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/libgnt'
Making install in plugins
make[2]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/plugins'
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch/plugins'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/finch" || mkdir -p -- "/usr/lib/finch"
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c  'gntclipboard.la' '/usr/lib/finch/gntclipboard.la'
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c  'gntgf.la' '/usr/lib/finch/gntgf.la'
libtool: install: warning: relinking `gntgf.la'
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c  'gnthistory.la' '/usr/lib/finch/gnthistory.la'
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c  'gntlastlog.la' '/usr/lib/finch/gntlastlog.la'
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c  'grouping.la' '/usr/lib/finch/grouping.la'
libtool: install: warning: relinking `grouping.la'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/plugins'
make[2]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch/plugins'
make[2]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch'
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/finch'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../libtool --silent --mode=install /usr/bin/install -c 'finch' '/usr/bin/finch'
test -z "/usr/include/finch" || mkdir -p -- "/usr/include/finch"
 /usr/bin/install -c -m 644 'gntaccount.h' '/usr/include/finch/gntaccount.h'
 /usr/bin/install -c -m 644 'gntblist.h' '/usr/include/finch/gntblist.h'
 /usr/bin/install -c -m 644 'gntcertmgr.h' '/usr/include/finch/gntcertmgr.h'
 /usr/bin/install -c -m 644 'gntconn.h' '/usr/include/finch/gntconn.h'
 /usr/bin/install -c -m 644 'gntconv.h' '/usr/include/finch/gntconv.h'
 /usr/bin/install -c -m 644 'gntdebug.h' '/usr/include/finch/gntdebug.h'
 /usr/bin/install -c -m 644 'gntft.h' '/usr/include/finch/gntft.h'
 /usr/bin/install -c -m 644 'finch.h' '/usr/include/finch/finch.h'
 /usr/bin/install -c -m 644 'gntidle.h' '/usr/include/finch/gntidle.h'
 /usr/bin/install -c -m 644 'gntlog.h' '/usr/include/finch/gntlog.h'
 /usr/bin/install -c -m 644 'gntnotify.h' '/usr/include/finch/gntnotify.h'
 /usr/bin/install -c -m 644 'gntplugin.h' '/usr/include/finch/gntplugin.h'
 /usr/bin/install -c -m 644 'gntpounce.h' '/usr/include/finch/gntpounce.h'
 /usr/bin/install -c -m 644 'gntprefs.h' '/usr/include/finch/gntprefs.h'
 /usr/bin/install -c -m 644 'gntrequest.h' '/usr/include/finch/gntrequest.h'
 /usr/bin/install -c -m 644 'gntroomlist.h' '/usr/include/finch/gntroomlist.h'
 /usr/bin/install -c -m 644 'gntsound.h' '/usr/include/finch/gntsound.h'
 /usr/bin/install -c -m 644 'gntstatus.h' '/usr/include/finch/gntstatus.h'
 /usr/bin/install -c -m 644 'gntui.h' '/usr/include/finch/gntui.h'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'finch.pc' '/usr/lib/pkgconfig/finch.pc'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch'
make[2]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch'
make[1]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/finch'
Making install in pidgin
make[1]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin'
Making install in pixmaps
make[2]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
Making install in emotes/default/24
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/default/24'
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/default/24'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/pixmaps/pidgin/emotes/default" || mkdir -p -- "/usr/share/pixmaps/pidgin/emotes/default"
 /usr/bin/install -c -m 644 'act-up.png' '/usr/share/pixmaps/pidgin/emotes/default/act-up.png'
 /usr/bin/install -c -m 644 'airplane.png' '/usr/share/pixmaps/pidgin/emotes/default/airplane.png'
 /usr/bin/install -c -m 644 'alien.png' '/usr/share/pixmaps/pidgin/emotes/default/alien.png'
 /usr/bin/install -c -m 644 'angel.png' '/usr/share/pixmaps/pidgin/emotes/default/angel.png'
 /usr/bin/install -c -m 644 'angry.png' '/usr/share/pixmaps/pidgin/emotes/default/angry.png'
 /usr/bin/install -c -m 644 'arrogant.png' '/usr/share/pixmaps/pidgin/emotes/default/arrogant.png'
 /usr/bin/install -c -m 644 'at-wits-end.png' '/usr/share/pixmaps/pidgin/emotes/default/at-wits-end.png'
 /usr/bin/install -c -m 644 'bad.png' '/usr/share/pixmaps/pidgin/emotes/default/bad.png'
 /usr/bin/install -c -m 644 'bashful.png' '/usr/share/pixmaps/pidgin/emotes/default/bashful.png'
 /usr/bin/install -c -m 644 'beat-up.png' '/usr/share/pixmaps/pidgin/emotes/default/beat-up.png'
 /usr/bin/install -c -m 644 'beauty.png' '/usr/share/pixmaps/pidgin/emotes/default/beauty.png'
 /usr/bin/install -c -m 644 'beer.png' '/usr/share/pixmaps/pidgin/emotes/default/beer.png'
 /usr/bin/install -c -m 644 'blowkiss.png' '/usr/share/pixmaps/pidgin/emotes/default/blowkiss.png'
 /usr/bin/install -c -m 644 'bomb.png' '/usr/share/pixmaps/pidgin/emotes/default/bomb.png'
 /usr/bin/install -c -m 644 'bowl.png' '/usr/share/pixmaps/pidgin/emotes/default/bowl.png'
 /usr/bin/install -c -m 644 'boy.png' '/usr/share/pixmaps/pidgin/emotes/default/boy.png'
 /usr/bin/install -c -m 644 'brb.png' '/usr/share/pixmaps/pidgin/emotes/default/brb.png'
 /usr/bin/install -c -m 644 'bulgy-eyes.png' '/usr/share/pixmaps/pidgin/emotes/default/bulgy-eyes.png'
 /usr/bin/install -c -m 644 'bunny.png' '/usr/share/pixmaps/pidgin/emotes/default/bunny.png'
 /usr/bin/install -c -m 644 'bye.png' '/usr/share/pixmaps/pidgin/emotes/default/bye.png'
 /usr/bin/install -c -m 644 'cake.png' '/usr/share/pixmaps/pidgin/emotes/default/cake.png'
 /usr/bin/install -c -m 644 'call-me.png' '/usr/share/pixmaps/pidgin/emotes/default/call-me.png'
 /usr/bin/install -c -m 644 'camera.png' '/usr/share/pixmaps/pidgin/emotes/default/camera.png'
 /usr/bin/install -c -m 644 'can.png' '/usr/share/pixmaps/pidgin/emotes/default/can.png'
 /usr/bin/install -c -m 644 'car.png' '/usr/share/pixmaps/pidgin/emotes/default/car.png'
 /usr/bin/install -c -m 644 'cat.png' '/usr/share/pixmaps/pidgin/emotes/default/cat.png'
 /usr/bin/install -c -m 644 'chicken.png' '/usr/share/pixmaps/pidgin/emotes/default/chicken.png'
 /usr/bin/install -c -m 644 'cigarette.png' '/usr/share/pixmaps/pidgin/emotes/default/cigarette.png'
 /usr/bin/install -c -m 644 'clap.png' '/usr/share/pixmaps/pidgin/emotes/default/clap.png'
 /usr/bin/install -c -m 644 'clock.png' '/usr/share/pixmaps/pidgin/emotes/default/clock.png'
 /usr/bin/install -c -m 644 'cloudy.png' '/usr/share/pixmaps/pidgin/emotes/default/cloudy.png'
 /usr/bin/install -c -m 644 'clover.png' '/usr/share/pixmaps/pidgin/emotes/default/clover.png'
 /usr/bin/install -c -m 644 'clown.png' '/usr/share/pixmaps/pidgin/emotes/default/clown.png'
 /usr/bin/install -c -m 644 'coffee.png' '/usr/share/pixmaps/pidgin/emotes/default/coffee.png'
 /usr/bin/install -c -m 644 'coins.png' '/usr/share/pixmaps/pidgin/emotes/default/coins.png'
 /usr/bin/install -c -m 644 'computer.png' '/usr/share/pixmaps/pidgin/emotes/default/computer.png'
 /usr/bin/install -c -m 644 'confused.png' '/usr/share/pixmaps/pidgin/emotes/default/confused.png'
 /usr/bin/install -c -m 644 'console.png' '/usr/share/pixmaps/pidgin/emotes/default/console.png'
 /usr/bin/install -c -m 644 'cowboy.png' '/usr/share/pixmaps/pidgin/emotes/default/cowboy.png'
 /usr/bin/install -c -m 644 'cow.png' '/usr/share/pixmaps/pidgin/emotes/default/cow.png'
 /usr/bin/install -c -m 644 'crying.png' '/usr/share/pixmaps/pidgin/emotes/default/crying.png'
 /usr/bin/install -c -m 644 'curl-lip.png' '/usr/share/pixmaps/pidgin/emotes/default/curl-lip.png'
 /usr/bin/install -c -m 644 'curse.png' '/usr/share/pixmaps/pidgin/emotes/default/curse.png'
 /usr/bin/install -c -m 644 'cute.png' '/usr/share/pixmaps/pidgin/emotes/default/cute.png'
 /usr/bin/install -c -m 644 'cyclops.png' '/usr/share/pixmaps/pidgin/emotes/default/cyclops.png'
 /usr/bin/install -c -m 644 'dance.png' '/usr/share/pixmaps/pidgin/emotes/default/dance.png'
 /usr/bin/install -c -m 644 'dazed.png' '/usr/share/pixmaps/pidgin/emotes/default/dazed.png'
 /usr/bin/install -c -m 644 'desire.png' '/usr/share/pixmaps/pidgin/emotes/default/desire.png'
 /usr/bin/install -c -m 644 'devil.png' '/usr/share/pixmaps/pidgin/emotes/default/devil.png'
 /usr/bin/install -c -m 644 'disappointed.png' '/usr/share/pixmaps/pidgin/emotes/default/disappointed.png'
 /usr/bin/install -c -m 644 'disdain.png' '/usr/share/pixmaps/pidgin/emotes/default/disdain.png'
 /usr/bin/install -c -m 644 'doctor.png' '/usr/share/pixmaps/pidgin/emotes/default/doctor.png'
 /usr/bin/install -c -m 644 'dog.png' '/usr/share/pixmaps/pidgin/emotes/default/dog.png'
 /usr/bin/install -c -m 644 'doh.png' '/usr/share/pixmaps/pidgin/emotes/default/doh.png'
 /usr/bin/install -c -m 644 'dont-know.png' '/usr/share/pixmaps/pidgin/emotes/default/dont-know.png'
 /usr/bin/install -c -m 644 'drink.png' '/usr/share/pixmaps/pidgin/emotes/default/drink.png'
 /usr/bin/install -c -m 644 'drool.png' '/usr/share/pixmaps/pidgin/emotes/default/drool.png'
 /usr/bin/install -c -m 644 'eat.png' '/usr/share/pixmaps/pidgin/emotes/default/eat.png'
 /usr/bin/install -c -m 644 'embarrassed.png' '/usr/share/pixmaps/pidgin/emotes/default/embarrassed.png'
 /usr/bin/install -c -m 644 'excruciating.png' '/usr/share/pixmaps/pidgin/emotes/default/excruciating.png'
 /usr/bin/install -c -m 644 'eyeroll.png' '/usr/share/pixmaps/pidgin/emotes/default/eyeroll.png'
 /usr/bin/install -c -m 644 'female-fighter.png' '/usr/share/pixmaps/pidgin/emotes/default/female-fighter.png'
 /usr/bin/install -c -m 644 'film.png' '/usr/share/pixmaps/pidgin/emotes/default/film.png'
 /usr/bin/install -c -m 644 'fingers-crossed.png' '/usr/share/pixmaps/pidgin/emotes/default/fingers-crossed.png'
 /usr/bin/install -c -m 644 'flag.png' '/usr/share/pixmaps/pidgin/emotes/default/flag.png'
 /usr/bin/install -c -m 644 'foot-in-mouth.png' '/usr/share/pixmaps/pidgin/emotes/default/foot-in-mouth.png'
 /usr/bin/install -c -m 644 'freaked-out.png' '/usr/share/pixmaps/pidgin/emotes/default/freaked-out.png'
 /usr/bin/install -c -m 644 'ghost.png' '/usr/share/pixmaps/pidgin/emotes/default/ghost.png'
 /usr/bin/install -c -m 644 'giggle.png' '/usr/share/pixmaps/pidgin/emotes/default/giggle.png'
 /usr/bin/install -c -m 644 'girl.png' '/usr/share/pixmaps/pidgin/emotes/default/girl.png'
 /usr/bin/install -c -m 644 'glasses-cool.png' '/usr/share/pixmaps/pidgin/emotes/default/glasses-cool.png'
 /usr/bin/install -c -m 644 'glasses-nerdy.png' '/usr/share/pixmaps/pidgin/emotes/default/glasses-nerdy.png'
 /usr/bin/install -c -m 644 'goat.png' '/usr/share/pixmaps/pidgin/emotes/default/goat.png'
 /usr/bin/install -c -m 644 'go-away.png' '/usr/share/pixmaps/pidgin/emotes/default/go-away.png'
 /usr/bin/install -c -m 644 'good.png' '/usr/share/pixmaps/pidgin/emotes/default/good.png'
 /usr/bin/install -c -m 644 'hammer.png' '/usr/share/pixmaps/pidgin/emotes/default/hammer.png'
 /usr/bin/install -c -m 644 'handcuffs.png' '/usr/share/pixmaps/pidgin/emotes/default/handcuffs.png'
 /usr/bin/install -c -m 644 'handshake.png' '/usr/share/pixmaps/pidgin/emotes/default/handshake.png'
 /usr/bin/install -c -m 644 'highfive.png' '/usr/share/pixmaps/pidgin/emotes/default/highfive.png'
 /usr/bin/install -c -m 644 'hug-left.png' '/usr/share/pixmaps/pidgin/emotes/default/hug-left.png'
 /usr/bin/install -c -m 644 'hug-right.png' '/usr/share/pixmaps/pidgin/emotes/default/hug-right.png'
 /usr/bin/install -c -m 644 'hypnotized.png' '/usr/share/pixmaps/pidgin/emotes/default/hypnotized.png'
 /usr/bin/install -c -m 644 'in-love.png' '/usr/share/pixmaps/pidgin/emotes/default/in-love.png'
 /usr/bin/install -c -m 644 'island.png' '/usr/share/pixmaps/pidgin/emotes/default/island.png'
 /usr/bin/install -c -m 644 'jump.png' '/usr/share/pixmaps/pidgin/emotes/default/jump.png'
 /usr/bin/install -c -m 644 'kissed.png' '/usr/share/pixmaps/pidgin/emotes/default/kissed.png'
 /usr/bin/install -c -m 644 'kissing.png' '/usr/share/pixmaps/pidgin/emotes/default/kissing.png'
 /usr/bin/install -c -m 644 'kiss.png' '/usr/share/pixmaps/pidgin/emotes/default/kiss.png'
 /usr/bin/install -c -m 644 'knife.png' '/usr/share/pixmaps/pidgin/emotes/default/knife.png'
 /usr/bin/install -c -m 644 'lamp.png' '/usr/share/pixmaps/pidgin/emotes/default/lamp.png'
 /usr/bin/install -c -m 644 'lashes.png' '/usr/share/pixmaps/pidgin/emotes/default/lashes.png'
 /usr/bin/install -c -m 644 'laugh.png' '/usr/share/pixmaps/pidgin/emotes/default/laugh.png'
 /usr/bin/install -c -m 644 'liquor.png' '/usr/share/pixmaps/pidgin/emotes/default/liquor.png'
 /usr/bin/install -c -m 644 'loser.png' '/usr/share/pixmaps/pidgin/emotes/default/loser.png'
 /usr/bin/install -c -m 644 'love-over.png' '/usr/share/pixmaps/pidgin/emotes/default/love-over.png'
 /usr/bin/install -c -m 644 'love.png' '/usr/share/pixmaps/pidgin/emotes/default/love.png'
 /usr/bin/install -c -m 644 'lying.png' '/usr/share/pixmaps/pidgin/emotes/default/lying.png'
 /usr/bin/install -c -m 644 'mad-tongue.png' '/usr/share/pixmaps/pidgin/emotes/default/mad-tongue.png'
 /usr/bin/install -c -m 644 'mail.png' '/usr/share/pixmaps/pidgin/emotes/default/mail.png'
 /usr/bin/install -c -m 644 'male-fighter1.png' '/usr/share/pixmaps/pidgin/emotes/default/male-fighter1.png'
 /usr/bin/install -c -m 644 'male-fighter2.png' '/usr/share/pixmaps/pidgin/emotes/default/male-fighter2.png'
 /usr/bin/install -c -m 644 'mean.png' '/usr/share/pixmaps/pidgin/emotes/default/mean.png'
 /usr/bin/install -c -m 644 'meeting.png' '/usr/share/pixmaps/pidgin/emotes/default/meeting.png'
 /usr/bin/install -c -m 644 'messed.png' '/usr/share/pixmaps/pidgin/emotes/default/messed.png'
 /usr/bin/install -c -m 644 'mobile.png' '/usr/share/pixmaps/pidgin/emotes/default/mobile.png'
 /usr/bin/install -c -m 644 'mohawk.png' '/usr/share/pixmaps/pidgin/emotes/default/mohawk.png'
 /usr/bin/install -c -m 644 'moneymouth.png' '/usr/share/pixmaps/pidgin/emotes/default/moneymouth.png'
 /usr/bin/install -c -m 644 'monkey.png' '/usr/share/pixmaps/pidgin/emotes/default/monkey.png'
 /usr/bin/install -c -m 644 'moon.png' '/usr/share/pixmaps/pidgin/emotes/default/moon.png'
 /usr/bin/install -c -m 644 'msn-away.png' '/usr/share/pixmaps/pidgin/emotes/default/msn-away.png'
 /usr/bin/install -c -m 644 'msn-busy.png' '/usr/share/pixmaps/pidgin/emotes/default/msn-busy.png'
 /usr/bin/install -c -m 644 'msn_online.png' '/usr/share/pixmaps/pidgin/emotes/default/msn_online.png'
 /usr/bin/install -c -m 644 'msn.png' '/usr/share/pixmaps/pidgin/emotes/default/msn.png'
 /usr/bin/install -c -m 644 'musical-note.png' '/usr/share/pixmaps/pidgin/emotes/default/musical-note.png'
 /usr/bin/install -c -m 644 'music.png' '/usr/share/pixmaps/pidgin/emotes/default/music.png'
 /usr/bin/install -c -m 644 'nailbiting.png' '/usr/share/pixmaps/pidgin/emotes/default/nailbiting.png'
 /usr/bin/install -c -m 644 'neutral.png' '/usr/share/pixmaps/pidgin/emotes/default/neutral.png'
 /usr/bin/install -c -m 644 'on-the-phone.png' '/usr/share/pixmaps/pidgin/emotes/default/on-the-phone.png'
 /usr/bin/install -c -m 644 'party.png' '/usr/share/pixmaps/pidgin/emotes/default/party.png'
 /usr/bin/install -c -m 644 'peace.png' '/usr/share/pixmaps/pidgin/emotes/default/peace.png'
 /usr/bin/install -c -m 644 'phone.png' '/usr/share/pixmaps/pidgin/emotes/default/phone.png'
 /usr/bin/install -c -m 644 'pig.png' '/usr/share/pixmaps/pidgin/emotes/default/pig.png'
 /usr/bin/install -c -m 644 'pill.png' '/usr/share/pixmaps/pidgin/emotes/default/pill.png'
 /usr/bin/install -c -m 644 'pirate.png' '/usr/share/pixmaps/pidgin/emotes/default/pirate.png'
 /usr/bin/install -c -m 644 'pissed-off.png' '/usr/share/pixmaps/pidgin/emotes/default/pissed-off.png'
 /usr/bin/install -c -m 644 'pizza.png' '/usr/share/pixmaps/pidgin/emotes/default/pizza.png'
 /usr/bin/install -c -m 644 'plate.png' '/usr/share/pixmaps/pidgin/emotes/default/plate.png'
 /usr/bin/install -c -m 644 'poop.png' '/usr/share/pixmaps/pidgin/emotes/default/poop.png'
 /usr/bin/install -c -m 644 'pray.png' '/usr/share/pixmaps/pidgin/emotes/default/pray.png'
 /usr/bin/install -c -m 644 'present.png' '/usr/share/pixmaps/pidgin/emotes/default/present.png'
 /usr/bin/install -c -m 644 'pumpkin.png' '/usr/share/pixmaps/pidgin/emotes/default/pumpkin.png'
 /usr/bin/install -c -m 644 'qq.png' '/usr/share/pixmaps/pidgin/emotes/default/qq.png'
 /usr/bin/install -c -m 644 'question.png' '/usr/share/pixmaps/pidgin/emotes/default/question.png'
 /usr/bin/install -c -m 644 'quiet.png' '/usr/share/pixmaps/pidgin/emotes/default/quiet.png'
 /usr/bin/install -c -m 644 'rainbow.png' '/usr/share/pixmaps/pidgin/emotes/default/rainbow.png'
 /usr/bin/install -c -m 644 'rain.png' '/usr/share/pixmaps/pidgin/emotes/default/rain.png'
 /usr/bin/install -c -m 644 'rose-dead.png' '/usr/share/pixmaps/pidgin/emotes/default/rose-dead.png'
 /usr/bin/install -c -m 644 'rose.png' '/usr/share/pixmaps/pidgin/emotes/default/rose.png'
 /usr/bin/install -c -m 644 'rotfl.png' '/usr/share/pixmaps/pidgin/emotes/default/rotfl.png'
 /usr/bin/install -c -m 644 'sad.png' '/usr/share/pixmaps/pidgin/emotes/default/sad.png'
 /usr/bin/install -c -m 644 'sarcastic.png' '/usr/share/pixmaps/pidgin/emotes/default/sarcastic.png'
 /usr/bin/install -c -m 644 'search.png' '/usr/share/pixmaps/pidgin/emotes/default/search.png'
 /usr/bin/install -c -m 644 'secret.png' '/usr/share/pixmaps/pidgin/emotes/default/secret.png'
 /usr/bin/install -c -m 644 'shame.png' '/usr/share/pixmaps/pidgin/emotes/default/shame.png'
 /usr/bin/install -c -m 644 'sheep.png' '/usr/share/pixmaps/pidgin/emotes/default/sheep.png'
 /usr/bin/install -c -m 644 'shock.png' '/usr/share/pixmaps/pidgin/emotes/default/shock.png'
 /usr/bin/install -c -m 644 'shout.png' '/usr/share/pixmaps/pidgin/emotes/default/shout.png'
 /usr/bin/install -c -m 644 'shut-mouth.png' '/usr/share/pixmaps/pidgin/emotes/default/shut-mouth.png'
 /usr/bin/install -c -m 644 'sick.png' '/usr/share/pixmaps/pidgin/emotes/default/sick.png'
 /usr/bin/install -c -m 644 'sidefrown.png' '/usr/share/pixmaps/pidgin/emotes/default/sidefrown.png'
 /usr/bin/install -c -m 644 'silly.png' '/usr/share/pixmaps/pidgin/emotes/default/silly.png'
 /usr/bin/install -c -m 644 'sinister.png' '/usr/share/pixmaps/pidgin/emotes/default/sinister.png'
 /usr/bin/install -c -m 644 'skeleton.png' '/usr/share/pixmaps/pidgin/emotes/default/skeleton.png'
 /usr/bin/install -c -m 644 'skywalker.png' '/usr/share/pixmaps/pidgin/emotes/default/skywalker.png'
 /usr/bin/install -c -m 644 'sleepy.png' '/usr/share/pixmaps/pidgin/emotes/default/sleepy.png'
 /usr/bin/install -c -m 644 'smile-big.png' '/usr/share/pixmaps/pidgin/emotes/default/smile-big.png'
 /usr/bin/install -c -m 644 'smile.png' '/usr/share/pixmaps/pidgin/emotes/default/smile.png'
 /usr/bin/install -c -m 644 'smirk.png' '/usr/share/pixmaps/pidgin/emotes/default/smirk.png'
 /usr/bin/install -c -m 644 'snail.png' '/usr/share/pixmaps/pidgin/emotes/default/snail.png'
 /usr/bin/install -c -m 644 'snicker.png' '/usr/share/pixmaps/pidgin/emotes/default/snicker.png'
 /usr/bin/install -c -m 644 'snowman.png' '/usr/share/pixmaps/pidgin/emotes/default/snowman.png'
 /usr/bin/install -c -m 644 'soccerball.png' '/usr/share/pixmaps/pidgin/emotes/default/soccerball.png'
 /usr/bin/install -c -m 644 'soldier.png' '/usr/share/pixmaps/pidgin/emotes/default/soldier.png'
 /usr/bin/install -c -m 644 'star.png' '/usr/share/pixmaps/pidgin/emotes/default/star.png'
 /usr/bin/install -c -m 644 'starving.png' '/usr/share/pixmaps/pidgin/emotes/default/starving.png'
 /usr/bin/install -c -m 644 'stop.png' '/usr/share/pixmaps/pidgin/emotes/default/stop.png'
 /usr/bin/install -c -m 644 'struggle.png' '/usr/share/pixmaps/pidgin/emotes/default/struggle.png'
 /usr/bin/install -c -m 644 'sun.png' '/usr/share/pixmaps/pidgin/emotes/default/sun.png'
 /usr/bin/install -c -m 644 'sweat.png' '/usr/share/pixmaps/pidgin/emotes/default/sweat.png'
 /usr/bin/install -c -m 644 'talktohand.png' '/usr/share/pixmaps/pidgin/emotes/default/talktohand.png'
 /usr/bin/install -c -m 644 'teeth.png' '/usr/share/pixmaps/pidgin/emotes/default/teeth.png'
 /usr/bin/install -c -m 644 'terror.png' '/usr/share/pixmaps/pidgin/emotes/default/terror.png'
 /usr/bin/install -c -m 644 'thinking.png' '/usr/share/pixmaps/pidgin/emotes/default/thinking.png'
 /usr/bin/install -c -m 644 'thunder.png' '/usr/share/pixmaps/pidgin/emotes/default/thunder.png'
 /usr/bin/install -c -m 644 'time-out.png' '/usr/share/pixmaps/pidgin/emotes/default/time-out.png'
 /usr/bin/install -c -m 644 'tongue.png' '/usr/share/pixmaps/pidgin/emotes/default/tongue.png'
 /usr/bin/install -c -m 644 'tremble.png' '/usr/share/pixmaps/pidgin/emotes/default/tremble.png'
 /usr/bin/install -c -m 644 'turtle.png' '/usr/share/pixmaps/pidgin/emotes/default/turtle.png'
 /usr/bin/install -c -m 644 'tv.png' '/usr/share/pixmaps/pidgin/emotes/default/tv.png'
 /usr/bin/install -c -m 644 'umbrella.png' '/usr/share/pixmaps/pidgin/emotes/default/umbrella.png'
 /usr/bin/install -c -m 644 'vampire.png' '/usr/share/pixmaps/pidgin/emotes/default/vampire.png'
 /usr/bin/install -c -m 644 'victory.png' '/usr/share/pixmaps/pidgin/emotes/default/victory.png'
 /usr/bin/install -c -m 644 'waiting.png' '/usr/share/pixmaps/pidgin/emotes/default/waiting.png'
 /usr/bin/install -c -m 644 'watermelon.png' '/usr/share/pixmaps/pidgin/emotes/default/watermelon.png'
 /usr/bin/install -c -m 644 'waving.png' '/usr/share/pixmaps/pidgin/emotes/default/waving.png'
 /usr/bin/install -c -m 644 'weep.png' '/usr/share/pixmaps/pidgin/emotes/default/weep.png'
 /usr/bin/install -c -m 644 'wilt.png' '/usr/share/pixmaps/pidgin/emotes/default/wilt.png'
 /usr/bin/install -c -m 644 'wink.png' '/usr/share/pixmaps/pidgin/emotes/default/wink.png'
 /usr/bin/install -c -m 644 'worship.png' '/usr/share/pixmaps/pidgin/emotes/default/worship.png'
 /usr/bin/install -c -m 644 'yawn.png' '/usr/share/pixmaps/pidgin/emotes/default/yawn.png'
 /usr/bin/install -c -m 644 'yin-yang.png' '/usr/share/pixmaps/pidgin/emotes/default/yin-yang.png'
 /usr/bin/install -c -m 644 'theme' '/usr/share/pixmaps/pidgin/emotes/default/theme'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/default/24'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/default/24'
Making install in emotes/none
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/none'
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/none'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/pixmaps/pidgin/emotes/none" || mkdir -p -- "/usr/share/pixmaps/pidgin/emotes/none"
 /usr/bin/install -c -m 644 'theme' '/usr/share/pixmaps/pidgin/emotes/none/theme'
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/none'
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps/emotes/none'
make[3]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[4]: Entering directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/share" || mkdir -p -- "/usr/share"
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/16x16/apps/pidgin.png' '/usr/share/icons/hicolor/16x16/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/16x16/apps/_inst.18639_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/22x22/apps/pidgin.png' '/usr/share/icons/hicolor/22x22/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/22x22/apps/_inst.18648_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/24x24/apps/pidgin.png' '/usr/share/icons/hicolor/24x24/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/24x24/apps/_inst.18657_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/32x32/apps/pidgin.png' '/usr/share/icons/hicolor/32x32/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/32x32/apps/_inst.18666_': No such file or directory
 /home/rune/Desktop/pidgin-2.5.2/install-sh -c -m 644 'icons/hicolor/48x48/apps/pidgin.png' '/usr/share/icons/hicolor/48x48/apps/pidgin.png'
chmod: changing permissions of `/usr/share/icons/hicolor/48x48/apps/_inst.18675_': No such file or directory
make[4]: *** [install-nobase_dist_pidginiconsDATA] Error 1
make[4]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin/pixmaps'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/rune/Desktop/pidgin-2.5.2/pidgin'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

---

### Post by kevdog on 2008-12-07
Check out this guide, Ive modified the checkinstall commands:

[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

Hopefully that might help!

---

### Post by runesvend on 2008-12-07
Running the following command instead of simply *sudo checkinstall* fixed the problem! (I have no idea why):

```
sudo checkinstall -D --fstrans=no --install=yes
```

I got it from this thread: [http://ubuntuforums.org/showthread.php?t=959729](http://ubuntuforums.org/showthread.php?t=959729)


With all this said. How do I keep Ubuntu from wanting to "update" my crisp and newly installed Pidgin 2.5.2 to version 2.4.1? I get the "updates available" icon (and it is red!) but it seems to want to actually downgrade the version of pidgin to the previous version...

Also it wants to install libpurple0 and pidgin-data, none of which seem to be installed. Should I install these (the versions for these are 2.4.1 so they won't be the same version as Pidgin (2.5.2)).

---

### Post by runesvend on 2008-12-07
[double post]

---

### Post by runesvend on 2008-12-07
That was a quick reply! I didn't even notice it before replying myself again. I just tried it and it worked as well.

Do you have any idea what will happen if I do what the Update Manager recommends and install libpurple0 and pidgin-data both of which are version 2.4.1?

> **kevdog said:**
> Check out this guide, Ive modified the checkinstall commands:

[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

Hopefully that might help!

---

### Post by kevdog on 2008-12-07
Depending on how you update your system:

Go into Synaptic, find the pidgin package, and mark the package as hold, or put on hold. 

Also type the following:

sudo aptitude hold pidgin

---

### Post by runesvend on 2008-12-07
I've run the command *sudo aptitude hold pidgin* but I can't find an option in Synaptic that's called "hold" (under the Package-menu I have "Lock version" and "Force version").

Choosing "Lock version" seems to work. The Update Manager icon disappears. Is this the correct way to do it?

---

### Post by kevdog on 2008-12-07
I hope you saw my previous post -- you don't want to mix libpurple problems.  Ive done that before and it was a mistake.  

Also it depends where you installed you pidgin.

I always install into /usr/local 
whereby the default version is installed into /usr

The reason I do this is that its possible to have 2 different program versions available on the system.  Synaptic will always want to update the /usr tree (ie /usr/bin /usr/lib), however it doesnt matter since /usr/local is preceded on my PATH statement. Hence libs and executables installed into (/usr/local/lib and /usr/local/bin) will never be touched.  I would continue using the /usr/local tree independent of whatever is going on in the /usr tree.  If you look at your PATH statement, you will notice by default /usr/local/bin is always before /usr/bin unless you modified something.

I hope this makes sense.

****
And yes its lock version within Synaptic (sorry). I use Synaptic so rarely I forget the options.  I'm a command line aptitude guy.  Synaptic is just so slow for me.

---

### Post by runesvend on 2008-12-07
That's clever! So instead of all this "hold" and "lock version" stuff, I can just compile pidgin and install it to the /usr/local directory and when I the run the command "pidgin" it will exectute the program present in /usr/local/bin/ instead of /usr/bin/? And then let the package manager install its preferrred pidgin-version (to /usr/) without me worrying about it?

And all this would require to function would be to specify the path when running the configure-script, like so?:

```
./configure --prefix=/usr/local --enable-mono
```

And then proceed as normal?

By the way, is the "--enable-gnutls=yes" argument not required for MSN support anymore? I noticed it was in the previous guide but not in the newer one you just linked to...

---

### Post by kevdog on 2008-12-07
/usr/local is the default prefix.  You can either explicitly include it, or simply not include this flag, since by default, all packages compiled in ubuntu (linux also), are placed in the /usr/local tree.

I'll have to check the --enable-gnutls option.  In a lot of older versions you had to specify these options.

From within the pidgin directory, if you do a 

./configure --help

It will tell you the options that are/are not included by default.

---

### Post by kevdog on 2008-12-07
Ok here are the options not included by default with the 2.5.2 package -- notice these are not a list of the options inluded in the compile, but options not included -- if you want to include the option (or disable the options, you must explcitly pass these to the configure command):

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --enable-static[=PKGS]  build static libraries [default=no]
  --enable-shared[=PKGS]  build shared libraries [default=yes]
  --enable-fast-install[=PKGS]
                          optimize for fast installation [default=yes]
  --disable-libtool-lock  avoid locking (might break parallel builds)
  --disable-largefile     omit support for large files
  --disable-missing-dependencies
                          skip missing dependencies instead of aborting
                          configure
  --disable-gtkui         compile without GTK+ user interface
  --disable-consoleui     compile without console user interface
  --disable-screensaver   compile without X screensaver extension (used to
                          detect idleness)
  --disable-sm            compile without X session management support
  --disable-startup-notification
                          compile without startup notification support
  --disable-gtkspell      compile without GtkSpell automatic spell checking
  --enable-gevolution     compile with the Evolution plugin
  --enable-cap            compile with Contact Availability Prediction plugin
  --disable-gestures      compile without the gestures plugin
  --disable-schemas-install	Disable the schemas installation
  --disable-gstreamer     compile without GStreamer audio support
  --disable-meanwhile     compile without meanwhile (required for Sametime
                          support)
  --disable-avahi         compile without avahi (required for Bonjour support)
  --disable-msnp15        Disable the newer MSNP15 protocol

  --disable-plugins       compile without plugin support
  --disable-fortify       compile without FORTIFY_SOURCE support
  --disable-dbus          disable D-Bus support
  --disable-nm            disable NetworkManager support (requires D-Bus)
  --enable-mono           compile with Mono runtime support (experimental)
  --disable-perl          compile without perl scripting
  --enable-gnutls=yes,no  attempt to use GnuTLS for SSL support default=yes
  --enable-nss=yes,no,static    attempt to use Mozilla libnss for SSL support default=yes
  --disable-tcl           compile without Tcl scripting
  --disable-tk            compile without Tcl support for Tk
  --enable-cyrus-sasl     enable Cyrus SASL support for jabberd
  --disable-pixmaps-install
                          disable installation of pixmap files - Pidgin still
                          needs them!
  --disable-nls           disable installation of translation files
  --disable-doxygen       enable documentation with doxygen
  --enable-dot            enable graphs in doxygen via 'dot'
  --enable-devhelp        enable building index for devhelp documentation
                          browser
  --enable-debug          compile with debugging support


You do not need to include --enable-gnutls since as you can see, its included by default.  I suppose I could add to my tutorial the --enable-cap option

---

### Post by runesvend on 2008-12-08
Great! I will immediately compile it to my /usr/local directory and forget about the holding back, the locking versions and whatnot. Thanks a lot!

---

### Post by dbhatt on 2010-10-09
I tried the following instruction on my Lucid build:

> sudo apt-get build-dep pidginand I got a list of unmet dependencies. I can go in and install the build dependencies for each of them, but I was hoping that there would be an easier way to build the dependencies for everything. Is there a way to do this or do we have to manually tackle each individual dependency issue? If there is a way, could someone please post it?

---

