---
title: "How-To Bluecurve theme on Ubuntu Dapper."
date: 2007-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ardchoille42 on 2007-01-19
I see a lot of threads regarding the Bluecurve theme. Indeed, I too feel the Bluecurve theme is quite nice. This how-to will demonstrate how to get the full Bluecurve theme running in the gnome desktop on your Ubuntu 6.06.1 LTS Dapper system. I have a feeling that this how-to will also work on Ubuntu 6.10 Edgy but I have not tried as I don't use Edgy yet.

**My system specs:**
AMD Sempron 2800+
60Gb Hard drive (/dev/hda1 main drive)
60Gb Hard drive (/dev/hdb1 - optional)
onboard graphics card
512Mb ram

As you can see, it's not the most powerful system available at the time of this writing, but there are no problems running the Bluecurve theme on this system.

So, on to the how-to :)

**1) Install the Wonderland engine and theme**
--------------------------------------------------------------------------------
The wonderland engine and theme are the same ones used in the original Bluecurve theme and can be installed from the Dapper repos with:

```

sudo apt-get install gtk2-engines-wonderland

```

This will install the wonderland engine and GTK2 theme. I would rather use a package which is in the repos rather than using Alien to convert an rpm to a deb because I have had troubles using "Aliened" .rpm to .deb's in the past. Besides, my method will yield the same result while allowing the package manager to update the engine and theme should there be updates, as well as easy removal.


**2) Download the full Bluecurve theme from the Fedora website:**
--------------------------------------------------------------------------------
```

wget http://download.fedora.redhat.com/pub/fedora/linux/core/5/i386/os/Fedora/RPMS/redhat-artwork-0.241-1.i386.rpm

```

You can also go [here]("http://download.fedora.redhat.com/pub/fedora/linux/core/") and get more recent versions of the "redhat-artwork" package if needed. The only thing you are going to use from this rpm is the Bluecurve icon theme and, if desired, the Bluecurve xmms theme.

[COLOR="Red"]NOTE: Something changed between Fedora 5 and Fedora 6 - I'm thinking Cairo. So, if you use Alien to convert the entire redhat-artwork theme for Fedora 6 to .deb and install the redhat-artwork package from the .deb, there will be problems - I tried it, it wasn't pretty. This is why I feel it is better to install from the repos as demonstrated in step 1.[/COLOR]

**Install the icons**
Open nautilus and browse to the directory where you downloaded the redhat-artwork-0.241-1.i386.rpm package. Right-click this rpm package and choose "Extract Here". You may need to install Alien (sudo apt-get install alien) in order to be able to extract .rpm's. Go into the /usr/share/icons folder **inside** the redhat-artwork-0.241-1.i386.rpm_FILES folder (ie, /home/USERNAME/path/redhat-artwork-0.241-1.i386.rpm_FILES/usr/share/icons) and copy the Bluecurve, Bluecurve-inverse, LBluecurve and LBluecurve-inverse folders to either ~/.icons (user) or /usr/share/icons (system wide - need to use [sudo]("https://help.ubuntu.com/community/RootSudo")).

**Install the Bluecurve xmms theme if desired**
Go into the /usr/share/xmms/Skins folder **inside** the redhat-artwork-0.241-1.i386.rpm_FILES folder (ie, /home/USERNAME/path/redhat-artwork-0.241-1.i386.rpm_FILES/usr/share/xmms/Skins) and right-click the Bluecurve-xmms.zip zip file, choose "Extract Here" to extract the zip file. Right-click on the Bluecurve folder that was created, choose "Create Archive" and create a .tar.gz archive. Copy the Bluecurve.tar.gz tarball to either ~/.xmms/skins (usr) or /usr/share/xmms/Skins (system wide - need to use [sudo]("https://help.ubuntu.com/community/RootSudo")). My version of xmms wouldn't load xmms themes from .zip files which is why I am recommending to create a tarball from the files in the zip file and install the tarball.


**3) Download the Bluecurve Metacity theme**
--------------------------------------------------------------------------------
```

wget http://art.gnome.org/download/themes/metacity/204/MCity-Bluecurve.tar.bz2

```

You can also download this theme with Firefox by surfing to [this webpage]("http://art.gnome.org/themes/metacity/204") and clicking the download link.

**Install the Bluecurve Metacity theme**
Right-click the MCity-Bluecurve.tar.bz2 file, choose "Extract Here". Rename the Bluecurve folder that was created, I renamed it to MCBluecurve. Right-click the renamed folder, choose "Create Archive" and create a new .tar.gz archive.

[COLOR="Red"]NOTE: The reason you need to extract, rename and re-create archive is because the folder created is named "Bluecurve" and the Wonderland theme installed in step 1 is also named "Bluecurve", installing the Metacity Bluecurve theme as is could create a problem and we don't want any problems.[/COLOR]

Open System -> Preferences -> Theme and drag and drop the MCBluecurve.tar.gz tarball, that you created, into the Theme Manager window, the Theme Manager should install the Bluecurve Metacity theme for you. You can also unpack this tarball into /usr/share/themes (system wide - need to use [sudo]("https://help.ubuntu.com/community/RootSudo")) for system-wide use.


**4) Setup the Bluecurve theme**
--------------------------------------------------------------------------------
Still using the Theme Manager, click the Theme Details button and set as follows:

