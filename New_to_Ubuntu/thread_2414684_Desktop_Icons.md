---
title: "Desktop Icons"
date: 2019-03-13
forum: New to Ubuntu
---

### Post by dec56 on 2019-03-13
Is there a way to add website shortcuts on my desktop like in Windows. I tried to right click on a site like in windows but there isn't anything there about sending it to my desktop. I am using Opera as my browser.

---

### Post by #&amp;thj^% on 2019-03-13
Sure it's easy, with your browser firefox used for this example.
In the URL window grab the icon for the site you want bookmarked and drop it to your desktop.
You will have to add trusted to the shortcut.
Ooopps you said Opera sorry bout that.
Opera
[list]
[*]Navigate to the page for which you want to create a desktop shortcut.
&#8232;
[*]Click "Bookmarks" in the top menu bar and select "Bookmark Page."
&#8232;
[*]Give the bookmark a name and click "OK."
&#8232;
[*]Click the "Bookmarks" menu, select "Manage Bookmarks," and then hold the cursor over the bookmark you just created.
&#8232;
[*]Click the bookmark, hold your click, drag the bookmark over your desktop, and then release your click.[/list]

---

### Post by dec56 on 2019-03-13
I tried that and it will not work. Not sure why.

---

### Post by #&amp;thj^% on 2019-03-14
I'm using XFCE and Mate here and it works as expected on my end.
See if you can get what you want from this: [https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-18-04-bionic-beaver-linux)
Just use Firefox to create the shortcut on the Desktop, and you can the select the properties option to open with the browser of your choice.
If your using Gnome you may have to allow show Desktop Icons, but I'm not a Gnome user.
And you could also do something like this:
[list]

Try the following to create a launcher to open a website with Firefox and add it to Ubuntu dock.

   [*] Create a new file, say MyWebsite.desktop in your ~/.local/share/applications/ directory. You can do that by running the following in Terminal

   ```
 touch ~/.local/share/applications/MyWebsite.desktop
```

    [*]Open this file with a text-editor, for example by running

    ```
gedit ~/.local/share/applications/MyWebsite.desktop
```

    [*]Add the following lines to this file and save the file

   ```
 [Desktop Entry]
    Comment=Open XYZ website
    Terminal=false
    Name=XYZ website
    Exec=firefox website-URL
    Type=Application
    Icon=applications-internet
    NoDisplay=false
```
[*]In place of website-URL put the address you want to visit, for example "https://ubuntuforums.org" for Ubuntu Forums. Also edit the the Comment= and Name= fields accordingly.

[*]Click on "Activities" at the top bar or "Show Applications" in the dock and search for "XYZ website". It should appear.

[*]Right click on it and select "Add to favourites".
[*]You can change "Exec=firefox website-URL"to "opera" if you like. [/list]
Good Luck!

---

### Post by oldrocker99 on 2019-03-14
MATE allows you to add icons from the Applications menu to a dock at the top, with nice tiny icons, which greatly appeals to me. I **HATE** huge icons, so it remains my desktop of choice, and, BTW, I have never used a better distribution. 

The development of MATE is done by the Ubuntu MATE team. It has great features I have never seen in ANY other distro, such as making the desktop look like Windows or OSX, and having a Welcome screen with their own selection of software which is curated by them, and which can be directly installed from the window.

It's worth downloading and burning to a USB just to give it a spin. [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/).

---

