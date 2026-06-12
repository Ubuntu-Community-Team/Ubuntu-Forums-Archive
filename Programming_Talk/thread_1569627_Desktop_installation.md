---
title: "Desktop installation"
date: 2010-09-07
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-07
After all that development work I'm sure we all want to install apps in appropriate menus of the desktop.

```

1. I copied my icon, attached l10n.png file to:
/usr/share/pixmaps/l10n.png
and installed my speaknumber.py script in /usr/local/bin

2. In /etc/xdg/menus/applications.menu I added an entry as follows:

  <!-- Experimental submenu -->
  <Menu>
    <Name>I18nL10n</Name>
    <Directory>l10n.directory</Directory>
    <Include>
      <And>
        <Category>l10n</Category>
      </And>
    </Include>
  </Menu> <!-- End Experimental -->

3. In file /usr/share/desktop-directories/l10n.directory I have:

[Desktop Entry]
Name=L10n & i18n
Comment=Exploring Internationalization and Localization
Icon=l10n
Type=Directory
Encoding=UTF-8

4. In file: /usr/share/applications/l10n.desktop I have:

[Desktop Entry]
Encoding=UTF-8
Name=Speak Number
Comment=Internationalization and Localization Experiments
Exec=speaknumber.py
Terminal=false
Type=Application
Icon=l10n
Categories=l10n

```

... and nothing shows in my applications menu :(

---

### Post by worksofcraft on 2010-09-07
oh... and my Icon file is attached just in case that's the problem... and yes it IS a lion: It's common practice to use the numeromon "l10n" to mean "localization"

---

### Post by worksofcraft on 2010-09-07
edit... no it isn't solved :(

When I reboot it disappears from the menu again.

The only way I get it to show is by editing and saving a new version of /usr/share/applications/l10n.desktop.

---

