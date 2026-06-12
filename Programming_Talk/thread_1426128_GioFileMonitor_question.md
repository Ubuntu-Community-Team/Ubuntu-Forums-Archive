---
title: "Gio::FileMonitor question"
date: 2010-03-09
forum: Programming Talk
---

### Post by kahumba on 2010-03-09
Hi,
The Gio::FileMonitor's event function looks like this:
[PHP]
on_changed (
const Glib::RefPtr< File >& file,
const Glib::RefPtr< File >& other_file,
FileMonitorEvent event_type)
[/PHP]Afaik first file argument is the file that changed, but what for is the **second** file argument?

---

### Post by kahumba on 2010-03-10
No one?

---

### Post by Zugzwang on 2010-03-10
No clue. Seems to be undocumented. Probably that parameter is put there to be able to support file renaming operations at some point in the future.

---

### Post by kahumba on 2010-03-10
Thanks, well, file renaming so far goes through "event deleted" and then "event created" events, so it's possible what you're suggesting is true, but I wonder why such an obvious issue hasn't been "fixed" when they created the API in the first place, (Java7 handles this easily through 'ENTRY_MODIFY"..), it's not like sending a man to the moon..

---

### Post by cszikszoy on 2010-03-10
Other file is supposed to be used when you move or rename a file.  File would be the name of the original file, other would be the new name.  Unfortunately, the new file argument was never used in the core of GIO.  There was a bug report, and there has been some activity on this (I think resolving the issue and actually using other file as it was meant to be used) but I can't seem to find the bug report.

---

