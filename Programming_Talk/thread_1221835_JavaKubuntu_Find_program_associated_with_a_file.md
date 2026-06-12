---
title: "Java/Kubuntu: Find program associated with a file"
date: 2009-07-24
forum: Programming Talk
---

### Post by qforce on 2009-07-24
Hello,

Does anybody know how to find the program associated with a certain file on Kubuntu? For example, I've got a PDF file and I'd like open it with the system's default PDF viewer (but from another program rather than by just double-clicking on it).

Thanks in advance!

---

### Post by kpkeerthi on 2009-07-24
-- bad post --

---

### Post by froggyswamp on 2009-07-24
It's not trivial, unless you find a Java library you can use right away.
The associations can be found by reading and parsing the data from the corresponding .desktop files which are scattered across the system in given directories.
About the location of these directories and the format of the .desktop files you can learn from freedesktop.org, for example the .desktop specs are here:
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

A sample implementation (in C++ though) of how to search for all the folders that contain .desktop files:
```

vector<Glib::ustring>* Settings::listDesktopEntryDirs() {

    vector<Glib::ustring> *pv = new vector<Glib::ustring > ();
    const Glib::ustring apps = "applications/";

    //highest priority to settings from home dir
    Glib::ustring sLocalDataDir = Glib::get_user_data_dir();
    if (sLocalDataDir.size() > 1) {
        pv->push_back(Glib::build_filename(sLocalDataDir, apps));
    }

    Glib::ustring sPaths = getenv("XDG_DATA_DIRS");

    //if not set use defaults
    if (sPaths.size() < 2) {
        sPaths = "/usr/local/share/:/usr/share/";
    }

    const Glib::ustring sep = ":";
    size_t iStart = 0;
    size_t iEnd = 0;

    while (true) {
        iEnd = sPaths.find(sep, iStart);
        if (iEnd == Glib::ustring::npos) {
            break;
        }

        Glib::ustring sToken = sPaths.substr(iStart, iEnd - iStart);
        iStart = iEnd + 1;

        pv->push_back(sToken + apps);
    }

    if (iStart < sPaths.size()) {
        pv->push_back(sPaths.substr(iStart, sPaths.size() - iStart) + apps);
    }

    return pv;

}

```

---

### Post by qforce on 2009-07-25
@ froggyswamp

Thanks for your answer. Is there really no easier way to do this? I was hoping for a command line tool or something... :(
Besides, I couldn't find a library for this either.

---

### Post by monraaf on 2009-07-25
You can use **xdg-open** for that.

---

### Post by froggyswamp on 2009-07-25
OMG sorry, I thought for some reason you want a list of "Open with" apps.

Since Java 6 you can do this, example:

```

import java.awt.*;

public class Main {

    public static void main(String[] args) {
        Desktop d = Desktop.getDesktop();
        try {
            d.open(new java.io.File("/home/fox/Desktop/books/GTK Development 2007.pdf"));
        } catch( Exception exc) {
            exc.printStackTrace();
        }
    }

}

```

> but from another program
Oops, I'm confused.

---

### Post by qforce on 2009-07-25
@ moonraf
xdg-open is just what I was looking for, thanks!

@ froggyswamp
Last time I checked the Java Desktop API only worked on Gnome, but not on KDE... :(

---

