---
title: "Problems setting up Ubuntu-SDK and QT"
date: 2013-02-25
forum: Programming Talk
---

### Post by moma on 2013-02-25
Hello,
I just want to ask if the Ubuntu-SDK is really ready for testing? I have tried to install it on both Ubuntu 13.04 and 12.10. 

On a fresh Ubuntu 12.10 I get this error.
[http://askubuntu.com/questions/259363/qtcreator-plugins-and-templates-missing](http://askubuntu.com/questions/259363/qtcreator-plugins-and-templates-missing)
QT-creator cannot find plugins.

I have very carefully followed this guide:
[http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/)

QT-framework worked fine in Ubuntu 13.04 but it had only "QtQuickly 1.1" (and no QtQuickly 2.0 which is required by the samples). Others who followed the devel-classes reported similar issues. Ref: [http://www.iloveubuntu.net/familiarize-yourself-qml-explanatory-4-hour-video-class](http://www.iloveubuntu.net/familiarize-yourself-qml-explanatory-4-hour-video-class)

These errors make it hard to start with mobile and tablet development. This QT-thing is just too intricado for us newbies.

[COLOR="Red"]EDIT[/COLOR]: Issue solved, bug fixed by this command.
[COLOR="DarkGreen"]sudo apt-get install libbotan*[/COLOR]
Thanks. Stay optimist! This looks good.

---

### Post by moma on 2013-02-26
deleted.

---

### Post by moma on 2013-02-27
Oh, hello.
Here are my current findings about the Ubuntu-phablet designer.

The "qt-components-ubuntu-demos" package has some very good samples to start with.
Create a working directory
[COLOR="DarkGreen"]$ mkdir $HOME/QML
$ cd $HOME/QML
[/COLOR]
Apt-get source of demos & samples:
[COLOR="DarkGreen"]$ sudo apt-get install dpkg-dev
$ apt-get source qt-components-ubuntu-demos
$ apt-get source qt-components-ubuntu-examples[/COLOR]

**EDIT:** You can also find these samples in /usr/lib/qt-components-ubuntu/ directory, so you could simply copy them to your working folder. Either way is good.
$ cp -fr /usr/lib/qt-components-ubuntu/demos  .
$ cp -fr /usr/lib/qt-components-ubuntu/examples .

Cd to the demos & samples
[COLOR="DarkGreen"]$ cd qt-components-ubuntu-0.1.36~quantal1
[/COLOR]
[COLOR="DarkGreen"]$ cd demos
$ ls -l *qml[/COLOR]
Buttons.qml Popups.qml rogressBars.qml Sliders.qml 
Theming.qml PageStack.qml Toolbars.qml ListItems.qml 
FadingRectangle.qml
...
Run the demos
[COLOR="DarkGreen"]$ qmlscene ListItems.qml
$ qmlscene Toolbars.qml
$ qmlscene examples/converter.qml[/COLOR]
etc..
Or with full path
[COLOR="DarkGreen"]$ qmlscene $HOME/QML/qt-components-ubuntu-0.1.36~quantal1/demos/ListItems.qml [/COLOR]

I also found a sample that requires the "qtdeclarative5-particles-plugin" package.
[COLOR="DarkGreen"]$ sudo apt-get install qtdeclarative5-particles-plugin
[/COLOR]
This is starting to be fun.

---

