---
title: "Bash scripting help needed"
date: 2011-09-02
forum: Programming Talk
---

### Post by vehemoth on 2011-09-02
Two things, first; how do I set a variable from a previously escaped line
and second
```

#!/bin/bash
#RSS Setup
badlines=6
URI=http://quotes4all.net/rss/240010110/quotes.xml #URI of RSS Feed
firstline=description #Top line to output
extrachar="- " #characters at start of second line
secondline=title #second line to output
quotes=temp

#Work Start
wget -q -O - $URI | sed -e 's/[ \t]*//' |\
sed ':a;N;$!ba;s/<description>\n/<description>/g' | sed ':a;N;$!ba;s/\n<\/description>/<\/description>/g' |\
grep -A 1 '<title>' |\
sed -e :a -e 's/<[^>]*>//g;/</N' |\
head -n $(($badlines+2)) |\
tail -n $((1))

```
Can I replace this line
```

sed ':a;N;$!ba;s/<description>\n/<description>/g' | sed  ':a;N;$!ba;s/\n<\/description>/<\/description>/g' |\

```
with something that works with more than just the description tag (it finds the tag and end tag and deletes the new line before or after if there is no contents on that line)
Thanks for your help :)

---

### Post by mikejonesey on 2011-09-02
previously escaped line... example?

---

### Post by sisco311 on 2011-09-02
You can't realistically parse tag-based markup languages like HTML and XML using Bash or utilities such as grep, sed or cut. If you just want to dump/render HTML, see (links|links2|lynx|w3m) -dump, html2text, vilistextum. For parsing out pieces of data, see tidy+(xmlstarlet|xmlgawk|xpath|xml2), or learn xslt. See: [http://www.codinghorror.com/blog/archives/001311.html](http://www.codinghorror.com/blog/archives/001311.html)

---

### Post by Lars Noodén on 2011-09-02
As mentioned, learn XSLT.

Or become familiar with XML parsers.  CPAN's [XML:: Parser](http://search.cpan.org/~msergeant/XML-Parser-2.36/Parser.pm) or [HTML:: Parser](http://search.cpan.org/~gaas/HTML-Parser-3.68/Parser.pm) are modules to start with in Perl.  Other languages have similar tools.

---

