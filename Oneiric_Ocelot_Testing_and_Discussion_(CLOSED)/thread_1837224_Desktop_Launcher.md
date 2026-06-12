---
title: "Desktop Launcher"
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by EgoGratis on 2011-09-01
Will users of Ubuntu 11.10+ be able to make desktop launchers from right click context menu? If the answer is no then what will be the alternative way if user would like to have custom launcher.

Thanks.

---

### Post by mdhollis on 2011-09-01
In unity you can launch a program then right click the icon in the launcher and select keep in launcher.  I'm not sure about gnome-shell.  There are extensions you can use through gnome-tweak-tool.  I had a working dock on my desktop in gnome-shell for about two days now its gone......In fact all of my extensions are gone and I haven't figured it out yet.

---

### Post by EgoGratis on 2011-09-01
Not Unity Launcher (bar on left side), but custom launcher (icon) on desktop. For example to make launcher to run a command or script.

In Ubuntu 11.04 you right click on the desktop and in context menu you select option to create new launcher.

---

### Post by fjgaude on 2011-09-01
The few custom launchers I use I put in home folder **.gnome2** in the **nautilus-scripts** folder, usually the ones for root access.

---

### Post by mdhollis on 2011-09-01
> **EgoGratis said:**
> Not Unity Launcher (bar on left side), but custom launcher (icon) on desktop. For example to make launcher to run a command or script.

In Ubuntu 11.04 you right click on the desktop and in context menu you select option to create new launcher.

Sorry I misunderstood you.  Gnome 3 really makes simple things difficult.  That's my biggest complaint.

---

### Post by sanderd17 on 2011-09-01
> **mdhollis said:**
> Sorry I misunderstood you.  Gnome 3 really makes simple things difficult.  That's my biggest complaint.

Huh?

In Gnome Shell you can choose to have your desktop directory shown on your desktop or not. And if you choose to show it, you can just right-click create a launcher.

What's the difficulty? If you choose for "no clutter" than you can't create any. If you choose for "clutter", than you can create clutter.

---

### Post by EgoGratis on 2011-09-01
I see GNOME 3 still has "create launcher" option in right click context menu if user clicks on the desktop. It is just not currently available in Oneiric Ocelot if u use Unity.

Thanks.

---

### Post by madjr on 2011-09-01
isnt a launcher like a .desktop file?

you can create one and then click its properties.

else i believe oneiric will have a create launcher, but am downloading the beta now to see..

---

### Post by terry_gardener on 2011-09-01
the unity launcher only accepts .desktop files. 

you can create your own and then put it in the launcher 

easiest way to do it. 

open gedit and then open a .desktop file (for example from /usr/share/applications)

use this as a guide to create your own. 

then is just a case to drag it to the launcher. 

this is how it worked in 11.04 not sure about 11.10 not tried but should work and the principles are still the same.

---

### Post by EgoGratis on 2011-09-01
I was not asking about Unity Launcher but about creating custom desktop launcher:

