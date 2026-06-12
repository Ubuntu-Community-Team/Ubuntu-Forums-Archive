---
title: "Where to save user data?"
date: 2010-08-04
forum: Programming Talk
---

### Post by jw37 on 2010-08-04
Hello all developers and others as well!

I'm still quite new to Linux. What is the preferred place to save user data of an application? I mean small data that the end user creates with the application, for example a list of records (name + phone number + address). It's data that the end user doesn't think as a file, and the end user doesn't have to see any SaveFile dialog. Is this Linux/Ubuntu way to do it? Or am I still stuck in Windows thinking?

All comments concerning this issue are very welcome!

---

### Post by squaregoldfish on 2010-08-04
These bits and pieces are generally stored in the user's home directory, in a file/directory starting with a . (so it's not usually visible).

If you do ls -a in your home directory, you'll see loads of these files created by the various applications you've used.

Steve.

---

### Post by jw37 on 2010-08-04
Thank you very much! :D

---

### Post by SledgeHammer_999 on 2010-08-04
Please follow the [XDG Base Directory Specification](http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html) standard.

I don't know which gui toolkit you're using but if you're using Gtk(gtkmm, pygtk etc) then the toolkit provides functions that automatically find the location of these special folders on any system.

---

### Post by jw37 on 2010-08-04
Thanks for that, too :D   -> Bookmarks

I don't use any GUI toolkit yet. First code the program and text-based UI... Allright maybe my question was a bit premature :rolleyes:  Anyway, you can write the data in the right place regardless the UI type don't you? ;)

---

### Post by wkhasintha on 2010-08-04
~/.<Application> is where user configs normally resides.

---

### Post by SledgeHammer_999 on 2010-08-04
@**wkhasintha** not anymore. Many apps start to follow the XDG standard. And usually that means that you save the configs to ~/.config/<application> 
The path to .config should not be hardcoded to your program.

@**jw37**, yes you can. The gui functions just help you discover the right place easier. (to be more precise, in gtk the helper function is provided by the glib module which is gui-agnostic).

So you have 3 choices. 
1. If you use a gui toolkit, use it's helper function to locate the right place.
2. Read the environment variables(eg XDG_CONFIG_HOME) to determine the location.
3. Use the [xdg-user-dirs](http://www.freedesktop.org/wiki/Software/xdg-user-dirs) tool. I think many modern distros include it by default, but I have never used it.

Happy coding.

---

### Post by interval1066 on 2010-08-04
If your doing gnome development you should keep user data managed with gconf. Anything system-wide should be xdg.

---

### Post by jw37 on 2010-08-05
> **SledgeHammer_999 said:**
> 2. Read the environment variables(eg XDG_CONFIG_HOME) to determine the location.

I think this is the way I'll do at this point.

> Happy coding.

Thanks!

> **interval1066 said:**
> If your doing gnome development you should keep user data managed with gconf. Anything system-wide should be xdg.

Is there something bad using xdg for gnome applications? Though I haven't thought much about GUI yet...

Anyway, in general, there are three types of "user data" (as I see it). First, obvious document files which the end user opens and saves (for example text or sound files). Second, pure configuration data (or settings; application preferences, colours, styles, etc). Then there's a "twilight zone" between these two: Small data that could be thought as a document but is always in a single file, and letting the end user to select the file would only be waste of time and confuse the end user. However, this kind of data is not pure configuration data and should not be put into config files. This is how I think, but I'm not sure if this is how most programmers think. But I believe the right place to put these "twilight zone" files is

$XDG_DATA_HOME/subdir/filename
or
/usr/share/subdir/filename

where subdir is the applications name.

---

### Post by SledgeHammer_999 on 2010-08-05
> **jw37 said:**
> 
Is there something bad using xdg for gnome applications? Though I haven't thought much about GUI yet...

The cross-desktop standard is xdg not gconf. Use gconf ONLY if you want to tie your application to GNOME. (If you develop using Gtk+ that doesn't necessarily mean you should tie your app to GNOME)

---

