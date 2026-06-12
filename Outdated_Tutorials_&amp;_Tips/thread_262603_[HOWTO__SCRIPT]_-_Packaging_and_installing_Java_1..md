---
title: "[HOWTO / SCRIPT] - Packaging and installing Java 1.6.0 (Mustang) JRE in few moves!"
date: 2006-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Treviño on 2006-09-21
Hello, while Java 1.5 has been added to our repositories some time ago, a new Java release is coming... 
In fact, **Java 1.6.0** (codenamed *mustang*) is actually in *Release Candidate* state but it is just really stable and really much more performing (using, from my point of view, less memory!).

[SIZE=4]_**Features**_[/SIZE]
This is a [summarized list of the **new features**]("http://www.javalobby.org/java/forums/t72230.html"); first of all for linux users I've to underline the support for *full-screen mode*, then for all the support for ***_native_ ****GTK graphics widgets*** (i.e. your gtk theme from your gtkrc conf file!), and ***subpixel rendering*** (finally!) :D
I want explain better this two &#8220;main&#8221; graphical features, showing what has really changed from the user interface point of view (anyway [here]("http://www.ffnn.nl/pages/articles/java/java-2-se-6.0-aesthetics-preview.php") you can find more informations on all others new aesthetics features).

**Gtk graphic theme support**
[[IMG]http://img245.imageshack.us/img245/4642/screenshot39rc1.th.png[/IMG]]("http://img245.imageshack.us/img245/4642/screenshot39rc1.png")
Above :rolleyes: you can see some kind of java test widgets rendered using &#8220;your&#8221; linux (true) gtk theme (the one in the shot, is [QtCurve]("http://www.kde-look.org/content/show.php?content=40492") the Qt/Gtk theme/engine that I use). You can see another example in [this screenshot]("http://img356.imageshack.us/img356/6994/mercurymustangku5.jpg") showing Mercury rendered using the Ubuntu Human Quicksilver gtk theme!!
*Finally Java apps could look like your standard applications! :)*

Anyway this feature isn't enabled by default (newer versions of make-jpkg-mustang will support it), you must define this environment variable:
```
export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"
```[SIZE=1]Btw some applications like Mercury have a built-in theme selector; in those cases, you should select the "Gtk theme".[/SIZE]

**Subpixel Rendering**
[[IMG]http://img153.imageshack.us/img153/4571/screenshot11ky2.th.png[/IMG]]("http://img153.imageshack.us/img153/4571/screenshot11ky2.png")
Above :rolleyes: you can see how it looks good the new font rendering (especially for LCD screens), the three windows shows (from left to right):
1) Java 1.5 (standard &#8220;old&#8221; java font rendering)
2) Java 1.5 (using the "-Dswing.aatext=true" paramter that activate a semi-antialiased font rendering)
3) Java 1.6 (using the built-in new subpixel rendering)

Java 1.6 reads your gnome (and KDE, using a package made with make-jpkg-mustang >=0.7.5) font antialiasing/rendering settings and apply it to its applications too; as you can see in the screenshot (3) the result is great (there are, btw, more settings so the screenshot shows only a case).[I]
Finally Java apps could have a smoother look in your LCD screen! :)[/I]

You can find more informations on Mustang's subpixel rendering [here]("http://today.java.net/pub/a/today/2005/07/26/lcdtext.html").

[SIZE=4]_**Installation**_[/SIZE]
Anyway after this little explaination, _***let's install and package it***_...
Well... Considering that the java-package's [FONT=Courier New]make-jpkg[/FONT] doesn't work with latest versions of the binary, I've decided to create a my own script that in only a move:
- Downloads the latest jdk java package (working both for i386 and amd64)
- Extracts it, removing the unnecessary JDK stuff
- Creates a debian _JRE_ package to be installed in your system
- The package installs and sets as default (using [FONT=Courier New]update-alternatives[/FONT]) all the Jre's binaries and the firefox java plugin
- KDE kcontrol font rendering settings supported ([read here]("http://ubuntuforums.org/showpost.php?p=1558000&postcount=21"))

