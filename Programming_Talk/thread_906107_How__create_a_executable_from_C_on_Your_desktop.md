---
title: "How  create a executable from C on Your desktop"
date: 2008-08-31
forum: Programming Talk
---

### Post by Windy Peaks on 2008-08-31
Ladies and Gentlemen of the forum:

I have written a few small programs in C, and I already know how to run them in the terminal window, but how do I create a desktop short cut that will let me run in from the desktop???

I have heard it has something to do with the switch settings I use when I compile them but not quite sure ??

Does anyone know ???

Thanks in advance
Windy

---

### Post by mike_g on 2008-08-31
In GNOME or XFCE You could create a launcher to run your program. Thats what I did and it works well; effectively a short cut.

---

### Post by jespdj on 2008-08-31
Right-click the desktop and select "Create Launcher..." from the popup menu.

---

### Post by Rany Albeg on 2008-08-31
Also you need to type in the 'command: ' line that will be opened,
the same command you type if you wish to run this application  through the command prompt.

HAVE A NICE DAY :D

---

### Post by mssever on 2008-09-01
Those launchers are also called .desktop files. If you want more control than you can get via the above methods, you can open up the .desktop file and edit it directly. Note that you must open it from the command line, since Nautilus will not allow you to edit .desktop files directly. There are many examples in /usr/share/applications. Also, there's a spec on freedesktop.org.

---

### Post by LaRoza on 2008-09-01
> **mssever said:**
> Those launchers are also called .desktop files. If you want more control than you can get via the above methods, you can open up the .desktop file and edit it directly. Note that you must open it from the command line, since Nautilus will not allow you to edit .desktop files directly. There are many examples in /usr/share/applications. Also, there's a spec on freedesktop.org.

Or use another file browser.

---

### Post by jinksys on 2008-09-01
I'll assume you are using Ubuntu and not a derivative like kubuntu, xubuntu, etc.

As the others have mentioned, simply right click your desktop and create a launcher (gnomespeak for shortcut).  If your app doesn't have a GUI then you'll need to have a terminal run your app.  It's simple, here is an example: 

[img]http://i38.tinypic.com/30bnuo8.png[/img]

Replace mycommand with the command you wish to run.

On the other hand, if your app 100% gui then you can disregard this :)

Good Luck!

---

### Post by mssever on 2008-09-01
> **LaRoza said:**
> Or use another file browser.
Are there really people who live outside the Gnome universe? :)

<off-topic>With Dolphin, it appears that the KDE folks finally have a halfway-decent file browser.</off-topic>

---

### Post by LaRoza on 2008-09-01
> **mssever said:**
> Are there really people who live outside the Gnome universe? :)

<off-topic>With Dolphin, it appears that the KDE folks finally have a halfway-decent file browser.</off-topic>

I don't use GNOME (xmonad).

I use mc and Thunar (sometimes, pcmanfm, but I don't have that installed at the moment).

---

### Post by -grubby on 2008-09-01
> **mssever said:**
> Are there really people who live outside the Gnome universe? :)


Quite a few. /me personally can't stand nautilus

---

### Post by mssever on 2008-09-01
> **mssever said:**
> Are there really people who live outside the Gnome universe? :)
Just to avoid any misunderstanding, this was intended as a joke, since I knew that LaRoza used a less-common WM.

I actually only use a file manager for a few specific tasks (for which Nautilus is sufficient). I usually use straight bash, which is much faster.

---

### Post by LaRoza on 2008-09-01
> **mssever said:**
> Just to avoid any misunderstanding, this was intended as a joke, since I knew that LaRoza used a less-common WM.

I actually only use a file manager for a few specific tasks (for which Nautilus is sufficient). I usually use straight bash, which is much faster.

It is common, in fact, xmonad is more common than GNOME. GNOME only runs when I first install, and xmonad runs after. So xmonad is much more common than GNOME.

I use the shell also for most things.

---

### Post by jinksys on 2008-09-01
> **mssever said:**
> Are there really people who live outside the Gnome universe? :)

