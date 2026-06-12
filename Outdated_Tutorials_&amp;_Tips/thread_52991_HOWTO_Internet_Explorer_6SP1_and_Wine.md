---
title: "HOWTO: Internet Explorer 6SP1 and Wine"
date: 2005-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Curufir on 2005-07-29
A large number of folks in the web browsing world use this browser and strangely enough 'Make them use a standards compliant browser' doesn't seem to be a valid argument for not supporting it when designing websites  :mad: . So it's handy to have a version of IE lying around to test pages against if you do any web design work. The problem is that IE6 **REALLY** does not like the version of Wine in CVS or the repositories (I may just have got a bad version of Wine from CVS).

Open up a terminal Applications->System Tools->Terminal

We're going to handle everything in a temporary directory, so make one.

```
cd ~/
mkdir temp
cd temp
```

Download the debs for the old version of Wine that we'll be using.

```
wget http://unc.dl.sourceforge.net/sourceforge/adambots-live/libwine_0.0.20041019-1.3_i386.deb
wget http://unc.dl.sourceforge.net/sourceforge/adambots-live/libwine-alsa_0.0.20041019-1.3_i386.deb
wget http://unc.dl.sourceforge.net/sourceforge/adambots-live/wine-utils_0.0.20041019-1.3_i386.deb
wget http://unc.dl.sourceforge.net/sourceforge/adambots-live/wine_0.0.20041019-1.3_i386.deb
```

Download the winetools utility.

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz
```

Install the Wine debs we just downloaded.

```
sudo dpkg -i libwine_0.0.20041019-1.3_i386.deb
sudo dpkg -i wine_0.0.20041019-1.3_i386.deb
sudo dpkg -i libwine-alsa_0.0.20041019-1.3_i386.deb
sudo dpkg -i wine-utils_0.0.20041019-1.3_i386.deb
```

Synaptic and the Ubuntu updater will continuously complain about there being a new version of Wine available. We stop this happening by adding some rules to the end of the /etc/apt/preferences file.

```
cp /etc/apt/preferences ./preferences
cat >> preferences << "EOF"

Package: libwine
Pin: release o=now
Pin-Priority: 990

Package: libwine-alsa
Pin: release o=now
Pin-Priority: 990

Package: wine-utils
Pin: release o=now
Pin-Priority: 990

Package: wine
Pin: release o=now
Pin-Priority: 990

EOF

