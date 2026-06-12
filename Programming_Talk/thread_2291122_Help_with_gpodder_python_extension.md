---
title: "Help with gpodder python extension"
date: 2015-08-18
forum: Programming Talk
---

### Post by CantankRus on 2015-08-18
Firstly let me say I know little coding besides basic shell scripts.

I use gpodder to download and transfer podcasts to my sansa clip sport.
gpodder has an [**_[COLOR="#B22222"]extension[/COLOR]_**]("https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/rename_download.py") in python to rename episodes to "<Episode Title>.<ext>" on download.

Is it possible to prefix "<Episode Title>.<ext>" with "date +%y%m%d-" ...eg 150818-[COLOR="#696969"]<Episode Title>.<ext>[/COLOR].

**_/usr/share/gpodder/extensions/rename_download.py_**
```
# -*- coding: utf-8 -*-
# Rename files after download based on the episode title
# Copyright (c) 2011-04-04 Thomas Perl <thp.io>
# Licensed under the same terms as gPodder itself

import os

import gpodder
from gpodder import util

import logging
logger = logging.getLogger(__name__)

_ = gpodder.gettext

__title__ = _('Rename episodes after download')
__description__ = _('Rename episodes to "<Episode Title>.<ext>" on download')
__authors__ = 'Bernd Schlapsi <brot@gmx.info>, Thomas Perl <thp@gpodder.org>'
__doc__ = 'http://wiki.gpodder.org/wiki/Extensions/RenameAfterDownload'
__payment__ = 'https://flattr.com/submit/auto?user_id=BerndSch&url=http://wiki.gpodder.org/wiki/Extensions/RenameAfterDownload'
__category__ = 'post-download'


class gPodderExtension:
    def __init__(self, container):
        self.container = container

    def on_episode_downloaded(self, episode):
        current_filename = episode.local_filename(create=False)

        new_filename = self.make_filename(current_filename, episode.title)

        if new_filename != current_filename:
            logger.info('Renaming: %s -> %s', current_filename, new_filename)
            os.rename(current_filename, new_filename)
            util.rename_episode_file(episode, new_filename)

    def make_filename(self, current_filename, title):
        dirname = os.path.dirname(current_filename)
        filename = os.path.basename(current_filename)
        basename, ext = os.path.splitext(filename)

        new_basename = util.sanitize_encoding(title) + ext
        # On Windows, force ASCII encoding for filenames (bug 1724)
        new_basename = util.sanitize_filename(new_basename,
                use_ascii=gpodder.ui.win32)
        new_filename = os.path.join(dirname, new_basename)

        if new_filename == current_filename:
            return current_filename

        for filename in util.generate_names(new_filename):
            # Avoid filename collisions
            if not os.path.exists(filename):
                return filename

```

Thanks

---

### Post by The Cog on 2015-08-18
Easy. The functions you need are in the **time **module.

You can pick out the year, month, day from the local time like this:
```
import time
y, m, d = time.localtime()[0:3]
```
but this gives the year as 2015 so then you have to mess around reducing to two digits. the Time module also has a strftime function that formats times according to a format string:
```
import time
title = "example-title"
new_title = time.strftime("%y%m%d-", time.localtime()) + title
```

[https://docs.python.org/2/library/time.html](https://docs.python.org/2/library/time.html)
This is for python2. Python3 is probably much the same.

---

### Post by CantankRus on 2015-08-18
Thanks, but for someone who is scared of snakes
I really need it implemented in the script. ;)

---

### Post by CantankRus on 2015-08-18
Can anyone edit the script to do this?

---

### Post by The Cog on 2015-08-19
OK, try this:
```

# -*- coding: utf-8 -*-
# Rename files after download based on the episode title
# Copyright (c) 2011-04-04 Thomas Perl <thp.io>
# Licensed under the same terms as gPodder itself

import os
import time
import gpodder
from gpodder import util

import logging
logger = logging.getLogger(__name__)

_ = gpodder.gettext

__title__ = _('Rename episodes after download')
__description__ = _('Rename episodes to "<Episode Title>.<ext>" on download')
__authors__ = 'Bernd Schlapsi <brot@gmx.info>, Thomas Perl <thp@gpodder.org>'
__doc__ = 'http://wiki.gpodder.org/wiki/Extensions/RenameAfterDownload'
__payment__ = 'https://flattr.com/submit/auto?user_id=BerndSch&url=http://wiki.gpodder.org/wiki/Extensions/RenameAfterDownload'
__category__ = 'post-download'


class gPodderExtension:
    def __init__(self, container):
        self.container = container

    def on_episode_downloaded(self, episode):
        current_filename = episode.local_filename(create=False)

        new_filename = self.make_filename(current_filename, episode.title)

        if new_filename != current_filename:
            logger.info('Renaming: %s -> %s', current_filename, new_filename)
            os.rename(current_filename, new_filename)
            util.rename_episode_file(episode, new_filename)

    def make_filename(self, current_filename, title):
        dirname = os.path.dirname(current_filename)
        filename = os.path.basename(current_filename)
        basename, ext = os.path.splitext(filename)
        prefix = time.strftime("%y%m%d-", time.localtime())

        new_basename = prefix + util.sanitize_encoding(title) + ext
        # On Windows, force ASCII encoding for filenames (bug 1724)
        new_basename = util.sanitize_filename(new_basename,
                use_ascii=gpodder.ui.win32)
        new_filename = os.path.join(dirname, new_basename)

        if new_filename == current_filename:
            return current_filename

        for filename in util.generate_names(new_filename):
            # Avoid filename collisions
            if not os.path.exists(filename):
                return filename

```

---

### Post by CantankRus on 2015-08-19
Ok thanks, I'll try it.
I'm going to [**_[COLOR="#B22222"]Learn Python the Hard Way[/COLOR]_**]("http://learnpythonthehardway.org/book/")
to see if I can understand the script and possibly start writing my own simple python scripts.

---

