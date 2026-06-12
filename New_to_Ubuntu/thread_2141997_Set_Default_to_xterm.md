---
title: "Set Default to xterm"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by UserJB on 2013-05-04
I have ALT-N set through my Keyboard Shortcuts to create a new Terminal.  But, that terminal is currently a gnome-terminal.  I want to change the default terminal to an xterm.  How can I do this?

Also, when I use ALT-N to create a new terminal, and I'm currently in Workspace 2, it creates that terminal in workspace-1, and switches to workspace-1.  This isn't what I want.  Can I create the new terminal in whatever worksapce I'm currently in?  Is GNOME broken on Ubuntu?

---

### Post by MG&amp;TL on 2013-05-04
I don't know about the workspaces thing (very odd - compiz *place windows* plugin or similiar?), but to set the default terminal emulator you can use this command:

```
sudo update-alternatives --config x-terminal-emulator
```

---

### Post by Frogs Hair on 2013-05-04
I can't reproduce the terminal placement problem, but I am not using a custom keyboard shortcut. If open a second terminal on workspace 2 it appears there . I use the standard Ctrl + Alt + T shortcut.

---

### Post by UserJB on 2013-05-04
I tried 'sudo update-alternatives --config x-terminal-emulator' and it didn't change anything.  When I ALT-N for a new terminal, it doesn't bring up an xterm: it brings up a gnome-terminal I think.

---

### Post by Frogs Hair on 2013-05-04
I use the XFCE session along with Gnome and Unity and it does allow changing the default terminal via the GUI . I like it better than Classic feature wise.

---

### Post by UserJB on 2013-05-04
What does 'XFCE Session' mean and how do I use it?

---

### Post by MG&amp;TL on 2013-05-04
> **UserJB said:**
> I tried 'sudo update-alternatives --config x-terminal-emulator' and it didn't change anything.  When I ALT-N for a new terminal, it doesn't bring up an xterm: it brings up a gnome-terminal I think.

If you run the command x-terminal-emulator, it uses the default terminal for the system. Whatever shortcut program you're using must be launching *gnome-terminal* specifically.

---

### Post by BluNova on 2013-05-05
```
 gsettings set org.gnome.desktop.default-applications.terminal exec 'xterm'  
```This should work

---