sudo cp /etc/apt/preferences /etc/apt/preferences.bak
sudo mv ./preferences /etc/apt/preferences
```

Decompress and install Winetools.

```
tar xvzf winetools-212jo.tar.gz
cd winetools-212jo
sudo sh ./install
```

Winetools uses the environment variable SFMIRROR to determine the sourceforge mirror from which it downloads various files. The default mirror is down, or otherwise unavailable, so we set it to one that works (You will need to do this every time you want to use wt2. If that annoys you then alter ~/.bashrc accordingly).

```
export SFMIRROR="http://kent.dl.sourceforge.net/sourceforge/"
```

Run the Winetools utility.

```
wt2
```

You will almost immediately get a dialogue from Wine saying this:

> You have started Wine, but we cannot find a Wine
configuration file.

This is normal if you have never run Wine before.
If this is the case, select the 'Configure Wine'
option, below, to create a configuration file.

**DO NOT CHOOSE THE CONFIGURE OPTION**. Winetools will do the configuration for us, so just press 'Proceed'.

*As you continue Wine will start showing you dialogue boxes. Some are indicating an application has been started (Dismiss these, or use the disable option to turn them off for good). Some indicate an application has exited badly "Wine has exited with a failure status of 1." (Hit Okay and ignore them).*

Choose Base Setup from the Winetools menu. Work your through the options on the list from top to bottom (If the same option is available in multiple languages then choose one language only).

*Wine experiences a huge error once Internet Explorer has finished installing. This brings up the wine debugger in the terminal (The prompt changes to wine-dbg>). Type "quit" to get rid of the debugger and pretend it didn't happen.*

You may want to install other software using the Winetools utility (I advise installing at least the fonts).

Winetools creates a ~/bin directory containing small scripts to start the various applications (E.g. ~/bin/ie6 will start IE6). This directory doesn't appear in a normal Hoary PATH, so you have to type in ~/bin/<script_name> every time. If you would prefer to just type in <script_name> then alter ~/.bashrc to add ~/bin to your PATH.

```
cat >> ~/.bashrc << "EOF"
# Prepend ~/bin to PATH if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
EOF
```

Open a new terminal and type 'ie6' to begin the CSS debugging nightmare  :grin: .

NOTE: The ie4linux script ([http://www.tatanka.com.br/ies4linux/](http://www.tatanka.com.br/ies4linux/)) will provide you with ie5, ie5.5 and ie6 separate from your default Wine drive. It is reported to work with current CVS, so that script may be more beneficial to some than this howto.

** Edited for clarity and to get away from the 90% debacle

---

### Post by Wandering Wombat on 2005-07-30
I havent tried this yet but you are right about checking your website with IE, caught myself out today lol. With Firefox the site was perfect and I was quite proud of myself, I had no reason to be lmao. I checked it with IE and it was all over the place hehehe. Will have to try this out cheers!

---

### Post by GavinX on 2005-07-30
[QUOTE=Curufir]90% of folks in the web browsing world use this browser[/QUOTE]
Which web-browser? 90% are using Internet Explorer for web-drowsing? You're serious? You have not done your homework on Firefox. SHame on you.  [-X

---

### Post by kevcart3 on 2005-07-30
Also, if you are already have wine, in my case it was the latest CVS build, and are having trouble getting IE to install from wt2 you need to try IEs 4 Linux, found [here](http://www.tatanka.com.br/ies4linux/)

---

### Post by Curufir on 2005-07-31
[QUOTE=GavinX]Which web-browser? 90% are using Internet Explorer for web-drowsing? You're serious? You have not done your homework on Firefox. SHame on you.  [-X[/QUOTE]

Since Google stopped posting browser stats it's difficult to get a good global picture. What I can say for sure is that over 90% of the people using the non-technical site I'm writing for are using IE. I imagine that scenario is pretty widespread amongst non-technical sites. Just because <Insert computer geek website of choice> has a lower percentage of IE users doesn't mean grandma has decided to quit using IE and start browsing with lynx  ;-) .

It's entirely possible I grabbed a bad version of Wine from CVS. I'd suggest people try the Wine CVS HOWTO first and think of the older Wine debs I've linked to as a failsafe version.

---

### Post by 8FootSativa on 2005-07-31
[QUOTE=GavinX]Which web-browser? 90% are using Internet Explorer for web-drowsing? You're serious? You have not done your homework on Firefox. SHame on you.  [-X[/QUOTE]

It's you who hasn't done your homework. Well over 90% of websurfers do, in fact, use IE.

---

### Post by Sam on 2005-07-31
[QUOTE=8FootSativa]It's you who hasn't done your homework. Well over 90% of websurfers do, in fact, use IE.[/QUOTE]
It depends of the country. In Europe, Firefox is widely used than in America.

[Stats on the rise again, Firefox still unstoppable in Europe!](http://www.spreadfirefox.com/?q=node/view/15888)

---

### Post by m0biu5 on 2005-07-31
And of course, there is always this: [http://www.w3junkies.com/toocool](http://www.w3junkies.com/toocool)  :razz:

---

### Post by GavinX on 2005-08-01
[QUOTE=8FootSativa]It's you who hasn't done your homework. Well over 90% of websurfers do, in fact, use IE.[/QUOTE]
I don't want this post to turn into flame, however, I've got to defend my honour (yah, where I'm from we conform to British English). IE is NOT used by 90% of web-surfers. Of couse, I'm not making the cae that Mozilla (of whatever flavour) is more widely used. But 90% is an arbitrary and I know exaggerated figure. I could pull stats to show that 90% is not correct. As Sam said, it depends on the country and North America does not have a greater population than Europe combined. Also, one needs to check out Asia, Latin America and the Caribbean where Mozilla usage is quite high. Please, expand the horizons when having discussions like these.

As an example check this page [http://webdesign.about.com/gi/dynamic/offsite.htm?site=http%3A%2F%2Fwww.cen.uiuc.edu%2Fbstats%2Flatest.html](http://webdesign.about.com/gi/dynamic/offsite.htm?site=http%3A%2F%2Fwww.cen.uiuc.edu%2Fbstats%2Flatest.html)

If you are making reference to stats like these [http://www.onestat.com/html/aboutus_pressbox23.html](http://www.onestat.com/html/aboutus_pressbox23.html) I think you will fully realize that this article was published in July of 2003. We are now in August 2005! Two years removed from those stats and things have really changed since then.

[Please, don't look at the number of posts that I have in these forums, that's misleading. I've been using Linux since 1999 so by now I think I have an idea of what's going on. Whenever I post, I've done the requisite homework.]

---

### Post by Curufir on 2005-08-01
90% is arbitrary and I suppose I should have qualified it as 'from personal experience'. However this isn't an article on browser usage, and I haven't set myself up as an authority on browser usage. I will say however that, because of the impossibility of actually getting a decent figure for global browser usage, my arbitrary 90% guess is **just** as valid as whatever guess anyone else comes up with (Even if they have convincing looking stats to back it up). Individual websites can, and should, track browser usage, but those stats are going to be specific to content and userbase.

[http://webdesign.about.com/gi/dynamic/offsite.htm?site=http%3A%2F%2Fwww.cen.uiuc.edu%2Fbstats%2Flatest.html](http://webdesign.about.com/gi/dynamic/offsite.htm?site=http%3A%2F%2Fwww.cen.uiuc.edu%2Fbstats%2Flatest.html)

Pretty stats, but fairly meaningless for the same reasons Google's stats had become meaningless.

---

### Post by abmcr on 2005-08-01
[QUOTE=Curufir]
Fix this by using 'export SFMIRROR="http://kent.dl.sourceforge.net/sourceforge/"' on the command line (This one works, use one geographically closer if it doesn't).

[/QUOTE]

I have installed the packages, but i have not understand where to do the fixing

[QUOTE=Curufir]
Now type 'wt2' on the command line.

Accept all the defaults and then run through each step in the 'Base Setup' menu (English or German, choose one and stick to it). This will leave you with IE6 installed. Exit the Winetools application.

Winetools installs a nice link to start IE6 in ~/bin. This is handy, but ~/bin isn't in a default Ubuntu path.

To fix this edit ~/.bashrc and add this to the end of the file.

# Prepend ~/bin to PATH if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
[/QUOTE]
At this point the wine configuration suggest the installation of winsetupdpkg (or similar..). I have installed it, but, after, i have not found the  ~/bin directory with the link. What it is my error? Thank you and excuse me for my english language. Ciao

---

### Post by slade_slater on 2005-08-01
I understand what you mean--although IE is NOT standards-compliant, it undisputedly has a significant (in fact, the majority) of browser share today.  At one point a claim was made that it had about 90% of the share.  Either way the spirit of the how-to is effectively communicated in that IE has most users deadlocked.  And sometimes you have to write pages in order to be IE-friendly...  Thanks for the excellent how-to!  As soon as I get my Ubuntu back up and running (I'm a distro wh0re and ashamed to say I tried some different distributions--but, as always I'm back to Ubuntu) I'll give it a try!

---

### Post by Curufir on 2005-08-01
[QUOTE=abmcr]I have installed the packages, but i have not understand where to do the fixing[/QUOTE]

winetools (Which is the utility that supplies the wt2 command) uses the environment variable SFMIRROR when determining which sourceforge mirror to download some files from. If the variable isn't present it tries to use a default site which is not currently working.

export SFMIRROR="http://kent.dl.sourceforge.net/sourceforge/"

Will set the SFMIRROR environment variable for a specific terminal session only, so use wt2 from the same terminal you set the variable in.

That mirror is currently working, so wt2 will be able to download the files it needs.

> 
At this point the wine configuration suggest the installation of winsetupdpkg (or similar..). I have installed it, but, after, i have not found the  ~/bin directory with the link. What it is my error? Thank you and excuse me for my english language. Ciao

Shared blame on the error. I never said that you should let Winetools do the configuration instead of Wine. I've updated the HOWTO accordingly.

---

### Post by Octane on 2005-08-08
Sorry to interfere your little argument but lets get back to the thread shall we... any way, your howto doesnt do anything to solve the winetools problem of installing IE6.

---

### Post by vkkim on 2005-08-08
[QUOTE=kevcart3]Also, if you are already have wine, in my case it was the latest CVS build, and are having trouble getting IE to install from wt2 you need to try IEs 4 Linux, found [here](http://www.tatanka.com.br/ies4linux/)[/QUOTE]

this worked great! (while the method outlined by this howto utterly failed... :neutral:

---

### Post by franziski on 2005-08-15
I followed the above procedure but winetools still doesn't work for me

The menu appears, then I click on "Base setup" item but happens nothing and appear again the menu.

Where I'm mistaking?

Thanks

---

### Post by franziski on 2005-08-15
[QUOTE=franziski]I followed the above procedure but winetools still doesn't work for me

The menu appears, then I click on "Base setup" item but happens nothing and appear again the menu.

Where I'm mistaking?

Thanks[/QUOTE]


Fixed! thanks to mr.google
[SIZE=3]
winetools doesn't work when gtk-engines-pixmap isn't installed ![/SIZE]

---

### Post by qferret on 2005-10-01
After tinkering with wine-tools for several hours & still not getting wget to work on any of the SF mirrors that I know of, I tried the sidenet utility. Worked flawlessly 1st time through.

---

### Post by aysiu on 2005-10-20
[QUOTE=kevcart3]Also, if you are already have wine, in my case it was the latest CVS build, and are having trouble getting IE to install from wt2 you need to try IEs 4 Linux, found [here](http://www.tatanka.com.br/ies4linux/)[/QUOTE] Whoa! IEs 4 Linux is awesome! You just run the script, and it's all good. One thing that wasn't mentioned, which I had to poke around a bit for, is that the script installs into a /bin folder of whatever user installs it. In my case, I installed it as sudo, so it ended up being in /root/bin/ie6. I had to create a symbolic link from /root/bin/ie6 to /usr/bin/ to get it to run as a regular program.

Awesome, though--awesome. Thanks for the link!

---

### Post by Rubin-Rah on 2006-02-12
Hi,
I'm trying to get startet ie6 on my Ubuntu 5.10, because i'm an web-developer and i need to test it with this crappy browser....

so i was trying several howtos from the net and all of them, as well like with this howto, has an error:

when i start winetools i get in the console a list of Gtk-WARNINGs like this:
```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so",
```

after that Winetools starts but i cant enter any issue like BaseSetup, even About doesnt work, it seems like entering but then it shows the main menu again.
please help me... google hasnt helped me

but I'm stupid. sorry you already gave me the answer. probably i will help somebody who is searching for this error message:
you just have to install gtk-engines-pixmap (sudo apt-get install gtk-engines-pixmap)

---

