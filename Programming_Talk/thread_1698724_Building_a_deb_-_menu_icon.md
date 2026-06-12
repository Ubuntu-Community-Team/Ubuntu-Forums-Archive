---
title: "Building a deb - menu icon?"
date: 2011-03-02
forum: Programming Talk
---

### Post by cgroza on 2011-03-02
Hello everyone. I am currently developing a text editor:[https://sourceforge.net/projects/gecrit/](https://sourceforge.net/projects/gecrit/)

and I wish that my deb would add a menu entry to the Ubuntu menu.

Does anyone know the steps to do it, maybe give me some guidance?
I tried putting it in a folder that gnome claims to scan it for menu items and it did not work.

Thank you.

---

### Post by dodle on 2011-03-02
In your build tree you need to have a .desktop file located in the applications folder. So it would be something like [color=blue]build_root/usr/share/applications/myapp.desktop[/color]. Open up a text editor then open up one of the .desktop files in /usr/share/applications to see some examples. Here is one that is on my system:

/usr/share/applications/codeblocks.desktop:
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Code::Blocks IDE
Comment=Configurable and extensible IDE
Exec=codeblocks %F
Icon=codeblocks
Terminal=false
X-MultipleArgs=false
Categories=Development;IDE;GTK;
StartupNotify=true
MimeType=application/x-codeblocks;application/x-codeblocks-workspace;
```

You can find an explanation of Desktop Entry files here: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

If you want a custom icon, you can place one in the [color=blue]/usr/share/pixmaps[/color] folder. So the codeblocks .desktop file has the following field:

```
Icon=codeblocks
```

That means that it will look for a pixmap file called codeblocks.xxx in /usr/share/pixmaps and use it as the menu icon. You don't have to place the icon file in the pixmaps folder, but if you don't you will have to specify where the file is located:

```
Icon=/usr/share/myapp/myicon.png
```

The "Exec" field need to have the name of the executable you wish to launch. If the executable is not located in your system path you will need to specify its location:

```
Exec=/usr/share/myapp/app
```

So, in your build tree you will need to have the following two files:

[color=blue]build_root/usr/share/applications/myapp.desktop
build_root/usr/share/pixmaps/myicon.xxx[/color]

I'm not sure all of which pixmap types are supported. I know that you can use .png and .svg files. I'm sure that .jpg is supported as well.

---

### Post by cgroza on 2011-03-02
Thank you. It is been very useful.

---

