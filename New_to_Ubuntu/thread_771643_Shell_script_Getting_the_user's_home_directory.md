---
title: "Shell script: Getting the user's home directory?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-04-27
I'm learning how to create a debian package installer.

I've got pretty much everything working okay so far but one thing remains.

When the .deb runs, it runs a file called postint which contains a shell script, which performs actions immediately after file installation.

In that script, I'm trying to create a Desktop link to the executable I have had the .deb place inside /usr/bin

The executable is called fishpants-app 

```


#!/bin/sh

echo "listing any fish-related files in /usr/bin"
ls /usr/bin/fish*
echo "okay, now creating link"
ln -s /usr/bin/fishpants-app $HOME/Desktop/fishpants-launcher -v
echo "that should be done now. ending."


```

Now, when it all runs, the message comes back, that it has created the shortcut just fine, but on root's Desktop:

```


Selecting previously deselected package fishpants.
(Reading database ... 101779 files and directories currently installed.)
Unpacking fishpants (from .../user/Desktop/fishpants.deb) ...
Setting up fishpants (0.5) ...
listing any fish-related files in /usr/bin
/usr/bin/fishpants-app
okay, now creating link
`/root/Desktop/fishpants-launcher' -> `/usr/bin/fishpants-app'
that should be done now. ending.


```

I want it to create the shortcut on user's Desktop, not root's (i.e. the user who invoked the .deb gets the shortcut)

Bit foxed as to how to proceed.. any ideas?

---

### Post by Vadi on 2008-04-27
I don't know how to get that, but I'd recommend against placing an icon on the desktop, because it pretty much goes against the standard. Better to put it somewhere in 'Applications'.

---

### Post by ChameleonDave on 2008-04-27
> **ecs_pf5 said:**
> 

I want it to create the shortcut on user's Desktop, not root's (i.e. the user who invoked the .deb gets the shortcut)


The user who invoked the .deb is root, via kdesudo or whatever.  You want the installer to know what user is logged into the graphical desktop while root does its thing?  Well, it's probably best not even to assume that any user is logged in like that.  Software can easily be installed via a root tty, for example.

Windows can put an icon on your desktop of course (and frequently does, annoyingly), but that's because there are multiple superusers, all normally logging in to the graphical desktop.

I really think you're trying to emulate slightly annoying Windows behaviour here.  If it is absolutely necessary for an app to advertise itself on the desktop (which feels almost like spam!), then this can happen the first time the app is run by a user, rather than on installation.

---

### Post by master5o1 on 2008-04-27
Why even write a installer script when we already have gdebi as an installer?

Although, this can be of some use but it makes more sense to add it to the Applications > xxx menu and then let the user drag the menu link over.

---

### Post by master5o1 on 2008-04-27
Why even write a installer script when we already have gdebi as an installer?

Although, this can be of some use but it makes more sense to add it to the Applications > xxx menu and then let the user drag the menu link over.

---

### Post by ecs_pf5 on 2008-04-27
Not a problem guys, after years of Windows use your brain gets to work a certain way & it's hard to get out of that way of thinking :)

Better to put it somewhere in 'Applications'... that sounds like a fine plan, if you have any pointers where to start looking into that it'd be great.

---

### Post by Bodsda on 2008-04-27
```
user=$(whoami)
```
will tell you the users name then youcan use like 
```
/home/$user/Desktop
```
but if the program is run with sudo im not sure if it will get the right name,.,.it might do but not sure

---

### Post by scragar on 2008-04-27
erm... try:

```
user=$(whoami)

home = cat /etc/passwd | grep $user | grep -o \\/home[^:]*

echo $home/Desktop/...
```

---

### Post by ecs_pf5 on 2008-04-27
Thanks for the reply Bodsda, tried it out out of interest but it returned 'root' from inside the running installer. Worth a shot although, I think I'm now forgetting the plan of icon-on-users-desktop & going with, add to the normal applications menu.

Haven't a clue where to start with that though either :lolflag:

I am currently on Kubuntu using the K menu..

---

### Post by Bodsda on 2008-04-27
having said that i believe 

```
$HOME
```
is already set

```
$HOME/Desktop
```

---

### Post by master5o1 on 2008-04-27
sudo whoami returns root.

---

### Post by scragar on 2008-04-27
most users install programs from either their home Dir's or the desktop, you could check for either of those as the current dir, and go from there.

---

### Post by master5o1 on 2008-04-27
```

jason@meinDell:~$ happy=$(ls /home)
jason@meinDell:~$ echo $happy
jason lost+found

```

So, if you can split $happy into separate vars and kick out lost+found from our list then it is possible to get the home dirs of each user...

---

### Post by ecs_pf5 on 2008-04-27
Isn't it always going to end up being root though, because it's always root that's running the script inside the .deb no matter who starts it off? (might be wrong)

happy with just a link in the main KDE or Gnome menu tbh, it seems more sensible like that, if I can figure it out.

I'm wondering whether this is the right place to be:

[http://www.debian.org/doc/packaging-manuals/menu.html/ch1.html](http://www.debian.org/doc/packaging-manuals/menu.html/ch1.html)

---

### Post by Vadi on 2008-04-27
Yeah, someone help him get it into the menu, that's a much better place.

This should be moved to programming talk though

---

### Post by master5o1 on 2008-04-27
ecs_pf5, That's why I realise that you cannot use $HOME like variables.

~ = $HOME = /home/`whoami` = ...

But where they invoke it can be used, I suppose.

---

### Post by ecs_pf5 on 2008-04-27
I'm wondering about dh_installmenu now having taken amor to bits.

Picked on amor for no other reason than it looked like a smallish .deb that did create a menu item, and I figured if I opened it up it might show some hints on how it inserts it's listing into the main menu. 

This is from it's /control/postinst script (the one that runs immediately after file payload unpacking, during package install):

```

