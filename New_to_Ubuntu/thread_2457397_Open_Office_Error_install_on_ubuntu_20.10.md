---
title: "Open Office Error install on ubuntu 20.10"
date: 2021-02-01
forum: New to Ubuntu
---

### Post by 9eorg on 2021-02-01
Gday Linux / ubuntu peeps :)

First time user, long time procrastinator for using Linux here.
Have just uninstalled LibraOffice to install open office, however always seem to get error when unpacking the .deb files through the terminal.  (I will post script below)

Questions:
1. How do I check what is left of the libraOffice install after I already removed it.
2. If some open office files have been installed, is there a way to check so I can remove to try the install again? (clean install of open office as it were)
3. Any suggestions for a newb for learning linux language, ie list of commands to use in terminal as linux reminds me a lot of DOS back in the day but that was a good 30's yrs ago I played with that.

Anywho thanks for any help and info peeps and I believe I have a converted user even after just a few days, just need to get my head around linux some more to make a full switch.

Cheers,

9eorg :)

```
openoffice_4.1.8-3_amd64.deb
openoffice-base_4.1.8-3_amd64.deb
openoffice-brand-base_4.1.8-3_amd64.deb
openoffice-brand-calc_4.1.8-3_amd64.deb
openoffice-brand-draw_4.1.8-3_amd64.deb
openoffice-brand-en-us_4.1.8-3_amd64.deb
openoffice-brand-impress_4.1.8-3_amd64.deb
openoffice-brand-math_4.1.8-3_amd64.deb
openoffice-brand-writer_4.1.8-3_amd64.deb
openoffice-calc_4.1.8-3_amd64.deb
openoffice-core01_4.1.8-3_amd64.deb
openoffice-core02_4.1.8-3_amd64.deb
openoffice-core03_4.1.8-3_amd64.deb
openoffice-core04_4.1.8-3_amd64.deb
openoffice-core05_4.1.8-3_amd64.deb
openoffice-core06_4.1.8-3_amd64.deb
openoffice-core07_4.1.8-3_amd64.deb
openoffice-draw_4.1.8-3_amd64.deb
openoffice-en-us_4.1.8-3_amd64.deb
openoffice-en-us-base_4.1.8-3_amd64.deb
openoffice-en-us-calc_4.1.8-3_amd64.deb
openoffice-en-us-draw_4.1.8-3_amd64.deb
openoffice-en-us-help_4.1.8-3_amd64.deb
openoffice-en-us-impress_4.1.8-3_amd64.deb
openoffice-en-us-math_4.1.8-3_amd64.deb
openoffice-en-us-res_4.1.8-3_amd64.deb
openoffice-en-us-writer_4.1.8-3_amd64.deb
openoffice-gnome-integration_4.1.8-3_amd64.deb
openoffice-graphicfilter_4.1.8-3_amd64.deb
openoffice-images_4.1.8-3_amd64.deb
openoffice-impress_4.1.8-3_amd64.deb
openoffice-javafilter_4.1.8-3_amd64.deb
openoffice-math_4.1.8-3_amd64.deb
openoffice-ogltrans_4.1.8-3_amd64.deb
openoffice-onlineupdate_4.1.8-3_amd64.deb
openoffice-ooofonts_4.1.8-3_amd64.deb
openoffice-ooolinguistic_4.1.8-3_amd64.deb
openoffice-pyuno_4.1.8-3_amd64.deb
openoffice-ure_4.1.8-3_amd64.deb
openoffice-writer_4.1.8-3_amd64.deb
openoffice-xsltfilter_4.1.8-3_amd64.deb
georg@dutch:~/Downloads/en-US/DEBS$ sudo dpkg -i *.deb
dpkg: regarding openoffice_4.1.8-3_amd64.deb containing openoffice:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice
dpkg: regarding openoffice-base_4.1.8-3_amd64.deb containing openoffice-base:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-base provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-base_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-base
dpkg: regarding openoffice-brand-base_4.1.8-3_amd64.deb containing openoffice-brand-base:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-brand-base provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-brand-base_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-brand-base
dpkg: regarding openoffice-brand-calc_4.1.8-3_amd64.deb containing openoffice-brand-calc:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-brand-calc provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-brand-calc_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-brand-calc
dpkg: regarding openoffice-brand-draw_4.1.8-3_amd64.deb containing openoffice-brand-draw:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-brand-draw provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-brand-draw_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-brand-draw
dpkg: regarding openoffice-brand-en-us_4.1.8-3_amd64.deb containing openoffice-brand-en-us:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-brand-en-us provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-brand-en-us_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-brand-en-us
dpkg: regarding openoffice-brand-impress_4.1.8-3_amd64.deb containing openoffice-brand-impress:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-brand-impress provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-brand-impress_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-brand-impress
dpkg: regarding openoffice-brand-math_4.1.8-3_amd64.deb containing openoffice-brand-math:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-brand-math provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-brand-math_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-brand-math
dpkg: regarding openoffice-brand-writer_4.1.8-3_amd64.deb containing openoffice-brand-writer:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-brand-writer provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-brand-writer_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-brand-writer
dpkg: regarding openoffice-calc_4.1.8-3_amd64.deb containing openoffice-calc:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-calc provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-calc_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-calc
dpkg: regarding openoffice-core01_4.1.8-3_amd64.deb containing openoffice-core01:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-core01 provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-core01_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-core01
dpkg: regarding openoffice-core02_4.1.8-3_amd64.deb containing openoffice-core02:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-core02 provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-core02_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-core02
dpkg: regarding openoffice-core03_4.1.8-3_amd64.deb containing openoffice-core03:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-core03 provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-core03_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-core03
dpkg: regarding openoffice-core04_4.1.8-3_amd64.deb containing openoffice-core04:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-core04 provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-core04_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-core04
dpkg: regarding openoffice-core05_4.1.8-3_amd64.deb containing openoffice-core05:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-core05 provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-core05_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-core05
dpkg: regarding openoffice-core06_4.1.8-3_amd64.deb containing openoffice-core06:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-core06 provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-core06_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-core06
dpkg: regarding openoffice-core07_4.1.8-3_amd64.deb containing openoffice-core07:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-core07 provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-core07_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-core07
dpkg: regarding openoffice-draw_4.1.8-3_amd64.deb containing openoffice-draw:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-draw provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-draw_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-draw
dpkg: regarding openoffice-en-us_4.1.8-3_amd64.deb containing openoffice-en-us:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us
dpkg: regarding openoffice-en-us-base_4.1.8-3_amd64.deb containing openoffice-en-us-base:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-base provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-base_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-base
dpkg: regarding openoffice-en-us-calc_4.1.8-3_amd64.deb containing openoffice-en-us-calc:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-calc provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-calc_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-calc
dpkg: regarding openoffice-en-us-draw_4.1.8-3_amd64.deb containing openoffice-en-us-draw:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-draw provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-draw_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-draw
dpkg: regarding openoffice-en-us-help_4.1.8-3_amd64.deb containing openoffice-en-us-help:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-help provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-help_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-help
dpkg: regarding openoffice-en-us-impress_4.1.8-3_amd64.deb containing openoffice-en-us-impress:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-impress provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-impress_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-impress
dpkg: regarding openoffice-en-us-math_4.1.8-3_amd64.deb containing openoffice-en-us-math:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-math provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-math_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-math
dpkg: regarding openoffice-en-us-res_4.1.8-3_amd64.deb containing openoffice-en-us-res:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-res provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-res_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-res
dpkg: regarding openoffice-en-us-writer_4.1.8-3_amd64.deb containing openoffice-en-us-writer:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-en-us-writer provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-en-us-writer_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-en-us-writer
dpkg: regarding openoffice-gnome-integration_4.1.8-3_amd64.deb containing openoffice-gnome-integration:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-gnome-integration provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-gnome-integration_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-gnome-integration
dpkg: regarding openoffice-graphicfilter_4.1.8-3_amd64.deb containing openoffice-graphicfilter:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-graphicfilter provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-graphicfilter_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-graphicfilter
dpkg: regarding openoffice-images_4.1.8-3_amd64.deb containing openoffice-images:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-images provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-images_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-images
dpkg: regarding openoffice-impress_4.1.8-3_amd64.deb containing openoffice-impress:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-impress provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-impress_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-impress
dpkg: regarding openoffice-javafilter_4.1.8-3_amd64.deb containing openoffice-javafilter:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-javafilter provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-javafilter_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-javafilter
dpkg: regarding openoffice-math_4.1.8-3_amd64.deb containing openoffice-math:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-math provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-math_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-math
dpkg: regarding openoffice-ogltrans_4.1.8-3_amd64.deb containing openoffice-ogltrans:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-ogltrans provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-ogltrans_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-ogltrans
dpkg: regarding openoffice-onlineupdate_4.1.8-3_amd64.deb containing openoffice-onlineupdate:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-onlineupdate provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-onlineupdate_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-onlineupdate
dpkg: regarding openoffice-ooofonts_4.1.8-3_amd64.deb containing openoffice-ooofonts:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-ooofonts provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-ooofonts_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-ooofonts
dpkg: regarding openoffice-ooolinguistic_4.1.8-3_amd64.deb containing openoffice-ooolinguistic:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-ooolinguistic provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-ooolinguistic_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-ooolinguistic
dpkg: regarding openoffice-pyuno_4.1.8-3_amd64.deb containing openoffice-pyuno:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-pyuno provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-pyuno_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-pyuno
dpkg: regarding openoffice-ure_4.1.8-3_amd64.deb containing openoffice-ure:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-ure provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-ure_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-ure
dpkg: regarding openoffice-writer_4.1.8-3_amd64.deb containing openoffice-writer:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-writer provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-writer_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-writer
dpkg: regarding openoffice-xsltfilter_4.1.8-3_amd64.deb containing openoffice-xsltfilter:
 libreoffice-common conflicts with openoffice.org-unbundled
  openoffice-xsltfilter provides openoffice.org-unbundled and is to be installed.

dpkg: error processing archive openoffice-xsltfilter_4.1.8-3_amd64.deb (--install):
 conflicting packages - not installing openoffice-xsltfilter
Errors were encountered while processing:
```

