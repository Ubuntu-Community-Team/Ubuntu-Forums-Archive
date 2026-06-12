---
title: "gnome mime, help please....."
date: 2008-07-10
forum: Programming Talk
---

### Post by Derviansoul on 2008-07-10
Hello

This is my question, maybe not the best place to ask, but... direct me please.
I use avant-window-navigator, and gnome do (brilliant apps,btw), now my question is, if i open per example a movie with pcmanfm, nautilus or dolphin it opens vlc because i change the default player with nautilus, and that's fine i'm happy about it.

But if i try to open with "gnome do" or avant window navigator file browser, what i get it's totem, now my question is why? i've being reading gnome-vfs developer tutorials and the information around mime types looks really incomplete to me, and looking at some mail lists apparently it's development it's stalled. 

Yesterday i've being on a chatroom with awn devs and they told me that their file browser applet calls a this function gnome_vfs_mime_application_launch_with_env (), for 12h i've being looking gconf and gnome-vfs documentation and i still can't figure it out what the hell gnome uses to choose it's defaults apps for some file type.
Can someone explain me this, and how could i change it?
thanks

---

### Post by henchman on 2008-07-10
well, awn uses gnome_vfs_mime_application_launch_with_env you say...

i did a koders search for that name, found a file called nautilus-program-choosing.c, which contains the following function

```
void
nautilus_launch_application (GnomeVFSMimeApplication *application, 
			     GList *files,
			     GtkWindow *parent_window)
{

        /* stripped unnecessary parts */

	result = gnome_vfs_mime_application_launch_with_env (application, uris, envp);

        /* stripped unnecessary parts */
}


```

if this is the currently used one and not of an old version of nautilus, it looks as if nautilus was using the same function...

---

### Post by Derviansoul on 2008-07-10
hello

just found out that gnome uses it's defaults apps [here]("http://ubuntuforums.org/showthread.php?p=4986640#post4986640") from a post in this forum, i still couldn't manage to change all the extensions that i wanted,but i feel that i'm on the good way, thanks allot


```
/etc/gnome/defaults.list
```

---

### Post by Derviansoul on 2008-07-16
Hello

For who this might interest i found as well the file that contains the default applications inside nautilus.

```

in your home folder:

.local/share/applications/mimeapps.list
```

regards.

---

