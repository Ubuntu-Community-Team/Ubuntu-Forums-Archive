---
title: "python-xlib send_event"
date: 2008-12-02
forum: Programming Talk
---

### Post by SBFC on 2008-12-02
Just curious if anyone here has any experience using python-xlib. I normally use ventriloctrl so that PTT functionality operates in Ventrilo but with upgrading to Intrepid it is unable to monitor /dev/input/event*.

I was working on a custom app that monitors X instead of input events and have a mostly functional script. It successfully sends events to the Ventrilo window...only I have to hover over it with my mouse. 

I don't have to select it, just hover. I can't for the life of me figure out what is causing this.

Just hoping someone else had dabbled with this as well. I've attached the script in case anyone wants to take a peak.

EDIT:

Well, thanks to Google I figured it out. I had to sync the display after sending the KeyPress events. Saw a script someone else was working on and noticed the sync() method and threw it in for the heck of it and it worked.

---