Plenty of people, myself included.  Unfortunately I had to learn to tolerate gnome and its hand holding since Ubuntu doesn't have a quality KDE equivalent.

---

### Post by CptPicard on 2008-09-01
> **jinksys said:**
> Unfortunately I had to learn to tolerate gnome and its hand holding since Ubuntu doesn't have a quality KDE equivalent.

I've run Kubuntu since Dapper when I first came to (Some)buntu, and it's worked great. KDE 4.1 is still a buggy mess though, but that's not Kubuntu's fault.

---

### Post by jinksys on 2008-09-01
> **CptPicard said:**
> I've run Kubuntu since Dapper when I first came to (Some)buntu, and it's worked great. KDE 4.1 is still a buggy mess though, but that's not Kubuntu's fault.

It's crap.  Compared OpenSuSE and PCLinuxOS, Kubuntu is a mess.  Kubuntu just doesn't get the attention it needs from Canonical.

---

### Post by mssever on 2008-09-01
> **CptPicard said:**
> I've run Kubuntu since Dapper when I first came to (Some)buntu, and it's worked great. KDE 4.1 is still a buggy mess though, but that's not Kubuntu's fault.I recently started messing with VirtualBox, which has freed me to explore other distros. So I tried the KDE4 version of Kubuntu Hardy and found it to be much slower and crashier than an equivalent Ubuntu VM install. I've heard that Kubuntu isn't the best KDE distro. Bugs aside, KDE4 does seem to be quite an improvement. When the bugs get fixed, I might seriously consider using KDE (though I've been using Gnome for so long that I'm really used to it, and that counts for quite a bit, IMO).

---

### Post by CptPicard on 2008-09-01
> **mssever said:**
> So I tried the KDE4 version of Kubuntu Hardy and found it to be much slower and crashier than an equivalent Ubuntu VM install.

KDE4 is still very much "beta" no matter what they say... it's a disgrace really that it's been let out of the door in the state it is in and be called a "release". I can't even get plasma to run without  crashing outright in 4.1... but 3.5.9 is very solid and I really don't see what Kubuntu should do differently, as I have no complaints whatsoever (after all, Kubuntu is just the underlying Ubuntu plus the kubuntu-desktop KDE packages) :)

---

### Post by LaRoza on 2008-09-01
> **jinksys said:**
> Plenty of people, myself included.  Unfortunately I had to learn to tolerate gnome and its hand holding since Ubuntu doesn't have a quality KDE equivalent.

Install KDE on Ubuntu (sudo aptitude install kde-core).

You'll be able to choose what DE to use, and you can use all the apps in the other.

---

### Post by jinksys on 2008-09-01
> **LaRoza said:**
> Install KDE on Ubuntu (sudo aptitude install kde-core).

You'll be able to choose what DE to use, and you can use all the apps in the other.

Thanks, but I know how to install packages.
Moreover, I just said that Ubuntu's KDE (IMHO) stinks, why would I want to install it? :confused:

---

### Post by LaRoza on 2008-09-01
> **jinksys said:**
> Thanks, but I know how to install packages.

Sorry, the kde-core package is not the kubuntu package. It is lighter and less altered.

> 
Moreover, I just said that Ubuntu's KDE (IMHO) stinks, why would I want to install it? :confused:
Because now it will be KDE on Ubuntu instead of a KDE Ubuntu version?

---

### Post by jinksys on 2008-09-01
> **jinksys]Thanks, but I know how to install packages.[/QUOTE]
[QUOTE=LaRoza said:**
> Sorry, the kde-core package is not the kubuntu package. It is lighter and less altered.

My above post may seem cynical, that was unintentional.

My issue with Kubuntu is that they haven't touched it enough.  It seems they took a vanilla distro, installed vanilla KDE, added a bootsplash and released it.  Ubuntu feels tight and integrated, Kubuntu feels klunky and ignored.  I personally think Gnome was a good choice for Ubuntu, since it tends to be a newbie distro.

---

### Post by CptPicard on 2008-09-01
> **jinksys said:**
> Ubuntu feels tight and integrated, Kubuntu feels klunky and ignored.  I personally think Gnome was a good choice for Ubuntu, since it tends to be a newbie distro.

Well, I'm not a noob, so I am actually pretty glad that they haven't introduced some weird distro-specific integration that gets in the way of my own customization :)

