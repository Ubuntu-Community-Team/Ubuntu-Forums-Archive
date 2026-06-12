---
title: "HOWTO: Perfecting your system bit by bit with GConf"
date: 2006-04-22
forum: Outdated Tutorials &amp; Tips
---

### Post by mostwanted on 2006-04-22
These are just some options in I found in Gconf that were nice and improved my desktop experience. They are listed here as a bunch of commands for your convenience:

```

# Make File-roller open the destination folder in Nautilus when extracting has finished
gconftool-2 --type boolean --set /apps/file-roller/dialogs/extract/view_destination_folder true

# Nautilus desktop shows mounted volumes
gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible true

# Make update-manager automatically look for new full distro updates
gconftool-2 --type boolean --set /apps/update-manager/check_dist_upgrades true

# Toolbars in GTK+ apps are detachable
gconftool-2 --type boolean --set /desktop/gnome/interface/toolbar_detachable true

# Automatically open DVDs in GXINE or VLC instead of Totem
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "gxine dvd:/%m"
gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "vlc %m"

# Set a different locale than US for Amazon cover retrival, in this case UK
gconftool-2 --type string --set /apps/muine/amazon_locale uk
```

---

