---
title: "Ubuntu Software Center missing apps?"
date: 2017-02-10
forum: New to Ubuntu
---

### Post by abandersnatch on 2017-02-10
Why does ubuntu software center lack so many applications?
For example:
Unetbootin, Dia, Godot Engine, Qtractor, ZSNES, Gens, epsxe, Brackets, Pencil Project, Eclipse, Scribus, Jitsi, Code::Blocks, kdenlive, etc.
whats weird is I remember some of these being available in the past. What the heck is going on?

---

### Post by Bucky Ball on 2017-02-10
I can't tell you what is wrong with it but can tell you you're not alone. Have a dig around and you will quickly find others are having problems with it also.

Have you tried Synaptic Package Manager? Seems to be problem free and many have swapped to that in the interim.

---

### Post by abandersnatch on 2017-02-10
yeah, I can find some apt like zsnes, kdenlive, unetbootin. Others such as Jitsi is just outright unavailable.
I thought software center was just a front end of apt though. Is this a bug? I thought it might be intentional but I could not imagine why since what is and is not available seem very random. for example, Gens is completely unavailable, ZSNES is only available on apt/synaptic, but higan is entirely available even on the software center.

---

### Post by howefield on 2017-02-10
The new Ubuntu Software application appears to be still a work in progress.

As mentioned above you can install Synaptic, an alternative to that is to install the old Software Centre which still works and should contain all relevant packages.

```
sudo apt install software-center
```

---

### Post by adawdp on 2017-02-10
Try&#8230;  sudo apt-get install unetbootin
```
unetbootin
The program 'unetbootin' is currently not installed. You can install it by typing:
sudo apt-get install unetbootin

```

---

### Post by Impavidus on 2017-02-10
Ubuntu Software is just a front end, but it tries to hide the more technical items to make it less confusing to new users. It doesn't always work very well. Synaptic is what I always use. Just better. It used to be the default.

Of course not every program ever published is available from the Ubuntu repositories. They must be popular enough to do the maintenance, testing and packaging and available under a free license. Not all packages you mention are. It is possible to add additional repositories, called PPAs. Maybe you can find one for the software you want. I can't guarantee their security. Else you need different methods to install your software. It's recommended you only do so if you really need that software.

---

