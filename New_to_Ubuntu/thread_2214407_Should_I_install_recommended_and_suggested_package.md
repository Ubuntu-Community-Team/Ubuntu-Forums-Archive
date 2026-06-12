---
title: "Should I install recommended and suggested packages?"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by bshatt1987 on 2014-04-01
So I'm using Kubuntu but I like having different desktop environments to choose from, so I was going to install the Unity, Lubuntu, XFCE and Gnome Shell desktop environments.
When I went to install them in the terminal, it suggested and recommended a lot of extra packages.  I looked up how to install those extra packages and when I ran the command again it showed that there would be about 4GB more installed, than if I just installed the DEs and their dependencies.  
I was just wondering; are there any benefits of installing all those packages or will they just be taking up space?

Thanks for your input.  :D

---

### Post by mastablasta on 2014-04-01
depends a lot if you install only xfce or xubuntu desktop metapackage for example.

a DE includes certian applications as well. such as file managers, network managers etc.

---

### Post by SeijiSensei on 2014-04-01
Any of the GNOME-based desktop environments will necessarily download a lot of associated libraries when they are installed on top of Kubuntu. GNOME uses an entirely different toolkit ([GTK+]("http://www.gtk.org/")) to manage the display than does KDE which uses [Qt]("http://qt-project.org/").  If you install something like Konsole on a Unity or Lubuntu system, you'll see apt-get bring in a lot of dependencies.  Same is true if you install a GNOME application on Kubuntu.

I generally skip recommended items.  Changing your desktop environment does not require changing all the applications to conform to the windowing model, nor does the design of an application dictate a specific desktop.  I run Firefox and GIMP in Kubuntu all the time.  I've run Dolphin and Konsole on an Lubuntu box as well.  So I just pick the applications I want to use and let apt-get sort out the dependencies.

---

### Post by Rob Sayer on 2014-04-01
Just be aware that installing multiple desktops can introduce problems.  Not such a good idea.

You can, as the last post mentioned, use utilities from other desktops.  Actually using dolphin and konsole in lubuntu is a great idea.  I don't want to use any file manager except dolphin anymore.

---

### Post by deadflowr on 2014-04-01
Were you going to install all those desktops at once?
Then I can see within reason for it taking 4GB.

As suggested, you can easily install them without the added recommends.
The terminal will default to install the recommends(but not suggested packages)
to only install the base + needed depends run
```
sudo apt-get install --no-install-recommends <packagenamehere>
```
which will do as it says.
If, by chance, you wished to go in the other dircetion and also install the suggested packages 
then
```
sudo apt-get install --install-suggests <packagenamehere>
```

Choice of what you install is always yours.

---

### Post by bshatt1987 on 2014-04-01
> **mastablasta said:**
> depends a lot if you install only xfce or xubuntu desktop metapackage for example.

a DE includes certian applications as well. such as file managers, network managers etc.

Well I would be installing xxxxx-desktop.  

> **SeijiSensei said:**
> Any of the GNOME-based desktop environments will necessarily download a lot of associated libraries when they are installed on top of Kubuntu. GNOME uses an entirely different toolkit ([GTK+]("http://www.gtk.org/")) to manage the display than does KDE which uses [Qt]("http://qt-project.org/").  If you install something like Konsole on a Unity or Lubuntu system, you'll see apt-get bring in a lot of dependencies.  Same is true if you install a GNOME application on Kubuntu.

I generally skip recommended items.  Changing your desktop environment does not require changing all the applications to conform to the windowing model, nor does the design of an application dictate a specific desktop.  I run Firefox and GIMP in Kubuntu all the time.  I've run Dolphin and Konsole on an Lubuntu box as well.  So I just pick the applications I want to use and let apt-get sort out the dependencies.


Yeah, I've noticed before that you can run applications that were designed for other DEs on a DE other than the one it was designed for.  
But, I recently installed Rhythmbox because I prefer it over the default Amarok.  The buttons all have an icon of a page with the corners folded down instead of, say, a play; pause; stop; forward; rewind symbol.  
So now I wonder, if I had installed the recommended and/or suggested packages would those buttons be proper?

> **Rob Sayer said:**
> Just be aware that installing multiple desktops can introduce problems.  Not such a good idea.

You can, as the last post mentioned, use utilities from other desktops.  Actually using dolphin and konsole in lubuntu is a great idea.  I don't want to use any file manager except dolphin anymore.

Hmm, well I've done this before and never really had any troubles, it's just now I'm curious what all the extra recommended and suggested packages were about.  
I now know that it automatically installs the recommended, unless you specify otherwise, but there are still a lot of suggested packages. 


> **deadflowr said:**
> Were you going to install all those desktops at once?
Then I can see within reason for it taking 4GB.

