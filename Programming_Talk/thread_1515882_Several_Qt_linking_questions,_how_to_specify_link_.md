---
title: "Several Qt linking questions, how to specify link version"
date: 2010-06-23
forum: Programming Talk
---

### Post by toglia3d on 2010-06-23
First post!

Well, I have been like crazy blaming my eclipse project configuration for a crash I'm getting after instantiating some qt classes, but maybe you guys can give me a better hint.

Right now I'm doing Qt development with Eclipse and everything works perfect if you use "Qt project templates" provided by Eclipse's Qt plugin. But In my case I already had a C++ project so the problems started.

My configuration:
Qt Instalation directory: /home/user/DEV/SDK/QtSDK
Qt Include Directory: /home/user/DEV/SDK/QtSDK/qt/include
Qt Link Directory: /home/user/DEV/SDK/QtSDK/qt/lib
Linking to: QtCore

```
#include <QEasingCurve>
int main() {
	QEasingCurve curve(QEasingCurve::InBounce);
	return 0;
}
```
Compiles and links perfectly, but it crashes on the first line. with:```
 ../AnimationTest: symbol lookup error: ../AnimationTest: undefined symbol: _ZN12QEasingCurveC1ENS_4TypeE

```
That doesn't make much sense. But what I thought is that maybe the executable is grabbing the old installed QtCore.so library on my /usr/lib folder instead of the new one in /home/user/DEV/SDK/QtSDK/qt/lib? In that case, how can that be? am I not telling eclipse I want to use the new one? how can I fix that?

Secondly, how can I choose to link to libQtCore.so.4.6.3 and not the default libQtCore.so (that probably links to an outdated QtCore)

Lastly, how can I install the latest Qt4.6.3 on my /usr/lib folder without breaking old qt version that surely support some of my installed programs.

Thanks for any help!

---

