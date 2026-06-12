---
title: "After 3 years of using Linux I've finally messed up gnome"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Warpnow on 2008-08-24
I did an upgrade. When I did it, my menus froze, so I rebooted. Now, when I boot up, the menus in gnome never load up, so I thought I'd try and reinstall the ubuntu desktop, and this is what I get:
```

ase@chase-desktop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtelepathy2 libjinglep2p0.3-0 planner python-hippocanvas
  xserver-xorg-video-i810 libgoffice-0-6-common xserver-xorg-video-ati
  telepathy-gabble libpigment0.3-5 sugar-toolkit python-numpy dia-libs
  python-avahi gstreamer0.10-plugins-farsight sugar-artwork python-json
  libgoffice-0-6 libots0 g++-4.2 libmatchbox1 libfarsight0.1-3
  sugar-presence-service libmp4v2-0 abiword abiword-common leafpad
  libjinglexmllite0.3-0 lxde-common libpoppler-qt4-2 libexiv2-2
  telepathy-salut liblapack3gf libstdc++6-4.2-dev cupsys-common libgnutlsxx13
  lxde-settings-daemon pcmanfm matchbox-window-manager dia-gnome libmagick++10
  kplato-kde4 python-xapian libwv-1.2-3 python-storm libtelepathy-glib0
  libjinglebase0.3-0 libaiksaurusgtk-1.2-0c2a python-telepathy
  libgsf-gnome-1-114 libopencdk10-dev telepathy-stream-engine
  python-twisted-web2 libblas3gf gnumeric-common gpicview liblzo2-dev
  dia-common gnumeric lxpanel libgfortran3 gcc-4.2-multilib libloudmouth1-0
  inkscape xarchiver libjinglexmpp0.3-0 libhippocanvas-1-0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ubuntu-desktop
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
32 not fully installed or removed.
Need to get 0B/26.9kB of archives.
After this operation, 53.2kB of additional disk space will be used.
Selecting previously deselected package ubuntu-desktop.
(Reading database ... 272116 files and directories currently installed.)
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.110_amd64.deb) ...
Setting up rarian-compat (0.8.0-1ubuntu3) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing rarian-compat (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.23); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends oNo apport report written because the error message indicates its a followup error from a previous failure.
                                                         No apport report written because the error message indicates its a followup error from a previous failure.
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   n capplets-data (<< 1:2.24); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.23); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.24); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.24); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                             gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.23); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.24); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gnome-control-center (>= 1:2.20.1); however:
  Package gnome-control-center is not configured yet.
 gnome-core depends on gedit (>= 2.20.4); however:
  Package gedit is not configured yet.
 gnome-core depends on gnome-applets (>= 2.20.0); however:
  Package gnome-applets is not configured yet.
 gnome-core depends on gnome-panel (>= 2.20.2); however:
  Package gnome-panel is not configured yet.
 gnome-core depends on gnome-session (>= 2.20.2); however:
  Package gnome-session is not configured yet.
 gnome-core depends on gnome-terminal (>= 2.18.3); however:
  Package gnome-terminal is not configured yet.
 gnome-core depends on nautilus (>= 2.20.0); however:
  Package nautilus is not configured yet.
 gnome-core depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not configured yet.
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.20.2.4ubuntu1); however:
  Package gnome-core is not configured yet.
 gnome-desktop-environment depends on bug-buddy (>= 2.20.1); however:
  Package bug-buddNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            y is not configured yet.
 gnome-desktop-environment depends on fast-user-switch-applet (>= 2.18.0); however:
  Package fast-user-switch-applet is not configured yet.
 gnome-desktop-environment depends on gnome-system-monitor (>= 2.20.1); however:
  Package gnome-system-monitor is not configured yet.
 gnome-desktop-environment depends on gnome-utils (>= 2.20.0.1); however:
  Package gnome-utils is not configured yet.
 gnome-desktop-environment depends on gucharmap (>= 1.10.1); however:
  Package gucharmap is not configured yet.
 gnome-desktop-environment depends on nautilus-cd-burner (>= 2.20.0); however:
  Package nautilus-cd-burner is not configured yet.
 gnome-desktop-environment depends on zenity (>= 2.20.1); however:
  Package zenity is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of planner:
 planner depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing planner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on gnome-utils; however:
  Package gnome-utils is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on language-selector; however:
  Package language-seNo apport report written because MaxReports is reached already
   lector is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on nautilus-cd-burner; however:
  Package nautilus-cd-burner is not configured yet.
 ubuntu-desktop depends on rarian-compat; however:
  Package rarian-compat is not configured yet.
 ubuntu-desktop depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rarian-compat
 gnome-applets-data
 capplets-data
 gnome-control-center
 gnome-session
 gnome-panel-data
 gnome-panel
 gnome-applets
 ubuntu-docs
 synaptic
 gnome-app-install
 apturl
 bug-buddy
 fast-user-switch-applet
 gedit
 gnome-terminal
 nautilus-data
 nautilus
 gnome-core
 gnome-system-monitor
 gnome-utils
 gucharmap
 nautilus-cd-burner
 zenity
 gnome-desktop-environment
 jockey-gtk
 language-selector
 nautilus-share
 planner
 software-properties-gtk
 update-manager
 update-notifier
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by imon9 on 2008-08-24
please do a "sudo apt-get update"
it will tell u to fix the broken pakages with a dpkg command
so, just type the suggested command, and it will continue upgrading from where it left off

everything mess up coz u did not let the upgrade finish installing, i think

---

### Post by SpaceMaster on 2008-08-24
I broke my x this morning, as well.  During an update, the computer froze, and had to be forced to restart.  This broke several packages that were in the process of installing.  The fixes were sort of a work-around, but after a little joshling, I got things to function within reason.  First, I ran
```
sudo apt-get update
```
this prompted me to run
```
sudo dpkg --configure -a
```
which picked up where the installation process previously crashed.  This cleaned up the broken packages, but I still was stuck with a broken X.  For this, I ran in low-graphics mode, and before logging in, clicked "Configure".  There, I manually selected my graphics card, and screen.  Although the auto-detect did not function properly, I was still able to manually enable these while scrolling through the list.  The "Test" feature failed, but knowing for certain my configurations were correct, I accepted them anyhow, and rebooted.

That was that.  Everything now works, although I did have to re-enable the restricted drivers and desktop effects.

---

### Post by Warpnow on 2008-08-24
Sudo apt-get update runs without flaw.

I then tried sudo dpkg --configure -a

```

