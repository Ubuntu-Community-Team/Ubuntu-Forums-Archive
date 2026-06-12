---
title: "where is API documentation for pynotify?"
date: 2007-05-18
forum: Programming Talk
---

### Post by Laterix on 2007-05-18
I have googled this documentation for awhile now and I just can't find it. Does it even exists? Simple notifications are straight forward, but I need to add buttons and actions for my notifications. Documentation would help alot.

---

### Post by Laterix on 2007-05-18
I never found API, but I got it to work. Here is a code snipets if someone is having some kind of problems

Create notification and show it
```

n = pynotify.Notification("Title", "body", "dialog-warning")
n.set_urgency(pynotify.URGENCY_NORMAL)
n.set_timeout(pynotify.EXPIRES_NEVER)
n.add_action("clicked","Button text", callback_function, None)
n.show()

```

And then what happens when user clicks that button
```

def callback_function(notification=None, action=None, data=None):
     print "It worked!"

```

---

### Post by Tyler Oderkirk on 2007-07-28
> **Laterix said:**
> 
```

n = pynotify.Notification("Title", "body", "dialog-warning")

```


I had to include a call to init() _before_ the above line:

```

pynotify.init( "Some Application or Title" )

```

Without using init(), I got:

```

** (.:6208): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (.:6208): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (.:6208): CRITICAL **: lookup_or_register_specialized: assertion `specialized_types_is_initialized ()' failed

** (.:6208): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)'

```

Via [http://python-forum.org/py/viewtopic.php?p=16122&sid=fd77db841811f8b591b093fa99991210#16122](http://python-forum.org/py/viewtopic.php?p=16122&sid=fd77db841811f8b591b093fa99991210#16122)

-Tyler

---

### Post by Laterix on 2007-07-29
Oops, that's true. init has to be called before using libnotify.

---

### Post by brammeleman on 2007-10-28
There are a lot of examples already on your computer. Have a look in /usr/share/doc/python-notify/examples. They all run 'out of the box'.

---

### Post by Endolith on 2008-09-11
Is it just me, or do third-party Python modules have no documentation at all?  Are we supposed to rely on the C documentation for libnotify or what?

---

### Post by sucotronic on 2009-02-21
There is no documentation in the [pynotify authors webpage]("http://www.galago-project.org"). But instead you can download the [source code of pynotify]("http://www.galago-project.org/downloads.php") and look for defined functions. I save you from doing the work:

```
(define-object Notification
(define-enum Urgency
(define-function notify_notification_get_type
(define-function notify_notification_new
(define-method update
(define-method attach_to_widget
(define-method attach_to_status_icon
(define-method show
(define-method set_timeout
(define-method set_category
(define-method set_urgency
(define-method set_icon_from_pixbuf
(define-method set_hint_int32
(define-method set_hint_double
(define-method set_hint_string
(define-method set_hint_byte
(define-method set_hint_byte_array
(define-method clear_hints
(define-method add_action
(define-method clear_actions
(define-method close
(define-function notify_urgency_get_type
(define-function init
(define-function uninit
(define-function is_initted
(define-function get_app_name
(define-function get_server_caps
(define-function get_server_info
```

---

### Post by Endolith on 2009-02-21
> **sucotronic said:**
> There is no documentation in the [pynotify authors webpage]("http://www.galago-project.org"). But instead you can download the [source code of pynotify]("http://www.galago-project.org/downloads.php") and look for defined functions. I save you from doing the work

That's not documentation; it's just a list of functions.  You can get the same thing by typing [FONT=Courier New]pynotify.Notification.[/FONT] and pressing [Tab].  There is no documentation of the functions, though:

```
pynotify.Notification.attach_to_widget?
Type:        method_descriptor
Base Class:    <type 'method_descriptor'>
String Form:    <method 'attach_to_widget' of 'pynotify.Notification' objects>
Namespace:    Interactive
Docstring:
    <no docstring>

```

---

### Post by woutervanvliet on 2009-11-01
Yeah, I'm also rather disappointed by the lack of documentation. But for some reason that seems to have come over the notify-osd thing. I was hoping to find this in docs for pynotify - but no such luck.

Questions I'm still trying to solve:

 - how to control the duration a message is displayed? The timeout doesn't seem to do that..
 - What exactly is the timeout supposed to do?
 - What are valid arguments for category, and what do they do?

---

### Post by Endolith on 2009-11-01
That's because of Shuttleworth's redesign of notifications.  Stuff like timeouts and urgency and X-Y coordinates used to work with the speech-balloon type notifications, but don't anymore since Ubuntu switched to the brown squareish notifications.

---

### Post by rev087 on 2010-05-15
I'm sorry to revive an old topic but I thought it was better then starting my own.

The third argument for pynotify.Notification seems to be an icon, but where can I find a list of available icons? And is it possible to use a custom one?

---

### Post by OgreProgrammer on 2010-05-15
> **rev087 said:**
> I'm sorry to revive an old topic but I thought it was better then starting my own.

The third argument for pynotify.Notification seems to be an icon, but where can I find a list of available icons? And is it possible to use a custom one?

I found this yesterday in the acire python snippets application. I think it shows what you want.

```

#!/usr/bin/env python
#
# [SNIPPET_NAME: Show notification bubble]
# [SNIPPET_CATEGORIES: Notify OSD]
# [SNIPPET_DESCRIPTION: Show a simple notification bubble]
# [SNIPPET_AUTHOR: Jono Bacon <jono@ubuntu.com>]
# [SNIPPET_LICENSE: GPL]

import pynotify
import os

pynotify.init('someName')

imageURI = 'file://' + os.path.abspath(os.path.curdir) + '/logo.png'

n = pynotify.Notification("message name", "message", imageURI)
n.show()

```

---

### Post by Flynsarmy on 2011-05-14
> **rev087 said:**
> where can I find a list of available icons?

There's a list [here]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#How do I get these slick icons").

---

