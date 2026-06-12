---
title: "Adobe plugin updates not required"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-07-18
Because of the age and characterisics of the hardware on this PC, i am unable to run any version of Shockwave Flash beyond v10.3r183. This restriction does not appear to affect the Windows  PCs. From time to time the updater offers to update the adobe plugin, along with the other updates. I have to decline the adobe ones by unticking the box, and click the "Remind me later". Is there any way to filter the updater specifically for the Adobe plugin, letting all the others through?
Any help or suggestions would be appreciated.

---

### Post by Dennis N on 2014-07-18
> **wimpy2 said:**
> Is there any way to filter the updater specifically for the Adobe plugin, letting all the others through?
Any help or suggestions would be appreciated.

You would have to "hold" that particular package. Then it will no longer show as being upgradable.

See [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
Maintainance Commands, #9.

---

### Post by wimpy2 on 2014-07-18
Thanks for the reply. I thought that the package name was "adobe-plugin" but the command 

echo "<package_name> hold" | sudo dpkg --set-selections

with adobe-plugin substituted for <package name>,  taken from the link, returns with an effective "unknown package", so I guess I mis-remembered the package name. Is there a list somewhere of the packages which I've consigned to the "Remind me later" bin?
Actual message from dpkg
> dpkg: warning: package not in database at line 1: adobe-plugin
dpkg: warning: found unknown packages; this might mean the available database
is outdated, and needs to be updated through a frontend method 

---

### Post by Dennis N on 2014-07-18
> **wimpy2 said:**
>  Is there a list somewhere of the packages which I've consigned to the "Remind me later" bin?
Actual message from dpkg

You can use dkpg to find a package in your system whose name contains a given string, such as "flash" or "adobe"

Here I am looking for packages containing "flash" as part of the package name:

```
dmn@Zotac:~$ dpkg --list | grep "flash"
ii  flashplugin-installer                11.2.202.350ubuntu0.12.10.1               i386         Adobe Flash Player plugin installer
```

My system had no packages containing "adobe". You can have different results.

---

### Post by Dennis N on 2014-07-18
Checked on an old system (Ubuntu 8.10) and looked for the flash package. Here is what I got:

```
dmn@Kayleigh:~$ dpkg --list | grep "flash"
ii  adobe-flashplugin                          10.1.85.3-1                             Adobe Flash Player plugin version 10
ii  flashplugin-nonfree                        10.0.45.2ubuntu0.8.10.1                 Adobe Flash Player plugin installer

```

(I'm not sure why both of these are present!)

So I think you will probably find "adobe-flashplugin" when your check.

---

### Post by Bucky Ball on 2014-07-18
Which release are you using? Be aware of this:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

We no longer support end-of-life releases here, but if you're using one, quite happy to help you install a supported release.

---

### Post by claracc on 2014-07-19
I think the package name you have to hold is flasplugin-installer (see attached image).

You can do it easily with synaptic package manager, look for flasplugin-installer with it, select the package and mark as hold with menu.

---

### Post by Dennis N on 2014-07-19
> **claracc said:**
> I think the package name you have to hold is flasplugin-installer (see attached image).

You can do it easily with synaptic package manager, look for flasplugin-installer with it, select the package and mark as hold with menu.

You can get tripped up by Synaptic Package Manager. Locking (pinning, holding) package versions in Synaptic isn't always honored by apt-get upgrade. Right now, I have 4 packages locked (pinned, held) in Synaptic that would be upgraded by apt-get upgrade if I ran that. Only upgrading with Synaptic always honors its locked packages.

I believe holding a package through dpkg always works to prevent an upgrade.

flashplugin-installer was used at least as far back as 10.04 (but not as far as 8.10) so you are probably right about that being the correct package. Depends on how old the OS is - some people still use very old versions, like 8.04.

---

### Post by wimpy2 on 2014-07-19
My thanks to all who replied, especially** Dennis N**. I followed his advice and I found that the package was flashplugin-installer. I put it on hold as per his link, and then used dpkg-query to verify that it was indeed on hold. 
@**claracc **I didn't see your post until after **Dennis N**'s post. You were absolutely right. 
@**Bucky Ball** I'm using Lubuntu 14.04. I read your link and it did not seem at all relevant to my query, which concerned the update service of this quite recent Lubuntu release. In future, I will make sure to state which release I am using.

---

### Post by Bucky Ball on 2014-07-19
> **wimpy2 said:**
> In future, I will make sure to state which release I am using.

+1. ;)

Then there can be no confusion and gives helpers more relevant info. Good luck.

---

### Post by vasa1 on 2014-07-30
> **Dennis N said:**
> You would have to "hold" that particular package. Then it will no longer show as being upgradable.

See [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
Maintainance Commands, #9.
I'm going to try this to keep my present version of LibreOffice applications till 14.10 comes along:
```
echo "libreoffice-base-core hold" | sudo dpkg --set-selections
echo "libreoffice-calc hold" | sudo dpkg --set-selections
echo "libreoffice-common hold" | sudo dpkg --set-selections
echo "libreoffice-core hold" | sudo dpkg --set-selections
echo "libreoffice-gtk hold" | sudo dpkg --set-selections
echo "libreoffice-help-en-us hold" | sudo dpkg --set-selections
echo "libreoffice-style-galaxy hold" | sudo dpkg --set-selections
echo "libreoffice-style-human hold" | sudo dpkg --set-selections
echo "libreoffice-writer hold" | sudo dpkg --set-selections
```

However, the apt-get howto has this:> apt-get dist-upgrade will override this, but will warn you first.I use **apt-get dist-upgrade** instead of **apt-get upgrade** so let's see what happens!

---

### Post by vasa1 on 2014-07-30
Looks like it worked. After running **dpkg --get-selections | grep libreoffice**, I get:```
libreoffice-base-core				hold
libreoffice-calc				hold
libreoffice-common				hold
libreoffice-core				hold
libreoffice-gtk					hold
libreoffice-help-en-us				hold
libreoffice-style-galaxy			hold
libreoffice-style-human				hold
libreoffice-writer				hold
```

---

