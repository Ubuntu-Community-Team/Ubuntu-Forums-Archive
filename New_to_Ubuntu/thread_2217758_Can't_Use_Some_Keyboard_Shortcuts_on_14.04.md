---
title: "Can't Use Some Keyboard Shortcuts on 14.04"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by karl13 on 2014-04-18
I'm running Lubuntu 14.04 LTS live (without installing) on my UFD. I can't "Alt+F2" or "Windows key (Super)+R" to run a command. I can use other keyboard shortcuts like Ctrl+Alt+T, etc. I had Lubuntu 13.10 on my UFD the other day, and this keyboard shortcut and others worked. Also I don't have the "Keyboard Shortcuts" applet under "Preferences". I thought I tested 14.04 at home (can't remember),  so maybe it's keyboard specific. I'm on another machine right now.

---

### Post by karl13 on 2014-04-18
I found this in "lubuntu-rc.xml", so why doesn't it work?

<!-- Keybindings for running Run menu from Lxpanel on Home + R--><keybind key="W-r"><action name="Execute"><command>lxsession-default launcher_manager</command></action></keybind><keybind key="A-F2"><action name="Execute"><command>lxsession-default launcher_manager</command></action></keybind>

---

### Post by Thomas_Hartmann on 2014-04-19
Hi,

I can confirm the problem - ALT+F2 is not working on a fresh Lubuntu 14.04
which is a biit annoying since I have to work to the menue (i.e., 'run') or use a terminal for program starts :(

---

### Post by mp3foley on 2014-04-21
> **karl13 said:**
> I found this in "lubuntu-rc.xml", so why doesn't it work?

<!-- Keybindings for running Run menu from Lxpanel on Home + R--><keybind key="W-r"><action name="Execute"><command>lxsession-default launcher_manager</command></action></keybind><keybind key="A-F2"><action name="Execute"><command>lxsession-default launcher_manager</command></action></keybind>

Also found it not working, did some investigation by looking in lxsession-default.  Found "launcher_manager" does not exist, it is now "launcher".

Seems to have fixed it by editting lubuntu-rc.xml and change the above lines to be "<command>lxsession-default launcher</command>".  Super-R and Alt-F2 not bring up the Run dialog.

I should find where to file a bug about this so it gets fixed, but don't have time right now.

---

### Post by bapoumba on 2014-04-21
Alt-F2 and W-r are running fine here. Here is what I have in my /home/bapoumba_lxde/.config/openbox/lubuntu-rc.xml
```

<keybind key="W-r">
      <action name="Execute">
        <command>lxpanelctl run</command>
      </action>
    </keybind>

</keybind>
    <keybind key="A-F2">
      <action name="Execute">
        <command>lxpanelctl run</command>
      </action>
    </keybind>
```

---

### Post by karl13 on 2014-04-22
OK, I tried both changes, and they both work. For it to go into effect, I had to logoff. I'm guessing they fixed the bug if it works for bapoumba out of the box?

---

### Post by bapoumba on 2014-04-22
I have to say I ran and upgrade from 13.10 when Trusty was at alpha stage.

---