To install this script, you've only to install a package from [**My Repository**]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/").
Add it to your [FONT=Courier New]sources.list[/FONT] (there's also other cool stuff):
```
deb http://download.tuxfamily.org/3v1deb/ 3v1n0
```Then
```
sudo apt-get install make-jpkg-mustang
```Anyway, if you don't want to add the repository, you can simply install the .deb downloading it from [this page]("http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/") [SIZE=1](look for the *make-jpkg-mustang* deb!)[/SIZE].

To do everything you need run (as user, please!)
```
make-jpkg-mustang
```The script will do all the work, btw you've to _*agree with the Sun Java License*_.

You can also generate the debian package from another mustang's downloaded bin file by running

```
make-jpkg-mustang /your_dir/your_sun_jdk_binary_file.bin
```After that the downloading/converting process has ended, you're asked for installing the just made package; if you refuse, you've to manually install the created package saved where the script says.

That's All!:KS

**Notes:**[INDENT]You don't need to remove the standard sun-java5-* packages, simply if you want to re-use the old version use the command [FONT=Courier New]sudo update-alternatives --config java[/FONT] to set your favourite java virtual machine [SIZE=1](or simply run the standard jvm by [FONT=Courier New]/usr/lib/jvm/java-1.5.0-sun/jre/bin/java[/FONT])[/SIZE]!

Actually the make-jpkg-mustang package build only the sun-java6-jre package, anyway, I'm planning to integrate it to create also the other packages (jdk, src, plugin, demo...): let me know if you're intrested in!

This should work in amd64 systems too, btw it's not tested there, so, please, let me know if there's something of wrong!

KDE font rendering settings are now read by an "home-made" script... To use subpixel rendering, use kcontrol standard font settings.

KDE/Qt theme Java support isn't just now in a Work in Progress status (read/try more [here]("http://kdelaf.freeasinspeech.org/")), anyway you can use the Gtk-Qt engine to make your gtk (and so, java) applications look (quite) like your KDE's ones.
Otherwise use themes like [QtCurve]("http://www.kde-look.org/content/show.php?content=40492") [SIZE=1](present in my repository)[/SIZE] to make both Qt and Gtk applications looks the same!

**FIXED in Java build 1.6.0_01-ea-b01** (or using the make-jpkg-mustang for previous versions):
*Java 1.6 (as the 1.5) could have problems with Compiz (for example, windows are open with a smaller horizontal size, so they appears like a vertical line), [read here]("http://bugs.compiz.net/view.php?id=136"). Anyway I'm running J2Se 1.6 with Compiz for weeks, so this is not a great bug...*
[/INDENT]If you found this usefull, please ***[digg it]("http://digg.com/linux_unix/Packaging_and_installing_Java_1_6_0_Mustang_JRE_in_Ubuntu_in_few_steps")***!

[SIZE=1]PS: In the screenshot you see Java 1.6 running [Mercury]("http://www.mercury.to"), btw to run it you need to [disable the trayicon]("http://ubuntuforums.org/showpost.php?p=1550670&postcount=17"); use kdocker or alltray instead![/SIZE]

---

### Post by robounix on 2006-09-25
Does this work for anyone?  

After I run make-jpkg-mustang I get the following output.  I thought the script took care of the install?  The note states that I still need to install the java package?

Building debian package in /tmp/sun-java6-jre_1.6.0-rc-b99_i386.deb...
Removing jdk and debian temporary directory trees...

Do you want remove temporary binary file '/tmp/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin'?
 [Y/n]: n

Done!
Now, you must install the package sun-java6-jre_1.6.0-rc-b99_i386.deb
Then, check your java version using "update-alternatives" and "java -version"

update-alternatives --list java
/usr/bin/gij-wrapper-4.1
/usr/lib/jvm/java-gcj/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

---

### Post by anodizer on 2006-09-25
robounix, you must manually install the generated .deb package.

It worked for me, a firefox-plugin would be nice though.

---

### Post by robounix on 2006-09-25
I think my issue is that no .deb package seems to be created, even though the script indicates that it is.  I've even tried in another filesystem and as another user.

Is there a pre-packaged Mustang file floating around yet?

---

### Post by Treviño on 2006-09-26
> **anodizer said:**
> robounix, you must manually install the generated .deb package.

It worked for me, a firefox-plugin would be nice though.
Well... The firefox plugin is installed...

To check that the plugin is loaded by firefox see about:plugins in your browser; if there's no java plugin you've only to do a
```
sudo update-alternatives --config firefox-javaplugin.so
```
Anyway, this should be done by default by the debian package.
> I think my issue is that no .deb package seems to be created, even though the script indicates that it is. I've even tried in another filesystem and as another user.
This script should create the package in the directory where you've launched it, if writable; otherwise it will make it in your home directory.

Maybe a locate could help you.

Anyway I'll update the script with an installation request, to make it even simpler ;)

Thanks for your feedback!

---

### Post by robounix on 2006-09-26
I'm still trying.  No .deb package is being built on my system, even though the script says it's in my home directory.  I've monitored both /tmp and my home directory and the only thing I ever see show up is the jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin file in /tmp.

Also, the java plugin is not installing in my firefox.  

I also tried this on another Dapper box - same result.

Any other suggestions would be greatly appreciated!](*,)

---

### Post by Treviño on 2006-09-26
Sure, if you don't install the debian package, you can't have the firefox plugin...
Btw your situation is strange...

What does the make-jpkg-mustang says when it finishes?

Try to do this
```
cd /tmp
mkdir tmp-sun
cd tmp-sun
make-jpkg-mustang
ls -lh
```
The package must bhe there...
If you don't get any warning it should be there...

Anyway if it still doesn't work, send me a private message, I'll send you a "debug" version so maybe we'll see what's wrong.

PS: I've made this script becouse I heard that we can't freely redistribuite own version of java packages!

---

### Post by robounix on 2006-09-26
Perhaps this is a proxy issue.  Is anything else being downloaded other then they java bin?

Here's my output of make-jpkg-mustang:

rob@recoil:/tmp/tmp-sun$ make-jpkg-mustang
Downloading jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin in /tmp...

