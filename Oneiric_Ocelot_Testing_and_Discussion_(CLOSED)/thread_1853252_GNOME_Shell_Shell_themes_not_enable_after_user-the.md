---
title: "GNOME Shell: Shell themes not enable after user-theme installed"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lolpenguin on 2011-10-01
Coming from my virtual machine (ubuntu 11.10 beta 2)
I am quite new to GNOME Shell and unclear how the extensions work. So I installed gnome-shell-extensions-common and gnome-shell-extensions-user-theme from terminal, but in GNOME tweak tool the shell theme remains disabled and says, "Shell user-theme extension not enabled":confused:
I reinstalled the user-theme extensions in tweak tool this time, and it says "user-theme@gnome-shell-extensions.gnome.org extension installed successfully [Restart]" and I restart the Shell, now a problem report saying Tweak Tool has crashed comes up, and Shell theme is STILL disable????
:confused::confused::confused:

---

### Post by tista on 2011-10-02
> **lolpenguin said:**
> Coming from my virtual machine (ubuntu 11.10 beta 2)
I am quite new to GNOME Shell and unclear how the extensions work. So I installed gnome-shell-extensions-common and gnome-shell-extensions-user-theme from terminal, but in GNOME tweak tool the shell theme remains disabled and says, "Shell user-theme extension not enabled":confused:
I reinstalled the user-theme extensions in tweak tool this time, and it says "user-theme@gnome-shell-extensions.gnome.org extension installed successfully [Restart]" and I restart the Shell, now a problem report saying Tweak Tool has crashed comes up, and Shell theme is STILL disable????
:confused::confused::confused:

Hi lolpengiuin,

Which version did you install to deal with extensions?
extensions must be the same version with gnome-shell.

And if your installed extensions might have some errors, try LookingGlass. LG could find any formatting/function error of extensions...

cheers.

---

### Post by ombra on 2011-10-02
Check if the version of your gnome-shell (gnome-shell --version) is the same as in the metadata.json file (found in /usr/share/gnome-shell/extensions/<name of the extension> or ~/.local/gnome-shell/extensions/<name of the extension>).

If not, that's the reason.

Try to replace the versionnumber in the metadata.json with the output of gnome-shell --version

Then restart the shell, open the gnome tweak tool and you shoud be able to switch the theme.

hope it helps

---

### Post by synd7 on 2011-10-02
Where (what repo) have you installed gnome-shell-extensions packages from?

In line with what ombra said, check in synaptic what version you've got installed. If its not the same as the gnome-shell version then the extensions wont show up in gnome tweak tool. ombra's solution is a bit hacky but if it works it works. The gnome-shell-extensions package should catch up quickly enough.

---

### Post by lolpenguin on 2011-10-02
Thanks guys, you have been a lot of help!
Editing the metadata.json file causes the extension to break, but now I know what's the problem.
Thanks

UPDATE: It seems Synaptic did not install the latest version of the extensions. Well, I got them working now!

---

