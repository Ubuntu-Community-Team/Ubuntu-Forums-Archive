---
title: "Clearing trash folder"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by waltclay on 2011-11-30
After using ubuntu for most of my work for 3 years or so, 11.10 is the last straw. My system disk has only 1G free space, so I copied a folder with its 67G of files to another disk and then moved the original folder to "trash." The file managers say the original is gone. "Trash" only has only a few files it can't find. Still only 1G space.

This forum has such a poor search engine that it could take me half a day to look through posts on "trash."

---

### Post by nothingspecial on 2011-11-30
Is this a request for support?

Any way, if you open a terminal in your home directory (should do by default) and type

```
du -h  | grep [0-9][0-9]G
```

That will list any folder in your home that is 10 gigs or more (and anthing else that happens to match the pattern).

---

### Post by coffeecat on 2011-11-30
Also...

> **waltclay said:**
> I copied a folder with its 67G of files to another disk and then moved the original folder to "trash."

Were you using a "gksudo nautilus" filebrowser, and did you use the delete key to move to trash? If yes to both, the 67G files are sitting in root's trash. If this is your problem, post back and we can tell you how to empty root's trash. And, here's a useful thread about freeing up disk space:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by waltclay on 2011-11-30
Thanks UK guys: I went to bed grumpy and woke up to your quick replies.

I was indeed using root nautilus to "move to trash" for _months_.

I used coffeecat's link to "trash" thread. In a better forum my search on "trash" would have returned that thread at the top of the list.

I found the trashed folder at /root/.local/share/Trash/files. Since I was in nautilus, the "move to trash" option seemed circular (re-entrant?), so I used gnome commander w/root privileges to delete the folder. I now have 60G free space.

I'm off to the ranch for the day, but there's a whole lot more to go through in that Trash. Might find something to retrieve, but will definitely clear more space.

Thanks again. Now, about unity....

---

### Post by coffeecat on 2011-11-30
> **waltclay said:**
> Since I was in nautilus, the "move to trash" option seemed circular (re-entrant?),

One trick is to hard delete with shift+delete. You are asked to confirm, and if you do so the files are deleted immediately and not sent to trash. This works with both a root nautilus and nautilus opened without escalated privileges. You can also use the same keyboard shortcut in Windows to bypass the Recycle Bin.

The forum search facility is known to be less than ideal. You can use google with:

```
site:ubuntuforums.org <your search string>
```

Or you can use this:

[http://www.google.com/advanced_search?q=site:ubuntuforums.org](http://www.google.com/advanced_search?q=site:ubuntuforums.org)

Or, not specifically for Ubuntuforums, but you might find this useful as well:

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Good luck with keeping that trash empty! :wink:

---

### Post by anewguy on 2011-11-30
Not sure exactly what your search looks like, so I can't comment on what you did.  I can suggest, *if* you haven't already tried, not using just the Search box at the top of the screen, but to instead click on the search button and choose advanced search - it gives a lot more flexibility.

Hope things have straightened out for you now. ;)

Dave ;)

---

### Post by oldos2er on 2011-11-30
> **waltclay said:**
> This forum has such a poor search engine that it could take me half a day to look through posts on "trash."

Use Google's site search; google.com, search <some search terms> site:ubuntuforums.org

Also gave your thread a more descriptive title.

---

