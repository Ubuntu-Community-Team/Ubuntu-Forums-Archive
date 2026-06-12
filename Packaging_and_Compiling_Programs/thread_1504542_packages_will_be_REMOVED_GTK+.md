---
title: "packages will be REMOVED: GTK+"
date: 2010-06-08
forum: Packaging and Compiling Programs
---

### Post by fopetesl on 2010-06-08
I'm trying to develop a GUI using C & GTK+ in LUCID.
The advice is```
# sudo aptitude install gnome-core-devel build-essential
```but I get this message after all the packages to install blurb```
The following packages will be REMOVED:
  gstreamer0.10-ffmpeg{u} gstreamer0.10-plugins-ugly{u} liba52-0.7.4{u} 
  libdvdnav4{u} libdvdread4{u} libmpeg2-4{u} libopencore-amrnb0{u} 
  libopencore-amrwb0{u} libpostproc51{u} libsidplay1{u} libswfdec-0.8-0{u} 
  libtwolame0{u} swfdec-mozilla{a}
```which looks like I'm about to lose some important utilities?

None of the [COLOR="Blue"]to-be-removed[/COLOR] packages show up in the [COLOR="Blue"]will-be-installed[/COLOR] packages.

I already seem to have build-essential```
# dpkg -l build-essential
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-==============================================================
ii  build-essential         11.4build1              Informational list of build-essential packages
```[COLOR="Blue"]gnome-core-devel[/COLOR] does not show up in Synaptic.
I'm at a loss as to whether to go ahead or not.
Any advice welcome.

Should this topic be in this forum anyway? :confused:

I did some more newb digging.  [COLOR="Blue"]gnome-core-devel[/COLOR] **does** show up in Synaptic! I hadn't realised that Synaptic doesn't alphabetise package titles :redface: though this time only [COLOR="Blue"]swftec[/COLOR] is to be removed and since it doesn't work in my Firefox it's no loss :)

So I cannot truthfully mark this SOLVED since the question is now: why does aptitude show a different list of [COLOR="Blue"]to-be-removed[/COLOR] packages from Synaptic?

---

