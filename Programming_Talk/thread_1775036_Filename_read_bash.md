---
title: "Filename read bash"
date: 2011-06-04
forum: Programming Talk
---

### Post by j_arquimbau on 2011-06-04
I know it might be a very simple question, but I've been looking for an answer and I haven't been able to find it, may be because of the search terms...

I'd like to create a Nautilus right-button bash script (~/.gnome2/nautilus-scripts/) that would create a symbolic link to the file and then move the original file to an specific destination.

How could I set the filename variable in bash? Would it be some kind of:

filename=$ read 'whatever'

I have on clue on this.

Thank you in advance!

---

### Post by j_arquimbau on 2011-06-04
Got it:

[https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)

path="${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS}"

---

