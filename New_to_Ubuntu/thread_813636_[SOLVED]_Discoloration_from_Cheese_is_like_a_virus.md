---
title: "[SOLVED] Discoloration from Cheese is like a virus!"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Melk79 on 2008-05-31
I'm dealing with this [Bug]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/219998") and it is extremely annoying.  I was taking some videos with Cheese using the different effect it has. I played a video while it was open from Totem and just like the bug says, now my color output is all screwed up.  The strange part is it only effects Cheese, Totem, Mplayer and Skype.  I can use Ekiga and play videos on Firefox (YouTube) without a problem.

Restarts and shutdowns have no effect.  I completely removed and reinstalled the problem programs and still nothing.  Does anyone have an idea on how to fix this?  The monitor output is fine and graphics display fine.  It is just the video. Thanks.

---

### Post by tdrusk on 2008-05-31
> **Melk79 said:**
> I'm dealing with this [Bug]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/219998") and it is extremely annoying.  I was taking some videos with Cheese using the different effect it has. I played a video while it was open from Totem and just like the bug says, now my color output is all screwed up.  The strange part is it only effects Cheese, Totem, Mplayer and Skype.  I can use Ekiga and play videos on Firefox (YouTube) without a problem.

Restarts and shutdowns have no effect.  I completely removed and reinstalled the problem programs and still nothing.  Does anyone have an idea on how to fix this?  The monitor output is fine and graphics display fine.  It is just the video. Thanks.

Try deleting the .cheese directory in your Home folder. .cheese may not be the name...

---

### Post by Melk79 on 2008-05-31
I can't find a .cheese file.  Here is the contents:
.                               .lesshst
..                              .lightyears.cfg
.adobe                          .lightyears.save0.dat
.bash_history                   .local
.bash_logout                    .macromedia
.bashrc                         .metacity
.cache                          .mozilla
.civclientrc                    .mplayer
.civserver_history              Music
.compiz                         .nautilus
.config                         .neverball
.dbus                           .nvidia-settings-rc
Desktop                         .openoffice.org2
.dmrc                           .picasa
Documents                       Pictures
.dvdcss                         .profile
.emerald                        Public
.esd_auth                       .pulse
.evolution                      .pulse-cookie
Examples                        .qt
.face                           .recently-used
.fontconfig                     .recently-used.xbel
.fprint                         scripts
.fr-9X1TQ8                      .Skype
.freeciv                        .ssh
.gconf                          .sudo_as_admin_successful
.gconfd                         .sudoku
.gimp-2.4                       .supertuxkart
.gksu.lock                      Templates
.gnome                          .themes
.gnome2                         Themes
.gnome2_private                 .thumbnails
.gnupg                          .tomboy
.googleearth                    .tomboy.log
.gphoto                         .transmission
grub-gfxboot_0.97-11_amd64.deb  .update-manager-core
grub-gfxboot_0.97-5_i386.deb    .update-notifier
.gstreamer-0.10                 Videos
.gtk-bookmarks                  .wapi
.gtkrc-2.0                      .wesnoth
.gtkrc-2.0~                     .Xauthority
.gvfs                           .xine
.ICEauthority                   .xscreensaver-getimage.cache
.icons                          .xsession-errors
.kde

---

### Post by shifty_powers on 2008-05-31
try looking in .config

---

### Post by Melk79 on 2008-05-31
.config/ has the following:
.   autostart  Google   menus  tracker         user-dirs.dirs
..  compiz     gtk-2.0  totem  Trolltech.conf  user-dirs.locale

I guess I'm not sure what to look for exactly.  Is there some kind of reset command?

---

### Post by Maestro23 on 2008-05-31
Look in **/usr/share**

---

### Post by Melk79 on 2008-05-31
Thank you.  There is all of this:
cheese
cheese/sounds
cheese/sounds/shutter4.ogg
cheese/sounds/shutter0.ogg
cheese/sounds/shutter3.ogg
cheese/sounds/shutter1.ogg
cheese/sounds/shutter2.ogg
cheese/pixmaps
cheese/pixmaps/thumbnail-frame.png
cheese/pixmaps/camera-icon.svg
cheese/cheese-ui.xml
cheese/cheese.ui
cheese/effects
cheese/effects/dicetv.png
cheese/effects/vertigotv.png
cheese/effects/shagadelictv.png
cheese/effects/identity.png
cheese/effects/warptv.png
cheese/effects/Saturation.png
cheese/effects/videoflip_v.png
cheese/effects/Hulk.png
cheese/effects/Mauve.png
cheese/effects/videoflip_h.png
cheese/effects/edgetv.png
cheese/effects/NoirBlanc.png

Are we saying to delete all of that?

---

### Post by Melk79 on 2008-06-01
OK.  I tried removing all the cheese stuff from the /usr/share.  This did not fix the problem.  My video output looks like the picture links I posted originally with the "bug".  I have family in town that I'd like to show "Linux" to, but video looking like this would not be good.  It seems like when I used Totem and Cheese at the same time is when the problem started, which makes me think some universal-type setting got changed.  Any help would be really appreciated.  Thanks.

---

### Post by Melk79 on 2008-06-02
I have found a temporary fix to this problem.  When the problem originally surfaced, the Color Balance setting sliders for Totem (Under Edit>Prefrences>Display) all lined up in the middle.  

After a log off and power down for the night, I found the hue bar to be at far left in the morning.  The picture output was not fixed.  When I hit the Reset to Defaults button, the hue slider moved back to the middle with the rest of the settings, but when I slid it back left the picture corrected.  This also fixed the color on Cheese and Skype. So, video looks good again, but I still don't know what happened and how to permanently fix it.  Doesn't this seem strange?  Why are these programs pulling settings from the same place, but Ekiga isn't?

---

