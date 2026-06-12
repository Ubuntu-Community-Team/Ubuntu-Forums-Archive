---
title: "HowTo Nicotine+: An Improved Version of Nicotine"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by INMCM on 2006-06-14
UPDATED: Edgy and Version 1.2.4.1 deb

Anyone who uses the [Soulseek]("http://www.slsknet.org/") P2P network  and Linux is probbaly familar with [Nicotine]("http://nicotine.thegraveyard.org/"). Sadly, the version in the repositories (Dapper and Older) is very old, has a number of nasty bugs remaining it, and will probbaly never be updated again. 

Thankfully, due to the beauty of open source, a new fork has been created: [Nicotine+]("http://nicotine-plus.sourceforge.net/").
This updated version fixes lots of bugs and adds new features as well.

There are two install methods: running the source code or installing from a deb. At the moment, running from source is probbably the preffered method, but for all you lazy/adventerous people, look below for the deb.

**NOTE for Edgy Users:**Nicotine+ has been merged into the repos as plain old Nicotine. Just install Nicotine as normal:

```
sudo apt-get install nicotine
```

It's a slightly old version (1.2.2), but that's far better than 1.0.8. If you want bleeding edge Nicotine+, follow the instructions below. You can always install regular Nicotine from the repos later on.

**Install From Source (Dapper, Brezzy, etc):**

Whether or not you have the old Nicotine from the repos installed (just make sure the old version isn't running!), just download the tarball here [http://prdownloads.sourceforge.net/nicotine-plus/nicotine%2B-1.2.4.1.tar.bz2?download](http://prdownloads.sourceforge.net/nicotine-plus/nicotine%2B-1.2.4.1.tar.bz2?download) and:

```
sudo apt-get install python-gtk2 python-pyvorbis
tar xvjf nicotine+-1.2.4.1.tar.bz2
cd nicotine+-1.2.4.1/
./nicotine
```

The new version will automatically use your settings/shares/username/password if you had run the old Nicotine. Otherwise, you'll need to set up your usename, password, and shares before it'll let connect to the server. You must run the ./nicotine command from the extract directory everytime you wish to use the program. You can also make a shortcut and use /path/to/extracted/folder/./nicotine as the command. Also, there are some new preferences that may intrest you, so do take a look at those once you are up and running.

Tray Icon Support
If you are used to the the Windows Soulseek client, or just love tray icons, you might want to try your hand at compiling the tray icon. Here's the general procedure

```
sudo apt-get install build-essential python-dev python-gtk2-dev libgtk2.0-dev
cd nicotine+-1.2.4.1/trayicon
./autogen.py
make
sudo make install
cd ..
cp trayicon/trayicon.so pynicotine/
```


instructions found here: [http://nicotine.le-vert.net/wiki/TrayIcon](http://nicotine.le-vert.net/wiki/TrayIcon)
and here: [http://nicotine.le-vert.net/wiki/IssuesWithNicotinePlus](http://nicotine.le-vert.net/wiki/IssuesWithNicotinePlus)

**Install From a Deb (Dapper Only)** 

47th_Ronin has made a deb of 1.2.4.1 . This is a **testing** package and, while it works VERY well, there still might be issues. You MUST uninstall all previous nicotine+ deb package before installing this. You may do this in synaptic or just by doubling clicking on the old deb if you still have it around. It is also HIGHLY recommended that you back up your ~/.nicotine folder before installing this. If you don't feel comfortable, use the source instructions above.  Just download [here]("http://www.osiris.codedchaos.com/osiris/e107_files/downloads/nicotine%2B-1.2.4.1-i386-dapper.deb") and double click on the .deb to install. Tray Icon is included. Please direct feedback for the deb package to 47th_Ronin

---

### Post by La muerte del DIos on 2006-06-17
Nice work. Already using Nicotine+. Thanks man.

---

### Post by foofightrs777 on 2006-06-18
Worked great for me!  Thanks!

Tray icon worked as well.  If you don't have luck maybe try alltray?

---

### Post by bionnaki on 2006-06-19
you rule.
thanks

---

### Post by prkfriryce on 2006-06-21
getting a python2.4 error.
```
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at http://sourceforge.net/projects/psyco/
Warning: Trayicon Python module not found.
Traceback (most recent call last):
  File "nicotine", line 149, in ?
    app = frame.MainApp(config)
  File "/home/cpage/software/nicotine+-1.2.2/pynicotine/gtkgui/frame.py", line 1189, in __init__
    self.frame = testwin(config)
  File "/home/cpage/software/nicotine+-1.2.2/pynicotine/gtkgui/frame.py", line 270, in __init__
    if self.np.config.needConfig():
  File "/home/cpage/software/nicotine+-1.2.2/pynicotine/config.py", line 86, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker", "players") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.4/UserDict.py", line 168, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.4/UserDict.py", line 101, in iteritems
    yield (k, self[k])
  File "/usr/lib/python2.4/shelve.py", line 119, in __getitem__
    value = Unpickler(f).load()
cPickle.UnpicklingError: pickle data was truncated

```

reinstalled python2.4 and reinstalled nicotine1.2.2 but still no luck...](*,)

---

### Post by INMCM on 2006-06-21
you have python-gtk2 installed?

```
sudo apt-get install python-gtk2
```

python 2.4 and python-gtk are the only dependecies.

---

### Post by prkfriryce on 2006-06-21
[QUOTE=INMCM]you have python-gtk2 installed?

```
sudo apt-get install python-gtk2
```

python 2.4 and python-gtk are the only dependecies.[/QUOTE]

i also have the latest python-gtk2 installed

---

### Post by INMCM on 2006-06-21
Try installing the regular nicotine out of the repos

```
sudo apt-get install nicotine
```

and see if it works if it doesn't work, then you have more serious issues than I can fix

---

### Post by prkfriryce on 2006-06-21
[QUOTE=INMCM]Try installing the regular nicotine out of the repos

```
sudo apt-get install nicotine
```

and see if it works if it doesn't work, then you have more serious issues than I can fix[/QUOTE]

I previously tried using 1.2.0 beofre 1.2.2 and received the same results. Likewise, after i configured 1.0.8, the debug print is the same. :(

---

### Post by INMCM on 2006-06-21
Try deleting ~/.nicotine. Maybe you have a corrupt config file somewhere.

---

### Post by prkfriryce on 2006-06-21
[QUOTE=INMCM]Try deleting ~/.nicotine. Maybe you have a corrupt config file somewhere.[/QUOTE]

rm'd all instances of pynicotine and nicotine, then reinstalled and still the same errors. I will try to first remove, then reinstall python2.4 and python-gtk2 tomorrow.

---

### Post by henriquemaia on 2006-06-22
Thanks for posting this. I was not aware of nicotine+ existence.

---

### Post by bionnaki on 2006-06-23
I like how you can play audio files now. very nice.

---

### Post by frank_b on 2006-06-25
I installed nicotine+1.2.2 but, since it was not installed as a package, it didn't replace the old nicotine version and I still run the old version when I click the icon in the menu.

Should I now run nicotine only by executing "./nicotine" in the directory I got from the tar file?

Can I make an ubuntu package out of the tar file I downloaded and replace the old package?

Should I do this?

Should I remove the old nicotine package anyway?

---

### Post by INMCM on 2006-06-26
[QUOTE=frank_b]I installed nicotine+1.2.2 but, since it was not installed as a package, it didn't replace the old nicotine version and I still run the old version when I click the icon in the menu.

Should I now run nicotine only by executing "./nicotine" in the directory I got from the tar file?[/QUOTE]

Yes, you should run the extracted ./nicotine from now on. You should be able to edit the old menu entry with the menu editor to point to the new 1.2.2. You could also create a new icon on you panel.

[QUOTE=frank_b]Can I make an ubuntu package out of the tar file I downloaded and replace the old package?[/QUOTE]

If you know how to do such magic, then please do so and feel free to post it up here. Before I made this How-to I thought about learning how to package and slapping one together, but, given the simple nature of extracting and running the the python code, I felt it would be overkill.

On the other hand, it would be very nice if this replaced the OLD nicotine in the repos. I'm going to post this on the MOTU wiki and hope it get's picked up. If any MOTU people are reading this, this is a real simple thing to package and would be greatly appreciated by many many many folks.


[QUOTE=frank_b]Should I remove the old nicotine package anyway?[/QUOTE]

If it's less confusing, go ahead. It'll leave all your configs behind.

---

### Post by maxol on 2006-06-26
Thanks for this, if the repos are updated that would be fantastic.

---

### Post by frank_b on 2006-06-27
Thanks for your explanation INMCM. :)

As for the package, seems that there is already one, although barely tested.

I'll post more information about it soon, after I confirm some things.

---

### Post by asplode on 2006-06-27
I'm getting an error on the apt-get install line... I believe the correct metapackage is "build-essential"

---

### Post by INMCM on 2006-06-27
[QUOTE=asplode]I'm getting an error on the apt-get install line... I believe the correct metapackage is "build-essential"[/QUOTE]


This is correct, thank you much....*fixed*

---

### Post by 47th_Ronin on 2006-06-27
Hello all,

Good to be back on ubuntu forum and it's lovely users :)

I'm working on making Nicotine+ available for majoriy of Linux distro's
I have also written [Nicotine Guide](http://nicotine.le-vert.net/wiki/NicotineGuide)

As far for packages: I made a .deb file for debian/ubuntu
[COLOR="Red"]Warning!! Package is not been released yet! it is for testing only...[/COLOR] File name is not correct, according to debian/ubuntu packing guide...

After testing is finished, it will be released officially..

You can get it here: [Link removed, see next page for a new link]

[SIZE="2"]Please post your questions and feedbacks here. It will help me and benefit others [/SIZE]:)

Do not ask how to install this .deb file. If you don't know it, then wait for official release.. Don't forget I sad it's for [COLOR="Red"]TESTING ONLY.[/COLOR]

You might want to remove v1.0.8 before you install this one :)
I haven't experince any problems with this .deb file

Greetz,

Nicotine+ homepage: [http://nicotine.le-vert.net](http://nicotine.le-vert.net)

---

### Post by INMCM on 2006-06-27
[QUOTE=47th_Ronin]As far for packages: I made a .deb file for debian/ubuntu
[COLOR="Red"]Warning!! Package is not been released yet! it is for testing only...[/COLOR] File name is not correct, according to debian/ubuntu packing guide...

After testing is finished, it will be released officially..

You can get it here: [http://www.speedyshare.com/599428432.html](http://www.speedyshare.com/599428432.html)

[SIZE="2"]Please post your questions and feedbacks here. It will help me and benefit others [/SIZE]:)[/QUOTE]


Excellent!! Going to try this right after I back up my .nicotine directory.

---

### Post by henriquemaia on 2006-06-27
[quote=47th_Ronin]Hello all,

Good to be back on ubuntu forum and it's lovely users :)

I'm working on making Nicotine+ available for majoriy of Linux distro's
I have also written [Nicotine Guide]("http://nicotine.le-vert.net/wiki/NicotineGuide")

As far for packages: I made a .deb file for debian/ubuntu
[COLOR=Red]Warning!! Package is not been released yet! it is for testing only...[/COLOR] File name is not correct, according to debian/ubuntu packing guide...

After testing is finished, it will be released officially..

You can get it here: [http://www.speedyshare.com/599428432.html]("http://www.speedyshare.com/599428432.html")

[SIZE=2]Please post your questions and feedbacks here. It will help me and benefit others [/SIZE]:)

Do not ask how to install this .deb file. If you don't know it, then wait for official release.. Don't forget I sad it's for [COLOR=Red]TESTING ONLY.[/COLOR]

You might want to remove v1.0.8 before you install this one :)
I haven't experince any problems with this .deb file

Greetz,

Nicotine+ homepage: [http://nicotine.le-vert.net]("http://nicotine.le-vert.net")[/quote]

Hi,

First of all, a very big thank you for providing the package.

Ok, I'm running Dapper 64bit. I get this dependency error:

Error: Dependency is not satisfiable: python

I have python installed and can run nicotine+ through the cli.

---

### Post by frank_b on 2006-06-27
To INMCM and all:

The package I was talking about is the one made by 47th_Ronin, which I met yesterday in SoulSeek.

I was unsure if it worked with ubuntu also, besides debian, and seem to be having a problem dowloading the package.

I was suposed to bring the news here, but, because of my doubts, I was afraid to give a bad tip.

Fortunatly, in the meantime, 47th_Ronin made the anouncement himself, clearing my main doubt, and now you can speak to him directly making things more simple.

---

### Post by 47th_Ronin on 2006-06-27
[QUOTE=henriquemaia]Hi,

First of all, a very big thank you for providing the package.
```

```
Ok, I'm running Dapper 64bit. I get this dependency error:

Error: Dependency is not satisfiable: python

I have python installed and can run nicotine+ through the cli.[/QUOTE]

Thanks for the feedback... I'm searching for the problem... stay tuned!!

---

### Post by maxol on 2006-06-27
I have the same problem on 32bit dapper

"Error: Dependency is not satisfiable: python"

I have also have python installed and can run nicotine+.

I'm "6ecko" on slsk btw.

---

### Post by frank_b on 2006-06-27
I still can't download the file from the site... For some unknowned reason it downloads a 2.8 K file instead that seems like a mixture of and html file and a script...

Nevertheless, 47th_Ronin was nice enough to provide me the file directly, but I get the same error as henriquemaia (olá! :) ): an error message in gdebi saying "Error: Dependency is not satisfiable: python".

Also, through gdebi I can see that it will try to install files in two directories that don't exist in ubuntu: "/share" (there's a "/usr/share" in ubuntu, supose that would be the one instead) and "/debian".

