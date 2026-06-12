---
title: "Qt : How can I use \0 like in Kate for search and replace?"
date: 2009-09-16
forum: Programming Talk
---

### Post by KIAaze on 2009-09-16
How can I use \0 like in Kate for search and replace?

i.e. If my search expression is: "(.*)",
my replace string: "prefix_\0_suffix"
and my input string is "foobar"
I want to obtain  "prefix_foobar_suffix".

Current test code:
```
    QString text = "foobar";
    QString rep = "prefix_\0_suffix";
    QRegExp rx(".*");
    qDebug()<<rx.indexIn(text);
    qDebug()<<rx.cap(0);
    qDebug()<<text;
//    qDebug()<<text.replace(rx.cap(0),"prefix_"+rx.cap(0)+"_suffix");
    qDebug()<<text;
    qDebug()<<rep.replace("\0",text);

```

Output:
```
0 
"foobar" 
"foobar" 
"foobar" 
"foobarpfoobarrfoobarefoobarffoobarifoobarxfoobar_foobar"
```

---

### Post by Reiger on 2009-09-16
I may be totally wrong but many languages tend to treate \ as an escape character; that is to say you are actually asking the thing to replace with "prefix_"++NULL++"_suffix" with ++ being the concatenation operator.

You may have more luck with "\\". I don't know for sure though, never used Qt for anything really.

---

### Post by KIAaze on 2009-09-16
Yes, the single "\" was indeed part of the problem. "rep.replace("\\0",text);" works better.
But now, I still get weird things, like this:
```

     QString t = "foobar";
     t.replace(QRegExp("(.*)"), "U");
     // t should be = "U", no?
     qDebug()<<"t="<<t;

```

Which outputs:
```
t= "UU"
```
:confused::confused::confused:

---

### Post by bigboy_pdb on 2009-09-16
You might want to check [this page]("http://doc.trolltech.com/qq/qq04-betterqt.html"). Search on the text "back-reference" (without the double quotes) to find the section that refers to using back-references with regular expressions.

You might also want to try using 1 instead of 0.

---

### Post by KIAaze on 2009-09-16
No, \0 is what I want.
When used in Kate's search and replace, it gets replaced by the full matching expression.
ex:
Using:
pattern = "f(o*)bar"
replacement = "\0 and \1"

Will replace "=== foobar ===" with:
"=== foobar and oo ==="

Anyway, I managed to get the behaviour I want, altough I'm not sure it will work exactly like Kate's search&replace because of an ugly hack I used:
```
QString RegexReplace(QString text, QString pattern, QString replacement)
{
    QRegExp rx(pattern);
    rx.indexIn(text);
    if(rx.cap(0)==text) {
      // Ugly prepend/append hack
      pattern.prepend("^");
      pattern.append("$");
      rx = QRegExp(pattern);
    }
    rx.indexIn(text);

    QString rep2=QString(replacement).replace("\\0",rx.cap(0));

    QString out;
//     out=text;out.replace(rx,replacement);qDebug()<<"out="<<out;
    out=text;
    out.replace(rx,rep2);
    return out;
}

```

The reason I need to prepend "^" and append "$" is because QString("foobar").replace(QRegExp(".*"),U) will match "foobar" and ""!
It therefore returns "UU".

QString("foobar").replace(QRegExp("^.*$"),U) gives the expected behaviour and returns "U".

---

