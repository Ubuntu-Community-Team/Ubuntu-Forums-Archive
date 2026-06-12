---
title: "Evolution pooped out"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by ctn03 on 2008-05-22
Hi, I'm a newbie...Been using Ubuntu Hardy and Evolution without problems until yesterday when I ran evolution from the terminal and get the following error message:

ctn@ctn-XPS:~$ evolution

(evolution:872: Gtk-WARNING **: Attempting to read the recently used resources file at `/home/cuong/.recently-used.xbel', but the parser failed: Error reading file '/home/cuong/.recently-used.xbel': Is a directory.

(evolution:872: GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

Evolution would start but it takes me to the Setting Assistant instead of my email accounts...

Is there a quick way to fix this?  I didn't do a proper backup so do I need to restore my emails/calender/contacts from the /home/user_name/.evolution folder. And how do I do that?

Thanks a bunch.

---

### Post by vanadium on 2008-05-22
I would try first to move out the .recently-used.xbel file. With "move out" I mean: move the file elsewhere rather than deleting it, so that eventually you can restore it if needed. This will likely fix your issue, though.

---

### Post by ctn03 on 2008-05-22
Thanks, Vanadium. Moving the .recently-used.xbel folder resolve the error.  However, evolution still takes me to the Setting Assistant instead of my emails.

Is there anyway for me to restore the previous settings & restore my emails/calender/contacts from the .evolution folder.  Thanks.

---

### Post by ctn03 on 2008-05-22
Went through Setup Assistant...all my emails/contacts/calender are still there.  But all my IMAP accounts are gone.  Just have to reset them.

Strange, how did the IMAP accounts got wiped out?

---