I was right to be cautious. Seems that it's only a package for debian for the moment. 47th_Ronin is working on the problem.

---

### Post by mrazster on 2006-06-28
tried it lastnight....everything went perfect...trayicon compilation also. :) 
Haven't decided yet if I'm gonna stick with this or not.....seemes good so far thou.

---

### Post by 47th_Ronin on 2006-06-28
Thank you all for your feedback.
I made a new better .deb file for Nicotine+
This one should install better and have no depency problems...

[COLOR="Red"]It is STILL a test module! and dapper only! so no breezy or even debian![/COLOR]

You can get it here: [http://www.speedyshare.com/908491984.html](http://www.speedyshare.com/908491984.html)

You can give also feedback through slsk network, you can find me in nicotine chat room under the name "47th_Ronin" or "ronin.soulseek"

Don't get mad at me if I don't answer immidiatelly :p 

Again, thank you for your feedback :)

---

### Post by spockrock on 2006-06-28
thanks got everything working and the tray icon.

---

### Post by henriquemaia on 2006-06-28
[quote=47th_Ronin]Thank you all for your feedback.
I made a new better .deb file for Nicotine+
This one should install better and have no depency problems...

[COLOR=Red]It is STILL a test module! and dapper only! so no breezy or even debian![/COLOR]

You can get it here: [http://www.speedyshare.com/908491984.html]("http://www.speedyshare.com/908491984.html")

You can give also feedback through slsk network, you can find me in nicotine chat room under the name "47th_Ronin" or "ronin.soulseek"

Don't get mad at me if I don't answer immidiatelly :p 

Again, thank you for your feedback :)[/quote]

Great work, 47th_Ronin! Now the package installs flawlessly and nicotine runs smoothly. 

Not even a complaint from my Dapper 64bit.

---

### Post by spockrock on 2006-06-28
thanks worked perfectly.

---

### Post by INMCM on 2006-06-28
I'm editing my original HOW-TO to include the deb.

---

### Post by 47th_Ronin on 2006-06-28
[QUOTE=INMCM]I'm editing my original HOW-TO to include the deb.[/QUOTE]

Thanks!! one thing: I see this in the edited HOW-TO:

henriquemaia has made a deb of 1.2.2. This is a testing package and, while it works VERY well, there still might be issues. If you don't feel comfortable, use the breezy instructions below. Just download here and double click on the .deb to install. Tray Icon is included.


Are you sure it is henriquemaia?? ;)

---

### Post by INMCM on 2006-06-28
Ha, sorry about that. I was a bit too quick on the draw. Fixed.

---

### Post by 47th_Ronin on 2006-06-28
[QUOTE=INMCM]Ha, sorry about that. I was a bit too quick on the draw. Fixed.[/QUOTE]

np.. bro... I sad it incase people have problems they know who they should talk to instead of flaming other ubuntu user :)

one last thing for users who're REALLY paranoid... Nicotine+ will be soon available as valid debian package (whatever that means)
when it will be released and the respo line will be is still unknow... just keep checking this topic or nicotine chat room...

---

### Post by frank_b on 2006-06-29
Can't download this one from the site also, but 47th_Ronin kindly gave it to me directly again, I installed it and everything seems OK.

---

### Post by The Waco Kidd on 2006-07-03
I'm on Kubuntu, Dapper. Having problems installing from the deb. Any help appreciated. Output below...

> Password:
(Reading database ... 79299 files and directories currently installed.)
Preparing to replace nicotine+ 1.2.2 (using .../nicotine+_1.2.2_all_testing_v1.1.deb) ...
Package `nicotine' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Unpacking replacement nicotine+ ...
Setting up nicotine+ (1.2.2) ...
Can't list /usr/lib/site-python
Can't list /usr/lib/site-python

Press <enter> to exit...

---

### Post by VFiend on 2006-07-03
I've installed the deb package and I'm getting the error:
Warning: Trayicon Python module not found.

Any ideas?

---

### Post by INMCM on 2006-07-03
Try installing the tray icon by compiling from source.

---

### Post by 47th_Ronin on 2006-07-07
> **The Waco Kidd said:**
> I'm on Kubuntu, Dapper. Having problems installing from the deb. Any help appreciated. Output below...

I assume you haven't remove 1.0.8 before installing 1.2.2
or
1.0.8 is running at the same time you're installing 1.2.2
maybe
python isn't installed properly... /usr/lib/site-packages is a dir that it's included in python 2.4 installation.. so if it's missing, then you have a corrupt installation of python...

Let me know how it went...

sorry for answering so late, was busy fixing Nicotine windows installer :)

---

### Post by 47th_Ronin on 2006-07-07
> **VFiend said:**
> I've installed the deb package and I'm getting the error:
Warning: Trayicon Python module not found.

Any ideas?

while I was making this .deb, I didn't pay any attention to Trayicon... however it is included in .deb.

Official debian packages are source only.. so if you install the following: build-essential python-dev python-gtk2-dev libgtk2.0-dev

and re-run the .deb installation it will get compiled and installed :)

No garantee that it will work, but just an idea :)

---

### Post by INMCM on 2006-07-07
How-to has been updated for version 1.2.3. Ronin, I hope we can see a deb soon.

---

### Post by OffHand on 2006-07-08
I have been using nicotine+ for quite a while.
I have just installed the latest version but I cannot get the trayicon to work, eventhough I installed it.

```

admin@dapper:~$ cd ~/.nicotine+-1.2.3
admin@dapper:~/.nicotine+-1.2.3$ cd trayicon
admin@dapper:~/.nicotine+-1.2.3/trayicon$ ./autogen.py
Generating Makefile for python 2.4
Done.. Now run 'make install' as root
admin@dapper:~/.nicotine+-1.2.3/trayicon$ sudo make install
install -d /usr/lib/python2.4/site-packages/pynicotine
install -m 755 trayicon.so /usr/lib/python2.4/site-packages/pynicotine
admin@dapper:~/.nicotine+-1.2.3/trayicon$

```

I get this

```

cannot import name trayicon
Warning: Trayicon Python module not found.

```

EDIT:

Somehow I got it working with the cp command. I copied those files before and it didn't work. Weird... Anyways, version 1.2.3+ uses other icons. If you guys wanna know how to get back the old icons let me know and I'll post what to do.

---

### Post by The Waco Kidd on 2006-07-09
> **47th_Ronin said:**
> ...

Let me know how it went...

sorry for answering so late, was busy fixing Nicotine windows installer :)

Thanks for your reply. I'm actually away from my Kubuntu box for another 10 days, will try your suggestions when I get back and let you know how it goes.
Cheers :)

---

### Post by 47th_Ronin on 2006-07-09
> **INMCM said:**
> How-to has been updated for version 1.2.3. Ronin, I hope we can see a deb soon.

sure, bro... stay tuned... 1 or 2 days...

since the .deb for 1.2.2 I have gained some more knowledge to make a .deb that follows debian guide-lines... so it will be much better than 1.2.2 deb...

greets :)

---

### Post by 47th_Ronin on 2006-07-09
> **subsonic_shadow said:**
> I have been using nicotine+ for quite a while.
I have just installed the latest version but I cannot get the trayicon to work, eventhough I installed it.

```

admin@dapper:~$ cd ~/.nicotine+-1.2.3
admin@dapper:~/.nicotine+-1.2.3$ cd trayicon
admin@dapper:~/.nicotine+-1.2.3/trayicon$ ./autogen.py
Generating Makefile for python 2.4
Done.. Now run 'make install' as root
admin@dapper:~/.nicotine+-1.2.3/trayicon$ sudo make install
install -d /usr/lib/python2.4/site-packages/pynicotine
install -m 755 trayicon.so /usr/lib/python2.4/site-packages/pynicotine
admin@dapper:~/.nicotine+-1.2.3/trayicon$

```

I get this

```

cannot import name trayicon
Warning: Trayicon Python module not found.

