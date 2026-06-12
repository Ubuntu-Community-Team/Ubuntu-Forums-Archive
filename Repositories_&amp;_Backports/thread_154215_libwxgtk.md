---
title: "libwxgtk"
date: 2006-04-02
forum: Repositories &amp; Backports
---

### Post by BeeWee on 2006-04-02
Hi,

I'm creating at the moment a project in python using wxwidgets for the graphical interface. The latest version of wxwidgets is 2.6.3 but in the ubuntu sources (in the breezy sources as well as in the dapper sources) is only version 2.6.1 of libwxgtk, so I'd like to compile libwxgtk myself and create my own package. I tried to download wxwidgets from [http://wxwidgets.org](http://wxwidgets.org) , but after compiling and installing it i saw that this was something else (the package that was created was named "wxwidgets" and contained something else)
And now my question: Where I can download the source of the package libwxgtk2.6.0 in version 2.6.3? And do I need to compile python-wxgtk2.6 too, because I'm programing in Python instead of C?

Thanks for your help

BeeWee

P.S.: I hope you understand my question and please sorry my bad English :D

---

### Post by Xian on 2006-04-02
[QUOTE=BeeWee]I tried to download wxwidgets from [http://wxwidgets.org](http://wxwidgets.org) , but after compiling and installing it i saw that this was something else (the package that was created was named "wxwidgets" and contained something else)
And now my question: Where I can download the source of the package libwxgtk2.6.0 in version 2.6.3? [/QUOTE]

This is all just an instance of differing filename conventions. If you will look at the Ubuntu [libwxgtk](http://packages.ubuntu.com/dapper/libs/libwxgtk2.6-0) package website, and then scroll down to where it lists the sources for that file, you will notice it points to the [wxwidgets](http://packages.ubuntu.com/dapper/source/wxwidgets2.6) page. And from there you can also see that yes, it lists libwxgtk as being a package that is built from that file.

---

### Post by wyo on 2006-04-06
[QUOTE=BeeWee]
... version 2.6.1 of libwxgtk, so I'd like to compile libwxgtk myself and create ...[/QUOTE]

Here is a thread ([http://lists.wxwidgets.org/cgi-bin/ezmlm-cgi?5:mss:72467:200604:ohiidcamnfjjohjcfehb](http://lists.wxwidgets.org/cgi-bin/ezmlm-cgi?5:mss:72467:200604:ohiidcamnfjjohjcfehb)) which tells the sad story why version 2.6.3 isn't in Ubuntu.

O. Wyss

---