[http://ubuntuforums.org/showpost.php?p=11208980&postcount=3](http://ubuntuforums.org/showpost.php?p=11208980&postcount=3)

But if we are talking so much about Unity Launcher:

> easiest way to do it. 

open gedit and then open a .desktop file (for example from /usr/share/applications)

In Ubuntu 11.04 easiest way to do it is from right click context menu and then dropping it on the Unity Launcher!

---

### Post by mc4man on 2011-09-01
To get the old launcher pop up, ect. try - either in terminal, Alt+f2 or make a desktop launcher to start 'create desktop launcher'
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

(note that the new unity (4.12), will allow pasting into Alt+f2 w/ Ctrl+v

Edit: the create launcher pop up does require gnome-panel - if one didn't want the fallback session and related extra packages then this would suffice
sudo apt-get install --no-install-recommends  gnome-panel

---

### Post by EgoGratis on 2011-09-02
> (note that the new unity (4.12), will allow pasting into Alt+f2 w/ Ctrl+v

Fantastic!

About custom desktop Launcher. I see user has to:

1.) Install gnome-panel package
2.) Then use command you provided

I did test this and it does work! By loosing  fallback session you are talking about GNOME 3  fallback session? I tried Unity 2D and it still worked. 

OK so it is possible. That is the good news. 

But still creating custom desktop launchers like this or with gedit is reserved to power users? There is just no way majority of Ubuntu users will be able to make custom desktop launchers? I hope something could be done about this to have options in right click context menu by default again.

---

### Post by mc4man on 2011-09-02
gnome/nautilus 3 aren't big on allowing custom commands, whether ubuntu wants to return anything I don't know - The r. click create a Desktop launcher isn't in gnome3 so don't expect any change there

You can also see this from the r. click context menu, there no longer is an option to use a custom command, nor in any of the dropdowns in system settings > removable media
In these cases users that want something out of the norm will have to create a .desktop to use their custom command rather than having it created for them when using a custom command (previously userapp .desktops

---

### Post by EgoGratis on 2011-09-02
> he r. click create a Desktop launcher isn't in gnome3 so don't expect any change there

I see. 

I was under the impression it was still there in GnomeShell. I didn't test it my self:

[http://ubuntuforums.org/showpost.php?p=11209169&postcount=6](http://ubuntuforums.org/showpost.php?p=11209169&postcount=6)

---

### Post by EgoGratis on 2011-09-02
Ok i did some investigation. 

1.) I tested GnomeShell in Oneiric Ocelot and it does not have option to create application launcher in right click context menu. Or maybe it has, BUT because i did upgrades for long time now something is broken?

2.) Then i did some investigation and indeed GnomeShell (GNOME 3) sill does have this option:

[Create an application launcher in Gnome 3]("http://linux-software-news-tutorials.blogspot.com/2011/05/create-application-launcher-in-gnome-3.html")

OK, this will probably be available to Ubuntu users sooner or later then!

Thanks!

---

### Post by thejambi on 2011-09-03
In 11.10 beta, I searched for "main menu" in software center, and you can install the old main menu editor, which lets you create launchers, etc.

---

### Post by cariboo on 2011-09-03
Alacarte gets installed as a dependency of gnome-session-fallback.

---

### Post by xfatherjack on 2011-09-10
This ubuntu 11.10 is some Geek on an EGO trip, maybe their idea of progress, they are seriously out of touch.
For a lay person,ubuntu 10.04 is user friendly.
We had something that worked well.
[COLOR="Red"]Now I'm copying and editing shortcuts,[/COLOR] which is daft.
'work-arounds are not the answer.

I'm still hopeful that someone will get sense.

If not, I will have to choose whether move away from this Labourious STUFF and to go back to 10.04, which is excellent OR back to 'Wi****s 7', 

Using ubuntu should not be a 'chalange', it should be easy!
This ubuntu 11.10 is a 'crock!!!

---

### Post by cariboo on 2011-09-10
If Windows works better for you, go for it. If it's just Unity you don't like, have you tried any of the other members of the Ubuntu family?

---

### Post by jbicha on 2011-09-11
> **EgoGratis said:**
> 
1.) I tested GnomeShell in Oneiric Ocelot and it does not have option to create application launcher in right click context menu. Or maybe it has, BUT because i did upgrades for long time now something is broken?

2.) Then i did some investigation and indeed GnomeShell (GNOME 3) sill does have this option:

[Create an application launcher in Gnome 3]("http://linux-software-news-tutorials.blogspot.com/2011/05/create-application-launcher-in-gnome-3.html")

OK, this will probably be available to Ubuntu users sooner or later then!

Thanks!

Actually, that feature was removed after GNOME 3.0 but before GNOME 3.2 so Ubuntu 11.10 will not have it and it probably won't be coming back any time soon.

---

### Post by kyleabaker on 2011-09-11
I filed a bug that when you open an application and arrange the icon it should be assumed to be pinned, but got shot down because apparently that didn't make sense to the retarded developers. Anyone else see what I'm talking about? If so I'll reopen the bug report and try to correct the stupid *** oversight.

+1 if you agree. ;)

---

### Post by jbicha on 2011-09-11
Please don't call people stupid.

In fact, I believe I found the bug report and your idea was not shot down but a developer asked you to provide more detail in your bug description with what the current behavior is, how it doesn't work right, and how it should work. I reserve the term "shot down" for a bug at least being marked Won't Fix or perhaps Invalid but definitely not for Incomplete bugs.

For what it's worth, my opinion is that the mere act of moving a launcher item for a running app should **not** pin that app to the launcher. Changing that wouldn't match the behavior on other systems (Windows 7 for instance).

