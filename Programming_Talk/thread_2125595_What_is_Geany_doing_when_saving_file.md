---
title: "What is Geany doing when saving file?"
date: 2013-03-14
forum: Programming Talk
---

### Post by bird1500 on 2013-03-14
Hi,
while tracking all (IN_ALL_EVENTS) file events with sys/inotify.h I got odd results when Geany modifies and saves a (text) file, for example:
a text file is open in Geany, I add a letter to the file (to change its contents) and click save (Ctrl+S), the Geany "save" action triggers the following **odd** inotify events (event->mask printed bitwise) in the following order:

```

events triggered when listening for IN_ALL_EVENTS
00000000 00000000 00000000 00100000 //IN_OPEN
00000000 00000000 00000000 00001000 //IN_CLOSE_WRITE
00000000 00000000 00000000 10000000 //IN_MOVED_TO
00000000 00000000 00000000 00001000 //IN_CLOSE_WRITE
00000000 00000000 00000000 00100000 //IN_OPEN
00000000 00000000 00000000 00000001 //IN_ACCESS
00000000 00000000 00000000 00010000 //IN_CLOSE_NOWRITE

```

Notice the event chain starts with "IN_OPEN" (but the file was already open in Geany), also, IN_MOVED_TO is typically used for **renaming** files.
So what is Geany doing?
I thought it should be as simple as: (1) IN_MODIFY and (2) IN_CLOSE_WRITE, end of story, no?

---

### Post by Linteg on 2013-03-14
To be more robust against errors that may occur while saving the file it's possible that instead of simply overwriting an existing file, Geany is first saving the file to a temporary file name then renaming it to the desired name which might explain the IN_MOVED_TO event.

---

### Post by trent.josephsen on 2013-03-14
I'd say it's more likely that it renames the original to a backup file, and saves the modified copy under the original filename.

It's possible some of these events are internal to Geany, and do not apply to the specific file you're editing. I don't know anything about Geany, but if it saves state from one invocation to the next, that has to be saved somewhere. Vim, for instance, stores temporary data in a dotfile in the current directory so that if your editing session gets killed between saves you won't have to lose everything.

---

### Post by r-senior on 2013-03-15
You might want to have a play around with the Preferences - Various tab:

[http://www.geany.org/manual/#various-preferences](http://www.geany.org/manual/#various-preferences)

In particular the settings you have for use_atomic_file_saving.

Also whether you have the Backup Copy plugin installed:

[http://www.geany.org/manual/#backup-copy](http://www.geany.org/manual/#backup-copy)

---

