---
title: "KURLRequester"
date: 2005-12-17
forum: Programming Talk
---

### Post by SeeLook on 2005-12-17
I try to add kurlrequester widget to my app. I work in Kdevelop. I try to do this both, by graphics projected *.ui file and in code:
```
KURLRequester *xxxx = new KURLRequester (this,"xxxx")
```

I get the same:
```
undefined reference to `KURLRequester::KURLRequester(QWidget*, char const*)'
``` (in case ui file, it shows error in auto generated .cpp file from ui) 

But when i compiled other project from sources, which used this widget everything is fine. I compared the code (mine and from the projects) it looks equaly. 
Have You any idea where is the problem ??

I use Kdevelop 3.3.0 on Kubuntu Breezy with KDE 3.5.0

---

### Post by toojays on 2005-12-17
Have you included the header file for this class?

---

### Post by SeeLook on 2005-12-18
Yes, I done this.
I tryed to declare variable in header, too.
(with class KURLRequester)

I've gived up. I tryed call KFileDialog::getOpenFilename method, but the effect is the same: undefined reference. 
All this headers (KURLRequester.h KFileDialog.h) are in the same directory (/usr/include/kde), but with the others (f eg. klineedit) i have no problem.

Could somebody try this in his system
```
#include <kurlrequester.h>

someclass::someclass {
    ...
    ...    
    KURLRequester *xxxx = new KURLRequester(this,"xxxx");
    ...
 }
```

---