chase@chase-desktop:~$ sudo dpkg --configure -a
[sudo] password for chase: 
Setting up rarian-compat (0.8.0-1ubuntu3) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing rarian-compat (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gnome-terminal (>= 2.18.3); however:
  Package gnome-terminal is not configured yet.
 gnome-core depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not configured yet.
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.20.2.4ubuntu1); however:
  Package gnome-core is not configured yet.
 gnome-desktop-environment depends on gnome-system-monitor (>= 2.20.1); however:
  Package gnome-system-monitor is not configured yet.
 gnome-desktop-environment depends on zenity (>= 2.20.1); however:
  Package zenity is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.23); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.24); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of planner:
 planner depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing planner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.23); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.24); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on rarian-compat; however:
  Package rarian-compat is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.24); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.23); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.24); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rarian-compat
 zenity
 ubuntu-docs
 gnome-terminal
 gnome-system-monitor
 capplets-data
 gnome-core
 gedit
 gnome-desktop-environment
 nautilus-data
 gnome-control-center
 synaptic
 bug-buddy
 gnome-session
 planner
 gucharmap
 jockey-gtk
 nautilus
 gnome-applets-data
 ubuntu-desktop
 gnome-utils
 gnome-panel-data
 gnome-applets
 update-manager
 software-properties-gtk
 apturl
 language-selector
 nautilus-share
 nautilus-cd-burner
 gnome-panel
 gnome-app-install
 fast-user-switch-applet
 update-notifier

