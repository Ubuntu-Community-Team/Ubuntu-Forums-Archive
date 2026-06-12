---
title: "MonoDevelop GTK# TrayIcon notification/balloon ?"
date: 2008-02-25
forum: Programming Talk
---

### Post by Sam on 2008-02-25
I'm developing a little tool in GTK#, using a TrayIcon. I need to implement a notification which can popup near the tray icon and disapear after a delay, or if the user clicks on it.

I'm looking for something like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60834&stc=1&d=1203992111[/IMG]
(the same as Update Notifier or Restricted Drivers Manager)

or this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60833&stc=1&d=1203992111[/IMG]
(not so sophisticated)


Is this possible to do so ? I've search a lot, didn't find anything... Am I missing something ?


Oh, I forgot to say, it should be run under Windows too.

---

### Post by imdano on 2008-02-26
I believe all the examples you mentioned use [libnotify](http://www.galago-project.org/news/index.php) to achieve what you're looking for.

---

### Post by Sam on 2008-02-26
Thank you, I'll check this.

---

### Post by mashcaster on 2008-10-22
Hello,

Did you manage to get the round type balloons to work?

---