```

EDIT:

Somehow I got it working with the cp command. I copied those files before and it didn't work. Weird... Anyways, version 1.2.3+ uses other icons. If you guys wanna know how to get back the old icons let me know and I'll post what to do.


Ehm... maybe I missed something, but on Nicotine Trac there's a page about TrayIcon issue in 1.2.3 :)

---

### Post by 47th_Ronin on 2006-07-11
@INMCM... you got PM :D

---

### Post by INMCM on 2006-07-12
*BUMP* For Updated DEB package..See First post

---

### Post by 47th_Ronin on 2006-07-13
I got feedback from one of the .deb users:

> beke feedback van n newbie: nieuw icoon in mn panel is ietske groter as de rest vd icons
Translation:> 
[babelfish says] a little feedback from a newbie: icon used in my panel is larger than the rest of the icons...

He also was kind enough to send me a screenshot to make clear what he ment... 

what the hell does he mean?? well, read on!

Nicotine icon is the old one... the one daelstorm made for gentoo??.. but IMHO I wanted icon to be in line with the new logo as seen on nicotine pages...

The famous orange circle with a white N.... So I got my hands on .xcf of the logo and copy&paste the "N" en used it as icon... the icon is however on the edge.. so no empty spaces arround it...

That's the reason why the icon appears large.. even when you shrink the logo and replace it... The same you can see with XMMS logo...

So for all you gnome users, I fixed the issue by making one for my favorite ubuntu users :)

You can get the logo [here]("http://www.speedyshare.com/856620986.html")

HowTo use:
- download :p
- rename it to nicotine.png
- place it in /usr/local/share/pixmaps/
- restart x... (I'm not sure about this, but if I remember it should)
====================================================

@INMCM: check your PM... again?? yeah, man.. HUGE NEWS :p   Oeps!!! I didn't see your reply PM :S... ohhh well, next time I just post here :)... sorry for the hussle..

---

### Post by loell on 2006-07-13
hi i'm new to nicotine p2p
do i need to have a username and password?

---

### Post by INMCM on 2006-07-13
loell, You can just make one up intially.

---

### Post by loell on 2006-07-13
thanks :)

---

### Post by Kevf on 2006-07-13
Thanks, lets see if I can get it working. 8)

---

### Post by th0mas on 2006-07-19
hello,

thank you for this howto !

but this problem i had in nicotine didn't disappear with nicotine+ :
people can't browse my shared files (e.g. some friend using soulseek).
though i can download from others.

I configured my routeur like this :
port from 2234 to 2240 are TCP-redirected to my computer

any clue ?

---

### Post by 47th_Ronin on 2006-07-20
> **th0mas said:**
> hello,

thank you for this howto !

but this problem i had in nicotine didn't disappear with nicotine+ :
people can't browse my shared files (e.g. some friend using soulseek).
though i can download from others.

I configured my routeur like this :
port from 2234 to 2240 are TCP-redirected to my computer

any clue ?

PM me at nicotine chatroom and I go trough all the steps I go with many users to fix this issue :)

---

### Post by 47th_Ronin on 2006-07-20
Nicotine+ 1.2.4 (beta) SVN is available for Ubuntu Dapper

you can get it here: [http://osiris.codedchaos.com/](http://osiris.codedchaos.com/)

version 1.2.4 has very nice feature.. you can choose your own theme... at the moment there're almost no themes available... consider making one.. 
more info: [http://osiris.codedchaos.com/](http://osiris.codedchaos.com/)

greets,

---

### Post by The Waco Kidd on 2006-07-20
> **47th_Ronin said:**
> I assume you haven't remove 1.0.8 before installing 1.2.2
or
1.0.8 is running at the same time you're installing 1.2.2
maybe
python isn't installed properly... /usr/lib/site-packages is a dir that it's included in python 2.4 installation.. so if it's missing, then you have a corrupt installation of python...

Let me know how it went...


Finally got round to this...

Am now working with latest 1.24 beta deb

Removed previous Nicotine instalation and that's solved the first problem.

The second one has been more thorny. I've reinstalled python 2.4 and that dir still isn't there. There is, however, in /usr/lib a /python 2.4 directory which has a /site-packages directory within. Might this be the one the installer is looking for or am I on totally the wrong track?

New output below, not that it seems to be saying anything fresh. Any help is truly appreciated...

> (Reading database ... 99101 files and directories currently installed.)
Preparing to replace nicotine+ 1.2.4 (using .../nicotine+-1.2.4beta-osiris.svn.deb) ...
Package `nicotine' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Unpacking replacement nicotine+ ...
Setting up nicotine+ (1.2.4) ...
Can't list /usr/lib/site-python
Can't list /usr/lib/site-python

---

### Post by 47th_Ronin on 2006-07-20
@ The Waco Kidd:

You downloaded 1.2.4 beta svn .deb package... now tell me the command you use to install it?

```
 dpkg -i nicotine+-x.x.x.deb 
```

or something else?

---

### Post by The Waco Kidd on 2006-07-21
> **47th_Ronin said:**
> @ The Waco Kidd:

You downloaded 1.2.4 beta svn .deb package... now tell me the command you use to install it?

```
 dpkg -i nicotine+-x.x.x.deb 
```

or something else?

No, I was right clicking on the deb, then selecting 'Kubuntu Package Menu/Install Package'. I tried using the code you suggested and got very similar output.