As suggested, you can easily install them without the added recommends.
The terminal will default to install the recommends(but not suggested packages)
to only install the base + needed depends run
```
sudo apt-get install --no-install-recommends <packagenamehere>
```
which will do as it says.
If, by chance, you wished to go in the other dircetion and also install the suggested packages 
then
```
sudo apt-get install --install-suggests <packagenamehere>
```

Choice of what you install is always yours.

Yeah, I was going to install them all at once.  When I went to install without suggested and recommended, it was going to be about 1GB, and with them it turned into 5GB.  I canceled the install until I got some more info, though.

For now I think I'll just skip the suggested packages.  Maybe I'll try that another time but I've spent a lot of time getting my system setup how I like it so I wouldn't want to break something.  


Thanks again, everybody, for your input.  :D

---

### Post by SeijiSensei on 2014-04-01
On my 14.04 Kubuntu development machine in System Settings > Application Appearance > GTK there is now the ability to specify an icon set for GTK applications.  Maybe that would help.

I usually dump Amarok in favor of [Clementine]("http://www.clementine-player.org/"), which forked from Amarok some years back.  You might give that a look; it's in the repositories.

---

### Post by bshatt1987 on 2014-04-01
Hmm, well I went into the Application Appearance, but I couldn't figure out how to change it for an individual application.  
But I did install Clementine just to see what that was about and it looks like something I might like.  I'll have to play with it a little bit and see.  Thanks for the suggestion.  :3

---

### Post by Rob Sayer on 2014-04-02
> **SeijiSensei said:**
> On my 14.04 Kubuntu development machine in System Settings > Application Appearance > GTK there is now the ability to specify an icon set for GTK applications.  Maybe that would help.

I usually dump Amarok in favor of [Clementine]("http://www.clementine-player.org/"), which forked from Amarok some years back.  You might give that a look; it's in the repositories.

+1 on Clementine.  It's the best music player I've ever used.  It's the only one other than vlc that has playlist features I find useful.

-1, I'm afraid, for even mentioning a beta release to someone who doesn't understand why installing a different desktop involves a lot of extra packages.  Alpha/beta releases are for the highly skilled *only*.  I'm seeing too many noobs here lately who've installed 14.04 beta and are livid because it's borked after a system update.

---

### Post by SeijiSensei on 2014-04-02
> **Rob Sayer said:**
> -1, I'm afraid, for even mentioning a beta release to someone who doesn't understand why installing a different desktop involves a lot of extra packages.  Alpha/beta releases are for the highly skilled *only*.  I'm seeing too many noobs here lately who've installed 14.04 beta and are livid because it's borked after a system update.

Kubuntu 14.04 has been pretty stable since it's alpha release.  I don't know what the status of 14.04 on other flavors is, but the OP and I are both running Kubuntu.

I had one problem after an upgrade where playing a video in mplayer would crash my X session.  That lasted about two days until it was fixed in the next batch of upgrades.  Otherwise I have had no unfortunate experiences with Kubuntu 14.04.  Of course, since it's already April, the pace of updates has slowed considerably.

---

### Post by bshatt1987 on 2014-04-02
> **Rob Sayer said:**
> +1 on Clementine.  It's the best music player I've ever used.  It's the only one other than vlc that has playlist features I find useful.

-1, I'm afraid, for even mentioning a beta release to someone who doesn't understand why installing a different desktop involves a lot of extra packages.  Alpha/beta releases are for the highly skilled *only*.  I'm seeing too many noobs here lately who've installed 14.04 beta and are livid because it's borked after a system update.

For what it's worth, I never said that I didn't understand why it would bring in extra packages, I just didn't know if the *suggested* packages were worth installing or not, and I didn't know that recommended packages were automatically installed or I wouldn't have even mentioned them.  I had read a thread where someone else had the same question and people were saying that recommended packages weren't installed automatically.  I understand perfectly well that different desktops have different dependencies for various reasons.
Also, I may not be "highly skilled" but I have been using 14.04 beta for a couple weeks now without problems.  Only a couple very minor KDE crashes after a set of updates (but that seems to have been fixed with more updates), but nothing system breaking.  Furthermore, I understood the risks of installing a beta release before I ever did it.  If my system breaks completely after an update I'm not going to be terribly upset, despite having spent a while making it how I want it. 

> **SeijiSensei said:**
> Kubuntu 14.04 has been pretty stable since it's alpha release.  I don't know what the status of 14.04 on other flavors is, but the OP and I are both running Kubuntu.

I had one problem after an upgrade where playing a video in mplayer would crash my X session.  That lasted about two days until it was fixed in the next batch of upgrades.  Otherwise I have had no unfortunate experiences with Kubuntu 14.04.  Of course, since it's already April, the pace of updates has slowed considerably.

In your defense, you didn't suggest that I install 14.04, either.  You just mentioned that that's how a certain action was performed on your machine.  
And thanks again for the Clementine suggestion.  I do enjoy it.  :3

---

