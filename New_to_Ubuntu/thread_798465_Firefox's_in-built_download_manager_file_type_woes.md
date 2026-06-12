---
title: "Firefox's in-built download manager file type woes."
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Raziel-chan on 2008-05-18
I have a problem with the in-built download manager of the fifth beta of Firefox 3. While I am able to set up a specific program to handle any files I want to open in the preferences>Applications menu, that's not what I really want.

I'm running Ubuntu 8.04, a fresh install, with the kde-desktop package, so, essentially, it's currently Kubuntu with an option to use Gnome. As my default archive viewer I use Ark.

But, frankly, Firefox disagrees. For Firefox, the default archive handler is Archive Manager (what results in filerunner being opened). Setting the browser to auto-open zip files in Ark is not the solution for me, as what I want to do is to have Firefox ask me what to do (I like saving files in different folders) and then open the file from the download manager.

And here comes my problem, as if I open a zip/rar/whatever_archive file from the download manager, it's always opened in filerunner (the default archive manager for gnome, methinks, that can't be uninstalled without uninstalling the whole ubuntu-desktop package).

Now, how can I change the default archive manager for firefox without setting it to auto-download and open files?

Thanks in advance.

cya
Raziel-chan

---

### Post by EXCiD3 on 2008-05-18
In Firefox preferences you can set "Always ask me where to save files" This will give you the option where to save the files and then it also gives you the option to open it with a program. You can go into the Content tab and change the default application firefox uses on certain file types also.

---

### Post by Raziel-chan on 2008-05-18
Umm, I did write that I had it set up for always ask, but that doesn't help me achieve the results I want - I can select it to open the file, but as I wrote, I do not want that.

Clearer description:
I want to be able to do that:
1. I click on a link.
2. It asks me for the location and I choose one.
3. It downloads the file.
4. I right-click on the file in the download manager (the downloads window) and left-click on open.
5. It opens it in the archiver of my earlier choosing, not in the one it wants to use.

As of now everything is alright excluding the fifth step, as now it looks like this:

5. It opens it in the archiver that it deemed as the 'default' one, which is 'File Roller', which also sucks because it apparently doesn't handle drag and drop unpacking in kde.

About the content tab in preferences: I see no settings regarding file handlers there. And in the Applications tab it only allows me to select what it will always do. It also shows which program is marked as the 'default one', but doesn't let me change it.

cya
Raziel-chan

---

### Post by EXCiD3 on 2008-05-18
Ah ok i misunderstood your question. Try these two things:

If you right-click a file, then click 'open with...' then chose the program you want to associate the filetype with, and click the box near the bottom that says 'Remember application association for this type of file'.
   You can also go into the Control Center. Start, Run Command and type kdesu kcontrol. Under KDE Components you'll find File Associations.

---

### Post by Raziel-chan on 2008-05-18
Umm, thanks, but it changes nothing - right-clicking on the file in the download manager and selecting open still opens it in file roller.

cya
Raziel-chan

---

### Post by Raziel-chan on 2008-05-18
Update:

What's interesting, if I set up firefox to automatically open files in Ark, the problem persists. Yes, Firefox opens ark properly, but if I choose open the file again from the downloads window, it uses file runner again.

In addition, .torrent files don't even get any options besides cancel and save in the open file dialogue, despite there being two applications available for it in the applications menu. Setting it to automatically open them with ktorrent works, but then again opening them afterwards in the downloads window brings up Transmission, seen by firefox as the default handler for these files.

cya
Raziel-chan

EDIT: Transmission was possible to be uninstalled without removing the whole gnome-desktop manager. Still, the open file dialogue contained only the cancel and save options. The 'choose and application' dialogue was finally invoked by opening the file from the downloads window and ordering the browser to remember this setting. Thanks to that now it opens the files in the downloads window in ktorrent, though the open file dialodue appearing after I click on the file's link on a site still contains only the save and cancel options.

---

### Post by EXCiD3 on 2008-05-18
Hmm, how about right clicking them and going to the open with, outside of firefox and doing it through your file browser. I don't use KDE and ive still got somewhat of the same problems with file associations in gnome.

---

### Post by Raziel-chan on 2008-05-18
That I can do without problems, as I've set all the files I use and appropriate programs to open them. There was never a problem with that. Everything comes down to Firefox and the way it handles files.

I found some new details of this problem and filed a >>link>>[COLOR="Navy"][new bug]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/231821")[/COLOR]<<link<<.

cya
Raziel-chan

---

### Post by EXCiD3 on 2008-05-19
Ok good to know. I will try to install KDE when i get that chance and see if i have the same problems with it. I have a feeling this is more of a firefox integration with kde problem than a general firefox problem.  I just wish i didnt have dialup so i could try more things!

---

