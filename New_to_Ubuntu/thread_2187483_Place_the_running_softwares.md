---
title: "Place the running softwares?"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by Niemil on 2013-11-12
Yesterday I installed ScreenCloud, and according to the installation guide I would have got some icon on the very top, where my volume control, wifi, bluetooth etc are. But nothing appeard, and I was just going on, as I could use the hotkeys.

However, I also installed Dropbox now, and it also doesn't appear.


I realized, time to time, idk when really, it just happends when I am switching windows etc, I see the dropbox and screencloud and other things in the bottom of my screen, it's like some gradient layer with a lot of transparency that just appears.

I wonder how I fix this? where in settings in ubuntu can I make so the icons appear on the very top of my computer?

[edit]
Now I have found out how to get this bottom menu appear. I put the mousepointer to the right borrom corner and it appears.
But how do I change this menu or whatever called? how can I make the icons go up to the top instead?

---

### Post by fantab on 2013-11-12
I think you are using Gnome-Shell. There is an extension to send the 'system tray'/'task bar' to the top.

**[GNOME Shell Extensions]("https://extensions.gnome.org/#page=1")** (You can install all or any extension from the website itself).

See which of the following extension works for you:
**[TaskBar]("https://extensions.gnome.org/extension/584/taskbar/")**
[**TopIcons**]("https://extensions.gnome.org/extension/495/topicons/")

---

### Post by Niemil on 2013-11-12
> **fantab said:**
> I think you are using Gnome-Shell. There is an extension to send the 'system tray'/'task bar' to the top.

**[GNOME Shell Extensions]("https://extensions.gnome.org/#page=1")** (You can install all or any extension from the website itself).

See which of the following extension works for you:
**[TaskBar]("https://extensions.gnome.org/extension/584/taskbar/")**
[**TopIcons**]("https://extensions.gnome.org/extension/495/topicons/")

OH! :O I didn't even knew there were all these extensions.

BIG THANKS!
This solved another problem of mine with conky! The show desktop button is working great with it.

---

### Post by fantab on 2013-11-12
You are welcome!
Mark this thread as 'Solved', use Thread Tools to do so.

---

### Post by Niemil on 2013-11-12
Done that.

Well!! I didn't notice but now, cus I concentrated me more on the output and design on the Taskbar extension.

It's weird this TopIcons.
When I press on the off button so it turns "on". And popup comes up and I press on install.
nothing happends!
It says it's "on", the button.

When I then update this webpage, it says "off".

So the TopIcons haven't got to work for me so far.

---

### Post by fantab on 2013-11-12
It may not have installed properly. Remove it and re-install. Switching it ON on the gnome-extensions webpage activates the extension. You can also manage the extensions from gnome-tweak-tools, aka, Advanced Settings.

---

### Post by Niemil on 2013-11-13
> **fantab said:**
> It may not have installed properly. Remove it and re-install. Switching it ON on the gnome-extensions webpage activates the extension. You can also manage the extensions from gnome-tweak-tools, aka, Advanced Settings.
Well, I have tried switching it on and off somany times.

How do I manage it via Advanced settings? I mean, mustn't I be able to download the extension? and I cannot see any download link in there.

---

### Post by fantab on 2013-11-13
I don't know if you can download it directly - it downloads and installs from the website only. If you are having problems then contact the extension's creator. I personally don't use either of those two extensions. 
What gnome version are you using? On the extensions page choose 'current version'. This detect your current Gnome-Shell versions and display extensions accordingly. I am on Gnome 3.10, Arch Linux- Not Ubuntu.
Sometimes you have to restart the gnome-shell.

Alt+F2 
r

EDIT: The Extension 'TopIcons' is working quite well for me.
Also keep and application like skype or dropbox open so that those icons appear on bottom 'tray'. Then install 'TopIcons' and see if it shows applications in the top bar.

---

### Post by Niemil on 2013-11-13
> **fantab said:**
> I don't know if you can download it directly - it downloads and installs from the website only. If you are having problems then contact the extension's creator. I personally don't use either of those two extensions. 
What gnome version are you using? On the extensions page choose 'current version'. This detect your current Gnome-Shell versions and display extensions accordingly. I am on Gnome 3.10, Arch Linux- Not Ubuntu.
Sometimes you have to restart the gnome-shell.

Alt+F2 
r

EDIT: The Extension 'TopIcons' is working quite well for me.
Also keep and application like skype or dropbox open so that those icons appear on bottom 'tray'. Then install 'TopIcons' and see if it shows applications in the top bar.

I can't find anything with "current version" on the extension page ( [https://extensions.gnome.org/extension/495/topicons/](https://extensions.gnome.org/extension/495/topicons/) if you mean this one).
But well, on terminal it says: GNOME Shell 3.4.1
Also tried restart the gnome-shell, but still not working.
And I already have dropbox running

---

### Post by fantab on 2013-11-13
No, look for in the main Extensions page. The 'current version' setting on the page will only show extensions which are supported for your version of gnome-shell.
What version of Ubuntu are you using? I ask because AFAIK, current supported gnome-shell version is 3.8....

EDIT:
Well the author says the extension does not work with 3.4 but from shell version 3.6.1

[QUOTE=ag, author of TopIcons]This requires the soon to be released gnome-shell 3.6.1[/QUOTE]

---

### Post by Niemil on 2013-11-13
ohh okey :/
well, and in order to get 3.6.1 and above I need update whole ubuntu? And no idea if I shall do that(?), as this 12.04 version is LTS and I thought that'd been great to keep.

---

### Post by fantab on 2013-11-13
I don't think its worth the trouble to upgrade Ubuntu just for one extension.

Most of us here keep two versions of Ubuntu on separate partitions; one latest LTS [12.04] and one the latest [13.10], that ways we can have the stablity of LTS and the Latest software versions. As you have found out that 12.04 uses gnome-shell 3.4 whereas 13.10 is using 3.8.
If something breaks in, say 13.10, then we can fall back to 12.04.

---

