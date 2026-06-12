---
title: "PYTHON: append string to prefix"
date: 2010-05-29
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-05-29
Hello there,

I am making a transcription program. This program can for instance replace a string input with 'aa' into '&#257;'. To transcript i must use unicode strings.

Right now i wrote a line for each character combination to be replaced as: 
[PHP]text_output = re.sub('aa', u'\u0101', text_output)[/PHP]
('\u0101' stands for '&#257;')

Instead i created a table in a csv file and load the csv into a list. The list contains other lists, each of which is a row of my csv (with two columns so far. So my list would look like [['a', '\u0101'], etc]

Now for each item in my list i want to replace item[0] by item[1] in the string. The problem is i don't know how to append item[1] to the unicode string prefix u and thus get u'\u0101'

I know how to concatenate strings, but i don't how to turn a string into code that is from 'u' to u and append it to another string...

So what i have so far is:
[PHP]for item in mylist:
        former = item[0]
        latter = item[1]
        text_output = re.sub(former, latter, text_output)
[/PHP]

But that, as you may have understood, doesn't work. :(
I come here as--again--i found the online documentation far too obscure to understand any of the jargon.
Any tips?
Thanks :)

---

### Post by diesch on 2010-05-29
To convert a bytestring into a unicode string you use its *decode* method:

```
latter = item[1].decode('utf-8')
```

Replace *'utf-8'* with the character encoding you are using for your bytestring

---

### Post by jesuisbenjamin on 2010-05-29
Yes thanks! :)

---