#!/bin/sh
set -e
# Automatically added by dh_installmenu
if [ "$1" = "configure" ] && [ -x "`which update-menus 2>/dev/null`" ]; then
    update-menus
fi

```Inside it's unpacked folder tree payload, there is:

/data/usr/share/menu/amor

which seems to be a text file configuring menu items:

```

?package(amor):\
    needs="x11"\
    section="Games/Toys"\
    hints="KDE"\
    title="AMOR"\
    longtitle="AMOR (Amusing Misuse of Resources)"\
    icon="/usr/share/pixmaps/amor.xpm"\
    command="/usr/bin/amor"

```Then there's a couple of directories of images:

/data/usr/share/pixmaps/amor.xpm --------> that looks like the menu icon

/data/usr/share/icons/hicolor/ --------> few more icons grouped by size in 4 subfolders, not sure they're menu related though

Looking at:

[http://packages.debian.org/lenny/debhelper](http://packages.debian.org/lenny/debhelper)

As far as I can gather so far, one needs a file called 'rules' located in the /package_build_directory (not inside the /package_build_directory/DEBIAN directory, but beside it, directly inside package_build_directory - which seems to be referred to throughout the debian documentation as lower case /debian/ )

i.e. a package build structure something like

/BuildDirectory/DEBIAN/control
/BuildDirectory/DEBIAN/postinst
/BuildDirectory/DEBIAN/prerm
/BuildDirectory/usr/bin/my-executable-file
/BuildDirectory/rules ----------------------------------------> ???

.. and then, one calls debhelper programs directly within the rules file. so you call dh_installmenu in there, and somehow it configures the package to include menu items. Hopefully in some kind of system independent manner.

As yet, haven't got to grips with the detail.. not sure which files and resources you have to manually supply and which are automatically generated, and not too sure of the syntax for the dh_installmenu entry in the rules file.. The documentation is not sparse but it is, quite confusing to a newcomer from Windows-land.

There's no evidence of a rules file in amor's .deb, I guess it gets ditched by dpkg once it's done it's job. Once the debhelper package is installed though, it does contain some (confusing looking) example rules files in /usr/share/doc/debhelper/examples/

I don't know about update-menus, it doesn't seem to be on my system even after installing debhelper and dpkg-dev (maybe it isn't needed on Kubuntu/Ubuntu?) - edit - wasn't on my system, apt-get install menu fixed that

Now having *limited* success. Did manage to coax my .deb into placing a link on the K menu, however it's very shaky, the main category seemed to be taken from the old install of amor (now removed) whilst the actual link item itself did list & point to my own app. So this is on the right lines but I've got the structure & syntax messed up.

I had to shove dh_installmenu way up high in the rules file before it worked, up above all the other stuff (I am just using the simplest example file out of the debhelper examples directory)

-?-

---

### Post by ecs_pf5 on 2008-04-29
Well I got it working.. after a fashion

I read and read and read and played the old insomniac trick.. 

The way to do it seemed to be, to build the debian package using a menu file in {build directory}/usr/share/menu/ a la:

```

?package(packagename):\
    needs="x11"\
    section="Development"\ <-- say, if you want it in the 'Development' main menu
    title="Packagename"\
    longtitle="Packagename (experiment)"\
    icon="/usr/share/pixmaps/packagename.xpm"\
    command="/usr/bin/packagename-executable"

```, then call 'update-menus' in the postinst and postrm scripts

however despite reading all the documentation I could find, and rebuilding the package numerous times, it never worked. I really did try and try but the debian package-building documentation just doesn't seem to work (clearly I'm doing something wrong somewhere, 4 or 5 tutorials can't all be wrong!)

Seems to be a couple of different package-building approaches that somewhat conflict in their details, varying in complexity level.. I got the packages to build okay but never, insert a menu item.

-------

Then in the end I found that if you make a 'Desktop Config File' with the right details in it using vi / kate / whatever:

```

[Desktop Entry]
Categories=GTK;Development;    <--- this seems to specify the menu link location
Comment=Get menus working
Comment[en_GB]=Get menus working
Exec[$e]=packagename
GenericName=An experiment
GenericName[en_GB]=An experiment
Icon=packagename
MimeType=
Name=Packagename
Name[en_GB]=Packagename
Path[$e]=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
Version=1.0
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=


```.. and put it in the build folder as {build folder}/usr/share/applications/kde/packagename.desktop

.. and supply a set of icons in {build folder}/usr/share/icons/hicolor/16x16/apps/

(and the corresponding 22x22, 32x32, 48x48 dirs)

.. and then build the package using

sudo dpkg -b {build folder} {packagename.deb}

hey presto - a package that installs, places a link in the proper place in the main menu, and then uninstalls completely via adept.

-----------

Wish I could find the trick to getting the /usr/share/menu/<packagename> menu-file method working though, because that seems to be the proper way to do it, and I guess would stand more chance of working properly across different systems?






Sorry that this has gone on a tangent regards coding, is it possible a mod can move the thread to the programming section?

---

