---
title: "a tool for designing and building graphical user
interfaces (GUIs)"
date: 2006-07-30
forum: Programming Talk
---

### Post by stanz on 2006-07-30
Hi All...
I remember having something in Breezy, that was a simple GUI maker.
Of course I don't remember it now, or to figure out what to look into, in the repo's, so I figured to ask!
[I][B] I'm looking to modify a current gnome gui:
NETWORKING[/B][/I], which I attached.
This is my first attempt...so, simple- is the word! :rolleyes:

=====================================
LATEST UPDATE:::
Here's my thoughts ~ to image! 
I'm having trouble saving & opening again, in 'Glade' format?
Any Clues?

---

### Post by jordilin on 2006-07-30
You can install Glade or Gazpacho, both in the repos.

---

### Post by stanz on 2006-07-30
jordilin ~ Thanks....
Glade was already installed, & I'm clueless.
I apt-got Gazpacho, Which showed more - to this newbie,
but, I'm still clueless as to the MANY unknown options...but I'll
search for info and give it a shot!
Thanks again!

---

### Post by stanz on 2006-07-30
Some results..after hours of fiddling!
I'm planning to use this in a bug report, and offer my alternative!
Any professional opinions, for this newbie?   ;-)

---

### Post by X.Cyclop on 2006-07-31
Glade, KDevelop (Designer), QtDesigner or WxWidgets.;)

---

### Post by stanz on 2006-07-31
Thanks X.Cyclop  
I think Glade is way advanced for me, right now..
Working Gazpacho, is do-able, tho I'm having saving issues with glade format, or something.
KDevelop looks like something to try..I may 'fresh install', soon, and include KUbuntu...just because- I can.
QtDesigner not in Repo's...
WxWidgetswill hang as last resort... ;)
Thanks again for your info..!!

---

### Post by X.Cyclop on 2006-07-31
> **stanz said:**
> 
KDevelop looks like something to try..I may 'fresh install', soon, and include KUbuntu...just because- I can.
Why? You can install and use KDevelop on GNOME (i do it).

> WxWidgets will hang as last resort...
I'd use WxW when i need to write cross-platforms apps.:p

---

### Post by Lord Illidan on 2006-07-31
> **stanz said:**
> Thanks X.Cyclop  
I think Glade is way advanced for me, right now..
Working Gazpacho, is do-able, tho I'm having saving issues with glade format, or something.
KDevelop looks like something to try..I may 'fresh install', soon, and include KUbuntu...just because- I can.
QtDesigner not in Repo's...
WxWidgetswill hang as last resort... ;)
Thanks again for your info..!!

Qt is in the repos, mate.. Have you searched synaptic for it?
What are you trying to do? A network app?

---

### Post by Daverz on 2006-07-31
If it's a GNOME program, you'll need to use glade to tweak the UI.  That is, if they used glade to begin with and there are .glade files in the source.  Also, glade leaves out a lot that still needs to be done by hand (uimanager stuff, treeview columns, sizegroups, etc.), so you can't tweak everything visible with it.

---

### Post by stanz on 2006-07-31
> **Daverz said:**
> If it's a GNOME program, you'll need to use glade to tweak the UI.  That is, if they used glade to begin with and there are .glade files in the source.  Also, glade leaves out a lot that still needs to be done by hand (uimanager stuff, treeview columns, sizegroups, etc.), so you can't tweak everything visible with it.
Thanks Daverz, good info- for this newbie!
And i don't know all that stuff too ~ as yet...
My attachments show what i did, and that got sent off to the programmers, with no code[ my problem saving?]
I'll be waiting for their response!  :rolleyes:

---

### Post by stanz on 2006-07-31
> **Lord Illidan said:**
> Qt is in the repos, mate.. Have you searched synaptic for it?
What are you trying to do? A network app?
For sure its there ! with abunch of stuff...:confused:
Illidan...I'm simple newbie, trying ! 
There's allot to choose with qt...geez- I don't know what I want or need?

But, This will need to wait...being my attachments [top thread] went to the programmers, and it may be a done deal... unless I continue finding gui's to tweak ! :rolleyes:
Oh...It's the 'network' gui.

---

### Post by stanz on 2006-07-31
> **X.Cyclop said:**
> Why? You can install and use KDevelop on GNOME (i do it).:p
I did try...
I tried to get it from the repos- no can do. I managed to get some dependencies, but got stopped.
Then tried to apt-get it...
>  $apt-get install **kdevelop3**
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:
**The following packages have unmet dependencies:**
  kdevelop3: Depends: **kdevelop3-plugins** (= 4:3.3.2-0ubuntu3) but it is not going to be installed
**E: Broken packages** SO THEN I TRIED...

> $apt-get install **kdevelop3 kdevelop3-plugins**
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
  kdevelop3-plugins: Depends: **libcvsservice0** (>= 4:3.5.2) but it is not installable
E: Broken packages SO THEN...> 
#apt-get install **kdevelop3 kdevelop3-plugins  libcvsservice0**
Reading package lists... Done
Building dependency tree... Done
Package **libcvsservice0 is not available**, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcvsservice0 has no installation candidate SOoooooo.....I Donno...
This is Dapper Repos...?!   :-&

---

### Post by X.Cyclop on 2006-07-31
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

    * Replace everything with the following lines 

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse 

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Save the edited file

```
sudo apt-get update
```

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

That works.;)

---

### Post by stanz on 2006-08-01
> **X.Cyclop said:**
> 
```
sudo apt-get update [http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)
That works.;)
``` 

My Sources list  :rolleyes:  is from dist-upgrade,
and once I 'source-o-matic`d & saved, 'apt-get' is getting ! =D>

So, now I managed to grab Qtdesigner & Assistant ~ worked it today.
Now, with kubuntu repos added, I've got  afew KDevelop apps to figure out!  :roll:

I guess once I put together a kewl GUI, then I'll need to find & learn - 
HowTo...make it work with a program !? :-\"
That HAS to be fun ?!!
Thanks again Everyone...I'll still be looking for advice and all.  ;)

---

