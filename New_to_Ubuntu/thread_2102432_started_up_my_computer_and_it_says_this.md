---
title: "started up my computer and it says this"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by blake7 on 2013-01-07
Atom CPU d525 1.89 ghz x4
Acer revo
ubuntu 12.04



failed to run /usr/share/apport/apport-gtk as user root
unable to copy the user xauthorization



can you help

thank you

---

### Post by tgalati4 on 2013-01-07
Apport is the crash reporting system:

tgalati4@Dell600m-mint14 ~/Desktop $ apt-cache search apport
apport - automatically generate crash reports for debugging
apport-gtk - GTK+ frontend for the apport crash report system
apport-retrace - tools for reprocessing Apport crash reports
apport-symptoms - symptom scripts for apport
dh-apport - debhelper extension for the apport crash report system
python-apport - Python library for Apport crash report handling
python3-apport - Python 3 library for Apport crash report handling
apport-kde - KDE frontend for the apport crash report system
reportbug - reports bugs in the Debian distribution
apport-hooks-medibuntu - Apport hooks for Medibuntu

So it looks like something crashed, related to gtk graphics, and that crash has probably also messed up the window that will display the crash dialog box.

Try rebooting into recovery mode (text termnal).

```
cd /var/log
less Xorg.0.log

```

Spacebar to page forward, "q" to quit.  Make note of errors (EE) and anything else that looks related to severe graphical errors.  Paste them here.

It could be a big file, so instead of paging through the entire file, you can cheat:

```
grep EE Xorg.0.log
```

Warnings are OK:

tgalati4@Dell600m-mint14 /var/log $ grep WW Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.928] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.928] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.928] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.928] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.928] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.928] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    39.206] (WW) Warning, couldn't open module fglrx
[    39.299] (WW) Warning, couldn't open module fglrx
[    39.353] (WW) Falling back to old probe method for modesetting
[    39.354] (WW) Falling back to old probe method for fbdev
[    41.142] (WW) VESA(0): Unable to estimate virtual size

---

