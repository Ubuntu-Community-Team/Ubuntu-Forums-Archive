---
title: "Plasma Active different from Kubuntu?"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by psykatog on 2013-05-09
If anyone knows an expert on the whole ubuntu/nexus situation, can you send them my way?

So, I got a nexus 7 recently, and I'd like to install Kubuntu on it.  (I tried 13.04 on my netbook and was underwhelmed, plus I'm a biased KDE fan anyways).  I'm not sure I'm understanding something, though, from the various videos I've seen : 
-1 Plasma Active seems to be based on "Meego" - is Meego another linux distro lineage altogether?  I've heard some people saying that plasma active is in the 13.04 repositories, so it must be Ubuntu at its heart, right?

And yet, what I've heard elsewhere is that Plasma active is a more broad redesign to cater to tablets, and that implies to me that it would be, well, not Ubuntu-based.

-2 Generally, one is better off installing Kubuntu from scratch vs installing the KDE desktop after a clean vanilla install.  Is that an option here?  Or is the installer that everyone's so floored with specific to vanilla ubuntu?

---

### Post by Aide9aic on 2013-05-13
**1. Plasma Active**

Plasma Active is KDE's effort to create a tabet-specific UI. KDE builds different variants of Plasma for different needs. Plasma Desktop is what you're running on your desktop. Plasma Netbook is almost the same thing, with a different launcher and a different default window handling mechanism. Plasma Active is for touch screens and has an altogether different feel, while still retaining a good degree of KDE-ness. Under the covers, though, it's all still KDE.

Most of the pre-built images listed on [Plasma Active's installation wiki]("http://community.kde.org/Plasma/Active/Installation") are built on [Mer]("http://merproject.org/"), an RPM-based distribution that traces its roots to the now-defunct Meego. For folks working on the Plasma Active project, Mer seems to be their distro of choice, especially for ARM-based hardware. The same folks also produce x86-based Plasma Active builds, again built on Mer.

An automatic build script assembles a remix of Kubuntu with Plasma Active. When I checked it many months ago, it was completely broken -- some package scripts were wrong. I tried the Raring build  a few days ago, and it still isn't great in a VM. There is no visible mouse cursor, and the "Development" tab on the settings page is missing. Trying to mouse around with an invisible cursor is frustrating as hell. Also, KWin keeps crashing, regardless of whether 3D acceleration is enabled or disabled, and regardless of whether I configure the backend to use XRender or OpenGL. I couldn't figure out how to use the non-GLES version of KWin.

I don't have an x86-based tablet anymore to test the Kubuntu build of Plasma Active. I have tried the ARM-based Mer build on my Nexus 7 early on, and it was minimally functional. From what I understand, it's matured somewhat, but I haven't looked at it since then.


**2. Kubuntu vs. hand-built KDE**

I've gone through the hand-building exercise a few times, [and even documented it]("http://www.kubuntuforums.net/showthread.php?56552-How-To-build-a-KDE-based-Ubuntu-by-hand") at Kubuntu Forums. That post is from December 2011, and probably out of date by now.

The standard Kubuntu is pretty close to vanilla KDE, as that's one of the project's goals. To get pure KDE, there isn't much you'd have to purge. I'm looking at what the package **kubuntu-desktop** pulls in; here's what I'd remove to get pureness:

* uncommon printer drivers
* LightDM -- replace with KDM
* appmenu-gtk and appmenu-gtk3
* foreign language fonts
* kubuntu-firefox-installer
* libreoffice-calc, -impress, -kde, -style-oxygen, -writer

---

