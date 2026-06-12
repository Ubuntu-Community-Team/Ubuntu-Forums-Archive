---
title: "Howto: Install Standalone Chatzilla Via XULrunner [Karmic]"
date: 2010-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Andruk Tatum on 2010-03-28
The process has gotten much easier since the howto here:
[URL="http://ubuntuforums.org/showthread.php?t=140811"]http://ubuntuforums.org/showthread.php?t=140811
[/URL]

It seems that xulrunner is already installed (as it is presumably used by Firefox) as /usr/bin/xulrunner.  Because of this, it is unnecessary to install xulrunner separately unless you want a newer version of xulrunner than is installed.  So, to install Chatzilla as a standalone program you have to do the following.

[LIST=1]
[*] Download the latest Chatzilla from [here]("http://chatzilla.rdmsoft.com/xulrunner/"):
```
wget http://chatzilla.rdmsoft.com/xulrunner/download/chatzilla-0.9.86-xr.zip
```
[*]Install Chatzilla using xulrunner.  I install Chatzilla to my home directory because I am the only user on my computer that will use it, but if you want to install it into a more "proper" place in the filesystem hierarchy, you could probably install it to /usr/local or /opt.
```
xulrunner --install-app ./chatzilla-0.9.86-xr.zip <folder-to-install-to>
```
[*]Create an entry in the Application menu in Applications -> Internet -> Chatzilla by going to System -> Preferences -> Main Menu, the properties should look like this:
```
Type: Application
Name:Chatzilla
Command: xulrunner --app /home/<username>/.chatzilla/chatzilla/application.ini
Comment: A clean, easy to use and highly extensible Internet Relay Chat (IRC) client
Icon: /home/<username>/.chatzilla/chatzilla/chrome/icons/default/chatzilla-window.ico

```
[*]If you want to import any of you preferences from another Chatzilla (like the one that runs in Firefox), you simply have to fire up the standalone Chatzilla and type in
```
/pref <profile-path>
```
to import your previous profile.  I haven't tried this myself, so let me know if this part works.
[/LIST]

That's it, it's a very easy task by this point.  If somebody with packaging experience wouldn't mind packaging it, it would make installation even easier!

---

### Post by rCXer on 2010-03-28
Thanks for the updated tutorial.  I'll try it the next time I install Chatzilla.

---