--11:09:32--  [http://www.java.net/download/jdk6/binaries/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin](http://www.java.net/download/jdk6/binaries/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin)
           => `jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin'
Connecting to [proxy address]... connected.
Proxy request sent, awaiting response... 301 Moved Permanently
Location: [http://download.java.net/jdk6/binaries/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin](http://download.java.net/jdk6/binaries/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin) [following]
--11:09:32--  [http://download.java.net/jdk6/binaries/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin](http://download.java.net/jdk6/binaries/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin)
           => `jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin'
Connecting to [proxy address]... connected.
Proxy request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.


Download Complete!

Now will be run 'jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin', you must accept the Sun's Java license to generate your debian package

Press any key to continue

Done.

Creating the debian package directory tree...
Generating debian package control file...
Calculating md5 sum...
Building debian package in /tmp/tmp-sun/sun-java6-jre_1.6.0-rc-b99_i386.deb...
Removing jdk and debian temporary directory trees...

Do you want remove temporary binary file '/tmp/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin'?
 [Y/n]:

---

### Post by hwbj on 2006-09-26
> **robounix said:**
> Perhaps this is a proxy issue.  Is anything else being downloaded other then they java bin?

Here's my output of make-jpkg-mustang:

rob@recoil:/tmp/tmp-sun$ make-jpkg-mustang
Downloading jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin in /tmp...

Do you want remove temporary binary file '/tmp/jdk-6-rc-bin-b99-linux-i586-15_sep_2006.bin'?
 [Y/n]:

Just a guess here....I had the same thing happen on a brand spanking new install this morning, same output.

I later tried it my regular box and it worked fine...I'm thinking you need
to have something like build-essentials, fakeroot or dpkg-dev installed.
some package that allows you to build .debs that isn't installed automatically. Not sure which it might be.

Looking forward to checking out 1.6, nice script (tho I think there are some dependency issues)

---

### Post by Treviño on 2006-09-26
Well, my package actually depends on 
> coreutils, dpkg, wget, gzip
Anyway, looking the code I forgot to add fakeroot too...
Do you have it?

If not, install it... Anyway I'm updating the package...

---

### Post by Treviño on 2006-09-26
Well... _*New version (0.6.5)*_ out... 
Now it has all the needed dipendencies (before I forgot to add fakeroot), and I've ***fixed the firefox java plugin installation***...

If you have my repository in your list, simply upgrade. Else, download the deb from [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/make-jpkg-mustang_0.6.5-3v1ubuntu1_all.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/make-jpkg-mustang_0.6.5-3v1ubuntu1_all.deb)

To look the script source, you can go here: [http://paste.ubuntu-nl.org/24939](http://paste.ubuntu-nl.org/24939)


Bye!

---

### Post by danderson3 on 2006-09-27
thanks for your work!

I don't seem to have the plugin.  update-alternatives returns no error
and does let me choose between 1.5 and 1.6.  Neither firefox 1.5.0.7 nor
swiftfox 1.5.0.7 show the plugin...  What exactly does u-a do?

David

---

### Post by danderson3 on 2006-09-27
never mind, I found firefox has the plugin.
( looking into swiftfox now )

---

### Post by sadiini on 2006-09-27
To do everything we need run (as user, please!)
```
make-jpkg-mustang
```The script will do all the work, btw you've to _*agree with the Sun Java License*_.

I had to do this using sudo. Otherwise it did not work. /tmp is root permissions dirctory. As user I got bunch of errors. 
Anyway - I wanted it to be istalled systemwide anyway...

---

### Post by danderson3 on 2006-09-27
for swiftfox:

/opt/swiftfox/plugins# mv libjavaplugin.so libjavaplugin.so.save
/opt/swiftfox/plugins# ln -s /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin.so

---

### Post by desperado666 on 2006-09-27
my messenger 1.8 doesnt start anymore. Does mercury version 1.9 solve this java 1.6 problem?

---

### Post by Treviño on 2006-09-27
**sadiini**, ehm... /tmp should have those permissions:
```
drwxrwxrwt  23 root  root      8192 2006-09-27 15:59 /tmp
```, that's why I used it... Anyway no problem... With sudo it should work anyway.

Regarding **swiftfox**, the deb package author has made many mistakes, in fact he has linked the swiftfox "plugins" directory to /usr/lib/mozilla-firefox/plugins (old firefox dir. i.e. <= breezy) instead of /usr/lib/firefox/plugins (firefox standard in from dapper).
So if you want use the firefox java plugin with swiftfox you could do this (or remake a new java .deb package with the newer make-jpkg-mustang that I'm uplodaing right now...):
```
sudo update-alternatives --install "/usr/lib/mozilla-firefox/plugins/libjavaplugin.so" "mozilla-firefox-javaplugin.so" "/usr/lib/jvm/java-1.6.0-sun/jre/plugin/$(dpkg --print-architecture)/ns7/libjavaplugin_oji.so" "3050"
```Regarding **Mercury**, as I said in the main post, you've to disable the tray icon, becouse java 1.6 doesn't support it at all... Anyway you could use softwares like kdocker or alltray to minimize to tray your Mercury.
I'm using kdocker (with [this icon]("http://img245.imageshack.us/img245/7833/msnsh4.png") - to be resized - if you need one), and I'm happier... The original tray icon is really bad to me... :P
To disable your mercury tray icon do this:
```
sudo mv /usr/lib/mercury/jni/linux/libtray.so /usr/lib/mercury/jni/linux/libtray.so.bak
```Then run mercury and it will work!

If you want use mercury 1.9 (beta), grab it from [this forum]("http://forum.mercury.to/index.php?showforum=40") (you need to be registered before)!

---

### Post by robounix on 2006-09-27
This is a new box and it looks like the issue was not having fakeroot.  I noticed after I installed it and ran make-jpkg-mustang that the step where the .deb package is being built took a minute or so where it used to proceed to the next step almost instantly.

So add those into your prerequisite checks and you should be good to go.

Thanks again! :p

---

### Post by Treviño on 2006-09-27
> **robounix said:**
> This is a new box and it looks like the issue was not having fakeroot.  I noticed after I installed it and ran make-jpkg-mustang that the step where the .deb package is being built took a minute or so where it used to proceed to the next step almost instantly.

So add those into your prerequisite checks and you should be good to go.

Thanks again! :p
Happy to know it! :)
Anyway the [latest version](http://ubuntuforums.org/showpost.php?p=1548490&postcount=11) I have made, was bugfixed... That was the only inportant dependency that I've to put in, and I forgot it! :D

Bye ;)

---

### Post by Treviño on 2006-09-28
New Java rc is out (b100) now... Few changes, no new features: [changelog]("http://download.java.net/jdk6/changes/jdk6-b100.html").
You can update creating the new package by running (again) 
```
make-jpkg-mustang
```A new deb file will be done for you! ^_^


Bye ;)

---

### Post by Treviño on 2006-09-29
Sorry for posting again, but there's a new ***important update (_especially for KDE users_)*** in my repository (or just use the link in the first post, it's updated!)...

In fact, also if I'm a kubuntu user, in the latest days I used to load gnome-settings-daemon to control some settings unmanaged by Xgl and KDE (small text resolution, no completely working keyboard...). Now I fixed my problems, so I removed completely gnome-settings-daemon from my starting script and I noticed that all the Java apps I have, lose their wonderful subpixel font rendering effect 
 that mustang give them...

So I searched a little and I've found that ***Java Mustang reads only the gnome settings _not_ the KDE ones*** to control the font rendering :(

So,_* I've managed to fix this*_ using a little escamotage-script, loaded before each "java call", which, if kde is in use, reads the KDE settings and reconfigures "on the fly" java.

From all my tests _**it works well**_, kde users have only to set their antialiasing options from Kcontrol -> Font settings.

