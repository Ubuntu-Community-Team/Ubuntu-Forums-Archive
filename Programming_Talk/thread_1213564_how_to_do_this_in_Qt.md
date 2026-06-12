---
title: "how to do this in Qt??"
date: 2009-07-14
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-14
as you can see in this pictures, what is simplest way of doing this in Qt, also controlling these objects wrt input or signals and values,
i went through Qt manual but din't find any solution,  
as i'm newbie to Qt, you can suggest your opinions of how to achieve this....

---

### Post by JordyD on 2009-07-14
> **abhilashm86 said:**
> as you can see in this pictures, what is simplest way of doing this in Qt, also controlling these objects wrt input or signals and values,

Create a class that inherits from QWidget. Then you can use a QImage or QPixmap to draw it, or so I read. I'm sure you can get more info from the Qt 4 Docs.

---

### Post by abhilashm86 on 2009-07-15
> **JordyD said:**
> Create a class that inherits from QWidget. Then you can use a QImage or QPixmap to draw it, or so I read. I'm sure you can get more info from the Qt 4 Docs.

oh ok, so for every particular component we create a class, so that anytime we want to access those component, we use that main class, 
can i say the created particular object is base class for each component??
i'd doubt as QWidget is main base class of all components, 
thanks i got an overview!! 
> I'm sure you can get more info from the Qt 4 Docs
i use Qt 4.5, i'll sure check out once more......

---

