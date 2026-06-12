---
title: "way to convert SWF to EXE and PKG?"
date: 2013-12-27
forum: Programming Talk
---

### Post by andrewkrieg on 2013-12-27
Okay. I developed a Flash game creator with a drag and drop interface that lets you quickly design a game and upload it to the web for all to play. I want to take it to the next level though. I want multiple export types. The current export type is a *.swf file (flash file), but I want to be able to export as a *.exe for Windows platform and *.apk for android platform WITHOUT changing to BASE export type (*.swf).

This is what I need:

[LIST]
[*]A console based application that converts a *.swf to a *.exe so my program can invoke it behind the scenes.
[*]A console based application that converts a *.swf to a *.apk so my program can invoke it behind the scenes.
[/LIST]

I was thinking something like an inserter than inserts the *.swf and a meta file into a *.exe or *.apk and then they just read off the data and display it. The *.exe could use a .NET browser element and load it into that with a URL from temporary storage.

Any help would be great. Thank guys.

---