So... Update to [make-jpkg-mustang 0.7.5]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/make-jpkg-mustang_0.7.5-3v1ubuntu1_all.deb") and regenerate/install your Java .deb package to get mustang _*full working*_ also _with the K desktop_!!! :)

---

### Post by ferd on 2006-10-09
OK, I've gone through all 3 pages and have suceeded installing JRE 1.6.0 for firefox. However, swiftfox does not recognize this install or any other JRE install for that matter. I have tried all the scipts and nothing works. Oh well.](*,)

---

### Post by berserker on 2006-10-09
> **ferd said:**
> OK, I've gone through all 3 pages and have suceeded installing JRE 1.6.0 for firefox. However, swiftfox does not recognize this install or any other JRE install for that matter. I have tried all the scipts and nothing works. Oh well.](*,)

Try this:

```
cd ~/.mozilla/plugins
ln -s /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so  libjavaplugin.so
```

---

### Post by ferd on 2006-10-10
Thanks for your reply. The first line of the help was not found. I know it is there. My /home is a seperate partition, if that makes a difference.

---

### Post by Treviño on 2006-10-10
So do a 
mkdir ~/.mozilla/plugins

Anyway swiftfox should use the /usr/lib/mozilla-firefox/plugins dir... While firefox uses /usr/lib/firefox/plugins...
Anyway my make-jpkg-mustang should support both directories... Strange!

Please, make a ls of these dir, and post your output here.
Thanks


Bye!

---

### Post by ferd on 2006-10-10
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.xpt
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in.xpt
libjavaplugin.so        mplayerplug-in-rm.so   nphelix.so
libunixprintplugin.so   mplayerplug-in-rm.xpt  nphelix.xpt
mplayerplug-in-gmp.so   mplayerplug-in.so      nppdf.so
mplayerplug-in-gmp.xpt  mplayerplug-in-wmp.so
bruce@bruce-desktop:~$ ls /usr/lib/firefox/plugins
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.xpt
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in.xpt
libjavaplugin.so        mplayerplug-in-rm.so   nphelix.so
libunixprintplugin.so   mplayerplug-in-rm.xpt  nphelix.xpt
mplayerplug-in-gmp.so   mplayerplug-in.so      nppdf.so
mplayerplug-in-gmp.xpt  mplayerplug-in-wmp.so
That's the output of the ls command you requested. Thanks again for the help.

---

### Post by Treviño on 2006-10-13
ls /usr/lib/firefox/plugins/libjavaplugin.so -l
And then do a "ls -l" of the file pointed by the file above...
It should be 

ls -l /etc/alternatives/firefox-javaplugin.so --> /usr/lib/jvm/java-1.6.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by tpischke on 2006-10-21
worked for me.   Thanks!  Now how about the option to install the JDK in addition to the JRE? :)

---

### Post by Treviño on 2006-10-22
I should update my script for this... When I find time I'll upgrade it ;)

---

### Post by cord on 2006-11-06
I would also love a version for edgy if you get the chance!

Cant wait to see if I can get any speedups with this new jre.

---

### Post by xen14 on 2006-11-08
worked fine for me, thanks! :-D

---

### Post by Treviño on 2006-11-27
Waiting for new script releases, if you've problems with Compiz/Beryl and java apps, add
> export AWT_TOOLKIT=MToolkit
to your /usr/bin/java scrpt-file... ;)

---

### Post by mundano on 2006-12-08
Will this script work on Edgy?

---

### Post by artisan on 2006-12-09
Worked for me.
Thanks.

---

### Post by Xubus on 2006-12-11
Doesn't seem to be working for 1.6 final :/

> The package you've chosen isn't a good Java binary self-extracting JDK package. Exiting...

---

### Post by berserker on 2006-12-11
Please follow the easier and better instructions below.

---

### Post by FunkyFish on 2006-12-13
Sun does no longer extract their files to /tmp/jdk... but to your current working directory/jdk... 

Therefore to get the script working with the final mustang release: 
```

cp jdk-6-linux-i586.bin /tmp/
cd /tmp
make-jpkg-mustang jdk-6-linux-i586.bin

```

That's all!

Greetings 
-Fufi-

---

### Post by Treviño on 2006-12-14
Ehm... Anyone know the java 6 stable *.bin direct link?
Because without it, I can't update the script :/

---

### Post by adam.tropics on 2006-12-14
The urls the sun downloader uses are

jdk: [http://192.18.108.147/ECom/EComTicketServlet/BEGIND06E18FF5D0124BDA2EFA667752C0B35/-2147483648/1834742079/1/790634/790370/1834742079/2ts+/westCoastFSEND/jdk-6-oth-JPR/jdk-6-oth-JPR:5/jdk-6-linux-i586.bin](http://192.18.108.147/ECom/EComTicketServlet/BEGIND06E18FF5D0124BDA2EFA667752C0B35/-2147483648/1834742079/1/790634/790370/1834742079/2ts+/westCoastFSEND/jdk-6-oth-JPR/jdk-6-oth-JPR:5/jdk-6-linux-i586.bin)
jre: [http://192.18.108.147/ECom/EComTicketServlet/BEGIN3EEBD24B1D7EC570C2FB9837B6157464/-2147483648/1834743423/1/790562/790382/1834743423/2ts+/westCoastFSEND/jre-6-oth-JPR/jre-6-oth-JPR:5/jre-6-linux-i586.bin](http://192.18.108.147/ECom/EComTicketServlet/BEGIN3EEBD24B1D7EC570C2FB9837B6157464/-2147483648/1834743423/1/790562/790382/1834743423/2ts+/westCoastFSEND/jre-6-oth-JPR/jre-6-oth-JPR:5/jre-6-linux-i586.bin)

are they what you're after?

---

### Post by Treviño on 2006-12-14
Ok, the first link is ok... Anyway I should upgrade the script to work also with the jre bin, but actually I've no time  :(

So, you can simply download [this file]("http://192.18.108.147/ECom/EComTicketServlet/BEGIND06E18FF5D0124BDA2EFA667752C0B35/-2147483648/1834742079/1/790634/790370/1834742079/2ts+/westCoastFSEND/jdk-6-oth-JPR/jdk-6-oth-JPR:5/jdk-6-linux-i586.bin") and then run the script with the file as parameter as stated by FunkyFish

Bye ;)

---

### Post by mlind on 2006-12-14
There's also **java-package** with sun's jdk/jre 1.6 support added
[http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15)

---

### Post by Treviño on 2006-12-15
I've just updated the package, it fixes the problems with the newer betas...
Consider to upgrade again, because the new beta fixes problems with Compiz (not with beryl yet :(): [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6429775)

---

### Post by oroboro on 2006-12-15
Sorry, didn't read previous posts.

---

### Post by Treviño on 2006-12-16
If you're using my beryl svn builds, you don't kneed anymore the "AWT_TOOLKIT"  patch... Simply ;)
edit your /usr/bin/java if you want ;)

