---
title: "Standard function to sanitize absolute file path?"
date: 2013-03-23
forum: Programming Talk
---

### Post by bird1500 on 2013-03-23
To check (*update: on a modern Unix-like OS*) if a file path is (will be) the closest parent of another path I need to first sanitize both paths: remove possible extra '/' and '.' characters (I'm thinking about ".." in the future).
From
"/.///home//&#20013;&#22830;&#25991;//.//fox/&#26032;&#21326;&#31038;&#21271;&#20140;&#65299;&#26376;&#65298;///"
I should get
"/home/&#20013;&#22830;&#25991;/fox/&#26032;&#21326;&#31038;&#21271;&#20140;&#65299;&#26376;&#65298;/"
The Chinese characters in the path are there to make sure it works with Unicode chars.

realpath(3) fails with "no such file or directory" so it doesn't suit my needs.
**Perhaps there's some (standard Unix/POSIX) library function that already does this?**

My function:
```

void
sanitizePath(Glib::ustring &unb)
{
    if(unb.size() < 1) {
        return;
    }
    
    Glib::ustring::value_type l, c;
    l = unb.at(0);
    
    for(int i=1; i<unb.size(); i++) {
        c = unb.at(i);
        
        if(c == '/') {
            if(l == '/') {
                unb.erase(i, 1);
                i--;
                continue;
            }
        } else if(c == '.') {
            if((l == '/') && (i < unb.size()-1) && (unb.at(i+1) == '/')) {
                unb.erase(i, 1);
                i--;
                continue;
            }
        }
        
        l = c;
    }
}

```
Usage:
```

Glib::init();
Glib::ustring s1 = "/.///home//&#20013;&#22830;&#25991;//.//fox/&#26032;&#21326;&#31038;&#21271;&#20140;&#65299;&#26376;&#65298;///";
sanitizePath(s1);
std::cout << "sanitized: \"" << s1.data() << "\"" << std::endl;

```
Yields:
> sanitized: "/home/&#20013;&#22830;&#25991;/fox/&#26032;&#21326;&#31038;&#21271;&#20140;&#65299;&#26376;&#65298;/"

---

### Post by Tony Flury on 2013-03-23
And of course your function is none-portable - you may not intend to use it on Windows - but someone else might :-) 

I would at least add a warning on the comments that it is Linux specific.

---

### Post by bird1500 on 2013-03-23
Yes, my function is for my app which is only for Linux, sorry I forgot to mention I only care about (modern) Unix-like systems, I'll update the 1st post.
Also, I said "standard" mainly because these tend to already be present in the OS and I'd just have to call it.

---

### Post by r-senior on 2013-03-23
GIO has [g_file_get_path]("https://developer.gnome.org/gio/stable/GFile.html#g-file-get-path") and [g_file_resolve_relative_path]("https://developer.gnome.org/gio/stable/GFile.html#g-file-resolve-relative-path") functions that should do what you need and are probably more robust than most of us would write ourselves.

If you are already using GLib with C++, configuring the project for GIO should be similar. I *think*, if you happen to be using gtkmm, that you get GIO anyway -- but you'd have to confirm that.

---

### Post by bird1500 on 2013-03-23
That seems to be it. Thanks, it also handles ".." properly (goes up one level).
Though the Gtkmm (C++) implementation requires to create a Gio::File before using that function which one shouldn't need to create if the path is absolute, in Gtkmm it should be a static function instead.

**EDIT**: After tinkering with it it turns out Gio::File sanitizes the path when created at Gio::File::create_for_path(path), after that calling file->get_path() returns a sanitized path. Out of curiosity I wanted to see how it's implemented but I got lost in a labyrinth of #defines and cross-references:
Glib::RefPtr<Gio::File> is a wrap of GFile which is in libglib2.0-dev which from "gfile.c" calls "g_file_new_for_path()" which calls "g_vfs_get_file_for_path()" from "gvfs.c" which calls:
> 
class = G_VFS_GET_CLASS (vfs);
return (* class->get_file_for_path) (vfs, path);

And that's where I'm lost, where's the class->get_file_for_path() implementation?

---