> sudo dpkg -i nicotine+-1.2.4beta-osiris.svn.deb
Password:
(Reading database ... 99221 files and directories currently installed.)
Preparing to replace nicotine+ 1.2.4 (using nicotine+-1.2.4beta-osiris.svn.deb) ...
Package `nicotine' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Unpacking replacement nicotine+ ...
Setting up nicotine+ (1.2.4) ...
Can't list /usr/lib/site-python
Can't list /usr/lib/site-python

---

### Post by 47th_Ronin on 2006-07-21
@ The Waco Kidd

I installed a fresh dapper last night... for you I'm gonna test to see what exacly is wrong... stay tuned!

I have installed nicotine 1.2.4..

---

### Post by The Waco Kidd on 2006-07-21
Oh. Thankyou. You managed to install on **Kubuntu** Dapper, right?

---

### Post by 47th_Ronin on 2006-07-23
> **The Waco Kidd said:**
> Oh. Thankyou. You managed to install on **Kubuntu** Dapper, right?

I don't think it has anything to do with KDE or Gnome.... before I go any deeper... can you please copy & paste your sources.list??

use this service if you like: [http://pastebin.ca](http://pastebin.ca)
and post the link here or PM it..

greets,

---

### Post by bionnaki on 2006-07-24
the latest version (123) is great. now only if nicotine could fix it's display of user speeds.

---

### Post by The Waco Kidd on 2006-07-24
> **47th_Ronin said:**
> can you please copy & paste your sources.list??

use this service if you like: [http://pastebin.ca](http://pastebin.ca)
and post the link here or PM it..

greets,

Okay, here it is. Thanks for sticking with me on this!

[http://pastebin.ca/98920](http://pastebin.ca/98920)

---

### Post by RavenOfOdin on 2006-07-24
how to Nicotine+ . . .

Easy. . .

Chain smoke. :D
smoke == Nicotine where chain smoking == Nicotine+.

I just feel like joking around, don't mind me.

Anywho, I might start using some sort of p2p again if I can get a USB hard drive set up to hold it all.

---

### Post by 47th_Ronin on 2006-07-24
> **RavenOfOdin said:**
> how to Nicotine+ . . .

Easy. . .

Chain smoke. :D
smoke == Nicotine where chain smoking == Nicotine+.

I just feel like joking around, don't mind me.

Anywho, I might start using some sort of p2p again if I can get a USB hard drive set up to hold it all.

:p ](*,)

---

### Post by jbaskr on 2006-07-26
I'm having a similar problem to prkfriryce on the first two pages--

<code>Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
cannot import name trayicon
Warning: Trayicon Python module not found.
Traceback (most recent call last):
  File "/usr/bin/nicotine", line 149, in ?
    app = frame.MainApp(config)
  File "/usr/lib/python2.4/site-packages/pynicotine/gtkgui/frame.py", line 1249, in __init__
    self.frame = testwin(config)
  File "/usr/lib/python2.4/site-packages/pynicotine/gtkgui/frame.py", line 260, in __init__
    if self.np.config.needConfig():
  File "/usr/lib/python2.4/site-packages/pynicotine/config.py", line 86, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker", "players") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.4/UserDict.py", line 168, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.4/UserDict.py", line 101, in iteritems
    yield (k, self[k])
  File "/usr/lib/python2.4/shelve.py", line 119, in __getitem__
    value = Unpickler(f).load()
cPickle.UnpicklingError: invalid load key, '/'.</code>

I installed the original Nicotine on my Dapper machine, and it worked fine -- it stopped working a few days ago, and I uninstalled it via symantec, & installed Nicotine+.  I've tried deleting config files, uninstalling nicotine & the various python files suggested.  Any ideas?

---

### Post by jbaskr on 2006-07-26
aha --
I just created a new "blank" user in ubuntu & tried to launch nicotine from there - it worked perfectly.  I can use this as a workaround (the program is great!) but if anyone knows what's going on, that would be deeply cool.

---

### Post by 47th_Ronin on 2006-07-27
> **The Waco Kidd said:**
> Okay, here it is. Thanks for sticking with me on this!

[http://pastebin.ca/98920](http://pastebin.ca/98920)

Sorry for my LATE answer.. I have trying every possible way to figurout why you have "Can't list /usr/lib/site-python" error..
Before I go and start type some huge story of what I have done, can you please tell me what you get when you typ following command in terminal?
```
apt-get -f install
```

Don't be scared it continues doing stuff.. it won't break your system. It suppose to fix broken packages :)

Thanks... I go now finding some wall to ](*,)  (I feel so stupid, not being able to help you faster :()

For the rest of you:

* new SVN is in make... includes:
- nicotine+ icon fixed for gnome
- menu is fixed (Nicotine+ instead of P2P)
- man pages
- huge .png in user-info bug-fix?? (I assume)

* TrayIcon .deb is in make :D
* Docs .deb is in make for those who need it :)

Wanted!
I want a nicotine+ ubuntu icon-theme. more info & template can be find at [http://osiris.codedchaos.com](http://osiris.codedchaos.com). if anybody wants to help me out, please do!

---

### Post by 47th_Ronin on 2006-07-27
@jbaskr
never, ever remove files manually!! specially if there're installed.. it's like removing files in system32 on windoze..

even I make mistakes.. anyway... try this in your profile that has the broken nicotine:

```
apt-get -f install
```

say what it says.. then we will see what happens :)

greetz,
PS. running from source?? does that work?? try it and tell me the results also :)

---

### Post by The Waco Kidd on 2006-07-27
Output as requested...

> :~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by 47th_Ronin on 2006-07-27
> **The Waco Kidd said:**
> Output as requested...

thanks, now some more questions :p

- have you ever been able to run nicotine?? (no matter which version)
- running from source, have you tried that??

---

### Post by jbaskr on 2006-07-27
Thanks for the help!
but... same output after apt-get -f install:

> Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

not sure how I'd run from source in this situation... apologies.

---

### Post by 47th_Ronin on 2006-07-28
Nicotine+ 1.2.4beta July 24, 2006 SVN available for download.

see [http://osiris.codedchaos.com](http://osiris.codedchaos.com)

---

### Post by vision on 2006-07-29
I have a problem with Nicotine+ - I was using v1.2.3 when without a reason my PC restarted. After that when I opened Nicotine+ it showed the Settings window as if this is the first time I run the program even tho my login name and password, shared download directory etc. were still the same as always. I clicked OK but it still shows the message "You need to finish configuring your settings (Server, Username, Password, Download Directory) before connecting...". I uninstalled it and downloaded v1.2.4 but nothing changes. Am I doing something wrong? Could be since basically im still a Ubuntu newbie.. Can anyone help? Also you probably noticed - my english isn't that good, im from Bulgaria.

---

### Post by 47th_Ronin on 2006-07-30
> **vision said:**
> I have a problem with Nicotine+ - I was using v1.2.3 when without a reason my PC restarted. After that when I opened Nicotine+ it showed the Settings window as if this is the first time I run the program even tho my login name and password, shared download directory etc. were still the same as always. I clicked OK but it still shows the message "You need to finish configuring your settings (Server, Username, Password, Download Directory) before connecting...". I uninstalled it and downloaded v1.2.4 but nothing changes. Am I doing something wrong? Could be since basically im still a Ubuntu newbie.. Can anyone help? Also you probably noticed - my english isn't that good, im from Bulgaria.

- uninstall 1.2.4 or any version you have...
- remove .nicotine from your home directory
- install 1.2.4
- configure settings and connect...

should work :)

---

### Post by vision on 2006-07-30
Yes, it did! I was thinking of deleting the whole Nicotine folder but as I said in my other post - I still have much to learn about Ubuntu and I didnt know that the folder was hidden. Anyway thanks for answering. :)

---

### Post by 47th_Ronin on 2006-07-31
@ The Waco Kidd

a shame you didn't answer my last questions... now you never know the answer and also wasted my time :)

good luck...

---

### Post by The Waco Kidd on 2006-07-31
Huh! Well I'm sorry if I was too busy with all the other stuff in my life to answer your question immediately. Much as I'd like to I don't have much time as I'd like to work on non-essential fun stuff like Nicotine.

If you're still up for helping me then great, if not then...not much I can say, really, is there? That's a bummer, I was really hoping I'd be able to get this to work.

---

### Post by 47th_Ronin on 2006-08-01
> **The Waco Kidd said:**
> Huh! Well I'm sorry if I was too busy with all the other stuff in my life to answer your question immediately. Much as I'd like to I don't have much time as I'd like to work on non-essential fun stuff like Nicotine.

If you're still up for helping me then great, if not then...not much I can say, really, is there? That's a bummer, I was really hoping I'd be able to get this to work.

hahahah... bro, sorry... man... Offcourse I want to help you... I had this odd feeling you might not wanting me to help you since people useally stop when someone says "have you triend running from source?" which is useally already a sign of people not being able to help... anyway.. I'm still here :D

But in this case I might know more if you tell me if you can or can't run from source... So looking forward to know... take your time :)

looking forward to solve this issue of yours, so people in the future get helped faster after we finally find out what the problem was...

Greets from a shames idiot.. :p

---

### Post by The Waco Kidd on 2006-08-01
> **47th_Ronin said:**
> hahahah... bro, sorry... man... Offcourse I want to help you... I had this odd feeling you might not wanting me to help you since people useally stop when someone says "have you triend running from source?" which is useally already a sign of people not being able to help... anyway.. I'm still here :D

But in this case I might know more if you tell me if you can or can't run from source... So looking forward to know... take your time :)

looking forward to solve this issue of yours, so people in the future get helped faster after we finally find out what the problem was...

Greets from a shames idiot.. :p

LOL. No worries, you're cool. And thanks again for all your help so far.

Background, I suppose...I'm fairly green w/Linux and these forums so don't know so much of convention. I have no idea what 'running from source' means, so when I read your message I just thought 'okay, that's going to take a few hours, I'm going to have to RTFM so I'll wait until I've got the time...' and got on with my work.

But getting this to run does mean a lot to me. This is my second serious attempt to switch to Linux, and the first time out the lack of a decent SLSK client was a dealbreaker. Since then my problems with Windows and addiction to KDE has grown to the point where I'd decided to just live without SLSK. But it'd still be great to not have to!

I'm mad busy this week, but I WILL make time to get my head round this at the weekend.

---

### Post by 47th_Ronin on 2006-08-04
> **The Waco Kidd said:**
> LOL. No worries, you're cool. And thanks again for all your help so far.

Background, I suppose...I'm fairly green w/Linux and these forums so don't know so much of convention. I have no idea what 'running from source' means, so when I read your message I just thought 'okay, that's going to take a few hours, I'm going to have to RTFM so I'll wait until I've got the time...' and got on with my work.

But getting this to run does mean a lot to me. This is my second serious attempt to switch to Linux, and the first time out the lack of a decent SLSK client was a dealbreaker. Since then my problems with Windows and addiction to KDE has grown to the point where I'd decided to just live without SLSK. But it'd still be great to not have to!

I'm mad busy this week, but I WILL make time to get my head round this at the weekend.

Runnin from source: useally it means downloading source of a software and compile it yourself.. BUT Nicotine doesn't need to be compiled nor installed to run.

So when you have time, download nicotine+-1.2.3.tar.bz2 from sf.net pages and do the following:

- unpack it on your desktop, so you get directory nicotine+-1.2.3
- start Terminal
- do this command: cd /usr/home/username/Desktop/nicotine+-1.2.3
- then this command: ./nicotine

link: [Nicotine+ sf.net page]("http://nicotine-plus.sourceforge.net/")

I just wait see what the results are... goodluck and next time, just keep asking when you even don't get the smallest thing :)

---

### Post by 47th_Ronin on 2006-08-04
NNPScript is now available for download. It allows you to display current listen song in Nicotine+

more info: [Chapter  6.1.1 of Nicotine+ Guide]("http://osiris.codedchaos.com/nicotine.guide/NicotineGuide/Extra/AddOn/NNPScript.htm")

---

### Post by The Waco Kidd on 2006-08-06
First thing first - yes, I had the old version in the repositries working but I found it useless compared to the Windows client.

Oddly enough, I checked synaptic before I tried to run from source, and nicotine+ is showing as installed. But I still wasn't able to run it until I followed your instructions and now it's running, sort of. I can't seem to make any download connections, but that's a whole other issue which I have a few hunches on...

---

### Post by The Waco Kidd on 2006-08-06
Okay, I got the download problem sorted out - a simple matter of playing with the settings on my router and now I'm connected. Thankyou for your help!

Is there any way I could set it up to launch automatically from an icon rather than via the command line every time?...

---

### Post by OffHand on 2006-08-08
> **The Waco Kidd said:**
> Okay, I got the download problem sorted out - a simple matter of playing with the settings on my router and now I'm connected. Thankyou for your help!

Is there any way I could set it up to launch automatically from an icon rather than via the command line every time?...

There is. I have added a link to my top panel.
Right click on the panel, pick 'add to panel', pick 'custom launcher'.
Name it and give it an icon.
The link would be something like:

/home/admin/.nicotine+-1.2.3/nicotine

Just change the path to match your setup.
Now you can start Nivotine+ by clicking the icon.

---

### Post by 47th_Ronin on 2006-08-08
Funkey Waco!! :p

finally you're online! which confuses me even more... the reason is if you were not able to run nicotine+ from source you probly didn't have pygtk.. that happens when you uninstall (k)ubuntu-desktop... which removes pygtk but you keep gnome/kde

so now you can run from source I wonder what the hell the problem is... as I cannot check what you have done with your setup I can only guess... BUT, now I sleep better... 

anyway... have fun with Nicotine+

All the other users:

there're 2 new /alias available: nMyLCTime and nCPUinfo
more info: [Chapter 6.1 ]("http://osiris.codedchaos.com/nicotine.guide/NicotineGuide/Extra/AddOn.htm")of Nicotine+ Guide

---

### Post by adds2one on 2006-08-09
Hi there,

I installed Nicotine+-1.2.3 and the tray icon a few days ago and everything worked great. Then I did a complete reinstall of my system, wiped my hard drive clean and started fresh. No I just installed Nicotine+-1.2.3 again which is working great! :) Sadly though this time around the trayicon doesn't seem to work. I followed the instructions at the top of this thread exactly and got no errrors at all.

Can anyone help me in my quest to get my trayicon to work again?

---

### Post by OffHand on 2006-08-10
> **adds2one said:**
> Hi there,

I installed Nicotine+-1.2.3 and the tray icon a few days ago and everything worked great. Then I did a complete reinstall of my system, wiped my hard drive clean and started fresh. No I just installed Nicotine+-1.2.3 again which is working great! :) Sadly though this time around the trayicon doesn't seem to work. I followed the instructions at the top of this thread exactly and got no errrors at all.

Can anyone help me in my quest to get my trayicon to work again?

Ask in the Nicotine room. The devs are chatting there too.

---

### Post by The Waco Kidd on 2006-08-10
> **47th_Ronin said:**
> so now you can run from source I wonder what the hell the problem is... as I cannot check what you have done with your setup I can only guess... BUT, now I sleep better... 

anyway... have fun with Nicotine+

Thankyou! Maybe one day I'll understand what went wrong. Now I'm just relieved I've got it working.

And it's way, way better than 1.08.

---

### Post by 47th_Ronin on 2006-08-11
> **adds2one said:**
> Hi there,

I installed Nicotine+-1.2.3 and the tray icon a few days ago and everything worked great. Then I did a complete reinstall of my system, wiped my hard drive clean and started fresh. No I just installed Nicotine+-1.2.3 again which is working great! :) Sadly though this time around the trayicon doesn't seem to work. I followed the instructions at the top of this thread exactly and got no errrors at all.

Can anyone help me in my quest to get my trayicon to work again?

can you cut& paste errors you get here?? or use [http://pastebin.ca](http://pastebin.ca)

---

### Post by adds2one on 2006-08-12
Unfortunately I got no errors at all so I have nothing to cut and paste. I followed the instructions exactly as per the original post of this thread.

Any ideas on what to check for? Any methods for troubleshooting?

I really miss the tray icon. :(

---

### Post by 47th_Ronin on 2006-08-13
> **adds2one said:**
> Unfortunately I got no errors at all so I have nothing to cut and paste. I followed the instructions exactly as per the original post of this thread.

Any ideas on what to check for? Any methods for troubleshooting?

I really miss the tray icon. :(

maybe a stupid question.. did you install pygtk?

---

### Post by adds2one on 2006-08-15
not a stupid question, but yes I did install pygtk.

---

### Post by 47th_Ronin on 2006-08-15
> **adds2one said:**
> not a stupid question, but yes I did install pygtk.

before we go on trying the suggestion, I assume you run dapper... if you run breezy, forget about installing my nicotine debian-package as it will not work...

if you run breezy:
download & unpack nicotine+ 1.2.3 from sf.net pages
install it:
```

