---
title: "QT4 Designer crashes on startup"
date: 2008-07-09
forum: Programming Talk
---

### Post by nealzilla on 2008-07-09
I'm new to QT programming, but an experienced developer migrating to a new GUI for multi-platform needs.  QT Develop works fine, but cannot launch QT Designer.  I did all the update-alternatives to select all the QT4 tools.  Still running under KDE3 as I'm not liking KDE4 right now.

On Ubuntu 8.04 (64 bit), I get this: :confused:

$ designer-qt4 &
[1] 17965
$ QMetaProperty::read: Unable to handle unregistered datatype 'QList<QChar>' for property 'KCharSelect::displayedChars'
QMetaProperty::read: Unable to handle unregistered datatype 'QList<QColor>' for property 'KColorCombo::colors'
Error while reparenting!
QMetaProperty::read: Unable to handle unregistered datatype 'KUrl' for property 'KUrlRequester::url'
QMetaProperty::read: Unable to handle unregistered datatype 'KFile::Modes' for property 'KUrlRequester::mode'
QMetaProperty::read: Unable to handle unregistered datatype 'KUrl' for property 'KUrlRequester::url'
QMetaProperty::read: Unable to handle unregistered datatype 'KFile::Modes' for property 'KUrlRequester::mode'
Designer: A class name mismatch occurred when creating a widget using the custom widget factory registered for widgets of class QwtScale. It returned a widget of class QwtScaleWidget.

---

### Post by henchman on 2008-07-10
i lately tried to compile it by source and it worked well, though i had not too much luck with other programs before because of errors :)

if you don't mind using non-repository software, you can download that here

[http://trolltech.com/developer/downloads/qt/x11](http://trolltech.com/developer/downloads/qt/x11)

unzip it and then ./configure && make && make install

but took me 40 minutes to compile on a core2duo 2 ghz :guitar:

you may also try the eclipse integration instead of the qt designer, as the eclipse integrations supplies nearly the same functionality

[http://trolltech.com/developer/downloads/qt/eclipse-integration-download](http://trolltech.com/developer/downloads/qt/eclipse-integration-download)

---

### Post by nealzilla on 2008-07-10
Going back over what I did between when it was working and when it stopped working.

Removing the kde4-style-bespin package fixed it.  Nothing like bad style, eh?

---