---

### Post by kyleabaker on 2011-09-11
> **jbicha said:**
> Please don't call people stupid.

In fact, I believe I found the bug report and your idea was not shot down but a developer asked you to provide more detail in your bug description with what the current behavior is, how it doesn't work right, and how it should work. I reserve the term "shot down" for a bug at least being marked Won't Fix or perhaps Invalid but definitely not for Incomplete bugs.

For what it's worth, my opinion is that the mere act of moving a launcher item for a running app should **not** pin that app to the launcher. Changing that wouldn't match the behavior on other systems (Windows 7 for instance).

I respect your opinion and don't mean to say they are all stupid, but I stand strong in this. I develop software myself and know how terrible some bug reports can be, but I had a valid point in my mind (obviously not in other's minds), but open source should be willing to deal with subpar bug reports anyways.

Working as a software developer on a closed source project I understand poor bug reports, but when I attach a crash log and describe how it happened and it still gets shot down I think they are pushing their luck.

I've pushed changes into the kernel, so I'm not a complete noob, but they shouldn't be blowing off bug reports the way they do is all I'm saying. To each their own. I'll continue to submit reports and help when I can, but the more they reject valid reports the more they are hurting themselves. Keep in mind that its a human making this decision to accept or reject a report. I could do that, but I'd be more willing to contact for more information if its needed rather than just closing it. Get the perspective right before you judge. ;)

---

### Post by apos on 2011-09-11
Just my 2 cents:

Many thanks for the hint: I reinstalled gnome-panel in oneiric with:
```
sudo apt-get install --no-install-recommends gnome-panel
```

By the way: the default place for saving starters is not "somewhere in the home directory", but in 

```
~/.local/share/applications
```

There the .desktop files can be found in each linux desktop environement (unity, gnome, kde, xfce, ...) by the corresponding menu apps.

So at best you put a starter with the following custom command in there (change USERNAME to match your home directory - $HOME or $USER will not work!):

```
gnome-desktop-item-edit **/home/USERNAME/.local/share/applications/** --create-new
```

That's it. Now you can create starters without having access to the desktop and newly created starters are instantly available within unity, the xfce-appfinder, ...

If you don't need a starter anymore, simply delete it from this directory. You can also edit it to add it to menu groups, add translations ...

Greets Axel

---

### Post by EgoGratis on 2011-09-11
@apos

Thank you for your explanation. BUT this is reserved for us "power users".

> Actually, that feature was removed after GNOME 3.0 but before GNOME 3.2 so Ubuntu 11.10 will not have it and it probably won't be coming back any time soon. 

Thank you for your explanation. Not having the (GUI) ability to create custom launcher does represent some trouble to average user i imagine. Using terminal for this task is one option, but i don't quite understand why would GNOME 3 take this (GUI) ability away from the users. Such a thing as custom launcher just does not exist any more for average GNOME 3 user. BUT i must say i do see one new possibility for average user in Ubuntu 11.10. User can drag any program launcher from dash to desktop -> right click on it -> Properties -> and customize it. Not so "straightforward" but still GUI + mouse way!

---

### Post by JRBASTIEN on 2011-09-25
I usually do not write to complain and try to be helpful but I really does not get this one.

