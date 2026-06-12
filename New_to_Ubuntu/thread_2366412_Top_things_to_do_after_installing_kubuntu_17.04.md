---
title: "Top things to do after installing kubuntu 17.04?"
date: 2017-07-17
forum: New to Ubuntu
---

### Post by termibuntu on 2017-07-17
So, recently, I decided to install kubuntu and wipe ubuntu with unity. The reason is because canonical will be switching to the gnome desktop soon. So I would appreciate it is people would give me some things to do. I'm a normal user, who does loads of general stuff. It would help. :) thanks.

---

### Post by Frogs Hair on 2017-07-17
There are various Blogs and websites that offer post installation lists, but they're generally a matter of personal preference anyway. I would fully update the system, see the desktop help manual, and install the software that supports the way you use your operating system. 

[https://userbase.kde.org/Welcome_to_KDE_UserBase](https://userbase.kde.org/Welcome_to_KDE_UserBase)

---

### Post by Tadaen_Sylvermane on 2017-07-17
The only guide for that is what you want. Like said those guides are a matter of preference. I know I find them useless because they do the writers idea of perfect, not my own. Figure out what you want and do it, don't rely on someone else's opinion. That is the joy of open source. It's up to you, not someone else.

---

### Post by termibuntu on 2017-07-17
Thanks for the answers! I will be sure to check out some of the stuff I can do personally. Meanwhile, I'll be on my kubuntu, making myself at home from installing it a few hours ago. :D

---

### Post by SeijiSensei on 2017-07-18
I've used KDE for many years now.  On a new installation I'll add these packages

firefox
thunderbird
smplayer
mpv

The latter two are for video playback. I prefer Clementine to the default Amarok as an audio player.

I usually install VirtualBox so I can run a Windows virtual machine when needed.  I prefer to use Oracle's repository as [described here]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions").

---

### Post by vasa1 on 2017-07-18
> **SeijiSensei said:**
> I've used KDE for many years now.  On a new installation I'll add these packages

firefox
thunderbird
smplayer
mpv

The latter two are for video playback. I prefer Clementine to the default Amarok as an audio player.

I usually install VirtualBox so I can run a Windows virtual machine when needed.  I prefer to use Oracle's repository as [described here]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions").

I installed mpv, the version in the software center, on Kubuntu 16.04 (with the kubuntu backports ppa so I have plasma 5.8.7), but it didn't seem to get along well with kwin :( I'm using vlc instead for both audio and video.

---

### Post by oldos2er on 2017-07-19
Kubuntu maintains their own forums, not that we don't welcome Kubuntu users and questions here, but there is more Kubuntu-specific information available there.

[https://www.kubuntuforums.net/content.php](https://www.kubuntuforums.net/content.php)

---

### Post by vasa1 on 2017-07-20
> **vasa1 said:**
> I installed mpv, the version in the software center, on Kubuntu 16.04 (with the kubuntu backports ppa so I have plasma 5.8.7), but it didn't seem to get along well with kwin :( I'm using vlc instead for both audio and video.
I tried again, this time with mpv from here: [ppa:mc3man/mpv-tests]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests?field.series_filter=xenial")

```
$ apt policy mpv
mpv:
  Installed: 2:0.25.0+git7~xenial1
  Candidate: 2:0.25.0+git7~xenial1
  Version table:
 *** 2:0.25.0+git7~xenial1 500
        500 http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     0.14.0-1build1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
$
```Works great!

---

### Post by miqrojamie on 2017-07-20
The only things I can really recommend are to update the system to the latest version and (optionally) customise the desktop environment to your liking. Everything else is up to you.

---

### Post by termibuntu on 2017-07-23
Ok! Thanks for the suggestions everyone! A lot of what described here I have already done... but thanks for the extra suggestions! I appreciate it. :)

@oldos2er how come you don&#8217;t accept questions about kubuntu? 1. Why is there an kubuntu tag? 2. Isn&#8217;t this a general forum for any Ubuntu flavours? For example, if I type &#8220;xubuntu forums&#8221; (still) it comes up with Ubuntu forums. :/
EDIT: Ubuntu forums (this forum) comes up with Choose the most appropriate category for your questions regarding Ubuntu, **Kubuntu**, Xubuntu, Edubuntu, Lubuntu, Ubuntu Gnome, Ubuntu Studio, Mythbuntu, Ubuntu Mate, Ubuntu Budgie and Ubuntu Kylin. 
So, we can ask questions about Kubuntu.

---

### Post by vasa1 on 2017-07-23
> **termibuntu said:**
> ...
@oldos2er how come you don’t accept questions about kubuntu? 1. Why is there an kubuntu tag? 2. Isn’t this a general forum for any Ubuntu flavours? For example, if I type “xubuntu forums” (still) it comes up with Ubuntu forums. :/
Please read what oldos2er wrote a little more carefully!

Here it is again:> Kubuntu maintains their own forums, not that we don't welcome Kubuntu users and questions here, but there is more Kubuntu-specific information available there.
I too often direct users to sites where they'll find more help if they need more eyeballs on an issue. So, in no way was it implied that we "don’t accept questions about kubuntu". I trust that clarifies matters!

---

### Post by SeijiSensei on 2017-07-24
As a KDE user, I've found this site more helpful than Kubuntu forums.

---

### Post by mastablasta on 2017-07-25
after years of battling with default(ish) theme on 14.04 (+firefox issues) i went to dark theme. it and opensuse theme are very clean nice and friendly for my eyes. i then modified the desktop somewhat (very small modification). anyway i am very pleased with how it now looks like. i hope i can get similar results with 16.04 one day. i haven't moved yet as i have AMD fglrx support with 14.04.

---

### Post by vasa1 on 2017-07-25
> **termibuntu said:**
> So, recently, I decided to install kubuntu and wipe ubuntu with unity. The reason is because canonical will be switching to the gnome desktop soon. So I would appreciate it is people would give me some things to do. I'm a normal user, who does loads of general stuff. It would help. :) thanks.Not Kubuntu-specific, but I'd suggest ensuring that you install aptitude, synaptic package manager and ppa-purge just in case you ever need them!

---

### Post by termibuntu on 2017-07-28
@SeijiSensei Yup, This forum is generally more helpful than Kubuntu Forums, that's for sure.
@vasa1 now I get it. :P Thanks for pointing that out! At the time of writing I was in a hurry... sorry. Also, hmm, the tools aptitude (for another way of managing packages), synaptic (as a graphical package manager for apt) and ppa-purge (for purging PPAs) are pretty important. I may be installing depending on the size of the packages required since I have limited space on my hard drive....
@mastablasta yeah, if I had decided to reinstall Ubuntu with unity I would have gone for a flat, darker theme, generally for the default theme being outdated by of what I would like. I'm more for material and flat designs. Also, good luck with your AMD fglrx driver support!

---

### Post by termibuntu on 2017-07-28
Hi again. So, with synaptic, when run as root from plasma start or terminal with sudo, it looks ugly. If ran from terminal WITHOUT sudo, it looks good and corresponds to the theme I use on my system, with a warning telling me that I can't do changes to the system. Can I make it look the same as the whole system? See the screen shot for a glance at what I mean.

---

### Post by vasa1 on 2017-07-28
> **termibuntu said:**
> Hi again. So, with synaptic, when run as root from plasma start or terminal with sudo, it looks ugly. If ran from terminal WITHOUT sudo, it looks good and corresponds to the theme I use on my system, with a warning telling me that I can't do changes to the system. Can I make it look the same as the whole system? See the screen shot for a glance at what I mean.Do you have */etc/gtk-3.0/settings.ini*? If you do, please post its contents.

I'm on Kubuntu 16.04 LTS and so what I did may not be applicable to your system. Anyway, this is my */etc/gtk-3.0/settings.ini*```
[Settings]
gtk-theme-name = Breeze-Dark
gtk-icon-theme-name = breeze-dark
gtk-sound-theme-name = ubuntu
gtk-icon-sizes = panel-menu-bar=24,24
```Please make sure you back up the file before editing it! And spellings maybe *case-sensitive*.

---

### Post by SeijiSensei on 2017-07-28
Isn't it the case that when run as root via sudo, the application is using whatever configuration it finds under /root?  That's unlikely to have anything like the configuration you've set up as an ordinary user.

What if you use the native "Software Center" (aka "Muon") application that comes with Kubuntu?

---

### Post by termibuntu on 2017-07-28
@SeijiSensei I have tried muon and it displays it correctly. :) although, one huge downside to muon is that there is no terminal to show what it&#8217;s doing. :( if only it did...
@vasa1 I&#8217;m on Kubuntu 17.04, so maybe it can be different? I&#8217;ll check for that file, anyways.

---

### Post by vasa1 on 2017-07-28
> **SeijiSensei said:**
> Isn't it the case that when run as root via sudo, the application is using whatever configuration it finds under /root?  That's unlikely to have anything like the configuration you've set up as an ordinary user.
...
Applications run with elevated rights should look the same as when run by a normal user _if_ OP is using themes located in */usr/share/themes*. 

So, back to the issue I pointed out. For several version of *buntu, there's been a "default" */etc/settings.ini* which sets *Ambiance* as the gtk3 theme. Kubuntu doesn't ship with Ambiance and so gtk3 applications run as "root" use GTK's default theme which has been Adwaita for the last few gtk versions.

---

### Post by termibuntu on 2017-07-29
@Vasa1 just opened the file... seems it wants Ambiance to be the default theme... how do I switch the whole theme to Breeze light (or dark, you can give me both examples) and the icons? Thanks.

---

### Post by vasa1 on 2017-07-29
That's why I provided my settings.ini file. I too had Ambiance and I changed that to Breeze Dark. Then synaptic (with sudo) showed up properly.

You need to edit /etc/settings.ini using sudo nano for example and carefully change Ambiance to your chosen theme. You could also change the icon theme using the exact spelling as refelcted in /usr/share/icons.

```
ls /usr/share/icons
Adwaita         mkusb.svg       oxy-lilac            oxy-sea_blue
**breeze**          oxy-black       oxy-midnight_meadow  oxy-steel
breeze_cursors  oxy-blue        oxy-navy             oxy-terra
**breeze-dark**     oxy-bluecurve   oxy-norway           oxy-terra_green
Breeze_Snow     oxy-brown       oxy-obsidian         oxy-violet
contrastlarge   oxy-cherry      oxy-obsidian-hc      oxy-viorange
default         oxy-chrome      oxy-olympus          oxy-white
default.kde4    oxy-desert      oxy-olympus-inv      oxy-whitewater
gnome           oxy-emerald     oxy-orchid           oxy-wonton
hicolor         oxygen          oxy-oxygen           oxy-yellow
Humanity        oxy-green       oxy-peach            oxy-zion
Humanity-Dark   oxy-grey        oxy-purple           Tango
locolor         oxy-honeycomb   oxy-red              ubuntu-mono-dark
LoginIcons      oxy-hot_orange  oxy-red-argentina    ubuntu-mono-light
```

Of course, for normal user purposes, there's a nice GUI accessible via *System Settings > Application Style > GNOME Application Style (GTK)*. See image.

---

### Post by speartip on 2017-07-30
I've found the easiest way to get a uniform look across all apps, is to install kdesudo, then from a terminal run:
```
kdesudo systemsettings5
```
Make sure the fonts, theme & icons, mirror your normal users settings, including the gnome application style mentioned in the last post.
Then all your applications, whether kde, gtk or administrator apps will all look the same.

---

### Post by termibuntu on 2017-08-01
Ok, I will try both ways. :) I&#8217;ll update you on how that goes.

---

### Post by TheFu on 2017-08-01
> **SeijiSensei said:**
> Isn't it the case that when run as root via sudo, the application is using whatever configuration it finds under /root?  That's unlikely to have anything like the configuration you've set up as an ordinary user.

No, using '**sudo**' doesn't change the HOME environment variable.  It leaves HOME set to the prior userid, hence a chief reason that using sudo with GUI programs isn't a good idea.  Any new directories or files are owned by root.  Want to see some pain?  Do a fresh install.  Then on your first login THE VERY FIRST THING, run **sudo gedit /etc/hosts** and make a trivial change.  Now try an assortment of programs from the menus.  Some will crash because the ~/.config/ directory has some things owned by root. Don't know of the normal KDE programs are safer and won't crash or not.

In theory, non-GUI applications could have a similar problem, if they wrote config files under ~/.config/, but I can't think of any non-GUI programs which do that.

A work-around is to use **sudo -H** instead ... or the GUI front-end for it (I don't use those enough to know their names).

Just for clarification, all these APT tools work with the same backend - they are just different front-ends for end-users.

---

### Post by termibuntu on 2017-08-02
Hmm, After editing settings.ini, GTK applications look good again! :D but KDE/Qt applications still look bad, and I know I was editing GTK configurations. But how do I do this for Plasma/Qt apps?

---

### Post by vasa1 on 2017-08-02
Don't you have something like this? You'd choose the widget style.

---

### Post by termibuntu on 2017-08-02
Yes, I did. Thanks for the help! Got my applications that are run as root look great! Thanks! :)

---

### Post by vasa1 on 2017-08-02
> **termibuntu said:**
> Yes, I did. Thanks for the help! Got my applications that are run as root look great! Thanks! :)I hope you don't burn your fingers playing with applications running as root!

---

