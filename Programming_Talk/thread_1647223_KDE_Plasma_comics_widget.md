---
title: "KDE Plasma comics widget"
date: 2010-12-17
forum: Programming Talk
---

### Post by rex_virtutis on 2010-12-17
I am using Kubuntu 10.04 and I have installed the Plasma Comic Viewer  widget which downloads comic strips from various websites and displays them. The widget's settings dialog has an option select which comic strips I would like to follow from a list. An online comic strip I read is not included in said list so as a challenge, I decided to add support for the strip. 

In ~/.kde/share/apps/plasma/comics/ I found a file and a directory for each comic I had installed through the settings dialog (eg. 92042-dilbert.comic and dilbert/). Each of these directories has a structure like this:
dilbert/
&#9500;&#9472;&#9472; contents
&#9474;** &#9492;&#9472;&#9472; code
&#9474;**     &#9492;&#9472;&#9472; main.es
&#9500;&#9472;&#9472; icon.png
&#9492;&#9472;&#9472; metadata.desktop

the main.es file uses a javascript like language and has code to locate the webpage, image file, previous strip, next strip and some other data.  I have already recreated this directory structure for a new comic strip and have written the main.es script. 

There are 2 things, however that I have not figured out and cannot find:
1) how does the widget find out which comic strips it is supposed to display
2) possibly related to 1, what are the .comic files and how can I generate one.

From a hex dump of the .comic files I have found that they are binary files that embed a png image near the beginning. I do not think they are Qt Resource files as I had first suspected but I haven't been able to determine much more than that. 

The source code for the widget isn't very helpful to me since I am not very familiar with the KDE APIs and I can't find any place where it reads from a file.

Thanks in advance for any help or insight you can provide.

---

### Post by GeneralZod on 2010-12-17
There is a guide here, but I don't know how up-to-date it is:

[http://techbase.kde.org/Development/Tutorials/Plasma/ComicPlugin](http://techbase.kde.org/Development/Tutorials/Plasma/ComicPlugin)

---

### Post by rex_virtutis on 2010-12-18
Thank you, GeneralZod. Your google skills are clearly better than mine. Though I'm kind of disappointed at how easy this makes it. I was looking for a reverse engineering challenge. Oh well, at least I get my comic.

---

