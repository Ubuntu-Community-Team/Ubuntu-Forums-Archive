---
title: "Icon doesn't show up."
date: 2023-10-02
forum: New to Ubuntu
---

### Post by rifqilubis on 2023-10-02
When i install discord and vscode, the icon appear instantly. but some other app appear a bit late. and there is an app that doesn't have the orginal icon. Why is that?


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292815&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292816&stc=1[/IMG]

its only appear gray and blue. all those icon are not the real icon.

---

### Post by rifqilubis on 2023-10-06
I guess there is no solution then

---

### Post by Holger_Gehrke on 2023-10-07
While in Windows the icon is stored inside the executable file on Linux it isn't. For starting programs in a graphical way you use a file with the extension '.desktop'. Those are simple text files with a [specific structure]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") similar to the old '.ini' files on Windows. One thing that can be in a '.desktop' file is a line giving an icon as either 'Icon=name' - used for icon files in specific well-known locations e.g. /usr/share/icons/ - or 'Icon=/path/to/the/imagefile.extension' - used for icons placed anywhere else.

Having a .desktop file for a program still doesn't make the actual executable show up as the icon. Instead the .desktop file will show up as the icon and can be used to start the executable. The menus and application overviews in the various desktop environments are generated from the desktop files. So to have an icon for a program on your desktop you'd put a .desktop file on your desktop and have the actual program somewhere else but referenced by an 'Exec=/path/to/executable' line in the desktop file.

The one on your desktop (PrismLauncher...) looks like an AppImage to me. Some of those will produce a desktop file and an image to be used as the icon when run for the first time. The one in the Dolphin window is probably some kind of shell script, you'd need to write a desktop file for that yourself.

Holger

---

### Post by rifqilubis on 2023-10-09
so the appimage (blue) and the grey one (minecraft launcher) are not possible to show their real icon?

and for second question, if i have to crate .desktop file. I can't  find the executable app on the directory. (Im talking about the appimage)

---

### Post by Holger_Gehrke on 2023-10-10
> **rifqilubis said:**
> so the appimage (blue) and the grey one (minecraft launcher) are not possible to show their real icon?
Not to get philosophical, but what even is the real icon of a program if there's no icon included in the binary ?

> **rifqilubis said:**
> and for second question, if i have to crate .desktop file. I can't  find the executable app on the directory. (Im talking about the appimage)
The AppImage is in your desktop directory. The name of that directory depends on the language your system is set to. On my (German) system it's "$HOME/Schreibtisch", on an English system it's "$HOME/Desktop". There's a configuration file in the hidden directory $HOME/.config named user-dirs.dirs which has a line starting with 'XDG_DESKTOP_DIR=' followed by the path to the desktop directory.

If it was me, I'd move the actual executable somewhere else since having both the .desktop file and the executable on the desktop can be a bit confusing. Either $HOME/.local/bin or $HOME/bin are good places for the executable since they are added to the $PATH by $HOME/.bashrc if they exist. Then I'd put a .desktop file either in the desktop directory for an icon on the desktop or in $HOME/.local/share/applications to get an item in the menu just for my user account or in /usr/local/share/applications to get an item in the menu for all user accounts on the system.

Holger

---

