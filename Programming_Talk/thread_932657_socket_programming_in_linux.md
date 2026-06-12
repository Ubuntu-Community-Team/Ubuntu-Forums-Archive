---
title: "socket programming in linux"
date: 2008-09-28
forum: Programming Talk
---

### Post by savalan86 on 2008-09-28
Hello My Friends ...
i have a project in university , my project is a client/server system , like a chat server . in Microsoft Windows i use winsock , but in linux i dont have any experience to this issuese ...
i search in google , and now know that c++ standard dont have any library for socket (network) programming . now i want to know in linux (unix) , i must use which libraries to this issues ... . my friends , i want a reliable and popular and portable way .
because my project is a open source project and i want use common and portable libraries ...
for instance i want to know , some applications such as firefox , wget , opera , pidgin , and other ... use which libraries to this issues
really my project transmit big data's between nodes ...
thanks dears [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by dribeas on 2008-09-28
> **savalan86 said:**
> I want a reliable and popular and portable way.

There are a couple of portable libraries out there: [ACE]("http://www.dre.vanderbilt.edu/Doxygen/Stable/ace/index.html"), [POCO]("http://pocoproject.org/poco/info/index.html"), [Boost]("http://www.boost.org/") does not have a socket library, but ASIO has network support and it might be enough for your needs. If you plan on having a GUI, then [QT]("http://doc.trolltech.com/4.2/index.html") and [wxWidgets]("http://www.wxwidgets.org/") have portable socket libraries. You could check gnome's gnet (I don't know if it has been ported to windows though).

It all depends on your needs.

---

