---
title: "C++, Qt and libindicate-qt"
date: 2011-07-03
forum: Programming Talk
---

### Post by mscm on 2011-07-03
Hi there.

I'm writing an application using C++ and Qt. I want it to use Messaging Menu, but I can't use libindicate.h, because I won't get signals (gtk-style) working in my Qt application.

I downloaded libindicate-qt and included it to my project. Everything was ok, I saw my app in Messaging Menu and I added message source. I wanted to set count property (time is working fine, but I don't need it), but then I saw sth like that:

[IMG]http://i.imgur.com/ul6EH.png[/IMG]

Empty circle, without my number. :x

My code: 
```

    QIndicate::Server* is = QIndicate::Server::defaultInstance();
    is->setDesktopFile("full path to my .desktop file);
    is->setType("message.sth");
    is->show();
    QIndicate::Indicator *mIndicator = new QIndicate::Indicator(is);
    mIndicator->setNameProperty("Whatever");
    mIndicator->setCountProperty(2);
    mIndicator->show();

```libindicate-dev - 0.5.0-0ubuntu2
libindicate-qt-dev - 0.2.5.91-0ubuntu2
Qt 4.7.2-0ubuntu6.2
Ubuntu Natty

What can I do to fix it?

[B]SOLVED
[/B]Ok, I found the solution. You can't use setCountProperty method. Instead of it you have to use setIndicatorProperty("count","1"). Yeah, int as string...

---

