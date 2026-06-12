---
title: "Create and Internet (URL) Shortcut on the Desktop from Chrome"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by cweinhofer on 2013-01-05
I have recently moved to Ubuntu for one of the computers in our home. Because the hardware is older, I landed on Lubuntu (12.10) after trying a few variants.

When using Windows & Firefox, I am used to being able to drag the icon from a webpage I am browsing to the desktop and it will create an internet shortcut. This doesn't seem to work with Lubuntu & Chromium. Instead it seems to copy the pages code document itself (i.e. it make a .html, .php, etc file).

Can someone tell me how to make this work with Lubuntu & Chromium, or at least how to create an Internet Shortcut on the desktop generally? Thanks!

---

### Post by The Cog on 2013-01-05
That's what happens in Xubuntu too. When you drag+drop a document from a web browser to the desktop, it copies that document to the desktop. 

But that's what I would expect to happen. I'm surprised it doesn't work in Windows. It makes me wonder how you **would** download a document in Windows.

It sounds as though you want to create an application launcher. I just tried this (in Xubuntu) and it worked. I don't know if there's an easier way:
Create a file on your desktop with whatever name you choose (e.g. bbcnews) and edit the contents to look like this:
```
#!/bin/sh
firefox news.bbc.co.uk
```
Then make the file executable. This can probably be done from your file manager by editing properties. If not use a command like this to change its properties:
```
chmod +x ~/Desktop/bbcnews
```

P.S.
If you want to launch chromium instead of firefox, the command is:
```
#!/bin/sh
chromium-browser news.bbc.co.uk
```

---

### Post by vasa1 on 2013-01-05
> **cweinhofer said:**
> ...
Can someone tell me how ... to create an Internet Shortcut on the desktop generally? Thanks!
Here's one way:
Use your file manager to go to /usr/share/applications and look a file with the Chrome icon. Copy that file to your desktop. Now, right-click on that icon on your desktop and open it with a **text editor** such as Leafpad.

Look for lines like these:
```
[Desktop Entry]
Version=1.0
Name=Google Chrome
GenericName=Web Browser
Exec=/opt/google/chrome/google-chrome %U
Terminal=false
Icon=google-chrome
Type=Application
Categories=Network;WebBrowser;Favorites;
MimeType=text/html;text/xml;application/xhtml_xml;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
X-Ayatana-Desktop-Shortcuts=NewWindow;NewIncognito

```

Most likely your file will have a lot of other stuff but just focus on a few.

Look for the line with
```
Name=Google Chrome
```
Change it to **Name=bbc**, for example.

Look for the line with
```
Exec=/opt/google/chrome/google-chrome %U
```
Change it to **Exec=/opt/google/chrome/google-chrome news.bbc.co.uk**, for example.
Don't bother about other lines. Save the file and close it.

Now, on your desktop, you should see the Chrome icon but with the text **bbc** below it. Double-clicking it will open Google Chrome to news.bbc.co.uk.

If you don't mind my saying so, I can't understand why you want an icon on your desktop for a specific url as opposed to just using the browser's bookmarks.

---

### Post by cweinhofer on 2013-01-07
Thanks for your thorough answers.

For what it's worth, in Windows (both Chrome & FF) you save a page a page by clicking on the menu button and choosing "Save page as...". Windows' action always made sense to me because the icon that you are dragging is right next to the address bar with the URL. (Plus I wouldn't guess many non-technical people have much use for saving a page's code.)

Which brings me to vasa's questions... I use URL shortcuts on my desktop all the time - particularly for pages that I just want remember the URL of for one-time visit in the future because 1) they are easier to deal with. One double-click gets you directly to the page (as opposed to having to open the browser and then navigate the Bookmarks menu) and they are easier to delete as well. 2) It's easy to forget some site buried in a menu on the browser, but having an icon on the desktop is a visual reminder.

---

### Post by vasa1 on 2013-01-07
> **cweinhofer said:**
> ... - particularly for pages that I just want remember the URL of for one-time visit in the future because 1) they are easier to deal with. One double-click gets you directly to the page (as opposed to having to open the browser and then navigate the Bookmarks menu) and they are easier to delete as well. 2) It's easy to forget some site buried in a menu on the browser, but having an icon on the desktop is a visual reminder.
I see your point. I use my desktop as the download destination so that I'm forced to deal with whatever I've downloaded :)
Let's see. If you do come across a drag-n-drop that works, do post. It certainly will be less cumbersome than editing text files.

---

### Post by vasa1 on 2013-01-07
See [Issue 94063: Drag and drop Omnibox URL to desktop doesn't create shortcut]("http://code.google.com/p/chromium/issues/detail?id=94063") but it's untriaged :(

---

### Post by ziawiki on 2013-04-23
> **cweinhofer said:**
> I have recently moved to Ubuntu for one of the computers in our home. Because the hardware is older, I landed on Lubuntu (12.10) after trying a few variants.

When using Windows & Firefox, I am used to being able to drag the icon from a webpage I am browsing to the desktop and it will create an internet shortcut. This doesn't seem to work with Lubuntu & Chromium. Instead it seems to copy the pages code document itself (i.e. it make a .html, .php, etc file).

Can someone tell me how to make this work with Lubuntu & Chromium, or at least how to create an Internet Shortcut on the desktop generally? Thanks!

I use Xubuntu 12.04 and i have no need to use the terminal to create a desktop shortcut, but i follow the same steps i use if i was on Windows:

1. Right-click on an empty area of the desktop.

2. Click "Create URL Link".

3. Paste the URL from the web page in the URL field.

4. Give it a name.

5. Voila, it's done. Same procedure as with Windows.

---

