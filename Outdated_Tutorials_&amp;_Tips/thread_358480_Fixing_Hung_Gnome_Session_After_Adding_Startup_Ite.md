---
title: "Fixing Hung Gnome Session After Adding Startup Items"
date: 2007-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2007-02-10
You may have gone into the Sessions preferences control panel and added a new startup item, then logged out, and then logged in only to find a hung workstation. It's hung because some program is not unloading itself properly and it's hanging your Gnome session. In fact, you find your keyboard may be hard-locked and nothing works, not even CTRL+ALT+F1 or CTRL+ALT+BACKSPACE to get you to some kind of prompt or to logout.

The fix is to power off, wait a couple seconds for the fan and hard drive to spin down, and then bootup again. However, at the login screen, DO NOT LOGIN YET. Instead, do CTRL+ALT+F1 and get to a prompt. Login as yourself and then do this:

$ nano ~/.gnome2/session-manual

Find your new entry that may be causing a problem. Look to the far left and identify the number for that item.

Highlight all such numbered items and delete those rows in this file.

Renumber the left column numbers so that they are back in order again, minus your new app you had attempted to load at startup.

Change the num_clients variable down by 1 since you removed an item.

Save the file and logout back to the console login prompt.

Now do CTRL+ALT+F7 and get to the Gnome login screen (GDM). Now login as yourself again. This will then execute this file you just edited, minus the new entry you made that may have caused the problem.

You may encounter a slight slowness of about 3 minutes. Just wait it out -- it will be okay.

Your desktop will appear back as it was again.

---

### Post by Tahir on 2007-03-06
Hello all,

I sorted out my problem. but I noticed that there was no

~/.gnome2/session-manual

file.  Just to let everyone know that this is not completely factually correct.  I had a problem with beryl and I found a file (I cant remember where it was) called beryl-manager.desktop and it was somewhere in a folder in the ~/ directory and I deleted it and I could then login to gnome.

Just so you know ;)

---

### Post by alvare on 2008-12-10
the startup files are on ~/.config/autostart/ and are .desktop files that link to the apps.

---