---

### Post by benjaminzsj on 2006-12-16
It's a great how-to, thanks.
I have a problem starting mercury after this update, now I can only start mercury from my home directory, which means it won't work whether I start it in any other directory or from the menu item.

---

### Post by Treviño on 2006-12-16
Mmhmh I run it from menu and it works well... :o
Could you provide a log (not running it from home)?

Thanks!

---

### Post by benjaminzsj on 2006-12-16
> **Treviño said:**
> Mmhmh I run it from menu and it works well... :o
Could you provide a log (not running it from home)?

Thanks!
Error message:```
/usr/bin/mercury: line 8: cd: ../../usr/lib/mercury/startup/..: No such file or directory
ls: lib: No such file or directory
```Startup script:```
#!/bin/bash
cmdline=$0
symlink=`find "$cmdline" -printf "%l"`
if [ $symlink ]; then
   cmdline=$symlink
fi

cd `dirname $cmdline`/..

classpath=""
for file in `ls lib`
do
   classpath="lib/$file:$classpath"
done

java -Djava.library.path=jni/linux:jni/linux/jmf -classpath $classpath com.dMSN.Main
```Thanks in advance.

BTW, when I start it with my account the GUI is alright, no conflict with Beryl, but if I run it as root, this problem remains.

---

### Post by rockprincess on 2006-12-17
hello,

has anyone found a helpful solution/approach to configure the bastard that JMF is??

I can't seem to get it working, and I don't wanna switch to windows just to use JMF :(

many thanks for future advice!

---

### Post by Treviño on 2006-12-17
Regarding the problem with beryl, if you try my beryl svn builds it should be fixed; regarding the script

Is you mercury installed in /usr/lib/mercury? If not put it there...
If it's there, try to change the script line 8 to 
cd /usr/lib/mercury

---

### Post by Treviño on 2006-12-17
> **rockprincess said:**
> hello,

has anyone found a helpful solution/approach to configure the bastard that JMF is??

I can't seem to get it working, and I don't wanna switch to windows just to use JMF :(

many thanks for future advice!
To make it work (with mercury) I used this way (i found that on the mercury forum, but I don't know if I remember it exactly :P): 
- run mercury as root
# - add your webcam from the JMF module (it should work as root!)
- sudo cp -arfv /root/.jmf ~/
- sudo chmod $USER:$USER ~/.jmf -R
- jmf now should work also for your user ;)

PS: have you also seen this: [http://mercury.to/index.php?page=Wiki&wikipage=InstallingJMF](http://mercury.to/index.php?page=Wiki&wikipage=InstallingJMF)

PS2: maybe the 2nd passage isn't needed, you only have to make jmf to create the /root/.jmf dir ;)

---

### Post by benjaminzsj on 2006-12-17
> **Treviño said:**
> Regarding the problem with beryl, if you try my beryl svn builds it should be fixed; regarding the script

Is you mercury installed in /usr/lib/mercury? If not put it there...
If it's there, try to change the script line 8 to 
cd /usr/lib/mercuryThanks a lot, changing the content works. Still wonder why this general purpose script fails me. I've been using your beryl svn repository and thanks again, now it's fine after this modification.:)
Java 6 really amazes me with its efficiency.

---

### Post by pepz on 2006-12-21
i've this problem: after the installation of the script , i've deleted sun-java5 packages and the .odt, .ods and .zip files became application/x-java-archive. How can i fix this problem?
i tried to reinstall the .deb package, but i've not success. This problem is due to the deleting of java5 .deb packages? have i to reinstall it? i've deleted also the gij wrapper to solve this problem, but i've no success.
help me, please.
bye
peppe

---

### Post by benjaminzsj on 2006-12-21
> **pepz said:**
> i've this problem: after the installation of the script , i've deleted sun-java5 packages and the .odt, .ods and .zip files became application/x-java-archive. How can i fix this problem?
i tried to reinstall the .deb package, but i've not success. This problem is due to the deleting of java5 .deb packages? have i to reinstall it? i've deleted also the gij wrapper to solve this problem, but i've no success.
help me, please.
bye
peppeSame here, I think it's the new Java6 changing the mime type since I haven't removed Java5.

---

### Post by pepz on 2006-12-22
i've reinstalled the old java5, but i got the same problem. i tried to use only java5 or java6 with the old version installed, but nothing changes.
how can i do?
thanks
bye
peppe

---

### Post by Treviño on 2006-12-22
Mhmmh... Never checked that, maybe it's due to the fact that the "jar" are standard zip files, and so now the system consider all the zip-like files as jar.. I should look it...

Does it create problems for you?
Here (kde), I don't get troubles, but maybe gnome has a different behavior

---

### Post by pepz on 2006-12-23
trevino you are right... i've opened also this thread on ubuntu-it.org: [http://forum.ubuntu-it.org/index.php?topic=51909.msg286899#msg286899](http://forum.ubuntu-it.org/index.php?topic=51909.msg286899#msg286899)
i'm on gnome, and this DE, unlike of kde, hasn't a control center in which set the association file.
thanks
bye
peppe

---

### Post by kalikiana on 2006-12-23
I was able to successfully install Java 1.6, so thank you very much for that nice script. However still no java app uses my gtk theme, it's just like before although it seems to recognize the new option.

Any suggestions?

---

### Post by saceirdoth on 2006-12-24
> **pepz said:**
> i've this problem: after the installation of the script , i've deleted sun-java5 packages and the .odt, .ods and .zip files became application/x-java-archive. How can i fix this problem?
i tried to reinstall the .deb package, but i've not success. This problem is due to the deleting of java5 .deb packages? have i to reinstall it? i've deleted also the gij wrapper to solve this problem, but i've no success.
help me, please.
bye
peppe

Same problem (Edgy+Gnome)

---

### Post by foureight84 on 2007-01-04
this works! awesome. it even fixes the blank screen on frostwire when running in beryl. however, i can't type anything in the dialog boxes. i have to paste it. anyone know a fix?

---

### Post by Treviño on 2007-01-05
Did you intsalled the latest version of java?
I had that problem on mercury too, but then fixed... Btw i don't know it the fix is due to the new mercury beta release or to the java (but I think it's due to mercury!)

---

### Post by adam.tropics on 2007-01-05
> **Treviño said:**
> Mhmmh... Never checked that, maybe it's due to the fact that the "jar" are standard zip files, and so now the system consider all the zip-like files as jar.. I should look it...


It's a syntax error in the file  /usr/lib/jvm/java-1.6.0-sun/jre/lib/deskt op/mime/packages/x-java-archive.xml

To fix:

```
sudo chmod +w /usr/lib/jvm/java-1.6.0-sun/jre/lib/deskt op/mime/packages/x-java-archive.xml
``````
sudo gedit /usr/lib/jvm/java-1.6.0-sun/jre/lib/desktop/ mime/packages/x-java-archive.xml
```If you scroll down you will see the line

```
match type="host16" value="0xcafe" offset="40" />
```which should instead read
```

<match type="host16" value="0xcafe" offset="40" />
``````
sudo update-mime-database /usr/share/mime
```

---

### Post by foureight84 on 2007-01-05
i tried to install the latest version of java6 by doing 

```

make-jpkg-mustang ~/Desktop/java6_package

```

the java6 package was from java.sun.com but it didn't work. i got an error. so i just ran make-jpkg-mustang and let it download and install the package.

---

### Post by pepz on 2007-01-05
thanks adam... it works, thank a lot
bye
pepz

---

### Post by Treviño on 2007-01-05
Thanks for the fix, BTW I think that someone should report this to sun bug tracker, because this is isn't a problem due to my packaging...

Bye ;)

