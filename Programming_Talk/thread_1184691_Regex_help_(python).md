---
title: "Regex help (python)"
date: 2009-06-11
forum: Programming Talk
---

### Post by matmatmat on 2009-06-11
Can anyone give me an regex to get the URL to a webpage in html:
```

<a href="test.html">click</a>
<a href='test.html'>click</a>

```
that can be used with the python re module, I'm not sure if i should check for a match then split the line or to do something else?

---

### Post by leblancmeneses on 2009-06-11
```

[FONT=monospace]Regex.Match(input, @"href\s*=\s*[/FONT][FONT=monospace]\"[/FONT][FONT=monospace](?<urlOfInterest>[^"]+)\"", [/FONT]RegexOptions.IgnoreCase | *RegexOptions*.*Multiline*)

```what i've done here is forget about tags and look for attributes of specific interest.
\s* means zero or more white spaces, because multiline is set it will also match newlines
[^"]+ negative character group that means match anything that is not a double quote. 


for perfect matching i would actually write grammar rule using my library
npeg.codeplex.com

other ways people accomplish this is to build a sax parser and just apply regex in attributes section.

---

### Post by ghostdog74 on 2009-06-11
its better to use a HTML parser.

---

### Post by myrtle1908 on 2009-06-11
BeautifulSoup is excellent and very easy to use ... [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)

---

