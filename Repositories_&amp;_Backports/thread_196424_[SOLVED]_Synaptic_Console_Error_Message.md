---
title: "[SOLVED] Synaptic Console Error Message"
date: 2006-06-14
forum: Repositories &amp; Backports
---

### Post by Malac on 2006-06-14
I keep getting this error message intermittently in the terminal when installing from Synaptic as it says "CRITICAL" I'm somewhat concerned. 
```
** (process:20957): CRITICAL **: egg_desktop_entries_add_group: assertion 'egg_desktop_entries_lookup_group (entries, group_name) = NULL' failed
```
 Any Ideas greatly appreciated.
Thanks in Advance.

---

### Post by Malac on 2006-06-23
To quote the Floyd : "....anybody out there."

---

### Post by Miguel on 2006-07-13
Hi Malac,

Have you been able so solve your problem? Did it happen with any concrete package or did it happen with random packages? I ask you because I'm trying to find out why maxddark is having some problems with Nautilus.

Sorry for not helping you :(

---

### Post by Malac on 2006-07-13
Hi Miguel,
I never did solve this, it is still happening and with random packages and updates. I can't see any common thread to follow and don't know what "egg_desktop_entries......" concern other than the Desktop.

---

### Post by Miguel on 2006-07-13
I think I have an idea. Could you post the output you get for the following command:
```

sudo update-desktop-database -v

```

I expect it to give some CRITICAL things, BTW.

---

### Post by Malac on 2006-07-14
Hi Miguel,
Here is the output. :)
```
Search path is now: [/usr/local/share/applications, /usr/share/applications]
Could not create cache file in directory '/usr/local/share/applications':
        Error opening directory '/usr/local/share/applications': No such file or  directory
File '/usr/share/applications/bug-buddy.desktop' lacks MimeType key
File '/usr/share/applications/gnome-network-preferences.desktop' lacks MimeType key
File '/usr/share/applications/accessibility-keyboard.desktop' lacks MimeType key
File '/usr/share/applications/at-properties.desktop' lacks MimeType key
File '/usr/share/applications/default-applications.desktop' lacks MimeType key
File '/usr/share/applications/font-properties.desktop' lacks MimeType key
File '/usr/share/applications/background.desktop' lacks MimeType key
File '/usr/share/applications/keyboard.desktop' lacks MimeType key
File '/usr/share/applications/gnome-settings-mouse.desktop' lacks MimeType key
File '/usr/share/applications/gnome-settings-sound.desktop' lacks MimeType key
File '/usr/share/applications/gtk-theme-selector.desktop' lacks MimeType key
File '/usr/share/applications/gnome-ui-properties.desktop' lacks MimeType key
File '/usr/share/applications/keybinding.desktop' lacks MimeType key
File '/usr/share/applications/window-properties.desktop' lacks MimeType key
File '/usr/share/applications/display-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnome-about-me.desktop' lacks MimeType key
File '/usr/share/applications/gnomecc.desktop' lacks MimeType key
File '/usr/share/applications/alacarte.desktop' lacks MimeType key
File '/usr/share/applications/gmenu-simple-editor.desktop' lacks MimeType key
File '/usr/share/applications/evolution-mail.desktop' lacks MimeType key
File '/usr/share/applications/evolution-2.2.desktop' lacks MimeType key
File '/usr/share/applications/gaim.desktop' lacks MimeType key
File '/usr/share/applications/gcalctool.desktop' lacks MimeType key
File '/usr/share/applications/gconf-editor.desktop' lacks MimeType key
File '/usr/share/applications/gdmflexiserver-xnest.desktop' lacks MimeType key
File '/usr/share/applications/session-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnome-terminal.desktop' lacks MimeType key
File '/usr/share/applications/gksu.desktop' lacks MimeType key
File '/usr/share/applications/gksuexec.desktop' lacks MimeType key
File '/usr/share/applications/gdmphotosetup.desktop' lacks MimeType key
File '/usr/share/applications/gdmsetup.desktop' lacks MimeType key
File '/usr/share/applications/gdmflexiserver.desktop' lacks MimeType key
File '/usr/share/applications/synaptic-kde.desktop' lacks MimeType key
File '/usr/share/applications/gnome-about.desktop' lacks MimeType key
File '/usr/share/applications/synaptic.desktop' lacks MimeType key
File '/usr/share/applications/gnome-volume-control.desktop' lacks MimeType key
File '/usr/share/applications/gnome-app-install.desktop' lacks MimeType key
File '/usr/share/applications/ubuntu-about.desktop' lacks MimeType key
File '/usr/share/applications/gnome-cups-icon.desktop' lacks MimeType key
File '/usr/share/applications/gnect.desktop' lacks MimeType key
File '/usr/share/applications/gnomine.desktop' lacks MimeType key
File '/usr/share/applications/same-gnome.desktop' lacks MimeType key
File '/usr/share/applications/mahjongg.desktop' lacks MimeType key
File '/usr/share/applications/gtali.desktop' lacks MimeType key
File '/usr/share/applications/ekiga.desktop' lacks MimeType key
File '/usr/share/applications/gataxx.desktop' lacks MimeType key
File '/usr/share/applications/gnotravex.desktop' lacks MimeType key
File '/usr/share/applications/gnotski.desktop' lacks MimeType key
File '/usr/share/applications/glines.desktop' lacks MimeType key
File '/usr/share/applications/iagno.desktop' lacks MimeType key
File '/usr/share/applications/gnobots2.desktop' lacks MimeType key
File '/usr/share/applications/gnibbles.desktop' lacks MimeType key
File '/usr/share/applications/gnometris.desktop' lacks MimeType key
File '/usr/share/applications/blackjack.desktop' lacks MimeType key
File '/usr/share/applications/sol.desktop' lacks MimeType key
File '/usr/share/applications/freecell.desktop' lacks MimeType key
File '/usr/share/applications/cddb-slave.desktop' lacks MimeType key
File '/usr/share/applications/vumeter.desktop' lacks MimeType key
File '/usr/share/applications/reclevel.desktop' lacks MimeType key
File '/usr/share/applications/gnome-cd.desktop' lacks MimeType key
File '/usr/share/applications/exo-preferred-applications.desktop' lacks MimeType  key
File '/usr/share/applications/gnome-sound-recorder.desktop' lacks MimeType key
File '/usr/share/applications/gstreamer-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnome-nettool.desktop' lacks MimeType key
File '/usr/share/applications/gnome-system-monitor.desktop' lacks MimeType key
File '/usr/share/applications/gnome-system-log.desktop' lacks MimeType key
File '/usr/share/applications/gnome-search-tool.desktop' lacks MimeType key
File '/usr/share/applications/gnome-dictionary.desktop' lacks MimeType key
File '/usr/share/applications/gucharmap.desktop' lacks MimeType key
File '/usr/share/applications/hwdb.desktop' lacks MimeType key
File '/usr/share/applications/language-selector.desktop' lacks MimeType key
File '/usr/share/applications/network-scheme.desktop' lacks MimeType key
File '/usr/share/applications/nautilus.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-home.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-computer.desktop' lacks MimeType key
File '/usr/share/applications/amsn.desktop' lacks MimeType key
File '/usr/share/applications/kde/componentchooser.desktop' lacks MimeType key
File '/usr/share/applications/kde/kresources.desktop' lacks MimeType key
File '/usr/share/applications/kde/kamera.desktop' lacks MimeType key
File '/usr/share/applications/kde/kappfinder.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkicker.desktop' lacks MimeType key
File '/usr/share/applications/kde/arts.desktop' lacks MimeType key
File '/usr/share/applications/kde/background.desktop' lacks MimeType key
File '/usr/share/applications/kde/bell.desktop' lacks MimeType key
File '/usr/share/applications/kde/cache.desktop' lacks MimeType key
File '/usr/share/applications/kde/clock.desktop' lacks MimeType key
File '/usr/share/applications/kde/colors.desktop' lacks MimeType key
File '/usr/share/applications/kde/desktopbehavior.desktop' lacks MimeType key
File '/usr/share/applications/kde/cookies.desktop' lacks MimeType key
File '/usr/share/applications/kde/crypto.desktop' lacks MimeType key
File '/usr/share/applications/kde/desktoppath.desktop' lacks MimeType key
File '/usr/share/applications/kde/desktop.desktop' lacks MimeType key
File '/usr/share/applications/kde/ebrowsing.desktop' lacks MimeType key
File '/usr/share/applications/kde/devices.desktop' lacks MimeType key
File '/usr/share/applications/kde/display.desktop' lacks MimeType key
File '/usr/share/applications/kde/dma.desktop' lacks MimeType key
File '/usr/share/applications/kde/filebrowser.desktop' lacks MimeType key
File '/usr/share/applications/kde/filetypes.desktop' lacks MimeType key
File '/usr/share/applications/kde/fonts.desktop' lacks MimeType key
File '/usr/share/applications/kde/icons.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmperformance.desktop' lacks MimeType key
File '/usr/share/applications/kde/interrupts.desktop' lacks MimeType key
File '/usr/share/applications/kde/ioports.desktop' lacks MimeType key
File '/usr/share/applications/kde/ioslaveinfo.desktop' lacks MimeType key
File '/usr/share/applications/kde/joystick.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmaccess.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmcss.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmfontinst.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkded.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmlaunch.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmnotify.desktop' lacks MimeType key
File '/usr/share/applications/kde/khtml_behavior.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmsmserver.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmtaskbar.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmusb.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmview1394.desktop' lacks MimeType key
File '/usr/share/applications/kde/KControl.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdm.desktop' lacks MimeType key
File '/usr/share/applications/kde/keys.desktop' lacks MimeType key
File '/usr/share/applications/kde/khtml_java_js.desktop' lacks MimeType key
File '/usr/share/applications/kde/khtml_fonts.desktop' lacks MimeType key
File '/usr/share/applications/kde/kthememanager.desktop' lacks MimeType key
File '/usr/share/applications/kde/kinfocenter.desktop' lacks MimeType key
File '/usr/share/applications/kde/krandrtray.desktop' lacks MimeType key
File '/usr/share/applications/kde/panel_appearance.desktop' lacks MimeType key
File '/usr/share/applications/kde/lanbrowser.desktop' lacks MimeType key
File '/usr/share/applications/kde/language.desktop' lacks MimeType key
File '/usr/share/applications/kde/media.desktop' lacks MimeType key
File '/usr/share/applications/kde/memory.desktop' lacks MimeType key
File '/usr/share/applications/kde/mouse.desktop' lacks MimeType key
File '/usr/share/applications/kde/netpref.desktop' lacks MimeType key
File '/usr/share/applications/kde/nic.desktop' lacks MimeType key
File '/usr/share/applications/kde/opengl.desktop' lacks MimeType key
File '/usr/share/applications/kde/partitions.desktop' lacks MimeType key
File '/usr/share/applications/kde/panel.desktop' lacks MimeType key
File '/usr/share/applications/kde/privacy.desktop' lacks MimeType key
File '/usr/share/applications/kde/pci.desktop' lacks MimeType key
File '/usr/share/applications/kde/spellchecking.desktop' lacks MimeType key
File '/usr/share/applications/kde/processor.desktop' lacks MimeType key
File '/usr/share/applications/kde/proxy.desktop' lacks MimeType key
File '/usr/share/applications/kde/screensaver.desktop' lacks MimeType key
File '/usr/share/applications/kde/scsi.desktop' lacks MimeType key
File '/usr/share/applications/kde/smbstatus.desktop' lacks MimeType key
File '/usr/share/applications/kde/sound.desktop' lacks MimeType key
File '/usr/share/applications/kde/useragent.desktop' lacks MimeType key
File '/usr/share/applications/kde/style.desktop' lacks MimeType key
File '/usr/share/applications/kde/xserver.desktop' lacks MimeType key
File '/usr/share/applications/kde/keyboard_layout.desktop' lacks MimeType key
File '/usr/share/applications/kde/keyboard.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcm_useraccount.desktop' lacks MimeType key
File '/usr/share/applications/kde/khotkeys.desktop' lacks MimeType key
File '/usr/share/applications/kde/knetattach.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdcop.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmcgi.desktop' lacks MimeType key
File '/usr/share/applications/kde/khtml_plugins.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdepasswd.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdeprintfax.desktop' lacks MimeType key
File '/usr/share/applications/kde/kjobviewer.desktop' lacks MimeType key
File '/usr/share/applications/kde/Kfind.desktop' lacks MimeType key
File '/usr/share/applications/kde/Help.desktop' lacks MimeType key
File '/usr/share/applications/kde/klipper.desktop' lacks MimeType key
File '/usr/share/applications/kde/kmenuedit.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmhistory.desktop' lacks MimeType key
File '/usr/share/applications/kde/Home.desktop' lacks MimeType key
File '/usr/share/applications/kde/kfmclient.desktop' lacks MimeType key
File '/usr/share/applications/kde/kde-hal-device-manager.desktop' lacks MimeType  key
File '/usr/share/applications/kde/khtml_filter.desktop' lacks MimeType key
File '/usr/share/applications/kde/konqbrowser.desktop' lacks MimeType key
File '/usr/share/applications/kde/konquerorsu.desktop' lacks MimeType key
File '/usr/share/applications/kde/konsole.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpager.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpersonalizer.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwindecoration.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwinoptions.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwinrules.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksplashthememgr.desktop' lacks MimeType key
File '/usr/share/applications/kde/ktip.desktop' lacks MimeType key
File '/usr/share/applications/kde/libkcddb.desktop' lacks MimeType key
File '/usr/share/applications/kde/audiocd.desktop' lacks MimeType key
File '/usr/share/applications/kde/kregexpeditor.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcron.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdat.desktop' lacks MimeType key
File '/usr/share/applications/kde/defaultapplication.desktop' lacks MimeType key
File '/usr/share/applications/kde/systemsettings.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcm_knetworkconfmodule.desktop' lacks MimeType  key
File '/usr/share/applications/kde/kuser.desktop' lacks MimeType key
File '/usr/share/applications/kde/lilo.desktop' lacks MimeType key
File '/usr/share/applications/kde/akregator.desktop' lacks MimeType key
File '/usr/share/applications/kde/amor.desktop' lacks MimeType key
File '/usr/share/applications/kde/atlantikdesigner.desktop' lacks MimeType key
File '/usr/share/applications/kde/artscontrol.desktop' lacks MimeType key
File '/usr/share/applications/kde/atlantik.desktop' lacks MimeType key
File '/usr/share/applications/kde/kanagram.desktop' lacks MimeType key
File '/usr/share/applications/kde/kalarm.desktop' lacks MimeType key
File '/usr/share/applications/kde/kalzium.desktop' lacks MimeType key
File '/usr/share/applications/kde/kandy.desktop' lacks MimeType key
File '/usr/share/applications/kde/karm.desktop' lacks MimeType key
File '/usr/share/applications/kde/katomic.desktop' lacks MimeType key
File '/usr/share/applications/kde/knewsticker-standalone.desktop' lacks MimeType  key
File '/usr/share/applications/kde/catalogmanager.desktop' lacks MimeType key
File '/usr/share/applications/kde/kbabeldict.desktop' lacks MimeType key
File '/usr/share/applications/kde/kbackgammon.desktop' lacks MimeType key
File '/usr/share/applications/kde/kbattleship.desktop' lacks MimeType key
File '/usr/share/applications/kde/kblackbox.desktop' lacks MimeType key
File '/usr/share/applications/kde/kbounce.desktop' lacks MimeType key
File '/usr/share/applications/kde/kbruch.desktop' lacks MimeType key
File '/usr/share/applications/kde/kbugbuster.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcalc.desktop' lacks MimeType key
File '/usr/share/applications/kde/KCharSelect.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcolorchooser.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcoloredit.desktop' lacks MimeType key
File '/usr/share/applications/kde/khangman.desktop' lacks MimeType key
File '/usr/share/applications/kde/kiten.desktop' lacks MimeType key
File '/usr/share/applications/kde/klatin.desktop' lacks MimeType key
File '/usr/share/applications/kde/klettres.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpercentage.desktop' lacks MimeType key
File '/usr/share/applications/kde/kstars.desktop' lacks MimeType key
File '/usr/share/applications/kde/ktouch.desktop' lacks MimeType key
File '/usr/share/applications/kde/kturtle.desktop' lacks MimeType key
File '/usr/share/applications/kde/kverbos.desktop' lacks MimeType key
File '/usr/share/applications/kde/kenolaba.desktop' lacks MimeType key
File '/usr/share/applications/kde/kfouleggs.desktop' lacks MimeType key
File '/usr/share/applications/kde/KGoldrunner.desktop' lacks MimeType key
File '/usr/share/applications/kde/kjumpingcube.desktop' lacks MimeType key
File '/usr/share/applications/kde/klickety.desktop' lacks MimeType key
File '/usr/share/applications/kde/klines.desktop' lacks MimeType key
File '/usr/share/applications/kde/kmahjongg.desktop' lacks MimeType key
File '/usr/share/applications/kde/kmines.desktop' lacks MimeType key
File '/usr/share/applications/kde/konquest.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpat.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpoker.desktop' lacks MimeType key
File '/usr/share/applications/kde/kreversi.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksame.desktop' lacks MimeType key
File '/usr/share/applications/kde/kshisen.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksirtet.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksnake.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksokoban.desktop' lacks MimeType key
File '/usr/share/applications/kde/ktron.desktop' lacks MimeType key
File '/usr/share/applications/kde/lskat.desktop' lacks MimeType key
File '/usr/share/applications/kde/kodo.desktop' lacks MimeType key
File '/usr/share/applications/kde/kteatime.desktop' lacks MimeType key
File '/usr/share/applications/kde/kworldclock.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksig.desktop' lacks MimeType key
File '/usr/share/applications/kde/kgamma.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkmrml.desktop' lacks MimeType key
File '/usr/share/applications/kde/kooka.desktop' lacks MimeType key
File '/usr/share/applications/kde/krec.desktop' lacks MimeType key
File '/usr/share/applications/kde/kscd.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdict.desktop' lacks MimeType key
File '/usr/share/applications/kde/kget.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwifimanager.desktop' lacks MimeType key
File '/usr/share/applications/kde/krdc.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkrfb.desktop' lacks MimeType key
File '/usr/share/applications/kde/krfb.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmwifi.desktop' lacks MimeType key
File '/usr/share/applications/kde/groupwarewizard.desktop' lacks MimeType key
File '/usr/share/applications/kde/multisynk.desktop' lacks MimeType key
File '/usr/share/applications/kde/KMail.desktop' lacks MimeType key
File '/usr/share/applications/kde/konsolekalendar.desktop' lacks MimeType key
File '/usr/share/applications/kde/KNode.desktop' lacks MimeType key
File '/usr/share/applications/kde/knotes.desktop' lacks MimeType key
File '/usr/share/applications/kde/Kontact.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpalmdoc.desktop' lacks MimeType key
File '/usr/share/applications/kde/KOrn.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpilotdaemon.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpilot.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwikdisk.desktop' lacks MimeType key
File '/usr/share/applications/kde/irkick.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmlirc.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmdf.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdf.desktop' lacks MimeType key
File '/usr/share/applications/kde/khexedit.desktop' lacks MimeType key
File '/usr/share/applications/kde/thinkpad.desktop' lacks MimeType key
File '/usr/share/applications/kde/Kjots.desktop' lacks MimeType key
File '/usr/share/applications/kde/laptop.desktop' lacks MimeType key
File '/usr/share/applications/kde/pcmcia.desktop' lacks MimeType key
File '/usr/share/applications/kde/kvaio.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwalletconfig.desktop' lacks MimeType key
File '/usr/share/applications/kde/ktimer.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwalletmanager-kwalletd.desktop' lacks MimeTyp e key
File '/usr/share/applications/kde/kfilereplace.desktop' lacks MimeType key
File '/usr/share/applications/kde/klinkstatus.desktop' lacks MimeType key
File '/usr/share/applications/kde/kxsldbg.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksayit.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkttsd.desktop' lacks MimeType key
File '/usr/share/applications/kde/kttsmgr.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdevdesigner.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdevassistant.desktop' lacks MimeType key
File '/usr/share/applications/kde/serviceconfig.desktop' lacks MimeType key
File '/usr/share/applications/kde/userconfig.desktop' lacks MimeType key
File '/usr/share/applications/kde/mountconfig.desktop' lacks MimeType key
File '/usr/share/applications/kde/displayconfig.desktop' lacks MimeType key
File '/usr/share/applications/kde/fileshare.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmsambaconf.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmktalkd.desktop' lacks MimeType key

** (process:7317): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_de sktop_entries_lookup_group (entries, group_name) == NULL' failed
File '/usr/share/applications/kde/kcmkbfx.desktop' lacks MimeType key
[Invalid UTF-8] Could not parse file '/usr/share/applications/kde/kcm_knemo.desk top': desktop entry contain line 'Comment[de]=\xdcberwacht Netzwerk-Schnittstell en' which is not UTF-8
File '/usr/share/applications/template.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-file-management-properties.desktop' lacks  MimeType key
File '/usr/share/applications/gnome-volume-properties.desktop' lacks MimeType ke y
File '/usr/share/applications/sound-juicer.desktop' lacks MimeType key
File '/usr/share/applications/tsclient.desktop' lacks MimeType key
File '/usr/share/applications/network.desktop' lacks MimeType key
File '/usr/share/applications/time.desktop' lacks MimeType key
File '/usr/share/applications/services.desktop' lacks MimeType key
File '/usr/share/applications/users.desktop' lacks MimeType key
File '/usr/share/applications/disks.desktop' lacks MimeType key
File '/usr/share/applications/shares.desktop' lacks MimeType key
File '/usr/share/applications/update-manager.desktop' lacks MimeType key
File '/usr/share/applications/vino-preferences.desktop' lacks MimeType key
File '/usr/share/applications/gparted.desktop' lacks MimeType key
File '/usr/share/applications/xsane.desktop' lacks MimeType key
File '/usr/share/applications/gtweakui-menus.desktop' lacks MimeType key
File '/usr/share/applications/yelp.desktop' lacks MimeType key
File '/usr/share/applications/gok.desktop' lacks MimeType key
File '/usr/share/applications/gtweakui-session.desktop' lacks MimeType key
File '/usr/share/applications/gtweakui-nautilus.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-cd-burner.desktop' lacks MimeType key
File '/usr/share/applications/evolution.desktop' lacks MimeType key
File '/usr/share/applications/gtweakui-galeon.desktop' lacks MimeType key
File '/usr/share/applications/gnome-screenshot.desktop' lacks MimeType key
File '/usr/share/applications/gpaint.desktop' lacks MimeType key
File '/usr/share/applications/gnome-power-preferences.desktop' lacks MimeType ke y
File '/usr/share/applications/software-properties.desktop' lacks MimeType key
File '/usr/share/applications/hplip.desktop' lacks MimeType key
File '/usr/share/applications/gnome-screensaver-preferences.desktop' lacks MimeT ype key
File '/usr/share/applications/gnopernicus.desktop' lacks MimeType key
File '/usr/share/applications/scim-setup.desktop' lacks MimeType key
File '/usr/share/applications/anjuta.desktop' lacks MimeType key
File '/usr/share/applications/netapplet.desktop' lacks MimeType key
File '/usr/share/applications/Xfmime_edit.desktop' lacks MimeType key
File '/usr/share/applications/Xffm.desktop' lacks MimeType key
File '/usr/share/applications/xfce-xfcalendar-settings.desktop' lacks MimeType k ey
File '/usr/share/applications/xfcalendar.desktop' lacks MimeType key
File '/usr/share/applications/xfce-wm-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce-wmtweaks-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce-workspaces-settings.desktop' lacks MimeType k ey
File '/usr/share/applications/xfce-settings-manager.desktop' lacks MimeType key
File '/usr/share/applications/xfce-ui-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce-keyboard-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce-mouse-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce-display-settings.desktop' lacks MimeType key
File '/usr/share/applications/Terminal.desktop' lacks MimeType key
File '/usr/share/applications/xfce-backdrop-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce-menueditor.desktop' lacks MimeType key
File '/usr/share/applications/xfce-session-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce-splash-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce4-autostart-editor.desktop' lacks MimeType key
File '/usr/share/applications/xfce4-appfinder.desktop' lacks MimeType key
File '/usr/share/applications/xfce-mixer-settings.desktop' lacks MimeType key
File '/usr/share/applications/xfce4-taskmanager.desktop' lacks MimeType key
File '/usr/share/applications/xfprint.desktop' lacks MimeType key
File '/usr/share/applications/xfprint-manager.desktop' lacks MimeType key
File '/usr/share/applications/xfce-xfprint-settings.desktop' lacks MimeType key
File '/usr/share/applications/Thunar-bulk-rename.desktop' lacks MimeType key
File '/usr/share/applications/Thunar.desktop' lacks MimeType key
File '/usr/share/applications/xfce-filemanager-settings.desktop' lacks MimeType key
File '/usr/share/applications/Xfbook.desktop' lacks MimeType key
File '/usr/share/applications/Xfdiff.desktop' lacks MimeType key
File '/usr/share/applications/Xffstab.desktop' lacks MimeType key
File '/usr/share/applications/Xfglob.desktop' lacks MimeType key
File '/usr/share/applications/Xfrecent.desktop' lacks MimeType key
File '/usr/share/applications/Xfsamba.desktop' lacks MimeType key
File '/usr/share/applications/Xfapps.desktop' lacks MimeType key
File '/usr/share/applications/Xffrequent.desktop' lacks MimeType key
File '/usr/share/applications/Xftrash.desktop' lacks MimeType key
File '/usr/share/applications/Xflocate.desktop' lacks MimeType key
File '/usr/share/applications/Xficonview.desktop' lacks MimeType key
File '/usr/share/applications/Xftree.desktop' lacks MimeType key
File '/usr/share/applications/gtranslator.desktop' lacks MimeType key
File '/usr/share/applications/devhelp.desktop' lacks MimeType key
File '/usr/share/applications/baobab.desktop' lacks MimeType key
File '/usr/share/applications/kcmgtk-xdg.desktop' lacks MimeType key
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-csrc' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-chdr' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-copying' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-makefile' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' appl ication/x-shellscript' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /xml' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-patch' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-python' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /html' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-authors' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-install' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' appl ication/x-php' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /css' that contains invalid characters
File '/usr/share/applications/gtkedit.desktop' contains invalid MIME type ' text /x-sql' that contains invalid characters
File '/usr/share/applications/camorama.desktop' lacks MimeType key
File '/usr/share/applications/balsa.desktop' lacks MimeType key
File '/usr/share/applications/gcompris.desktop' lacks MimeType key
File '/usr/share/applications/dasher.desktop' lacks MimeType key
File '/usr/share/applications/gnome-keyring-manager.desktop' lacks MimeType key
File '/usr/share/applications/gcompris-edit.desktop' lacks MimeType key
File '/usr/share/applications/gnome-art.desktop' lacks MimeType key
File '/usr/share/applications/regexxer.desktop' lacks MimeType key
File '/usr/share/applications/gnome-splashscreen-manager.desktop' lacks MimeType  key
File '/usr/share/applications/gtetrinet.desktop' lacks MimeType key
File '/usr/share/applications/seahorse.desktop' lacks MimeType key
File '/usr/share/applications/seahorse-pgp-preferences.desktop' lacks MimeType k ey
File '/usr/share/applications/gnome-ppp.desktop' lacks MimeType key

``` Thanks for the reply by the way.