```

---

### Post by picpak on 2008-08-24
Try running

```
sudo apt-get install -f
```

Don't know how you managed to remove scrollkeeper...

---

### Post by Warpnow on 2008-08-24
```
chase@chase-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
32 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up rarian-compat (0.8.0-1ubuntu3) ...
update-xmlcatalog: error: entity already registered
dpkg: error processing rarian-compat (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.23); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends oNo apport report written because the error message indicates its a followup error from a previous failure.
                                                         No apport report written because the error message indicates its a followup error from a previous failure.
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   n capplets-data (<< 1:2.24); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-control-center (>= 1:2.22); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel-data:
 gnome-panel-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-panel-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.23); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.24); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.24); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
 apturl depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                             gnome-terminal depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-data:
 nautilus-data depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing nautilus-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on nautilus-data (>= 1:2.23); however:
  Package nautilus-data is not configured yet.
 nautilus depends on nautilus-data (<< 1:2.24); however:
  Package nautilus-data is not configured yet.
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gnome-control-center (>= 1:2.20.1); however:
  Package gnome-control-center is not configured yet.
 gnome-core depends on gedit (>= 2.20.4); however:
  Package gedit is not configured yet.
 gnome-core depends on gnome-applets (>= 2.20.0); however:
  Package gnome-applets is not configured yet.
 gnome-core depends on gnome-panel (>= 2.20.2); however:
  Package gnome-panel is not configured yet.
 gnome-core depends on gnome-session (>= 2.20.2); however:
  Package gnome-session is not configured yet.
 gnome-core depends on gnome-terminal (>= 2.18.3); however:
  Package gnome-terminal is not configured yet.
 gnome-core depends on nautilus (>= 2.20.0); however:
  Package nautilus is not configured yet.
 gnome-core depends on rarian-compat | scrollkeeper; however:
  Package rarian-compat is not configured yet.
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gucharmap:
 gucharmap depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing gucharmap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on scrollkeeper; however:
  Package scrollkeeper is not installed.
  Package rarian-compat which provides scrollkeeper is not configured yet.
dpkg: error processing zenity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.20.2.4ubuntu1); however:
  Package gnome-core is not configured yet.
 gnome-desktop-environment depends on bug-buddy (>= 2.20.1); however:
  Package bug-buddNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              y is not configured yet.
 gnome-desktop-environment depends on fast-user-switch-applet (>= 2.18.0); however:
  Package fast-user-switch-applet is not configured yet.
 gnome-desktop-environment depends on gnome-system-monitor (>= 2.20.1); however:
  Package gnome-system-monitor is not configured yet.
 gnome-desktop-environment depends on gnome-utils (>= 2.20.0.1); however:
  Package gnome-utils is not configured yet.
 gnome-desktop-environment depends on gucharmap (>= 1.10.1); however:
  Package gucharmap is not configured yet.
 gnome-desktop-environment depends on nautilus-cd-burner (>= 2.20.0); however:
  Package nautilus-cd-burner is not configured yet.
 gnome-desktop-environment depends on zenity (>= 2.20.1); however:
  Package zenity is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gnome-terminal; however:
  Package gnome-terminal is not configured yet.
 ubuntu-desktop depends on gnome-utils; however:
  Package gnome-utils is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on language-selector; however:
  Package language-selector is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on nautilus-cd-burner; however:
  Package nautilus-cd-burner is not configured yet.
 ubuntu-desktop depends on rarian-compat; however:
  Package rarian-compat is not cNo apport report written because MaxReports is reached already
              onfigured yet.
 ubuntu-desktop depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rarian-compat
 gnome-applets-data
 capplets-data
 gnome-control-center
 gnome-session
 gnome-panel-data
 gnome-panel
 gnome-applets
 ubuntu-docs
 synaptic
 gnome-app-install
 apturl
 bug-buddy
 fast-user-switch-applet
 gedit
 gnome-terminal
 nautilus-data
 nautilus
 gnome-core
 gnome-system-monitor
 gnome-utils
 gucharmap
 nautilus-cd-burner
 zenity
 gnome-desktop-environment
 jockey-gtk
 language-selector
 nautilus-share
 software-properties-gtk
 update-manager
 update-notifier
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
chase@chase-desktop:~$ 

```

Bleh, I really don't want to have to reformat. I don't have a drive large enough to keep all my files during the install...

---

### Post by picpak on 2008-08-24
Can you post your /etc/apt/sources.list? There may be an unofficial repository that's screwing things up.

---