---

### Post by pepz on 2007-01-06
i've another little problem: when i try to verify the installation of java by java's website, i get on this page, [http://www.java.com/it/download/installed.jsp?jre_version=1.6.0_01-ea&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.17-10-generic](http://www.java.com/it/download/installed.jsp?jre_version=1.6.0_01-ea&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.17-10-generic)
but this is blank, it doesn't display any information about jvm.
how can i solve it?
bye
pepz

---

### Post by NoJock on 2007-01-06
> **Treviño said:**
> Hello, while Java 1.5 has been added to our repositories some time ago, a new Java release is coming... 
In fact, **Java 1.6.0** (codenamed *mustang*) is actually in *Release Candidate* state but it is just really stable and really much more performing (using, from my point of view, less memory!).

[SIZE=4]_**Features**_[/SIZE]
This is a [summarized list of the **new features**]("http://www.javalobby.org/java/forums/t72230.html"); first of all for linux users I've to underline the support for *full-screen mode*, then for all the support for ***_native_ ****GTK graphics widgets*** (i.e. your gtk theme from your gtkrc conf file!), and ***subpixel rendering*** (finally!) :D
I want explain better this two “main” graphical features, showing what has really changed from the user interface point of view (anyway [here]("http://www.ffnn.nl/pages/articles/java/java-2-se-6.0-aesthetics-preview.php") you can find more informations on all others new aesthetics features).

**Gtk graphic theme support**
[[IMG]http://img245.imageshack.us/img245/4642/screenshot39rc1.th.png[/IMG]]("http://img245.imageshack.us/img245/4642/screenshot39rc1.png")
Above :rolleyes: you can see some kind of java test widgets rendered using “your” linux (true) gtk theme (the one in the shot, is [QtCurve]("http://www.kde-look.org/content/show.php?content=40492") the Qt/Gtk theme/engine that I use). You can see another example in [this screenshot]("http://img356.imageshack.us/img356/6994/mercurymustangku5.jpg") showing Mercury rendered using the Ubuntu Human Quicksilver gtk theme!!
*Finally Java apps could look like your standard applications! :)*

Anyway this feature isn't enabled by default (newer versions of make-jpkg-mustang will support it), you must define this environment variable:
```
export _JAVA_OPTIONS="-Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel"
```[SIZE=1]Btw some applications like Mercury have a built-in theme selector; in those cases, you should select the "Gtk theme".[/SIZE]

**Subpixel Rendering**
[[IMG]http://img153.imageshack.us/img153/4571/screenshot11ky2.th.png[/IMG]]("http://img153.imageshack.us/img153/4571/screenshot11ky2.png")
Above :rolleyes: you can see how it looks good the new font rendering (especially for LCD screens), the three windows shows (from left to right):
1) Java 1.5 (standard “old” java font rendering)
2) Java 1.5 (using the "-Dswing.aatext=true" paramter that activate a semi-antialiased font rendering)
3) Java 1.6 (using the built-in new subpixel rendering)

Java 1.6 reads your gnome (and KDE, using a package made with make-jpkg-mustang >=0.7.5) font antialiasing/rendering settings and apply it to its applications too; as you can see in the screenshot (3) the result is great (there are, btw, more settings so the screenshot shows only a case).[I]
Finally Java apps could have a smoother look in your LCD screen! :)[/I]

You can find more informations on Mustang's subpixel rendering [here]("http://today.java.net/pub/a/today/2005/07/26/lcdtext.html").

