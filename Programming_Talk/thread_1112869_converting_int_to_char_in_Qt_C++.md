---
title: "converting int to char in Qt C++"
date: 2009-04-01
forum: Programming Talk
---

### Post by animefan82 on 2009-04-01
I want to convert an int to const char. Here's the background.

function call

```

msg(const char *message, const char *title)
{
   QString str(message);
   QString tt(title);
   return QMessage::critical(parentWidget, str, tt, Qt::Ok, Qt::Escape)
}

```

the variable message needs a constant char, but here's the catch. I can't use std, iostream. just Qt. anybody know how I can convert an int variable to const char without using printf, sprintf, atoi or array-loops?
it's basically supposed to look something like this:
```

int counter = ui.listWidget->count();
const char tmp = (casted int) counter;
msg(tmp, "fooTitle);

```

---

### Post by dwhitney67 on 2009-04-01
A const char is not the same as a const char*, aka a "string".  The latter generally refers to a null-terminated string, whereas the former is a single 8-bit character (where only the first 7-bits are usable).

You should consider using QTextStream.

```

QString message;
QTextStream(&message) << ui.listWidget->count;

// QString stores chars as 16-bit unicode characters; thus convert to std::string so that you can get the const char* equivalent.
msg(message.toStdString().c_str(), "footitle");

```

You could also consider using QByteArray, but this seems like overkill.

P.S.  For more on QTextString, [http://doc.trolltech.com/4.5/qtextstream.html](http://doc.trolltech.com/4.5/qtextstream.html).  I would recommend that you bookmark the [Qt Classes API]("http://doc.trolltech.com/4.5/classes.html") webpage so that you can do your own research next time.

---

### Post by scourge on 2009-04-01
> **dwhitney67 said:**
> ```

QString message;
QTextStream(&message) << ui.listWidget->count;
```


I think QString::number() is more convenient than using a QTextStream: [http://doc.trolltech.com/latest/qstring.html#number-3](http://doc.trolltech.com/latest/qstring.html#number-3)

"QString("%1").arg(number)" is another way to do it.

---

### Post by dwhitney67 on 2009-04-01
> **scourge said:**
> I think QString::number() is more convenient than using a QTextStream: [http://doc.trolltech.com/latest/qstring.html#number-3](http://doc.trolltech.com/latest/qstring.html#number-3)

"QString("%1").arg(number)" is another way to do it.

Yes, you are probably correct.  Goes to show that I do not know Qt at all, other than the 5 minutes of research I did last night.  I only wish the OP and other like him would conduct their own research before posting a "simple" question on the forum.

---

### Post by animefan82 on 2009-04-02
> **dwhitney67 said:**
> Yes, you are probably correct.  Goes to show that I do not know Qt at all, other than the 5 minutes of research I did last night.  I only wish the OP and other like him would conduct their own research before posting a "simple" question on the forum.

I don't understand how you guys do that. I'm going around googling and searching the documentation (I've bookmarked the 4.4 API, and not the 4.5), as well as wiki.qtcentre.org, for over a week before posting, and you guys find it in less than 10 minutes???? What's your secret? I guess I'm not cut out to be a researcher, hehe.

```

QString str("Current item count: ");
str.append(QString("%1").arg(widget->count()));
msg(str.toUtf8().constData(), "Item count.");

```

As for the code, the above statements worked beautifully.
PS: I did do research. I'm also not fond of people posting up simple questions without doing at least some initial research. Then again, I always assume they've done that since they're posting in a community forum...
PPS: After re-reading through the QString::number-part of the QString API, I found out I still wouldn't've come to the conclusion of using QString("%1").arg(int) to show me a number as a string by myself. Then again, I'm still a C++ uber-novice, so that could explain some things.

Many thanks, fellas!

---

### Post by scourge on 2009-04-02
> **animefan82 said:**
> I don't understand how you guys do that. I'm going around googling and searching the documentation (I've bookmarked the 4.4 API, and not the 4.5), as well as wiki.qtcentre.org, for over a week before posting, and you guys find it in less than 10 minutes???? What's your secret? I guess I'm not cut out to be a researcher, hehe.

It's okay. We've been programming for a while, so we know where to look.

> 
```

QString str("Current item count: ");
str.append(QString("%1").arg(widget->count()));
msg(str.toUtf8().constData(), "Item count.");

```

As for the code, the above statements worked beautifully.

I think you can still make that shorter:
```

QString str = QString("Current item count: %1").arg(widget->count());
msg(str.toUtf8().constData(), "Item count.");

```


> PPS: After re-reading through the QString::number-part of the QString API, I found out I still wouldn't've come to the conclusion of using QString("%1").arg(int) to show me a number as a string by myself. Then again, I'm still a C++ uber-novice, so that could explain some things.

QString::number() is a totally different way to do it than the arg() method. This is what you used: [http://doc.trolltech.com/latest/qstring.html#arg-10](http://doc.trolltech.com/latest/qstring.html#arg-10)

---

### Post by aliancemd on 2012-02-09
Actually, QString::number([the number variable]) is enough. Btw, I got there searching actually the answer to the initial question. I want to get from 65 an 'A'.

---

### Post by karlson on 2012-02-09
> **animefan82 said:**
> 
the variable message needs a constant char, but here's the catch. I can't use std, iostream. just Qt. anybody know how I can convert an int variable to const char without using printf, sprintf, atoi or array-loops?
it's basically supposed to look something like this:
```

int counter = ui.listWidget->count();
const char tmp = (casted int) counter;
msg(tmp, "fooTitle);

```

Have you looked at [QString documentation](http://developer.qt.nokia.com/doc/qt-4.8/QString.html) for functions ```
setNum
``` or simply do:
```
QString::number(counter).toStdString().c_str()
```

Which will do everything you need for you.

---

