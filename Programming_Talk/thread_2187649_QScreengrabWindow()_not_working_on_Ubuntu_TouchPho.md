---
title: "QScreen::grabWindow() not working on Ubuntu Touch/Phone"
date: 2013-11-13
forum: Programming Talk
---

### Post by liripiri on 2013-11-13
Hi everyone. I'm developing an app for Ubuntu Touch (13.10) running on Nexus 4 that has a feature that can take a screenshot of my running app. However this is not working on the device but IS working when I run my app on Ubuntu desktop. This is a C++ plugin that is loaded to my QML application. Here's the code in short:

```

[COLOR=#800000]QScreen *screen [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#800080]QGuiApplication[/COLOR][COLOR=#000000]::[/COLOR][COLOR=#000000]primaryScreen[/COLOR][COLOR=#000000]();[/COLOR]
[COLOR=#800080]QPixmap [/COLOR][COLOR=#000000]pxm [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#800000]screen[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]grabWindow[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000080]qApp[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]focusWindow[/COLOR][COLOR=#000000]()->[/COLOR][COLOR=#000000]winId[/COLOR][COLOR=#000000]());
[/COLOR]
```[FONT=Verdana]

pxm QSize is always (0, 0). However on Desktop, it returns a valid screenshot.

I've also tried this, but it's not working:
[/FONT]```

[COLOR=#800080]QWindow [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000]topWin [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#000080]qApp[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]topLevelAt[/COLOR][COLOR=#000000]([/COLOR][COLOR=#800080]QPoint[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000080]360[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000080]2[/COLOR][COLOR=#000000],[/COLOR][COLOR=#000080]640[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000080]2[/COLOR][COLOR=#000000]));
WId id = topWin->winId(); // <--- returns 1 (device)
[/COLOR]
[COLOR=#800080]QPixmap [/COLOR][COLOR=#000000]pxm [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#800000]screen[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]grabWindow[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000080]id[/COLOR][COLOR=#000000]);[/COLOR]

```
[FONT=Verdana]
How do I get the correct winId? I assume the problem is with that since grabWindow is working on desktop.
[/FONT]

---

### Post by liripiri on 2013-11-13
Just realized that maybe this is not implemented or is not yet working on Ubuntu Touch since it uses the new Mir display server and is it so that Ubuntu desktop is using something else?

---

### Post by liripiri on 2013-11-14
Tried also:
```

[COLOR=#800080]QWindow [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000]topwin [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#000080]NULL[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#808000]foreach[/COLOR][COLOR=#000000]([/COLOR][COLOR=#800080]QWindow [/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000080]qApp[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]topLevelWindows[/COLOR][COLOR=#000000]()) [/COLOR][COLOR=#000000]{[/COLOR][INDENT][COLOR=#000080]qDebug[/COLOR][COLOR=#000000]() [/COLOR][COLOR=#000000]<< [/COLOR][COLOR=#008000]"win[/COLOR][COLOR=#008000]id:" [/COLOR][COLOR=#000000]<< [/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]winId[/COLOR][COLOR=#000000]();[/COLOR][/INDENT]
[INDENT][COLOR=#000080]qDebug[/COLOR][COLOR=#000000]() [/COLOR][COLOR=#000000]<< [/COLOR][COLOR=#008000]"win[/COLOR][COLOR=#008000]is[/COLOR][COLOR=#008000]active:" [/COLOR][COLOR=#000000]<< [/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]isActive[/COLOR][COLOR=#000000]();
[/COLOR][COLOR=#000080]qDebug[/COLOR][COLOR=#000000]() [/COLOR][COLOR=#000000]<< [/COLOR][COLOR=#008000]"win[/COLOR][COLOR=#008000]is[/COLOR][COLOR=#008000]toplevel:" [/COLOR][COLOR=#000000]<< [/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]isTopLevel[/COLOR][COLOR=#000000]();
[/COLOR][COLOR=#000080]qDebug[/COLOR][COLOR=#000000]() [/COLOR][COLOR=#000000]<< [/COLOR][COLOR=#008000]"win[/COLOR][COLOR=#008000]size:" [/COLOR][COLOR=#000000]<<[/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]*size*[/COLOR][COLOR=#000000]();
[/COLOR][COLOR=#808000]if [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]isActive[/COLOR][COLOR=#000000]() [/COLOR][COLOR=#000000]&& [/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]isTopLevel[/COLOR][COLOR=#000000]()) [/COLOR][COLOR=#000000]{
[/COLOR][COLOR=#000000]     topwin [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#000000]win[/COLOR][COLOR=#000000];
[/COLOR][COLOR=#808000]     break[/COLOR][COLOR=#000000];
[/COLOR][/INDENT]
[INDENT][COLOR=#000000]}
[/COLOR][/INDENT]
[COLOR=#000000]}
[/COLOR]
[COLOR=#808000]if [/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]topwin [/COLOR][COLOR=#000000]!= [/COLOR][COLOR=#000080]NULL[/COLOR][COLOR=#000000]) [/COLOR][COLOR=#000000]{
[/COLOR][INDENT][COLOR=#800080]QPixmap [/COLOR][COLOR=#000000]pxm [/COLOR][COLOR=#000000]= [/COLOR][COLOR=#800000]m_screen[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]grabWindow[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]topwin[/COLOR][COLOR=#000000]->[/COLOR][COLOR=#000000]winId[/COLOR][COLOR=#000000]());
[/COLOR][/INDENT]
[COLOR=#000000]}
[/COLOR]
```

.. which works again on Desktop but not on device. WId seems to be correct, but grabWindow() must be buggy...

---

### Post by nidzo732 on 2013-11-14
I haven't done much programming for Ubuntu Touch but i think that the problem is that Ubuntu Touch doesn't have an actual window manager like the one used on desktop.
This is just a wild guess, I'm not familiar with the internals of Qt. grabWindow probaly relies on window manager or X to give it some kind of pointer to the actual window but those don't exist on the phone (might be that Mir hasn't implemented it yet).
Maybe you should check out the Qt sources and see what grabWindow relies on.

[B]Edit
[/B]
I've checked out the Qt source, it seems that grabWindow relies on OS specific implementation, you can find the actual code of grabWindow in Qt source in /src/gui/image/gpixmap_*.cpp, replace the asterisk with the actual graphics implementation (X11, Windows, Mac).
The X11 version is used on Desktop linux and it relies on the functions from X11 API which are available on the desktop, but the phone uses Mir, try contacting Qt or Mir developers to see if this will be implemented for Mir in the future.
Here's the link for the X11 implementation:
[https://qt.gitorious.org/qt/qt/source/a18d932b09137bb0f20e254dec5bb2313863d3e4:src/gui/image/qpixmap_x11.cpp#L2108](https://qt.gitorious.org/qt/qt/source/a18d932b09137bb0f20e254dec5bb2313863d3e4:src/gui/image/qpixmap_x11.cpp#L2108)

---