---

### Post by Impavidus on 2021-02-01
Remove all libreoffice packages before installing openoffice. They don't like each other.
```
sudo apt-get remove libreoffice*
```

Keep in mind that when you install software as .deb files not from some repository, you won't get automatic upgrades.

---

### Post by 9eorg on 2021-02-01
Sweet thanks  				 				 					 						 	[**[COLOR=#000000]Impavidus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721"), 

I have tried that command line however I will give it another go.

As to .deb file of open office I thought you can only get open office as a .deb file as have not found command line for repository??  Am I incorrect in the assumption?

Cheers.

Impavidus that worked mate .. Thanks Heaps ! :)

---

### Post by grahammechanical on 2021-02-01
> As to .deb file of open office I thought you can only get open office as  a .deb file as have not found command line for repository??  Am I  incorrect in the assumption?


I do not understand you completely. A lot of software in the Ubuntu repositories (sources) are as deb files. Ubuntu accepts the standard Debian package format (deb). It is true that some applications are packaged in a different format. That is, as Snaps. I think that LibreOffice is one of those applications.

Open Office is not in the Ubuntu repositories. When I first installed Ubuntu the default office suite was Open Office. But all that changed when community Open Office developers decided to fork the code and develop it as LibreOffice.

There are also versions of Open Office to install in Redhat versions of Linux (rpm), Windows (exe) and MacOS (DMG) but to install Open Office on a Linux version based on Debian, such as Ubuntu, it has to be in the Debian package format (deb).

Regards

---

### Post by ActionParsnip on 2021-02-01
You may want to blacklist the libreoffice debs as (I think) they are part of the ubuntu-desktop metapackage

---

### Post by 9eorg on 2021-02-01
Alright thanks for clarif[COLOR=#000000]ing [**[COLOR=#000000]grahammechanical[/COLOR]**]("https://ubuntuforums.org/member.php?u=1087323"),  looks like I installed the 'deb' version of open office.  Ubuntu did  have libra office installed when I first installed but a work colleague  mentioned open office would may be better.  Any thoughts on the  difference between the two and which one better?   [/COLOR]  [URL="https://ubuntuforums.org/member.php?u=1087323"][COLOR=#000000]
[/COLOR][/URL]

> **ActionParsnip said:**
> You may want to blacklist the libreoffice debs as (I think) they are part of the ubuntu-desktop metapackage

I dont quite understand what you mean here sorry Action?  Is there something else I should do now that I have installed open office rather then Libra?

---

### Post by Impavidus on 2021-02-01
Openoffice is not in the official Ubuntu repositories. There may exist some third-party repository (a PPA) from which it may be installed, or it can be installed from .deb file using dpkg, as you did. In the latter case, you won't get automatic bugfixes. If you get your software from PPA, you may get automatic bugfixes. It's still less reliable and secure than software from the official repositories.

I don't use Openoffice. I have Libreoffice installed, but rarely use it. I'm not particularly fond of this office-like software. I can't say which is better.

---

### Post by Hagar Delest on 2021-02-01
> **9eorg said:**
> Ubuntu did  have libra office installed when I first installed but a work colleague  mentioned open office would may be better.  Any thoughts on the  difference between the two and which one better?
I have been a long time user and supporter of AOO (using it from OOo in 2006).
I was disappointed by the forking of LO. But after several years, it is now clear that AOO has lost its momentum and LO is best. I've switched to LO last year and I don't regret.
So I were you I would come back to LO. Now, you can just try and make your own opinion. Note that sudo apt purge libreoffice* is recommended to get rid of all the remnants of LO.

---

### Post by 9eorg on 2021-02-03
smashing thanks for the info mate much appreciated :)

---

