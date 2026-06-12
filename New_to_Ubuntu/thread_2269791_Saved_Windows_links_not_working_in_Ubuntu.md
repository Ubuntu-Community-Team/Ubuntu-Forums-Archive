---
title: "Saved Windows links not working in Ubuntu"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by Donna_Steenkamp on 2015-03-18
I recently got rid of Windows and am now running Ubuntu.  I had a folder that had all my links to sites I use everyday, however now when I click on them it says "no application associated..."   How do I connect the two so they will work again?

---

### Post by mastablasta on 2015-03-18
they are probably windows shortcuts. if you open the file with editors such as gedit what do you see inside? can you copy & paste it here? or at least part of it.

I mean it is hard for us to know exactly what kind of files you have.

otherwise if you used Firefox in windows you could have exported the bookmarks. if you used explorer then they are likely shortcut files.

edit here is what I get in editor if this is a .website file:
```
[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,2
Prop4=31,BBC - Homepage
[InternetShortcut]
IDList=
URL=http://www.bbc.com/
IconFile=http://www.bbc.co.uk/favicon.ico
IconIndex=1
[{A7AF692E-098D-4C08-A225-D433CA835ED0}]
Prop5=3,0
Prop9=19,0
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop5=8,Microsoft.Website.7D5AE94C.CA4F3BC

```

but what Ubuntu actually needs is only this part: 
```
[http://www.bbc.com/](http://www.bbc.com/)
```

---