[SIZE=4]_**Installation**_[/SIZE]
Anyway after this little explaination, _***let's install and package it***_...
Well... Considering that the java-package's [FONT=Courier New]make-jpkg[/FONT] doesn't work with latest versions of the binary, I've decided to create a my own script that in only a move:
- Downloads the latest jdk java package (working both for i386 and amd64)
- Extracts it, removing the unnecessary JDK stuff
- Creates a debian _JRE_ package to be installed in your system
- The package installs and sets as default (using [FONT=Courier New]update-alternatives[/FONT]) all the Jre's binaries and the firefox java plugin
- KDE kcontrol font rendering settings supported ([read here]("http://ubuntuforums.org/showpost.php?p=1558000&postcount=21"))

To install this script, you've only to install a package from [**My Repository**]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/").
Add it to your [FONT=Courier New]sources.list[/FONT] (there's also other cool stuff):
```
deb http://download.tuxfamily.org/3v1deb/ 3v1n0
```Then
```
sudo apt-get install make-jpkg-mustang
```Anyway, if you don't want to add the repository, you can simply install the .deb downloading it from [this page]("http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/") [SIZE=1](look for the *make-jpkg-mustang* deb!)[/SIZE].

To do everything you need run (as user, please!)
```
make-jpkg-mustang
```The script will do all the work, btw you've to _*agree with the Sun Java License*_.

You can also generate the debian package from another mustang's downloaded bin file by running

```
make-jpkg-mustang /your_dir/your_sun_jdk_binary_file.bin
```After that the downloading/converting process has ended, you're asked for installing the just made package; if you refuse, you've to manually install the created package saved where the script says.

That's All!:KS

**Notes:**[INDENT]You don't need to remove the standard sun-java5-* packages, simply if you want to re-use the old version use the command [FONT=Courier New]sudo update-alternatives --config java[/FONT] to set your favourite java virtual machine [SIZE=1](or simply run the standard jvm by [FONT=Courier New]/usr/lib/jvm/java-1.5.0-sun/jre/bin/java[/FONT])[/SIZE]!

Actually the make-jpkg-mustang package build only the sun-java6-jre package, anyway, I'm planning to integrate it to create also the other packages (jdk, src, plugin, demo...): let me know if you're intrested in!

This should work in amd64 systems too, btw it's not tested there, so, please, let me know if there's something of wrong!

KDE font rendering settings are now read by an "home-made" script... To use subpixel rendering, use kcontrol standard font settings.

KDE/Qt theme Java support isn't just now in a Work in Progress status (read/try more [here]("http://kdelaf.freeasinspeech.org/")), anyway you can use the Gtk-Qt engine to make your gtk (and so, java) applications look (quite) like your KDE's ones.
Otherwise use themes like [QtCurve]("http://www.kde-look.org/content/show.php?content=40492") [SIZE=1](present in my repository)[/SIZE] to make both Qt and Gtk applications looks the same!

**FIXED in Java build 1.6.0_01-ea-b01** (or using the make-jpkg-mustang for previous versions):
*Java 1.6 (as the 1.5) could have problems with Compiz (for example, windows are open with a smaller horizontal size, so they appears like a vertical line), [read here]("http://bugs.compiz.net/view.php?id=136"). Anyway I'm running J2Se 1.6 with Compiz for weeks, so this is not a great bug...*
[/INDENT]If you found this usefull, please ***[digg it]("http://digg.com/linux_unix/Packaging_and_installing_Java_1_6_0_Mustang_JRE_in_Ubuntu_in_few_steps")***!

[SIZE=1]PS: In the screenshot you see Java 1.6 running [Mercury]("http://www.mercury.to"), btw to run it you need to [disable the trayicon]("http://ubuntuforums.org/showpost.php?p=1550670&postcount=17"); use kdocker or alltray instead![/SIZE]


This didnt work for me here is my out put las lines
Download Complete!
Checking java binary file...
/usr/bin/make-jpkg-mustang: line 76: strings: command not found
The java binary file is not for your i386 architecture, please download the righ t file
lee@lee-desktop:~$ make-jpkg-mustang /your_dir/your_sun_jdk_binary_file.bin

Downloading jdk-6u1-ea-bin-b01-linux-i586-14_dec_2006.bin in /tmp...

jdk-6u1-ea-bin-b01-linux-i586-14_dec_2006.bin: Permission denied

Download Complete!
Checking java binary file...
/usr/bin/make-jpkg-mustang: line 76: strings: command not found
The java binary file is not for your i386 architecture, please download the right file
lee@lee-desktop:~$

---

### Post by Treviño on 2007-01-07
Install the "binutils" package...

---

### Post by NoJock on 2007-01-07
And were do i find this? Checked binutils-static is installed.

---

### Post by Treviño on 2007-01-14
I mean this: [http://packages.ubuntu.com/edgy/devel/binutils](http://packages.ubuntu.com/edgy/devel/binutils)

It includes the "strings" software...

---

### Post by finite9 on 2007-01-14
Ubuntu 6.06 amd64 with Firefox 1.0.5.  I ran the script today to make the jre and the plugin for Firefox does not work because the links that point to the .so file are all invalid.  The jre does not contain the plugins directory in the following path:

/usr/lib/jvm/java-1.6.0-sun/jre/plugin/amd64/ns7/libjavaplugin_oji.so

How do I fix this?

UPDATE:  I downloaded JRE and JDK manually from Sun and after unpacking, neither of them contain the plugin.  Does anyone have an older beta that does have the plugin...has anyone done this with amd64?

---

### Post by ernstblaauw on 2007-01-18
Works great for me! Do you know if you're going to make such a script for the JDK? Because I don't know how to install that one.
Thanks for this great script!

---

### Post by Treviño on 2007-01-20
There's no plugin for amd64 I guess... Look on google about it, but I don't really know...

Regarding JDK, is in my todo-list... But I've really a little free time to maintain all the projects I'm involved in :(

---

### Post by Jojo12a on 2007-01-21
I think I have a better solution which more closely integrates into the debian java package format. I have just recompiled the source package "sun-java6" from feisty for edgy.

It needs a bit more download than most other solutions, as both jre and jdk have to be downloaded from the ubuntu servers, but I personally think it's worth it.

1. create a suitable directory and enter it:
```
mkdir ~/sun-java6-package
cd ~/sun-java6-package
```

2. download the feisty sources and unpack them:
```
wget http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6_6-00-0ubuntu1.dsc http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6_6-00.orig.tar.gz http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6_6-00-0ubuntu1.diff.gz
dpkg-source -x sun-java6_6-00-0ubuntu1.dsc
```

3. enter the source directory and change the versioning, to make the version slightly lower than the feisty version (good for upgrades):
```
cd sun-java6-6-00
dch -b -v 6-00-0ubuntu1~edgy1 -D edgy "Backport to edgy."
```

4. compile the package, this might need a bit of time:
```
debuild binary
```
note that if there are errors regarding build dependencies, just install the packages asked for, they are all available in edgy.

5. install the created packages, try taking packages not needed out of the braces, but they might depend on each other:
```
sudo dpkg -i ../sun-java6-{bin,demo,doc,fonts,jdk,jre,plugin,source}_*.deb
```

6. update all links to java executables:
```
sudo update-java-alternatives -s java-6-sun
```

7. delete all created files:
```
cd
rm -r ~/sun-java6-package
```

I have done this some time ago, so that there might be some things i have forgotten, but i think it's the most fitting solution, as it's just like the java 1.5 packages in edgy and not a make-jpkg package which won't fit into the system as nicely.

---

### Post by wigard89 on 2007-01-23
> **Treviño said:**
> Well... The firefox plugin is installed...

To check that the plugin is loaded by firefox see about:plugins in your browser; if there's no java plugin you've only to do a
```
sudo update-alternatives --config firefox-javaplugin.so
```
Anyway, this should be done by default by the debian package.

This script should create the package in the directory where you've launched it, if writable; otherwise it will make it in your home directory.

Maybe a locate could help you.

Anyway I'll update the script with an installation request, to make it even simpler ;)

Thanks for your feedback!

I run your script. completed the install using your script. I don't have a javaplugin.so in firefox. I used your suggestion to issue command
```
 sudo update-alternatives --config firefox-javaplugin.so
```
and update-alternatives reports that there is no plugins anywhere on my system.

I am using Ubuntu 6.10 Edgy AMD64, I ran this script against my 64-bit system.
 I don't find any javaplugin in any directory for me to make a symlink to either.
Any suggestions?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Treviño on 2007-01-25
From what I *heard* the amd64 build doesn't include the firefox plugin...

---

### Post by neymac on 2007-01-26
Today we have the option to install java 6 from the repository:

[http://archive.ubuntu.com](http://archive.ubuntu.com)  edgy-backports/multiverse

The packages:
sun-java6-bin 6-00-0ubuntu1~edgy1
sun-java6-jre 6-00-0ubuntu1~edgy1

Is this the java mustang version of this thread?

---

### Post by benjaminzsj on 2007-01-27
> **neymac said:**
> Today we have the option to install java 6 from the repository:

[http://archive.ubuntu.com](http://archive.ubuntu.com)  edgy-backports/multiverse

The packages:
sun-java6-bin 6-00-0ubuntu1~edgy1
sun-java6-jre 6-00-0ubuntu1~edgy1

Is this the java mustang version of this thread?Along with jdk.

---

### Post by Treviño on 2007-02-05
**neymac**, this script always download the latest version (not stable) from web and generate a package... Unfortunately this package name doesn't overwrite the new one, I should maybe change the version naming...
In fact, actually with my script you can install the version 1.6.0_01-ea-b03 wich fixes many bugs related to Compiz/Beryl swing support for example...

---

### Post by Flingus on 2007-02-07
This is an older thread so I hope someone notices. :)

I tried these steps (so I could install LimeWire) and got the following msg:

flingus@flingus-desktop:~/LimeWire$ ./runLime.sh
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

Now, from my understanding this script installs a newer version of JRE correct?

Thanks!! 

Flingus:guitar:

---

### Post by Flingus on 2007-02-08
Sorry, figured it out. Managed to install a newer version of java using the applications pulldown. :)

---

### Post by Treviño on 2007-04-05
Few days ago I've uploaded a new version... It has changed the version naming to override the standard ubuntu version...

This has been done since the packages now installed (with auto-downloading) from this script are generally newer than the one on ubuntu repositories...

So, also if this script seems now with no sense, it can be used to install latest JRE with many fixes (first of all for compiz/beryl)... However I'll add this project to launchpad to be supported again for a better support (i.e. jdk building) and maybe it will be useful when newer java7 will be out...

Bye!

---

### Post by ernstblaauw on 2007-04-05
Works this script also on Feisty?

---

### Post by Treviño on 2007-04-05
Sure... 

I wanted to test new launchpad and integrate this project on bazaar and so now you can find latest sources and informations/bugs at [https://launchpad.net/make-jpkg-mustang]("https://bugs.launchpad.net/make-jpkg-mustang/")

---

### Post by giorgosts on 2007-04-05
Some applets don't run under the new Java 1.6.0_02-ea java plugin I've installed with this script. They load but they don't start Eg. [http://cemp1.switch.ch/network/performance/web100/tcpbw100.html](http://cemp1.switch.ch/network/performance/web100/tcpbw100.html) Internet speed test. Some other applets run fine though. Has anyone else experienced this problem?

---

### Post by Treviño on 2007-04-05
Well, here it works (tested on konqueror) BTW I know that there are some problems with the plugin (also with standard 1.6 version), sometimes it blocks the browser until the applet has loaded completely...
There is also a bug on launchpad about it...

---

### Post by giorgosts on 2007-04-05
Before posting I tested it to all the browsers I have, i.e. all mozilla-like, konq. and opera. I also tried to delete the .java folder. I then reverted to the default version. The bug which you are talking about (i.e. page doesn't render until applel loads) is present in 1.6.0.0 version also, but I have no problem with that since when the applet loads everything works.

---

