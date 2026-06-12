---
title: "Evolution Data Server - adding an event from python"
date: 2006-12-22
forum: Programming Talk
---

### Post by MattNuzum on 2006-12-22
I've been trying for a while to do this and gave up. I'm hoping during the holidays to resume...
I'd like to be able to add an event or a todo item to evolution from a python program. The goal is for the gnome calendar to pop-up a reminder when the event approaches.

Some work was done to make swig work and supposedly you can do this all from Ruby, because the swig bindings have been fully ported/completed for ruby. This can be found here: [http://www.go-evolution.org/SWIGforEDS](http://www.go-evolution.org/SWIGforEDS)

I've never used swig before, but I tried to use the code to make swig bindings for python. Unfortunately, I only succeeded in frustrating myself. ](*,) 

To compare, a few years ago when I used Windows XP, Outlook and a Palm based handheld, I thought it would be cool to create a program that automatically reminded me (at random times) to compliment my wife. In about 1.5 hours I was able to whip up a program that did it. 2-3 hours later it actually had a nice UI. The program worked so good, I even called it "happy family" because my wife's [love language]("http://www.fivelovelanguages.com/") is "words of affirmation" (she likes compliments). Even when she found out I'd written a program to cover up my inability to remember to say, "I love you", "you look nice today" and etc more often than once in a blue moon it still worked like a charm.

Evolution/EDS is not nearly as hackable as Outlook.

So, anyone willing to offer some insight so that I can bring some love back to the new-zee house hold?

---

### Post by Wolki on 2006-12-23
Yes, evolution and its backend seem to be quite messy and hard to extend unless you know exactly what you're doing.

If you can live without the calendar thing, you should be able to have a small python program popup a notification bubble via dbus

Could work similar to this:
```
import dbus
import gobject 
if getattr(dbus, 'version', (0,0,0)) >= (0,41,0):
    import dbus.glib

# get the notify interface
bus = dbus.SessionBus()
notify_object = bus.get_object("org.freedesktop.Notifications", "/org/freedesktop/Notifications")
notify_iface=dbus.Interface(notify_object, "org.freedesktop.Notifications")

def send_notification(notify_title, notify_text):
    notify_iface.Notify("", 0, "", notify_title, notify_text, [], {}, 0)

send_notification("Compliment your wife", "She looks nice today")

```

There are a lot of things you can tweak, documentation for the notification stuff is here: [http://www.galago-project.org/specs/notification/0.9/index.html](http://www.galago-project.org/specs/notification/0.9/index.html)

I'll leave making it happen randomly to you... :)

---

### Post by 23meg on 2008-03-06
The [Evolution-python]("http://www.conduit-project.org/wiki/evolution-python") library lets you do this. I've managed to extract data from e-d-s, but haven't been able to write any. If someone can come up with simple practical examples of how to create appointments and tasks, I'd be grateful.

---

### Post by MattNuzum on 2008-03-07
I did some work on this a month or two ago and wrote this example code. Todo items and calendar items are very similar so its straightforward to make events too.

(this works on Hardy, probably on Gutsy)

```
import evolution
taskSource = evolution.ecal.open_calendar_source('file:///home/matt/.evolution/tasks/local/system', evolution.ecal.CAL_SOURCE_TYPE_TODO)
for c in taskSource.get_all_objects():
    print c.get_uid(), c.get_summary(), c.get_description()


summary = "New Task2"
description = "This is a very new task2"

obj = evolution.ecal.ECalComponent(evolution.ecal.CAL_COMPONENT_TODO)
obj.set_summary(summary)
obj.set_description(description)

uid = taskSource.add_object(obj)
print "Added %s to %s (uid: %s)" % (obj, taskSource, uid)

```

It feels like a light python wrapper around C code to me. Still, it works.

---

### Post by calsaverini on 2009-01-06
I was thinking about improving the priority atribution of evolution tasks but I don't know if it's possible to do it with python using the python-evolution package.

My idea is to have custom states of priority for each task and to program automatic priority changes in specific dates.

Anyone knows if its possible to do it?

---

### Post by dr4c4n on 2010-06-04
[MattNuzum]("http://ubuntuforums.org/member.php?u=24378") Kudos to your code.. it's very similar to what I want to achieve which is create a bunch of tasks from a text file automatically, line by line :) Have a great day!

---

