---
title: "Maintaining backward compatibility when dependencies are deprecated"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by IrmaLiddleTeapot on 2013-05-04
I've spent a bit of time looking through the forums but haven't found an explicit answer to this question of dependecies and deprecation.   For example some distro's have deprecated Midnight Commander in favour of links but my experience has been that "Midnight Commander" appears to be freer of dependencies than "links".   I know I can use "lsmod" and "depmod" to determine kernel which kernel modules are present and their dependencies, but the question becomes if the tools or tool-chains I require aren't present, what can I do to restore functionality ?

     I'm quite happy using a command line without all of the cruft associated with a nice visual interface but some toolchains don't seem to separate out, for example, the gtk stuff from the straight gcc compiled code that runs on a command line interface and isn't "prettyfied".
I want compact code that is portable and runs on a command line interface using the bare minimum of drivers.  Can I build my own kernel (like gentoo) in Ubuntu if I wish ?

I'd greatly appreciate any pointers yoy'd care to offer.   Many thanks in advance and despite my whinge, thanks for a great product."

---

### Post by tgalati4 on 2013-05-04
Linux Mint Mate may be closer to what you want in a distro:

tgalati4@Mint14-Extensa ~ $ apt-cache search midnight commander
avfs - virtual filesystem to access archives, disk images, remote locations
gnome-commander - nice and fast file manager for the GNOME desktop
gnome-commander-data - Data files for GNOME Commander
gnome-commander-dbg - Debugging symbols for gnome-commander
junior-system - Debian Jr. System tools
krusader - twin-panel (commander-style) file manager
lfm - simple but powerful file manager for the UNIX console
mc - Midnight Commander - a powerful file manager
mc-data - Midnight Commander - a powerful file manager -- data files
mc-dbg - Midnight Commander - a powerful file manager - debug package
moc - ncurses based console audio player
pilot - Simple file browser from Alpine, a text-based email client
ranger - File manager with an ncurses frontend written in Python
tuxcmd - twin-panel (commander-style) file manager using GTK+ 2

I don't understand the toolchain question.  Each distro assembles packages slightly differently.  Mate renames all of its packages so that it won't conflict with Gnome2 or Gnome3 packages:

tgalati4@Mint14-Extensa ~ $ apt-cache depends mate-desktop
mate-desktop
  Depends: libc6
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libunique-1.0-0
  Depends: libmatenotify
  Depends: hicolor-icon-theme
  Depends: libmatedesktop
  Depends: mate-desktop-common
 |Depends: mate-desktop-gnome
 |Depends: gnome-desktop-data
  Depends: gnome-desktop3-data
  Conflicts: mate-desktop:i386

Yes, you can build your own kernel.  It takes 2 to 3 hours and you may have to do it a couple of times to get a kernel that works correctly.  As you turn off features that you don't intend to use, you may break other packages that need those features.  So you are correct, there is not a "clean" way to build Ubuntu and add elements that you want.  There are several flavors of supported Ubuntu and several Ubuntu spin-offs (such as Linux Mint) that take a different direction.  There is also a minimal Ubuntu install and you can search the forums for how folks customize this mini distro for their purposes.

If you really want the "build-it-yourself" experience then Arch, Gentoo, or Slackware is where I would spin my electrons.  If you don't want to spend the time learning those other distros, then Linux Mint Mate gives you more of what you want and less of what you don't want--out of the box.

---

### Post by Cheesehead on 2013-05-04
> **IrmaLiddleTeapot said:**
> For example some distro's have deprecated Midnight Commander in favour of links but my experience has been that "Midnight Commander" appears to be freer of dependencies than "links".

Huh? Who has deprecated mc? And what do you mean by 'links'?

---