### Post by mc4man on 2017-02-10
Some of the sources you mentioned weren't brought forward to 16.04, maybe a couple haven't adjusted to gnome-software. Though many you say you can't find are certainly available in ubuntu-software
(I use synaptic myself

---

### Post by abandersnatch on 2017-02-10
> **mc4man said:**
> Some of the sources you mentioned weren't brought forward to 16.04, maybe a couple haven't adjusted to gnome-software. Though many you say you can't find are certainly available in ubuntu-software
(I use synaptic myself



weird, the ones I mentioned do not show up for me.

[ATTACH=CONFIG]273622[/ATTACH][ATTACH=CONFIG]273623[/ATTACH]

---

### Post by Perfect Storm on 2017-02-10
> **abandersnatch said:**
> weird, the ones I mentioned do not show up for me.

[ATTACH=CONFIG]273622[/ATTACH][ATTACH=CONFIG]273623[/ATTACH]

That's why it was suggested that you use synaptic Package Manager :KS

---

### Post by wildmanne39 on 2017-02-10
Have you checked to make sure all repositories are enabled like in the screenshots? after you enable some you have to reload the repository to update it.

This is synaptic, I never use gnome software installer, I use the terminal most of the time but when I do use the gui it is always synaptic.

---

### Post by ajgreeny on 2017-02-10
Another vote here for synaptic.

I have been using Ubuntu or one of its DE varieties since 2005 when synaptic was the default, and I think the only package management application available.  It is the first thing I add now to any new installation of the *ubuntu family, except Lubuntu where it is still installed as default.

I have never ever used the software-centre or the new ubuntu-software; I can see no advantage of those over synaptic, which lists all packages, and can be searched quickly and easily by "Name" alone or "Name & description"
It can also be used to fix broken packages, pin versions of packages, or to install different versions from the default should there be more than one version available.

---

### Post by martemarziano on 2017-02-10
Appgrid is another option for searching for apps and installation; have a look at the following article from OMG Ubuntu:
[http://www.omgubuntu.co.uk/2014/05/appgrid-ubuntu-software-centre-alternative](http://www.omgubuntu.co.uk/2014/05/appgrid-ubuntu-software-centre-alternative)

If you don't mind adding another PPA to your software sources, you can install it by running the following lines:
```
[COLOR=#333333]sudo add-apt-repository -y ppa:appgrid/stable
sudo apt-get update && sudo apt-get install appgrid [/COLOR]
```[COLOR=#333333]
[/COLOR][COLOR=#333333][FONT=inherit !important]
[/FONT][/COLOR]

---

### Post by abandersnatch on 2017-02-10
> **wildmanne39 said:**
> Have you checked to make sure all repositories are enabled like in the screenshots? after you enable some you have to reload the repository to update it.

This is synaptic, I never use gnome software installer, I use the terminal most of the time but when I do use the gui it is always synaptic.

yeah, sources are fine.  Besides, if they were not, apt or synaptic wouldn't work as well if I am not mistaken.[ATTACH=CONFIG]273626[/ATTACH][ATTACH=CONFIG]273627[/ATTACH]

---

### Post by abandersnatch on 2017-02-10
Example of it working fine in apt and synaptic.
[ATTACH=CONFIG]273628[/ATTACH][ATTACH=CONFIG]273629[/ATTACH]

---

### Post by RobGoss on 2017-02-10
**Synaptic Package Manager** is the best and fastest, way to install software it has just about anything you can think of

---

### Post by abandersnatch on 2017-02-10
I know I can just use Synaptic, as I have mentioned before, I just use app. This isn't really about what I should do as much as it is about why is this an issue. Is it a bug or intentionally not available? If it is a bug, what the heck kind of bug is this? Is it server side? What the hell.

---

### Post by Bucky Ball on 2017-02-10
> **abandersnatch said:**
> I know I can just use Synaptic, as I have mentioned before, I just use app. This isn't really about what I should do as much as it is about why is this an issue. Is it a bug or intentionally not available? If it is a bug, what the heck kind of bug is this? Is it server side? What the hell.

In that case, as I mentioned in the second post, you are not alone having problems with this. Consequently, if you want to know what the problem is, have you done some research? You might [try looking for some answers here]("https://duckduckgo.com/?q=ubuntu+16+software+centre+problem&t=hb&ia=web") for a start.

This is a known issue. You and thousands of others are having it. An explanation that will satisfy will be available online if you have a look. It is clear that most of the people responding to you on this thread are using Synaptic and don't have much idea why there is a problem with Software Centre, perhaps haven't bothered to look or don't care, else they would be telling you. ;)

---

### Post by Geoffrey_Arndt on 2017-02-10
Not a bug.   It's by design.   A smaller, faster and safer way to distribute (keep certain apps out of the main - - sorta like "hidden files").

It's not uncommon to have extra, and/or missing apps for various repos.   Different marketing for distro user bases (inasmuch as Linux has marketing).    Don't quibble about mundane stuff.   Same situation in other distros . . . so, not a bug.   Sometimes even just a workload question.

What's important is that the "base" is "complete" - - all the required libs and dependencies.

All this is getting less important anyway with stand-alone installers and new package tools such as flatppak, snappy etc.   Then the vendor will supply many or most of those apps (more like Windows world).

---

### Post by mc4man on 2017-02-10
Not to 'push' ubuntu-software/gnome-software, I actually remove them,  update-notifier & update-manager on any of my 'using' installs.
It just happens I've a somewhat  unadulterated 16.04 install to test xserver 0.19 so took a look.

What you mentioned in first post

```
Unetbootin,  found in both
Dia,  found in both
Godot Engine, not found at all
Qtractr, found only synaptic
ZSNES, not found, synaptic only finds the debug package
Gens, not found at all
epsxe, not found at all
Brackets, not found at all
Pencil Project, found in both, e.g. pencil2d
Eclipse, found in both
Scribus, found in both
Jitsi, not found at all but both return package named keysync
Code::Blocks, found in both, i.e. search codeblocks
kdenlive, found in both
```

The not founds at all are either never available or no longer  in 16.04 or from ppa's, not going to enable ppa's to check. Some of those emulators would probably not work anyway..
Qtractr has no good reason not to show, may be something about how packaged, also searched midi, jack & sequencer which all produced numerous similar packages..
Zsnes doesn't really show in synaptic either, only zsnes-dbg:i386 (- which if installed would pull in the zsnes:i386 package.

So all in all don't see anything unexpected in ubuntu/gnome-software, it's certainly tailored to user packages & due to a different search function may not show all it could.
(- i.e. it likely would never show lib* ,ect. To see some diff search sys in both, big difference as to search results

As to why your ubuntu-software can't find things I guess that's a different story than how this thread progressed.

edit: just to note, if interested in snap packages then the odds of them showing in synaptic are currently none & that's likely not to change.

---

### Post by deadflowr on 2017-02-11
The missing packages are most certainly related to appstream and the way appstream handles the package metadata( or cannot handle the metadata).
Sort of old, but this gives a good explaination of the gist of it:
[https://lists.ubuntu.com/archives/ubuntu-desktop/2016-February/004785.html]("https://lists.ubuntu.com/archives/ubuntu-desktop/2016-February/004785.html")

---

