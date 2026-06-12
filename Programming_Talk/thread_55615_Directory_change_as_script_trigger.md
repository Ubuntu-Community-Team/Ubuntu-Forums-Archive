---
title: "Directory change as script trigger?"
date: 2005-08-09
forum: Programming Talk
---

### Post by dewarrn1 on 2005-08-09
Hi all.  I'd like to fire a script when the contents of a directory change.  I've googled a bit and come up with some kludgey stuff, but I was wondering whether there was an easier way.  Under Windows, I could use a Python API to catch system signals from MS ReadDirectoryChanges or MS FindFirstChangeNotification.  Examples: [http://tgolden.sc.sabren.com/python/win32_how_do_i/watch_directory_for_changes.html](http://tgolden.sc.sabren.com/python/win32_how_do_i/watch_directory_for_changes.html)
Currently, I'm just running the script as a cron job every so often, but that seems kind of wasteful.  Anyway, thanks for any help.

---

### Post by tomchuk on 2005-08-09
python2.4-gamin in universe will do what you need, if python is your thing.

---