Even if I succeed to add a command like "python /home/jrbastien/Scripts/WakeOnLanLinkstation.py" in the unity bar (I still don't know how - keeping in launcher would only keep the terminal not the python command),  am I supposed to fill it up with commands like this?

What is the desktop supposed to be used for in 11.10?  Watching clean wallpaper?

---

### Post by t1497f35 on 2011-09-25
> **JRBASTIEN said:**
> I usually do not write to complain and try to be helpful but I really does not get this one.

Even if I succeed to add a command like "python /home/jrbastien/Scripts/WakeOnLanLinkstation.py" in the unity bar (I still don't know how - keeping in launcher would only keep the terminal not the python command),  am I supposed to fill it up with commands like this?

What is the desktop supposed to be used for in 11.10?  Watching clean wallpaper?
If you're willing to create a link with an icon which when run executes something - then you might wanna learn to create files whose names end up with [".desktop"]("http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html"), or just look at similar .desktop files from /usr/share/applications/ and create your own one, put it into ~/.local/share/applications/ and from there you can drag it to the left Unity pane, or whatever.

---

### Post by JRBASTIEN on 2011-09-25
Thanks for the suggestion.

Yes, I am willing to follow that path to create my shortcuts as I'm a computer geek.  However I share the same feeling as xfatherjack who started this thread.  This is a big step backward.  I can't ask the other members of my family to do this...

Hopefully, this will not take years to get addressed.

---

### Post by jbicha on 2011-09-25
Sorry, but non-computer geeks don't write random scripts and expect to be able to start them by clicking a button. The old functionality is part of gnome-panel which is not installed by default and the Nautilus shortcut was removed upstream as well since the developers & designers don't think it makes sense with how the desktop works now.

---

### Post by EgoGratis on 2011-09-26
> Sorry, but  non-computer geeks don't write random scripts and expect to be able to  start them by clicking a button.

And they don't use any method mentioned in this thread to create a custom launcher! 


> The old functionality is part of  gnome-panel which is not installed by default and the Nautilus shortcut  was removed upstream as well since the developers & designers don't  think it makes sense with how the desktop works now.

How does it work now? I am not asking you. ;) I still see locally installed application, desktops and home folders full of launchers, files, folders, scripts, portable apps, paths... that can be controlled with custom Launcher. The only difference is before you could use simple GUI tool to create one but now you have to make it yourself with one of the options in this thread. If we are talking about "web apps" guess what? User needs simple (GUI) way to create desktop launcher for "web app"? Go figure! :D

---

### Post by EgoGratis on 2011-09-26
Funny thing! Thread just above this one:

[http://ubuntuforums.org/showthread.php?t=1849973](http://ubuntuforums.org/showthread.php?t=1849973)

How do i achieve my goal..?

First answer: you can create custom Launcher and..!

---

### Post by beew on 2011-09-26
> **cariboo907 said:**
> If Windows works better for you, go for it. If it's just Unity you don't like, have you tried any of the other members of the Ubuntu family?

Actually it is not so much Unity that is the problem, but gnome3. In 11.04 you can create short cuts and custom desktop files in Unity with no issue. Since the new Unity Ui is supposed to be friendly to new users  this state of affair is absurd and shouldn't be tolerated. If the gnome devs continue to have their heads up their you know where Canonical should provide patches for doing mudane things like creating launchers.

---

### Post by JRBASTIEN on 2011-09-26
It becomes interesting.  From this bug: [https://bugs.launchpad.net/ayatana-design/+bug/723861](https://bugs.launchpad.net/ayatana-design/+bug/723861), you can see that it is still available but disable. It is therefore not a gnome 3 issue but really a design decision.

You can style type "gnome-desktop-item-edit shortcutname.desktop" in a "run a command" entry.  I tried it and it work for creating new shortcuts.

---

### Post by jbicha on 2011-09-26
> **JRBASTIEN said:**
> It becomes interesting.  From this bug: [https://bugs.launchpad.net/ayatana-design/+bug/723861](https://bugs.launchpad.net/ayatana-design/+bug/723861), you can see that it is still available but disable. It is therefore not a gnome 3 issue but really a design decision.

You can style type "gnome-desktop-item-edit shortcutname.desktop" in a "run a command" entry.  I tried it and it work for creating new shortcuts.

It's part of gnome-panel which will not be included in Ubuntu 11.10 so the Ubuntu decisionmakers agree with the Nautilus designers and developers who have removed the easy button in Nautilus. You won't find the button in Fedora 16 either because it was removed in Nautilus 3.2.

```
$ dpkg -S gnome-desktop-item-edit
gnome-panel: /usr/bin/gnome-desktop-item-edit
```

---

### Post by cariboo on 2011-09-26
> **beew said:**
> Actually it is not so much Unity that is the problem, but gnome3. In 11.04 you can create short cuts and custom desktop files in Unity with no issue. Since the new Unity Ui is supposed to be friendly to new users  this state of affair is absurd and shouldn't be tolerated. If the gnome devs continue to have their heads up their you know where Canonical should provide patches for doing mudane things like creating launchers.

Instead of insulting the developers, maybe you should move to something else until gnome 3 matures a bit more, or make a well reasoned and polite request to the gnome-tweak -tool developers to add the missing option.

---

### Post by beew on 2011-09-26
> **cariboo907 said:**
> Instead of insulting the developers, maybe you should move to something else until gnome 3 matures a bit more, or make a well reasoned and polite request to the gnome-tweak -tool developers to add the missing option.

I don't need to go anywhere. Just stick with 11.04 for a while. I did some googling and saw  how the "polite request" was shot down so I am not even wasting my time. A third party tweak will come.

---

### Post by cariboo on 2011-09-26
> **beew said:**
> I don't need to go anywhere. Just stick with 11.04 for a while. I did some googling and saw  how the "polite request" was shot down so I am not even wasting my time. A third party tweak will come.

That's what I said, gnome-tweak-tool, is not an official part of Ubuntu, so you would have to ask those developers, not the developers that work for Canonical.

---

### Post by beew on 2011-09-27
> **cariboo907 said:**
> That's what I said, gnome-tweak-tool, is not an official part of Ubuntu, so you would have to ask those developers, not the developers that work for Canonical.

Can you run gnome-tweak-tool in Unity instead of Gnome Shell?

---

### Post by cariboo on 2011-09-27
Gnome-tweak-tool installs gnome-shell as a dependency, but it does work in Unity.

---

### Post by EgoGratis on 2011-09-27
Real case scenarios:

[http://www.omgubuntu.co.uk/2011/09/create-wunderlist-unity-launcher-ubuntu/](http://www.omgubuntu.co.uk/2011/09/create-wunderlist-unity-launcher-ubuntu/)

---

### Post by makitso on 2011-09-27
I understand that the Gnome-tweak-tool is an add on.  However, after I added it to my Fedora 15 VB install, it enabled the ability to add a launcher anywhere on the desktop and a shutdown in the top right menu.  It does not do this for my VB Ubuntu 11.10 beta.

---

### Post by EgoGratis on 2011-09-27
> **makitso said:**
> I understand that the Gnome-tweak-tool is an add on.  However, after I added it to my Fedora 15 VB install, it enabled the ability to add a launcher anywhere on the desktop and a shutdown in the top right menu.  It does not do this for my VB Ubuntu 11.10 beta.

This was disused in this topic already. It was removed later on:

> You won't find the button in Fedora 16 either because it was removed in Nautilus 3.2.About gnome-tweak-tool. If this will be ever added then probably it will be "extension"? If there is no "extension" available or "built in" option to "switch" something on/off then gnome-tweak-tool can't do much!

One "workaround" more for "desktop shortcuts" that are not the same as ability to create custom launcher but somebody can find it useful!

If u open nautilus and click on folder, file, application launcher, script... with your middle mouse button you can drag it to the desktop and when you release it you have some options available you can choose from. You can create "symlink"!

Today after updates Unity 3D has the "bug" mentioned in this thread again:

[http://ubuntuforums.org/showthread.php?t=1848346](http://ubuntuforums.org/showthread.php?t=1848346)

I hope this will lead to ability to drag any application launcher from the Dash to the desktop! Right now user can only drag it to Unity launcher in Unity 3D, but in Unity 2D user can drag it to desktop to. Why is this important? Because then user can customize launcher to his needs and have simple "GUI" option for creating custom launchers back again!

---

### Post by ELD on 2011-09-27
Forgive me but when i tested 11.10 i could easily place anything on the desktop, what exactly is the problem here? Is it that you cannot create a new launcher on the desktop or that you cannot have a shortcut on the desktop or what?

---

### Post by EgoGratis on 2011-09-27
> **ELD said:**
> Is it that you cannot create a new launcher on the desktop

Yes.

---

### Post by EgoGratis on 2011-09-27
Ok, i see some progress on the way for Unity 3D:

[http://ubuntuforums.org/showthread.php?t=1848346](http://ubuntuforums.org/showthread.php?t=1848346)

---

### Post by EgoGratis on 2011-09-27
OK i made some tests. 

User can drag & drop any application launcher from Dash to desktop (installed section right now) and it can customize it too it's needs. Than it can drag it to Unity launcher and it can remove it from Unity launcher. 

Maybe in the future there will be more logic behind it, for example if user drags custom launcher to Unity launcher it automatically creates copy in .local/share/applications/ and user then can remove it from location it was added from and it won't be removed from Unity launcher automatically! This way user can find it in the Dash too, but that is more advanced capabilities and developers will decide that.

Users have (one) simple and default GUI option in Unity 3D now to create custom launcher and i am fine with that! Thanks developers!

---

