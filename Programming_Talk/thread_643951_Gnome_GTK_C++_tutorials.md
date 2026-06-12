---
title: "Gnome GTK C++ tutorials"
date: 2007-12-18
forum: Programming Talk
---

### Post by DrMega on 2007-12-18
Hi

I am a developer (on Windows) and would like to develop stuff for Linux, in particular the Gnome desktop environment.

Does anyone know of any good tutorials in developing Gnome apps in C++ using GTK?

Ideally I'm looking for a quickstart of some kind. I don't need to read about C++ language basics, I just need to read about how I design a user interface (using a GUI designer of some kind), and how I get my C++ code to use and interact with the GUI.

Thanks in advance.

---

### Post by LaRoza on 2007-12-18
[http://laroza.pbwiki.com/C++](http://laroza.pbwiki.com/C++)

I don't know how much will be useful to you, but something should pop out.

---

### Post by jespdj on 2007-12-19
The C++ binding to GTK+ is called [gtkmm](http://www.gtkmm.org/).

---

### Post by zipperback on 2008-08-24
> **jespdj said:**
> The C++ binding to GTK+ is called [gtkmm](http://www.gtkmm.org/).


They're licence is a little confusing for me.


[http://www.gtkmm.org/license.shtml]("http://www.gtkmm.org/license.shtml")
> 
License

gtkmm is licensed under the GNU Library General Public License (LGPL) for all platforms. Our intent in licensing it in this way is to provide it for use through shared libraries in all projects both open and proprietary. Other GNU projects may of course integrate and link in a static manner. The full body of the license is provided for your inspection.

This is the only license which grants you use of the software, so if you do not agree to its terms, you may not use this software. 


I'm developing something which I plan on releasing under GPL v3 so I'm not sure what kind of impact this would have on the use of gtkmm.
Perhaps I'll just keep looking around and find something which will work better with a GPL V3 license.

I'm open to suggestions and clarificaton on the subject if anyone have more experience with it that myself.

Thank you.

- zipperback
:popcorn:

---

### Post by techmarks on 2008-08-24
You could still use GTK+ with C++, without having to use gtkmm, but gtkmm does make it nicer.

---

### Post by nrs on 2008-08-24
> **zipperback said:**
> 
I'm developing something which I plan on releasing under GPL v3 so I'm not sure what kind of impact this would have on the use of gtkmm.

None.

---

### Post by WitchCraft on 2008-08-24
> **zipperback said:**
> 

Perhaps I'll just keep looking around and find something which will work better with a GPL V3 license.



Use wxWidgets:
[http://www.wxwidgets.org/](http://www.wxwidgets.org/)

---

### Post by nrs on 2008-08-24
> **WitchCraft said:**
> Use wxWidgets:
[http://www.wxwidgets.org/](http://www.wxwidgets.org/)

1.) Eww.
2.) There are no issues using LGPL code in GPL'd programs, they're compatible. The restriction applies to proprietary software, they may link to it, but they cannot create derivative works.

> A program that contains no derivative of any portion of the Library, but is designed to work with the Library by being compiled or linked with it, is called a "work that uses the Library". Such a work, in isolation, is not a derivative work of the Library, and therefore falls outside the scope of this License.
[http://www.fsf.org/licensing/licenses/index_html#GPLCompatibleLicenses](http://www.fsf.org/licensing/licenses/index_html#GPLCompatibleLicenses)
> 
GNU Lesser General Public License (LGPL) version 2.1

This is the previous version of the LGPL: a free software license, but not a strong copyleft license, because it permits linking with non-free modules.** It is compatible with GPLv2 and GPLv3**. We generally recommend the latest version of the LGPL, for special circumstances only.


---

