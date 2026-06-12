---
title: "HOWTO: Beagle 0.0.9 and Mono 1.1.6 on Hoary Hedgehog"
date: 2005-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by sebgate20 on 2005-05-03
Hey All

Again, Evolution Colt has made another HOWTO for installing Beagle 0.0.9 and Mono 1.1.6 on Hoary Hedehog. It covers installing it and configuring all the bits. It works fully with Evolution 2.2 support, Tomboy, MS Office, GStreamer and Web Services Support.

You can find the HOWTO at [http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall)

I hear it is going to be included in Breezy Badger. Could the person who is doing this contact me at spayne (at) evolutioncolt.com (just for a chat!)

Give me feedback!

Seb

---

### Post by jonny on 2005-05-03
I tried this yeaterday.  It's very clear and it worked perfectly.

Unfortunately, Epiphany support's not compiled in to these packages.  I've tried compiling from CVS, but it's asking me for a package called epiphany-1.2 that I can't find anywhere.

Has anyone got Beagle woring with Epiphany?  If so, how did you do it?

---

### Post by sebgate20 on 2005-05-03
Jon Trowbridge (chief Beagle guy) said that Epiphany support is going to be discontiuned as most people seem to use Mozilla Firefox now!

Bad luck. I tried it get it to compile but it won't.

Seb

---

### Post by jonny on 2005-05-03
[QUOTE=sebgate20]Jon Trowbridge (chief Beagle guy) said that Epiphany support is going to be discontiuned as most people seem to use Mozilla Firefox now![/QUOTE]That's so depressing.  I tried epiphany out of curiosity and now I much prefer it to Firefox - I really don't want to go back.

Firefox is a great app - it's my browser of choice in WIndows - but it feels really out of place in Gnome.  I hate the way its menus and icons feel so alien, and I hate the way it doesn't use the default apps to open files.  And epiphany's handling of bookmarks and in-line searching is just soo slick.

Shucks.

---

### Post by sebgate20 on 2005-05-03
[QUOTE=jonny]That's so depressing.  I tried epiphany out of curiosity and now I much prefer it to Firefox - I really don't want to go back.

Firefox is a great app - it's my browser of choice in WIndows - but it feels really out of place in Gnome.  I hate the way its menus and icons feel so alien, and I hate the way it doesn't use the default apps to open files.  And epiphany's handling of bookmarks and in-line searching is just soo slick.

Shucks.[/QUOTE]
 Sod's law eh? I like both but I prefer Firefox with the Ximian Industrial Theme from [http://primates.ximian.com/~glesage/stuff/firefox/](http://primates.ximian.com/~glesage/stuff/firefox/) which looks good with the Clearlooks/Industrial theme.

Seb

---

### Post by aleahey on 2005-05-03
all works but when i try to run best (the gui searcher dealy) i get :

> Unhandled Exception: System.DllNotFoundException: gtkembedmoz
in <0x00053> (wrapper managed-to-native) Gecko.WebControl:gtk_moz_embed_set_profile_path (string,string)
in <0x00026> Gecko.WebControl:.ctor ()
in [0x00024] (at /home/andrew/cvs/beagle/Tiles/TileCanvas.cs:45) Beagle.Tile.TileCanvas:.ctor ()
in [0x000f9] (at /home/andrew/cvs/beagle/Best/BestWindow.cs:356) Best.BestWindow:CreateContents ()
in [0x00052] (at /home/andrew/cvs/beagle/Best/BestWindow.cs:88) Best.BestWindow:CreateWindow (string)
in [0x00033] (at /home/andrew/cvs/beagle/Best/BestWindow.cs:62) Best.BestWindow:.ctor ()
in [0x00065] (at /home/andrew/cvs/beagle/Best/Best.cs:111) Best.Best:Main (string[])


any thoughts?

---

### Post by rlcoach on 2005-05-04
I followed the install notes and it worked fine. However now I have gotten it working I would really like to make best use of inotify and wondered if anyone knew how easy it would be to patch the Kernel for inotify 0.22?

---