cd nicotine+-1.2.3
python setup.py install
nicotine #command to run
```
you will not have a menu entry as you can make it yourself. 

my suggestions:

-suggestion 1:
1. first start Nicotine+ via Terminal
open Terminal and typ nicotine
that should give you what's wrong.. maybe something is missing and you will be able to cut&paste the output

-suggestion 2: (do every step as you can see)
1. remove every nicotine related stuff.. so nicotine-1.0.8, python-gtk2 and python-pyvorbis
```
apt-get remove nicotine python-gtk2 python-pyvorbis
```
2. remove .nicotine dir in your /home (maybe back it up)
3. install nicotine-1.0.8, python-gtk2 and python-pyvorbis
```
apt-get install nicotine python-gtk2 python-pyvorbis
```
4. start Nicotine+ via Terminal
```
username@ubuntu:~# nicotine
```
5. cut&paste the output... (for later)
6. if nicotine 1.0.8 starts correct we can move to follwing steps:
7. remove nicotine-1.0.8
```
apt-get remove nicotine
```
8. download nicotine+ 1.2.3 and save it on your desktop
9. double click it and wait till you see "depencies satisfied"
10. install!!
11. see step 4&5...

I just wait to see what happens. if Nicotine+ is still not running use this service [http://pastebin.ca](http://pastebin.ca) to pass the output...

good luck!

---

### Post by adds2one on 2006-08-16
I am running Dapper. Just to clarify, the only thing not working for me is the tray icon.

---

### Post by 47th_Ronin on 2006-08-17
> **adds2one said:**
> I am running Dapper. Just to clarify, the only thing not working for me is the tray icon.

ohh god... oke, if you install 1.2.3 deb then indeed TrayIcon is not included. You need to install that from source... [http://nicotine.le-vert.net/wiki/TrayIcon](http://nicotine.le-vert.net/wiki/TrayIcon)

Note: [This page]("http://nicotine.le-vert.net/wiki/IssuesWithNicotinePlus") is NOT what you should do, It counts only when you run from source.

1.2.3 source [download]("http://prdownloads.sourceforge.net/nicotine-plus/nicotine%2B-1.2.3.tar.bz2?download") (as trayicon is included)

---

### Post by stokedfish on 2006-08-18
Nicotine+ 1.2.4 (August 17 2006) 432 KB (bz2)

[http://nicotine-plus.sourceforge.net/](http://nicotine-plus.sourceforge.net/)

Will there be a new deb? That would be awesome! ;)

---

### Post by OffHand on 2006-08-18
> **stokedfish said:**
> Nicotine+ 1.2.4 (August 17 2006) 432 KB (bz2)

[http://nicotine-plus.sourceforge.net/](http://nicotine-plus.sourceforge.net/)

Will there be a new deb? That would be awesome! ;)

It is really easy to compile it yourself. I am sure another deb will be online soon though.

---

### Post by INMCM on 2006-08-18
*BUMP* Updated for 1.2.4.1

---

### Post by TOPPEL on 2006-08-22
i need a deb for 1.2.4.1 

please someone help.. osirus.codedchaos.com is down.  i can provide mirrored hosting for the .deb if someone please do the honors.  

thanks

:-k

---

### Post by INMCM on 2006-08-22
> **TOPPEL said:**
> i need a deb for 1.2.4.1 

please someone help.. osirus.codedchaos.com is down.  i can provide mirrored hosting for the .deb if someone please do the honors.  

thanks

Do you really NEED a .deb? The source instructions on the first page are very simple (no compiling) and the only thing you aren't automatically given is an icon which is also a piece of cake to add using the menu editor. These are VERY fresh releases here, and .debs take time and effort to make and test. You could already be using the program right now, instead of waiting for a .deb.

---

### Post by 47th_Ronin on 2006-08-23
> **TOPPEL said:**
> i need a deb for 1.2.4.1 

please someone help.. osirus.codedchaos.com is down.  i can provide mirrored hosting for the .deb if someone please do the honors.  

thanks

:-k

I'm so sorry for the problems with my host... it has been down for a while now because of host switch with probly means a faster server...

1.2.4.1 deb and extra TrayIcon deb are ready... but I have no other options to distribute them since my files are uploaded and don't have them... and can't download it either... if everything goes well, it should be back in 2 days...

again, sorry for the problems...

UPDATE: I found it :D... [Nicotine+ 1.2.4.1Ubuntu Dapper package](http://www.osiris.codedchaos.com/osiris/request.php?23)

---

### Post by th0mas on 2006-08-24
noob question someone ?

i have Nicotine+ 1.2.3 installed by hand one month ago.
i also have the Nicotine ubuntu package

How do I upgrade to the last version ?
Do I have to remove the 1.2.3 before ? How ?
Do you like tomatoes ?

thx !

---

### Post by isolationist on 2006-08-24
can someone re-upload that .deb to another sharing service please? speedyshare doesn't let me to grab one...

---

### Post by INMCM on 2006-08-24
> **th0mas said:**
> noob question someone ?

i have Nicotine+ 1.2.3 installed by hand one month ago.
i also have the Nicotine ubuntu package

How do I upgrade to the last version ?
Do I have to remove the 1.2.3 before ? How ?
Do you like tomatoes ?

thx !

When you say "by hand" did you use the deb or source?

---

### Post by 47th_Ronin on 2006-08-24
> **isolationist said:**
> can someone re-upload that .deb to another sharing service please? speedyshare doesn't let me to grab one...

[Nicotine+ 1.2.4.1 Dapper Package](http://www.osiris.codedchaos.com/osiris/request.php?23)

---

### Post by isolationist on 2006-08-25
big thanks

---

### Post by shunthemask on 2006-08-25
Hi,

I have a question regarding the trayicon in version 1.2.4.1 (and yes, I am running Dapper).  I installed nicotine from source and it now runs fine, but I can't get the trayicon to work.  I made the makefile, but when I run the makefile:

sudo make install
Password:
cc `pkg-config --cflags gtk+-2.0 pygtk-2.0` -I/usr/include/python2.4/ -I. -fPIC   -c -o trayicon.o trayicon.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package pygtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `pygtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pygtk-2.0' found
/bin/sh: cc: command not found
make: *** [trayicon.o] Error 127

so I tried to install it via the .deb instead:

sudo dpkg -i nicotine+-1.2.4.1-i386-dapper.deb
(Reading database ... 83655 files and directories currently installed.)
Preparing to replace nicotine+ 1.2.4.1 (using nicotine+-1.2.4.1-i386-dapper.deb) ...
Unpacking replacement nicotine+ ...
Setting up nicotine+ (1.2.4.1) ...
Can't list /usr/lib/site-python
Can't list /usr/lib/site-python

Nicotine itself runs fine, so I figured that all of the dependencies are installed.

thanks

---

### Post by INMCM on 2006-08-25
See Next.... :mad:

---

### Post by INMCM on 2006-08-25
> **shunthemask said:**
> Hi,

I have a question regarding the trayicon in version 1.2.4.1 (and yes, I am running Dapper).  I installed nicotine from source and it now runs fine, but I can't get the trayicon to work.  I made the makefile, but when I run the makefile:

sudo make install
Password:
cc `pkg-config --cflags gtk+-2.0 pygtk-2.0` -I/usr/include/python2.4/ -I. -fPIC   -c -o trayicon.o trayicon.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package pygtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `pygtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pygtk-2.0' found
/bin/sh: cc: command not found
make: *** [trayicon.o] Error 127

so I tried to install it via the .deb instead:

sudo dpkg -i nicotine+-1.2.4.1-i386-dapper.deb
(Reading database ... 83655 files and directories currently installed.)
Preparing to replace nicotine+ 1.2.4.1 (using nicotine+-1.2.4.1-i386-dapper.deb) ...
Unpacking replacement nicotine+ ...
Setting up nicotine+ (1.2.4.1) ...
Can't list /usr/lib/site-python
Can't list /usr/lib/site-python

Nicotine itself runs fine, so I figured that all of the dependencies are installed.

thanks


Ok, sounds like you didn't do the first line of the instructions

```
sudo apt-get install build-essential python-dev python-gtk2-dev libgtk2.0-dev
``` 

Do that then, the ./autogen.py...make...sudo make install...etc....it should work then.

---

### Post by shunthemask on 2006-08-25
> **INMCM said:**
> Ok, sounds like you didn't do the first line of the instructions

```
sudo apt-get install build-essential python-dev python-gtk2-dev libgtk2.0-dev
``` 

Do that then, the ./autogen.py...make...sudo make install...etc....it should work then.

You're right, I installed all of the packages from synaptic before I saw this how-to.  But of course, now I am having trouble with the dependencies: build-essential and python-dev came through fine, but python-gtk2-dev won't install because libgtk2.0-dev depends upon broken packages, as far as I can tell:

```
$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages

```

I take it this means that I should wait for the packages to be fixed?  I tried to install these two in synaptic, but I got more broken package errors.

Just in case:
```
$ sudo apt-get update
Reading package lists... Done
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

If you can't tell, I'm a bit of a noob.  So what should I do now?

thanks.

---

### Post by th0mas on 2006-08-26
> **INMCM said:**
> When you say "by hand" did you use the deb or source?

i had installed nicotine using the howto on the first page of this topic, which requires just to untar the nicotine folder.
I assume i can install the 1.2.4 version next to the 1.2.3, and even delete the nicotine+-1.2.3/ folder if i want. Am I right ?

btw, i just installed the 1.2.4.1 version, and compiled the trayicon successfully. And now, I'd like to be able to launch nicotine+1.2.4.1 just by typing nicotine+ in a terminal, wherever i am in the folder tree (i already know how to create a gnome launcher), how do i create this bin shortcut ?

thx

---

### Post by INMCM on 2006-08-26
try 

```
sudo ln -s /path/to/program /usr/bin
```

---

### Post by th0mas on 2006-08-26
> **INMCM said:**
> try 

```
sudo ln -s /path/to/program /usr/bin
```

thanx, i did this, it works perfectly !

```
sudo ln -s /home/myusername/nicotine+-1.2.4.1/./nicotine /usr/bin/nicotine+
```

---

### Post by shunthemask on 2006-08-26
I found another thread with the same problem that I am having, so I moved my question over here:

