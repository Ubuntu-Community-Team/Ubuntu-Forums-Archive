---
title: "Openoffice Upgrade Causing Problems."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by NeonSamurai on 2008-05-12
Hi,

I've just rebuilt a laptop using 7.10 and left it doing its update/upgrades, but when I come back to it I find this rather lengthy error:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-opensymbol (1:2.3.0-1ubuntu5.4) ...
Updating fontconfig cache...
/usr/share/fonts: failed to write cache
/usr/share/fonts/X11: failed to write cache
/usr/share/fonts/X11/100dpi: failed to write cache
/usr/share/fonts/X11/75dpi: failed to write cache
/usr/share/fonts/X11/Type1: failed to write cache
/usr/share/fonts/X11/encodings: failed to write cache
/usr/share/fonts/X11/encodings/large: failed to write cache
/usr/share/fonts/X11/misc: failed to write cache
/usr/share/fonts/X11/util: failed to write cache
/usr/share/fonts/truetype: failed to write cache
/usr/share/fonts/truetype/arphic: failed to write cache
/usr/share/fonts/truetype/freefont: failed to write cache
/usr/share/fonts/truetype/kochi: failed to write cache
/usr/share/fonts/truetype/thai: failed to write cache
/usr/share/fonts/truetype/ttf-arabeyes: failed to write cache
/usr/share/fonts/truetype/ttf-bitstream-vera: failed to write cache
/usr/share/fonts/truetype/ttf-dejavu: failed to write cache
/usr/share/fonts/truetype/ttf-gentium: failed to write cache
/usr/share/fonts/truetype/ttf-indic-fonts-core: failed to write cache
/usr/share/fonts/truetype/ttf-lao: failed to write cache
/usr/share/fonts/truetype/ttf-malayalam-fonts: failed to write cache
/usr/share/fonts/truetype/ttf-mgopen: failed to write cache
/usr/share/fonts/truetype/unfonts: failed to write cache
/usr/share/fonts/type1: failed to write cache
/usr/share/fonts/type1/gsfonts: failed to write cache
/usr/local/share/fonts: failed to write cache
/var/lib/defoma/fontconfig.d: failed to write cache
/var/lib/defoma/fontconfig.d/A: failed to write cache
/var/lib/defoma/fontconfig.d/B: failed to write cache
/var/lib/defoma/fontconfig.d/C: failed to write cache
/var/lib/defoma/fontconfig.d/D: failed to write cache
/var/lib/defoma/fontconfig.d/E: failed to write cache
/var/lib/defoma/fontconfig.d/F: failed to write cache
/var/lib/defoma/fontconfig.d/G: failed to write cache
/var/lib/defoma/fontconfig.d/H: failed to write cache
/var/lib/defoma/fontconfig.d/J: failed to write cache
/var/lib/defoma/fontconfig.d/K: failed to write cache
/var/lib/defoma/fontconfig.d/L: failed to write cache
/var/lib/defoma/fontconfig.d/M: failed to write cache
/var/lib/defoma/fontconfig.d/N: failed to write cache
/var/lib/defoma/fontconfig.d/O: failed to write cache
/var/lib/defoma/fontconfig.d/P: failed to write cache
/var/lib/defoma/fontconfig.d/R: failed to write cache
/var/lib/defoma/fontconfig.d/S: failed to write cache
/var/lib/defoma/fontconfig.d/T: failed to write cache
/var/lib/defoma/fontconfig.d/U: failed to write cache
/var/lib/defoma/fontconfig.d/V: failed to write cache
/var/lib/defoma/fontconfig.d/m: failed to write cache
/var/lib/defoma/fontconfig.d/u: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 49
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 1:2.3.0); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 1:2.3.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-math
 python-uno
 openoffice.org-writer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now this laptop is going to be used as a DNS/DHCP server, so I could happily lose all the openoffice files, but I'm not sure that they're actually the root of the problem.

Any suggestions on how to proceed?

Thanks


Mark

---

### Post by HotShotDJ on 2008-05-12
Open a terminal and type: ```
sudo dpkg --configure -a
```That should fix things up.

---

### Post by NeonSamurai on 2008-05-12
Thanks HotshotDJ,

Unfortunately the problem persists. I ran the code like you suggested, but it ran the same error messages again. I'm not sure if it's some spurious font that's messing the whole thing up and any programs associated with it.

Any other ideas of what I could try (like I said I can strip out openoffice if necessary).

Thanks


Mark

---

### Post by HotShotDJ on 2008-05-12
> **NeonSamurai said:**
> Any other ideas of what I could try (like I said I can strip out openoffice if necessary).What I would do at this point is use Synaptic Package Manager to search for and remove all openoffice packages.  THEN, using the terminal, run "sudo apt-get autoremove" to get rid of any cruft left behind.  Then finally, just to be safe, run "sudo dpkg --configure -a" just to be sure there is nothing else gumming up the works.

After that, you can try reinstalling openoffice or just leave it gone.  Best of luck with this.  I'm heading to bed, but will check back to see how it went when I wake up.

---

### Post by watsbe on 2008-05-12
It could be simply a space problem.  Try opening a terminal and typing
df
and see if anything is at 100%

---