Controls - Bluecurve
Window Border - MCBluecurve (or whatever you named it in step 3)
Icons - Bluecurve


**5) You're done :)**
--------------------------------------------------------------------------------
Enjoy :)

The first screenshot below is a screenshot of this nice theme running on my computer. I've always loved the Bluecurve theme.

**[COLOR="Red"]EDIT[/COLOR]: Uploaded new Bluecurve themes for various apps** :D

**Bluecurve for Openbox**
--------------------------------------------------------------------------------
I use the openbox window manager in gnome because I like the highly configurable desktop menu openbox provides - much better than the Metacity menu. I have created a Bluecurve theme for openbox and have attached it to this post as obBluecurve.tar.bz2. The Bluecurve theme for openbox can be seen in the second screenshot.


**Bluecurve for GKrellm**
--------------------------------------------------------------------------------
For those of you who use gkrellm and would like a Bluecurve theme for it, I have created a Bluecurve theme for gkrellm and have attached it to this post as gkBluecurve.tar.bz2. This theme can be seen at the right of the second screenshot.


**Custom Bluecurve menu icon**
--------------------------------------------------------------------------------
For those of you who use the Main Menu in the gnome panel, I have uploaded a custom Main Menu icon for this panel item as gmBluecurve.tar.gz. I have created a custom Main Menu icon and attached it to this post.

Instructions for using the custom Main Menu icon:
1) Right-click the panel and choose "Add to Panel"
2) Add the Main Menu panel applet
3) Open gconf-editor and go to /apps/panel/objects/object_X
  where "x" is the number of the Main Menu panel applet, it was 0 on my computer.
4) Enter a path for the custom button icon in the 'custom_icon key'
5) Check the box next to the 'use_custom_icon' key
The Main Menu icon should change immediately, but you might need to 'killall gnome-panel'.

You can see this custom Main Menu icon at the top left of the second screenshot.

---

### Post by Sklasko on 2007-01-21
Hey, thanks for this! I've always loved those icons in Fedora but hated Fedora itself :lolflag:

Anyway, I'll have to try this out later. =D>

---

### Post by ardchoille42 on 2007-01-22
> **Sklasko said:**
> Hey, thanks for this! I've always loved those icons in Fedora but hated Fedora itself :lolflag:

Anyway, I'll have to try this out later. =D>

You're welcome :)
I fell in love with the Bluecurve icons when I used Fedora Core 2.. and the Bluecurve theme is awesome too. I"m glad my how-to was helpful :)

---

### Post by aysiu on 2007-01-22
I've moved this to the HowTo section.

---

### Post by ardchoille42 on 2007-01-22
> **aysiu said:**
> I've moved this to the HowTo section.

Oops.. I just realised it was posted in the wrong section. Thank you for moving it :)

---

### Post by ardchoille42 on 2007-02-08
EDIT: Added the Bluecurve openbox theme and the menu icon to the original post.

---

### Post by ardchoille42 on 2007-03-11
20070311 - Uploaded new Bluecurve themes for the openbox window manager, gkrellm and a Main Menu custom icon.

---

### Post by cgarre on 2008-05-14
Too good, verified on Hardy too, it works great !!! Thanks a lot for the steps, they were too detailed.

---

### Post by ardchoille42 on 2008-07-11
> **cgarre said:**
> Too good, verified on Hardy too, it works great !!! Thanks a lot for the steps, they were too detailed.

You're very welcome. I'm very happy to see that my instructions still work in Ubuntu. I haven't used the Bluecurve theme since setting up the Mac4Lin project on my Hardy installation, I may have to revisit the wonderful Bluecurve :)

---

### Post by mr53308 on 2008-08-08
Confirmed to work in Hardy

---

### Post by ardchoille42 on 2008-10-24
It seems that the Fedora folks have removed most of the older packages. If anyone knows of a new location please post a useful url.

---

### Post by cmonopoly72 on 2008-12-11
I found the bluecurve rpms here:[http://download.fedora.redhat.com/pub/fedora/linux/releases/10/Everything/i386/os/Packages/](http://download.fedora.redhat.com/pub/fedora/linux/releases/10/Everything/i386/os/Packages/)

Hope it helps.

---

### Post by sougatain on 2010-03-08
[QUOTE=


2) Download the full Bluecurve theme from the Fedora website:[/B]
--------------------------------------------------------------------------------
```

wget http://download.fedora.redhat.com/pub/fedora/linux/core/5/i386/os/Fedora/RPMS/redhat-artwork-0.241-1.i386.rpm

```You can also go [here]("http://download.fedora.redhat.com/pub/fedora/linux/core/") and get more recent versions of the "redhat-artwork" package if needed. The only thing you are going to use from this rpm is the Bluecurve icon theme and, if desired, the Bluecurve xmms theme.

[COLOR=Red]NOTE: Something changed between Fedora 5 and Fedora 6 - I'm thinking Cairo. So, if you use Alien to convert the entire redhat-artwork theme for Fedora 6 to .deb and install the redhat-artwork package from the .deb, there will be problems - I tried it, it wasn't pretty. This is why I feel it is better to install from the repos as demonstrated in step 1.[/COLOR]

[/QUOTE]
Your links are not working. What should I do now?

---

### Post by TruViet911 on 2010-09-30
nice guide. thanks alot. i got it working on my ubuntu 10.10 hehe

---