[http://ubuntuforums.org/showthread.php?t=234089](http://ubuntuforums.org/showthread.php?t=234089)

---

### Post by INMCM on 2006-08-27
> **shunthemask said:**
> 
```
$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages

```



The packages shouldn't be broken, more likely your systems is screwed up. Open /etc/apt/source.list and post the contents.

---

### Post by shunthemask on 2006-08-27
INMCM, thanks, but I just got her fixed over here:
[http://www.ubuntuforums.org/showthread.php?p=1430613#post1430613](http://www.ubuntuforums.org/showthread.php?p=1430613#post1430613)

now I just have to figure out how to get the trayicon to work.

I ran the autogen.py, did the make install and copied the trayicon.so to the pynicotine directory, but when i run nicotine, I get the following error:
```
/pynicotine/trayicon.so: undefined symbol: trayicon_functions
Warning: Trayicon Python module not found.

```

Anybody have any ideas?

Thanks.

---

### Post by INMCM on 2006-08-27
> **shunthemask said:**
> INMCM, thanks, but I just got her fixed over here:
[http://www.ubuntuforums.org/showthread.php?p=1430613#post1430613](http://www.ubuntuforums.org/showthread.php?p=1430613#post1430613)

now I just have to figure out how to get the trayicon to work.

I ran the autogen.py, did the make install and copied the trayicon.so to the pynicotine directory, but when i run nicotine, I get the following error:
```
/pynicotine/trayicon.so: undefined symbol: trayicon_functions
Warning: Trayicon Python module not found.

```

Anybody have any ideas?

Thanks.

did you do SUDO make install?

---

### Post by shunthemask on 2006-08-27
> **INMCM said:**
> did you do SUDO make install?

yessir, I did:

```

stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ sudo ./autogen.py
Generating Makefile for python 2.4
Done.. Now run 'make install' as root
stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ sudo make install
install -d /usr/lib/python2.4/site-packages/pynicotine
install -m 755 trayicon.so /usr/lib/python2.4/site-packages/pynicotine
stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ sudo cp ./trayicon.so ../pynicotine/
stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ cd ..
stm@stm-desktop:/usr/share/nicotine+/src$ ls pynicotine/
ConfigParser.py   __init__.py    pynicotine.pyc    transfers.py
ConfigParser.pyc  __init__.pyc   slskmessages.py   transfers.pyc
config.py         mp3.py         slskmessages.pyc  trayicon.so
config.pyc        mp3.pyc        slskproto.py      utils.py
gtkgui            pynicotine.py  slskproto.pyc     utils.pyc
stm@stm-desktop:/usr/share/nicotine+/src$ ./nicotine
/usr/share/nicotine+/src/pynicotine/trayicon.so: undefined symbol: trayicon_functions
Warning: Trayicon Python module not found.

```

---

### Post by INMCM on 2006-08-28
> **shunthemask said:**
> yessir, I did:

```

stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ sudo ./autogen.py
Generating Makefile for python 2.4
Done.. Now run 'make install' as root
stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ sudo make install
install -d /usr/lib/python2.4/site-packages/pynicotine
install -m 755 trayicon.so /usr/lib/python2.4/site-packages/pynicotine
stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ sudo cp ./trayicon.so ../pynicotine/
stm@stm-desktop:/usr/share/nicotine+/src/trayicon$ cd ..
stm@stm-desktop:/usr/share/nicotine+/src$ ls pynicotine/
ConfigParser.py   __init__.py    pynicotine.pyc    transfers.py
ConfigParser.pyc  __init__.pyc   slskmessages.py   transfers.pyc
config.py         mp3.py         slskmessages.pyc  trayicon.so
config.pyc        mp3.pyc        slskproto.py      utils.py
gtkgui            pynicotine.py  slskproto.pyc     utils.pyc
stm@stm-desktop:/usr/share/nicotine+/src$ ./nicotine
/usr/share/nicotine+/src/pynicotine/trayicon.so: undefined symbol: trayicon_functions
Warning: Trayicon Python module not found.

```

Don't try installing nicotine anywhere where you need root access to write anything. It makes all the "sudo" stuff very complex. Extract the source to somewhere in your home directory and follow my instructions on the first page. You only need sudo on the make install part.

---

### Post by shunthemask on 2006-08-29
Sir, you are a genius!  Thanks much for the help.

---

### Post by p0pnfresh on 2006-08-31
Hi nice thread, I've been running nicotine 1.8 but found out about 2.4 so I downloaded the source and compiled it successfully, however when running "python ./nicotine" from the /bin folder it gives me the following error: 

Can not find Nicotine modules.
Perhaps they're installed in a directory which is not
in an interpreter's module search path.
(there could be a version mismatch between
what version of python was used to build the Nicotine
binary package and what you try to run Nicotine with.)

What could be the problem here? I've got only one version of python installed.

---

### Post by OffHand on 2006-09-01
> **p0pnfresh said:**
> Hi nice thread, I've been running nicotine 1.8 but found out about 2.4 so I downloaded the source and compiled it successfully, however when running "python ./nicotine" from the /bin folder it gives me the following error: 

Can not find Nicotine modules.
Perhaps they're installed in a directory which is not
in an interpreter's module search path.
(there could be a version mismatch between
what version of python was used to build the Nicotine
binary package and what you try to run Nicotine with.)

What could be the problem here? I've got only one version of python installed.

Try downloading the latest Nicotine+, navigate to the folder and run:

```
./nicotine
```

---

### Post by Mike_Bhoy on 2006-09-04
I downloaded Nicotine from the Package Manager... but I don't know where to find it..lol I got linux installed last night so I'm still trying to get used to it. Any ideas where it installed to?

---

### Post by SlugO on 2006-09-04
> **Mike_Bhoy said:**
> I downloaded Nicotine from the Package Manager... but I don't know where to find it..lol I got linux installed last night so I'm still trying to get used to it. Any ideas where it installed to?
Press ALT+F2 and type nicotine. You can also add it to program menu, just make a new entry there with Alacarte that has the command: nicotine.


Well I installed Ronin's deb but I'm getting the same errors as with the source:```
cannot import name trayicon
Warning: Trayicon Python module not found.
/home/janne/.themes/Clearlooks_Cairo-Serenity/gtk-2.0/gtkrc:48: error: unexpected identifier `scrollbar_color', expected character `}'
Traceback (most recent call last):
  File "/usr/bin/nicotine", line 149, in ?
    app = frame.MainApp(config)
  File "/usr/lib/python2.4/site-packages/pynicotine/gtkgui/frame.py", line 1383, in __init__
    self.frame = testwin(config)
  File "/usr/lib/python2.4/site-packages/pynicotine/gtkgui/frame.py", line 338, in __init__
    if self.np.config.needConfig():
  File "/usr/lib/python2.4/site-packages/pynicotine/config.py", line 86, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker", "players") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.4/UserDict.py", line 168, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.4/UserDict.py", line 101, in iteritems
    yield (k, self[k])
  File "/usr/lib/python2.4/shelve.py", line 119, in __getitem__
    value = Unpickler(f).load()
cPickle.UnpicklingError: could not find MARK

```What's the problem? I have Python and all the other dependencies.

---

### Post by H.E. Pennypacker on 2006-09-04
How do we go about asking the repository people to replace Nicotine with Nicotine+?

---

### Post by INMCM on 2006-09-07
> **H.E. Pennypacker said:**
> How do we go about asking the repository people to replace Nicotine with Nicotine+?

That's a very good question. I'd imagine [here]("https://wiki.ubuntu.com/MOTU/Packages/New?action=show&redirect=MOTUNewSoftware") would be a good place to look. But I also wonder how it works to get the old Nicotine out. It's easy to make the case that the old Nicotine 1.0.8 is busted, but hard to prove this new version (Nicotine+ 1.2.4.1 as of this writing) is stable and worth packaging. 47th_Ronin has been doing a bang up job making packages; perhapes those could be used after a little MotU love and extensive testing.

---

### Post by INMCM on 2006-09-07
Well, it looks like someone up there in MotU land likes us!!!!! Nicotine+ is in Edgy!!!!
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nicotine&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nicotine&searchon=names&subword=1&version=all&release=all)

[http://packages.ubuntu.com/edgy/net/nicotine](http://packages.ubuntu.com/edgy/net/nicotine)

I wonder why they didn't change the name to Nicotine+ and decpreceate Nicotine.

---

### Post by OffHand on 2006-09-18
daelstorm just released version 1.2.5.1

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

---

### Post by Zhen-Xlogic on 2006-09-19
Hello can i ask you somethink
I install Nicotine+ 1.2.4 via deb file and i cant find where is save her settings can any one help me?
BTW is very good program! :D

---

### Post by OffHand on 2006-09-19
> **Zhen-Xlogic said:**
> Hello can i ask you somethink
I install Nicotine+ 1.2.4 via deb file and i cant find where is save her settings can any one help me?
BTW is very good program! :D

It is stored in .nicotine in your /home

---

### Post by mrgnash on 2006-09-19
The link to the deb is broken.

And is the Soulseek network actually any good? Having to talk to people in order to get files seems a bit sucky :P

---

### Post by Zhen-Xlogic on 2006-09-20
> **mrgnash said:**
> The link to the deb is broken.

And is the Soulseek network actually any good? Having to talk to people in order to get files seems a bit sucky :P

The link for deb is broken its true the correct link is this: [Nicotine+ for Ubuntu Dapper Version: 1.2.4.1 deb]("http://www.osiris.codedchaos.com/osiris/request.php?23")

:cool:

---

### Post by bionnaki on 2006-09-20
> **mrgnash said:**
> The link to the deb is broken.

And is the Soulseek network actually any good? Having to talk to people in order to get files seems a bit sucky :P

nicotine uses the same network as soulseek. nicotine is just as good as the windows soulseek client, in my opinion. actually, you have more options with nicotine.

why do you have to "talk to peopl in order to get files"? you dont.

---

### Post by 47th_Ronin on 2006-09-21
Nicotine+ 1.2.5.1 (k)Ubuntu dapper package available for download

This time 2 packages:

[LINK REMOVED]nicotine+-1.2.5.1-x86-dapper[/URL]
Trayicon included and nothing is know about it's behavier on 64-bit systems.

[LINK REMOVED]nicotine+-1.2.5.1-noarch-dapper
Trayicon NOT included. Useable on 64-bit systems.

[SEE THIS POST](http://ubuntuforums.org/showpost.php?p=1557098&postcount=141)

[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] NOTE:
1.2.5.1 you can download at sf.net requires GTK 2.8, which means you have to update. 
The package as I made them is 1.2.5.1 SVN rev.87, where that problem is solved, no need for updating anything.

1.2.5.1 has a nice "Sound notification" feature. In order to use it you need vorbis-tools installed. I made the 1.2.5.1 package DEPENDING on vorbis-tools.. as you can always turn it off it you don't like it. (Settings/UI/Userinterface/Icon and Sound Themes)

---

### Post by spockrock on 2006-09-21
the 1.2.5.1 works great thanks.

---

### Post by raintheory on 2006-09-24
> **47th_Ronin said:**
> Nicotine+ 1.2.5.1 (k)Ubuntu dapper package available for download

This time 2 packages:

[nicotine+-1.2.5.1-x86-dapper]("http://www.osiris.codedchaos.com/osiris/download.php?view.32")
Trayicon included and nothing is know about it's behavier on 64-bit systems.

[nicotine+-1.2.5.1-noarch-dapper]("http://www.osiris.codedchaos.com/osiris/download.php?view.33")
Trayicon NOT included. Useable on 64-bit systems.



Can anyone post alternate links to those?

---

### Post by 47th_Ronin on 2006-09-24
> **raintheory said:**
> Can anyone post alternate links to those?

As always, second time my host is down :(

anyway... alternate link:

LINK REMOVED. See previous post.

---

### Post by raintheory on 2006-09-24
Great thanks!

---

### Post by 47th_Ronin on 2006-09-28
Nicotine+ has now an [official repository](http://nicotine-plus.org/wiki/NicotineOnDebian) @ [Nicotine+ Trac](http://www.nicotine-plus.org)

I want to thank you, who used my Ubuntu packages and gave feedback. It has been quite an experince and had lot's of joy helping you fixing issues.

My ubuntu packages will no longer be available for download. This, in case you have issues, is to prevent confusion about which packages you have installed.

A Special thank to:

[SIZE="3"]**INMCM** for starting this topic and putting up with me. You saved me loads of time. Thanks man! :)
**henriquemaia** for giving the first feedback after trying to install on 64-bit
**frank_b** for giving an exellent feedback.
??? for giving feedback to fix the icon issue.[/SIZE]

---

### Post by OffHand on 2006-09-29
> **47th_Ronin said:**
> Nicotine+ has now an [official repository](http://nicotine-plus.org/wiki/NicotineOnDebian) @ [Nicotine+ Trac](http://www.nicotine-plus.org)

I want to thank you, who used my Ubuntu packages and gave feedback. It has been quite an experince and had lot's of joy helping you fixing issues.

My ubuntu packages will no longer be available for download. This, in case you have issues, is to prevent confusion about which packages you have installed.

A Special thank to:

[SIZE="3"]**INMCM** for starting this topic and putting up with me. You saved me loads of time. Thanks man! :)
**henriquemaia** for giving the first feedback after trying to install on 64-bit
**frank_b** for giving an exellent feedback.
??? for giving feedback to fix the icon issue.[/SIZE]

More time for you to troll the nicotine room  :mrgreen:

---

### Post by sktfeelsdapper on 2006-10-10
Soooooooooooooooooooooo much easier than trying to compile it myself I might add.

Hurray for Trac!:-D

---

### Post by bionnaki on 2006-10-27
not sure if this has been covered in the thread yet or not.

but installing the trayicon works if you do this instead:

> 
sudo apt-get install build-essential python-dev python-gtk2-dev libgtk2.0-dev
cd nicotine+-1.2.4.1/trayicon
./autogen.py
sudo make install
cd ..
cp trayicon/trayicon.so pynicotine/


---

### Post by s6dalane on 2006-11-01
Is there a deb file for the version 1.2.6? If not, could anyone please build one?
Thanks in advance!

---

### Post by OffHand on 2006-11-01
> **s6dalane said:**
> Is there a deb file for the version 1.2.6? If not, could anyone please build one?
Thanks in advance!

1) Download Nicotine+ from here:

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

2) Extract it to your home folder

3) Open your terminal

4) ```
sudo apt-get install python-gtk2 python-mutagen python-psyco python-geoip
```

5) cd nicotine+-1.2.12 (or wherever you have extracted it)

6) ./nicotine

7) You can make a launcher using this path: /home/username/nicotine+ folder/nicotine.py

That's all there is to it.

---

### Post by knoxy5000 on 2006-11-07
When trying to install nicotine using terminal command "sudo apt-get install nicotine". It states this;

sudo apt-get install nicotine
Reading packaging lists...done
E: Couldn't find package nicotine

---

### Post by OffHand on 2006-11-07
> **knoxy5000 said:**
> When trying to install nicotine using terminal command "sudo apt-get install nicotine". It states this;

sudo apt-get install nicotine
Reading packaging lists...done
E: Couldn't find package nicotine

Install it in a few easy steps:

[http://www.ubuntuforums.org/showpost.php?p=1698178&postcount=146](http://www.ubuntuforums.org/showpost.php?p=1698178&postcount=146)

Also check the Nicotine+ Guide:

[http://nicotine-plus.sourceforge.net/NicotinePlusGuide/](http://nicotine-plus.sourceforge.net/NicotinePlusGuide/)

---

### Post by Tamacracker on 2006-11-11
> **OffHand said:**
> 1) Download Nicotine+ from here:

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

2) Extract it to your home folder

3) Open your terminal

4) ```
sudo apt-get install python-gtk2 python-pyvorbis python-psyco
```

5) cd nicotine+-1.2.6

6) ./nicotine

7) You can make a launcher using this path: /home/username/nicotine+ folder/nicotine

That's all there is to it. To get the tray icon working read the post above yours.

It's not letting me extract to my home folder, and I forget how to edit my options so that it'll give me access at all times.

I wanted to extract it onto my desktop and go from there... but whatever's clever...

---

### Post by OffHand on 2006-11-11
> **Tamacracker said:**
> It's not letting me extract to my home folder, and I forget how to edit my options so that it'll give me access at all times.

I wanted to extract it onto my desktop and go from there... but whatever's clever...

You should be able to extract it to your home folder. To your desktop too for that matter. What method did you use to extract it?

---

### Post by adas on 2006-11-12
> **s6dalane said:**
> Is there a deb file for the version 1.2.6? If not, could anyone please build one?
Thanks in advance!
see [http://www.nicotine-plus.org/wiki/NicotineOnDebian](http://www.nicotine-plus.org/wiki/NicotineOnDebian)

or add a new repository:
```
deb http://www.nicotine-plus.org/ubuntu edgy main
```

---

### Post by marx2k on 2007-01-21
Is anyone else experiencing a slow memory leak with Nicotiune 1.2.6+? 

It seems like if I download stuff, the memory will begin to leak, but Im not sure if that is what it is directly related to.

10 hours I started the program at 65M resident for memory, now it's at 81M

2 days ago it startet at 65M and 8 hoiurs later I had to restart it because it was at 351M!!

Im also using the Python Optimizer install that was recommended by Nicotine when you start the program (if you dont have it installed) 

I just downloaded SVN revision 170 and will see if that does the trick.. I hope so! :( 

(10:20PM ...)
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13638 marx2k    15   0  140m  66m  11m S  0.7  6.5   0:19.25 python             

Let's see what happens in a few hours...

---

### Post by marx2k on 2007-01-22
12:44 PM --
```

  PID   USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13638 marx2k    15   0  201m 120m  12m S  2.0 12.0   8:28.04 python             

```

The program seems to grow when I view someone else's shared files. but it doesnt shrink when I close their file list.

---

### Post by OffHand on 2007-01-22
> **marx2k said:**
> 12:44 PM --
```

  PID   USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13638 marx2k    15   0  201m 120m  12m S  2.0 12.0   8:28.04 python             

```

The program seems to grow when I view someone else's shared files. but it doesnt shrink when I close their file list.

The only way to let the developer of Nicotine+ know is to file a ticket:

[http://www.nicotine-plus.org/newticket](http://www.nicotine-plus.org/newticket)

But before you file it check the open tickets:

[http://www.nicotine-plus.org/report/1](http://www.nicotine-plus.org/report/1)

---

### Post by marx2k on 2007-01-22
Done and Done! 

I hope this gets fixed but it's like I am the only person who seems to be having this problem.

I checked in the Nicotine chat room on the slsk server, I checked the slsk forums, I checked in here, I googled it....

...I downloaded the latest SVN build, I recompiled PyGTK to ensure threading is used...

I'm not sure what else CAN be done... So yes, I did open up a ticket. Let's see what happens.

I wonder if it could be the Psyco package doing it...

---

### Post by OffHand on 2007-02-25
Version 1.2.7,  with many great improvements, has been released today!  :guitar: 

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

---

### Post by headphase on 2007-02-26
Where is the best place to install nicotine so I can add it on Alacarte?

---

### Post by OffHand on 2007-02-28
> **headphase said:**
> Where is the best place to install nicotine so I can add it on Alacarte?
I'm running it from my /home folder. You don't have to install it. You can add a manual menu entry in Alacarte. You can also make a launcher on your panel. Just point it to /home/username/nicotine+/nicotine (or wherever your N+ folder is)

[http://www.ubuntuforums.org/showpost.php?p=1698178&postcount=146](http://www.ubuntuforums.org/showpost.php?p=1698178&postcount=146)

---

### Post by OffHand on 2007-03-07
Yet another release with even more bug fixes and enhancements.

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

1.2.7.1

You can check the changes here:

[http://www.nicotine-plus.org/browser/trunk/nicotine%2B/doc/CHANGELOG](http://www.nicotine-plus.org/browser/trunk/nicotine%2B/doc/CHANGELOG)

:guitar:

---

### Post by czmiel on 2007-03-24
Unfortunately I couldn't have found the newest version of Nicotine for Ubuntu ;/
But it seems that Debian's deb works quite fine (apt displays warnings)
Just copy & run following lines:

[HTML]sudo apt-get remove nicotine
wget http://ftp.pl.debian.org/debian/pool/main/n/nicotine/nicotine_1.2.7.1+dfsg-1_i386.deb
sudo dpkg --ignore-depends=libfontconfig1,libpango1.0-0 -i nicotine_1.2.7.1+dfsg-1_i386.deb
rm nicotine_1.2.7.1+dfsg-1_i386.deb[/HTML]

**Added:**
Deb for Ubuntu is [here]("http://www.getdeb.net/download.php?release=542&fpos=0").
Thanks João!

---

### Post by zwervertje on 2007-03-29
Hey!

I just installed nicotine+ (1.2.7.1) on my pc, but it can't login...  i used soulseek before and tried that username and pw, but in the logbar, it says it is connected to server and logging in, and it stays that way
when i use another (non existent) username, still the same problem

any suggestions?
Tnx!

---

### Post by logoodnix on 2007-03-30
Howdy, I tried the above code (deb for both Debian and Ubuntu) and I got this error message;
*Error: Dependency is not satisfiable: libatk1.0-0*

I checked and libatk IS installed. Anyone know how to fix this or what the problem might be? 
I'm using dapper and am quite the newbie. 
thanx

---

### Post by czmiel on 2007-03-30
@zwervertje

What is showing in log scrollbox while connecting?
Maybe your ISP has blocked Soulseek ports...

@logoodnix

Nicotine package from GetDeb is prepared for Edgy - not for Dapper. Egdy has newer version of libatk1.0-0 library.

You can just ignore this dependency but it is not safe and apt may show annoying warnings while updating...
sudo dpkg -i --force-depends-version <name_of_package>.deb

Another idea is to ask people from GetDeb to prepare *.deb for Dapper.

Regards

---

### Post by zwervertje on 2007-03-31
> **czmiel said:**
> @zwervertje

What is showing in log scrollbox while connecting?
Maybe your ISP has blocked Soulseek ports...

Regards

nothing actually... but in the bar underneath, it states "connected to server server.slsknet.org:2240, logging in...

---

### Post by czmiel on 2007-03-31
> **zwervertje said:**
> nothing actually... but in the bar underneath, it states "connected to server server.slsknet.org:2240, logging in...

Did you try to install older version of Nicotine and/or create new slsk account?

Best idea to have your problem solved quickly is to describe it here: [http://www.nicotine-plus.org/newticket](http://www.nicotine-plus.org/newticket)
Before you create "New Ticket" browse existing problems: [http://www.nicotine-plus.org/report](http://www.nicotine-plus.org/report)

Regards

---

### Post by oobe on 2007-04-24
anyone installed 1.2.7.1 on the feisty final?

---

### Post by n2j3 on 2007-04-24
> **oobe said:**
> anyone installed 1.2.7.1 on the feisty final?

Just installed a few mins ago [from [http://www.getdeb.net/app.php?name=Nicotine%20Plus](http://www.getdeb.net/app.php?name=Nicotine%20Plus) ]
Everything's working fine.

---

### Post by oobe on 2007-04-24
> **n2j3 said:**
> Just installed a few mins ago [from [http://www.getdeb.net/app.php?name=Nicotine%20Plus](http://www.getdeb.net/app.php?name=Nicotine%20Plus) ]
Everything's working fine.

thanks! :-) , working also

---

### Post by stokedfish on 2007-04-25
I much prefer museek...

[http://museek-plus.org/](http://museek-plus.org/)

You guys should give it a try...it's fantastic!   :)

---

### Post by stylofone on 2007-06-02
I love the soulseek network! When you're looking for some rare gem, you will find it there. Soulseek users with their marvellously diverse, strange, rare, adventurous tastes should be on the cover of Time Magazine! It is all about the passion, the love, the obsession for music.  You are all stars and I salute you.

I've only switched to Ubuntu recently, and while there have been annoyances, the healthy state of P2P apps has not been one of them. Nicotine+ rocks! Amule has been flawless, and Ktorrent has been ...pretty good. Vive la Revolution!

---

### Post by OffHand on 2007-06-02
Nicotine+ 1.2.8 has been released and is ready for download here: [http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

:guitar::guitar::guitar:

New features: [http://www.nicotine-plus.org/wiki/NicotinePlusNewFeatures](http://www.nicotine-plus.org/wiki/NicotinePlusNewFeatures)

---

### Post by OffHand on 2007-09-22
Version 1.2.9 has been released: [http://www.nicotine-plus.org/wiki/NicotinePlusNewFeatures](http://www.nicotine-plus.org/wiki/NicotinePlusNewFeatures)

Download from: [http://www.nicotine-plus.org](http://www.nicotine-plus.org)

---

### Post by loell on 2007-09-22
thanks for the heads up on the new developer :)

---

### Post by OffHand on 2007-09-22
> **loell said:**
> thanks for the heads up on the new developer :)

Well - "new" - daelstorm has been the developer of N+ for over 2 years... maybe even more  ;) 
Hyriand quit developing at version 1.0.9 iirc.

---

### Post by loell on 2007-09-22
> **Raeligh said:**
>  The main developer now is daelstorm.:)

so i guess this is not correct?

---

### Post by OffHand on 2007-09-22
> **loell said:**
> so i guess this is not correct?

It's correct. It's just that I wouldn't consider over 2 years "new", so it isn't news either  ;)

---

### Post by loell on 2007-09-22
> **OffHand said:**
> It's correct. It's just that I wouldn't consider over 2 years "new", so it isn't news either  ;)

it seems that you know the nicotine development well..

so.. care to sprinkle a development news? since you are nitpicking on what i said over there :)

which was my impression on what raliegh said .

---

### Post by OffHand on 2007-09-22
> **loell said:**
> it seems that you know the nicotine development well..

so.. care to sprinkle a development news? since you are nitpicking on what i said over there :)

which was my impression on what raliegh said .

I do testing and come up with new ideas for N+ but I do not code myself.

The news was that a new version (1.2.9) has  been released.

[http://ubuntuforums.org/showpost.php?p=3407186&postcount=172](http://ubuntuforums.org/showpost.php?p=3407186&postcount=172)

---

### Post by loell on 2007-09-22
ohh, the changes are quite huge!!!  :)

---

### Post by gmaniac on 2007-10-27
I like this program and I'm using version 1.2.8 and because it feels kind of slow
i was hoping to test this new version.
Is there an ubuntu package of version 1.2.9 anywhere?
Or how soon we will be getting this in the repositories?
Thnx

---

### Post by OffHand on 2007-10-27
> **gmaniac said:**
> I like this program and I'm using version 1.2.8 and because it feels kind of slow
i was hoping to test this new version.
Is there an ubuntu package of version 1.2.9 anywhere?
Or how soon we will be getting this in the repositories?
Thnx

[http://ubuntuforums.org/showpost.php?p=1698178&postcount=146](http://ubuntuforums.org/showpost.php?p=1698178&postcount=146)

1.2.9 probably hits the repositories in the new release....

---

### Post by gmaniac on 2007-10-28
I know it isn't difficult to run this/any program and even like the idea of compiling from source sometimes, but i like more the feature of auto updating whenever there is a new release automatically. 
I don't know how anyone can live without it ;).
I was hoping for an unofficial repository.
Thnx anyway

---

### Post by OffHand on 2007-10-28
> **gmaniac said:**
> I know it isn't difficult to run this/any program and even like the idea of compiling from source sometimes, but i like more the feature of auto updating whenever there is a new release automatically. 
I don't know how anyone can live without it ;).
I was hoping for an unofficial repository.
Thnx anyway

You do not actually compile it... you just run it from the source. There is no unofficial repository I know of. I couldn't live without automatic updating although I do not consider it a big problem to do a few applications manually. Either way.... it's up to you.

---

### Post by rolheika on 2007-10-30
I have a question about using nicotine - I have selected a few songs to download, but under the status it has been showing "getting status" for a long time, showing no sign of downloading (the percentage shows 0% for them all).  This is unusual as I have used SoulSeek on Windows for a long time, and usually things get started.  There doesn't seem to be any problem with my server connection, what else could be the problem?  Or is it simply a bug?

NEVER MIND - IT SEEMS TO HAVE FIXED ITSELF

---

### Post by Kanji_Man on 2007-11-18
The gutsy repositories still only have 1.2.8 packages and the latest avalable deb packages according to the [official site]("http://nicotine-plus.org/wiki/NicotineOnDebian") are also still at 1.2.8. However there are many new features in 1.2.9 that I would like to use without breaking the apt upgrade path. So this is what I do:

- Search google for "nicotine 1.2.9 rpm x86_64' (I use 64bit gutsy)
- Download the RPM package
- Convert the RPM to DEB with alien:
```
sudo alien -k nicotine-1.2.9-1plf2008.0.x86_64.rpm
```

I then have a nice deb package that I can install and if a higher version ever rolls out on the ubuntu repositories it should upgrade as normal.

Hope this helps someone.

---

### Post by sojusnik on 2007-12-12
Hi,

Is there somebody who has "ported" nicotine+ 1.2.9. to a .deb File for Ubuntu Gutsy 32bit?

---

### Post by OffHand on 2007-12-12
> **sojusnik said:**
> Hi,

Is there somebody who has "ported" nicotine+ 1.2.9. to a .deb File for Ubuntu Gutsy 32bit?

You really don't need a deb file. Recommended method is to just run it.

[http://ubuntuforums.org/showpost.php?p=1698178&postcount=146](http://ubuntuforums.org/showpost.php?p=1698178&postcount=146)

---

### Post by sojusnik on 2007-12-12
Hi,

Thank you for your advice.

What do I have to do when I want to install nicotine+ to another place, for example:

/usr/nicotine+-1.2.9 _and not_

/home/username/nicotine+-1.2.9

What about ./nicotine then, will it be created automatically in my home directory?

Thx

---

### Post by OffHand on 2007-12-12
> **sojusnik said:**
> Hi,

Thank you for your advice.

What do I have to do when I want to install nicotine+ to another place, for example:

/usr/nicotine+-1.2.9 _and not_

/home/username/nicotine+-1.2.9

What about ./nicotine then, will it be created automatically in my home directory?

Thx
./nicotine will launch it. you do not need to install or compile it in order to use it. It's made in python.

---

### Post by sojusnik on 2007-12-12
Got it :)

---

### Post by sojusnik on 2007-12-13
Hi,

I have extracted it to

/root/nicotine+-1.2.9

and made a shortcut

/root/nicotine+-1.2.9/nicotine

Everything seems to work well, I've granted via nautilus all rights to this folder, because I'm not "root" at default, so file changes can be made, but discovered that some files are read-only. They all are in this folder:

/root/nicotine+-1.2.9/pynicotine

Here is a screenshot of the whole folder: [http://www.box.net/shared/ntpxt18777](http://www.box.net/shared/ntpxt18777)

Is this normal?

Thx for helping.

---

### Post by OffHand on 2007-12-14
There should not be any locked files in the N+ folder. And why run it from root? Do you have a multi user system?

You might have forgotten to give the rights recursively?

---

### Post by sojusnik on 2007-12-14
Hi,

I copied it there, because I don't want to have programs in my 

/home 

folder.

> You might have forgotten to give the rights recursively?

How can I do this?

---

### Post by OffHand on 2007-12-14
> **sojusnik said:**
> Hi,

I copied it there, because I don't want to have programs in my 

/home 

folder.



How can I do this?

Home still is the best place bro if you have a single user machine. I run a few applications from source in my home folder. They are subfolders of a folder named Applications so home will not be messy. but if you want to keep it in root  open a root nautilus session with gksudo nautilus, go to the folder, right-click and select propertis. Then check the screenshot.

---

### Post by sojusnik on 2007-12-14
Thank you very much, it works now like a charm!

---

### Post by sojusnik on 2007-12-16
Hi,

After some time of using nicotne+, sporadically the program crashs.
I've launched it via console to log the event:
> xxxx@xxxx:~$ /root/nicotine+-1.2.9/nicotine
Nicotine supports a country code blocker but that
        requires a (GPL'ed) library called GeoIP. You can find it here:
        C library:       [http://www.maxmind.com/app/c](http://www.maxmind.com/app/c)
        Python bindings: [http://www.maxmind.com/app/python](http://www.maxmind.com/app/python)
        (the python bindings require the C library)

Warning: unknown object type <type 'bool'> in message pynicotine.slskmessages.UserInfoReply
/root/nicotine+-1.2.9/pynicotine/gtkgui/frame.py:2716: PangoWarning: Invalid UTF-8 string passed to pango_layout_set_text()
  gtk.main()
Segmentation fault (core dumped)


How can I solve my dilemma?

Thx in advance!

---

### Post by OffHand on 2007-12-16
> **sojusnik said:**
> Hi,

After some time of using nicotne+, sporadically the program crashs.
I've launched it via console to log the event:


How can I solve my dilemma?

Thx in advance!

Search for excisting bug reports: [http://www.nicotine-plus.org/report](http://www.nicotine-plus.org/report)

If you can't find a similar bug report create a new one: [http://www.nicotine-plus.org/newticket](http://www.nicotine-plus.org/newticket)

---

### Post by Kanji_Man on 2008-02-05
For those who are interested, nicotine+ 1.2.9 packages are available over on deiban sid (unstable) [here]("http://packages.debian.org/sid/nicotine"). Although I did have to upgrade the package "python-support" beforehand (available at that same link) this version runs a bit better than previous builds I had converted from rpm with alien.

EDIT: 1.2.9 is also available in the Hardy repository [here]("http://packages.ubuntu.com/hardy/net/nicotine").

---

### Post by ahorriblemess on 2008-02-29
Don't know if this belongs here... but I've been trying to find a solution to this problem... I can't browse users files. Is it because he's on windows using Soulseek and I'm on ubuntu? Or am I just not setting something correctly? I can chat with him... just can't get his files. I've tried it on other users at random and it never works.

---

### Post by OffHand on 2008-03-01
> **ahorriblemess said:**
> Don't know if this belongs here... but I've been trying to find a solution to this problem... I can't browse users files. Is it because he's on windows using Soulseek and I'm on ubuntu? Or am I just not setting something correctly? I can chat with him... just can't get his files. I've tried it on other users at random and it never works.

You will probably have to open a port in your firewall.

Check if your port is open (use link). 

[http://daelstorm.thegraveyard.org/scripts/slsktest.php](http://daelstorm.thegraveyard.org/scripts/slsktest.php)

---

### Post by atombomb on 2008-03-14
I'm trying to install Nicotine+ but I am absolutely illiterate in Linux.  I have no idea what the codes are, where to put them, and what to do with them.  They're just a bunch letters and characters to me. lol.  Can anyone kindly give me step-by-step instructions on how to install and run Nicotine in my notebook? :)

---

### Post by OffHand on 2008-03-14
> **atombomb said:**
> I'm trying to install Nicotine+ but I am absolutely illiterate in Linux.  I have no idea what the codes are, where to put them, and what to do with them.  They're just a bunch letters and characters to me. lol.  Can anyone kindly give me step-by-step instructions on how to install and run Nicotine in my notebook? :)

[http://ubuntuforums.org/showpost.php?p=1698178&postcount=146](http://ubuntuforums.org/showpost.php?p=1698178&postcount=146)

---

### Post by Capt_Zaphod on 2008-08-13
Thank you!

---

### Post by OffHand on 2008-10-31
N+ is under active development again. The new dev is Quinox. You can check out the svn version for the latest bug fixes and enhancements.

[http://www.nicotine-plus.org/wiki/NicotineFromSubversion](http://www.nicotine-plus.org/wiki/NicotineFromSubversion)

---

### Post by hbbk on 2009-12-20
hi

I'm using nicotine+ 1.2.14. Just would like to know how to do to save banned users list between sessions ? the banned users list seems to be reset between nicotine sesssions, not saved in any file

thanks in advance

---

### Post by OffHand on 2009-12-27
> **hbbk said:**
> hi

I'm using nicotine+ 1.2.14. Just would like to know how to do to save banned users list between sessions ? the banned users list seems to be reset between nicotine sesssions, not saved in any file

thanks in advance

This is a bug. Please open a new ticket at [www.nicotine-plus.org](www.nicotine-plus.org) and we will look into it. 

Cheers!

---

### Post by Lockheed on 2010-02-21
I start Nicotine+ with **nicotine -s** to minimize it at startup.

However, it still opens a fullscreen window for few seconds before it is being minimized, while it starts. Is there any way to prevent it?

---

