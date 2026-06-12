---
title: "How to update to Fluxbox-1.0-RC2"
date: 2006-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-11-21
I found this .deb at [Lotta Linux](http://lottalinuxlinks.com/blog/index.html?find=fluxbox&plugin=find&path=) (Thanks Tami) and wrote a short bash script to install (or update) fluxbox-1.0-RC2

EDIT: This script will install Fluxbox-1.0-RC2 but will not update GDM. It works best if you install fluxbox and then update :p

> This is really the same version I packaged earlier; this time though I included imlib2 support (for png icon support). I also correctly built the package this time so that the name doesn't include the version number, i.e. the old package I made would require uninstalling this way sudo dpkg -r sudo dpkg -r fluxbox-1.0rc2. This package will just install the program as fluxbox, not fluxbox-1.0rc2. Not to be confusing, this will still install fluxbox-1.0rc2-1, but it will include imlib2 support, as well as be properly named. So, if you installed the version I packaged last month, you can either leave it installed, and live without png icons, or you can uninstall it with sudo dpkg -r sudo dpkg -r fluxbox-1.0rc2, and then install this version.

[color=red]WARNING: This Fluxbox .deb has changed the way it handles styles and with this update the background images will not change when you change styles. You can set the background any other way you like..... 

WARNING: This will SIGNIFICANTLY CHANGE YOUR FLUXBOX INSTALLATION !! 

**/usr/bin/fluxbox and /usr/bin/startfluxbox ARE REMOVED AND RE-INSTALLED IN /usr/local/bin/fluxbox and /usr/local/bin/startfluxbox**

I addition to downloading and installing Fluxbox-1.0-RC2 this script will fix this problem (via links).[/color]

Download "Install_RC2.txt" to ~ (~ = shorthand for /home/user_name)

Make it executable & run:```
chmod a+x Install_RC2.txt
sudo ./Install_RC2.txt
```

NOW RESTART FLUXBOX (From the menu or exit to xdm and login)

You may have some new styles...

Enjoy

[img]http://www.laiwa.com/cache/3/1/531045_70x70.gif[/img] [color=navy]bodhi.[/color][color=gray]zazen[/color]

---

### Post by vindicta on 2006-12-02
Thanks much.  I was looking for exactly this.:)

---

### Post by nest on 2007-10-08
thanks b.z

ill do it when i arrive home :)

---

