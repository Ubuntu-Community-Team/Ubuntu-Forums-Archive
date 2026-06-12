---
title: "Qt: QFont has no setColor() option?"
date: 2016-02-18
forum: Programming Talk
---

### Post by fallenshadow on 2016-02-18
Why can't I just go do something like this:

```
qFont->setColor(qcolor);
```

QFont doesn't seem to have any method for setting a colour. Isn't that a common requirement for text. =/

---

### Post by spjackson on 2016-02-19
Why? I don't know because I don't know the reasoning for the design decisions behind Qt. However, it is not uncommon to regard font as not having colour: the controls for this text box that I am typing into have 3 controls for Font, Size and "Text Color".

Yes, setting colour is a common requirement for **text**, but not for font. What is it precisely you are trying to do? e.g. set the default text colour of a QLabel, switch colour within a QTextDocument,  do something with QPainter::drawText or something completely different. Also, could you please say whether you are using Qt 4 or Qt 5?

---

### Post by fallenshadow on 2016-02-19
Thanks spjackson. Its Qt 5 and I think I have this figured out already. I understand now colour isn't part of a font option but its more of a text option. I can see the point I need to change is before I draw the font which is done with a painter. So all I would need to do is pass in the selected colour and then:

```
painter->setPen(qcolor);
```

I will have a go at this tonight and see how it works out. A quick test does show this method works.

---

### Post by fallenshadow on 2016-02-24
This is solved. I just needed to pass on the colour to the point of painting the text with QPainter and it worked. =)

---

