---
title: "How do you install Flash Player?"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by Delysid23 on 2012-01-23
I just installed Ubuntu 10.04 LTS on an older laptop.  Runs great, but how do I install Flash Player for Firefox?  

When I go to a web page requiring Flash, I get notice that I need to install Flash Player, and a link to Adobe's Flash download page.  There I find two versions of the installer, one a .tar.gz file, the other .rpm.

I can download either one, but then I'm stuck.  How do I install it?

---

### Post by Gwaro on 2012-01-23
> **Delysid23 said:**
> I just installed Ubuntu 10.04 LTS on an older laptop.  Runs great, but how do I install Flash Player for Firefox?  

When I go to a web page requiring Flash, I get notice that I need to install Flash Player, and a link to Adobe's Flash download page.  There I find two versions of the installer, one a .tar.gz file, the other .rpm.

I can download either one, but then I'm stuck.  How do I install it?


I find it easier using flashaid, a firefox plugin. Its very easy.

---

### Post by Delysid23 on 2012-01-23
Oh, I figured it out.  You do it from the Ubuntu Software Centre, under the Applications menu (in Ubuntu 10.04 anyway).  Once in Ubuntu Software Centre, just search for "flash".  Not exactly intuitive, and the "Install Flash" link you'll get on a web page requiring Flash is useless, and a red herring.

---

### Post by chaoszerox on 2012-01-23
worked for me
[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Linux (32-bit for me) - > flash player 11 for Ubuntu

make sure to restart firefox

---

### Post by Fernhill Linux Project on 2012-01-23
We have always installed codecs & flash player without problems by using/installing the 'ubuntu restricted extras' package available from software centre or a terminal.

---

### Post by mastablasta on 2012-01-23
> **Delysid23 said:**
>  Not exactly intuitive, and the "Install Flash" link you'll get on a web page requiring Flash is useless, and a red herring.
 
 
what do you mean not Intuitive? You are supposed to install all your software form the Ubuntu Software center.
 
Also (forgot if this is unsolved bug in 10.04 or missing feature) firefox should offer to install it in a propper way. 
 
But usually people indeed install it with restricted extras package. if oyu used a newer version you would be asked toward the end of OS install if you want to install this package which would install flash as well. that way on your first OS boot you would already have flash working. ;-)

---

### Post by hhh on 2012-01-23
> **mastablasta said:**
> You are supposed to install all your software form the Ubuntu Software center.Zuh? What about Synaptic, or using apt from a terminal? Or downloading the Flash tar.gz directly from Adobe, unpacking it and placing the libflashplayer.so file in ~/.mozilla/plugins ? You're right though, the Software Center is easiest for newcomers ...
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

### Post by mastablasta on 2012-01-23
well yes, but all are frontend to same repositories. that is what i ment. 
 
In linux you are supposed to install from distributions repositories otherwise presented as Ubuntu Software Center (which is a nice GUI for them). there, this is better. :-)
 
in some rare occasions you might need to use source code (which you then compile), .deb files or by adding a PPA. All these are considered a security risk, however if you know the source is valid you can install them. and sometimes this is necessary (as is the case with certain drivers).
 
but the first place to look at for those should always be repositories.

---

### Post by oklokl on 2012-01-23
sudo sh -c 'echo "deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid partner" >> \ /etc/apt/sources.list.d/canonical_partner.list' 

sudo apt-get update && sudo apt-get install adobe-flashplugin

## [http://www.ubuntuupdates.org/ppa/canonical_partner?dist=lucid](http://www.ubuntuupdates.org/ppa/canonical_partner?dist=lucid)

or
## [https://launchpad.net/ubuntu/+source/adobe-flashplugin](https://launchpad.net/ubuntu/+source/adobe-flashplugin)
## [https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.55-0lucid1](https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.55-0lucid1)

[COLOR=#FF0000]wget [/COLOR]https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.55-0lucid1/+build/2916964/+files/adobe-flash-properties-gtk_11.1.102.55-0lucid1_amd64.deb
[COLOR=#FF0000]wget [/COLOR]https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.55-0lucid1/+build/2916964/+files/adobe-flashplugin_11.1.102.55-0lucid1_amd64.deb
or 
[COLOR=#FF0000]wget [/COLOR]https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.55-0lucid1/+build/2916965/+files/adobe-flash-properties-gtk_11.1.102.55-0lucid1_i386.deb
[COLOR=#FF0000]wget [/COLOR]https://launchpad.net/ubuntu/+source/adobe-flashplugin/11.1.102.55-0lucid1/+build/2916965/+files/adobe-flashplugin_11.1.102.55-0lucid1_i386.deb

and
sudo -i
dpkg -i *deb

---

### Post by philinux on 2012-01-23
Or simply use this, just in case someone has tried and installed it incorrectly. This will sort it out.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

