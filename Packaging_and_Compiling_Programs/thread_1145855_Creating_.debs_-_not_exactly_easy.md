---
title: "Creating .debs - not exactly easy"
date: 2009-05-02
forum: Packaging and Compiling Programs
---

### Post by duncan_bayne on 2009-05-02
Hi All,

I'm trying to offer an application with a .deb installer, and am having limited success.

The application itself is pretty simple; it contains a .NET .EXE (to run on Mono), a dependency upon the Mono runtime, a couple of icon files, and a licence file.

All I want to do is:

[LIST=1]
[*]copy the .exe, licence and icons into [FONT="Courier New"]/usr/share/myapp[/FONT]
[*]copy a shim .sh (that basically calls [FONT="Courier New"]mono /usr/share/myapp/myapp.exe "$@")[/FONT] into [FONT="Courier New"]/usr/bin[/FONT]
[*]set up a file association in KDE and Gnome
[*]add a menu item in KDE and Gnome
[/LIST]

I've been to the #ubuntu-mutu IRC channel, & the helpful folk there pointed me at the debhelper suite.  However, they look a little ... heavy ... for my purposes, and seem to be heavily dependent upon source being available and in the classic 'configure, make, make install' vein.   [At least one poster](http://ubuntuforums.org/showpost.php?p=2142775&postcount=4) reckons that what I'm trying to do isn't what debhelper was designed to do.