---

### Post by LaRoza on 2008-09-01
> **jinksys said:**
> 
My issue with Kubuntu is that they haven't touched it enough.  It seems they took a vanilla distro, installed vanilla KDE, added a bootsplash and released it.  Ubuntu feels tight and integrated, Kubuntu feels klunky and ignored.  I personally think Gnome was a good choice for Ubuntu, since it tends to be a newbie distro.

Oh, I see.

I had the complete opposite view :-) I think distros shouldn't mess with the packages (vanilla is the best). That is why I recommended kde-core, because it is not excessively altered.

---

### Post by LaRoza on 2008-09-01
> **CptPicard said:**
> Well, I'm not a noob, so I am actually pretty glad that they haven't introduced some weird distro-specific integration that gets in the way of my own customization :)

Doesn't matter, KDE and GNOME are the same type of DE anyway. Just like Windows and OS X.

If you are going to use KDE or GNOME (or Xfce), you might as well use Windows. :)

---

### Post by jinksys on 2008-09-01
> **CptPicard said:**
> Well, I'm not a noob, so I am actually pretty glad that they haven't introduced some weird distro-specific integration that gets in the way of my own customization :)
 
Well I use Ubuntu and I've been using Linux for ten years, my first distro was a TurboLinux boxset I bought at BestBuy.  I think one of Ubuntu's greatest attributes is that it (usually) just works, and yet is powerful enough for experienced users.

---

### Post by LaRoza on 2008-09-01
> **jinksys said:**
> Well I use Ubuntu and I've been using Linux for ten years, my first distro was a TurboLinux boxset I bought at BestBuy.  I think one of Ubuntu's greatest attributes is that it (usually) just works, and yet is powerful enough for experienced users.

Well, I've been using computers for almost 2 years. 

My first distro was Ubuntu 6.06 which I got in a book on sale at Borders and I randomly bought (not sure why, perhaps God's grace)

I've continued to use Ubuntu (albeit, heavily altered) because I am used to it, although I find other distros more suitable.

---

### Post by CptPicard on 2008-09-01
> **jinksys said:**
> Well I use Ubuntu and I've been using Linux for ten years, my first distro was a TurboLinux boxset I bought at BestBuy.  I think one of Ubuntu's greatest attributes is that it (usually) just works, and yet is powerful enough for experienced users.

Mine was Slackware 3.4 that was installed from a set of floppies -- downloading them over modem from a BBS was slow! :)

Yes, the reason why I migrated from Gentoo is that all the fixing of under the hood stuff was getting tiresome. But I still personally feel that all the "just works" stuff that is not DE-specific in Ubuntu works fine in Kubuntu, and the non-tweaked KDE just gets tweaked to what I want it to be over time as I use it...

---

### Post by jinksys on 2008-09-01
> **LaRoza said:**
> Well, I've been using computers for almost 2 years. 


Wow, you must be young.

---

### Post by LaRoza on 2008-09-01
> **jinksys said:**
> Wow, you must be young.

I am younger than people older than me, and older than people younger than me.

I am always "my age", neither young nor old.

My age is no secret on the forum, and I leave it to you to find it :-) (in fact, googling my name would get you the entire story...)

---

### Post by mssever on 2008-09-01
> **LaRoza said:**
> My first distro was Ubuntu 6.06 which I got in a book on sale at Borders and I randomly bought (not sure why, perhaps God's grace)
Dapper was my introduction to Ubuntu, as well, but it wasn't my introduction to Linux. My first encounter with *nix was the shell account that my school provided for e-mail purposes, and which I exploited for much more than just e-mail. My first install was Debian Unstable back in 1999. Later, I ran Red Hat 7.3, and now I'm very happy with Ubuntu.

---

