---
title: "How to Remove YouTube Application"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by rgcounts on 2013-11-22
When I went to youtube.com, I was prompted to install an app for it, which I did. It turned out to simply be a shortcut that brings me to youtube.com (like the native Amazon app), and I want it removed. I don't know how. When I look through the installed software section in the Ubuntu Software Center, it's not listed, nor is it listed when I just search for "youtube." I would remove using the terminal, but I don't know the name of the package (if it even is a package). How can I get rid of it?

This might matter:
Firefox
13.10

---

### Post by sandyd on 2013-11-22
> **rgcounts said:**
> When I went to youtube.com, I was prompted to install an app for it, which I did. It turned out to simply be a shortcut that brings me to youtube.com (like the native Amazon app), and I want it removed. I don't know how. When I look through the installed software section in the Ubuntu Software Center, it's not listed, nor is it listed when I just search for "youtube." I would remove using the terminal, but I don't know the name of the package (if it even is a package). How can I get rid of it?

This might matter:
Firefox
13.10

right click on the icon in dash -> unlock

---

### Post by rgcounts on 2013-11-22
It's already not in the dash. It's still on my computer though.

---

### Post by sandyd on 2013-11-22
Oh, you mean that - remove the unity-webapps-youtube package.
Run
```

sudo apt-get remove unity-webapps-youtube
```
in a terminal

---

### Post by deadflowr on 2013-11-22
It's installed locally as a simple shortcut.
It is not an actual program.
Go to /home/username/.local/share/applications and find the file listed for youtube.
the .local means the folder is hidden, press ctrl + H to unhide it.(or hide it)
It should say youtube.desktop, or something with youtube in the name.
Simply delete that file.
Since you own the file, there is no need to run as root(sudo) to remove it.

---

### Post by rgcounts on 2013-11-22
sandyd: I pasted that into the command line, and the terminal removed a package, but the shortcut still exists.

deadflowr: When I navigate to the applications folder, I find it to be empty. Even when I unhide everything, nothing shows up. Is there another step that I'm missing?

EDIT: I went and checked again before posting, and it wasn't there anymore. I did both, so I don't know which was the solution. Thanks for the help!

---

