---
title: "Mini Ubuntu based distro sound issue."
date: 2009-10-02
forum: Programming Talk
---

### Post by kev000 on 2009-10-02
I'm one of the dev's for LinuxICE, a ubuntu 9.04 based distro for Car Entertainment/Infotainment systems.  Right now we are currently beta and have run into a wall with getting sound to work.

In order to make booting simpler/faster, we don't use GDM or any other login manager.  We simply log-in directly from tty1 and startx.  In Xsession.d we have a simple startup script that launches our software and matchbox-window-manager with ck-launch-session.  This gives us the correct permissions for the audio device, but when we play, no sound.  Pulseaudio thinks it's playing but no output.

I'm wondering if anyone has any suggestions on things to try.  We are really stuck until we get sound working.

If you want to take a look, you can download the 350mb image here: [http://linuxice.openice.org/daily-live/LinuxICE2-2009-09-27.iso](http://linuxice.openice.org/daily-live/LinuxICE2-2009-09-27.iso)

it boots in vbox.  Please help!  Any suggestions on things to try would be awesome.  Thanks!

---

### Post by kev000 on 2009-10-02
Oh.  One more note: in Xsession.d there is a script that starts up console-kit.  This wasn't working before for some reason and the result was no permissions to the /dev/snd/* devices for normal users.  Once we started launching matchbox-window-manager with ck-launch-session matchbox-window-manager ... we at least got the permissions correct.

It still may be a permissions thing because we can't seem to get auto mounting working still either in thunar/nautilus.

Plz help. Thanks again!

---