My current solution is a shell script that creates a directory tree containing my files, then runs [FONT="Courier New"]dpkg --build[/FONT] in it.  As far as I can tell I can get the rest (menu items, file associations) going by following [these instructions from Sun](http://developers.sun.com/solaris/articles/integrating_gnome.html), at least on Mono.

So I'm not stumped ... so much as wondering if there is something I'm missing?  Is creating packages for Ubuntu *really* this awkward?

---

### Post by directhex on 2009-05-02
> **duncan_bayne said:**
> Hi All,

I'm trying to offer an application with a .deb installer, and am having limited success.

The application itself is pretty simple; it contains a .NET .EXE (to run on Mono), a dependency upon the Mono runtime, a couple of icon files, and a licence file.

All I want to do is:

[LIST=1]
[*]copy the .exe, licence and icons into [FONT="Courier New"]/usr/share/myapp[/FONT]
[*]copy a shim .sh (that basically calls [FONT="Courier New"]mono /usr/share/myapp/myapp.exe "$@")[/FONT] into [FONT="Courier New"]/usr/bin[/FONT]
[*]set up a file association in KDE and Gnome
[*]add a menu item in KDE and Gnome
[/LIST]

I've been to the #ubuntu-mutu IRC channel, & the helpful folk there pointed me at the debhelper suite.  However, they look a little ... heavy ... for my purposes, and seem to be heavily dependent upon source being available and in the classic 'configure, make, make install' vein.   [At least one poster](http://ubuntuforums.org/showpost.php?p=2142775&postcount=4) reckons that what I'm trying to do isn't what debhelper was designed to do.

My current solution is a shell script that creates a directory tree containing my files, then runs [FONT="Courier New"]dpkg --build[/FONT] in it.  As far as I can tell I can get the rest (menu items, file associations) going by following [these instructions from Sun](http://developers.sun.com/solaris/articles/integrating_gnome.html), at least on Mono.

So I'm not stumped ... so much as wondering if there is something I'm missing?  Is creating packages for Ubuntu *really* this awkward?

I suggest you take a look at an existing binary-only package, e.g. a font package, for how to do this - e.g. ttf-inconsolata. If your assembly is fully managed, then you want to keep things in the "indep" rules and make sure your debian/control is "architecture: all". If you do arch-specific things, then use "arch" and "architecture: i386 amd64" etc. Oh, and remove the font-related rules from the inconsolata example.

Please be sure to use a dependency on ${cli:Depends}, and use the dh_clideps rule in binary-arch or binary-indep to track PROPER Mono dependencies, don't do anything lazy by hand. dh_clideps works on binaries, not source, producing a list of required packages based on assemblyrefs.

I think dh_installmenu deals with icons, but I could be misremembering

---

### Post by duncan_bayne on 2009-05-02
Thanks :-)  For anyone following this thread, the ttf-inconsolata source can be had from svn://svn.debian.org/svn/pkg-fonts/packages/ttf-inconsolata.

---

### Post by duncan_bayne on 2009-05-03
Right, I think I've got it.  I've produced a set of files & a rules file that in turn produces a .deb that is deemed valid by lintian.  Great tool that.

---

### Post by duncan_bayne on 2009-05-03
Right, I've got my .desktop file working properly - meaning that I get a nice icon in Applications -> Accessories.  However, I am now totally stuck on adding a MIME type.

In my debian directory I have (amongst other things like manpages etc.)

myapp.desktop
```

[Desktop Entry]
Name=MyApp
Comment=Does stuff
Exec=myapp %F
Terminal=false
Type=Application
StartupNotify=true
Icon=/usr/share/myapp/app.png
Categories=GNOME;GTK;Utility;TextEditor
MimeType=application/myapp

```

myapp.keys
```

application/myapp:
    description=Stuff
    icon_filename=/usr/share/myapp/doc.png
    default_action=application
    short_list_application_ids_for_novice_user_level=myapp
    category=Documents/Text

```

myapp.mime
```

application/myapp
    ext: myapp

```

myapp.applications
```
myapp
    command=myapp
    name=myapp
    expects_uris=false
    requires_terminal=false
    mime_types=application/myapp
    can_open_multiple_files=false

```

In install, I specify where these files are to go:

```

...

    debian/myapp.desktop /usr/share/applications
    debian/myapp.mime /usr/share/mime-info
    debian/myapp.keys /usr/share/mime-info
    debian/myapp.applications /usr/share/application-registry

```

I have used dh_installmime to generate snippets for my postinst script (and my postrm, which isn't relevant here):

postinst
```

#!/bin/sh
# Automatically added by dh_desktop
if [ "$1" = "configure" ] && which update-desktop-database >/dev/null 2>&1 ; then
    update-desktop-database -q
fi
# End automatically added section
# Automatically added by dh_installmime
if [ "$1" = "configure" ] && [ -x "`which update-mime 2>/dev/null`" ]; then
    update-mime
fi
# End automatically added section

```

This is all assembled by my rules file:

```

...

binary-indep:
    dh_testdir
    dh_testroot
    dh_clean -k
    dh_install
    dh_testdir
    dh_testroot
    dh_makeclilibs
    dh_clideps
    dh_installchangelogs
    dh_installman debian/myapp.1
    dh_installmime
    dh_desktop
    dh_compress
    dh_installdefoma
    dh_fixperms
    dh_installdeb
    dh_gencontrol
    dh_md5sums
    dh_builddeb

```

Everything works, except that GNOME doesn't pick up on the new MIME type, even after a restart.  For what it's worth my .deb seems to be screwing up /etc/mailcap too.  I see the following in it, which isn't in keeping with the rest of the entries:

```

...

multipart/x-zip; /usr/bin/file-roller '%s'; test=test -n "$DISPLAY"
application/x-troff-man; /usr/bin/nroff -mandoc -Tutf8; copiousoutput; print=/usr/bin/nroff -mandoc -Tutf8 | print text/plain:-
[b]application/myapp
    ext: myapp[/B]
application/x-ogg; rhythmbox '%s'; description="Ogg Vorbis audio"; test=test -n "$DISPLAY"; nametemplate=%s.ogg

...

```

The only warnings I'm getting from lintian are:

```

W: myapp: maintainer-script-ignores-errors postinst
W: myapp: maintainer-script-ignores-errors postrm

```

... so now I *am* totally stumped.  Any assistance would be greatly appreciated.  I think I must be missing something _so_ simple here ... odd that lintian isn't picking it up though.

---

### Post by duncan_bayne on 2009-09-14
I finally figured this out, & I've provided a breakdown of the resultant .deb structure here:

[Deploying Proprietary Java Software on Ubuntu Linux](http://www.offbyzero.com/resources/java_deb_ubuntu)

Hope it helps anyone else who gets stuck on the same issues.  

(FYI, since I my previous post we re-wrote the app in Java due to very poor performance and Mac OS X stability issues in Mono.)

---

### Post by internalkernel on 2009-09-15
Haha! Thank you! I think you figured it out for both of us.... lol... I've been struggling with something similar, as I posted [here]("http://ubuntuforums.org/showthread.php?t=1265032"). 

Just trying to roll a simple deb package that configures some system settings and drops a couple scripts into /usr/bin. I was failing miserably when using dh_make and debuild; some measure of success with dpkg --build... I knew there was a better way. 

Thanks for posting that how-to...

---

### Post by MrQuincle on 2010-08-20
This is an old post, but one of the few actually illustrating how to install a desktop icon from a Debian package.

I added to my robot3d1.dirs file (very unlikely that they don't already exist though):
```

usr/share/desktop
usr/share/pixmaps

```

And to the robot3d1.install file:
```

debian/robot3d.desktop usr/share/applications
debian/robot3d.png usr/share/pixmaps

```

The desktop file:
```

[Desktop Entry]
Version=1.0
Name=Robot3D Simulator
Name[nl]=Robot3D Simulator
GenericName=Simulator
GenericName[nl]=Simulator
Comment=A 3D robot simulator
Comment[nl]=Een 3D robot simulator
Exec=GameStart Robot3D %u
Icon=robot3d
Terminal=false
Categories=Science;Physics;Education;
Type=Application
```

What I haven't been able to figure out is where the "Categories" come from, and how they are parsed. If I leave for example "Education;" out of it, it will not show up in the "Science" menu, but in the "Others" menu.

Oh, yeah, and use sudo update-desktop-database to apply changes. It will (normally) run automatically if you install a .deb package.

---

### Post by SevenMachines on 2010-08-20
> What I haven't been able to figure out is where the "Categories" come from, and how they are parsed. If I leave for example "Education;" out of it, it will not show up in the "Science" menu, but in the "Others" menu.

Try the spec 'registered categories' list 
[http://standards.freedesktop.org/menu-spec/latest/](http://standards.freedesktop.org/menu-spec/latest/)

---

### Post by MrQuincle on 2010-08-20
> **SevenMachines said:**
> Try the spec 'registered categories' list 
[http://standards.freedesktop.org/menu-spec/latest/](http://standards.freedesktop.org/menu-spec/latest/)

Cool, I didn't know there was even a Robotics additional category: 

[http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

So, even though "Robotics" has related category "Science, Education", both are needed in the Category field. The last because it is one of the few Main Category possibilities.

---

