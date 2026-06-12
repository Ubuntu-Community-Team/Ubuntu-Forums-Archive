---
title: "Regex related question"
date: 2011-02-13
forum: Programming Talk
---

### Post by jeree on 2011-02-13
I'm trying to extract sentences form raw HTML. I'm trying to do it by using some keyword and I'm only intrested in actual content of webpage (so not interested in attributes etc).
I figured the best way to do it is by searching for that keyword as a word and then matching the last '.' or '<p>' on the left side and first '.' (not capturing) or '</p>' on the right side. 
For example: 
**<p>Cars are good**. *garbage***. Sentence with another car**. *garbage***.  Sentence with the last car</p>**
So far I have this:
```
String regex = "(\\.|(<p>))[^\\.]*?keyword[^\\.]*?((?=\\.)|</p>)";
```
This is buggy, because it matches the first <p> not the last <p> on the right side.
For example given "<p> *garbage* </p><p>Cars are good." this captures: **<p> *garbage* </p><p>Cars are good**. But I'd like to only capture **<p>Cars are good**
How can I only exclude <p> tags which are not the last ones (I also need to exclude that '.' already there)?

---

### Post by schauerlich on 2011-02-13
HTML is not a regular language. It cannot be parsed by a regular expression. Don't do it.

[http://www.codinghorror.com/blog/2009/11/parsing-html-the-cthulhu-way.html](http://www.codinghorror.com/blog/2009/11/parsing-html-the-cthulhu-way.html)

---

### Post by myrtle1908 on 2011-02-13
You definitely want a parser for this.  I would first "tidy" the HTML with something like HTMLTidy and have it produce something easily parsed by an XML parser.  I've done this before and it works well.  Following this you can easily extract just the document text.  However, you cannot control the document authors grammar and prose - ultimately ensuring parsing is still painful.  For example, their idea of sentence may differ from yours.  Not to mention the potential lack of full-stops/periods and spelling etc.

Of course, instead of HTMLTidy, you could simply strip all HTML tags from the document and try working with that.

There really is no fun to be had with this style of problem!

Good Luck

---

### Post by sdowney717 on 2011-02-14
[http://php.net/manual/en/function.strip-tags.php](http://php.net/manual/en/function.strip-tags.php)
this will strip html and php tags

---

### Post by Some Penguin on 2011-02-14
File under 'doable but not necessarily recommended.

The components of what you're looking for are:

- initial <p> tag
- consecutive items which are:
  tags other than <p>, </p>
  characters outside tags other than .
- </p> tag

so --
```

<[Pp]>  for first part, concatenated with

((?:
  (?:</?[^Pp>][^>]*>)  |      -- start,end tags except <p*>, <P*>
  (?:</?[Pp][^\s>]+[^>]*>) |  -- acceptable p tags like <pre>
  (?:[^\.<])                  -- non-period, non-<
)*)                           -- greedy match any sequence of above

```

or so would in theory work.  Untested but the theory should be plain.  Use of non-capturing ?: is probably a bit gratuitous.  I have /not/ escaped the / (in "/?") or \ (in "\s"); do so as whatever language you're working in requires.

---

### Post by jeree on 2011-02-14
Thanks for help. I decide to go with HTMLTidy, then replacing every <p> and </p> manually with a reserved string and finally discarding every HTML tag.
EDIT to Vapshell: manually as in not with some external tool (e.g. HTMLTIDY).

---

### Post by Vaphell on 2011-02-14
manually? i hope it doesn't mean what it means :) replacing <p> with SOMESTRING and wiping all remaining tags can be done with 3 sed commands.

---

