---
title: "ugh, two more program questions"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by crimlaw on 2008-10-21
the more I get into ubuntu, the more I get a little frustrated.  

Anyway, I have tried two new programs, screenlets and songbird.  

I love screenlets, but they do not start up when I start up ubuntu.  If I start up the program, and click on the screenlets I already opened last time I was signed on, all of my old screenlets open in my widgets window where I want them.  However, they do not start on their own.

As for songbird, I find it annoying.  However, I cannot uninstall it.  How do I?  What is your favorite media player for Ubuntu 8.04?

Thanks!!!

---

### Post by damispyderbyte on 2008-10-21
Add the screenlets commands under the sessions manager under system>perfs>sessions.

Go to Add and add the command that starts screenlets!
i hope that works!

---

### Post by bsharp on 2008-10-21
What happens when you try to uninstall songbird?

As for my media player, I just use the default Rhythmbox.

---

### Post by sethvath on 2008-10-21
I assume damispyderbyte has answered your first question. As for the second, how did you install songbird? from a deb or tar.gz?

If its a deb file, search for songbird in synaptic and remove+purge it. For a tar.gz file, do you recall where it was extracted to? If not do a system scan of the songbird folder likely /usr/bin or /opt and sudo rm -f songbird. Desktop menu for songbird would still have to be removed manually.

---

### Post by crimlaw on 2008-10-21
ok, stupid question, how do I find the command for screenlets?

---

### Post by crimlaw on 2008-10-21
and I lied, I have one more question . . . sorry.  While using Opera, I tried to click to desktop 2, just to look at another website on a separate desktop, no real reason for doing so.  However, I could not use opera independetly on that desktop.  I tried adjusting the settings, but that did not work.  any suggests here?

---

### Post by pigmelt on 2008-10-21
for screenlets, on the bottom left of screenlets manager are some boxes that you can select to auto start at login.

---

### Post by bsharp on 2008-10-21
> **crimlaw said:**
> ok, stupid question, how do I find the command for screenlets?

Short way: Have you just tried "screenlets"?

Long way:
Assuming you launch them from the panel, right click on the panel and select "edit menus." Find the location it's under in the "Menus" pane and when you see the icon/name for screenlets in the "Items" pane, right click that and select properties. Whatever is in the command dialog is what it is.

I'm not really sure what you mean by using Opera independantly, but just launching a new window has always worked for me in Firefox...(never used Opera)


EDIT:Pigmelt's way seems easier.

---

### Post by crimlaw on 2008-10-21
its not the necessarily the new window I am concerened about.  Maybe I should use the word, "workspace?"  If I have opera open on workspace 1, then go to workspace 2 and try to open opera, it jumps back to workspace 1.  In other words, I can't open opera "independently" in a chosen workspace if it is open in another workspace.  Does that make more sense?

---

### Post by sethvath on 2008-10-22
Check your settings by right clicking on opera menu tab. Did you check "Always on visible workspace"? I tried it out myself and opera works fine when I open it from workspace 2, 3, or 4.

---

### Post by CloudFX on 2008-10-22
To make Screenlets start automatically, it's as simple as entering **screenlets** into the command field.

As for media players, I use Banshee, and I strongly suggest it.  It's prepackaged in Ubuntu, naturally ;).

```
sudo apt-get install banshee
```

---

