---
title: "Unicode in Qmessagebox?"
date: 2010-11-06
forum: Programming Talk
---

### Post by leon.vitanos on 2010-11-06
want to put a qmessagebox that contains greek characters...

Something like this:

```
QMessageBox msgBox;
msgBox.setWindowTitle("Wallpaper Changer | &#914;&#947;&#940;&#955;&#949; Webcam-&#917;&#953;&#954;&#972;&#957;&#945;");
msgBox.setText("<b>&#913;&#965;&#964;&#942; &#951; &#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#952;&#945; &#949;&#943;&#957;&#945;&#953; &#948;&#953;&#945;&#952;&#941;&#963;&#953;&#956;&#951; &#963;&#964;&#951;&#957;<br>&#949;&#960;&#972;&#956;&#949;&#957;&#951; &#941;&#954;&#948;&#959;&#963;&#951;...</b>");
msgBox.setIconPixmap(QIcon(":/icons/Pictures/Webcam.png").pixmap(QSize(128,128)));
msgBox.setWindowIcon(QIcon(":/icons/Pictures/Webcam.png"));
        msgBox.exec();
```

But I get Chinese/strange symbols and not the greek ones I expected. How can this solved??

---