---

### Post by Miguel on 2006-07-14
Good morning Malac,

The good news:
[list]
[*]From what I've read, this message appears generaly due to a duplicated MIME type. So, it appears everytime you install or update a package that reads or writes info to the mimetype database.
[*]Although it reads "CRITICAL", it is not. The system is still usable.
[*]Maxddark also had the "CRITICAL" thing in "kcmkbfx". It is possible that reinstalling the package related to this file fixes it. I've just found that this package is... kbfx*. Reinstalling also ktalkd wouldn't hurt.
[/list]

The bad news:
[list]
[*]My knowledge finishes here, so if that doesn't help your problem I don't have further ideas.
[*]A dev will be more able than I am in understanding the messages and troubleshooting you.
[*]As two people (at least) have suffered from this, it may be time for bughunting!.
[/list]

So this is basically it. I'll perform a search in Malone to see if anything similar has been reported.

Hope it helps ;)

---

### Post by Miguel on 2006-07-14
Hi malac,

Have a look at this:

[https://launchpad.net/distros/ubuntu/+source/kcontrol-autostart/+bug/49859](https://launchpad.net/distros/ubuntu/+source/kcontrol-autostart/+bug/49859)

Maybe editing /usr/share/applications/kcmkbfx.desktop will reveal something similar. What do you think?

---

### Post by Malac on 2006-07-14
Thanks miguel for pointing me in the right direction.
The strange thing is I don't have either of the two files that are listed in the database on my system at all.
'/usr/share/applications/kde/kcmkbfx.desktop'
'/usr/share/applications/kde/kcm_knemo.desktop'
Wierd. :-k

---

### Post by Miguel on 2006-07-14
Helo again Malac,

Have you ever used the "locate" command? Whenever you are in doubt where a file is, locate will tell you. You only need an up-to-date database (there is a ubuntu service that updates the locate database every day). So you can try
```

locate kcmkbfx.desktop
locate kcm_knemo.desktop

```

If it complains about the database, you'll have to build it. The command is (it needs root power):
```

sudo locate -u

```


BTW: What KDE are you using?

---

### Post by Malac on 2006-07-14
Sorry Miguel I was just being dense. :oops:
I looked at the files in nautilus and just saw the "friendly" names but realised fairly quickly how stupid I'd been.

The files are there but i can't see anything wrong with them compared to the others.

One of the errors is because the [de] entry has a Ü in it which is not UTF-8.
But the other seems okay. :confused:

I'm using the latest KDE from the repositories 5.45ubuntu1.

Thanks anyway. Hopefully it will get fixed with an update.

---

### Post by Miguel on 2006-07-17
Sorry for the late reply, Malac. I've been away the whole weekend. Anyway, I had to tell you I know no better. Maybe you can fill a bug report?

---

