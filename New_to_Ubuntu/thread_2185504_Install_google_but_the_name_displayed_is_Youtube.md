---
title: "Install google but the name displayed is Youtube"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by mksuip6962 on 2013-11-02
Hello!

I'm new to Ubuntu. I've installed Google Chrome but the name displayed is Youtube. I try to launch it but I cant. It cannot start. 
So anyone? Please Help me.

---

### Post by deadflowr on 2013-11-02
Open a terminal, use the keyboard shortcut ctrl+alt+T, or look in the dash/menu for terminal and run
```
google-chrome
```
copy and paste what it says, if anything.
(Use the # button(this is called code tags) in the forum reply box when you paste the results.)

The next step would be to look at the .desktop file in the applications folder.
That is located in the folder /usr/share/applications/google-chrome.desktop.
Normally, this file won't open by simply clicking on it, so open a text editor, gedit and either search for it in gedit > file > open > file system > usr > share >applications > google-chrome.desktop.
Or drag it from the file manager into the gedit window.

The output for google chrome is long on that file, but what we want is Name=Google Chrome( You can ignore all the other names ) , and the execution which should be Exec=/opt/google-something something(sorry I forget.)
You can post those two things as well.

And maybe also look for a desktop file for youtube as well.
And if you find one post the name and exec command for that as well.

---

### Post by vasa1 on 2013-11-02
Are you sure you completed the installation process for google-chrome?

What do you see when you run **dpkg --get-selections | grep chrome** in a terminal?

---

