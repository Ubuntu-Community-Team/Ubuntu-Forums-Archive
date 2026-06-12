---
title: "Flash Issue"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by wormser on 2008-06-17
Flash is not displaying right on the [Dell website]("http://configure.us.dell.com/dellstore/config.aspx?oc=dycwtu1&c=us&l=en&s=dhs&cs=19&kc=segtopic%7Elinux_3x").  I am using flashplugin-nonfree.  Isn't there an Adobe version of the plugin?  Would that resolve the issue?

---

### Post by wolfen69 on 2008-06-17
did you select list view on the dell site? btw, great avatar, great album. saw them 4 times.

---

### Post by Dougie187 on 2008-06-17
If im not mistaken, nonfree is adobe. Although if you want to check you can download the one from adobe's site. Its easy to install. Although It doesnt fix the issue. I guess its a known issue, heh ive been waiting for it to be fixed for a while.

Edit: not sure if your issue is the same as mine, but mine is that flash is always on top and it looks really weird and its rather irritating.

---

### Post by Superkoop on 2008-06-17
I have no problem with the site, but if you haven't restarted your browser, do that. Some times flash will go wonky after a while, and a quick browser restart will fix it.

---

### Post by RomeReactor on 2008-06-17
Hi. That *is* the Adobe Flash plugin, which is the newest version available from their site (9.0.124). Can you post a screenshot of the problem? If you're referring to the images disappearing after the page finishes loading, that's been happening for quite a while. Are you running Ubuntu 32 bit or 64?

---

### Post by wormser on 2008-06-17
> **wolfen69 said:**
> did you select list view on the dell site? btw, great avatar, great album. saw them 4 times.

List view makes it more functional.  But, I would like to resolve the flash issue.  I have seen this problem on other sites too.

Rush rocks.  I missed them when they came by a few weeks ago.  :(  The worst part is they were playing at the Gorge which is the best place in the world to see a concert.  I am hijacking my own thread with a photo!!!

[IMG]http://www.hob.com/pics/corporate/040322/gorge.jpg[/IMG]

---

### Post by mailtwogopal on 2008-06-17
hi,

 if am not wrong, you can restart your browser. by the way did u install flash through "firefox plug in search and install" while visiting a site which requires flash to view or play. if so the problem will not arise probably. i did it in the same way and am not getting any issues. keep posted.

---

### Post by wormser on 2008-06-17
> **RomeReactor said:**
> Hi. That *is* the Adobe Flash plugin, which is the newest version available from their site (9.0.124). Can you post a screenshot of the problem? If you're referring to the images disappearing after the page finishes loading, that's been happening for quite a while. Are you running Ubuntu 32 bit or 64?

The image disappears and I am running 32 bit.  A screen shot would show an empty space.

> **mailtwogopal said:**
> hi,

 if am not wrong, you can restart your browser. by the way did u install flash through "firefox plug in search and install" while visiting a site which requires flash to view or play. if so the problem will not arise probably. i did it in the same way and am not getting any issues. keep posted.

I have had this issue for awhile.  Flash works fine on most sites like youtube.com.  I will try install with the missing plugin option.

---

### Post by wormser on 2008-06-17
I removed flashplugin-nonfree.  Flash images were still appearing and disappearing.  About:plugins was still showing Flash.  I went to Tools> Add-ons and it would only let me disable the Shockwave Flash plugin.  Tried disabling and enabling but the same problem happens.  

How can I remove Flash from Firefox.  Do I need to install from source?

---

### Post by mailtwogopal on 2008-06-18
hi,

  Usually addons have two options after installation one is "Disable" and another is "Uninstall". Dint u have that option. if not [read]("http://ubuntuforums.org/archive/index.php/t-219259.html") this. hope it helps u probably.

---

### Post by wormser on 2008-06-18
> **mailtwogopal said:**
> hi,

  Usually addons have two options after installation one is "Disable" and another is "Uninstall". Dint u have that option. if not [read]("http://ubuntuforums.org/archive/index.php/t-219259.html") this. hope it helps u probably.

I did get it uninstalled.  I used locate libflashplayer.so to find and delete it.  Is anybody able to view that page?  If so which Flash player are you using.

---

### Post by kansasnoob on 2008-06-18
Make sure you have all of the following installed from synaptic:

ALL gstreamer (if it begins with gstreamer you want it, good, bad, and ugly)

sun-java6 (again you want ALL sun-java6 except -doc & -source) TRUST ME!

flashplugin-nonfree

And I recommend:

totem
totem-gstreamer
totem mozilla
vlc

If anything is not there you may need the Medibuntu repo:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Remember the GPG key!

---

### Post by wormser on 2008-06-18
> **kansasnoob said:**
> Make sure you have all of the following installed from synaptic:

ALL gstreamer (if it begins with gstreamer you want it, good, bad, and ugly)

sun-java6 (again you want ALL sun-java6 except -doc & -source) TRUST ME!

flashplugin-nonfree

And I recommend:

totem
totem-gstreamer
totem mozilla
vlc

If anything is not there you may need the Medibuntu repo:
[https://help.ubuntu.com/community/Medibunt]("https://help.ubuntu.com/community/Medibuntu")
Remember the GPG key!

I installed all the gstreamer and sun apps but the problem still persists.  The rest was already installed.  Any other ideas out there or is this just a bug?

---

### Post by RomeReactor on 2008-06-18
It seems [it's a bug]("https://answers.launchpad.net/ubuntu/+question/8877"), which hasn't been corrected yet.

---

### Post by wormser on 2008-06-18
> **RomeReactor said:**
> It seems [it's a bug]("https://answers.launchpad.net/ubuntu/+question/8877"), which hasn't been corrected yet.

Thanks man.  I will stop banging my head against the wall.  ](*,)

---