### Post by supernaut on 2005-05-04
No PPC packages. :(

---

### Post by risager on 2005-05-04
Will this break tomboy, f-spot?

---

### Post by henriquemaia on 2005-05-04
Two thanks in one:

Thanks for Beagle.
Thanks for OOo 2.

Both HowTo worked great!

---

### Post by Heliode on 2005-05-04
Hey! Thanks for the howto, now I finally got beagle working! Since the release of OSX Tiger i've seen a lot more interest in beagle.

However, i've found beagle screenshots around like [this one](http://www.novell.com/products/linuxprofessional/img/screenshots/beagle.png) , and that isn't exactly what i'm getting; it seems to group results by category, while for me it just shows all results by date.  Is that a newer version or anything?
Also, are there plugins so it also support the .doc format or anything like that? That would help out alot since I have all my school stuff in .doc.

Beagle is still really great though! Its ability to let you search chat logs alone makes it worth it!

---

### Post by sebgate20 on 2005-05-04
[QUOTE=Heliode]Hey! Thanks for the howto, now I finally got beagle working! Since the release of OSX Tiger i've seen a lot more interest in beagle.

However, i've found beagle screenshots around like [this one](http://www.novell.com/products/linuxprofessional/img/screenshots/beagle.png) , and that isn't exactly what i'm getting; it seems to group results by category, while for me it just shows all results by date.  Is that a newer version or anything?
Also, are there plugins so it also support the .doc format or anything like that? That would help out alot since I have all my school stuff in .doc.

Beagle is still really great though! Its ability to let you search chat logs alone makes it worth it![/QUOTE]
 That is a very old version of Beagle (0.0.7?) whereas 0.0.9 has a newer, easier to use Best interface. Look at my screenshots here on how it should look:

[http://www.sebgate.f2s.com/shots/love.png](http://www.sebgate.f2s.com/shots/love.png)
[http://www.sebgate.f2s.com/shots/loveweb.png](http://www.sebgate.f2s.com/shots/loveweb.png)
[http://www.sebgate.f2s.com/shots/clamav.png](http://www.sebgate.f2s.com/shots/clamav.png)

Seb

---

### Post by Heliode on 2005-05-04
hmm ok... the screenshots you posted are indeed what I am getting. The screenshot I posted just looked more... how do you say... complete to me. But that just might be me talking funny  :roll: 

How long does it generally take for beagle to have indexed new files? And does it index files only in the users home directory? If so, does it search in all the folders and sub-folders therein? Also, how exact does a keyword have to match something to get a result? Does it need to be somewhat similar, or does it have to be exact and case sensitive? I added a bunch of pictures from a Windows partition to my home dir, but they didn't show up in Best at all, even when searching for the complete file name. Any thoughts?

Also, I understand that it searches on 'meta-data', but what more can it get from things like pictures and music than its file name? In other worlds, what sets it apart from programs like, say, Slocate in that sense?

Also, being able to search .doc files would be great  :wink: . Are there even such things as plugins for beagle?

I still think Beagle is/will be a great app. I've heard mac-people saying Spotlight changed everything for them, and I suspect that in time, Beagle will do the same for us. Even before MS rips off^H^H^H^H implements their own version of it in Longhorn.

---

### Post by Heliode on 2005-05-04
Just a little update:

I've looked into it a bit, and it actually does include .doc files. The problem is, though, that it doesn't seem to find all my files. There are a bunch of files in my homedir, which can all be found with Best. There's a ~/Docs dir which is also searched, but there is also a ~/Pics dir with lots and lots of pictures in it. Only some of those can be found with Best. 

It does seem to work more than fine with indexing webpages and finding stuff in IM logs though. 

Anyone have any idea what might be wrong here?

---

### Post by nehalem on 2005-05-05
Well I installed it.  Here are some things I noticed:

Memory consumption is pretty high.  Between best and beagle it's a pretty big dent.  This is probably due to it's beta status.

I can search files and have no idea why.  I can get webpages, blogs from bam, tomboy notes, but have pulled up anything else.

It still feels pretty immature.

That said it's a pretty cool little tech demo, can't wait until it come out.

---

### Post by SKLP on 2005-05-05
From the wiki
> Q: Can't it depend on mozilla | firefox then?
Yes, (I think) this can be accomplished by adding ```
--with-mozilla=firefox
``` to the ./configure line.

---

### Post by harryc on 2005-05-07
Should Tomboy be installed before or after Beagle? It requires some mono packages.

---

### Post by crun on 2005-05-07
Anyone know how to solve the following problem? At the moment, Beagle only indexes your home dir. I have all my long-term data stored on a sperate HD. I've set up fstab to allow this HD to be indexed (it's hdb1):

```
proc            /proc    proc    defaults        0       0
/dev/hda1/      ext3     defaults,errors=remount-ro,user_xattr 0 1
/dev/hda5       /proc    proc    defaults        0       0
/dev/hda1/      ext3     defaults,errors=remount-ro,user_xattr 0 1
/dev/hda5       nonone    swap    sw              0       0
/dev/hdb1       /home/crun/Desktop/data           ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

```

I've set the mount point for this drive inside my Desktop folder, and at first, Beagle indeed started indexing files from it. Then after a reboot, all the files were gone from the index, and since then the Beagle deamon hasn't touched it.

I believe they're working on a config utility for Best that allows you to specify other directories, but at the moment I'm stuck.

---

### Post by harryc on 2005-05-08
I installed Beagle using the wiki instructions to the letter. It left me with Mono 1.0.5-1. I thought the latest version was 1.1.6? How do I get the latest Mono?

---

### Post by Eatingdogs on 2005-05-09
It seems that these mono packages have been moved out of hoary-backports-staging to hoary-backports . Edit your apt repositories to reflect this. I had the same problem, but it works fine now.

---

### Post by harryc on 2005-05-09
[QUOTE=Eatingdogs]It seems that these mono packages have been moved out of hoary-backports-staging to hoary-backports . Edit your apt repositories to reflect this. I had the same problem, but it works fine now.[/QUOTE]Thanks, that got it sorted out.

---

### Post by harryc on 2005-05-16
Does anyone notice 100% CPU utilization after running Beagle for a couple of days? TOP shows mono is the cause. If I delete the .beagle folder in my home directory it works again for a couple of days. Then one day on boot it will peg the CPU again. Killing Beagle does not make the 100% utilization go away.

---

### Post by ericsp on 2005-05-18
I followed the instructions at [http://www.ubuntulinux.org/wiki/BeagleInstallHowto](http://www.ubuntulinux.org/wiki/BeagleInstallHowto) but Beagle cannot be found anymore. Any idea where it has gone?

Eric

---

### Post by Majlo on 2005-05-18
[QUOTE=ericsp]I followed the instructions at [http://www.ubuntulinux.org/wiki/BeagleInstallHowto](http://www.ubuntulinux.org/wiki/BeagleInstallHowto) but Beagle cannot be found anymore. Any idea where it has gone?

Eric[/QUOTE]

Try this [http://www.ubuntulinux.org/wiki/HoaryBeagleInstallHowto](http://www.ubuntulinux.org/wiki/HoaryBeagleInstallHowto)
This is for Hoary

---

### Post by infinito on 2005-05-18
That's what I did to get Beagle 0.0.9 and Mono 1.1.7 up and tunning on my Hoary

(1) Add **extended attributes** to / on **/etc/fstab**
```
Old -> /dev/hde6   /   ext3   defaults,errors=remount-ro   0   1
New -> /dev/hde6   /   ext3   defaults,errors=remount-ro,user_xattr   0   1
```
(2) Add **Backports** repositories to **/etc/apt/sources.list**
```
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras-staging main universe multiverse restricted
```
(3) Install needed **packages** (I know there're too many packages, but Beagle needs a lot of dev dependencies...)
```
$ sudo apt-get install beagle gtk-doc-tools gtk-sharp-gapi \
libdbus-cil libevolution-cil libgconf2-dev libgconf-cil \
libgcrypt11-dev libgecko-cil libglade-cil libglib-cil libgmime-cil \
libgnome-cil libgnomevfs2-dev libgnutls11-dev libgpg-error-dev \
libgsf-cil libgtk-cil libgtksourceview-cil libidl-dev libmono0 \
libopencdk8-dev liborbit2-dev libpopt-dev libtasn1-2-dev mono \
mono-assemblies-arch mono-assemblies-base mono-common mono-gac \
mono-jit mono-mcs mono-utils sqlite indent libbonobo2-dev \
comerr-dev libart-2.0-dev libaudiofile-dev libbonoboui2-dev \
libcamel1.2-dev libebook1.2-dev libedataserver1.2-dev libesd0-dev \
libgnome-keyring-dev libgnome2-dev libgnomecanvas2-dev libgnomeui-dev \
libjpeg62-dev libkadm55 libkrb5-dev libnspr-dev
```
(4) **Link some libs** no linked correctly(because it was giving me problems...)
```
$ sudo ln -s /usr/lib/libMonoPosixHelper.so.0 /usr/lib/libMonoPosixHelper.so
$ sudo ln -s /usr/lib/libebook-1.2.so /usr/lib/libebook-1.2.so.0
```
(5) Run **Beagle daemon**
```
$ beagled
```
(6) Run **search tool**
```
$ best
```
(7) If everythings works fine, maybe you should **add both daemon and search tool to your gnome-session**, so they load when you login to Gnome
```
System -> Preferences -> Sessions
* Startup Programs -> Add: Startup Command [beagled] / Order: [50]
* Startup Programs -> Add: Startup Command [best   ] / Order: [50]
```
That's all, and everything is working perfect!

-- infinito

---

### Post by arnieboy on 2005-06-15
for some weird reason, i cannot make beagle index my mail.. that way I dont see any results when i search for mail items on Best. I use thunderbird mail client. Does anybody know of any workaround?

---

### Post by lizardking on 2005-06-15
[QUOTE=infinito]
(2) Add **Backports** repositories to **/etc/apt/sources.list**
```
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras-staging main universe multiverse restricted
```[/QUOTE]
**Are this repository url just?**  ](*,)
```
Impossibile ottenere http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz  401 Authorization Required
```

---

### Post by Majlo on 2005-06-15
[QUOTE=arnieboy]for some weird reason, i cannot make beagle index my mail.. that way I dont see any results when i search for mail items on Best. I use thunderbird mail client. Does anybody know of any workaround?[/QUOTE]

Beagle search mail only in Evolution ..

---

### Post by arnieboy on 2005-06-15
aah.. ok.. no wonder it wasnt searching on thunderbird. Thanks anyway

---

### Post by lizardking on 2005-06-16
[QUOTE=infinito]That's what I did to get Beagle 0.0.9 and Mono 1.1.7 up and tunning on my Hoary

(1) Add **extended attributes** to / on **/etc/fstab**
```
Old -> /dev/hde6   /   ext3   defaults,errors=remount-ro   0   1
New -> /dev/hde6   /   ext3   defaults,errors=remount-ro,user_xattr   0   1
```
(2) Add **Backports** repositories to **/etc/apt/sources.list**
```
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras-staging main universe multiverse restricted
```
(3) Install needed **packages** (I know there're too many packages, but Beagle needs a lot of dev dependencies...)
```
$ sudo apt-get install beagle gtk-doc-tools gtk-sharp-gapi \
libdbus-cil libevolution-cil libgconf2-dev libgconf-cil \
libgcrypt11-dev libgecko-cil libglade-cil libglib-cil libgmime-cil \
libgnome-cil libgnomevfs2-dev libgnutls11-dev libgpg-error-dev \
libgsf-cil libgtk-cil libgtksourceview-cil libidl-dev libmono0 \
libopencdk8-dev liborbit2-dev libpopt-dev libtasn1-2-dev mono \
mono-assemblies-arch mono-assemblies-base mono-common mono-gac \
mono-jit mono-mcs mono-utils sqlite indent libbonobo2-dev \
comerr-dev libart-2.0-dev libaudiofile-dev libbonoboui2-dev \
libcamel1.2-dev libebook1.2-dev libedataserver1.2-dev libesd0-dev \
libgnome-keyring-dev libgnome2-dev libgnomecanvas2-dev libgnomeui-dev \
libjpeg62-dev libkadm55 libkrb5-dev libnspr-dev
```
(4) **Link some libs** no linked correctly(because it was giving me problems...)
```
$ sudo ln -s /usr/lib/libMonoPosixHelper.so.0 /usr/lib/libMonoPosixHelper.so
$ sudo ln -s /usr/lib/libebook-1.2.so /usr/lib/libebook-1.2.so.0
```
(5) Run **Beagle daemon**
```
$ beagled
```
(6) Run **search tool**
```
$ best
```
(7) If everythings works fine, maybe you should **add both daemon and search tool to your gnome-session**, so they load when you login to Gnome
```
System -> Preferences -> Sessions
* Startup Programs -> Add: Startup Command [beagled] / Order: [50]
* Startup Programs -> Add: Startup Command [best   ] / Order: [50]
```
That's all, and everything is working perfect!

-- infinito[/QUOTE]
Doen not Wok for me...Best and beagled are up but if i find some document I see always **No Results..always**

---

### Post by Labonte on 2005-06-16
[QUOTE=lizardking]**Are this repository url just?**  ](*,)
```
Impossibile ottenere http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz  401 Authorization Required
```[/QUOTE]


yes i'm getting the same 401 error here.. :(

---

### Post by foxy123 on 2005-06-18
does it index fat32 partitions?

---

### Post by netrattler on 2005-06-21
Figured out my problem.

---

### Post by arnieboy on 2005-06-22
I removed beagle today.. These guys need to work a lot on the code before I install it again. All it was indexing were some inconsequential webpages.

---

### Post by kiddo on 2005-07-20
Hello there, using Beagle 0.0.11 and Mono 1.1.7.x from the hoary backports. I've managed to run Beagle fine (after installing about a hundred packages for dependencies!), however there is now tomboy broken, and it cannot be upgraded, so maybe you can shed some light on this. You can load tomboy on the panel and popup the menu, but when you click to open a note, it outputs this in the terminal:
```
** (Tomboy:11215): WARNING **: Missing method .ctor in assembly /usr/lib/mono/ga c/gtk-sharp/1.0.0.0__35e10195dab3c99f/gtk-sharp.dll, type Value

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> 
in <0x00058> Tomboy.NoteWindow:MakeToolbar ()
in <0x0009e> Tomboy.NoteWindow:.ctor (Tomboy.Note note)
in <0x0002b> Tomboy.Note:get_Window ()
in <0x00070> Tomboy.TomboyTray:ShowNote (System.Object sender, System.EventArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventAr gs (object,System.EventArgs)
in <0x000bb> GtkSharp.voidObjectSignal:voidObjectCallback (IntPtr arg0, Int32 ke y)
in (wrapper native-to-managed) GtkSharp.voidObjectSignal:voidObjectCallback (int ptr,int)
in <0x00000> 
in (wrapper managed-to-native) PanelApplet.AppletFactory:panel_applet_factory_ma in (string,intptr,PanelAppletSharp.FactoryCallbackNative,intptr)
in <0x00138> PanelApplet.AppletFactory:Register (System.Type applet_type)
in <0x0000c> Tomboy.Tomboy:RegisterPanelAppletFactory ()
in <0x000d8> Tomboy.Tomboy:Main (System.String[] args)
``` 

It does not make a difference whether beagled & best have been started or not, so I suspect mono being the culprit. But why does a newer version of the framework mess up entirely an application such as tomboy? :-|


Edit: hey actually that **might** be the problem, I've been to tomboy's website see the changelog for version 0.3.> Version 0.3.2
* Support building under Mono 1.1.x.
Do you think this might be the cause? If so, how could I tell the backport guys to get a newer tomboy?

---

### Post by Riggs on 2005-09-25
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono-assemblies-arch: Depends: mono-assemblies-base-1.1.7 but it is not installable
  mono-jit: Depends: mono-assemblies-base-1.1.7 but it is not installable
E: Broken packages



This is what I get....not sure what's going on.

---

### Post by delsdog on 2005-09-25
I'm getting the same error as Riggs above on a completely new install, I had everything working on my previous setup, just haven't a clue how I did it then and can't now.

---

### Post by awtomlinson on 2005-09-25
This is off topic, so I apologize.  Beagle runs fine on my Hoary system.  I installed from the official Bealge wiki.  My question is, since Beagle is built in to Breezy, when I upgrade to Breezy, will this cause any issues for the current Beagle install?  Should I uninstall all packages required from the Beagle wiki?  How about for Dashboard?  Does Breezy include Dashboard?

---

### Post by awtomlinson on 2005-09-25
This is off topic, so I apologize.  Beagle runs fine on my Hoary system.  I installed from the official Beagle wiki.  My question is, since Beagle is built in to Breezy, when I upgrade to Breezy, will this cause any issues for the current Beagle install?  Should I uninstall all packages required from the Beagle wiki?  How about for Dashboard?  Does Breezy include Dashboard?

---

