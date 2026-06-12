---
title: "HOWTO: Create a quick launch for Firefox in Unity."
date: 2011-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by wojox on 2011-05-11
This is really a pretty simple little hack. A lot of the credit goes to Jorge Castros Unity Guide.

[IMG]http://ubuntuforums.org/picture.php?albumid=1546&pictureid=7814[/IMG]

First thing to do is create a local file in your home folder. This way if we really mess something up we can delete it and we are back to the original.

```
cp /usr/share/applications/firefox.desktop ~/.local/share/applications
```

Now lets do a little editing:

```
gedit ~/.local/share/applications/firefox.desktop
```

You will notice my file looks a little different because I took out all the other Languages.

```
[Desktop Entry]
Version=1.0
Name=Firefox Web Browser
Comment=Browse the World Wide Web
GenericName=Web Browser
Exec=firefox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;
StartupWMClass=Firefox
StartupNotify=true
[COLOR="Green"]X-Ayatana-Desktop-Shortcuts=UbuntuForums;AskUbuntu;UbuntuLaunchpad;NewWindow
[UbuntuForums Shortcut Group]
Name=Ubuntu Forums
Exec=firefox -new-window 'http://ubuntuforums.org'
TargetEnvironment=Unity

[AskUbuntu Shortcut Group]
Name=Ask Ubuntu
Exec=firefox -new-window 'http://askubuntu.com/'
TargetEnvironment=Unity

[UbuntuLaunchpad Shortcut Group]
Name=Ubuntu Launchpad
Exec=firefox -new-window 'https://launchpad.net/ubuntu'
TargetEnvironment=Unity

[NewWindow Shortcut Group]
Name=Open a New Window
Exec=firefox -new-window about:blank
TargetEnvironment=Unity[/COLOR]
```

Now if you want more or different features you need to look at these areas:

```
X-Ayatana-Desktop-Shortcuts=UbuntuForums;AskUbuntu;UbuntuLaunchpad;NewWindow
``` 

are the names of our shortcut groups. For instance, ```
[UbuntuForums Shortcut Group]
``` 

is our first one in X-Ayatana-Desktop-Shortcuts and our first block of code after that. That's it. It's pretty self explanatory once you look at the code.


Say you would like to add OMG! Ubuntu or Web Upd8 to your list to have instant access (because you just can't check out the daily news and updates quick enough).

You would append:

```
[COLOR="Green"]X-Ayatana-Desktop-Shortcuts=[COLOR="Red"]OMGUbuntu;WebUpd8;[/COLOR]UbuntuForums;AskUbuntu;UbuntuLaunchpad;NewWindow[/COLOR]
```

Then add to the bottom:

```
[COLOR="Green"][OMGUbuntu Shortcut Group]
Name=OMG! Ubuntu
Exec=firefox -new-window 'http://www.omgubuntu.co.uk/'
TargetEnvironment=Unity

[WebUpd8 Shortcut Group]
Name=WebUpd8
Exec=firefox -new-window 'http://www.webupd8.org/'
TargetEnvironment=Unity
[/COLOR]
```

[IMG]http://ubuntuforums.org/picture.php?albumid=1546&pictureid=7815[/IMG]

---

### Post by geazzy on 2011-05-12
great tutorial :)
thanks....

---

### Post by wojox on 2011-05-12
> **geazzy said:**
> great tutorial :)
thanks....

Thanks geazzy.

---

