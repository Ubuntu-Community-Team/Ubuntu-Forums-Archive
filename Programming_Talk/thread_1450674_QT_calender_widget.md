---
title: "QT calender widget"
date: 2010-04-09
forum: Programming Talk
---

### Post by manojboopathi on 2010-04-09
Hi guys i am developing system restore in ubuntu.
 
i wanna display the restore points the same way as it gets displayed in windows xp
 
is it possible to change the color of individual dates in the calender widget in QT.
 
waiting 4 reply

---

### Post by Zugzwang on 2010-04-09
That should be possible by deriving from the "QCalendarWidget" and overloading the "paintCell" method.

---

### Post by manojboopathi on 2010-04-09
thanks for your quick rep...
 
u said it can be done by overloading paintcell method...
 
after doing that can we obtain which date is clicked by the user..
 
if possible say me the code of that overloading. i am very new to qt. dont have much knowledge in tweeking widgets

---

### Post by Zugzwang on 2010-04-09
I've never did so much QT coding. However, a quick google search revealed that there seem to be examples lying around on the web, for example the following one: [http://www.qtforum.org/article/21614/paintcell-and-qcalendarwidget.html](http://www.qtforum.org/article/21614/paintcell-and-qcalendarwidget.html)

---

### Post by Jammanuser on 2010-04-09
Let me know how it goes. System Restore in Ubuntu would be nice. :)
BTW, I've been coding in QT for a little while, but I haven't used that particular class yet. Are you using Qt Creator? Pretty much every class in Qt is fully documented. I suggest you read all that you find on that class.

---

